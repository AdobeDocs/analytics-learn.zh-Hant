---
title: 單頁應用程式實作最佳實務(SPA)
description: 了解在單頁應用程式(SPA)上實作Adobe Analytics的一些最佳實務。 這包括使用Experience Platform標籤，這是建議的實作方法。
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
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 2%

---

# 單頁應用程式實作最佳實務(SPA) {#implementation-best-practices-for-single-page-appliations}

了解實作的一些最佳實務 [!DNL Adobe Analytics] 在單頁應用程式(SPA)上。 這包括使用 [!DNL Experience Platform Tags]，此為建議的實施方法。

初始筆記：

* 以下內容會參考 [!DNL Experience Platform Tags] 在您的網站上實作Adobe Analytics。 若 [!DNL Experience Platform Tags] 因此，您必須將其調整為您的實施方法。
* 因此，SPA中有些差異，您應據此調整方法，以最符合您的需求。

## 在 [!DNL Experience Platform Tags] 中使用 SPA 的簡圖 {#simple-diagram-of-working-with-spas-in-tags}

![標籤中的SPA for analytics](assets/spa_for_analyticsinlaunch.png)

**注意：** 此簡化圖表說明在Adobe Analytics實作中，使用 [!DNL Experience Platform Tags]. 以下各節將說明需要考慮的步驟和問題。

## 設定資料層 {#set-the-data-layer}

載入新內容或在SPA頁面上發生動作時， *先更新資料層*. 這必須發生 **befor** 觸發規則的自訂事件會在 [!DNL Experience Platform Tags]. 這可確保將資料層的正確值推送至「標籤」，然後再推送至Adobe Analytics。

以下是範例資料層。 在您的SPA頁面上採取的動作下，這些元素中的任何元素都可能會根據初始檢視或後續檢視變更而變更。 例如，在完整檢視或大部分檢視變更時，傳入唯一「[!DNL pageName]「值可區分Adobe Analytics報表中的檢視。

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

## 設定自訂事件，並監聽 [!DNL Experience Platform Tags] {#setting-custom-events-and-listening-in-tags}

當新內容載入時或SPA頁面上發生動作時，必須通知Experience Platform標籤，才能執行將資料傳送至的規則 [!DNL Analytics]. 此作法有幾項： [!UICONTROL 直接呼叫規則] 或自訂事件。

* [!UICONTROL 直接呼叫規則]:設定 [!UICONTROL 直接呼叫規則] 會在從頁面直接呼叫時執行。 如果頁面載入或動作簡單或唯一，而且每次都能執行特定指令集(例如，設定 [!DNL eVar4] X觸發 [!DNL event2] 每次)，則此方法適合。 請參閱 [!DNL Experience Platform Tags] 說明檔案以取得關於建立 [!UICONTROL 直接呼叫規則].
* 自訂事件：如果您需要針對SPA頁面上發生的事件，以唯一值動態附加裝載，請使用自訂JavaScript事件，並在 [!DNL Experience Platform Tags]. 使用裝載來設定標籤中的資料元素和Analytics變數。 此方法被視為最佳實務，因為此需求通常適用於SPA。 以下範例使用自訂事件方法。

**範例：** [在此](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html) 說明檔案中，有實作的範例SPA網站連結 [!DNL Analytics] 和其他Experience Cloud解決方案。 在這些範例中，會使用下列自訂事件：

* **[!DNL Event-view-start]**:在載入的檢視/狀態的檢視開始時執行。
* **[!DNL Event-view-end]**:當檢視/狀態變更發生，且頁面上的所有SPA元件完成載入時執行。 這是通常會傳送資料至Adobe Analytics的事件。
* **[!DNL Event-action-trigger]**:在頁面上發生除檢視/狀態載入以外的任何事件時執行。 例如點按事件或較小的內容變更，而未變更檢視。

請參閱上述參考的頁面和檔案，以取得關於這些事件如何引發及何時引發的詳細資訊。 在實施中，您不需要使用相同的事件名稱。 所用方法的功能使用案例對於了解每種方法的建議最佳實務至關重要。 下列影片示範中的範例SPA頁面和范常式式碼 [!DNL Experience Platform Tags] 會監聽自訂事件。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在 [!DNL Experience Platform Tags] {#running-s-t-or-s-tl-in-the-launch-rule}

需要了解的重要概念 [!DNL Analytics] 使用SPA時， `s.t()` 和 `s.tl()`. 您的程式碼會在 [!DNL Experience Platform Tags] 將資料傳送至 [!DNL Analytics].

* **s.t()** - &quot;t&quot;代表「track」，代表頁面檢視。 如果檢視變更得足夠，  *考慮* 這是新的「頁面」，請使用此呼叫。 將唯一值設為 [!DNL s.pageName] 變數與使用 `s.t()` 將資料傳送至 [!DNL Analytics].

* **s.tl()** - &quot;tl&quot;代表「追蹤連結」，這代表連結點擊或小幅內容變更。 如果檢視變更最小，請使用 `s.tl()` 傳入關於互動的唯一值至 [!DNL Analytics]. 傳入的變數不是 [!DNL s.pageName]，因為當 `s.tl()` 會收到呼叫。

**提示：** 如果畫面變更超過50%，請使用 `s.t()` 頁面檢視呼叫。 否則，請使用 `s.tl()`. 不過，在考慮構成新「頁面」的動作時，請運用您的判斷，以及該如何在Adobe Analytics報告中呈現。

以下影片說明觸發的位置和方式 `s.t()` 或 `s.tl()` 中。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數 {#clear-variables}

將正確的資料傳送至 [!DNL Analytics] 在正確的時間。 在SPA環境中，儲存在 [!DNL Analytics] 變數會持續存在並重新發送至 [!DNL Analytics]，當您不再想要時。 函式存在於 [!DNL Analytics] [!DNL Tags] 擴充功能，以清除變數，確保下次呼叫不會即時將資料傳入 [!DNL Analytics].

上圖顯示已清除的變數 *after* 您傳送資料。 實際上，這可能會在呼叫或之後發生，不過請在您的 [!DNL Experience Platform Tags] 更清潔實施的規則。 如果您清除變數 *befor* 執行 `s.t()`，請在呼叫後立即設定新變數，然後繼續將新資料傳送至 [!DNL Analytics].

**注意：** 執行時，不一定需要清除變數 `s.tl()`. 此呼叫需要使用 [!DNL linkTrackVars] 用於指示的變數 [!DNL Analytics] 要設定的變數。 這會自動發生 [!DNL Experience Platform Tags] 透過設定。 它可防止設定錯誤的變數，而與 `s.t()` 呼叫。 為確保實作最乾淨最可靠，在SPA環境中為兩個呼叫使用清除變數函式可能會較為容易。

以下影片說明清除變數的位置和方式， [!DNL Tags].

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量 {#additional-considerations}

### 中的自訂程式碼視窗 [!DNL Experience Platform Tags] {#custom-code-windows-in-tags}

在 [!DNL Tags] [!DNL Analytics] 擴充功能中，有兩個位置可插入自訂程式碼：「[!UICONTROL 程式庫管理]&quot;和&quot;[!UICONTROL 使用自訂程式碼設定追蹤器]」部分。

![標籤Analytics自訂程式碼視窗](assets/launch_analyticscustomcodewindows.png)

其中一個位置會對初始頁面載入您的SPA頁面執行一次其中所包含的程式碼。 如果程式碼應在檢視或動作變更時執行，請在適當的 **[!UICONTROL 規則]** (例如「頁面載入」：event-view-end」規則)，以確保每次執行程式碼時 [!UICONTROL 規則] 執行。 在中建立動作時 [!UICONTROL 規則]，設定 *擴充功能=核心* 和 *動作類型=自訂程式碼*.

### 「混合」SPA與傳統網站 {#hybrid-spa-and-traditional-sites}

有些網站是由傳統頁面和SPA頁面組合而成。 在此例中，請使用適用於兩種頁面類型的策略。 在網站上設定自訂事件時，以及 [!DNL Experience Platform Tags]，請確定不會將雙重點擊傳入 [!DNL Analytics] 根據雜湊變更等。 在此情況下，會隱藏其中一個頁面檢視，以防止傳入Adobe Analytics的重複資料。

如果您決定將功能區隔為唯一 [!UICONTROL 規則] 要獲得更多控制權，請記住記錄您已完成此操作。 如果您變更 [!UICONTROL 規則]，對另一個進行相同的變更 [!UICONTROL 規則].

### 與整合 [!DNL Target] 使用A4T {#integration-with-target-using-a4t}

與整合時 [!DNL Target] 使用A4T，確認 [!DNL Target] 和 [!DNL Analytics] 在相同檢視或動作上傳送的請求會傳遞相同的SDID參數值。 這可確保您的資料在後端正確同步。

若要檢視這些點擊，請使用偵錯工具或封包監視工具。 Adobe提供Experience Platform偵錯工具。 這是Chrome擴充功能，可以 [下載此處](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en). [!DNL Target] 應先在頁面上執行。 這也可在除錯工具中驗證。

## 其他資源 {#additional-resources}

* [Adobe 論壇上的 SPA 討論](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [Reference Architecture 網站說明如何在 Experience Platform Launch 中實作 SPA](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
