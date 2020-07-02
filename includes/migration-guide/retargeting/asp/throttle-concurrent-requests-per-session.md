---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614325"
---
### <a name="throttle-concurrent-requests-per-session"></a>每一個工作階段的節流閥並行要求數目

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 和更早版本中，ASP.NET 會使用相同的 Sessionid 循序執行要求，且 ASP.NET 預設一律會透過 Cookie 發出 Sessionid。 如果頁面需要很長的時間來回應，則只要在瀏覽器上按<kbd>F5</kbd> ，就會大幅降低伺服器效能。 在修正程式中，我們新增了一個計數器來追蹤佇列要求，並在超過指定限制時終止要求。 預設值是 50。 如果達到限制，會在事件記錄檔記錄警告並在 IIS 記錄檔中記錄 HTTP 500 回應。

#### <a name="suggestion"></a>建議

若要還原舊行為，您可以將下列設定加入您的 web.config 檔案以選擇退出新行為。

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7         |
| 類型    | 正在重定目標 |
