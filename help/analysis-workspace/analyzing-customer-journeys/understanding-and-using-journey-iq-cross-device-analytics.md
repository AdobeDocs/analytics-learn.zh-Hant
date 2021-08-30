---
title: 了解及使用歷程IQ — 跨裝置分析
description: 當使用者與您的品牌互動時，會透過多種方式和在多部裝置上進行互動。 跨裝置分析與Adobe Experience Platform Identity Service整合，以識別裝置對應至人員的方式。 然後，它會運用此智慧，建立使用者行為的跨裝置檢視。 這樣就能對人員，而非裝置進行分析。
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: User
level: Intermediate
exl-id: 3748d5d7-d250-4057-8131-afdc66c80200
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 4%

---

# 了解及使用[!DNL Journey IQ] — 跨裝置分析

當使用者與您的品牌互動時，會透過多種方式和在多部裝置上進行互動。 跨裝置分析與[!DNL Adobe Experience Platform Identity Service]整合，以識別裝置對應至人員的方式。 然後，它會運用此智慧，建立使用者行為的跨裝置檢視。 這樣就能對人員，而非裝置進行分析。

## 跨裝置分析概觀

### 我不是我的設備

當使用者與您的品牌互動時，會以多種方式和在多個「表面」或「裝置」上進行互動。 他們可能在PC或行動裝置上使用網頁瀏覽器，也可能使用行動應用程式。 在以Cookie為基礎收集資料的傳統數位分析中，每個表面都會呈現為獨特的「訪客」。 這表示您的每個人類使用者會以多個不重複訪客的形式呈現。

範例如下. 假設Isabelle以下列方式與您的品牌互動：

*Isabelle有三個訪*
![客傳統Analytics歷程](assets/cda-isabelle-journey-traditional-analytics.png)

伊莎貝爾的歷程分為三部分。 她會以三個不重複訪客來呈現，每個訪客使用不同的裝置執行孤立的工作。 我們需要對伊莎貝爾的互動進行統一、跨裝置的檢視。 [!DNL Journey IQ: Cross-Device Analytics] 提供此檢視。

*Isabelle是*
![一人跨裝置分析歷程](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨裝置檢視可提供更好的分析

以人為中心、跨裝置檢視伊莎貝爾的行為，可能對您的分析產生重大影響。 例如，傳統的訪客型方法無法全面了解行銷管道的成效。 讓我們再次審視Isabelle的歷程，著重於哪個管道獲得其產品檢視和購買的評分。 為了簡單起見，我們會使用[!UICONTROL 上次接觸]歸因，但當您將Isabelle的行為分割為不同的訪客時，使用任何歸因模型都會發生相同的問題。 使用傳統的以訪客為基礎的世界觀，會產生非常不同甚至誤導的結果：

*傳統Analytics與跨裝置分析管道歸*
![因的比較](assets/channel-attribution.png)

請注意，透過跨裝置檢視，電子郵件管道會收到產品檢視和購買的評分，更精確地呈現Isabelle的真實世界體驗。

繼續閱讀以了解：

* [!DNL Cross-Device Analytics]如何運作
* [!DNL Cross-Device Analytics]的必要條件
* 解譯跨裝置資料
* 在Analysis Workspace中分析跨裝置資料

## [!DNL Cross-Device Analytics]如何運作

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 與整合， [!DNL Adobe Experience Platform Identity Service]利用或來 [[!DNL Co-op Graph]](https://experienceleague.adobe.com/docs/device-co-op/using/home.html?lang=zh-Hant) 識別 [!DNL Private Graph] 裝置對應至人員的方式。然後，它會運用此智慧，建立使用者行為的跨裝置檢視。 CDA包含無與倫比的功能和工具，可協助您的企業在與品牌互動時，了解這些裝置的使用方式和客戶體驗。 它位於Analysis Workspace下方的一個層級，可使用功能強大的工具（例如[!UICONTROL Fallout]、[!DNL Flow]、[!DNL Cohort]、[!DNL Segment IQ]及[!DNL Attribution IQ]），深入分析以人為為基礎的受眾分析和跨裝置歸因、細分和歷程分析。

### 此  [!DNL Cross-Device Virtual Report Suite]

CDA是透過特殊類型的跨裝置[[!UICONTROL 虛擬報表套裝]](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html)呈現。 這可讓您在組織導入跨裝置分析時，繼續使用原始的裝置型報表套裝。 設定CDA VRS很簡單。

在VRS產生器的步驟一中，選擇已由Adobe設定為已啟用CDA的[!UICONTROL 報表套裝]:

*選擇啟用CDA的基礎（來源）報表套 [!UICONTROL 裝虛]*
![[!UICONTROL 擬報表套] 裝步驟一](assets/cda-vrs-step-one.png)

然後開啟[!UICONTROL 報表時間處理]並啟用[!UICONTROL 跨裝置匯整]:

*啟 [!UICONTROL 用報表時] 間處 [!UICONTROL 理和跨裝]*
![[!UICONTROL 置匯整虛擬報表] 套裝步驟二](assets/cda-vrs-step-two.png)

完成VRS設定並儲存。 CDA VRS會在Analysis Workspace中顯示，旁邊會顯示一個特殊圖示，如下所示：

*在Analysis Workspace中選取CDA VRS虛擬*
![[!UICONTROL 報表套] 裝步驟三](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以在啟用CDA的基礎[!UICONTROL 報表套裝]上，視需要建立任意數量的CDA [!UICONTROL 虛擬報表套裝]。

### 重設歷史記錄

有時候，您的使用者需要一段時間才能登入，以及[!DNL Co-op Graph]或[!DNL Private Graph]才能識別他們，並將他們的裝置對應在一起。 CDA採用30天的回顧期間，可讓先前未識別的訪客在過去最多30天內重新聲明為人員。

這有什麼用？ 回想一下Isabelle從上述討論中的使用者歷程：

![[!DNL Cross-Device Analytics] 歷程](assets/cda-isabelle-journey-cross-device-analytics.png)

Isabelle直到購買前才登錄，而[!DNL Co-op Graph]或[!DNL Private Graph]直到購買後某個時間才將Isabelle的設備映射到一起。 但CDA的30天回顧讓CDA能夠重新描述伊莎貝爾在個人層面的過去行為，為您提供所需的跨裝置歷程視圖。

>[!NOTE]
>
>由於歷史記錄可以重列，這表示您的資料可能會在啟用CDA的[!UICONTROL 虛擬報表套裝]中隨著時間而變更。 傳達CDA型分析的深入分析時，請謹記這一點。

## [!UICONTROL 跨裝置分析]的必要條件

CDA隨[[!DNL Analytics Ultimate]](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)一起包含。 自2019年9月起，符合下列先決條件的[!DNL Analytics Ultimate]客戶即符合使用CDA的資格。 CDA的必要條件如下：

* 您的公司必須是[!DNL Adobe Experience Platform Identity Service] [[!DNL Co-op Graph]](https://experienceleague.adobe.com/docs/device-co-op/using/home.html)的成員，或使用[!DNL Adobe Experience Platform Identity Service Private Graph]。
* 您必須實作[!DNL Co-op Graph]或[!DNL Private Graph]所需的所有項目，包括[Experience CloudID(ECID)](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)以及與圖形同步的ID。 請注意，除技術要求外，[!DNL Co-op Graph]還有其他法律和合同要求。
* 目前無法搭配單一[!DNL Private Graph]使用兩個IMS組織，因此您必須標準化單一IMS組織。 在某些情況下，具有多個IMS組織的客戶可搭配CDA使用[!DNL Co-op Graph]。
* [!DNL Co-op graph]和[!DNL Private Graph]以及CDA的某些元件托管在[!DNL Microsoft Azure]中。 這表示[!DNL Analytics]資料會在Adobe的資料處理中心與Adobe在[!DNL Microsoft Azure]中的存在之間來回複製。 某些[!DNL Analytics]資料將儲存在[!DNL Azure]中。 貴公司必須同意這項安排。
* CDA需要「跨裝置」[!UICONTROL 報表套裝]。 也就是說，您用於CDA的[!UICONTROL 報表套裝]必須包含來自多種不同裝置類型或「曲面」（例如案頭網頁、行動網頁和行動應用程式）的資料。 自2019年9月起，此[!UICONTROL 報表套裝]的伺服器呼叫量必須為100MM/天或更短時間。 （未來幾個月，伺服器呼叫量限制將會增加。）
* 自2019年9月起，[!DNL Co-op Graph]和[!DNL Private Graph]僅在北美提供。 歐洲、中東和非洲地區及亞太地區的圖形顯示時間表將於未來宣佈。 如果您位於這些地區，建議您現在開始考量這些必要條件，以便在圖形可用時立即開始使用。

## 解譯跨裝置資料

### 不是訪客的人員

在CDA [!UICONTROL 虛擬報表套裝]中，您會看到一些變更。 例如，[!UICONTROL 獨特訪客]量度會取代為兩個新量度：[!UICONTROL People]和[!UICONTROL 不重複裝置]。 這些新量度可讓您更深入了解受眾規模。

*人員與不重複裝*
![置CDA [!UICONTROL 人員量度]](assets/cda-people-metric.png)

在[[!UICONTROL 區段產生器]](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=zh-Hant)中，[!UICONTROL 訪客]區段容器已由[!UICONTROL 人員]區段容器取代。 您可以使用CDA VRS建立跨裝置區段，例如：

* 使用多部裝置的使用者
* 在行動裝置上開始歷程，之後在桌上型電腦裝置上購買的人
* 人們使用多部裝置來完成工作的造訪

*人員層級區*
![[!DNL Segment Builder]  段PersonContainer](assets/cda-segment-builder-person-container.png)

### Dimension持續性

在CDA VRS中，[!DNL eVars]之類的維度現在會自動跨裝置持續存在。 例如，[!DNL eVar]設定為：

* 配置：最近（最後一個）
* 過期時間：購買

現在會自動從一部裝置持續到另一部裝置，直到引發購買事件為止。

## 在Analysis Workspace中分析跨裝置資料

### 以人員為基礎的受眾分析

您是否曾想過有多少人正在與您的品牌互動？ 您是否想要了解他們使用的裝置數量和類型？ 其使用量如何重疊？ 使用CDA VRS，您可以建立跨裝置[Venn圖表](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html?lang=zh-Hant)和每人裝置[色階分佈圖](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/histogram.html?lang=zh-Hant)。

*以人為基礎的受眾*
![分析Venn和色階分佈圖](assets/cda-venn-and-histogram.png)

### 跨裝置[!DNL Flow]

透過CDA和Analysis Workspace，您可以在[[!DNL Flow visualization]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)中將人們在不同裝置間移動的情形，隨著時間推移而視覺化。 你可以看到他們在旅程中的下場，以及他們的下場。

*[!DNL Flow]與CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 跨裝置[!DNL Fallout]

您可能會使用數個[[!DNL Fallout visualizations]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html?lang=zh-Hant)來分析使用者在成功前，透過一系列指定步驟所完成的進度。 您是否知道使用傳統的基於設備的分析時，您對這些[!DNL Fallout visualizations]的視圖有限？ 為了成功「落體」，下一個步驟必須發生在與上一個步驟相同的瀏覽器或應用程式中。 在以裝置為基礎的分析中，您不會看見在另一部裝置上成功完成下一個步驟的使用者。

別擔心，CDA給你包了。 CDA會建立讓[!DNL Fallout visualizations]更實用的跨裝置檢視。 畢竟，真正重要的是，這個人最終是否在某個地方成功完成了自己的任務。

*[!DNL Fallout]與CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

因為CDA會在Analysis Workspace下建立一層跨裝置資料，因此您的所有分析都會以跨裝置的觀點來調整。 有一個強大的範例是透過[[!DNL Attribution IQ]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/attribution/attribution.html?lang=zh-Hant)。 [!DNL Attribution IQ] Analysis Workspace可讓您並排比較多個歸因模型。透過CDA使用此功能，您現在可以比較不同裝置對成功的貢獻。

例如，假設您想要了解行動電話是互動中第一個最終導致成功的裝置的頻率。 這代表行動電話的「贏取率」。 CDA + [!DNL Attribution IQ]可讓您執行此分析：

*[!DNL Attribution IQ]與CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

如需詳細資訊，請參閱[[!DNL Cross-Device Analytics] 說明檔案](https://experienceleague.adobe.com/docs/analytics/components/cda/cda-home.html?lang=zh-Hant)。
