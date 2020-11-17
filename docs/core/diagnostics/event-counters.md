---
title: .NET Core 中的 EventCounters
description: 在本文中，您將瞭解什麼是 EventCounters、如何實行它們，以及如何使用它們。
ms.date: 08/07/2020
ms.openlocfilehash: 212cd6b495785dcd091187f97a1b5e44e5597a4a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687638"
---
# <a name="eventcounters-in-net-core"></a>.NET Core 中的 EventCounters

本文 **適用于：✔️** .net CORE 3.0 SDK 和更新版本

EventCounters 是 .NET Core Api，用於輕量、跨平臺和近乎即時的效能計量集合。 EventCounters 已新增為 Windows 上 .NET Framework 之「效能計數器」的跨平臺替代方案。 在本文中，您將瞭解什麼是 EventCounters、如何實行它們，以及如何使用它們。

.NET Core 執行時間和一些 .NET 程式庫會使用 EventCounters （從 .NET Core 3.0 開始）發佈基本的診斷資訊。 除了 .NET 執行時間所提供的 EventCounters 之外，您還可以選擇執行自己的 EventCounters。 EventCounters 可以用來追蹤各種計量。

EventCounters 即時作為的一部分 <xref:System.Diagnostics.Tracing.EventSource> ，並且會定期自動推送至接聽程式工具。 就像上的所有其他事件一樣 <xref:System.Diagnostics.Tracing.EventSource> ，它們都可以透過內部進程和跨進程的方式，透過 <xref:System.Diagnostics.Tracing.EventListener> 和 [EventPipe](./eventpipe.md)使用。 本文著重于 EventCounters 的跨平臺功能，並刻意排除 PerfView 和 ETW (Windows) 的事件追蹤，雖然兩者都可以搭配 EventCounters 使用。

![EventCounters 同進程和跨進程的圖表影像](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a>EventCounter API 總覽

有兩個主要的計數器類別。 某些計數器適用于「速率」值，例如例外狀況總數、Gc 總數和要求總數。 其他計數器是「快照集」值，例如堆積使用量、CPU 使用量和工作集大小。 在這些類別的計數器中，有兩種類型的計數器會因其取得值的方式而有所不同。 輪詢計數器會透過回呼抓取其值，而非輪詢計數器會在計數器實例上直接設定其值。

計數器是由下列實作為表示：

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

事件接聽程式會指定度量間隔的時間長度。 在每個間隔結束時，會將值傳送至每個計數器的接聽程式。 計數器的實，會決定使用哪一個 Api 和計算來產生每個間隔的值。

1. 會 <xref:System.Diagnostics.Tracing.EventCounter> 記錄一組值。 <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>方法會將新的值加入至集合。 在每個間隔中，會計算集合的統計摘要，例如最小值、最大值和平均值。 [Dotnet 計數器](dotnet-counters.md)工具一律會顯示 mean 值。 適用 <xref:System.Diagnostics.Tracing.EventCounter> 于描述一組不連續的作業。 常見的使用方式可能包括監視最近 IO 作業的平均大小（以位元組為單位），或一組財務交易的平均貨幣值。

1. 會 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 記錄每個時間間隔的總執行總數。 <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>方法會加總。 例如，如果 `Increment()` 在一個間隔期間使用值、和來呼叫三次，則 `1` 會將 `2` `5` `8` 執行總數報告為此間隔的計數器值。 [Dotnet 計數器](dotnet-counters.md)工具會將速率顯示為記錄的總/時間。 <xref:System.Diagnostics.Tracing.IncrementingEventCounter>有助於測量動作的發生頻率，例如每秒處理的要求數。

1. <xref:System.Diagnostics.Tracing.PollingCounter>使用回呼來判斷所報告的值。 在每個時間間隔中，會叫用使用者提供的回呼函數，並使用傳回值做為計數器值。 <xref:System.Diagnostics.Tracing.PollingCounter>可以用來查詢外部來源的度量，例如取得磁片上的目前可用位元組。 它也可以用來報告應用程式可依需求計算的自訂統計資料。 範例包括報告最近要求延遲的第95個百分位數，或快取的目前命中或遺漏率。

1. <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>使用回呼來判斷回報的遞增值。 在每個時間間隔中，會叫用回呼，然後目前的調用和最後一個調用之間的差異是回報的值。 [Dotnet 計數器](dotnet-counters.md)工具一律會以比率（回報的值/時間）顯示差異。 當每次發生時都不能呼叫 API 時，此計數器很有用，但可以查詢發生的總次數。 例如，您可以報告每秒寫入檔案的位元組數，即使每次寫入位元組都沒有通知也是一樣。

## <a name="implement-an-eventsource"></a>執行 EventSource

下列程式碼會實 <xref:System.Diagnostics.Tracing.EventSource> 作為命名提供者公開的範例 `"Sample.EventCounter.Minimal"` 。 此來源包含 <xref:System.Diagnostics.Tracing.EventCounter> 表示要求處理時間的。 這類計數器的名稱 (，也就是它在來源) 的唯一識別碼和顯示名稱，這兩者都是由接聽程式工具（例如 [dotnet-counter](dotnet-counters.md)）所使用。

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

您可以使用 `dotnet-counters ps` 來顯示可監視的 .net 進程清單：

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

將 <xref:System.Diagnostics.Tracing.EventSource> 名稱傳遞至 `counter_list` 參數，以開始監視您的計數器：

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

按 <kbd>q</kbd> 停止監視命令。

#### <a name="conditional-counters"></a>條件式計數器

在執行時 <xref:System.Diagnostics.Tracing.EventSource> ，如果使用的值來呼叫方法，則可以有條件地具現化包含的計數器 <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> `EventCommand.Enable` 。 若只要安全地具現化計數器實例 `null` ，請使用 [null 聯合指派運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)。 此外，自訂方法可以評估 <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> 方法，以判斷是否已啟用目前的事件來源。

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> 條件式計數器是有條件地具現化的計數器，亦即微優化。 執行時間會在通常未使用計數器的情況下採用此模式，以節省毫秒的部分。

### <a name="net-core-runtime-example-counters"></a>.NET Core 執行時間範例計數器

.NET Core 執行時間中有許多絕佳的範例執行。 以下是可追蹤應用程式工作集大小的計數器執行時間執行。

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

<xref:System.Diagnostics.Tracing.PollingCounter>會報告應用程式的目前對應至進程的實體記憶體數量 (工作集) ，因為它會在某個時間點捕獲計量。 輪詢值的回呼是提供的 lambda 運算式，只是對 API 的呼叫 <xref:System.Environment.WorkingSet?displayProperty=fullName> 。 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> 和 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> 都是選擇性屬性，可設定以協助計數器的取用者端更清楚地顯示值。 例如， [dotnet 計數器](dotnet-counters.md) 會使用這些屬性來顯示更容易顯示的計數器名稱版本。

> [!IMPORTANT]
> `DisplayName`未當地語系化屬性。

在 <xref:System.Diagnostics.Tracing.PollingCounter> 和 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 中，不需要完成任何其他動作。 它們會在取用者要求的間隔輪詢這些值。

以下是使用執行之執行時間計數器的範例 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 。

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

<xref:System.Diagnostics.Tracing.IncrementingPollingCounter>使用 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API 來報告總鎖定爭用計數的增量。 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>屬性是選擇性的，但使用時，可以提供提示，指出計數器最適合顯示的時間間隔。 例如，鎖定爭用計數最適合顯示為 _每秒的計數_，因此其 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 設定為一秒。 您可以針對不同類型的速率計數器調整顯示速率。

> [!NOTE]
> <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>Dotnet _不_ 會使用，且事件接聽 [程式](dotnet-counters.md)不需要使用它。

在 [.net 運行](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) 時間存放庫中，有更多的計數器會用來做為參考。

## <a name="concurrency"></a>並行

> [!TIP]
> EventCounters API 不保證執行緒安全。 當 <xref:System.Diagnostics.Tracing.PollingCounter> 多個執行緒呼叫傳遞給或實例的委派時 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> ，您必須負責確保委派的執行緒安全。

例如，請考慮下列事項 <xref:System.Diagnostics.Tracing.EventSource> 來追蹤要求。

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

您 `AddRequest()` 可以從要求處理常式呼叫方法，然後在 `RequestRateCounter` 計數器的取用者所指定的間隔輪詢該值。 但是， `AddRequest()` 方法可以一次呼叫多個執行緒，並將競爭條件放在上 `_requestCount` 。 用來遞增的安全線程替代方法 `_requestCount` <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 。

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

若要防止讀取 (在32位架構上的) 的 `long` 欄位 `_requestCount` 使用 <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> 。

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a>使用 EventCounters

有兩種主要方式可取用 EventCounters，不論是在進程中，或是跨進程使用。 EventCounters 的耗用量可分為三層不同的取用技術。

- 透過 ETW 或 EventPipe 在原始資料流程中傳輸事件：
  - ETW Api 隨附于 Windows 作業系統，而 EventPipe 可作為 [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)或診斷 [IPC 通訊協定](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)來存取。
- 將二進位事件資料流程解碼成事件：
  - [TraceEvent 程式庫](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)會處理 ETW 和 EventPipe 資料流程格式。
- 命令列和 GUI 工具：
  - PerfView (ETW 或 EventPipe) 、dotnet 計數器 (僅 EventPipe) 和 dotnet 監視器 (EventPipe 的工具。

### <a name="consume-out-of-proc"></a>使用跨進程

使用 EventCounters 跨進程是一個非常常見的方法。 您可以使用 [dotnet 計數器](dotnet-counters.md) 透過 EventPipe 以跨平臺的方式取用它們。 此 `dotnet-counters` 工具是一個跨平臺 DOTNET CLI 全域工具，可用來監視計數器值。 若要瞭解如何使用 `dotnet-counters` 來監視您的計數器，請參閱 [dotnet 計數器](dotnet-counters.md)，或使用 EventCounters 教學課程進行 [測量效能](event-counter-perf.md) 。

#### <a name="dotnet-trace"></a>dotnet-trace

此 `dotnet-trace` 工具可用來透過 EventPipe 使用計數器資料。 以下是使用 `dotnet-trace` 來收集計數器資料的範例。

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

如需有關如何在一段時間內收集計數器值的詳細資訊，請參閱 [dotnet 追蹤](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) 檔。

#### <a name="azure-application-insights"></a>Azure Application Insights

Azure 監視器可以取用 EventCounters，特別是 Azure 應用程式的見解。 您可以新增和移除計數器，而且可以自由指定自訂計數器或已知的計數器。 如需詳細資訊，請參閱 [自訂要收集的計數器](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)。

#### <a name="dotnet-monitor"></a>dotnet-監視

此 `dotnet-monitor` 工具是實驗性工具，可讓您更輕鬆地存取 .net 進程中的診斷資訊。 此工具可做為所有診斷工具的超集合。 除了追蹤，它還可以監視計量、收集記憶體傾印，以及收集 GC 傾印。 它是以 CLI 工具和 docker 映射的形式散發。 它會公開 REST API，並透過 REST 呼叫來收集診斷成品。

如需詳細資訊，請參閱 [dotnet-監視器簡介（實驗性工具）](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)。

### <a name="consume-in-proc"></a>使用同進程

您可以透過 API 使用計數器值 <xref:System.Diagnostics.Tracing.EventListener> 。 <xref:System.Diagnostics.Tracing.EventListener>是在您的應用程式中取用所有實例所寫入之任何事件的同進程方式 <xref:System.Diagnostics.Tracing.EventSource> 。 如需如何使用 API 的詳細資訊 `EventListener` ，請參閱 <xref:System.Diagnostics.Tracing.EventListener> 。

首先，必須 <xref:System.Diagnostics.Tracing.EventSource> 啟用產生計數器值的。 覆寫 <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> 方法以在建立時取得通知 <xref:System.Diagnostics.Tracing.EventSource> ，如果是正確 <xref:System.Diagnostics.Tracing.EventSource> 的 EventCounters，您可以 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> 對其進行呼叫。 以下是範例覆寫：

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a>範例程式碼

以下範例類別會 <xref:System.Diagnostics.Tracing.EventListener> 印出 .net 執行時間的所有計數器名稱和值 <xref:System.Diagnostics.Tracing.EventSource> ，以便 `System.Runtime` 在某個時間間隔內 () 發佈其內部計數器。

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

如上所示，呼叫時，您 _必須_ 確定引數 `"EventCounterIntervalSec"` 已設定引數 `filterPayload` <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> 。 否則，計數器將無法排清值，因為它不知道應該將它排清的間隔。

## <a name="see-also"></a>另請參閱

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
