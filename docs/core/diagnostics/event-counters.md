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
# <a name="eventcounters-in-net-core"></a><span data-ttu-id="3fb02-103">.NET Core 中的 EventCounters</span><span class="sxs-lookup"><span data-stu-id="3fb02-103">EventCounters in .NET Core</span></span>

<span data-ttu-id="3fb02-104">本文 **適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="3fb02-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="3fb02-105">EventCounters 是 .NET Core Api，用於輕量、跨平臺和近乎即時的效能計量集合。</span><span class="sxs-lookup"><span data-stu-id="3fb02-105">EventCounters are .NET Core APIs used for lightweight, cross-platform, and near real-time performance metric collection.</span></span> <span data-ttu-id="3fb02-106">EventCounters 已新增為 Windows 上 .NET Framework 之「效能計數器」的跨平臺替代方案。</span><span class="sxs-lookup"><span data-stu-id="3fb02-106">EventCounters were added as a cross-platform alternative to the "performance counters" of the .NET Framework on Windows.</span></span> <span data-ttu-id="3fb02-107">在本文中，您將瞭解什麼是 EventCounters、如何實行它們，以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="3fb02-107">In this article you'll learn what EventCounters are, how to implement them, and how to consume them.</span></span>

<span data-ttu-id="3fb02-108">.NET Core 執行時間和一些 .NET 程式庫會使用 EventCounters （從 .NET Core 3.0 開始）發佈基本的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="3fb02-108">The .NET Core runtime and a few .NET libraries publish basic diagnostics information using EventCounters starting in .NET Core 3.0.</span></span> <span data-ttu-id="3fb02-109">除了 .NET 執行時間所提供的 EventCounters 之外，您還可以選擇執行自己的 EventCounters。</span><span class="sxs-lookup"><span data-stu-id="3fb02-109">Apart from the EventCounters that are provided by the .NET runtime, you may choose to implement your own EventCounters.</span></span> <span data-ttu-id="3fb02-110">EventCounters 可以用來追蹤各種計量。</span><span class="sxs-lookup"><span data-stu-id="3fb02-110">EventCounters can be used to track various metrics.</span></span>

<span data-ttu-id="3fb02-111">EventCounters 即時作為的一部分 <xref:System.Diagnostics.Tracing.EventSource> ，並且會定期自動推送至接聽程式工具。</span><span class="sxs-lookup"><span data-stu-id="3fb02-111">EventCounters live as a part of an <xref:System.Diagnostics.Tracing.EventSource>, and are automatically pushed to listener tools on a regular basis.</span></span> <span data-ttu-id="3fb02-112">就像上的所有其他事件一樣 <xref:System.Diagnostics.Tracing.EventSource> ，它們都可以透過內部進程和跨進程的方式，透過 <xref:System.Diagnostics.Tracing.EventListener> 和 [EventPipe](./eventpipe.md)使用。</span><span class="sxs-lookup"><span data-stu-id="3fb02-112">Like all other events on an <xref:System.Diagnostics.Tracing.EventSource>, they can be consumed both in-proc and out-of-proc via <xref:System.Diagnostics.Tracing.EventListener> and [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="3fb02-113">本文著重于 EventCounters 的跨平臺功能，並刻意排除 PerfView 和 ETW (Windows) 的事件追蹤，雖然兩者都可以搭配 EventCounters 使用。</span><span class="sxs-lookup"><span data-stu-id="3fb02-113">This article focuses on the cross-platform capabilities of EventCounters, and intentionally excludes PerfView and ETW (Event Tracing for Windows) - although both can be used with EventCounters.</span></span>

![EventCounters 同進程和跨進程的圖表影像](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a><span data-ttu-id="3fb02-115">EventCounter API 總覽</span><span class="sxs-lookup"><span data-stu-id="3fb02-115">EventCounter API overview</span></span>

<span data-ttu-id="3fb02-116">有兩個主要的計數器類別。</span><span class="sxs-lookup"><span data-stu-id="3fb02-116">There are two primary categories of counters.</span></span> <span data-ttu-id="3fb02-117">某些計數器適用于「速率」值，例如例外狀況總數、Gc 總數和要求總數。</span><span class="sxs-lookup"><span data-stu-id="3fb02-117">Some counters are for "rate" values, such as total number of exceptions, total number of GCs, and total number of requests.</span></span> <span data-ttu-id="3fb02-118">其他計數器是「快照集」值，例如堆積使用量、CPU 使用量和工作集大小。</span><span class="sxs-lookup"><span data-stu-id="3fb02-118">Other counters are "snapshot" values, such as heap usage, CPU usage, and working set size.</span></span> <span data-ttu-id="3fb02-119">在這些類別的計數器中，有兩種類型的計數器會因其取得值的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3fb02-119">Within each of these categories of counters, there are two types of counters that vary by how they get their value.</span></span> <span data-ttu-id="3fb02-120">輪詢計數器會透過回呼抓取其值，而非輪詢計數器會在計數器實例上直接設定其值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-120">Polling counters retrieve their value via a callback, and non-polling counters have their values directly set on the counter instance.</span></span>

<span data-ttu-id="3fb02-121">計數器是由下列實作為表示：</span><span class="sxs-lookup"><span data-stu-id="3fb02-121">The counters are represented by the following implementations:</span></span>

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

<span data-ttu-id="3fb02-122">事件接聽程式會指定度量間隔的時間長度。</span><span class="sxs-lookup"><span data-stu-id="3fb02-122">An event listener specifies how long measurement intervals are.</span></span> <span data-ttu-id="3fb02-123">在每個間隔結束時，會將值傳送至每個計數器的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3fb02-123">At the end of each interval a value is transmitted to the listener for each counter.</span></span> <span data-ttu-id="3fb02-124">計數器的實，會決定使用哪一個 Api 和計算來產生每個間隔的值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-124">The implementations of a counter determine what APIs and calculations are used to produce the value each interval.</span></span>

1. <span data-ttu-id="3fb02-125">會 <xref:System.Diagnostics.Tracing.EventCounter> 記錄一組值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-125">The <xref:System.Diagnostics.Tracing.EventCounter> records a set of values.</span></span> <span data-ttu-id="3fb02-126"><xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>方法會將新的值加入至集合。</span><span class="sxs-lookup"><span data-stu-id="3fb02-126">The <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> method adds a new value to the set.</span></span> <span data-ttu-id="3fb02-127">在每個間隔中，會計算集合的統計摘要，例如最小值、最大值和平均值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-127">With each interval, a statistical summary for the set is computed, such as the min, max, and mean.</span></span> <span data-ttu-id="3fb02-128">[Dotnet 計數器](dotnet-counters.md)工具一律會顯示 mean 值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-128">The [dotnet-counters](dotnet-counters.md) tool will always display the mean value.</span></span> <span data-ttu-id="3fb02-129">適用 <xref:System.Diagnostics.Tracing.EventCounter> 于描述一組不連續的作業。</span><span class="sxs-lookup"><span data-stu-id="3fb02-129">The <xref:System.Diagnostics.Tracing.EventCounter> is useful to describe a discrete set of operations.</span></span> <span data-ttu-id="3fb02-130">常見的使用方式可能包括監視最近 IO 作業的平均大小（以位元組為單位），或一組財務交易的平均貨幣值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-130">Common usage may include monitoring the average size in bytes of recent IO operations, or the average monetary value of a set of financial transactions.</span></span>

1. <span data-ttu-id="3fb02-131">會 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 記錄每個時間間隔的總執行總數。</span><span class="sxs-lookup"><span data-stu-id="3fb02-131">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> records a running total for each time interval.</span></span> <span data-ttu-id="3fb02-132"><xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>方法會加總。</span><span class="sxs-lookup"><span data-stu-id="3fb02-132">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> method adds to the total.</span></span> <span data-ttu-id="3fb02-133">例如，如果 `Increment()` 在一個間隔期間使用值、和來呼叫三次，則 `1` 會將 `2` `5` `8` 執行總數報告為此間隔的計數器值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-133">For example, if `Increment()` is called three times during one interval with values `1`, `2`, and `5`, then the running total of `8` will be reported as the counter value for this interval.</span></span> <span data-ttu-id="3fb02-134">[Dotnet 計數器](dotnet-counters.md)工具會將速率顯示為記錄的總/時間。</span><span class="sxs-lookup"><span data-stu-id="3fb02-134">The [dotnet-counters](dotnet-counters.md) tool will display the rate as the recorded total / time.</span></span> <span data-ttu-id="3fb02-135"><xref:System.Diagnostics.Tracing.IncrementingEventCounter>有助於測量動作的發生頻率，例如每秒處理的要求數。</span><span class="sxs-lookup"><span data-stu-id="3fb02-135">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> is useful to measure how frequently an action is occurring, such as the number of requests processed per second.</span></span>

1. <span data-ttu-id="3fb02-136"><xref:System.Diagnostics.Tracing.PollingCounter>使用回呼來判斷所報告的值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-136">The <xref:System.Diagnostics.Tracing.PollingCounter> uses a callback to determine the value that is reported.</span></span> <span data-ttu-id="3fb02-137">在每個時間間隔中，會叫用使用者提供的回呼函數，並使用傳回值做為計數器值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-137">With each time interval, the user provided callback function is invoked and the return value is used as the counter value.</span></span> <span data-ttu-id="3fb02-138"><xref:System.Diagnostics.Tracing.PollingCounter>可以用來查詢外部來源的度量，例如取得磁片上的目前可用位元組。</span><span class="sxs-lookup"><span data-stu-id="3fb02-138">A <xref:System.Diagnostics.Tracing.PollingCounter> can be used to query a metric from an external source, for example getting the current free bytes on a disk.</span></span> <span data-ttu-id="3fb02-139">它也可以用來報告應用程式可依需求計算的自訂統計資料。</span><span class="sxs-lookup"><span data-stu-id="3fb02-139">It can also be used to report custom statistics that can be computed on demand by an application.</span></span> <span data-ttu-id="3fb02-140">範例包括報告最近要求延遲的第95個百分位數，或快取的目前命中或遺漏率。</span><span class="sxs-lookup"><span data-stu-id="3fb02-140">Examples include reporting the 95th percentile of recent request latencies, or the current hit or miss ratio of a cache.</span></span>

1. <span data-ttu-id="3fb02-141"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter>使用回呼來判斷回報的遞增值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-141">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses a callback to determine the reported increment value.</span></span> <span data-ttu-id="3fb02-142">在每個時間間隔中，會叫用回呼，然後目前的調用和最後一個調用之間的差異是回報的值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-142">With each time interval, the callback is invoked, and then the difference between the current invocation, and the last invocation is the reported value.</span></span> <span data-ttu-id="3fb02-143">[Dotnet 計數器](dotnet-counters.md)工具一律會以比率（回報的值/時間）顯示差異。</span><span class="sxs-lookup"><span data-stu-id="3fb02-143">The [dotnet-counters](dotnet-counters.md) tool will always display the difference as a rate, the reported value / time.</span></span> <span data-ttu-id="3fb02-144">當每次發生時都不能呼叫 API 時，此計數器很有用，但可以查詢發生的總次數。</span><span class="sxs-lookup"><span data-stu-id="3fb02-144">This counter is useful when it isn't feasible to call an API on each occurrence, but it's possible to query the total number of occurrences.</span></span> <span data-ttu-id="3fb02-145">例如，您可以報告每秒寫入檔案的位元組數，即使每次寫入位元組都沒有通知也是一樣。</span><span class="sxs-lookup"><span data-stu-id="3fb02-145">For example, you could report the number of bytes written to a file per second, even without a notification each time a byte is written.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="3fb02-146">執行 EventSource</span><span class="sxs-lookup"><span data-stu-id="3fb02-146">Implement an EventSource</span></span>

<span data-ttu-id="3fb02-147">下列程式碼會實 <xref:System.Diagnostics.Tracing.EventSource> 作為命名提供者公開的範例 `"Sample.EventCounter.Minimal"` 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-147">The following code implements a sample <xref:System.Diagnostics.Tracing.EventSource> exposed as the named `"Sample.EventCounter.Minimal"` provider.</span></span> <span data-ttu-id="3fb02-148">此來源包含 <xref:System.Diagnostics.Tracing.EventCounter> 表示要求處理時間的。</span><span class="sxs-lookup"><span data-stu-id="3fb02-148">This source contains an <xref:System.Diagnostics.Tracing.EventCounter> representing request processing time.</span></span> <span data-ttu-id="3fb02-149">這類計數器的名稱 (，也就是它在來源) 的唯一識別碼和顯示名稱，這兩者都是由接聽程式工具（例如 [dotnet-counter](dotnet-counters.md)）所使用。</span><span class="sxs-lookup"><span data-stu-id="3fb02-149">Such a counter has a name (that is, its unique ID in the source) and a display name, both used by listener tools such as [dotnet-counter](dotnet-counters.md).</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="3fb02-150">您可以使用 `dotnet-counters ps` 來顯示可監視的 .net 進程清單：</span><span class="sxs-lookup"><span data-stu-id="3fb02-150">You use `dotnet-counters ps` to display a list of .NET processes that can be monitored:</span></span>

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

<span data-ttu-id="3fb02-151">將 <xref:System.Diagnostics.Tracing.EventSource> 名稱傳遞至 `counter_list` 參數，以開始監視您的計數器：</span><span class="sxs-lookup"><span data-stu-id="3fb02-151">Pass the <xref:System.Diagnostics.Tracing.EventSource> name to the `counter_list` switch to start monitoring your counter:</span></span>

```console
dotnet-counters monitor --process-id 1400180 Sample.EventCounter.Minimal
```

<span data-ttu-id="3fb02-152">下列範例顯示監視輸出：</span><span class="sxs-lookup"><span data-stu-id="3fb02-152">The following example shows monitor output:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

<span data-ttu-id="3fb02-153">按 <kbd>q</kbd> 停止監視命令。</span><span class="sxs-lookup"><span data-stu-id="3fb02-153">Press <kbd>q</kbd> to stop the monitoring command.</span></span>

#### <a name="conditional-counters"></a><span data-ttu-id="3fb02-154">條件式計數器</span><span class="sxs-lookup"><span data-stu-id="3fb02-154">Conditional counters</span></span>

<span data-ttu-id="3fb02-155">在執行時 <xref:System.Diagnostics.Tracing.EventSource> ，如果使用的值來呼叫方法，則可以有條件地具現化包含的計數器 <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> `EventCommand.Enable` 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-155">When implementing an <xref:System.Diagnostics.Tracing.EventSource>, the containing counters can be conditionally instantiated when the <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> method is called with a <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> value of `EventCommand.Enable`.</span></span> <span data-ttu-id="3fb02-156">若只要安全地具現化計數器實例 `null` ，請使用 [null 聯合指派運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="3fb02-156">To safely instantiate a counter instance only if it is `null`, use the [null-coalescing assignment operator](../../csharp/language-reference/operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="3fb02-157">此外，自訂方法可以評估 <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> 方法，以判斷是否已啟用目前的事件來源。</span><span class="sxs-lookup"><span data-stu-id="3fb02-157">Additionally, custom methods can evaluate the <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> method to determine whether or not the current event source is enabled.</span></span>

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> <span data-ttu-id="3fb02-158">條件式計數器是有條件地具現化的計數器，亦即微優化。</span><span class="sxs-lookup"><span data-stu-id="3fb02-158">Conditional counters are counters that are conditionally instantiated, a micro-optimization.</span></span> <span data-ttu-id="3fb02-159">執行時間會在通常未使用計數器的情況下採用此模式，以節省毫秒的部分。</span><span class="sxs-lookup"><span data-stu-id="3fb02-159">The runtime adopts this pattern for scenarios where counters are normally not used, to save a fraction of a millisecond.</span></span>

### <a name="net-core-runtime-example-counters"></a><span data-ttu-id="3fb02-160">.NET Core 執行時間範例計數器</span><span class="sxs-lookup"><span data-stu-id="3fb02-160">.NET Core runtime example counters</span></span>

<span data-ttu-id="3fb02-161">.NET Core 執行時間中有許多絕佳的範例執行。</span><span class="sxs-lookup"><span data-stu-id="3fb02-161">There are many great example implementations in the .NET Core runtime.</span></span> <span data-ttu-id="3fb02-162">以下是可追蹤應用程式工作集大小的計數器執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="3fb02-162">Here is the runtime implementation for the counter that tracks the working set size of the application.</span></span>

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

<span data-ttu-id="3fb02-163"><xref:System.Diagnostics.Tracing.PollingCounter>會報告應用程式的目前對應至進程的實體記憶體數量 (工作集) ，因為它會在某個時間點捕獲計量。</span><span class="sxs-lookup"><span data-stu-id="3fb02-163">The <xref:System.Diagnostics.Tracing.PollingCounter> reports the current amount of physical memory mapped to the process (working set) of the app, since it captures a metric at a moment in time.</span></span> <span data-ttu-id="3fb02-164">輪詢值的回呼是提供的 lambda 運算式，只是對 API 的呼叫 <xref:System.Environment.WorkingSet?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-164">The callback for polling a value is the provided lambda expression, which is just a call to the <xref:System.Environment.WorkingSet?displayProperty=fullName> API.</span></span> <span data-ttu-id="3fb02-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> 和 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> 都是選擇性屬性，可設定以協助計數器的取用者端更清楚地顯示值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> and <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> are optional properties that can be set to help the consumer side of the counter to display the value more clearly.</span></span> <span data-ttu-id="3fb02-166">例如， [dotnet 計數器](dotnet-counters.md) 會使用這些屬性來顯示更容易顯示的計數器名稱版本。</span><span class="sxs-lookup"><span data-stu-id="3fb02-166">For example, [dotnet-counters](dotnet-counters.md) uses these properties to display the more display-friendly version of the counter names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fb02-167">`DisplayName`未當地語系化屬性。</span><span class="sxs-lookup"><span data-stu-id="3fb02-167">The `DisplayName` properties are not localized.</span></span>

<span data-ttu-id="3fb02-168">在 <xref:System.Diagnostics.Tracing.PollingCounter> 和 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 中，不需要完成任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="3fb02-168">For the <xref:System.Diagnostics.Tracing.PollingCounter>, and the <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>, nothing else needs to be done.</span></span> <span data-ttu-id="3fb02-169">它們會在取用者要求的間隔輪詢這些值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-169">They both poll the values themselves at an interval requested by the consumer.</span></span>

<span data-ttu-id="3fb02-170">以下是使用執行之執行時間計數器的範例 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-170">Here is an example of a runtime counter implemented using <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>.</span></span>

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

<span data-ttu-id="3fb02-171"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter>使用 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API 來報告總鎖定爭用計數的增量。</span><span class="sxs-lookup"><span data-stu-id="3fb02-171">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses the <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API to report the increment of the total lock contention count.</span></span> <span data-ttu-id="3fb02-172"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>屬性是選擇性的，但使用時，可以提供提示，指出計數器最適合顯示的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="3fb02-172">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> property is optional, but when used it can provide a hint for what time interval the counter is best displayed at.</span></span> <span data-ttu-id="3fb02-173">例如，鎖定爭用計數最適合顯示為 _每秒的計數_，因此其 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 設定為一秒。</span><span class="sxs-lookup"><span data-stu-id="3fb02-173">For example, the lock contention count is best displayed as _count per second_, so its <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is set to one second.</span></span> <span data-ttu-id="3fb02-174">您可以針對不同類型的速率計數器調整顯示速率。</span><span class="sxs-lookup"><span data-stu-id="3fb02-174">The display rate can be adjusted for different types of rate counters.</span></span>

> [!NOTE]
> <span data-ttu-id="3fb02-175"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>Dotnet _不_ 會使用，且事件接聽 [程式](dotnet-counters.md)不需要使用它。</span><span class="sxs-lookup"><span data-stu-id="3fb02-175">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is _not_ used by [dotnet-counters](dotnet-counters.md), and event listeners are not required to use it.</span></span>

<span data-ttu-id="3fb02-176">在 [.net 運行](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) 時間存放庫中，有更多的計數器會用來做為參考。</span><span class="sxs-lookup"><span data-stu-id="3fb02-176">There are more counter implementations to use as a reference in the [.NET runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) repo.</span></span>

## <a name="concurrency"></a><span data-ttu-id="3fb02-177">並行</span><span class="sxs-lookup"><span data-stu-id="3fb02-177">Concurrency</span></span>

> [!TIP]
> <span data-ttu-id="3fb02-178">EventCounters API 不保證執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="3fb02-178">The EventCounters API does not guarantee thread safety.</span></span> <span data-ttu-id="3fb02-179">當 <xref:System.Diagnostics.Tracing.PollingCounter> 多個執行緒呼叫傳遞給或實例的委派時 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> ，您必須負責確保委派的執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="3fb02-179">When the delegates passed to <xref:System.Diagnostics.Tracing.PollingCounter> or <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> instances are called by multiple threads, it's your responsibility to guarantee the delegates' thread-safety.</span></span>

<span data-ttu-id="3fb02-180">例如，請考慮下列事項 <xref:System.Diagnostics.Tracing.EventSource> 來追蹤要求。</span><span class="sxs-lookup"><span data-stu-id="3fb02-180">For example, consider the following <xref:System.Diagnostics.Tracing.EventSource> to keep track of requests.</span></span>

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

<span data-ttu-id="3fb02-181">您 `AddRequest()` 可以從要求處理常式呼叫方法，然後在 `RequestRateCounter` 計數器的取用者所指定的間隔輪詢該值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-181">The `AddRequest()` method can be called from a request handler, and the `RequestRateCounter` polls the value at the interval specified by the consumer of the counter.</span></span> <span data-ttu-id="3fb02-182">但是， `AddRequest()` 方法可以一次呼叫多個執行緒，並將競爭條件放在上 `_requestCount` 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-182">However, the `AddRequest()` method can be called by multiple threads at once, putting a race condition on `_requestCount`.</span></span> <span data-ttu-id="3fb02-183">用來遞增的安全線程替代方法 `_requestCount` <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-183">A thread-safe alternative way to increment the `_requestCount` is to use <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span>

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

<span data-ttu-id="3fb02-184">若要防止讀取 (在32位架構上的) 的 `long` 欄位 `_requestCount` 使用 <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-184">To prevent torn reads (on 32-bit architectures) of the `long`-field `_requestCount` use <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType>.</span></span>

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a><span data-ttu-id="3fb02-185">使用 EventCounters</span><span class="sxs-lookup"><span data-stu-id="3fb02-185">Consume EventCounters</span></span>

<span data-ttu-id="3fb02-186">有兩種主要方式可取用 EventCounters，不論是在進程中，或是跨進程使用。</span><span class="sxs-lookup"><span data-stu-id="3fb02-186">There are two primary ways of consuming EventCounters, either in-proc, or out-of-proc.</span></span> <span data-ttu-id="3fb02-187">EventCounters 的耗用量可分為三層不同的取用技術。</span><span class="sxs-lookup"><span data-stu-id="3fb02-187">The consumption of EventCounters can be distinguished into three layers of various consuming technologies.</span></span>

- <span data-ttu-id="3fb02-188">透過 ETW 或 EventPipe 在原始資料流程中傳輸事件：</span><span class="sxs-lookup"><span data-stu-id="3fb02-188">Transporting events in a raw stream via ETW or EventPipe:</span></span>
  - <span data-ttu-id="3fb02-189">ETW Api 隨附于 Windows 作業系統，而 EventPipe 可作為 [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)或診斷 [IPC 通訊協定](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)來存取。</span><span class="sxs-lookup"><span data-stu-id="3fb02-189">ETW APIs come with the Windows OS, and EventPipe is accessible as a [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console), or the diagnostic [IPC protocol](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>
- <span data-ttu-id="3fb02-190">將二進位事件資料流程解碼成事件：</span><span class="sxs-lookup"><span data-stu-id="3fb02-190">Decoding the binary event stream into events:</span></span>
  - <span data-ttu-id="3fb02-191">[TraceEvent 程式庫](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)會處理 ETW 和 EventPipe 資料流程格式。</span><span class="sxs-lookup"><span data-stu-id="3fb02-191">The [TraceEvent library](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) handles both ETW and EventPipe stream formats.</span></span>
- <span data-ttu-id="3fb02-192">命令列和 GUI 工具：</span><span class="sxs-lookup"><span data-stu-id="3fb02-192">Command-line and GUI tools:</span></span>
  - <span data-ttu-id="3fb02-193">PerfView (ETW 或 EventPipe) 、dotnet 計數器 (僅 EventPipe) 和 dotnet 監視器 (EventPipe 的工具。</span><span class="sxs-lookup"><span data-stu-id="3fb02-193">Tools like PerfView (ETW or EventPipe), dotnet-counters (EventPipe only), and dotnet-monitor (EventPipe only).</span></span>

### <a name="consume-out-of-proc"></a><span data-ttu-id="3fb02-194">使用跨進程</span><span class="sxs-lookup"><span data-stu-id="3fb02-194">Consume out-of-proc</span></span>

<span data-ttu-id="3fb02-195">使用 EventCounters 跨進程是一個非常常見的方法。</span><span class="sxs-lookup"><span data-stu-id="3fb02-195">Consuming EventCounters out-of-proc is a very common approach.</span></span> <span data-ttu-id="3fb02-196">您可以使用 [dotnet 計數器](dotnet-counters.md) 透過 EventPipe 以跨平臺的方式取用它們。</span><span class="sxs-lookup"><span data-stu-id="3fb02-196">You can use [dotnet-counters](dotnet-counters.md) to consume them in a cross-platform manner via an EventPipe.</span></span> <span data-ttu-id="3fb02-197">此 `dotnet-counters` 工具是一個跨平臺 DOTNET CLI 全域工具，可用來監視計數器值。</span><span class="sxs-lookup"><span data-stu-id="3fb02-197">The `dotnet-counters` tool is a cross-platform dotnet CLI global tool that can be used to monitor the counter values.</span></span> <span data-ttu-id="3fb02-198">若要瞭解如何使用 `dotnet-counters` 來監視您的計數器，請參閱 [dotnet 計數器](dotnet-counters.md)，或使用 EventCounters 教學課程進行 [測量效能](event-counter-perf.md) 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-198">To find out how to use `dotnet-counters` to monitor your counters, see [dotnet-counters](dotnet-counters.md), or work through the [Measure performance using EventCounters](event-counter-perf.md) tutorial.</span></span>

#### <a name="dotnet-trace"></a><span data-ttu-id="3fb02-199">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="3fb02-199">dotnet-trace</span></span>

<span data-ttu-id="3fb02-200">此 `dotnet-trace` 工具可用來透過 EventPipe 使用計數器資料。</span><span class="sxs-lookup"><span data-stu-id="3fb02-200">The `dotnet-trace` tool can be used to consume the counter data through an EventPipe.</span></span> <span data-ttu-id="3fb02-201">以下是使用 `dotnet-trace` 來收集計數器資料的範例。</span><span class="sxs-lookup"><span data-stu-id="3fb02-201">Here is an example using `dotnet-trace` to collect counter data.</span></span>

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

<span data-ttu-id="3fb02-202">如需有關如何在一段時間內收集計數器值的詳細資訊，請參閱 [dotnet 追蹤](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) 檔。</span><span class="sxs-lookup"><span data-stu-id="3fb02-202">For more information on how to collect counter values over time, see the [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) documentation.</span></span>

#### <a name="azure-application-insights"></a><span data-ttu-id="3fb02-203">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="3fb02-203">Azure Application Insights</span></span>

<span data-ttu-id="3fb02-204">Azure 監視器可以取用 EventCounters，特別是 Azure 應用程式的見解。</span><span class="sxs-lookup"><span data-stu-id="3fb02-204">EventCounters can be consumed by Azure Monitor, specifically Azure Application Insights.</span></span> <span data-ttu-id="3fb02-205">您可以新增和移除計數器，而且可以自由指定自訂計數器或已知的計數器。</span><span class="sxs-lookup"><span data-stu-id="3fb02-205">Counters can be added and removed, and you're free to specify custom counters, or well-known counters.</span></span> <span data-ttu-id="3fb02-206">如需詳細資訊，請參閱 [自訂要收集的計數器](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)。</span><span class="sxs-lookup"><span data-stu-id="3fb02-206">For more information, see [Customizing counters to be collected](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).</span></span>

#### <a name="dotnet-monitor"></a><span data-ttu-id="3fb02-207">dotnet-監視</span><span class="sxs-lookup"><span data-stu-id="3fb02-207">dotnet-monitor</span></span>

<span data-ttu-id="3fb02-208">此 `dotnet-monitor` 工具是實驗性工具，可讓您更輕鬆地存取 .net 進程中的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="3fb02-208">The `dotnet-monitor` tool is an experimental tool that makes it easier to get access to diagnostics information in a .NET process.</span></span> <span data-ttu-id="3fb02-209">此工具可做為所有診斷工具的超集合。</span><span class="sxs-lookup"><span data-stu-id="3fb02-209">The tool serves as a superset of all diagnostics tools.</span></span> <span data-ttu-id="3fb02-210">除了追蹤，它還可以監視計量、收集記憶體傾印，以及收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="3fb02-210">In addition to traces, it can monitor metrics, collect memory dumps, and collect GC dumps.</span></span> <span data-ttu-id="3fb02-211">它是以 CLI 工具和 docker 映射的形式散發。</span><span class="sxs-lookup"><span data-stu-id="3fb02-211">It's distributed as both a CLI tool and a docker image.</span></span> <span data-ttu-id="3fb02-212">它會公開 REST API，並透過 REST 呼叫來收集診斷成品。</span><span class="sxs-lookup"><span data-stu-id="3fb02-212">It exposes a REST API, and the collection of diagnostic artifacts occurs through REST calls.</span></span>

<span data-ttu-id="3fb02-213">如需詳細資訊，請參閱 [dotnet-監視器簡介（實驗性工具）](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)。</span><span class="sxs-lookup"><span data-stu-id="3fb02-213">For more information, see [Introducing dotnet-monitor, an experimental tool](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).</span></span>

### <a name="consume-in-proc"></a><span data-ttu-id="3fb02-214">使用同進程</span><span class="sxs-lookup"><span data-stu-id="3fb02-214">Consume in-proc</span></span>

<span data-ttu-id="3fb02-215">您可以透過 API 使用計數器值 <xref:System.Diagnostics.Tracing.EventListener> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-215">You can consume the counter values via the <xref:System.Diagnostics.Tracing.EventListener> API.</span></span> <span data-ttu-id="3fb02-216"><xref:System.Diagnostics.Tracing.EventListener>是在您的應用程式中取用所有實例所寫入之任何事件的同進程方式 <xref:System.Diagnostics.Tracing.EventSource> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-216">An <xref:System.Diagnostics.Tracing.EventListener> is an in-proc way of consuming any events written by all instances of an <xref:System.Diagnostics.Tracing.EventSource> in your application.</span></span> <span data-ttu-id="3fb02-217">如需如何使用 API 的詳細資訊 `EventListener` ，請參閱 <xref:System.Diagnostics.Tracing.EventListener> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-217">For more information on how to use the `EventListener` API, see <xref:System.Diagnostics.Tracing.EventListener>.</span></span>

<span data-ttu-id="3fb02-218">首先，必須 <xref:System.Diagnostics.Tracing.EventSource> 啟用產生計數器值的。</span><span class="sxs-lookup"><span data-stu-id="3fb02-218">First, the <xref:System.Diagnostics.Tracing.EventSource> that produces the counter value needs to be enabled.</span></span> <span data-ttu-id="3fb02-219">覆寫 <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> 方法以在建立時取得通知 <xref:System.Diagnostics.Tracing.EventSource> ，如果是正確 <xref:System.Diagnostics.Tracing.EventSource> 的 EventCounters，您可以 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> 對其進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="3fb02-219">Override the <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> method to get a notification when an <xref:System.Diagnostics.Tracing.EventSource> is created, and if this is the correct <xref:System.Diagnostics.Tracing.EventSource> with your EventCounters, then you can call <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> on it.</span></span> <span data-ttu-id="3fb02-220">以下是範例覆寫：</span><span class="sxs-lookup"><span data-stu-id="3fb02-220">Here is an example override:</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a><span data-ttu-id="3fb02-221">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="3fb02-221">Sample code</span></span>

<span data-ttu-id="3fb02-222">以下範例類別會 <xref:System.Diagnostics.Tracing.EventListener> 印出 .net 執行時間的所有計數器名稱和值 <xref:System.Diagnostics.Tracing.EventSource> ，以便 `System.Runtime` 在某個時間間隔內 () 發佈其內部計數器。</span><span class="sxs-lookup"><span data-stu-id="3fb02-222">Here is a sample <xref:System.Diagnostics.Tracing.EventListener> class that prints out all the counter names and values from the .NET runtime's <xref:System.Diagnostics.Tracing.EventSource>, for publishing its internal counters (`System.Runtime`) at some interval.</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

<span data-ttu-id="3fb02-223">如上所示，呼叫時，您 _必須_ 確定引數 `"EventCounterIntervalSec"` 已設定引數 `filterPayload` <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3fb02-223">As shown above, you _must_ make sure the `"EventCounterIntervalSec"` argument is set in the `filterPayload` argument when calling <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>.</span></span> <span data-ttu-id="3fb02-224">否則，計數器將無法排清值，因為它不知道應該將它排清的間隔。</span><span class="sxs-lookup"><span data-stu-id="3fb02-224">Otherwise the counters will not be able to flush out values since it doesn't know at which interval it should be getting flushed out.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fb02-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fb02-225">See also</span></span>

- [<span data-ttu-id="3fb02-226">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="3fb02-226">dotnet-counters</span></span>](dotnet-counters.md)
- [<span data-ttu-id="3fb02-227">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="3fb02-227">dotnet-trace</span></span>](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
