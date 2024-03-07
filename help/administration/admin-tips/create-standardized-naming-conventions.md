---
title: 建立標準化的命名慣例
description: 標準化的命名慣例適用於變數名稱本身 (在 AA 管理員 UI 中啟用時) 以及傳遞到維度的值。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10531.jpg
kt: 10531
exl-id: 0fe3b981-0d9b-4f12-a6ca-63a4140f4baf
source-git-commit: 54f9d15d705cd2d9dfa0fb177d14e2e602e35b7c
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 80%

---

# 建立標準化的命名慣例

**主題：**&#x200B;標準化的命名慣例適用於變數名稱本身 (在 Adobe Analytics (AA) 管理員 UI 中啟用時) 以及傳遞到維度的值。 (也就是頁面名稱會以「頁面名稱 (v1)」作為變數名稱，而傳入的頁面名稱值應該是統一的且遵循特定的結構/階層，例如「sitename|homepage」或「sitename|search|searchresults」)。

**理由：**&#x200B;命名慣例是保持一切項目統一，並讓使用者容易了解介面的好方法。 如果您從一開始就建立慣例並在平台和程式碼中強制執行，會比較容易規模化。

**做法：** 介面和標籤檔案應同時符合「名稱」和「說明」 — 這讓您的使用者無須提取Excel檔案，並能在介面中直接理解您的資料。 此外也建議所有內容採用小寫，以維持一致性。

最好在整個平台上保持頁面名稱一致（或應用程式的熒幕名稱）。 例如，您可以設定 `property:section:sub section:sub sub section:unique page name` 變數/維度。 如果以上這些都是資料層中的單獨欄位，您甚至可以直接在 JS 檔案/Launch 中建置頁面名稱。 將所有這些元素都設定在其本身的維度中，可協助您更輕鬆地劃分網站/應用程式的特定屬性或區域，以及更加了解流量。

可讓使用者更容易找到和理解資料的任何措施，包括命名慣例這樣簡單的項目，都能提高 Adobe Analytics 的使用率，也能為企業提供更好的深入分析。

## 作者

本文的共同作者為：

![Christel Guidon](assets/Christel-Headshot-150.png)

NortonLifeLock 數位分析平台經理 Christel Guidon
Adobe Analytics 達人

![Rachel Fenwick](assets/Rachel-Fenwick-150.png)

Adobe 資深顧問 Rachel Fenwick
