---
title: 建立客戶歷程區段 — 第二部分
description: 在第二部分中，瞭解如何建立購買和保留造訪意圖區段，以瞭解客戶的購買歷程並個人化內容。 我們會使用「Book Now」點按或登入等訊號，識別購買和保留意圖，以便有效分析和針對性行銷。
feature: Segmentation
role: User
level: Experienced
last-substantial-update: 2023-07-21T00:00:00Z
jira: KT-13476
thumbnail: KT-13476.jpeg
source-git-commit: bc3bf5b22e3cf5a9d77e3fe8aa2d86c65a7eaefb
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 0%

---


# 建立客戶歷程區段 — 第二部分

在第二部分中，瞭解如何建立購買和保留造訪意圖區段，以瞭解客戶的購買歷程並個人化內容。 我們會使用「Book Now」點按或登入等訊號，識別購買和保留意圖，以便有效分析和針對性行銷。

## 建立購買和保留造訪意圖區段

在上一則貼文中，我們描述了建立造訪意圖區段的程式，並建置了我們的第一個造訪意圖區段「單次點選奇蹟」。 今天，我們將建立購買和保留區段。 我們已將大約23%的造訪分段，並為剩餘的造訪意圖區段建立預留位置。

![影像1](assets/Image-1.png)

我們現在建立的造訪意圖區段，是建立訪客型客戶歷程區段的基礎。 建立造訪意圖區段後，我們會建立這些以訪客為基礎的歷程區段。

回想一下，建立造訪意圖區段是一個排除的過程。 因此，我們並未依時間順序建立這些區段。 我們正在建立造訪意圖區段，以便最輕鬆地定義，更易於定義：

1. 意圖： 0 — 一個點選奇蹟
1. 目的： 3 — 購買
1. 目的： 4 — 保留
1. 目的： 2 — 考量
1. 目的： 1 — 意識

在上一篇文章中，我稱「購買」區段為「預訂」，因為我從事旅遊業務。 但日後我們將稱之為「購買」區段，以便更輕鬆地套用至多個產業。

訊號愈清晰，建立區段愈容易。 在上一個貼文中，我們建立了One Hit Wonders區段，這是最容易定義的區段，因為其流量只是跳出。 您會發現「購買」和「保留」意圖區段也非常容易定義，因為它們是根據非常清楚的訊號。

## 客戶歷程與購買傾向不同

在考慮建立購買意圖區段時，請務必記住，識別客戶在其歷程中的位置與傾向不同。 您可能會有一些購買傾向模型，這些模型會對網站訪客評分，以預測他們購買的可能性。 這些模型非常實用，但它們與我們今天要建立的購買意圖區段不同。

雖然傾向模型會嘗試預測訪客是否會購買，但我們的造訪意圖區段會嘗試瞭解個人在購買歷程中的所在位置。 使用意圖區段來瞭解客戶的心態，有助於我們個人化內容並量身打造行銷，以推動適當的流量，進而促進我們的銷售管道。 因此，我們的購買意向區段會尋找明確的行為訊號，指出訪客有意購買。

## 建立購買造訪意圖區段

購買造訪意圖區段很容易定義。 在我的案例中，任何按下「立即預訂」按鈕的人，都會表示預訂郵輪的意圖。 這類似於為線上零售商按一下「結帳」，或媒體內容中的「訂閱」連結。

在決定使用哪個訊號來推斷購買意圖時，您需要做出一些判斷。 我們希望購買意向區段包含所有購買，但轉換率不應為100%。 因此，我們不想針對此區段使用「購買確認」或「感謝您」頁面。

同樣地，「檢閱您的購買」頁面（或在購買確認前的任何頁面）可能太靠下漏斗，無法用於分析和定位。

隨著漏斗往上移，訊號是否適合用於表示客戶有意進行購買就變得不那麼清楚了。 在我的案例中，「立即預訂」類似於零售業「結帳」連結，也就是我使用的訊號。 但在零售內容中，「結帳」可能仍會在漏斗下方太遠，「檢視購物車」甚至「加入購物車」可能更好。

我們可以把它想像成一個雜貨店。 如果有人從貨架上拿起產品，並不表示他們打算購買。 即使他們將其放入購物車中，他們也可以立即將其放回貨架上。 但如果他們將產品放入購物車中，並開始四處走動，則很有可能是想要購買它。 如果他們在結帳行中購買該產品，就非常值得打賭。

我建議使用造訪的頁面或其他明確的購買意向訊號，並避免使用其他較不直接的訊號來識別購買意向。 例如，我不會使用工作階段數或工作階段中的頁面數或類似專案。 這些間接訊號代表考量，而非購買意圖。 請記住，此區段的目的是推斷訪客的造訪意圖，而不是其傾向。

### 使用Analytics工作區識別購買意向訊號

流失報表對於識別指出購買意圖的良好訊號非常有用。 尋找邏輯上表示意圖的地方。 如果您看到某個重大流失進入該步驟，通常會接著在該步驟緊接著發生較小的流失，您可以確認該步驟代表意圖。

![影像2](assets/Image-2.png)

檢視與網站上不同頁面相關聯的轉換率也很實用。 這對於識別指出購買意向但可能不需要購買的頁面特別有用（例如融資頁面、購買設定頁面等）。

![影像3](assets/Image-3.png)

最後，在您的區段中納入購買開始與購買確認之間的所有頁面也很重要。 訪客可在不同時間點四處跳出，並重新進入您的購買流程。

### 排除其他區段

回想一下我們的第一個貼文，我們的造訪意圖區段必須互斥，並完整無遺。 此為本系列中經常會聽到的限制條件。

請確定您的購買意圖區段不包含「一個」和「完成」區段。 您應該只需要排除「一個」和「完成」區段，因為用於購買意圖的訊號非常特定。

請注意，排除「一個」和「完成」區段可能會排除從結帳頁面重新進入您網站的人。 這沒有關係。「一個」和「完成」的定義其實是單頁檢視，這表示即使訪客在結帳頁面上進入或重新整理，其造訪也不會進行，因此沒有購買意圖的表示方式。

### 區段產生器中的購買意圖區段

購買意圖的區段定義非常簡單。

使用造訪容器時，納入明確表示購買意圖的頁面或其他動作。 如果您有多個包含條件，請務必將其放在以「And」條件連線的容器中。

新增排除容器至以「And」條件聯結的區段。 將您的One Hit Wonders區段定義（頁面檢視等於1）新增至「排除」容器。

![影像4](assets/Image-4.png)

作為最佳實務，請務必為容器加上標籤。 您會很高興您這麼做了，尤其是因為我們的區段定義愈來愈複雜。

現在我們已建立購買意圖區段，接下來可以使用造訪意圖資料品質工作區來檢視我們的購買意圖區段與我們的完成和單一意圖區段互斥。

![影像5](assets/Image-5.png)

## 建立保留造訪意圖區段

在郵輪業務中，許多訪客造訪我們的網站是為了管理預訂，但不一定是要購買。 他們可以前往網站輸入旅行資訊、檢視行程、預約晚餐或進行其他活動，而不需要購買郵輪。 我們的客人還可以購買岸邊遊覽或體驗的其他增強功能。 我們將這些增強功能視為保留的一部分，因此將它們與Booking區段（在此部落格系列中稱為「購買」）分開。

零售客戶或許可以帶來回報，或管理其忠誠度計畫。 媒體或技術訂閱者可能使用產品。 如果您的訪客在您的網站上管理他們與您之間的關係，那就是「保留造訪」，我們應檢視這些訊號。 若您提供線上產品，例如媒體、技術、線上銀行或其他產品，可能有許多其他型別的造訪意圖區段，我們不會在本系列中討論。

與購買意向區段一樣，我們要尋找非常明確的意向指示。 對我來說，我們網站的整個區段都專用於管理瀏覽，以便輕鬆識別這些頁面。 對於其他企業來說，這可能更複雜。 尋找登入、帳戶管理、支援頁面造訪等訊號。

我應該注意，「保留」對於此造訪意圖而言有點尷尬，因為該訪客不在我們的網站上，「所以我可以保留為客戶。」 保留是我們此次造訪的打算。 請記得同情我們的客戶，並維持客戶至上的原則！

### 使用Analytics Workspace識別保留意圖訊號

同樣地，Analytics Workspace可協助我們識別保留意圖。 您可以使用頁面、網站區段或自訂區段維度來分類頁面。 尋找低購買轉換率的頁面。 在我們的案例中，我們發現「線上簽到」和「岸邊旅行」(Shorex)頁面的轉換率，比其他在邏輯上與購物和購買更相關聯的頁面要低。

![影像6](assets/Image-6.png)

在Workspace中尋找高流量頁面也是不錯的作法。 掃描高流量頁面的清單，並決定它們是否代表保留意圖。

## 排除其他區段

同樣地，我們的造訪意圖區段需要互斥且完全詳盡。 如果您還沒厭倦閱讀此文，一定會厭倦的！ 對於我們的保留意圖區段，排除購買意圖行為至關重要。

對我們大多數人來說，購買意圖和保留意圖並非互斥行為。 我們邀請來訪者造訪網站管理即將到來的郵輪，同時也為他們的下一次旅行預約（謝謝！）。 如果您是餐廳，訪客可能會檢查其忠誠度點數，然後線上上下訂單。

即使行為並非互斥，我們的區段必須用於Customer Journey分析。 我們可以建立其他非常有趣的區段，以分析購買和忠誠度行為之間的重疊。 但就我們目前的目的而言，我們需要這些區段互相排斥。

由於產生需求是行銷的主要目標之一，因此我們的保留意圖區段將排除購買意圖。 換言之，如果有人造訪我們的網站以管理郵輪，但也表示有意預訂新的郵輪，則該次造訪將進入購買意向區段。

### 區段產生器中的保留意圖區段

我們的區段定義越來越清晰。 在您的區段中包含造訪。 新增保留意圖訊號。 對我來說，這很簡單。 如果頁面名稱開頭為「bge：」（我們已預訂的來賓頁面），則表示您位於區段中。 我新增了超過一個的頁面檢視作為額外的測量（但我們仍會排除下方的一個點選奇蹟）。

然後為您的一次點選奇蹟和購買意圖造訪新增排除容器。 請確定您的容器已加入「And」條件。

![影像7](assets/Image-7.png)

再次檢視您的造訪意圖資料品質工作區，確保您的區段互斥。 我們的造訪意圖區段正在成形良好！

![影像8](assets/Image-8.png)

此時，我們已設定五個造訪意圖區段中的三個。 我們發現這些區段是互斥的。 在接下來的文章中，我們將建立最終的「造訪意圖」區段、「考量與知覺」，而我們的區段將會完整無遺。 設定造訪意圖區段後，我們會將它們集合到訪客型區段中，您會發現這些區段對於分析和個人化非常有用。

## 作者

本文件的作者為：

![Aaron Fossum](assets/aaron-headshot.png)

**Aaron Fossum**、Director、數位分析

Adobe Analytics 達人