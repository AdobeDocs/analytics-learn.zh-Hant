---
title: 提升效率和自助服務的簡單技巧 - 第 1 部分
description: 了解分析團隊現今面臨的主要挑戰，以及我們對於在 Adobe Analytics UI 外部使用策略來克服這些挑戰的建議。
feature: Analytics Basics
role: Admin, Leader
level: Intermediate
solution: Analytics
exl-id: 5d1077fd-d006-4a85-bf1c-54f6b2d31934
TQID: https://experienceleague.adobe.com/tavjm7si5M73xvfMYmKLLCk6-c3Epjgv2oUtZiklnGE
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
feature_v2:
  - id: a421fb65-2c82-457a-921c-28c46b697a39
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 677e5a22dab92be7ff021c8410525b9091975aef
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 94%

---

# Adobe Analytics：提升效率和自助服務的簡單技巧

**第 1 部分：在 UI 外部**

本文介紹分析團隊現今面臨的主要挑戰，以及我們對於在 Adobe Analytics 介面外部使用策略來克服這些挑戰的的建議。

## Analytics 團隊面臨的主要挑戰

許多 Analytics 團隊發現自己的工作分配不平衡。 很多組織發現自己並非處於 80% 分析搭配 20% 實施，而是相反。 他們發現大部分精力都花在建立、報告和提供支援上，而不是進行分析以推動高價值的洞察。

Analytics 團隊發現他們的生產力和效率被各種原因消耗殆盡。 其中包括不斷變化和不斷發展的實施、讓組織維持信任資料，以及減少分析人員流動。 減少人員流動，就不用重複訓練新團隊成員熟悉自訂實施工具的漫長過程。

分析人員面臨的其他主要挑戰：

* **競爭：**&#x200B;線上和多通路零售業務越來越具備競爭力。
* **客戶期望：**&#x200B;客戶體驗和行銷策略越來越複雜。
* **資料價值：**&#x200B;推動競爭優勢的精準資料和洞察的價值越來越重要。
* **利害關係人的期望：**&#x200B;業務合作夥伴、利害關係人和高階主管在核准之前，對於資料提供的要求越來越高。
* **專案管理：**&#x200B;分析團隊忙於為永無止境的新功能請求收集資料，同時還要產生準確的報告、協助新分析人員上任，以及發表新洞察。

## 效率的關鍵：在 UI 外部

1. 讓您的[解決方案設計參考](/help/implementation/implementation-basics/creating-and-maintaining-an-sdr.md) (SDR) 保持在最新狀態：

   * SDR 是分析實施中所有變數的定義和預期用途的主要信任來源。
   * SDR 是使用者必須熟悉的主要參考資料，以便從您的 Adobe Analytics UI 中取得價值。
   * 保持在最新狀態和建立版本 (可以使用簡單的日期格式) 很重要。

1. 資料彙集文件和治理 - 技術規格：

   與 SDR 相比，技術規格的客群較受限，但對於完整功能的實施，也同樣重要。 一個良好的技術規格，應該包含實施解決方案所需的一切開發、QA 和標記管理資源。 請務必盡量加入適應獨特實施架構所需的一切文件。

   **技術規格**

   使用案例&#x200B;:_說明如何建構資料收集的指令碼(_U)

   主要使用者&#x200B;:_開發人員(_P)

   其他附註(_O):_

   * 專為您的部署環境建構的高等技術文件
   * 對初始實施和後續維護/參考都很有用
   * 依解決方案類型分組 (例如行銷活動追蹤、頁面中繼資料等)。
   * 進行 SDR 變更時，需要更新和維護主要文件
   * 中央存放庫
   * SDR 和技術規格的同步版本編號

1. 在發佈時傳達和記載解決方案設計意圖：

   * 與使用者進行溝通
   * 在發佈或增強資料彙集時，建立可與利害關係人分享的簡單摘要
   * 加強正確的變數使用
   * 傳送摘要發佈公告電子郵件給主要利害關係人和分析人員
   * 建立可支援辦公時間、團隊啟用工作階段或團隊特定入職的資料庫

1. 資料彙集文件、控管和資料檢疫 - AHD：

   Analytics 健全儀表板 (AHD) 深入探究&#x200B;_單一_&#x200B;報告套裝，並提供每個元件 (eVar、prop 和 event) 中所收集資料的檢視。 這可協助指出是否已停止收集資料到元件中，讓您可以採取動作來更正問題。 您稍後隨時可以為任何報告套裝執行此儀表板。

   Analytics 健全儀表板 (AHD)：

   單一報表套裝擷取的每個量度和維度的使用案例&#x200B;:_快照(_U)

   主要使用者&#x200B;:_領導Analytics SME和/或開發人員(_P)

   其他附註(_O):_
   * 使用 Adobe Reporting API 的自訂整合透過 Excel 傳遞
   * 使用者必須具備 Analytics Web 服務 API 存取權
   * 具有半自動化選項

1. 透過擴大主題專家 (SME) 的領域來取勝：

   * 在組織的各個團隊中建立 SME
   * 透過協助社交發佈和獲勝來建立其存在感
   * 利用正常的辦公時間來協助培訓訓練人員並減少臨時要求

在[客戶成功](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html)中心了解更多策略和構想領導力。