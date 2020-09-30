---
title: 如何識別您的Analytics追蹤伺服器和報表套裝
description: 設定Adobe Analytics或在其他Experience Cloud解決方案中參照Adobe Analytics時，瞭解您使用的Analytics「追蹤伺服器」或您傳送資料的「報表套裝」通常很有幫助，甚至有必要。 此影片會示範如何找出這兩個值，不論您是否已實作Adobe Analytics。
feature: implementation basics
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
translation-type: tm+mt
source-git-commit: 60f4ce4f563a990576b3331b01cd87c29d424f43
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# 如何識別您的分析 [!DNL Tracking Server] 和報 [!UICONTROL 表套裝] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

設定Adobe Analytics或在其他Experience Cloud解決方案中參照Adobe Analytics時，瞭解您使用的 [!DNL Analytics] 「[!DNL Tracking Server]」或您要傳送資料的「報表套裝」通常很有幫助甚至必要。 此影片會示範如何找出這兩個值，不論您是否已實作Adobe Analytics。

## 實施後 {#after-implementation}

在網站上 [!DNL Analytics] 實作後，您可以在追蹤信標中 [!DNL tracking server] 找到 [!DNL report suite ID] 和右側。 信 [!DNL tracking server] 標中的主機名稱，因此很容易找到。 報 [!UICONTROL 表套裝] ID是信標路徑名稱中緊接在&quot;/b/ss/&quot;後面以逗號分隔的清單。

若要查看信標，以及Experience Cloud解決方案和其他所 [!DNL Analytics] 有資訊，請安裝「 [Experience Cloud除錯程式」Chrome Extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=tw)。

## 實施前 {#before-implementation}

**[!DNL Tracking Server]** -如果您尚未開始Adobe Analytics實作，則會為&quot;。sc.omtrdc.net&quot;選擇子網域 [!DNL tracking server]。 例如，假設我有線上的帽子商店，名為「Jim』s Brims」。 我只需將設定 [!DNL tracking server] 為：

&quot;jimsbrims.sc.omtrdc.net&quot;。

**[!UICONTROL 報表套裝]** -若要尋找已建立的報表套裝，請登入 [!UICONTROL >] AdminReport Suites [!DNL Analytics]in the top功能表，以查看報表套裝清單，包括ID和標題。

請參閱以下視訊以取得詳細資訊。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12)
