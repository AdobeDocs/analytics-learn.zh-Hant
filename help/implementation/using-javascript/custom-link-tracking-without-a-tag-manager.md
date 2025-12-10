---
title: 無 Tag Manager 的自訂連結追蹤
description: 對於頁面上的許多動作，不應將追蹤視為頁面檢視處理。在本影片中，您將了解如何將連結追蹤指標編碼到 Analytics，如果您未使用 Tag Manager (如 Experience Platform Launch)。請參閱編碼並學習重要秘訣。
feature: Appmeasurement Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: Developer
level: Intermediate
exl-id: e4567b1c-414e-44ad-982f-52b0150e7eda
source-git-commit: 474e68e2937c82efa459b6ed8048a4abd2753285
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 無 Tag Manager 的自訂連結追蹤 {#custom-link-tracking-without-a-tag-manager}

對於頁面上的許多動作，不應將追蹤視為頁面檢視處理。在本影片中，您將了解如何將連結追蹤指標編碼到 Analytics，如果您未使用 Tag Manager (如 Adobe [!DNL Experience Platform Launch])。請參閱編碼並學習重要秘訣。

## 傳送 s.tl() 指標 {#sending-an-s-tl-beacon}

有兩個功能會傳送資料到 Adobe Analytics：

1. s.t() - 「追蹤」指標是頁面檢視點擊，增加指定頁面名稱的頁面檢視，以及設定其他變數
1. s.tl() - 「追蹤連結」指標常稱為「自訂連結」點擊/治標，不會增加頁面檢視並忽略 pageName 變數。這常用於追蹤頁面上不會載入新頁面/畫面的小動作，或不會造成新頁面載入的其他動作。

>[!NOTE]
>
>在本影片中，我們將說明如何在未使用 Tag Manager (如 Adobe [!DNL Experience Platform Launch]) 時編碼自訂連結點擊。我們建議您使用 [!DNL Experience Platform Launch] 我們對於實作的最佳實務建議。然而，如果您需要在 `s.tl()` 中編碼，以下說明該怎麼做。

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12&learn=on)

## 程式碼範例 {#sample-code}

以下是在影片中自訂連結使用的程式碼範例：

```JavaScript
<a href="#" onclick="
    s.linkTrackVars='events,eVar2,prop2';
    s.linkTrackEvents=s.events='event2';
    s.eVar2='facebook share';
    s.prop2='facebook share';
    s.tl(this,'o','Social Share');
    s.manageVars('clearVars',s.linkTrackVars,1);">
    Click here to share on FaceBook
</a>
```
