---
title: 使用Experience Platform SDK的行動應用程式中的追蹤動作（亦即自訂連結）
description: '動作是發生在您行動應用程式中的事件。 在此影片中，瞭解如何使用trackAction API來追蹤和測量動作。 '
feature: mobile sdk
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
translation-type: tm+mt
source-git-commit: a42658cfd4bae7b077ddd48b4cf5c7db54e35c98
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# 使用Experience Platform SDK的行動應用程式中的追蹤動作（亦即自訂連結） {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

動作是發生在您行動應用程式中的事件。 在此影片中，瞭解如何使用trackAction API來追蹤和測量動作。

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12)

這是您應用來追蹤網站上所有非螢幕載入動作的API。 如果畫面即將出現，則使用trackState，它會觸發頁面檢視點擊。 否則，請使用trackAction傳送與正在發生之動作相關的變數。

這些資料的傳入 `contextData`方式也表示，您接著需要使用「處理規則」來提取這些變 [!UICONTROL 數中的行動資料，並將其對應] 至、 `contextData`[!DNL eVars][!DNL Props]事件等。 在Adobe Analytics中。

如需trackAction的詳細資訊，請參閱文 [件](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference)。
