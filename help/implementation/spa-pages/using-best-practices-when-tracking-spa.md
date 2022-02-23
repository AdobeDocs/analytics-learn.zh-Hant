---
title: '在 Adobe Analytics 中追蹤單次頁面應用程式 (SPA) 時使用最佳實務 '
description: 在本文件中，我們將說明您應遵循並在使用 Adobe Analytics 追蹤單次頁面應用程式 (SPA) 時應知道的數種最佳實務。本文件著重於使用 Experience Platform Launch (此為建議使用的實作方法)。
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: Developer, Data Engineer
level: Intermediate
exl-id: 8fe63dd1-9629-437f-ae07-fe1c5a05fa42
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: ht
source-wordcount: '1669'
ht-degree: 100%

---

# 在 Adobe Analytics 中追蹤單次頁面應用程式 (SPA) 時使用最佳實務 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在本文件中，我們將說明您應遵循並在使用 Adobe Analytics 追蹤單次頁面應用程式 (SPA) 時應知道的數種最佳實務。本文件著重於使用 Adobe [!DNL Experience Platform Launch] (此為建議使用的實作方法)。

初始筆記：

* 以下項目假設您正使用 [!DNL Experience Platform Launch] 在您的網站上實作。如果您未使用 [!DNL Experience Platform Launch]，但可能需要根據您的實作方法調整，可能仍適用這些考量。
* 所有 SPA 不盡相同，因此您可能需要調整部分以下項目，以最符合您的需要，但我們想要跟您分享部分最佳實務；在 SPA 頁面上實作 Adobe Analytics 時您需要考量的要點。

## 在 [!DNL Experience Platform Launch] 中使用 SPA 的簡圖 {#simple-diagram-of-working-with-spas-in-launch}

![適用於 Launch 中 Analytics 的 SPA](assets/spa_for_analyticsinlaunch.png)

**注意：**&#x200B;如上所述，這是如何在 Adobe Analytics 實作中使用 [!DNL Experience Platform Launch] 處理 SPA 頁面的簡圖。我們將在本頁面的下列各節中探討您應仔細考量或進行的步驟和任何問題。

## 設定資料圖層 {#setting-the-data-layer}

在 SPA 頁面上載入新內容時，或在 SPA 頁面上出現動作，您應做的其中一件事就是更新資料圖層。此動作需要在自訂事件引發並觸發 [!DNL Experience Platform Launch] 中的規則前發生，因此 [!DNL Experience Platform Launch] 可以從資料圖層選擇新規則並將這些規則推送到 Adobe Analytics。

以下是資料圖層範例，其中的元素可以在 SPA 上的視圖變更或動作時變更。例如，在全螢幕/多數螢幕變更中，常會變更「[!DNL pageName]」元素，使新的元素可在 [!DNL Experience Platform Launch] 中擷取並傳送至 Adobe Analytics。

```JavaScript
<script>
    digitalData = {
        pageInstanceID: "Launch Demo Site",
        page:{
            pageInfo:{
                pageID: '2745374',
                pageName: 'acs demo - product listing page'
            },
            attributes:{
                project: "Experience Platform Launch Project"
            }
        },
        user : [ {
          "profile" : [ {
            "attributes" : {
              "gender" : "male",
              "age" : "35"
            }
          } ]
        }],
        libraries : {
          adobe : {
            launch : {
              state : 0, // 0 = not loaded , 1 = loaded
              domain : "assets.adobedtm.com"
            }
          }
        }

     };
    </script>
```

## 設定自訂事件並在 [!DNL Experience Platform Launch] 中接聽 {#setting-custom-events-and-listening-in-launch}

新的內容在頁面上載入時，或在網站上發生動作時，您將會想要告知 [!DNL Experience Platform Launch]，因此它可以執行規則並傳送資料至 [!DNL Analytics]。有多種方式可以達成此目的：[!UICONTROL 直接呼叫] [!UICONTROL 規則]或自訂事件。

* [!UICONTROL 直接呼叫] [!UICONTROL 規則]：在 [!DNL Experience Platform Launch] 中，您可以設定[!UICONTROL 直接呼叫] [!UICONTROL 規則]，以在從頁面直接呼叫該規則時執行規則。如果您的頁面載入或您的網站上的動作非常簡單，或它是唯一的並可以每次執行特定的指令集 (每次設定 [!DNL eVar4] to X and trigger [!DNL event2])，則可以使用[!UICONTROL 直接呼叫] [!UICONTROL 規則]。 請參閱有關於建立[!UICONTROL 直接呼叫][!UICONTROL 規則]的 [!DNL Experience Platform Launch] 文件。
* 自訂事件：如需更多功能與動態附加不同值的裝載的功能，您應設定自訂 JavaScript 事件並在 [!DNL Experience Platform Launch] 中接聽它們，其中您可以使用裝載設定變數並傳送資料至 Adobe Analytics。您更有可能會需要用到此功能，因此此選項可視為是最佳實務。然而，您網站上的每項函數可以判定哪一種方法是最適合的方法。我們將在此文件中繼續探討，假設您需要使用此自訂事件方法。

**範例：**&#x200B;在[此](https://helpx.adobe.com/tw/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)說明文件中會有已實作 [!DNL Analytics] (及其他 Experience Cloud 解決方案) 的範例 SPA 網站連結，以及說明哪些項目已實作的文件。在這些 SPA 範例中，已使用下列自訂事件：

* [!DNL event-view-start]：此事件應在所載入視圖/狀態的視圖啟動時引發。
* [!DNL event-view-end]：此事件甚至應在視圖/狀態變更發生且頁面上的所有 SPA 元件都已完成載入時引發。此為一般會觸發呼叫 Adobe Analytics 的事件。
* [!DNL event-action-trigger]：此事件應任何事件在頁面上發生時引發，但不包括視圖/狀態載入。這可能是點選事件或較小的內容變更，而無視圖變更。

如需如何/何時引發事件的詳細資訊，請參閱以上參考頁面/文件。您不必使用相同的事件名稱，但本文列出的功能是建議的最佳實務。下列影片將說明網站範例和在 [!DNL Experience Platform Launch] 中哪裡可接聽自訂事件。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在 [!DNL Experience Platform Launch] [!UICONTROL 規則] 中執行 s.t() 或 s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

使用 SPA 時對於 [!DNL Analytics] 要了解的最重要事情之一就是 `s.t()` 與 `s.tl()` 之間的差異。您將會在 [!DNL Experience Platform Launch] 中觸發其中一種方法，以傳送資料至 [!DNL Analytics]，但您需要知道何時要傳送每筆資料。

* **s.t()** - 「t」表示「追蹤」，為一般頁面檢視。即使 URL 可能不會變更，但視圖變更是否足以讓您&#x200B;*認為*&#x200B;它是新「頁面」？倘若如此，請設定 s.[!DNL pageName] 變數並使用 `s.t()` 傳送呼叫至 [!DNL Analytics]

* **s.tl()** - 「tl」表示「追蹤連結」，一般用於追蹤頁面上的點選或小幅內容變更 (與全螢幕變更相反)。如果您的頁面變更幅度甚小，讓您不會將它視為全新的「頁面」，請使用 `s.tl()`，也不用擔心 s.pageName 變數的設定，因為 [!DNL Analytics] 將忽略該變數。

**秘訣：**&#x200B;有些人會依照一般指導方針行事，如果畫面變更超 50%，則應視為頁面檢視並使用 `s.t()`。如果畫面變更不到 50%，請使用 `s.tl()`。但完全取決於您，而且哪些是您視為新「頁面」，以及您如何可能想要在 Adobe Analytics 中追蹤您的網站。

以下影片說明要在哪裡/如何觸發 Launch by Adobe 中的 `s.t()` 或 `s.tl()`。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數 {#clearing-variables}

使用 Adobe Analytics 追蹤您的網站時，您當然只想要將在合適的時間將合適的資料傳送至 [!DNL Analytics]。在 SPA 環境中，在 [!DNL Analytics] 變數中追蹤的值可持續存在並重新傳送至 [!DNL Analytics] (可能在我們不想要這樣做時)。因此，[!DNL Analytics] [!DNL Launch] 擴充功能中有一個清除變數的函數，因此當您執行下一個影像要求並傳送資料至 [!DNL Analytics] 時，您就能重新開始。

在上圖中，我們將它列在流程的結尾，在您傳入點擊&#x200B;*後*&#x200B;清除變數。其實可以在點擊傳入前或後完成，但應在 [!DNL Experience Platform Launch] 規則中保持一致，因此您可以隨時在設定變數並傳入變數前或後進行清除。 請記住，如果您將要在執行 `s.t()` *前*&#x200B;清除變數，請確定先清除變數，然後設定新變數，最終將新資料傳送至 [!DNL Analytics]。

**注意：**&#x200B;執行 `s.tl()` 時不一定要清除變數，這是因為 `s.tl()` 每次都需要搭配 [!DNL linkTrackVars] 變數使用，才能告知 [!DNL Analytics] 哪些變數要被設定 (自動在 [!DNL Experience Platform Launch] 中背後新增)。 這表示不當的變數通常不會在使用 `s.tl()` 時進入，但在 SPA 環境中使用 `s.t()` 時則是非常建議使用。儘管如此，我想要建議的最佳實務就是將 Clear Variables 函數用於 SPA 環境中的 `s.t()` 和 `s.tl()`，以確保品質資料收集。

以下影片說明要在哪裡/如何清除 [!DNL Launch] 中的變數。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量 {#additional-considerations}

### [!DNL Experience Platform Launch] 中的自訂編碼視窗 {#custom-code-windows-in-launch}

在 [!DNL Launch] [!DNL Analytics] 擴充功能中，您可以將自訂編碼插入兩處：「[!UICONTROL 資料庫管理]」區段和額外的「[!UICONTROL 使用自訂編碼設定追蹤器]」區段。

![Launch Analytics 自訂編碼視窗](assets/launch_analyticscustomcodewindows.png)

重要的是，應知道當在 SPA 頁面上發生初始頁面載入動作時，任一位置確實只會在其中執行編碼一次。如果您需要在網站的視圖變更或動作上執行編碼，則應將其他動作新增到合適的&#x200B;**[!UICONTROL 規則]** (例如，在「page load: event-view-end」[!UICONTROL 規則] 中)，因此編碼每次都會在[!UICONTROL 規則]執行時跟著執行。在[!UICONTROL 規則]中建立該動作時，請設定 *Extension = Core* 和 *Action Type = Custom Code*。

### 「混合式」SPA/一般網站 {#hybrid-spa-regular-sites}

某些網站是「一般」頁面與 SPA 頁面的組合。在此情況下，您需要使用對這兩種類型都有效的策略。在網站上設定自訂事件並觸發 [!DNL Experience Platform Launch] 中的規則時，請 注意，不會根據雜湊變更等從頁面傳送兩次點擊到 [!DNL Analytics]。(如果那是您如何選擇觸發 [!DNL Experience Platform Launch] 規則)。在此情況下，您需要隱藏其中一個頁面檢視，因此不會在 Adobe Analytics 中提供故障資料。

如果您決定將功能分成個別的多個[!UICONTROL 規則]，以便於更能掌控功能，請務必記住/記載您已完成此動作，因此對一項[!UICONTROL 規則]所做的任何變更也可以對其他[!UICONTROL 規則]進行變更，以保護您的 [!DNL Analytics] 資料完整性。

### 透過 A4T 與 [!DNL Target] 整合 {#integration-with-target-via-a4t}

以下為快速圖說文字。如果您使用 A4T 整合 [!DNL Target]，請確定 [!DNL Target] 請求和相同視圖變更上的 [!DNL Analytics] 請求都有相同的 SDID。這將確保您的資料會在解決方案上正確同步。

若要查看點擊數，請使用除錯工具或封包 Sniffer 程式。您也可以使用 Experience Cloud Debugger，此為可以[在這裡](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)下載的 Chrome 擴充功能。[!DNL Target] 應先在頁面上引發，因此您可以在 JavaScript 主控台或除錯工具中查看。

## 其他資源 {#additional-resources}

* [Adobe 論壇上的 SPA 討論](https://forums.adobe.com/thread/2451022)
* [Reference Architecture 網站說明如何在 Experience Platform Launch 中實作 SPA](https://helpx.adobe.com/tw/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
