---
title: 記錄和追蹤-.NET Core
description: .NET Core 記錄和追蹤的簡介。
ms.date: 10/12/2020
ms.openlocfilehash: 33c78ecc839b552267ad43dd00b7d627e756a939
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997700"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core 記錄和追蹤

記錄和追蹤其實是相同技術的兩個名稱。 自電腦提早起，使用了簡單的技巧。 它只需要檢測應用程式，以寫入稍後要使用的輸出。

## <a name="reasons-to-use-logging-and-tracing"></a>使用記錄和追蹤的原因

這項簡單的技巧非常強大。 它可用於偵錯工具失敗的情況：

- 在很長一段時間內發生的問題，可能很難使用傳統偵錯工具來進行偵測。 記錄檔可讓您在長時間內進行詳細的事後剖析後評論。 相反地，偵錯工具會限制為即時分析。
- 多執行緒應用程式和分散式應用程式通常難以進行調試。  附加偵錯工具通常會修改行為。 您可以視需要分析詳細的記錄，以瞭解複雜的系統。
- 分散式應用程式中的問題可能是來自許多元件之間的複雜互動，而將偵錯工具連接到系統的每個部分可能並不合理。
- 許多服務不應停止。 附加偵錯工具通常會導致逾時錯誤。
- 問題不一定是預見。 記錄和追蹤是針對低負擔而設計，因此在發生問題的情況下，一律可以記錄程式。

## <a name="net-core-apis"></a>.NET Core Api

### <a name="print-style-apis"></a>列印樣式 Api

<xref:System.Console?displayProperty=nameWithType>、 <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 類別都提供類似的列印樣式 api，方便您進行記錄。

您可以選擇要使用的列印樣式 API。 主要差異包括：

- <xref:System.Console?displayProperty=nameWithType>
  - 一律啟用且一律寫入主控台。
  - 適用于您的客戶可能需要在發行中看到的資訊。
  - 因為這是最簡單的方法，所以通常用於臨機操作暫存的偵錯工具。 此偵錯工具程式碼通常不會簽入原始檔控制中。
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - 只有在定義時才 `TRACE` 會啟用。
  - <xref:System.Diagnostics.Trace.Listeners>依預設，寫入至附加 <xref:System.Diagnostics.DefaultTraceListener> 。
  - 建立將在大部分組建中啟用的記錄時，請使用此 API。
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - 只有在定義時才 `DEBUG` 會啟用。
  - 寫入附加的偵錯工具。
  - 如果設定，則在 `*nix` 寫入至 stderr 時 `COMPlus_DebugWriteToStdErr` 。
  - 建立只會在 debug 組建中啟用的記錄檔時，請使用此 API。

### <a name="logging-events"></a>記錄事件

下列 Api 更是事件導向。 它們不會記錄簡單字串，而是記錄事件物件。

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource 是主要的根 .NET Core 追蹤 API。
  - 適用于所有的 .NET Standard 版本。
  - 只允許追蹤可序列化的物件。
  - 寫入附加的 [事件](xref:System.Diagnostics.Tracing.EventListener)接聽程式。
  - .NET Core 提供下列各項的接聽程式：
    - 所有平臺上的 .NET Core EventPipe
    - [Windows 事件追蹤 (ETW)](/windows/win32/etw/event-tracing-portal)
    - [適用于 Linux 的 LTTng 追蹤架構](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - 隨附于 .NET Core，以及做為 .NET Framework 的 [NuGet 套件](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) 。
  - 允許非可序列化物件的同進程追蹤。
  - 包含允許將已記錄物件的選定欄位寫入至的橋接器 <xref:System.Diagnostics.Tracing.EventSource> 。

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - 提供一種明確的方式，可識別特定活動或交易所產生的記錄訊息。 此物件可用來將不同服務之間的記錄相互關聯。

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - 僅限 Windows。
  - 將訊息寫入 Windows 事件記錄檔。
  - 系統管理員預期會在 Windows 事件記錄檔中出現嚴重的應用程式錯誤訊息。

## <a name="ilogger-and-logging-frameworks"></a>ILogger 和記錄架構

低層級 Api 可能不是您記錄需求的正確選擇。 您可能會想要考慮使用記錄架構。

<xref:Microsoft.Extensions.Logging.ILogger>介面已用來建立一般記錄介面，可透過相依性插入來插入記錄器。

比方說，若要讓您為應用程式 .NET 提供最理想的選擇，您可以選擇內建和協力廠商架構：

- [.NET 內建記錄提供者](../extensions/logging-providers.md#built-in-logging-providers)
- [.NET 協力廠商記錄提供者](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a>記錄相關參考

- [作法：使用追蹤和偵錯進行條件式編譯](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [作法：將追蹤陳述式新增至應用程式程式碼](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [.Net 中的記錄](../extensions/logging.md) 提供它所支援之記錄技術的總覽。

- [C # 字串插補](../../csharp/language-reference/tokens/interpolated.md) 可簡化撰寫記錄程式碼的程式。

- <xref:System.Exception.Message?displayProperty=nameWithType>屬性適用于記錄例外狀況。

- <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>類別有助於在記錄中提供堆疊資訊。

## <a name="performance-considerations"></a>效能考量

字串格式化可能需要很明顯的 CPU 處理時間。

在效能關鍵的應用程式中，建議您：

- 當沒有人在接聽時，請避免進行大量記錄。 藉由檢查是否先啟用記錄，以避免建立昂貴的記錄訊息。
- 只記錄有用的內容。
- 將複雜的格式設定延遲至分析階段。
