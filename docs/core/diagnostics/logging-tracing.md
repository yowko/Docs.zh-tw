---
title: 記錄和追蹤-.NET Core
description: .NET Core 記錄和追蹤的簡介。
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 06781c6a5c1d771b1fa772539705cd1e2b3ad2d4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "70234662"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core 記錄和追蹤

針對相同的技巧, 記錄和追蹤其實是兩個名稱。 自電腦提早起, 使用了簡單的技巧。 它只需要檢測應用程式來寫入輸出, 以便稍後使用。

## <a name="reasons-to-use-logging-and-tracing"></a>使用記錄和追蹤的理由

這項簡單的技巧非常強大。 它可以用於偵錯工具失敗的情況:

- 很長一段時間內發生的問題, 可能會很容易使用傳統的偵錯工具進行 debug。 記錄允許長時間內的詳細事後剖析後評論。 相反地, 偵錯工具會限制為即時分析。
- 多執行緒應用程式和分散式應用程式通常很難進行調試。  附加偵錯工具通常會修改行為。 您可以視需要分析詳細的記錄, 以瞭解複雜的系統。
- 分散式應用程式中的問題可能是因為許多元件之間的複雜互動而引發, 所以將偵錯工具連接到系統的每個部分可能並不合理。
- 許多服務都不應該停止。 附加偵錯工具通常會導致逾時錯誤。
- 問題不一定是預見。 記錄和追蹤是針對低額外負荷而設計的, 因此在發生問題的情況下, 程式一律會進行記錄。

## <a name="net-core-apis"></a>.NET Core Api

### <a name="print-style-apis"></a>列印樣式 Api

<xref:System.Console?displayProperty=nameWithType>、和<xref:System.Diagnostics.Trace?displayProperty=nameWithType>類別各自提供類似的<xref:System.Diagnostics.Debug?displayProperty=nameWithType>列印樣式 api, 方便進行記錄。

選擇要使用的列印樣式 API 是由您決定。 主要的差異如下:
- <xref:System.Console?displayProperty=nameWithType>
  - 一律啟用並一律寫入主控台。
  - 適用于您的客戶可能需要在版本中看到的資訊。
  - 因為這是最簡單的方法, 所以通常用於臨機操作暫存的偵錯工具。 此 debug 程式碼通常不會簽入原始檔控制中。
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - 只有在定義`TRACE`時才啟用。
  - 預設會寫入<xref:System.Diagnostics.Trace.Listeners>至附加的。 <xref:System.Diagnostics.DefaultTraceListener>
  - 建立將在大部分組建中啟用的記錄檔時, 請使用此 API。
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - 只有在定義`DEBUG`時才啟用。
  - 寫入附加的偵錯工具。
  - `*nix` 當`COMPlus_DebugWriteToStdErr`已設定時, 寫入 stderr。
  - 建立只會在 debug 組建中啟用的記錄檔時, 請使用此 API。

### <a name="logging-events"></a>記錄事件

下列 Api 是更多事件導向。 與其記錄簡單的字串, 它們會記錄事件物件。

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource 是主要根 .NET Core 追蹤 API。
  - 適用于所有 .NET Standard 版本。
  - 只允許追蹤可序列化物件。
  - 寫入附加的[事件](xref:System.Diagnostics.Tracing.EventListener)接聽程式。
  - .NET Core 會針對下列各項提供接聽程式:
    - 所有平臺上的 .NET Core EventPipe
    - [Windows 事件追蹤 (ETW)](/windows/win32/etw/event-tracing-portal)
    - [適用于 Linux 的 LTTng 追蹤架構](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - 包含在 .NET Core 中, 以及做為 .NET Framework 的[NuGet 套件](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)。
  - 允許非可序列化物件的同進程追蹤。
  - 包含橋接器, 可讓所選的已記錄物件欄位寫入<xref:System.Diagnostics.Tracing.EventSource>。

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - 提供明確的方式來識別特定活動或交易所產生的記錄檔訊息。 此物件可用來讓不同服務之間的記錄相互關聯。

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - 僅限 Windows。
  - 將訊息寫入 Windows 事件記錄檔。
  - 系統管理員預期 Windows 事件記錄檔中會出現嚴重的應用程式錯誤訊息。

## <a name="ilogger-and-logging-frameworks"></a>ILogger 和記錄架構

低層級 Api 可能不是您記錄需求的正確選擇。 您可能想要考慮使用記錄架構。

<xref:Microsoft.Extensions.Logging.ILogger>介面已用來建立一般記錄介面, 可透過相依性插入來插入記錄器。

比方說, 若要讓您為應用程式`ASP.NET`提供最佳選擇, 讓您能夠選擇內建和協力廠商架構:
- [ASP.NET 內建記錄提供者](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET 協力廠商記錄提供者](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>記錄相關參考

- [如何：使用追蹤和偵錯進行條件式編譯](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [如何：將追蹤語句新增至應用程式程式碼](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET 記錄](/aspnet/core/fundamentals/logging)提供它所支援的記錄技術的總覽。

- 字串內插補點可簡化撰寫記錄程式碼的程式。 [ C# ](../../csharp/language-reference/tokens/interpolated.md)

- <xref:System.Exception.Message?displayProperty=nameWithType>屬性適用于記錄例外狀況。

- 在<xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>您的記錄中提供堆疊資訊時, 類別可能會很有用。

## <a name="performance-considerations"></a>效能考量

字串格式設定可能會產生顯著的 CPU 處理時間。

在效能關鍵應用程式中, 建議您:
- 當沒有人在接聽時, 請避免大量記錄。 請先檢查是否已啟用記錄, 以避免建立昂貴的記錄訊息。
- 只記錄有用的功能。
- 將複雜的格式延後到分析階段。
