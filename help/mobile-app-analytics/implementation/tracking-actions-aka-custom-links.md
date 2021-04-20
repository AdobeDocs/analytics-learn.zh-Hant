---
title: 透過 Experience Platform SDK 追蹤行動應用程式內的行動 (又稱客戶連結)
description: '動作是指行動應用程式中發生的事件。在本影片中，了解如何使用 trackAction API 來追蹤和衡量一項動作。 '
feature: Mobile SDK
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: Mobile
role: "Developer, Data Engineer"
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
translation-type: ht
source-git-commit: 5dead486510dd74b7f6a04848ecd7dc03267958f
workflow-type: ht
source-wordcount: '177'
ht-degree: 100%

---

# 透過 Experience Platform SDK 追蹤行動應用程式內的動作 (又稱客戶連結) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

動作是指行動應用程式中發生的事件。在本影片中，了解如何使用 trackAction API 來追蹤和衡量一項動作。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12)

您應該使用此 API 來追蹤網站上的所有非螢幕載入動作。如果螢幕即將顯示，請使用 trackState (這將觸發頁面檢視點閱)。否則，請使用 trackAction 發送與正在執行的動作有關聯的變數。

這項資料會以 `contextData` 傳入，這也表示您將需要使用[!UICONTROL 處理規則]從這些`contextData` 變數取得行動資料，並對應至 Adobe Analytics 中的 [!DNL eVars]、[!DNL Props]、事件等。。

如需 trackAction 的詳細資訊，請參閱本[文件](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference)。
