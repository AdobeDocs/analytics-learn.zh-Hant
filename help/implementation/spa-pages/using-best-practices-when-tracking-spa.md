---
title: '在Adobe Analytics中追蹤單頁應用程式(SPA)時使用最佳實務 '
description: 在本檔案中，我們將說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時應遵循並注意的幾個最佳實務。 本檔案將著重於使用建議的實作方法- Experience Platform Launch。
feature: implementation basics
topics: spa
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
translation-type: tm+mt
source-git-commit: 548ac75589383dfd4da4ae02412de91a0a3b28d6
workflow-type: tm+mt
source-wordcount: '1669'
ht-degree: 0%

---


# 在Adobe Analytics中追蹤單頁應用程式(SPA)時使用最佳實務 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

在本檔案中，我們將說明您在使用Adobe Analytics追蹤單頁應用程式(SPA)時應遵循並注意的幾個最佳實務。 本檔案將著重於使用建議 [!DNL Experience Platform Launch]的實作方法Adobe。

初始附註：

* 以下項目將假設您使用在您的 [!DNL Experience Platform Launch] 網站上實施。 如果您未使用，仍會有考量 [!DNL Experience Platform Launch]事項，但您必須將它們調整為您的實作方法。
* 所有SPA都不同，因此您可能需要調整下列部分項目以最符合您的需求，但我們想與您分享一些最佳實務；在SPA頁面上實作Adobe Analytics時需要考慮的事項。

## 使用SPA的簡單圖表 [!DNL Experience Platform Launch] {#simple-diagram-of-working-with-spas-in-launch}

![啟動中的分析spa](assets/spa_for_analyticsinlaunch.png)

**注意：** 如前所述，此圖說明如何在Adobe Analytics實作中使用SPA頁面 [!DNL Experience Platform Launch]。 在本頁的下列章節中，我們將討論您應仔細考慮或處理的步驟和任何問題。

## 設定資料層 {#setting-the-data-layer}

當新內容載入SPA頁面，或在SPA頁面上執行動作時，您應先執行的其中一項動作是更新資料層。 這必須在自訂事件觸發並觸發規則之前 [!DNL Experience Platform Launch]，才能 [!DNL Experience Platform Launch] 從資料層擷取新值並將它們推送至Adobe Analytics。

以下是範例資料層，其元素可在檢視變更或SPA動作時變更。 例如，在全螢幕／大部分螢幕變更時，常會變更「[!DNL pageName]」元素，如此新元素便可擷取並 [!DNL Experience Platform Launch] 傳送至Adobe Analytics。

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

## 設定自訂事件和監聽 [!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}

當頁面載入新內容或網站上發生動作時，您會想要通知， [!DNL Experience Platform Launch] 以便執行規則並傳送資料 [!DNL Analytics]。 有幾種不同的方式可以做到： [!UICONTROL 直接呼叫] 規則  或自訂事件。

* [!UICONTROL 直接呼叫] 規則 :在中 [!DNL Experience Platform Launch]，您可以設定直接 [!UICONTROL 呼叫規則] ，在從頁面  直接呼叫該規則時執行。 如果您的頁面載入或網站上的動作非常簡單，或是它是唯一的，而且每次都可以執行一組特定指示(設為 [!DNL eVar4] X並每次觸發 [!DNL event2] )，則可以使用直接呼叫 [!UICONTROL 規] 則 。 請參 [!DNL Experience Platform Launch] 閱有關建立直接 [!UICONTROL 呼叫規] 則的檔案 。
* 自訂事件：若需更多功能，以及要動態附加具有不同值的裝載，您應設定自訂JavaScript事件，並在中監聽這些事件 [!DNL Experience Platform Launch]，您可在其中使用裝載來設定變數，並將資料傳送至Adobe Analytics。 您更可能需要此功能，因此此選項被視為最佳實務。 不過，您網站上的每個函式都可以決定最適合的方法。 我們將在本檔案中進一步假設您需要使用此自訂事件方法。

**範例：** 在本 [說明檔案中](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)[!DNL Analytics] ，有已實作的範例SPA網站（和其他Experience Cloud解決方案）的連結，以及說明已實作內容的檔案。 在這些SPA範例中，已使用下列自訂事件：

* [!DNL event-view-start]:此事件應在正在載入的檢視／狀態的檢視開始時觸發。
* [!DNL event-view-end]:即使發生檢視／狀態變更，且頁面上的所有SPA元件已完成載入時，仍應引發此事件。 此事件通常會觸發對Adobe Analytics的呼叫。
* [!DNL event-action-trigger]:當頁面上發生除檢視／狀態載入外的任何事件時，應觸發此事件。 這可以是點按事件，或是內容變更較小，而不會變更檢視。

請參閱上述參考的頁面／檔案，以取得有關如何／何時引發的詳細資訊。 您不必使用這些相同的事件名稱，但此處列出的功能是建議的最佳實務。 以下視訊將顯示範例網站，以及監聽 [!DNL Experience Platform Launch] 自訂事件的位置。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在規則中執行s.t()或s.tl() [!DNL Experience Platform Launch][!UICONTROL 。] {#running-s-t-or-s-tl-in-the-launch-rule}

使用SPA時，最需要瞭解的 [!DNL Analytics] 一點是和之 `s.t()` 間的差 `s.tl()`異。 您會在中觸發其中一種方 [!DNL Experience Platform Launch] 法，以傳送資 [!DNL Analytics]料，但您必須知道何時傳送每一種資料。

* **s.t()** - &quot;t&quot;代表&quot;track&quot;，是一般的頁面檢視。 即使URL可能不會變更，檢視是否變更得足夠，您會 *將* 它視為新的「頁面」? 如果是，請設定s。[!DNL pageName] 變數，並 `s.t()` 用於將呼叫 [!DNL Analytics]

* **s.tl()** - &quot;tl&quot;代表&quot;track link&quot;，通常用於追蹤頁面上的點按次數或小內容變更，而非全螢幕變更。 如果頁面上的變更很小，因此您不會將其視為全新的「頁面」，請使用 `s.tl()` ，並且不要擔心設定s.pageName變數，因為 [!DNL Analytics] 會忽略它。

**提示：** 有些人會使用一般准則，如果畫面變更超過50%，應視為頁面檢視並使用 `s.t()`。 如果變更的畫面少於50%，請使用 `s.tl()`。 不過，這完全取決於您，以及您認為新的「頁面」，以及您想要如何在Adobe Analytics中追蹤網站。

以下視訊顯示Launch by Adobe中觸發 `s.t()` 或觸 `s.tl()` 發的位置／方式。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數 {#clearing-variables}

當使用Adobe Analytics追蹤您的網站時，您當然只想在適當的時間傳送 [!DNL Analytics] 適當的資料。 在SPA環境中，變數中追蹤的 [!DNL Analytics] 值可持續存在，並可能會在我們不再希望 [!DNL Analytics]時重新傳入。 因此，擴充功能中有一個函 [!DNL Analytics] 數可清除變數，因此當您執行下一個影像要求並傳送資料至時，變數會呈現全新狀態 [!DNL Launch][!DNL Analytics]。

在上圖中，我們會在程式結束時列出變數，在您傳送點擊 *後* ，清除變數。 實際上，它可在點擊傳入OR之前或之後完成，但應在規則中保持一致，以便您在設定變數並傳入之前或之後 [!DNL Experience Platform Launch] ，都能先清除。 請記住，如果您要在執行前清除 *變數* ，請務必先清除變數，然後設定新變數，最後將新資料傳送至 `s.t()`[!DNL Analytics]。

**注意：** 執行時並非一律需要清除變數 `s.tl()`，因為 `s.tl()` 每次都需要使用變數旁邊的 [!DNL linkTrackVars] 變數，以告知要設定哪些變數( [!DNL Analytics][!DNL Experience Platform Launch]會自動在幕後新增)。 這表示使用時通常不會傳入錯誤的變數 `s.tl()`，但在SPA環境中使用時， `s.t()` 建議使用它。 所以，我建議您在SPA環境中同時使用清除變數功能，以 `s.t()` 確 `s.tl()` 保資料收集品質，這是最佳實務。

以下視訊顯示如何／如何清除中的變數 [!DNL Launch]。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量 {#additional-considerations}

### 自訂程式碼視窗(位於 [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}

在擴充功 [!DNL Launch] 能中，有兩個 [!DNL Analytics] 位置可讓您插入自訂代碼：程式 [!UICONTROL 庫管理] (Library management[!UICONTROL )區段和額外的「使用自]訂代碼設定追蹤器」區段。

![啟動Analytics自訂程式碼視窗](assets/launch_analyticscustomcodewindows.png)

請務必知道，當您的SPA頁面載入初始頁面時，其中一個位置實際上只會執行一次程式碼。 如果您需要在檢視變更或網站上的動作上執行程式碼，則應新增額外的動作至適當的 **[!UICONTROL 規則]** (例如，在「頁面載入：event-view-end」規則) [!UICONTROL 中]，如此程式碼就會在每次執行規則 [!UICONTROL 時執行] 。 在規則中建立該動作 [!UICONTROL 時]，請設 *定「延伸功能=核心* 」, *並設定「動作類型=自訂代碼」*。

### 「混合型」SPA/常規站點 {#hybrid-spa-regular-sites}

有些網站是「一般」頁面和SPA頁面的組合。 在此例中，您需要使用兩種頁面類型都適用的策略。 在網站上設定自訂事件並觸發中的規則時 [!DNL Experience Platform Launch]，請務必注意，根據雜湊變更等，頁面 [!DNL Analytics] 上沒有重複點擊。 (如果您選擇觸發規則的方 [!DNL Experience Platform Launch] 式)。 在這種情況下，您需要隱藏其中一個頁面檢視，以免在Adobe Analytics中提供錯誤資料。

如果您決定將功能區分為不同的 [!UICONTROL 規則] ，以便對它有更多控制權，請務必記住／記錄您已做過的動作，如此一來，對某個規則所做的任何變更，  都可對另一個規則進行變更，以保護您的 [!DNL Analytics] 資料完整性。

### 透過A4T [!DNL Target] 與整合 {#integration-with-target-via-a4t}

這裡就是一個快速的圖說。 如果您要與使 [!DNL Target] 用A4T整合，請確定相同檢視變 [!DNL Target] 更的 [!DNL Analytics] 要求和要求具有相同的SDID。 這將確保您的資料在解決方案上正確同步。

若要查看點擊，請使用偵錯器或封包嗅探器程式。 您也可以使用Experience Cloud除錯程式，此為Chrome擴充功能，可從此處 [下載](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)。 [!DNL Target] 應該是在頁面上先引發，因此您也可以在JavaScript主控台或除錯程式中檢查。

## 其他資源 {#additional-resources}

* [Adobe論壇上的SPA討論](https://forums.adobe.com/thread/2451022)
* [參考架構網站，以示範如何在Experience Platform Launch中建置SPA](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)