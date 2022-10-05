---
title: 使用資料層透過「標籤」設定Analytics變數
description: 了解如何使用資料層來搜尋Analytics資料和其他Experience Cloud解決方案。
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 9%

---

# 使用資料層，透過 [!DNL Tags] {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

將資料層用於 [!DNL Analytics] 而其他Experience Cloud解決方案則是最佳作法。 此影片可讓您了解如何從資料層提取值，並在 [!DNL Experience Platform Tags] 填入Adobe Analytics中的變數。

## 資料層 {#data-layers}

A _資料層_ 是JavaScript物件的架構，由開發人員將其新增至數位網頁。 Analytics解決方案最終會使用資料層來填入報表。 標籤管理系統，包括 [!DNL Experience Platform Tags])是讀取資料層、將值對應至變數，並將該資料傳送至數位體驗解決方案的中介。

檢閱 [Experience Cloud檔案](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hant) 和部落格 [資料層：從流行語到最佳實踐](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice).

## 資料層、 [!DNL Experience Platform Tags]，和Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 定義或識別要在網站上使用的資料層標準。

   1. 將資料層盡可能放在頁面的標題區段和呼叫之前 [!DNL Experience Platform Tags]. 這可確保值被立即存取 [!DNL Tags] 以及需要高在上的Adobe解決方案，例如Adobe Target。

1. 請將資料填入資料圖層。
1. 在 [!DNL Experience Platform Tags]，建立&quot;[!UICONTROL 資料元素]」，以對應資料層中的資料點。 這些資料元素會貫穿於 [!DNL Experience Platform Tags] in [!UICONTROL 規則] 和 [!UICONTROL 擴充功能].
1. 在 [!DNL Analytics] 擴充功能的全域變數區段或 [!DNL Tags rule]，請在 [!UICONTROL 資料元素] to [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName]，和其他 [!DNL Analytics] 變數。
1. 觸發傳送資料到 [!DNL Analytics] 的指標。

下列影片會為您逐步解說此程序。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)

>[!NOTE]
>
>此影片中使用的特定資料層可能不被視為貴組織的「最佳實務」。 使用資料層向您的數位行銷解決方案呈現重要資料的概念，是最佳作法。