---
title: '在Adobe Analytics使用追蹤單頁應用程式(SPA)的最佳實務 '
description: 在本檔案中，我們將說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時，應遵循並注意的幾個最佳實務。 本檔案將著重於使用Experience Platform Launch，這是建議的實施方法。
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: "Developer, Data Engineer"
level: Intermediate
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---


# 在Adobe Analytics{#using-best-practices-when-tracking-spa-in-adobe-analytics}中使用追蹤單頁SPA應用程式()的最佳實務

在本檔案中，我們將說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時，應遵循並注意的幾個最佳實務。 本檔案將著重於使用Adobe[!DNL Experience Platform Launch]，這是建議的實施方法。

初始附註：

* 以下項目將假設您使用[!DNL Experience Platform Launch]在您的網站上實施。 如果您未使用[!DNL Experience Platform Launch]，則仍會有考量，但您必須將它們調整為您的實施方法。
* 所有SPA項目都不同，因此您可能需要調整下列項目以最符合您的需求，但我們想與您分享一些最佳實務；當您在頁面上實作Adobe Analytics時，需要考慮的SPA事。

## 在[!DNL Experience Platform Launch] &lt;a1/SPA>中使用的簡單圖表{#simple-diagram-of-working-with-spas-in-launch}

![啟動中的分析spa](assets/spa_for_analyticsinlaunch.png)

**注意：** 如上所述，這是Adobe Analytics實SPA施中使用的頁面處理簡化圖 [!DNL Experience Platform Launch]。在本頁的下列章節中，我們將討論您應仔細考慮或處理的步驟和任何問題。

## 設定資料層{#setting-the-data-layer}

當新內容載入至頁SPA面，或在頁面上執行動作SPA時，您首先應該做的一件事就是更新資料層。 在[!DNL Experience Platform Launch]中觸發自訂事件並觸發規則之前，必須先執行此動作，如此[!DNL Experience Platform Launch]才能從資料層擷取新值並將其推送至Adobe Analytics。

以下是範例資料層，其元素可在檢視變更時變更，或在您的頁面上執行動作時變SPA更。 例如，在全螢幕／多數螢幕變更時，常會變更&quot;[!DNL pageName]&quot;元素，如此新元素就可在[!DNL Experience Platform Launch]中擷取並傳送至Adobe Analytics。

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

## 在[!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}中設定自訂事件和監聽

當頁面上載入新內容或網站上發生動作時，您會想要通知[!DNL Experience Platform Launch]，讓它執行規則並傳送資料至[!DNL Analytics]。 有幾種不同的方式可以做到：[!UICONTROL 直接呼叫] [!UICONTROL rules]或自訂事件。

* [!UICONTROL 直接] [!UICONTROL 呼叫規則]:在中 [!DNL Experience Platform Launch]，您可以設定直 [!UICONTROL 接]  從頁面呼叫直接呼叫時執行的直接呼叫規則。如果您的頁面載入或網站上的動作非常簡單，或者它是唯一的，而且每次都能執行特定指令集（將[!DNL eVar4]設為X並每次觸發[!DNL event2]），則您可以使用[!UICONTROL 直接呼叫] [!UICONTROL 規則]。 請參閱[!DNL Experience Platform Launch]有關建立[!UICONTROL 直接呼叫] [!UICONTROL 規則]的文檔。
* 自訂事件：若需更多功能，以及為了動態附加不同值的裝載，您應設定自訂JavaScript事件並在[!DNL Experience Platform Launch]中監聽這些事件，您可在中使用裝載來設定變數並將資料傳送至Adobe Analytics。 您更可能需要此功能，因此此選項被視為最佳實務。 不過，您網站上的每個函式都可以決定最適合的方法。 我們將在本檔案中進一步假設您需要使用此自訂事件方法。

**範例：在** THIShelp檔案中，SPA有實作過的範例網站(及其他Experience Cloud解決方 [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)  [!DNL Analytics] 案)的連結，以及說明實作過的檔案。在這些范SPA例中，已使用下列自訂事件：

* [!DNL event-view-start]:此事件應在正在載入的檢視／狀態的檢視開始時觸發。
* [!DNL event-view-end]:即使發生檢視／狀態變更且頁面上的所有元件已完成載SPA入時，仍應引發此事件。這個事件通常會觸發對Adobe Analytics的呼叫。
* [!DNL event-action-trigger]:當頁面上發生除檢視／狀態載入外的任何事件時，應觸發此事件。這可以是點按事件，或是內容變更較小，而不會變更檢視。

請參閱上述參考的頁面／檔案，以取得有關如何／何時引發的詳細資訊。 您不必使用這些相同的事件名稱，但此處列出的功能是建議的最佳實務。 以下視訊將顯示範例網站，以及[!DNL Experience Platform Launch]中用來監聽自訂事件的位置。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在[!DNL Experience Platform Launch] [!UICONTROL 規則] {#running-s-t-or-s-tl-in-the-launch-rule}中執行s.t()或s.tl()

使用a時，[!DNL Analytics]最需要瞭解的一SPA點是`s.t()`和`s.tl()`之間的差異。 您將觸發[!DNL Experience Platform Launch]中的其中一種方法，以將資料傳送至[!DNL Analytics]，但您需要知道何時傳送每個方法。

* **s.t()** - &quot;t&quot;代表&quot;track&quot;，是一般的頁面檢視。即使URL不會變更，檢視是否變更得足夠，以便您&#x200B;*考慮*&#x200B;將其視為新的「頁面」? 如果是，請設定s.[!DNL pageName]變數，然後使用`s.t()`將呼叫傳送至[!DNL Analytics]

* **s.tl()** - &quot;tl&quot;代表&quot;track link&quot;，通常用於追蹤頁面上的點按次數或小內容變更，而非全螢幕變更。如果頁面上的變更很小，因此您不會將其視為全新的&quot;page&quot;，請使用`s.tl()`，而不要擔心設定s.pageName變數，因為[!DNL Analytics]會忽略它。

**提示：** 有些人會使用一般准則，如果畫面變更超過50%，應視為頁面檢視並使用 `s.t()`。如果對畫面的變更小於50%，請使用`s.tl()`。 不過，這完全取決於您，以及您認為的新「頁面」，以及您想要如何追蹤您在Adobe Analytics的網站。

以下視頻顯示如何在Launch by Adobe中觸發`s.t()`或`s.tl()`。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數{#clearing-variables}

使用Adobe Analytics追蹤您的網站時，您當然只想在適當的時間將適當的資料傳送至[!DNL Analytics]。 在環SPA境中，[!DNL Analytics]變數中追蹤的值可持續存在，並可能會在我們不再希望時重新傳送至[!DNL Analytics]。 因此，[!DNL Analytics] [!DNL Launch]擴充功能中有一個函式可清除變數，因此當您執行下一個影像要求並傳送資料至[!DNL Analytics]時，會有新的清單。

在上圖中，我們會在程式結束時列出變數，清除您在點擊中傳送&#x200B;*之後的變數*。 實際上，它可在點擊傳入OR之前或之後執行，但應在[!DNL Experience Platform Launch]規則中保持一致，以便您在設定變數並傳入變數之前或之後，一律清除。 請記住，如果您要在&#x200B;*之前清除*&#x200B;變數，請務必先清除變數，然後設定新變數，最後將新資料傳送至[!DNL Analytics]。`s.t()`

**注意：** 執行時並非一律需要清除變數 `s.tl()`, `s.tl()` 因為每次都需要使用變數旁邊的 [!DNL linkTrackVars] 變數，以告知 [!DNL Analytics]  [!DNL Experience Platform Launch]要設定哪些變數（自動在幕後新增）。這表示使用`s.tl()`時通常不會傳入錯誤的變數，但在環境中使用`s.t()`時，則建議使用此變SPA數。 所以，我建議在環境中同時使用`s.t()`和`s.tl()`的「清除變數」函式，以便確保資料收集的品質，這是SPA最佳做法。

以下視訊顯示如何清除[!DNL Launch]中的變數。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量 {#additional-considerations}

### [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}中的自訂代碼窗口

在[!DNL Launch] [!DNL Analytics]擴充功能中，有兩個位置可插入自訂代碼：「[!UICONTROL 程式庫管理]」區段和「使用自訂代碼設定追蹤器」區段。

![啟動Analytics自訂程式碼視窗](assets/launch_analyticscustomcodewindows.png)

請務必知道，當您的頁面上出現初始頁面載入時，其中一個位置實際上只會執行一次程式碼SPA。 如果您需要在檢視變更或網站上的動作上執行程式碼，則應新增額外的動作至適當的&#x200B;**[!UICONTROL 規則]**(例如，在「頁面載入：event-view-end&quot; [!UICONTROL rule])，因此每次運行[!UICONTROL rule]時代碼都會執行。 在[!UICONTROL 規則]中建立該操作時，設定&#x200B;*擴展=核心*&#x200B;和&#x200B;*操作類型=自定義代碼*。

### &quot;Hybrid&quot;SPA/一般網站{#hybrid-spa-regular-sites}

有些網站是「一般」頁面和頁面的SPA組合。 在此例中，您需要使用兩種頁面類型都適用的策略。 在網站上設定自訂事件並觸發[!DNL Experience Platform Launch]中的規則時，請務必注意，根據雜湊變更等，沒有從頁面傳入[!DNL Analytics]的雙重點擊。 （如果您選擇以此方式觸發[!DNL Experience Platform Launch]規則）。 在這種情況下，您需要隱藏其中一個頁面檢視，以免在Adobe Analytics提供有問題的資料。

如果您決定將功能區分為個別的[!UICONTROL 規則]，以便您對其有更多控制權，請務必記住／記錄您已做過的動作，如此您對某個[!UICONTROL 規則]的任何變更都可對另一個[!UICONTROL 規則]進行變更，以保護您的[!DNL Analytics]資料完整性。

### 透過A4T {#integration-with-target-via-a4t}與[!DNL Target]整合

這裡就是一個快速的圖說。 如果您使用A4T與[!DNL Target]整合，請確定相同檢視變更的[!DNL Target]要求和[!DNL Analytics]要求具有相同的SDID。 這將確保您的資料在解決方案上正確同步。

若要查看點擊，請使用偵錯器或封包嗅探器程式。 您也可以使用Experience Cloud Debugger，此為Chrome擴充功能，可下載[HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)。 [!DNL Target] 應該是在頁面上先引發，因此您也可以在JavaScript主控台或除錯程式中檢查。

## 其他資源 {#additional-resources}

* [在SPAAdobe論壇上討論](https://forums.adobe.com/thread/2451022)
* [參考架構網站，以展示如何在Experience Platform LaunchSPA中實作](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)