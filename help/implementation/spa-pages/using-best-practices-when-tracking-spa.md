---
title: 適用於單次頁面應用程式 (SPA) 的實作最佳做法
description: 了解在單次頁面應用程式 (SPA) 上實作 Adobe Analytics 的一些最佳做法。這包括使用 Experience Platform Tags (此為建議使用的實作方法)。
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
ht-degree: 100%

---

# 適用於單次頁面應用程式 (SPA) 的實作最佳做法 {#implementation-best-practices-for-single-page-appliations}

了解在單次頁面應用程式 (SPA) 上實作 [!DNL Adobe Analytics] 的一些最佳做法。這包括使用 [!DNL Experience Platform Tags] (建議的實作方法)。

初始筆記：

* 以下內容參考使用 [!DNL Experience Platform Tags] 在您的網站上實作 Adobe Analytics。若不使用 [!DNL Experience Platform Tags]，這些考量事項即適用，因此，您必須依您的實作方法進行調整。
* SPA 中存在差異，因此，您應該據以調整方法以最好的方式滿足您的需求。

## 在 [!DNL Experience Platform Tags] 中使用 SPA 的簡圖 {#simple-diagram-of-working-with-spas-in-tags}

![適用於 Tags 中分析的 SPA](assets/spa_for_analyticsinlaunch.png)

**注意：**&#x200B;這是如何在 Adobe Analytics 實作中使用 [!DNL Experience Platform Tags] 處理 SPA 頁面的簡圖。以下區段會確認要考慮的步驟和問題。

## 設定資料層 {#set-the-data-layer}

載入新內容或在 SPA 頁面上發生操作時，請&#x200B;*先更新資料層*。這必須&#x200B;**先**&#x200B;發生，自訂事件才能在 [!DNL Experience Platform Tags] 中觸發規則。這可確保將來自資料層的正確值推送到 Tags，然後再推送到 Adobe Analytics。

以下是範例資料層。 鑑於在您的 SPA 頁面上採取的操作，這些元素中的任何一個都可能會根據初始檢視或檢視的後續變更而改變。例如，在全部或大多數檢視變更時，通常需要傳入唯一的「[!DNL pageName]」值，以區分 Adobe Analytics 報表中的檢視。

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

## 設定自訂事件並在 [!DNL Experience Platform Tags] 中接聽這些事件 {#setting-custom-events-and-listening-in-tags}

當新內容載入或 SPA 頁面上發生操作時，需要通知 Experience Platform Tags 以執行將資料傳送到 [!DNL Analytics] 的規則。對此有多種方式：[!UICONTROL 直接呼叫規則]或自訂事件。

* [!UICONTROL 直接呼叫規則]：設定[!UICONTROL 直接呼叫規則]，以從頁面直接呼叫時進行執行。如果頁面載入或操作簡單或是唯一，並每次都能執行特定的指令集 (例如，將 [!DNL eVar4] 設定為 X 並且每次都會觸發 [!DNL event2])，則此方法即適合。請參閱 [!DNL Experience Platform Tags] 文件，以取得有關建立 [!UICONTROL  直接呼叫規則]的詳細資料。
* 自訂事件：如果您需要為 SPA 頁面上發生的事件動態附加具有唯一值的有效裝載，請使用自訂 JavaScript 事件，並在 [!DNL Experience Platform Tags] 中接聽。使用該裝載在 Tags 中設定資料元素和 Analytics 變數。這種方法被認為是最佳做法，因為這種需求通常對 SPA 很普遍。我們以下範例會使用自訂事件方法。

**範例：**[在這個](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)說明文件中，有範例 SPA 網站的連結，這些網站會實作 [!DNL Analytics] 和其他 Experience Cloud 解決方案。在這些範例中，已使用下列自訂事件：

* **[!DNL Event-view-start]**：在載入的檢視/狀態的檢視開始時執行。
* **[!DNL Event-view-end]**：當發生檢視/狀態變更並且頁面上的所有 SPA 元件完成載入時執行。這種事件通常會傳送資料到 Adobe Analytics。
* **[!DNL Event-action-trigger]**：當頁面上發生任何事件時執行，但不包括檢視/狀態載入。這類範例包括點選事件或較小的內容變更，但檢視未變更。

如需如何及何時引發事件的詳細資訊，請參閱頁面和文件。您不需要在實作中使用相同的事件名稱。所用方法的功能使用案例對於理解為每種方法的建議最佳做法至關重要。以下影片示範了在 [!DNL Experience Platform Tags] 中接聽自訂事件的 SPA 頁面範例和程式碼範例。

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 在 [!DNL Experience Platform Tags] 中執行 st() 或 s.tl() {#running-s-t-or-s-tl-in-the-launch-rule}

使用 SPA 時對於 [!DNL Analytics] 要了解的最重要概念就是 `s.t()` 與 `s.tl()` 之間的差異。您的程式碼會在 [!DNL Experience Platform Tags] 中觸發這些方法的一個或其他，以將資料傳送到 [!DNL Analytics]。

* **s.t()** - 此「t」代表「追蹤」，這表示頁面檢視。如果檢視的變更程度足以讓您將其&#x200B;*視為*&#x200B;一個新的「頁面」，則使用此呼叫。設定 [!DNL s.pageName] 變數的唯一值並使用 `s.t()` 將資料傳送到 [!DNL Analytics]。

* **s.tl()** - 此「tl」代表「追蹤連結」，而且這表示連結點擊或小規模的內容變更。如果檢視變更很小，請使用 `s.tl()` 將有關互動的唯一值傳遞給 [!DNL Analytics]。傳入的這個變數並不是 [!DNL s.pageName]，因為當接聽 `s.tl()` 呼叫時，這在 Analytics 中會受到忽略。

**提示：** 一般而言，如果畫面變更超過 50%，則使用 `s.t()` 頁面檢視呼叫。否則，會使用 `s.tl()`。但是，在考慮構成新「頁面」的操作以及應如何在 Adobe Analytics 報表中呈現時，請使用您的判斷。

以下影片會說明要在哪裡以及如何觸發 Tags 中的 `s.t()` 或 `s.tl()`。

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 清除變數 {#clear-variables}

在適當的時間將正確的資料傳送到 [!DNL Analytics]。在 SPA 環境中，儲存在 [!DNL Analytics] 變數中的值可持續存在並重新傳送至 [!DNL Analytics] (可能在您不再需要時)。在 [!DNL Analytics] [!DNL Tags] 擴充功能中存在用來清除變數的函數，以確保下一次呼叫不會錯誤地將資料傳送到 [!DNL Analytics]。

上圖顯示變數在您傳送資料&#x200B;*之後*&#x200B;已清除。實際上，這可能發生在呼叫之前或之後，但是，在您的 [!DNL Experience Platform Tags] 規則中必須一致，以便實作結果更乾淨。如果您&#x200B;*先*&#x200B;清除變數，再執行 `s.t()`，則在呼叫後需立即設定新變數，然後繼續將新資料傳送到 [!DNL Analytics]。

**注意：**&#x200B;執行 `s.tl()` 並不一定都要清除變數。此呼叫需要使用 [!DNL linkTrackVars] 變數來指示 [!DNL Analytics] 要設定哪些變數。這會透過設定自動發生 [!DNL Experience Platform Tags]。這可防止設定了和 SPA 環境中 `s.t()` 呼叫相反的錯誤變數。為了確保最乾淨和最可靠的實作，在 SPA 環境中對兩個呼叫都使用清除變數函數可能較為容易。

以下影片會說明要在哪裡以及如何清除 [!DNL Tags] 中的變數。

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 其他考量事項 {#additional-considerations}

### [!DNL Experience Platform Tags] 中的自訂程式碼視窗 {#custom-code-windows-in-tags}

在 [!DNL Tags] [!DNL Analytics] 擴充功能中，可將自訂程式碼插入兩處：「[!UICONTROL 資料庫管理]」和「[!UICONTROL 使用自訂程式碼設定追蹤器]」區段。

![Tags Analytics 自訂程式碼視窗](assets/launch_analyticscustomcodewindows.png)

這些位置中的任何一個都會執行一次其中包含的程式碼，以便初始頁面載入您的 SPA 頁面。如果程式碼應該在檢視或操作變更上執行，請在適當的 **[!UICONTROL 規則]** (例如「頁面載入：event-view-end」規則) 中實作該程式碼，以確保每次執行 [!UICONTROL  規則]時程式碼都會執行。在[!UICONTROL 規則]中建立該操作時，請設定 *Extension = Core* 和 *Action Type = Custom Code*。

### 「混合」SPA 和傳統網站 {#hybrid-spa-and-traditional-sites}

某些網站是「傳統」和 SPA 頁面的組合。在此情況下，您需要使用對這兩種頁面類型都有效的策略。在網站上設定自訂事件並觸發 [!DNL Experience Platform Tags] 中的規則時，請確保不會根據雜湊變更等而傳送兩次點擊到 [!DNL Analytics]。在這種情況下，需抑制其中一個頁面檢視以防止重複資料傳遞到 Adobe Analytics。

如果您決定將功能分離成唯一 [!UICONTROL  規則]，以獲得更多控制權，請記得記錄您已完成此操作。如果變更一個 [!UICONTROL  規則]，則對另一個 [!UICONTROL  規則]需進行同樣的變更。

### 使用 A4T 和 [!DNL Target] 整合 {#integration-with-target-using-a4t}

當使用 A4T 和 [!DNL Target] 整合時，需確認在相同檢視或操作上傳入的 [!DNL Target] 和 [!DNL Analytics] 請求會傳遞相同的 SDID 參數值。這可確保您的資料會在後端中正確同步。

若要檢視這些點擊，請使用偵錯工具或封包監視工具。Adobe 為此提供了一個 Experience Platform Debugger。這是一種 Chrome 擴充功能，可以[在這裡下載](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en)。[!DNL Target] 應該先在頁面上執行。這也能在偵錯工具中驗證。

## 其他資源 {#additional-resources}

* [Adobe 論壇上的 SPA 討論](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [Reference Architecture 網站說明如何在 Experience Platform Launch 中實作 SPA](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
