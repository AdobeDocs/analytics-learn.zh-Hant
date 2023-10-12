---
title: 如何識別您的Analytics追蹤伺服器和報表套裝ID
description: 設定Adobe Analytics或在其他Experience Cloud解決方案中引用時，您可以甚至有必要瞭解正在使用的Analytics「追蹤伺服器」，或也可瞭解您的資料所要傳送的「報表套裝」。 本影片將展示如何找到這兩個值，無論您是否已經實施 Adobe Analytics。
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
source-wordcount: '330'
ht-degree: 17%

---

# 如何識別您的分析 [!DNL tracking server] 和 [!UICONTROL 報告套裝ID] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

設定Adobe Analytics或在其他Experience Cloud解決方案中引用時，您可以甚至有必要瞭解正在使用的Analytics「追蹤伺服器」，或[!UICONTROL 報告套裝]」中，您已傳送資料至該處。 本影片將展示如何找到這兩個值，無論您是否已經實施 Adobe Analytics。

>[!IMPORTANT]
>
>本文和影片適用於Adobe Analytics的「AppMeasurement」實作，而非使用Web SDK的實作。

## 實施以後 {#after-implementation}

在網站上實施Analytics後，您會找到 [!DNL tracking server] 和 [!DNL report suite ID] 在追蹤信標中。 此 [!DNL tracking server] 是指標中的主機名稱，因此很容易可找到。 此 [!UICONTROL 報告套裝] ID是指標路徑名稱內在「/b/ss/」之後且以逗號分隔的清單。

若要檢視指標，以及隨Analytics和其他Experience Cloud解決方案而來的所有其他資訊，請安裝 [&quot;Experience Cloud Debugger&quot; Chrome擴充功能](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=en).

## 實施以前 {#before-implementation}

**[!DNL Tracking server]**  — 如果您尚未開始實施Adobe Analytics，則您將需為&quot;。sc.omtrdc.net&quot;選擇一個子網域 [!DNL tracking server]. 例如，假設我有一家名為「Jim』s Brims」的線上帽子商店。 我只需設定我的 [!DNL tracking server] 為：

&quot;jimsbrims.sc.omtrdc.net&quot;。

**[!UICONTROL 報告套裝]**  — 若要尋找您的 [!UICONTROL 報告套裝] 已建立的，請登入 [!DNL Analytics] 並前往 [!UICONTROL 管理員] > [!UICONTROL 報表套裝] ，檢視清單 [!UICONTROL 報告套裝]，包括其ID和標題。

如需詳細資訊，請參閱下面影片。

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12&learn=on)
