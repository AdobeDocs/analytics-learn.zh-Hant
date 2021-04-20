---
title: 無 Tag Manager 的自訂連結追蹤
description: 對於頁面上的許多動作，追蹤不應被視為頁面檢視。 在此影片中，如果您不使用標籤管理器(如Experience Platform Launch)，您將學習如何將連結追蹤信標編碼至Analytics。 檢視程式碼，以及學習重要提示。
feature: Appmeasurement Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: "Developer, Data Engineer"
level: Intermediate
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 8%

---


# 無 Tag Manager 的自訂連結追蹤 {#custom-link-tracking-without-a-tag-manager}

對於頁面上的許多動作，追蹤不應被視為頁面檢視。 在此影片中，如果您未使用標籤管理器(例如Adobe[!DNL Experience Platform Launch])，您將學習如何將連結追蹤信標編碼至Analytics。 檢視程式碼，以及學習重要提示。

## 傳送s.tl()信標{#sending-an-s-tl-beacon}

將資料發送到Adobe Analytics有兩個功能：

1. s.t()- 「track」信標，即頁面檢視點擊、增加指定頁面名稱的頁面檢視，以及設定其他變數
1. s.tl()- 「追蹤連結」信標，通常稱為「自訂連結」點擊／信標，不會增加頁面檢視，並會忽略pageName變數。 這通常用於追蹤未載入新頁面／畫面之頁面上的較小動作，或其他未導致新頁面載入的動作。

>[!NOTE]
>
>在此影片中，我們將示範如何在您未使用標籤管理器(例如Adobe[!DNL Experience Platform Launch])時，對自訂連結點擊進行編碼。 我們建議您使用[!DNL Experience Platform Launch]，這是我們實施的最佳實務建議。 不過，如果您需要在`s.tl()`中編寫程式碼，請參閱以下說明如何執行。

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12)

## 程式碼範例 {#sample-code}

以下是影片中自訂連結所使用的范常式式碼：

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

有關自訂連結的詳細資訊，請參閱[documentation](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/function_tl.html)。