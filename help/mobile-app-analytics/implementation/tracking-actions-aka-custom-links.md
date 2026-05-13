---
title: 透過 Experience Platform SDK 追蹤行動應用程式內的行動 (又稱客戶連結)
description: 動作是指行動應用程式中發生的事件。 在本影片中，了解如何使用 trackAction API 來追蹤和衡量一項動作。
feature: Mobile SDK
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: Mobile
role: Developer
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
TQID: https://experienceleague.adobe.com/msvft7mQiNGjLqGEezPIbwruvSbsunPGUIFF1q7vlT0
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 677e5a22dab92be7ff021c8410525b9091975aef
workflow-type: tm+mt
source-wordcount: 184
ht-degree: 73%

---

# 透過 Experience Platform SDK 追蹤行動應用程式內的行動 (又稱客戶連結) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

動作是指行動應用程式中發生的事件。 在本影片中，了解如何使用 trackAction API 來追蹤和衡量一項動作。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12&learn=on)

您應該使用此 API 來追蹤網站上的所有非螢幕載入動作。 如果螢幕即將顯示，請使用 trackState (這將觸發頁面檢視點閱)。 否則，請使用 trackAction 發送與正在執行的動作有關聯的變數。

此資料以`contextData`的形式提供，這也表示您需要使用[!UICONTROL 處理規則]來從這`contextData`個變數取得行動資料，並將其對應到Adobe Analytics中的[!DNL eVars]、[!DNL Props]、事件等等。

如需 trackAction 的詳細資訊，請參閱本[文件](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/#track-user-actions-for-adobe-analytics)。
