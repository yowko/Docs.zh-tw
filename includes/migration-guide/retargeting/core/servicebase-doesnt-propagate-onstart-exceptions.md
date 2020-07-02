---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614369"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase 不會傳播 OnStart 例外狀況

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7 和更早版本中，在服務啟動時擲回的例外狀況不會傳播至 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> 的呼叫端。<br/>從 .NET Framework 4.7.1 為目標的應用程式開始，執行階段會為無法啟動的服務將例外狀況傳播到 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>。

#### <a name="suggestion"></a>建議

在服務啟動時，如果有例外狀況，將會傳播該例外狀況。 這應該有利於診斷服務無法啟動的情況。 <br/>如果不需要此行為，您可以在應用程式組態檔的 &lt;runtime&gt; 區段中新增以下 &lt;AppContextSwitchOverrides&gt; 元素，以選擇退出：

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

如果您的應用程式以比 4.7.1 舊的版本為目標，但您想要有這種行為，請在應用程式設定檔的 &lt;runtime&gt; 區段中新增以下 &lt;AppContextSwitchOverrides&gt; 元素：

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
