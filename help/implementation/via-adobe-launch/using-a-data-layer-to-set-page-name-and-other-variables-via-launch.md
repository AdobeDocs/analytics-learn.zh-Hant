---
title: 使用資料層透過Launch在Adobe Analytics中設定頁面名稱和其他變數
description: 使用資料層做為Analytics和其他Experience Cloud解決方案的最佳實務。 在此影片中，您將瞭解如何將值從資料層拉出，並在Launch中使用這些值，以填入Adobe Analytics中的變數。
feature: launch implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
translation-type: tm+mt
source-git-commit: ee6c03cff5b051d9293d75965e9fd98f151d7fce
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 4%

---


# 使用資料層透過 [!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

使用資料層和其 [!DNL Analytics] 他Experience Cloud解決方案被視為最佳實務。 在此影片中，您將瞭解如何將值從資料層拉出，並使用這些值在Adobe Analytics [!DNL Experience Platform Launch] 中填入變數。

## 資料層 {#data-layers}

在處理網站資料和Adobe Experience Cloud解決方案（尤其是與Adobe Analytics搭配使用）時，最好使用資料層。 _資料層_&#x200B;是 JavaScript 物件的架構，由開發人員將其插入頁面中。The data layers can be used by tracking tools (including tag management systems like [!DNL Experience Platform Launch]) to populate reports. 在 [Experience Cloud檔案或](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html) W3C網站上，尋找有關資料層的其他資訊 [](https://www.w3.org/)。

此外，請參閱部落格資 [料層：從Buzzword到Best Practice](https://theblog.adobe.com/data-layers-buzzword-best-practice/)，它提供您一些有關資料層的絕佳資訊，以及一些範例。

## 資料圖 [!DNL Experience Platform Launch]層和Adobe Analytics（哦，我的？）{#data-layers-launch-and-adobe-analytics-oh-my}

1. 建立資料層標準，以便在您的網站上使用，可供參考 [!DNL Experience Platform Launch]。

   1. 在呼叫前，將此資料層盡可能放在頁面的標題中 [!DNL Experience Platform Launch]，以便讓值立即由Adobe解決方案使用，而 [!DNL Launch]Adobe解決方案則需要放在頁面的標題中，例如Adobe Target。

1. 在資料層中填入資料。
1. 在中 [!DNL Experience Platform Launch]，會建[!UICONTROL 立「資料元素]」，以參考資料層中的資料點，並可在整個規則中使用， [!DNL Experience Platform Launch] 以 [!UICONTROL 及建]立延伸模 組等等。
1. 使用擴 [!UICONTROL 充全域變數或] 規則中的元素 [!DNL Analytics] ，將值指派到 [!UICONTROL prop]、 [!UICONTROL eArs][!DNL Analytics] 、PageNameNameProp或其他變數中。
1. 觸發將資料傳送至的信標 [!DNL Analytics]。

以下視訊會逐步帶您完成整個程式。

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
