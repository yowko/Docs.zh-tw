---
title: .NET Core 中的 EventCounters
description: 在本文中，您將瞭解 EventCounters 是什麼、如何執行，以及如何使用它們。
ms.date: 08/07/2020
ms.openlocfilehash: 68868ff8b4e1393fc3b23af2bc8eef239ac56975
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024999"
---
# <a name="eventcounters-in-net-core"></a>.NET Core 中的 EventCounters

**本文適用于：✔️** .net CORE 3.0 SDK 和更新版本

EventCounters 是用於輕量、跨平臺且近乎即時效能標準集合的 .NET Core Api。 EventCounters 已新增為 Windows 上 .NET Framework 「效能計數器」的跨平臺替代方案。 在本文中，您將瞭解 EventCounters 是什麼、如何執行，以及如何使用它們。

.NET Core 執行時間和一些 .NET 程式庫會使用 EventCounters （從 .NET Core 3.0 開始）發行基本的診斷資訊。 除了 .NET 執行時間所提供的 EventCounters 之外，您也可以選擇執行自己的 EventCounters。 EventCounters 可以用來追蹤各種計量。

即時 EventCounters 為的一部分 <xref:System.Diagnostics.Tracing.EventSource> ，並且會定期自動推送至接聽程式工具。 就像上的所有其他事件一樣 <xref:System.Diagnostics.Tracing.EventSource> ，您可以透過和 EventPipe 同時使用進程內和跨進程 <xref:System.Diagnostics.Tracing.EventListener> 。 本文著重于 EventCounters 的跨平臺功能，並刻意排除 PerfView 和 ETW (Windows) 的事件追蹤，不過這兩者都可以搭配 EventCounters 使用。

![EventCounters 同進程和跨進程圖表影像](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a>EventCounter API 總覽

計數器有兩個主要類別。 某些計數器適用于「速率」值，例如例外狀況總數、Gc 總數和要求總數。 其他計數器則是「快照集」值，例如堆積使用量、CPU 使用量和工作集大小。 在上述每個類別的計數器中，有兩種類型的計數器會因取得其值的方式而有所不同。 輪詢計數器會透過回呼來抓取其值，而非輪詢計數器會在計數器實例上直接設定其值。

這些計數器是由下列的實作為表示：

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

事件接聽程式會指定測量間隔的時間長度。 在每個間隔結束時，會將值傳送到每個計數器的接聽程式。 計數器的執行會決定要使用哪些 Api 和計算來產生每個間隔的值。

1. 會 <xref:System.Diagnostics.Tracing.EventCounter> 記錄一組值。 <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>方法會將新的值加入至集合。 在每個間隔中，會計算集合的統計摘要，例如 min、max 和 mean。 [Dotnet 計數器](dotnet-counters.md)工具一律會顯示平均值。 適用 <xref:System.Diagnostics.Tracing.EventCounter> 于描述一組不連續的作業。 常見的用法可能包括監視最近 IO 作業的平均大小（以位元組為單位），或一組財務交易的平均貨幣值。

1. 會 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 記錄每個時間間隔的執行總計。 <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>方法會將新增至總計。 例如，如果在 `Increment()` 一段時間內呼叫了三次，且值為 `1` 、 `2` 和 `5` ，則的總計 `8` 會回報為此間隔的計數器值。 [Dotnet 計數器](dotnet-counters.md)工具會將速率顯示為記錄的總/時間。 適用 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 于測量動作發生的頻率，例如每秒處理的要求數目。

1. <xref:System.Diagnostics.Tracing.PollingCounter>會使用回呼來判斷所報告的值。 在每個時間間隔中，會叫用使用者提供的回呼函式，並使用傳回值做為計數器值。 <xref:System.Diagnostics.Tracing.PollingCounter>可以用來查詢來自外部來源的計量，例如取得磁片上目前可用的位元組。 它也可以用來報告應用程式可以視需要計算的自訂統計資料。 範例包括報告最近要求延遲的第95個百分位數，或快取的目前叫用或遺漏比例。

1. 會 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 使用回呼來判斷回報的遞增值。 在每個時間間隔內，會叫用回呼，然後在目前的調用與最後一個調用之間的差異是報告的值。 [Dotnet 計數器](dotnet-counters.md)工具一律會以速率（回報的值/時間）顯示差異。 如果在每次發生時都不能呼叫 API，此計數器很有用，但可以查詢發生的總次數。 例如，您可以報告每秒寫入檔案的位元組數目，即使每次寫入一個位元組，都不會有通知。

## <a name="implement-an-eventsource"></a>執行 EventSource

下列程式碼會實 <xref:System.Diagnostics.Tracing.EventSource> 作為命名提供者公開的範例 `"Sample.EventCounter.Minimal"` 。 此來源包含 <xref:System.Diagnostics.Tracing.EventCounter> 代表要求處理時間的。 這類計數器的名稱 (，也就是它在來源) 中的唯一識別碼和顯示名稱，這兩者都是由接聽程式工具（例如[dotnet-counter](dotnet-counters.md)）所使用。

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

您可以使用 `dotnet-counters ps` 來顯示可以監視的 .net 進程清單：

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

將 <xref:System.Diagnostics.Tracing.EventSource> 名稱傳遞給 `counter_list` 參數以開始監視計數器：

```console
dotnet-counters monitor --process-id 1400180 Sample.EventCounter.Minimal
```

下列範例顯示監視輸出：

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

按<kbd>q</kbd>停止監視命令。

#### <a name="conditional-counters"></a>條件式計數器

在執行時 <xref:System.Diagnostics.Tracing.EventSource> ，包含的計數器可以在 <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> 使用值呼叫方法時，有條件地具現化 <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> `EventCommand.Enable` 。 若要安全地具現化計數器實例（如果它是 `null` ），請使用[null 聯合指派運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)。 此外，自訂方法可以評估 <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> 方法，以判斷是否已啟用目前的事件來源。

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> 條件式計數器是有條件地具現化的計數器（微優化）。 在通常不會使用計數器的情況下，執行時間會採用此模式，以節省毫秒的分數。

### <a name="net-core-runtime-example-counters"></a>.NET Core 執行時間範例計數器

.NET Core 執行時間中有許多絕佳的範例實現。 以下是用來追蹤應用程式工作集大小之計數器的執行時間執行。

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

<xref:System.Diagnostics.Tracing.PollingCounter>會報告應用程式的目前對應至進程 (工作集) 的實體記憶體量，因為它會在一段時間內捕捉計量。 輪詢值的回呼是提供的 lambda 運算式，這只是對 API 的呼叫 <xref:System.Environment.WorkingSet?displayProperty=fullName> 。 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName>和 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> 是選擇性屬性，可設定來協助計數器的取用者端更清楚地顯示值。 例如， [dotnet 計數器](dotnet-counters.md)會使用這些屬性來顯示更容易顯示的計數器名稱版本。

> [!IMPORTANT]
> `DisplayName`屬性未當地語系化。

對於 <xref:System.Diagnostics.Tracing.PollingCounter> 、和，則 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 不需要執行任何其他動作。 它們都會以取用者要求的間隔來輪詢值本身。

以下是使用所實作為執行時間計數器的範例 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 。

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

會 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 使用 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API 來報告總鎖定爭用計數的增量。 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>屬性是選擇性的，但在使用時，它可以針對最適合顯示計數器的時間間隔提供提示。 例如，鎖定爭用計數最好顯示為_每秒計數_，因此其 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 設定為一秒。 顯示速率可以針對不同類型的速率計數器進行調整。

> [!NOTE]
> 不 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 是_not_由[dotnet 計數器](dotnet-counters.md)使用，而且事件接聽程式不需要使用它。

在[.net 運行](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs)時間存放庫中，您可以使用更多的計數器來做為參考。

## <a name="concurrency"></a>並行

> [!TIP]
> EventCounters API 不保證執行緒的安全。 當 <xref:System.Diagnostics.Tracing.PollingCounter> 多個執行緒呼叫傳遞給或實例的委派時 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> ，您必須負責確保委派的執行緒安全。

例如，請考慮下列事項 <xref:System.Diagnostics.Tracing.EventSource> 以追蹤要求。

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

`AddRequest()`方法可以從要求處理常式呼叫，而且會 `RequestRateCounter` 以計數器取用者所指定的間隔來輪詢值。 不過， `AddRequest()` 方法可以同時由多個執行緒呼叫，並將競爭條件放在 `_requestCount` 。 以執行緒安全的替代方式，遞增 `_requestCount` 會使用 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 。

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

## <a name="consume-eventcounters"></a>使用 EventCounters

有兩種主要的方式可使用 EventCounters （不論是在進程中或跨進程）。 EventCounters 的耗用量可以區別成各種取用技術的三層。

- 透過 ETW 或 EventPipe 傳輸原始資料流程中的事件：
  - ETW Api 隨附于 Windows 作業系統，而 EventPipe 可透過[.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)或診斷[IPC 通訊協定](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)來存取。
- 將二進位事件資料流程解碼成事件：
  - [TraceEvent 程式庫](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)會同時處理 ETW 和 EventPipe 資料流程格式。
- 命令列和 GUI 工具：
  - 像是 PerfView (ETW 或 EventPipe) 的工具、dotnet 計數器 (僅 EventPipe) ，以及 dotnet 監視器 (僅) EventPipe。

### <a name="consume-out-of-proc"></a>耗用進程外

使用 EventCounters 跨進程是非常常見的方法。 您可以使用[dotnet](dotnet-counters.md) ，透過 EventPipe 以跨平臺方式取用這些計數器。 此 `dotnet-counters` 工具是一個跨平臺 DOTNET CLI 全域工具，可用來監視計數器值。 若要瞭解如何使用 `dotnet-counters` 監視計數器，請參閱[dotnet-計數器](dotnet-counters.md)，或[使用 EventCounters 的測量效能](event-counter-perf.md)教學課程。

#### <a name="dotnet-trace"></a>dotnet-trace

此 `dotnet-trace` 工具可用來透過 EventPipe 使用計數器資料。 以下是使用 `dotnet-trace` 來收集計數器資料的範例。

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

如需有關如何在一段時間內收集計數器值的詳細資訊，請參閱[dotnet 追蹤](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time)檔。

#### <a name="azure-application-insights"></a>Azure Application Insights

Azure 監視器可以使用 EventCounters，特別是 Azure 應用程式深入解析。 可以新增和移除計數器，您可以隨意指定自訂計數器或已知的計數器。 如需詳細資訊，請參閱[自訂要收集的計數器](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)。

#### <a name="dotnet-monitor"></a>dotnet-監視

`dotnet-monitor`是一個實驗性工具，可讓您更輕鬆地存取 .net 進程中的診斷資訊。 如需詳細資訊，請參閱[dotnet-監視器簡介（實驗性工具）](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)。

### <a name="consume-in-proc"></a>耗用內部進程

您可以透過 API 取用計數器值 <xref:System.Diagnostics.Tracing.EventListener> 。 <xref:System.Diagnostics.Tracing.EventListener>是使用應用程式中所有實例所寫入之任何事件的同進程方式 <xref:System.Diagnostics.Tracing.EventSource> 。 如需有關如何使用 API 的詳細資訊 `EventListener` ，請參閱 <xref:System.Diagnostics.Tracing.EventListener> 。

首先，必須 <xref:System.Diagnostics.Tracing.EventSource> 啟用產生計數器值的。 覆寫 <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> 方法以在建立時取得通知 <xref:System.Diagnostics.Tracing.EventSource> ，如果這是 <xref:System.Diagnostics.Tracing.EventSource> 您 EventCounters 的正確，您可以 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> 在其上呼叫。 以下是範例覆寫：

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a>範例程式碼

以下範例類別會 <xref:System.Diagnostics.Tracing.EventListener> 從 .net 執行時間中列印出所有的計數器名稱和值 <xref:System.Diagnostics.Tracing.EventSource> ，以 `System.Runtime` 在某個間隔) 發佈其內部計數器 (。

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

如上所示，當呼叫時，您_必須_確定引數 `"EventCounterIntervalSec"` 中已設定引數 `filterPayload` <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> 。 否則，計數器將無法排清值，因為它不知道應該要清除的間隔。

## <a name="see-also"></a>另請參閱

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
