---
title: 使用資料層透過Launch在Adobe Analytics設定頁面名稱和其他變數
description: 使用資料層做為Analytics和其他Experience Cloud解決方案被視為最佳實務。 在此影片中，您將瞭解如何將值從資料層拉出，並在Launch中使用這些值來填入Adobe Analytics的變數。
feature: 啟動實施
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: 「開發人員、資料工程師」
level: 初學者
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 7%

---


# 透過 使用資料圖層來設定頁面名稱和其他變數[!DNL Experience Platform Launch]{#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

使用[!DNL Analytics]資料層和其他Experience Cloud解決方案被視為最佳實務。 在此影片中，您將瞭解如何將值從資料層拉出，並在[!DNL Experience Platform Launch]中使用這些值來填入Adobe Analytics的變數。

## 資料層{#data-layers}

在您的網站和Adobe Experience Cloud解決方案(尤其是Adobe Analytics)上處理資料時，最好使用資料層。 _資料層_&#x200B;是 JavaScript 物件的架構，由開發人員將其插入頁面中。資料層可供追蹤工具（包括[!DNL Experience Platform Launch]等標籤管理系統）用來填入報表。 在[Experience Cloud文檔](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html)或[W3C站點](https://www.w3.org/)中查找有關資料層的其他資訊。

此外，請參閱部落格[資料層：從Buzzword到Best Practice,](https://theblog.adobe.com/data-layers-buzzword-best-practice/)提供您一些有關資料層的絕佳資訊，以及一些範例。

## 資料層、[!DNL Experience Platform Launch]和Adobe Analytics（哦，我的？）{#data-layers-launch-and-adobe-analytics-oh-my}

1. 建立資料層標準，以便在您的網站上使用，[!DNL Experience Platform Launch]可參考此標準。

   1. 在呼叫[!DNL Experience Platform Launch]之前，將此資料層盡量放在頁面的標題中，讓[!DNL Launch]和需要頁面高度的Adobe解決方案(例如Adobe Target)立即使用這些值。

1. 在資料層中填入資料。
1. 在[!DNL Experience Platform Launch]中，建立「[!UICONTROL 資料元素]」，以參考資料層中的資料點，並可在[!UICONTROL 規則]、[!UICONTROL 擴充功能]等的整個[!DNL Experience Platform Launch]中使用。
1. 在[!DNL Analytics]擴充全域變數或規則中使用[!UICONTROL 資料元素]，將值指派至[!UICONTROL props]、[!UICONTROL eVars]、[!UICONTROL pageName]或其他[!DNL Analytics]變數。
1. 觸發將資料傳送至[!DNL Analytics]的信標。

以下視訊會逐步帶您完成整個程式。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
