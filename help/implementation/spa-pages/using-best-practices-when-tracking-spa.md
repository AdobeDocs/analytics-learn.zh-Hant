---
title: '在Adobe Analytics中追蹤單頁應用程式(SPA)時使用最佳實務 '
description: 在本檔案中，我們會說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時應遵循並注意的幾項最佳實務。 本檔案將著重於使用Experience Platform Launch，此為建議的實作方法。
feature: 實作基本知識
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
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 0%

---

# 在Adobe Analytics中追蹤單頁應用程式(SPA)時使用最佳實務 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在本檔案中，我們會說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時應遵循並注意的幾項最佳實務。 本檔案將著重於使用Adobe[!DNL Experience Platform Launch]，此為建議的實作方法。

初始附註：

* 以下項目會假設您使用[!DNL Experience Platform Launch]在您的網站上實作。 若您未使用[!DNL Experience Platform Launch]，則考量事項仍會存在，但您需要將其調整至實施方法。
* 所有SPA都不同，因此您可能需要調整下列一些項目，以最符合您的需求，但我們想與您分享一些最佳實務；在SPA頁面上實作Adobe Analytics時需要思考的事項。

## [!DNL Experience Platform Launch]中使用SPA的簡單圖表 {#simple-diagram-of-working-with-spas-in-launch}

![launch中的spa](assets/spa_for_analyticsinlaunch.png)

**注意：** 如上所述，此為在Adobe Analytics實作中使用處理SPA頁面的簡化圖 [!DNL Experience Platform Launch]表。在本頁的以下幾節中，我們將討論步驟，以及您應認真考慮或處理的任何問題。

## 設定資料層 {#setting-the-data-layer}

當SPA頁面上載入新內容，或在SPA頁面上發生動作時，您應先更新資料層，這是最好的作法之一。 這必須在自訂事件引發之前發生，並在[!DNL Experience Platform Launch]中觸發規則，這樣[!DNL Experience Platform Launch]才能從資料層擷取新值，並將其推送至Adobe Analytics。

以下是範例資料層，其元素可在檢視變更或在SPA上執行動作時變更。 例如，在全螢幕/大部分螢幕變更中，常會變更「[!DNL pageName]」元素，這樣新元素就能在[!DNL Experience Platform Launch]中擷取並傳送至Adobe Analytics。

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

## 在[!DNL Experience Platform Launch]中設定自訂事件和監聽 {#setting-custom-events-and-listening-in-launch}

當新內容載入頁面或網站上發生動作時，您會想要通知[!DNL Experience Platform Launch]，讓它執行規則並將資料傳送至[!DNL Analytics]。 您可以透過下列幾種不同方式來執行此作業：[!UICONTROL 直接呼叫] [!UICONTROL 規則]或自訂事件。

* [!UICONTROL 直接] [!UICONTROL 呼叫規則]:在中 [!DNL Experience Platform Launch]，您可以設定 [!UICONTROL 直接]  從頁面呼叫時執行的直接呼叫規則。如果您的頁面載入或網站上的動作非常簡單，或者它是唯一的，且每次都能執行特定指令集（將[!DNL eVar4]設為X並每次觸發[!DNL event2]），則您可以使用[!UICONTROL 直接呼叫] [!UICONTROL 規則]。 請參閱[!DNL Experience Platform Launch]關於建立[!UICONTROL 直接呼叫] [!UICONTROL 規則]的檔案。
* 自訂事件：為了獲得更多功能，以及為了能以不同值動態附加裝載，您應設定自訂JavaScript事件，並在[!DNL Experience Platform Launch]中監聽這些事件，以便使用裝載來設定變數，並將資料傳入Adobe Analytics。 您更可能需要此功能，因此此選項會被視為最佳實務。 不過，您網站上的每個函式都可決定最適合的方法。 在本檔案中，我們會假設您需要使用此自訂事件方法。

**範例：** 本說 [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 明檔案中提供已實作(和其他SPA解決方 [!DNL Analytics] 案)的範例Experience Cloud網站連結，以及說明已實作的檔案。在這些SPA範例中，已使用下列自訂事件：

* [!DNL event-view-start]:此事件應會在載入之檢視/狀態的檢視開始時觸發。
* [!DNL event-view-end]:即使發生檢視/狀態變更，且頁面上的所有SPA元件已完成載入，仍應觸發此事件。這通常是觸發對Adobe Analytics的呼叫的事件。
* [!DNL event-action-trigger]:除檢視/狀態載入外，頁面上發生任何事件時，都應觸發此事件。這可以是點按事件，或較小的內容變更，而不會變更檢視。

請參閱上述參考的頁面/檔案，以取得關於如何/何時引發的詳細資訊。 您不必使用這些相同的事件名稱，但此處列出的功能是建議的最佳實務。 以下影片將顯示範例網站，以及[!DNL Experience Platform Launch]中的其中，以監聽自訂事件。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在[!DNL Experience Platform Launch] [!UICONTROL Rule]中執行s.t()或s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

使用SPA時，[!DNL Analytics]最需了解的事項之一，是`s.t()`與`s.tl()`之間的差異。 您將在[!DNL Experience Platform Launch]中觸發其中一種方法，以將資料傳送至[!DNL Analytics]，但您必須知道每個方法的傳送時間。

* **s.t()**  - &quot;t&quot;代表「track」，且為一般頁面檢視。即使URL可能不會變更，檢視是否變更到足以讓您&#x200B;*將*&#x200B;視為新的「page」？ 若是如此，請設定s.[!DNL pageName]變數，並使用`s.t()`將呼叫傳送至[!DNL Analytics]

* **s.tl()**  - &quot;tl&quot;代表「追蹤連結」，通常用於追蹤頁面上的點按次數或小型內容變更，而非全螢幕變更。如果您頁面上的變更很小，因此您不會將其視為全新的「page」，請使用`s.tl()`且不必擔心要設定s.pageName變數，因為[!DNL Analytics]會忽略它。

**提示：** 有些人會使用一般准則，如果畫面變更超過50%，則應視為頁面檢視並使用 `s.t()`。如果對螢幕的更改小於50%，請使用`s.tl()`。 不過，這完全取決於您，以及您認為的新「頁面」，以及您想如何在Adobe Analytics中追蹤您的網站。

以下影片說明在Launch by Adobe中觸發`s.t()`或`s.tl()`的位置/方式。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數 {#clearing-variables}

使用Adobe Analytics追蹤您的網站時，您當然只想在正確的時間將正確的資料傳送至[!DNL Analytics]。 在SPA環境中，[!DNL Analytics]變數中追蹤的值可持續存在，並可在不再需要時重新傳送至[!DNL Analytics]。 因此，[!DNL Analytics] [!DNL Launch]擴充功能中有一個函式可清除變數，這樣當您執行下一個影像要求並將資料傳送至[!DNL Analytics]時，就會有新的顯示窗。

在上圖中，我們將其列在程式結尾，清除您在點擊中傳送之&#x200B;*之後的變數*。 實際上，它可在點擊傳入前或後完成，但在[!DNL Experience Platform Launch]規則中應一致，這樣您一律可在設定變數並傳入之前或之後清除。 請記住，如果要清除&#x200B;*之前`s.t()`的變數，請務必先清除變數，然後設定新變數，最後將新資料傳送至[!DNL Analytics]。*

**注意：** 執行時並非一律需要清除變數， `s.tl()`因為 `s.tl()` 每次都需搭配使 [!DNL linkTrackVars] 用變數，以告 [!DNL Analytics] 知要設定哪些變數(在背景自動新增 [!DNL Experience Platform Launch])。這表示使用`s.tl()`時通常不會傳入錯誤的變數，但在SPA環境中使用`s.t()`時，非常建議使用。 話雖如此，我建議您在SPA環境中同時使用`s.t()`和`s.tl()`清除變數函式，以確保資料收集品質，並以此為最佳實務。

以下影片顯示在何處/如何清除[!DNL Launch]中的變數。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量 {#additional-considerations}

### [!DNL Experience Platform Launch]中的自訂程式碼視窗 {#custom-code-windows-in-launch}

在[!DNL Launch] [!DNL Analytics]擴充功能中，有兩個位置可以插入自訂程式碼：[!UICONTROL 程式庫管理]區段和額外的「[!UICONTROL 使用自訂程式碼設定追蹤器]」區段。

![啟動Analytics自訂程式碼視窗](assets/launch_analyticscustomcodewindows.png)

請務必知道，當您的SPA頁面上發生初始頁面載入時，其中一個位置實際上只會執行其中的程式碼一次。 如果您需要在檢視變更或網站上的動作上執行程式碼，則應將其他動作新增至適當的&#x200B;**[!UICONTROL rule]**(例如在「頁面載入：event-view-end&quot; [!UICONTROL rule])，如此一來，每次[!UICONTROL rule]執行時，就會執行程式碼。 在[!UICONTROL rule]中建立該動作時，請設定&#x200B;*Extension = Core*&#x200B;和&#x200B;*Action Type = Custom Code*。

### 「混合」SPA/一般網站 {#hybrid-spa-regular-sites}

有些網站是「一般」頁面和SPA頁面的組合。 在此例中，您需要使用適用於兩種頁面類型的策略。 在網站上設定自訂事件並觸發[!DNL Experience Platform Launch]中的規則時，請留意，根據雜湊變更等，沒有從頁面進入[!DNL Analytics]的雙重點擊。 （如果您選擇以此方式觸發[!DNL Experience Platform Launch]規則）。 在此情況下，您需要隱藏其中一個頁面檢視，這樣就不會在Adobe Analytics中提供有問題的資料。

如果您決定將功能分解為單獨的[!UICONTROL rules]，以便對其擁有更多控制權，請務必記住/記錄您已執行此操作，以便對一個[!UICONTROL rule]進行任何更改也可以對另一個[!UICONTROL rule]進行，從而保護您的[!DNL Analytics]資料完整性。

### 透過A4T與[!DNL Target]整合 {#integration-with-target-via-a4t}

快速的標注。 如果您使用A4T與[!DNL Target]整合，請確定相同檢視變更上的[!DNL Target]要求和[!DNL Analytics]要求具有相同的SDID。 這可確保您的資料在解決方案上正確同步。

若要查看點擊，請使用除錯程式或封包Sniffer程式。 您也可以使用Experience Cloud Debugger，此Chrome擴充功能可下載[HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)。 [!DNL Target] 應會先在頁面上引發，因此您也可以在JavaScript主控台或除錯工具中檢查。

## 其他資源 {#additional-resources}

* [SPA在Adobe論壇上的討論](https://forums.adobe.com/thread/2451022)
* [參考架構網站，以說明如何在Experience Platform Launch中實作SPA](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
