---
title: 沒有標籤管理器的自訂連結追蹤
description: 對於頁面上的許多動作，追蹤不應被視為頁面檢視。 在此影片中，如果您不使用標籤管理器（例如Experience Platform Launch），您將學習如何將連結追蹤信標編碼至Analytics。 檢視程式碼，以及學習重要提示。
feature: appmeasurement implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
translation-type: tm+mt
source-git-commit: 8276828e9e759a1964ca5ea89bb1395e5e78b500
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 4%

---


# 沒有標籤管理器的自訂連結追蹤 {#custom-link-tracking-without-a-tag-manager}

對於頁面上的許多動作，追蹤不應被視為頁面檢視。 在此影片中，如果您不使用標籤管理器(如Adobe [!DNL Experience Platform Launch])，您將學習如何將連結追蹤信標編碼至Analytics。 檢視程式碼，以及學習重要提示。

## 傳送s.tl()信標 {#sending-an-s-tl-beacon}

有兩種功能可將資料傳送至Adobe Analytics:

1. s.t()- 「track」信標，即頁面檢視點擊、增加指定頁面名稱的頁面檢視，以及設定其他變數
1. s.tl()- 「追蹤連結」信標，通常稱為「自訂連結」點擊／信標，不會增加頁面檢視，並會忽略pageName變數。 這通常用於追蹤未載入新頁面／畫面之頁面上的較小動作，或其他未導致新頁面載入的動作。

>[!NOTE]
>
>在此影片中，我們會示範如何在您未使用Adobe等標籤管理程式時，對自訂連結點擊進行程式碼編寫 [!DNL Experience Platform Launch]。 建議您使用我們 [!DNL Experience Platform Launch]的最佳實作建議來實施。 不過，如果您需要在中編寫程 `s.tl()`式碼，請以下說明如何執行。

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

如需自訂連結的詳細資訊，請參閱文 [件](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/function_tl.html)。