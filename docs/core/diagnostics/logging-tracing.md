---
title: 記錄和追蹤-.NET Core
description: .NET Core 記錄和追蹤的簡介。
ms.date: 10/12/2020
ms.openlocfilehash: fac8eeed63e8737ad42699d81b421747b207c69a
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753623"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core 記錄和追蹤

記錄和追蹤其實是相同技術的兩個名稱。 自電腦提早起，使用了簡單的技巧。 它只需要檢測應用程式，以寫入稍後要使用的輸出。

## <a name="reasons-to-use-logging-and-tracing"></a>使用記錄和追蹤的原因

這種簡單的技術出奇的強大。 它可用於偵錯工具失敗的情況：

- 長時間出現的問題，可能很難利用傳統的偵錯工具進行偵錯。 記錄允許長時間進行詳盡的事後檢討。 相反地，偵錯工具受限於即時分析。
- 多執行緒應用程式與分散式應用程式通常很難偵錯。  連結偵錯工具往往會修改行為。 您可以視需要分析詳細的記錄，以了解複雜的系統。
- 分散式應用程式中的問題可能是因為許多元件之間的複雜互動而引發，因此，將偵錯工具連接到系統的每個部分可能並不合理。
- 許多服務都不應該停止。 連結偵錯工具通常會導致逾時失敗。
- 問題不一定可以預見。 記錄和追蹤是針對低額外負荷而設計，因此，在發生問題時，程式一律會進行記錄。

## <a name="net-core-apis"></a>.NET Core Api

### <a name="print-style-apis"></a>列印樣式 Api

<xref:System.Console?displayProperty=nameWithType>、 <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 類別都提供類似的列印樣式 api，方便您進行記錄。

選擇要使用的列印樣式 API 完全取決於您。 主要差異包括：

- <xref:System.Console?displayProperty=nameWithType>
  - 一律啟用且一律寫入到主控台。
  - 適用於客戶可能需要在發行版本中看到的資訊。
  - 因為這是最簡單的方法，所以通常用於進行臨機操作的暫時性偵錯。 此偵錯程式碼通常絕對不會簽入到原始程式碼控制。
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - 只有在透過 `TRACE` 加入 `#define TRACE` 至您的來源或在編譯時指定選項來定義時，才會啟用 `/d:TRACE` 。
  - <xref:System.Diagnostics.Trace.Listeners>依預設，寫入至附加 <xref:System.Diagnostics.DefaultTraceListener> 。
  - 在建立將在大部分組建中啟用的記錄時，使用此 API。
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - 只有在透過 `DEBUG` 加入 `#define DEBUG` 至您的來源或在編譯時指定選項來定義時，才會啟用 `/d:DEBUG` 。
  - 寫入到已連結的偵錯工具。
  - 如果設定，則在 `*nix` 寫入至 stderr 時 `COMPlus_DebugWriteToStdErr` 。
  - 在建立將只會在偵錯組建中啟用的記錄時，使用此 API。

### <a name="logging-events"></a>記錄事件

下列 Api 更是事件導向。 它們不會記錄簡單字串，而是記錄事件物件。

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource 是主要的根 .NET Core 追蹤 API。
  - 適用于所有的 .NET Standard 版本。
  - 只允許追蹤可序列化的物件。
  - 可以透過設定為取用 EventSource 的任何 [EventListener](xref:System.Diagnostics.Tracing.EventListener) 實例，在同進程中使用。
  - 可透過下列方式跨進程使用：
    - 所有平臺上[的 .Net Core EventPipe](./eventpipe.md)
    - [Windows 事件追蹤 (ETW)](/windows/win32/etw/event-tracing-portal)
    - [適用于 Linux 的 LTTng 追蹤架構](https://lttng.org/)
      - 逐步解說： [使用 PerfCollect 收集 LTTng 追蹤](trace-perfcollect-lttng.md)。

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

- [執行時間提供者事件清單](../../fundamentals/diagnostics/runtime-events.md)

- [.NET 中的知名事件提供者](well-known-event-providers.md)

- <xref:System.Exception.Message?displayProperty=nameWithType>屬性適用于記錄例外狀況。

- <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>類別有助於在記錄中提供堆疊資訊。

## <a name="performance-considerations"></a>效能考量

字串格式化可能需要很明顯的 CPU 處理時間。

在效能關鍵的應用程式中，建議您：

- 當沒有人在接聽時，請避免進行大量記錄。 藉由檢查是否先啟用記錄，以避免建立昂貴的記錄訊息。
- 只記錄有用的內容。
- 將複雜的格式設定延遲至分析階段。
