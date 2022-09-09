---
title: 了解並使用 Journey IQ - 跨裝置分析
description: 使用者與您的品牌互動時，他們會以許多方式在多種裝置上進行互動。跨裝置分析會整合 Adobe Experience Platform 身份識別服務，以識別多少部裝置對應到使用者。然後運用此情報建立使用者行為的跨裝置檢視。如此便能夠對使用者進行分析，而非對裝置。
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: User
level: Intermediate
exl-id: 3748d5d7-d250-4057-8131-afdc66c80200
source-git-commit: 01e6e84f748e359aeb42c9be3afa52088f41018b
workflow-type: ht
source-wordcount: '1529'
ht-degree: 100%

---

# 了解並使用 [!DNL Journey IQ] - 跨裝置分析

使用者與您的品牌互動時，他們會以許多方式在多種裝置上進行互動。跨裝置分析會整合 [!DNL Adobe Experience Platform Identity Service]，以識別多少部裝置對應到使用者。然後運用此情報建立使用者行為的跨裝置檢視。如此便能夠對使用者進行分析，而非對裝置。

## 跨裝置分析總覽

### 我不是我的裝置

使用者與您的品牌互動時，他們會以許多方式在多種「表面」或「裝置」上進行互動。他們可能使用 PC 或行動裝置上的網頁瀏覽器，或使用行動應用程式。在傳統的數位分析中 (資料彙集根據 Cookie 成長)，每個表面都是以不重複「訪客」表示。這表示您的每位人類使用者都是以多個不重複訪客表示。

範例如下。假設 Isabelle 透過下列方式與您的品牌互動：

*Isabelle 是三位訪客*
![傳統分析歷程](assets/cda-isabelle-journey-traditional-analytics.png)

透過傳統分析，Isabelle 的歷程可以分成三部分。她以三位不重複訪客表示，每位都使用不同裝置執行分離的任務。所需的是統一跨裝置檢視 Isabelle 的互動。[!DNL Journey IQ: Cross-Device Analytics] 提供此檢視。

*Isabelle 是一個人*
![跨裝置分析歷程](assets/cda-isabelle-journey-cross-device-analytics.png)

### 跨裝置檢視提供更佳的分析

取得 Isabelle 行為以人為中心的跨裝置檢視後，即可讓您的分析產生巨大差異。例如，傳統以訪客為基礎的方法無法呈現行銷頻道有效性的完整面貌。接著再次查看 Isabelle 的歷程，著重於哪個頻道收到其產品檢視和購買的點數。為了簡化，我們將使用[!UICONTROL 上次接觸]歸因，但當您將 Isabelle 的行為分成多個個別訪客時，使用任何歸因模式都會發生相同的問題。使用傳統以訪客為基礎的世界檢視會產生非常不同，甚至是誤導的結果：

*傳統分析與跨裝置分析*
![頻道歸因](assets/channel-attribution.png)

請注意，有了跨裝置檢視，電子郵件頻道會收到產品檢視和購買的點數，藉以更準確地呈現 Isabelle 的真實世界體驗。

請繼續閱讀，以深入了解：

* [!DNL Cross-Device Analytics]的運作方式
* [!DNL Cross-Device Analytics]的先決條件
* 解讀跨裝置資料
* 分析 Analysis Workspace 中的跨裝置資料

## [!DNL Cross-Device Analytics]的運作方式

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 會和 [!DNL Adobe Experience Platform Identity Service] 整合，並利用 [!DNL Device Graph] 來辨識裝置與使用者的對應方式。然後運用此情報建立使用者行為的跨裝置檢視。CDA 包含無與倫比的功能和工具，有助於您的企業了解多個裝置的使用情況，以及在其與您的品牌互動過程中，橫跨這些裝置的客戶體驗。它作為 Analysis Workspace 下方的圖層，使用如[!UICONTROL 流失]、[!DNL Flow]、[!DNL Cohort]、[!DNL Segment IQ]及[!DNL Attribution IQ]等強大工具，提供深入的個人型對象分析和跨裝置歸因、細分和歷程分析見解。

### 此 [!DNL Cross-Device Virtual Report Suite]

CDA 透過特殊類型的跨裝置[[!UICONTROL 虛擬報告套裝]](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=zh-Hant)提出。這可讓您在將跨裝置分析導入您的組織時，繼續使用以原始裝置為基礎的報告套裝。CDA VRS 的設定很容易。

在 VRS 產生器的步驟 1，請選擇已由 Adobe 設為啟用 CDA 的[!UICONTROL 報告套裝]：

*選擇啟用 CDA 的基底 (來源) [!UICONTROL 報告套裝]*
![[!UICONTROL 虛擬報告套裝]步驟 1](assets/cda-vrs-step-one.png)

然後開啟[!UICONTROL 報告時間處理]並啟用[!UICONTROL 跨裝置銜接]：

*啟用[!UICONTROL 報告時間處理]和[!UICONTROL 跨裝置銜接]*
![[!UICONTROL 虛擬報告套裝]步驟 2](assets/cda-vrs-step-two.png)

完成 VRS 設定並儲存。CDA VRS 將在 Analysis Workspace 中顯示，旁邊會出現特殊圖示，如下所示：

*在 Analysis Workspace 中選取 CDA VRS*
![[!UICONTROL 虛擬報告套裝]步驟 3](assets/cda-vrs-step-three.png)

>[!TIP]
>
>您可以在啟用 CDA 基底[!UICONTROL 報告套裝]上方，建立任意數量的 CDA [!UICONTROL 虛擬報告套裝]。

### 重述記錄

有時您的使用者需要一些時間才能登入，而 [!DNL Device Graph] 也需要一些時間才能辨識他們，並將他們與其裝置對應在一起。CDA 利用 30 天回溯視窗，以便將之前未識別的訪客重述為過去最長 30 天內的個人。

此做法如何協助？從以上討論中回想 Isabelle 的使用者歷程：

![[!DNL Cross-Device Analytics] 歷程](assets/cda-isabelle-journey-cross-device-analytics.png)

Isabelle 可能直到進行購買前才登入，而且 [!DNL Device Graph] 直到 Isabelle 購買後的一段時間，才將她和她的裝置對應在一起。但 CDA 的 30 天回溯可讓 CDA 以個人層級重述 Isabelle 的過去行為，提供您所需的跨裝置歷程檢視。

>[!NOTE]
>
>由於可以重述記錄，因此這表示您的資料在啟用 CDA 的[!UICONTROL 虛擬報告套裝]中可能隨著時間變更。 當您傳達以 CDA 為基礎的分析的深入見解時，請將此謹記在心。

## [!UICONTROL 跨裝置分析]的先決條件

CDA 包含在 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-analytics.html) 內。自 2019 年 9 月起，符合下列先決條件的 [!DNL Analytics Ultimate] 客戶即符合使用 CDA 的資格。CDA 的先決條件如下所示：

* 您的公司必須使用 [!DNL Adobe Experience Platform Identity Service Device Graph]。
* 您必須實作 [!DNL Device Graph] 所需的一切，包括 [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant) 以及與圖表同步的 ID。
* 目前無法將兩個 IMS 組織與單一 [!DNL Device Graph] 搭配使用，因此您必須在單一 IMS 組織上進行標準化。
* [!DNL Device Graph] 以及 CDA 的某些元件都在 [!DNL Microsoft Azure] 中託管。這表示 [!DNL Analytics] 資料會在 Adobe 的資料處理中心與 Adobe 在 [!DNL Microsoft Azure] 的存在之間來回複製。部分 [!DNL Analytics] 資料將儲存於 [!DNL Azure]。貴公司必須同意此安排。
* CDA 需要使用「跨裝置」[!UICONTROL 報告套裝]。換言之，您用於 CDA 的[!UICONTROL 報告套裝]必須包括來自於多部不同裝置類型或「表面」(例如桌面網頁、行動網頁、行動應用程式) 的資料。截至 2019 年 9 月，此[!UICONTROL 報告套裝]的伺服器呼叫量必須為每天 100MM 筆伺服器呼叫或更少。(伺服器呼叫量限制將在未來數月增加。)

## 解讀跨裝置資料

### 不是訪客的使用者

在 CDA [!UICONTROL 虛擬報告套裝]中，您會見到一些變動。例如，「[!UICONTROL 不重複訪客]」量度已被兩個量度取代：「[!UICONTROL 使用者]」和「[!UICONTROL 不重複裝置]」。這些新量度能讓您更深入分析對象規模。

*使用者和不重複裝置*
![CDA [!UICONTROL 使用者量度]](assets/cda-people-metric.png)

在「[[!UICONTROL 區段產生器]](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=zh-Hant)」中，「[!UICONTROL 訪客]」區段容器已被「[!UICONTROL 使用者]」區段容器取代。您可以使用 CDA VRS 建立跨裝置區段，例如：

* 不只使用一部裝置的使用者
* 開始在行動裝置展開歷程，然後在桌面裝置上購買的使用者
* 使用者不只使用一部裝置完成任務的造訪

*個人層級區段*
![[!DNL Segment Builder] [!UICONTROL 個人]容器](assets/cda-segment-builder-person-container.png)

### 維度持續性

在 CDA VRS 中，如 [!DNL eVars] 的維度會自動跨裝置持續存在。 例如，[!DNL eVar] 設為：

* 配置：最近 (上次)
* 有效期限：購買

現在將自動從一部裝置持續存在到另一部裝置，直到引發購買事件為止。

## 分析 Analysis Workspace 中的跨裝置資料

### 個人化對象分析

您是否曾想過有多少人正在與您的品牌互動？您是否想要了解他們使用多少裝置及裝置類型？他們的使用情況如何重疊？您可以使用 CDA VRS 建立跨裝置[文氏圖表](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html?lang=zh-Hant)和每人裝置數[長條圖](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/histogram.html?lang=zh-Hant)。

*個人化對象分析*
![文式圖表和長條圖](assets/cda-venn-and-histogram.png)

### 跨裝置[!DNL Flow]

您可以使用 CDA 和 Analysis Workspace 在 [[!DNL Flow visualization]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/flow/flow.html?lang=zh-Hant) 中用視覺方式呈現使用者使用者如何隨著時間從一部裝置移至另一部裝置。您可以查看他們在哪處推出其歷程，以及在哪處繼續進行。

*[!DNL Flow]使用 CDA*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 跨裝置[!DNL Fallout]

您可能會使用數個 [[!DNL Fallout visualizations]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html?lang=zh-Hant) 分析使用者在成功達成前透過指定的一系列步驟成功達成的機率。您是否知道這些 [!DNL Fallout visualizations] 的檢視在使用以傳統裝置為基礎的分析時會受到限制？為了成功「通過」，下一個步驟必須在跟上一步中所使用的相同瀏覽器或應用程式中發生。在以裝置為基礎的分析中，您不會知道成功在另一部裝置上完成下一步的使用者。

不用擔心，CDA 已為您設想到這點。CDA 會建立跨裝置檢視，使 [!DNL Fallout visualizations] 變得更為實用許多。畢竟真正重要的是，使用者最終是否在某處成功完成其任務。

*[!DNL Fallout]使用 CDA*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

由於 CDA 會在 Analysis Workspace 下方建立跨裝置資料圖層，因此您的所有分析將多了跨裝置觀點。一個有力的範例就是透過 [[!DNL Attribution IQ]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/attribution/attribution.html?lang=zh-Hant)。Analysis Workspace 中的 [!DNL Attribution IQ] 可讓您並排比較多個歸因模式。您可以使用此 CDA 功能，比較不同裝置對於成功購買的貢獻度。

例如，假設您想要了解行動電話多常在最終成功購買的互動中作為第一個使用的裝置。這以行動電話的「贏取率」表示。CDA + [!DNL Attribution IQ] 可讓您進行此分析：

*[!DNL Attribution IQ]使用 CDA*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

如需詳細資訊，請參閱[[!DNL Cross-Device Analytics] 說明文件](https://experienceleague.adobe.com/docs/analytics/components/cda/cda-home.html?lang=zh-Hant)。
