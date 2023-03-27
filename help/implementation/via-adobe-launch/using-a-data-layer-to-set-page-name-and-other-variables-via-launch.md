---
title: 使用資料層透過 Tags 設定 Analytics 變數
description: 了解如何將資料層用於獲取 Analytics 資料和其他 Experience Cloud 解決方案。
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: 8fc641743bc9e07b838a22ca64ccc15344d52764
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 100%

---

# 使用資料層透過 [!DNL Tags] 設定 Analytics 變數 {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

最佳做法就是將資料層用於 [!DNL Analytics] 和其他 Experience Cloud 解決方案。在本影片中，您將會了解如何從資料層提取值，並用於在 [!DNL Experience Platform Tags] 填入 Adobe Analytics 中的變數。

## 資料層 {#data-layers}

_資料層_&#x200B;是 JavaScript 物件的架構，由開發人員將其新增至數位網頁。Analytics 解決方案最終會利用資料層填入報告。標記管理系統 (包括[!DNL Experience Platform Tags]) 是讀取資料層、將值對應至變數並將該資料傳送到數位體驗解決方案的中間媒介。

查看有關 [Experience Cloud](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hant) 和部落格[資料層的其他資訊：從流行語到最佳做法](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice)。

## 資料層、[!DNL Experience Platform Tags] 和 Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 定義或確認要在您的網站上使用的資料層標準。

   1. 將資料層放置在頁面的頂端區段中盡可能高的位置，並在對 [!DNL Experience Platform Tags] 呼叫之前。這確保可透過 [!DNL Tags] 以及需要保持在頁面上較高位置的 Adobe 解決方案 (例如 Adobe Target) 存取該值。

1. 請將資料填入資料層中。
1. 在 [!DNL Experience Platform Tags] 中，建立在資料層中可對應資料點的「[!UICONTROL 資料元素]」。這些資料元素在整個 [!DNL Experience Platform Tags] (在[!UICONTROL 規則]和[!UICONTROL 擴充功能]中) 都可使用。
1. 在 [!DNL Analytics] 擴充功能的全域變數區段或 [!DNL Tags rule] 中，將[!UICONTROL 資料元素]中的值分配給[!UICONTROL 屬性]、[!UICONTROL eVars]、[!UICONTROL pageName] 和其他[!DNL Analytics]變數。
1. 觸發傳送資料到 [!DNL Analytics] 的指標。

下列影片會為您逐步解說此程序。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12&learn=on)

>[!NOTE]
>
>本影片中使用的特定資料層可能不被視為您組織的「最佳做法」。使用資料層為您的數位行銷解決方案提供重要資料的概念是最佳做法。