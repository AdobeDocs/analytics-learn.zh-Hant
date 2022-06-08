---
title: 建立標準化命名約定
description: 在AA Admin UI中啟用時，標準命名約定將同時應用於變數名稱本身和傳遞到維的值。
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10531.jpg
kt: 10531
source-git-commit: 160df6c23acb67f1b07f2fcd25f1eca96eb6dee7
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 建立標準化命名約定

**什麼：** 在Adobe Analytics(AA)管理員UI中啟用時，標準化命名約定適用於變數名稱本身以及傳遞到維的值。 (即頁名將是&quot;頁名(v1)&quot;作為變數名，傳入的頁名值應一致，並遵循特定的結構/層次結構，如&quot;sitename|homepage&quot;或&quot;sitename|search|searchresults&quot;)。

**原因：** 命名約定是保持所有內容均一併保持介面易於用戶理解的絕佳方法。 如果您從頭開始建立這些元件，並在平台和代碼中強制執行，則這些元件將更容易擴展。

**方式：** 介面和標籤文檔應該與「名稱」和「說明」匹配 — 這樣，您的用戶就不必拉出Excel文檔，而可以直接在介面中瞭解您的資料。 還建議保持所有更低的一致性。

始終最好保持跨平台的頁名一致（或應用程式的螢幕名）。 例如，可以設定「property」:section:子節：子節：唯一頁名&quot;到變數/維中。 如果所有這些欄位都是資料層中單獨的欄位，您甚至可以直接在JS檔案/啟動中生成頁名。 將所有這些元素都設定在它們自己的維中，也可以幫助您更輕鬆地分解站點/應用的特定屬性或區域，並更好地瞭解流量和流。

任何能讓用戶更容易查找和理解資料的內容，包括諸如命名慣例之類的簡單內容，都將增加Adobe Analytics的使用，並為企業提供更好的見解。

## 作者

本文由以下人士共同撰寫：

![克里斯特爾·吉東](assets/Christel-Headshot-150.png)

Christel Guidon , NortonLifeLockAdobe Analytics冠軍的數字分析平台經理

![瑞秋·芬威克](assets/Rachel-Fenwick-150.png)

Rachel Fenwick,Adobe高級顧問
