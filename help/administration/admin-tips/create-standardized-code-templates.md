---
title: 建立標準化代碼模板
description: '對於基準實施(即您的公司認為所有Adobe Analytics站點必備的KPI)，您的組織應盡可能採用單一實施方法。 '
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10532.jpg
kt: 10532
source-git-commit: 160df6c23acb67f1b07f2fcd25f1eca96eb6dee7
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 2%

---


# 建立標準化代碼模板

**什麼：** 對於「基線」實施(即您的公司認為所有Adobe Analytics站點的必備KPI)，您的組織應盡可能採用單一實施方法。 例如，跨站點使用相同的資料層結構，並利用相同的標籤管理器規則/自定義代碼捕獲內部搜索或訪問者配置檔案資訊等內容。

**原因：** 擁有可重複且可擴展的基準實施，可以簡化、減少工作量，同時保持實施乾淨且易於排除故障。 使用統一的方法還使新管理員/開發人員更容易聯機並瞭解他們正在處理什麼。

**方式：** 在新站點或標籤增強功能上線時，採用單一格式模板向開發人員分發。 通常，word doc在以下項目中可以概述，這些功能非常有效：

* 正在實現的變數、其目的以及何時設定。 例如：

| AA變數 | 說明 | 設定時間/位置 | 如何設定 |
|--- |--- |--- |--- |
| eVar8 | 內部搜尋關鍵字 | 在內部搜索結果頁面登錄時 | 資料層 |
| 事件8 | 內部搜索計數 | 在內部搜索結果頁面登錄時 | 啟動規則 |

* 詳細說明如何設定。 在此處，您將指定所需的任何資料層對象及其語法，以及需要配置的任何TMS規則和規則設定的詳細資訊。
* 要確保的test案例在QA和您希望在成功的test案例中看到的所有變數中都有所介紹。 概述當開發人員test此增強時成功實施應包括的內容。

理想情況下，您只需對此文檔進行微調，以便您在下一個站點更新基本資訊，如屬性名稱、頁面命名約定等。 不必每次都重新發明車輪，這樣可以節省更多時間。

## 作者

本文由以下人士共同撰寫：

![克里斯特爾·吉東](assets/Christel-Headshot-150.png)

Christel Guidon , NortonLifeLockAdobe Analytics冠軍的數字分析平台經理

![瑞秋·芬威克](assets/Rachel-Fenwick-150.png)

Rachel Fenwick,Adobe高級顧問
