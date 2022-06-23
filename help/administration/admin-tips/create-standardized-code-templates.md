---
title: 建立標準化的程式碼範本
description: 對於基準線實施 (亦即貴公司認為所有 Adobe Analytics 網站必備的 KPI)，貴組織應盡可能採用單一實施方法。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10532.jpg
kt: 10532
exl-id: be00c8c0-a4bc-4380-98da-d1e2a3d31ec5
source-git-commit: df00d4fb8cc5093903ed4628dfe12f152294123a
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---

# 建立標準化的程式碼範本

**主題：**&#x200B;對於「基準線」實施 (亦即貴公司認為所有 Adobe Analytics 網站必備的 KPI)，貴組織應盡可能採用單一實施方法。 例如，跨網站使用相同的資料層結構，以及運用相同的標籤管理程式規則/自訂程式碼來擷取內部搜尋或訪客資料資訊此類內容。

**理由：**&#x200B;擁有可重複且可擴展的基準線實施，能簡化新增新元素或新網站/應用程式的工作，同時保持實施整潔且易於疑難排解。 使用統一的方法，還能讓新的管理員/開發人員更容易上線並了解他們正在使用的內容。

**做法：**&#x200B;採用單一格式範本，在新網站或標記增強功能上線時交給開發人員。 通常，Word 文件就很好用了，您可以在其中概述以下項目：

* 實施的變數、變數的用途以及何時設定。 例如：

| AA 變數 | 說明 | 何時/何處設定 | 如何設定 |
|--- |--- |--- |--- |
| eVar8 | 內部搜尋關鍵字 | 登陸內部搜尋結果頁面時 | 資料層 |
| event8 | 內部搜尋計數 | 登陸內部搜尋結果頁面時 | Launch 規則 |

* 如何設定的詳細說明。 您可以在此處指定所需的任何資料層物件及其語法，以及任何需要設定的 TMS 規則和規則設定的詳細資料。
* QA 中涵蓋要確保的測試案例，以及您希望在成功的測試案例中看到的所有變數。 概述當開發人員測試此增強功能時，成功實施應包括的內容。

理想情況下，此文件只需針對下一個網站進行調整，您可以更新屬性名稱、頁面命名慣例等基本知識。 不用每次都重複相同的步驟，就能節省更多時間。

## 作者

本文的共同作者為：

![Christel Guidon](assets/Christel-Headshot-150.png)

NortonLifeLock 數位分析平台經理 Christel Guidon
Adobe Analytics 達人

![Rachel Fenwick](assets/Rachel-Fenwick-150.png)

Adobe 資深顧問 Rachel Fenwick
