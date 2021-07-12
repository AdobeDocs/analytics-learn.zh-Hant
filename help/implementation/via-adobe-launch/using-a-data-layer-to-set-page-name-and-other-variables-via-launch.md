---
title: 透過Launch使用資料層在Adobe Analytics中設定頁面名稱和其他變數
description: 將資料層用於Analytics和其他Experience Cloud解決方案，是最佳作法。 在此影片中，您將了解如何從資料層提取值，並在Launch中使用這些值來填入Adobe Analytics中的變數。
feature: Launch實作
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: Developer, Data Engineer
level: Beginner
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 7%

---

# 透過 使用資料圖層來設定頁面名稱和其他變數[!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

將資料層用於[!DNL Analytics]和其他Experience Cloud解決方案被視為最佳作法。 在此影片中，您將了解如何從資料層提取值，並在[!DNL Experience Platform Launch]中使用這些值來填入Adobe Analytics中的變數。

## 資料層 {#data-layers}

使用您網站和Adobe Experience Cloud解決方案上的資料時(尤其是搭配Adobe Analytics)，最好使用資料層。 _資料層_&#x200B;是 JavaScript 物件的架構，由開發人員將其插入頁面中。追蹤工具（包括[!DNL Experience Platform Launch]等標籤管理系統）可使用資料層來填入報表。 在[Experience Cloud文檔](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html)或[W3C站點](https://www.w3.org/)上查找有關資料層的其他資訊。

此外，請參閱部落格[資料層：從Buzzword到最佳實務，](https://theblog.adobe.com/data-layers-buzzword-best-practice/)可提供一些關於資料層的絕佳資訊，以及一些範例。

## 資料層、[!DNL Experience Platform Launch]和Adobe Analytics（哦，我的？）{#data-layers-launch-and-adobe-analytics-oh-my}

1. 建立可在您的網站上使用，且可由[!DNL Experience Platform Launch]參照的資料層標準。

   1. 將此資料層盡可能放在頁面標題中、呼叫[!DNL Experience Platform Launch]之前，讓[!DNL Launch]和需要在頁面上高的Adobe解決方案(例如Adobe Target)可立即使用值。

1. 在資料層中填入資料。
1. 在[!DNL Experience Platform Launch]中，建立參考資料層中資料點的「[!UICONTROL 資料元素]」，並可在[!UICONTROL rules]、[!UICONTROL 擴充功能]等的整個[!DNL Experience Platform Launch]中使用。
1. 在[!DNL Analytics]擴充功能全域變數或規則中使用[!UICONTROL 資料元素]，將值指派至[!UICONTROL prop]、[!UICONTROL eVars]、[!UICONTROL pageName]或其他[!DNL Analytics]變數。
1. 觸發將資料傳送至[!DNL Analytics]的信標。

以下影片會逐步帶您了解程式。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
