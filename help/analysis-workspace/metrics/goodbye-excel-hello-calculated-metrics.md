---
title: 再見Excel，您好計算量度
description: 了解在Adobe Analytics中使用計算量度的優點，以及如何在本文中持續動態檢視您的資料。
feature: Calculated Metrics
role: User
level: Experienced
doc-type: Article
last-substantial-update: 2023-05-02T00:00:00Z
jira: KT-13178
thumbnail: KT-13178.jpeg
source-git-commit: 28db96c38e5318942ddc9f39ec0a2d561e14200c
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# 再見Excel，您好計算量度

了解在Adobe Analytics中使用計算量度的優點，以及如何在本文中持續動態檢視您的資料。

嘿！ 你現在為什麼用Excel? 我知道為什麼。 你要向正確的人彙報。 您正忙著從Adobe Analytics輸入資料，計算轉換率，繪製圖表，並準備將資料全部放入一個PowerPoint中，以便讓決策者接受。 我真的希望您至少能使用Report Builder來執行，但我知道您當中有些人會手動將資料從工作區複製並貼到Excel。

原因為何？

為什麼每個月都要進行手動程式？ 為什麼要每月呈現一次靜態檢視，而非持續的動態檢視？ 為什麼要將它複製到PowerPoint中？ 為何不直接在Adobe Analytics中建立計算量度？

## 計算量度功能強大

計算量度功能強大，但與在Excel中進行數學運算相比，即使是基本的數學函式也確實有用且大幅改善。 讓我們來了解一些優點和使用案例：

1. **計算量度為最新和動態**

   從Adobe Analytics匯出數字時，會鎖定在某個時間點。 您絕對需要知道您的網站或應用程式在前一個月的表現如何，但決策者如何追蹤月中的進展？ 如果您的轉換率下跌一天，然後在月底前回復為平均值，您知道嗎？ 這種暴跌可能是揭示重要遙測問題的有價值資料，甚至更重要的是訪客行為的改變。 透過計算量度，您可以繪製圖表，並在發生當天查看，讓您隨時可以回應。

1. **計算量度可節省您的時間**

   我去過那裡。 複製/貼上。 輸入公式或將上方的儲存格拖曳至下方。 按一下圖表並變更範圍，即可查看過去12或13個月的資料。 現在復製圖表。 再做一次。 再來一次。 再來一次。 發送PowerPoint。 它既乏味又費時，感覺好像你每月都要永遠做。

   您可以改為建立使用計算量度的工作區，將「最近12或13個完整月」當作日期範圍，並讓資料和圖表在每月第一天的午夜時分自動更新。 收件者可以直接存取工作區。 他們可以在當月的第一天或您使用文字視覺效果在資料上新增您的評註（您知道，是報表的有趣部分）後，自動以電子郵件傳送PDF副本給他們。

1. **計算量度可套用至大資料集**

   您可以將所有產品名稱匯出至Excel，並開始計算每位訪客的轉換率和收入，但若有100,000個左右，這會很麻煩。 計算量度沒有問題。 照常將維度放入表格中，然後使用計算量度作為量度。 現在您有一個動態可排序表格，當產品或您使用的任何維度新增至目錄時，表格就會自動更新。

1. **計算量度可避免錯誤**

   Excel錯誤會發生。 我們都去過那裡。 赫克，希臘的整個經濟和兩位著名學者的聲譽都因Excel公式錯誤而毀於一旦。 你可能沒有一個歐洲經濟依靠你的Excel技能，但是，關於預算的決定肯定會根據你的資料而改變。 使用計算量度表示您可以建立量度、提供QA，然後不必再擔心。

### 現在，我們已逐步了解使用計算量度的優點，接下來我們來看看如何將其付諸實踐

**使用案例1 :轉換率**

大部分的轉換率只是簡單的劃分。 將轉換次數除以訪客或造訪次數。 將漏斗最終頁面的頁面檢視次數除以漏斗第一頁的頁面檢視次數。 將內部促銷活動點進次數除以曝光次數。 所有這些作為計算量度可輕鬆完成，並放置在資料延遲低、更新視覺效果和更高分享率的控制面板中。

**使用案例2:內部搜尋**

內部搜尋是了解您網站的最重要工具之一。 網站搜尋結果會告訴您訪客對什麼感興趣，以及他們是否能透過導覽輕鬆找到。 您必須能夠判斷您的網站搜尋是否正常運作，並使用一些基本的加法，而除法就能提供答案。

讓我們從搜索結果開始。 您想知道搜尋詞是會得到結果，還是什麼也沒有。 這些通常是個別事件。 您想不想為新增的所有內部網站搜尋取得第三個事件？ 請改為讓您的裝置休息，並使用計算量度來新增內部搜尋：結果和內部搜索：沒有結果一起獲取內部搜索總計。

未傳回結果的搜尋百分比是多少？ 劃分內部搜尋：新的「內部搜尋總計」計算量度沒有結果。 現在您知道建立新內容以符合這些搜尋詞是否緊迫，或您的內容團隊是否可處理更優先的事項。

我們想知道有多少個搜尋結果會獲得點進次數，且通常也有個別的量度可用。 使用計算量度將點進次數除以該辭彙帶出搜尋結果的次數，並以百分比顯示。 現在您擁有網站上每個內部搜尋詞的點進率。 您可以隔離出帶來無益結果的搜尋辭彙。 它有所有可用的歷史資料，這樣你就可以繪製它的圖表，當你做出改進時，你可以通過觀察該速率的上升或下降，輕鬆地看到它們是否在工作。

將內部搜尋數除以搜尋訪客數。 每個詞語的每位訪客都有搜尋。 如果這個數字很高（越接近1.0越好），您就有兩個可能的問題之一。 點按的結果不良，且您的訪客正在執行多項搜尋以尋找最佳結果，或是他們無法透過導覽找到要尋找的頁面。

如何透過導覽找出這些關鍵頁面？ 為搜尋結果頁面檢視之後的頁面檢視建立計算量度。 將其除以該頁面的頁面檢視總數。 現在您知道來自搜尋結果的頁面檢視百分比。 如果您的比例很高，您可能需要在導覽方面做一些工作。

### 計算量度功能強大

我希望這能告訴您在計算量度中使用基本數學函式的一些可能性，並且您會開始自行建立。 這只會開始說明在計算量度中可進行的數學運算的可能性，即使有四個簡單的函式亦然。 計算量度可協助您從全新的層級了解訪客行為，一旦掌握相關資訊，您就能開啟大門，使用您也能使用的更複雜函式。

## 作者

本文件的作者為：

![吉塔伊頭像](assets/gittai.png)

**奇泰本阿米**,Contrix Catalyst首席顧問

Adobe Analytics 達人