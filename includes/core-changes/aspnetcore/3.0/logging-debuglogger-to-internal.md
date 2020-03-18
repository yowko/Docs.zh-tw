---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394395"
---
### <a name="logging-debuglogger-class-made-internal"></a>日誌記錄：調試記錄器類是內部製作的

在 ASP.NET Core 3.0 之前，`DebugLogger`訪問修改`public`器為 。 在 ASP.NET 核心 3.0 中，訪問`internal`修改器更改為 。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>更改原因

正在作出以下更改：

* 強制與其他記錄器實現（如`ConsoleLogger`） 保持一致。
* 減少 API 表面。

#### <a name="recommended-action"></a>建議的動作

<xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`使用擴充方法啟用調試日誌記錄。 <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>如果服務需要`public`手動註冊，則仍處於此情況。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
