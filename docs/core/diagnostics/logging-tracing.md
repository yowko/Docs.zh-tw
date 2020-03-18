---
title: 日誌記錄和跟蹤 - .NET 核心
description: .NET 核心日誌記錄和跟蹤簡介。
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714415"
---
# <a name="net-core-logging-and-tracing"></a>.NET 核心日誌記錄和跟蹤

日誌記錄和跟蹤實際上是同一技術的兩個名稱。 這種簡單的技術從電腦的早期就被使用。 它只需檢測應用程式以寫入以後使用的輸出。

## <a name="reasons-to-use-logging-and-tracing"></a>使用日誌記錄和跟蹤的原因

這個簡單的技術是驚人的強大。 它可用於調試器失敗的情況：

- 長時間出現問題，使用傳統調試器可能很難調試。 日誌允許長時間進行詳細的事後審查。 相反，調試器受限制為即時分析。
- 多執行緒應用程式和分散式應用程式通常難以調試。  附加調試器往往會修改行為。 可以根據需要分析詳細的日誌，以瞭解複雜的系統。
- 分散式應用程式中的問題可能來自許多元件之間的複雜交互，將調試器連接到系統的每個部分可能不合理。
- 許多服務不應停滯。 附加調試器通常會導致超時失敗。
- 問題並不總是被預見到的。 日誌記錄和跟蹤專為低開銷而設計，以便在出現問題時始終可以記錄程式。

## <a name="net-core-apis"></a>.NET 核心 API

### <a name="print-style-apis"></a>列印樣式 API

各<xref:System.Console?displayProperty=nameWithType><xref:System.Diagnostics.Trace?displayProperty=nameWithType>各<xref:System.Diagnostics.Debug?displayProperty=nameWithType>各提供便於日誌記錄的類似列印樣式 API。

選擇使用哪種列印樣式 API 由您決定。 主要差異包括：

- <xref:System.Console?displayProperty=nameWithType>
  - 始終啟用並始終寫入主控台。
  - 對於您的客戶可能需要在版本中看到的資訊非常有用。
  - 因為它是最簡單的方法，它通常用於臨時臨時調試。 此調試代碼通常從未簽入到原始程式碼。
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - 僅在定義時`TRACE`啟用。
  - 預設情況下，寫入<xref:System.Diagnostics.Trace.Listeners>附加的<xref:System.Diagnostics.DefaultTraceListener>。
  - 創建將在大多數生成中啟用的日誌時使用此 API。
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - 僅在定義時`DEBUG`啟用。
  - 寫入附加的調試器。
  - 如果`*nix``COMPlus_DebugWriteToStdErr`設置為"設置"，則寫入穩穩。
  - 創建僅在調試生成中啟用的日誌時使用此 API。

### <a name="logging-events"></a>日誌記錄事件

以下 API 更加面向事件。 他們不是記錄簡單的字串，而是記錄事件物件。

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - 事件源是主根 .NET 核心跟蹤 API。
  - 適用于所有 .NET 標準版本。
  - 只允許跟蹤可序列化物件。
  - 寫入附加[的事件攔截器](xref:System.Diagnostics.Tracing.EventListener)。
  - .NET 核心為：
    - .NET Core 在所有平臺上的事件管道
    - [Windows 事件追蹤 (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Linux 的 LTTng 跟蹤框架](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - 包含在 .NET 核心中，並作為 .NET 框架的[NuGet 包](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)。
  - 允許在進程內跟蹤不可序列化的物件。
  - 包括一個橋接器，用於允許將記錄物件的選定欄位寫入<xref:System.Diagnostics.Tracing.EventSource>。

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - 提供了一種識別特定活動或事務產生的日誌消息的明確方法。 此物件可用於關聯不同服務的日誌。

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - 僅限 Windows。
  - 將消息寫入 Windows 事件日誌。
  - 系統管理員希望致命的應用程式錯誤訊息出現在 Windows 事件日誌中。

## <a name="ilogger-and-logging-frameworks"></a>ILogger 和日誌記錄框架

低級 API 可能不是滿足日誌記錄需求的正確選擇。 您可能需要考慮日誌記錄框架。

該<xref:Microsoft.Extensions.Logging.ILogger>介面已用於創建一個公共日誌記錄介面，其中記錄器可以通過依賴項注入插入。

例如，為了允許您為應用程式`ASP.NET`做出最佳選擇，可以支援一系列內置和協力廠商框架：

- [ASP.NET內置日誌記錄提供程式](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET協力廠商日誌記錄提供程式](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>記錄相關引用

- [如何：使用追蹤和偵錯進行條件式編譯](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [如何：將追蹤陳述式加入至應用程式程式碼](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET日誌記錄](/aspnet/core/fundamentals/logging)提供了它支援的日誌記錄技術的概述。

- [C# 字串插值](../../csharp/language-reference/tokens/interpolated.md)可以簡化日誌記錄代碼的編寫。

- 該<xref:System.Exception.Message?displayProperty=nameWithType>屬性可用於記錄異常。

- 該<xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>類可用於在日誌中提供堆疊資訊。

## <a name="performance-considerations"></a>效能考量

字串格式可能需要明顯的 CPU 處理時間。

在性能關鍵型應用程式中，建議您：

- 當沒有人在聽時，避免大量日誌記錄。 通過檢查是否首先啟用日誌記錄，避免構造昂貴的日誌記錄消息。
- 只記錄有用內容。
- 將花哨的格式延遲到分析階段。
