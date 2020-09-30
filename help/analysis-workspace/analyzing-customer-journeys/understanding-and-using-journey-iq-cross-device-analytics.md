---
title: 瞭解和使用歷程IQ —— 跨裝置分析
description: 當使用者與您的品牌互動時，他們會以多種方式在多種裝置上進行互動。 跨裝置分析與Adobe Experience Platform Identity Service整合，以識別裝置如何對應至人。 然後，它運用這項智慧來建立使用者行為的跨裝置檢視。 這可讓您對人員進行分析，而非對裝置進行分析。
feature: cda
topics: null
audience: all
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
translation-type: tm+mt
source-git-commit: 24ad92b0ccdf1112e3ed4a0968cd47db757598c3
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 6%

---


# 瞭解和使用 [!DNL Journey IQ] -跨裝置分析

當使用者與您的品牌互動時，他們會以多種方式在多種裝置上進行互動。 跨裝置分析與整合，以 [!DNL Adobe Experience Platform Identity Service] 識別裝置如何對應至人。 然後，它運用這項智慧來建立使用者行為的跨裝置檢視。 這可讓您對人員進行分析，而非對裝置進行分析。

## 跨裝置分析概觀

### 我不是我的裝置

當使用者與您的品牌互動時，他們會以多種方式在多個「介面」或「裝置」上進行互動。 他們可能在PC或行動裝置上使用網頁瀏覽器，也可能使用行動應用程式。 在傳統的數位分析中，這些表面都以獨特的「訪客」表示。 這表示您的每個人類使用者都會被表示為多個獨特訪客。

範例如下. 假設Isabelle以下列方式與您的品牌互動：

*伊莎貝爾是三位傳統*![分析之旅的訪客](assets/cda-isabelle-journey-traditional-analytics.png)

伊莎貝爾的旅程用傳統的分析方法分為三部分。 她被表示為三個獨特訪客，每個訪客使用不同的裝置執行隔離的工作。 我們需要對Isabelle的互動進行統一、跨裝置的檢視。 [!DNL Journey IQ: Cross-Device Analytics] 提供此視圖。

*Isabelle是跨裝置*![分析之旅的一員](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨裝置檢視提供更佳的分析

以人為中心、跨裝置檢視Isabelle的行為，對您的分析可能有重大影響。 例如，傳統的訪客導向方法無法提供行銷管道有效性的完整說明。 讓我們再來看看Isabelle的歷程，重點瞭解哪個頻道可獲得她的產品檢視和購買的評分。 為了簡單起見  ，我們會使用上次接觸歸因，但是當您將Isabelle的行為分為不同的訪客時，使用任何歸因模型都會發生相同的問題。 使用傳統以訪客為基礎的世界檢視，會產生非常不同甚至誤導的結果：

*傳統Analytics與跨裝置Analytics通道歸因*![的比較](assets/channel-attribution.png)

請注意，透過跨裝置檢視，電子郵件渠道可同時獲得產品檢視和購買的評分，這更精確地代表Isabelle的實際體驗。

繼續閱讀以瞭解：

* How [!DNL Cross-Device Analytics] Works
* 的先決條件 [!DNL Cross-Device Analytics]
* 解讀跨裝置資料
* 分析工作區中的跨裝置資料

## How [!DNL Cross-Device Analytics] Works

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 與整合 [!DNL Adobe Experience Platform Identity Service]，使用[!DNL Co-op Graph] [，或](https://docs.adobe.com/content/help/zh-Hant/device-co-op/using/home.html)[!DNL Private Graph] 識別裝置對應人的方式。 然後，它運用這項智慧來建立使用者行為的跨裝置檢視。 CDA包含無人能及的功能和工具，可協助您的企業瞭解這些裝置與品牌互動時的多裝置使用情形和客戶體驗。 它位於分析工作區下方，可使用流失、 [!UICONTROL Fallout等強大工具，深入洞察以人為基礎的受眾分析以及跨裝置歸因、細分和歷程分]析 [!DNL Flow][!DNL Cohort][!DNL Segment IQ][!DNL Attribution IQ]。

### 此  [!DNL Cross-Device Virtual Report Suite]

CDA是透過一種特殊的跨裝置虛擬報表套 [[!UICONTROL 裝所呈現]](https://docs.adobe.com/content/help/zh-Hant/analytics/components/virtual-report-suites/vrs-about.html)。 這可讓您在組織中引入跨裝置分析時，繼續使用原始的裝置型報表套裝。 設定CDA VRS很簡單。

在其中一個VRS產生器步驟中，選 [!UICONTROL 擇由Adobe設定為] CDA啟用的報表套裝：

*選擇啟用CDA的基本（來源）報表套裝[!UICONTROL 虛擬報]*![ 表套裝步驟一](assets/cda-vrs-step-one.png)

然後開啟「 [!UICONTROL 報表時間處理] 」並啟 [!UICONTROL 用跨裝置拼接]:

*啟[!UICONTROL 用報表時間處理][!UICONTROL 和跨裝置聯繫虛擬]*![[!UICONTROL 報表] 套裝步驟二](assets/cda-vrs-step-two.png)

完成VRS設定並儲存。 CDA VRS會顯示在分析工作區中，旁邊會有特殊圖示，如下所示：

*在分析工作區中選取CDA VRS*![[!UICONTROL 虛擬報表套裝步驟] 3](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以在啟用CDA的基 [!UICONTROL 本報表套裝上] ，建立任意數量的CDA虛擬報 [!UICONTROL 表套裝]。

### 重設歷史

有時，您的使用者需要一段時間才能登入，以及為或 [!DNL Co-op Graph] 識別 [!DNL Private Graph] 他們，並將他們的裝置對應在一起。 CDA利用30天的回顧視窗，讓它可將先前未識別的訪客重新描述為過去最多30天的訪客。

這有什麼幫助？ 回想一下Isabelle從上述討論開始的使用者歷程：

![[!DNL Cross-Device Analytics] 旅程](assets/cda-isabelle-journey-cross-device-analytics.png)

Isabelle可能直到購買前才登入，而且購買後的某個時 [!DNL Co-op Graph] 間 [!DNL Private Graph] ，才會將Isabelle的裝置對應在一起。 但CDA的30天回顧讓CDA可以重述伊莎貝爾過去在個人層面的行為，為您提供您所需要的跨裝置歷程視圖。

>[!NOTE]
>
>由於歷史記錄可以重述，這表示您的資料可能會隨著時間在啟用CDA的虛擬報表套裝 [!UICONTROL 中變更]。 當您透過以CDA為基礎的分析傳達見解時，請記住這一點。

## 跨裝置分 [!UICONTROL 析的必要條件]

CDA隨附於 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)。 自2019年9月起， [!DNL Analytics Ultimate] 符合下列先決條件的客戶即有資格使用CDA。 CDA的先決條件如下：

* 您的公司必須是 [!DNL Adobe Experience Platform Identity Service] [!DNL合作 [圖]的成員](https://docs.adobe.com/content/help/zh-Hant/device-co-op/using/home.html)，或使用 [!DNL Adobe Experience Platform Identity Service Private Graph]。
* 您必須實作與圖形同 [!DNL Co-op Graph] 步所需 [!DNL Private Graph] 的一 [切，或包括Experience Cloud ID(ECID)](https://docs.adobe.com/content/help/zh-Hant/id-service/using/home.html) 和ID同步。 請注意，除了技術要求外，還有其 [!DNL Co-op Graph] 他法律和合同要求。
* 目前無法將兩個IMS組織與單一組織搭配使用， [!DNL Private Graph]因此您必須標準化單一IMS組織。 在某些情況下，擁有多個IMS組織的客戶可能會與CDA [!DNL Co-op Graph] 搭配使用。
* CDA [!DNL Co-op graph] 的 [!DNL Private Graph]和以及某些元件都托管在中 [!DNL Microsoft Azure]。 這表示 [!DNL Analytics] 資料會在Adobe的資料處理中心與Adobe的存在之間來回複製 [!DNL Microsoft Azure]。 有些 [!DNL Analytics] 資料會儲存在 [!DNL Azure]中。 貴公司必須同意此安排。
* CDA需要「跨裝置」報 [!UICONTROL 表套裝]。 也就是說，您用 [!UICONTROL 於CDA的報表套裝] ，必須包含來自多種不同裝置類型或「曲面」（例如案頭網頁、行動網頁和行動應用程式）的資料。 自2019年9月起，此報表套裝的伺服器 [!UICONTROL 呼叫量必須為] 100MM/天或更短。 （伺服器呼叫量限制將在未來數月增加。）
* 自2019年9月起， [!DNL Co-op Graph] 和僅 [!DNL Private Graph] 在北美地區提供。 圖形在EMEA和亞太地區的存在時間表將於未來宣佈。 如果您位於這些地區，我們鼓勵您現在開始考慮這些必要條件，以便您在圖形可用時做好準備。

## 解讀跨裝置資料

### 訪客而非訪客

在CDA虛擬 [!UICONTROL 報表套裝中]，您會看到一些變更。 例如，「獨特訪 [!UICONTROL 客] 」量度會由兩個新量度取代： [!UICONTROL 人物] 和 [!UICONTROL 獨特裝置]。 這些新量度可讓您更深入瞭解受眾規模。

*人員與獨特裝置*![CDA人 [!UICONTROL 員量度]](assets/cda-people-metric.png)

在「區 [[!UICONTROL 段產生器]](https://docs.adobe.com/content/help/zh-Hant/analytics/components/segmentation/segmentation-workflow/seg-build.html)」中，「訪客 [!UICONTROL 」區段容器已由「人員」區] 段容器取代。 使用CDA VRS，您可以建立跨裝置區段，例如：

* 使用多種裝置的使用者
* 在行動裝置上開始旅程，然後在桌上型裝置上購買的人
* 使用多個裝置完成工作的瀏覽

*人員層級區段*![[!DNL Segment Builder] 人員容器](assets/cda-segment-builder-person-container.png)

### 維持久性

在CDA VRS中，例如尺寸現在會 [!DNL eVars] 自動跨裝置持續存在。 例如，設 [!DNL eVar] 定為：

* 配置：最近（最後一個）
* 過期時間：購買

現在會自動從一個裝置持續存在另一個裝置，直到引發購買事件為止。

## 分析工作區中的跨裝置資料

### 基於人的受眾分析

您是否曾想過有多少人與您的品牌互動？ 您是否想要瞭解他們使用的裝置數量和類型？ 它們的使用如何重疊？ 使用CDA VRS，您可以建立跨裝置 [Venn圖](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/analysis-workspace/visualizations/venn.html) 和裝置的每人直方 [圖](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/analysis-workspace/visualizations/histogram.html)。

*基於人的受眾分析*![Venn和直方圖](assets/cda-venn-and-histogram.png)

### Cross-Device [!DNL Flow]

透過CDA和分析工作區，您可以在 [[!DNL流量視覺化]中，以視覺化方式呈現人們在不同裝置間的移動](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)。 你可以看到他們在旅程中的下場，以及他們的下場。

*[!DNL Flow]與CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### Cross-Device [!DNL Fallout]

您可能會使 [用數個[!DNL流失視覺化]](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html) ，分析使用者在成功之前，先透過一系列指定步驟完成的成效。 您是否知道使用傳統的裝 [!DNL Fallout visualizations] 置式分析時，對這些內容的檢視有限？ 為了成功「落體」，下一個步驟必須發生在與上一個步驟相同的瀏覽器或應用程式中。 在裝置分析中，您無法看到在其他裝置上成功完成下一步的人員。

別擔心，CDA有你的。 CDA會建立跨裝置檢視，讓 [!DNL Fallout visualizations] 它更有用。 畢竟，真正重要的是，這個人最終是否在某個地方成功完成了任務。

*[!DNL Fallout]與CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

由於CDA會在「分析工作區」下建立跨裝置資料層，所以您的所有分析都將採用跨裝置視角。 一個強大的例 [子是透過[!DNL Attribution IQ]](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)。 [!DNL Attribution IQ] 分析工作區中可讓您並排比較多個歸因模型。 您現在可以搭配使用此功能與CDA，比較不同裝置對成功的貢獻。

例如，假設您想瞭解行動電話是互動中第一個最終導致成功的裝置。 這代表行動電話的「贏取率」。 CDA +可 [!DNL Attribution IQ] 讓您執行以下分析：

*[!DNL Attribution IQ]與CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

For more information, see the [[!DNL Cross-Device Analytics] help documentation](https://docs.adobe.com/content/help/zh-Hant/analytics/components/cda/cda-home.html).
