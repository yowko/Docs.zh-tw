---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394395"
---
### <a name="logging-debuglogger-class-made-internal"></a>記錄： DebugLogger 類別設為內部

在 ASP.NET Core 3.0 之前， `DebugLogger` 的存取修飾詞是 `public` 。 在 ASP.NET Core 3.0 中，存取修飾詞變更為 `internal` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

正在進行變更：

* 強制執行與其他記錄器執行的一致性，例如 `ConsoleLogger` 。
* 減少 API 介面。

#### <a name="recommended-action"></a>建議的動作

使用 <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` 擴充方法來啟用 debug 記錄。 <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> 也仍然 `public` 在事件中，必須以手動方式註冊服務。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
