---
title: 如何識別您的分析追蹤伺服器和報表套裝 ID
description: 設定 Adobe Analytics 或在其他 Experience Cloud 解決方案中引用時，了解您所使用的 Analytics「追蹤伺服器」通常很有用或者甚至是有必要，或者了解您的資料所要發送的「報表套裝」也很有用。本影片將展示如何找到這兩個值，無論您是否已經實施 Adobe Analytics。
feature: Implementation Basics
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
role: Developer, Data Engineer
level: Beginner
exl-id: 3925026f-69f1-4425-b3a9-6fef26375fed
source-git-commit: 42bf16df9585d1f41206b81bf509a72c10f1d7f2
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---

# 如何識別您的 Analytics [!DNL tracking server]和[!UICONTROL 報表套裝 ID] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

設定 Adobe Analytics 或在其他 Experience Cloud 解決方案中引用時，了解您所使用的 Analytics「追蹤伺服器」通常很有用或者甚至是有必要，或者了解您的資料所要發送的「[!UICONTROL 報表套裝]」也很有用。本影片將展示如何找到這兩個值，無論您是否已經實施 Adobe Analytics。

>[!IMPORTANT]
>
>本文和影片適用於 Adob&#x200B;&#x200B;e Analytics 的「AppMeasurement」實施作業，而不是使用 Web SDK 的實施作業。

## 實施以後 {#after-implementation}

在網站上實施 Analytics 以後，您可以在追蹤指標中找到[!DNL tracking server]和 [!DNL report suite ID]。[!DNL tracking server]是指標內的主機名稱，因此很容易可找到。[!UICONTROL 報表套裝] ID 是指標路徑名稱內在 &quot;/b/ss/&quot; 以後且以逗號分隔的清單。

若要查看指標，以及隨 Analytics 和其他 Experience Cloud 解決方案而來的所有其他資訊，請安裝 [“Experience Cloud Debugger” Chrome Extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=en)。

## 實施以前 {#before-implementation}

**[!DNL Tracking server]** - 如果您尚未開始實施 Adobe Analytics，則您將需為 &quot;.sc.omtrdc.net&quot; [!DNL tracking server] 選擇一個子網域。例如，假設我有一家銷售帽子的網絡商店，名為 &quot;Jim&#39;s Brims&quot;。我只需設定我的 [!DNL tracking server]為：

“jimsbrims.sc.omtrdc.net” 即可。

**[!UICONTROL 報表套裝]** - 若要查詢您已建立的[!UICONTROL 報表套裝]清單，請登入 [!DNL Analytics]，並從上方選單前往「[!UICONTROL 管理員] > [!UICONTROL 報表套裝]」，即可查看[!UICONTROL 報表套裝]清單 (包含其 ID 和名稱)。

如需詳細資訊，請參閱下面影片。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12&learn=on)
