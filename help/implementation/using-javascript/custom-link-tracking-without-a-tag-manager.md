---
title: 無 Tag Manager 的自訂連結追蹤
description: 對於頁面上的許多動作，追蹤不應視為頁面檢視。 如果您未使用標籤管理程式(如Experience Platform Launch)，您將學習如何將連結追蹤信標編碼至Analytics。 請參閱程式碼，並學習重要秘訣。
feature: Appmeasurement實作
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: Developer, Data Engineer
level: Intermediate
exl-id: e4567b1c-414e-44ad-982f-52b0150e7eda
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 8%

---

# 無 Tag Manager 的自訂連結追蹤 {#custom-link-tracking-without-a-tag-manager}

對於頁面上的許多動作，追蹤不應視為頁面檢視。 如果您未使用標籤管理程式(例如Adobe[!DNL Experience Platform Launch])，您將學習如何將連結追蹤信標編碼至Analytics。 請參閱程式碼，並學習重要秘訣。

## 傳送s.tl()信標 {#sending-an-s-tl-beacon}

有兩個函式可將資料傳送至Adobe Analytics:

1. s.t()- 「track」信標（即頁面檢視點擊）會遞增指定頁面名稱的頁面檢視，以及設定其他變數
1. s.tl()- 「追蹤連結」信標，通常稱為「自訂連結」點擊/信標，不會遞增頁面檢視，並會忽略pageName變數。 這通常用於追蹤未載入新頁面/畫面之頁面上的較小動作，或不導致新頁面載入的其他動作。

>[!NOTE]
>
>此影片會示範當您未使用Adobe[!DNL Experience Platform Launch]之類的標籤管理程式時，如何編寫自訂連結點擊的程式碼。 建議您使用[!DNL Experience Platform Launch]，我們的實作最佳實務建議。 不過，如果您需要在`s.tl()`中編寫程式碼，以下說明操作方式。

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

如需自訂連結的詳細資訊，請參閱[檔案](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/function_tl.html)。
