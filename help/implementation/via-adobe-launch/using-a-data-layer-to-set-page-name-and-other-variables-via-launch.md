---
title: 透過 Launch 使用資料圖層來設定 Adobe Analytics 中的頁面名稱和其他變數
description: 最佳實務就是將資料圖層用於 Analytics 和其他 Experience Cloud 解決方案。在本影片中，您將會了解如何從資料圖層提取值，並在 Launch 用於填入 Adobe Analytics 中的變數。
feature: Launch Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: Developer, Data Engineer
level: Beginner
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: ht
source-wordcount: '365'
ht-degree: 100%

---

# 透過 使用資料圖層來設定頁面名稱和其他變數[!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

最佳實務就是將資料圖層用於 [!DNL Analytics] 和其他 Experience Cloud 解決方案。在本影片中，您將會了解如何從資料圖層提取值，並在 [!DNL Experience Platform Launch] 用於填入 Adobe Analytics 中的變數。

## 資料圖層 {#data-layers}

使用您的網站上資料和 Adobe Experience Cloud 解決方案，尤其是 Adobe Analytics 時，最佳實務就是使用資料圖層。_資料圖層_&#x200B;是 JavaScript 物件的架構，由開發人員將其插入頁面中。資料圖層可以供追蹤工具 (包含如 [!DNL Experience Platform Launch] 等標記管理系統) 用於填入報告。尋找 [Experience Cloud 文件](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hant)中或 [W3C 網站](https://www.w3.org/)上關於資料圖層的其他資訊。

此外，另請參閱部落格「[資料圖層：從流行語到最佳實務](https://theblog.adobe.com/data-layers-buzzword-best-practice/)」，其中會提供關於資料圖層的部分實用資訊，以及一些範例。

## 資料圖層、[!DNL Experience Platform Launch] 和 Adobe Analytics (喔，我的？){#data-layers-launch-and-adobe-analytics-oh-my}

1. 建立要在網站上使用的資料圖層標準，可供 [!DNL Experience Platform Launch] 參照。

   1. 在呼叫 [!DNL Experience Platform Launch] 之前，盡可能將此資料圖層放在頁面前端，越前面越好，因此可供 [!DNL Launch] 和需要在頁面前端的 Adobe 解決方案 (如 Adobe Target) 立即使用。

1. 請將資料填入資料圖層。
1. 在 [!DNL Experience Platform Launch] 中， 建立參照資料圖層內資料點，並可以在[!UICONTROL 規格]、[!UICONTROL 擴充功能]等中 [!DNL Experience Platform Launch] 全程使用的「[!UICONTROL 資料元素]」。
1. 在 [!DNL Analytics] 擴充功能全域變數或規則中使用[!UICONTROL 資料元素]，指派值給 [!UICONTROL props]、[!UICONTROL eVars]、[!UICONTROL pageName] 或其他 [!DNL Analytics] 變數。
1. 觸發傳送資料到 [!DNL Analytics] 的指標。

下列影片會為您逐步解說此程序。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
