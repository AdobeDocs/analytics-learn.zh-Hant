---
title: 使用資料層在Experience Platform中設定Analytics變數 [!DNL tags]
description: 瞭解如何使用資料層來獲取Analytics資料和其他Experience Cloud解決方案。
feature: Tags
topics: Development
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: a45667a8d7ccb46b9e33bd11a78fac9714a61df5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 50%

---

# 使用資料層在Experience Platform中設定Analytics變數 [!DNL tags]

最佳做法就是將資料層用於 [!DNL Analytics] 和其他 Experience Cloud 解決方案。在本影片中，瞭解如何從資料圖層提取值，並在Experience Platform中使用 [!DNL tags] 以在Adobe Analytics中填入變數。

## 資料層

_資料層_&#x200B;是 JavaScript 物件的架構，由開發人員將其新增至數位網頁。Analytics 解決方案最終會利用資料層填入報告。標籤管理系統，包括Experience Platform [!DNL tags])是讀取資料層、將值對應至變數並將該資料傳送至數位體驗解決方案的中介。

檢閱中資料層的其他資訊 [Experience Cloud檔案](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=zh-Hant).

## 資料層，Experience Platform [!DNL tags]和Adobe Analytics

1. 定義或確認要在您的網站上使用的資料層標準。

   1. 將資料層放置在頁面的頂端區段中儘可能高的位置，並在呼叫Experience Platform之前 [!DNL tags]. 這確保可透過 [!DNL tags] 以及需要保持在頁面上較高位置的 Adobe 解決方案 (例如 Adobe Target) 存取該值。

1. 請將資料填入資料層中。
1. 在Experience Platform中 [!DNL tags]，建立&quot;[!UICONTROL 資料元素]」來對映資料層中的資料點。 這些資料元素在整個Experience Platform過程中都會使用 [!DNL tags] 在 [!UICONTROL 規則] 和 [!UICONTROL 擴充功能].
1. 在 [!DNL Analytics] 擴充功能的全域變數區段或 [!DNL Tags rule] 中，將[!UICONTROL 資料元素]中的值分配給[!UICONTROL 屬性]、[!UICONTROL eVars]、[!UICONTROL pageName] 和其他[!DNL Analytics]變數。
1. 觸發傳送資料到 [!DNL Analytics] 的指標。

下列影片會為您逐步解說此程序。

>[!NOTE]
>
> Launch現在為 **[!DNL tags]**

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12&learn=on)

>[!NOTE]
>
>本影片中使用的特定資料層可能不被視為您組織的「最佳做法」。使用資料層為您的數位行銷解決方案提供重要資料的概念是最佳做法。
