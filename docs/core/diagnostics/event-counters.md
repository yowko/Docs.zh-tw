---
title: .NET Core 中的 EventCounters
description: 在本文中，您將瞭解 EventCounters 是什麼、如何執行，以及如何使用它們。
ms.date: 08/07/2020
ms.openlocfilehash: fc2f945e3de732a81b9ce3fd82eff10e455cae87
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062960"
---
# <a name="eventcounters-in-net-core"></a><span data-ttu-id="b3f79-103">.NET Core 中的 EventCounters</span><span class="sxs-lookup"><span data-stu-id="b3f79-103">EventCounters in .NET Core</span></span>

<span data-ttu-id="b3f79-104">**本文適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b3f79-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="b3f79-105">EventCounters 是用於輕量、跨平臺且近乎即時效能標準集合的 .NET Core Api。</span><span class="sxs-lookup"><span data-stu-id="b3f79-105">EventCounters are .NET Core APIs used for lightweight, cross-platform, and near real-time performance metric collection.</span></span> <span data-ttu-id="b3f79-106">EventCounters 已新增為 Windows 上 .NET Framework 「效能計數器」的跨平臺替代方案。</span><span class="sxs-lookup"><span data-stu-id="b3f79-106">EventCounters were added as a cross-platform alternative to the "performance counters" of the .NET Framework on Windows.</span></span> <span data-ttu-id="b3f79-107">在本文中，您將瞭解 EventCounters 是什麼、如何執行，以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="b3f79-107">In this article you'll learn what EventCounters are, how to implement them, and how to consume them.</span></span>

<span data-ttu-id="b3f79-108">.NET Core 執行時間和一些 .NET 程式庫會使用 EventCounters （從 .NET Core 3.0 開始）發行基本的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="b3f79-108">The .NET Core runtime and a few .NET libraries publish basic diagnostics information using EventCounters starting in .NET Core 3.0.</span></span> <span data-ttu-id="b3f79-109">除了 .NET 執行時間所提供的 EventCounters 之外，您也可以選擇執行自己的 EventCounters。</span><span class="sxs-lookup"><span data-stu-id="b3f79-109">Apart from the EventCounters that are provided by the .NET runtime, you may choose to implement your own EventCounters.</span></span> <span data-ttu-id="b3f79-110">EventCounters 可以用來追蹤各種計量。</span><span class="sxs-lookup"><span data-stu-id="b3f79-110">EventCounters can be used to track various metrics.</span></span>

<span data-ttu-id="b3f79-111">即時 EventCounters 為的一部分 <xref:System.Diagnostics.Tracing.EventSource> ，並且會定期自動推送至接聽程式工具。</span><span class="sxs-lookup"><span data-stu-id="b3f79-111">EventCounters live as a part of an <xref:System.Diagnostics.Tracing.EventSource>, and are automatically pushed to listener tools on a regular basis.</span></span> <span data-ttu-id="b3f79-112">就像上的所有其他事件一樣 <xref:System.Diagnostics.Tracing.EventSource> ，您可以透過和 EventPipe 同時使用進程內和跨進程 <xref:System.Diagnostics.Tracing.EventListener> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-112">Like all other events on an <xref:System.Diagnostics.Tracing.EventSource>, they can be consumed both in-proc and out-of-proc via <xref:System.Diagnostics.Tracing.EventListener> and EventPipe.</span></span> <span data-ttu-id="b3f79-113">本文著重于 EventCounters 的跨平臺功能，並刻意排除 PerfView 和 ETW (Windows) 的事件追蹤，不過這兩者都可以搭配 EventCounters 使用。</span><span class="sxs-lookup"><span data-stu-id="b3f79-113">This article focuses on the cross-platform capabilities of EventCounters, and intentionally excludes PerfView and ETW (Event Tracing for Windows) - although both can be used with EventCounters.</span></span>

![EventCounters 同進程和跨進程圖表影像](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a><span data-ttu-id="b3f79-115">EventCounter API 總覽</span><span class="sxs-lookup"><span data-stu-id="b3f79-115">EventCounter API overview</span></span>

<span data-ttu-id="b3f79-116">計數器有兩個主要類別。</span><span class="sxs-lookup"><span data-stu-id="b3f79-116">There are two primary categories of counters.</span></span> <span data-ttu-id="b3f79-117">某些計數器適用于「速率」值，例如例外狀況總數、Gc 總數和要求總數。</span><span class="sxs-lookup"><span data-stu-id="b3f79-117">Some counters are for "rate" values, such as total number of exceptions, total number of GCs, and total number of requests.</span></span> <span data-ttu-id="b3f79-118">其他計數器則是「快照集」值，例如堆積使用量、CPU 使用量和工作集大小。</span><span class="sxs-lookup"><span data-stu-id="b3f79-118">Other counters are "snapshot" values, such as heap usage, CPU usage, and working set size.</span></span> <span data-ttu-id="b3f79-119">在上述每個類別的計數器中，有兩種類型的計數器會因取得其值的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="b3f79-119">Within each of these categories of counters, there are two types of counters that vary by how they get their value.</span></span> <span data-ttu-id="b3f79-120">輪詢計數器會透過回呼來抓取其值，而非輪詢計數器會在計數器實例上直接設定其值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-120">Polling counters retrieve their value via a callback, and non-polling counters have their values directly set on the counter instance.</span></span>

<span data-ttu-id="b3f79-121">這些計數器是由下列的實作為表示：</span><span class="sxs-lookup"><span data-stu-id="b3f79-121">The counters are represented by the following implementations:</span></span>

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

<span data-ttu-id="b3f79-122">事件接聽程式會指定測量間隔的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b3f79-122">An event listener specifies how long measurement intervals are.</span></span> <span data-ttu-id="b3f79-123">在每個間隔結束時，會將值傳送到每個計數器的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b3f79-123">At the end of each interval a value is transmitted to the listener for each counter.</span></span> <span data-ttu-id="b3f79-124">計數器的執行會決定要使用哪些 Api 和計算來產生每個間隔的值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-124">The implementations of a counter determine what APIs and calculations are used to produce the value each interval.</span></span>

1. <span data-ttu-id="b3f79-125">會 <xref:System.Diagnostics.Tracing.EventCounter> 記錄一組值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-125">The <xref:System.Diagnostics.Tracing.EventCounter> records a set of values.</span></span> <span data-ttu-id="b3f79-126"><xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>方法會將新的值加入至集合。</span><span class="sxs-lookup"><span data-stu-id="b3f79-126">The <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> method adds a new value to the set.</span></span> <span data-ttu-id="b3f79-127">在每個間隔中，會計算集合的統計摘要，例如 min、max 和 mean。</span><span class="sxs-lookup"><span data-stu-id="b3f79-127">With each interval, a statistical summary for the set is computed, such as the min, max, and mean.</span></span> <span data-ttu-id="b3f79-128">[Dotnet 計數器](dotnet-counters.md)工具一律會顯示平均值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-128">The [dotnet-counters](dotnet-counters.md) tool will always display the mean value.</span></span> <span data-ttu-id="b3f79-129">適用 <xref:System.Diagnostics.Tracing.EventCounter> 于描述一組不連續的作業。</span><span class="sxs-lookup"><span data-stu-id="b3f79-129">The <xref:System.Diagnostics.Tracing.EventCounter> is useful to describe a discrete set of operations.</span></span> <span data-ttu-id="b3f79-130">常見的用法可能包括監視最近 IO 作業的平均大小（以位元組為單位），或一組財務交易的平均貨幣值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-130">Common usage may include monitoring the average size in bytes of recent IO operations, or the average monetary value of a set of financial transactions.</span></span>

1. <span data-ttu-id="b3f79-131">會 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 記錄每個時間間隔的執行總計。</span><span class="sxs-lookup"><span data-stu-id="b3f79-131">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> records a running total for each time interval.</span></span> <span data-ttu-id="b3f79-132"><xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>方法會將新增至總計。</span><span class="sxs-lookup"><span data-stu-id="b3f79-132">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> method adds to the total.</span></span> <span data-ttu-id="b3f79-133">例如，如果在 `Increment()` 一段時間內呼叫了三次，且值為 `1` 、 `2` 和 `5` ，則的總計 `8` 會回報為此間隔的計數器值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-133">For example, if `Increment()` is called three times during one interval with values `1`, `2`, and `5`, then the running total of `8` will be reported as the counter value for this interval.</span></span> <span data-ttu-id="b3f79-134">[Dotnet 計數器](dotnet-counters.md)工具會將速率顯示為記錄的總/時間。</span><span class="sxs-lookup"><span data-stu-id="b3f79-134">The [dotnet-counters](dotnet-counters.md) tool will display the rate as the recorded total / time.</span></span> <span data-ttu-id="b3f79-135">適用 <xref:System.Diagnostics.Tracing.IncrementingEventCounter> 于測量動作發生的頻率，例如每秒處理的要求數目。</span><span class="sxs-lookup"><span data-stu-id="b3f79-135">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> is useful to measure how frequently an action is occurring, such as the number of requests processed per second.</span></span>

1. <span data-ttu-id="b3f79-136"><xref:System.Diagnostics.Tracing.PollingCounter>會使用回呼來判斷所報告的值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-136">The <xref:System.Diagnostics.Tracing.PollingCounter> uses a callback to determine the value that is reported.</span></span> <span data-ttu-id="b3f79-137">在每個時間間隔中，會叫用使用者提供的回呼函式，並使用傳回值做為計數器值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-137">With each time interval, the user provided callback function is invoked and the return value is used as the counter value.</span></span> <span data-ttu-id="b3f79-138"><xref:System.Diagnostics.Tracing.PollingCounter>可以用來查詢來自外部來源的計量，例如取得磁片上目前可用的位元組。</span><span class="sxs-lookup"><span data-stu-id="b3f79-138">A <xref:System.Diagnostics.Tracing.PollingCounter> can be used to query a metric from an external source, for example getting the current free bytes on a disk.</span></span> <span data-ttu-id="b3f79-139">它也可以用來報告應用程式可以視需要計算的自訂統計資料。</span><span class="sxs-lookup"><span data-stu-id="b3f79-139">It can also be used to report custom statistics that can be computed on demand by an application.</span></span> <span data-ttu-id="b3f79-140">範例包括報告最近要求延遲的第95個百分位數，或快取的目前叫用或遺漏比例。</span><span class="sxs-lookup"><span data-stu-id="b3f79-140">Examples include reporting the 95th percentile of recent request latencies, or the current hit or miss ratio of a cache.</span></span>

1. <span data-ttu-id="b3f79-141">會 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 使用回呼來判斷回報的遞增值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-141">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses a callback to determine the reported increment value.</span></span> <span data-ttu-id="b3f79-142">在每個時間間隔內，會叫用回呼，然後在目前的調用與最後一個調用之間的差異是報告的值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-142">With each time interval, the callback is invoked, and then the difference between the current invocation, and the last invocation is the reported value.</span></span> <span data-ttu-id="b3f79-143">[Dotnet 計數器](dotnet-counters.md)工具一律會以速率（回報的值/時間）顯示差異。</span><span class="sxs-lookup"><span data-stu-id="b3f79-143">The [dotnet-counters](dotnet-counters.md) tool will always display the difference as a rate, the reported value / time.</span></span> <span data-ttu-id="b3f79-144">如果在每次發生時都不能呼叫 API，此計數器很有用，但可以查詢發生的總次數。</span><span class="sxs-lookup"><span data-stu-id="b3f79-144">This counter is useful when it isn't feasible to call an API on each occurrence, but it's possible to query the total number of occurrences.</span></span> <span data-ttu-id="b3f79-145">例如，您可以報告每秒寫入檔案的位元組數目，即使每次寫入一個位元組，都不會有通知。</span><span class="sxs-lookup"><span data-stu-id="b3f79-145">For example, you could report the number of bytes written to a file per second, even without a notification each time a byte is written.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="b3f79-146">執行 EventSource</span><span class="sxs-lookup"><span data-stu-id="b3f79-146">Implement an EventSource</span></span>

<span data-ttu-id="b3f79-147">下列程式碼會實 <xref:System.Diagnostics.Tracing.EventSource> 作為命名提供者公開的範例 `"Sample.EventCounter.Minimal"` 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-147">The following code implements a sample <xref:System.Diagnostics.Tracing.EventSource> exposed as the named `"Sample.EventCounter.Minimal"` provider.</span></span> <span data-ttu-id="b3f79-148">此來源包含 <xref:System.Diagnostics.Tracing.EventCounter> 代表要求處理時間的。</span><span class="sxs-lookup"><span data-stu-id="b3f79-148">This source contains an <xref:System.Diagnostics.Tracing.EventCounter> representing request processing time.</span></span> <span data-ttu-id="b3f79-149">這類計數器的名稱 (，也就是它在來源) 中的唯一識別碼和顯示名稱，這兩者都是由接聽程式工具（例如[dotnet-counter](dotnet-counters.md)）所使用。</span><span class="sxs-lookup"><span data-stu-id="b3f79-149">Such a counter has a name (that is, its unique ID in the source) and a display name, both used by listener tools such as [dotnet-counter](dotnet-counters.md).</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="b3f79-150">您可以使用 `dotnet-counters ps` 來顯示可以監視的 .net 進程清單：</span><span class="sxs-lookup"><span data-stu-id="b3f79-150">You use `dotnet-counters ps` to display a list of .NET processes that can be monitored:</span></span>

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

<span data-ttu-id="b3f79-151">將 <xref:System.Diagnostics.Tracing.EventSource> 名稱傳遞給 `counter_list` 參數以開始監視計數器：</span><span class="sxs-lookup"><span data-stu-id="b3f79-151">Pass the <xref:System.Diagnostics.Tracing.EventSource> name to the `counter_list` switch to start monitoring your counter:</span></span>

```console
dotnet-counters monitor --process-id 1400180 Sample.EventCounter.Minimal
```

<span data-ttu-id="b3f79-152">下列範例顯示監視輸出：</span><span class="sxs-lookup"><span data-stu-id="b3f79-152">The following example shows monitor output:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

<span data-ttu-id="b3f79-153">按<kbd>q</kbd>停止監視命令。</span><span class="sxs-lookup"><span data-stu-id="b3f79-153">Press <kbd>q</kbd> to stop the monitoring command.</span></span>

#### <a name="conditional-counters"></a><span data-ttu-id="b3f79-154">條件式計數器</span><span class="sxs-lookup"><span data-stu-id="b3f79-154">Conditional counters</span></span>

<span data-ttu-id="b3f79-155">在執行時 <xref:System.Diagnostics.Tracing.EventSource> ，包含的計數器可以在 <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> 使用值呼叫方法時，有條件地具現化 <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> `EventCommand.Enable` 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-155">When implementing an <xref:System.Diagnostics.Tracing.EventSource>, the containing counters can be conditionally instantiated when the <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> method is called with a <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> value of `EventCommand.Enable`.</span></span> <span data-ttu-id="b3f79-156">若要安全地具現化計數器實例（如果它是 `null` ），請使用[null 聯合指派運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="b3f79-156">To safely instantiate a counter instance only if it is `null`, use the [null-coalescing assignment operator](../../csharp/language-reference/operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="b3f79-157">此外，自訂方法可以評估 <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> 方法，以判斷是否已啟用目前的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b3f79-157">Additionally, custom methods can evaluate the <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> method to determine whether or not the current event source is enabled.</span></span>

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> <span data-ttu-id="b3f79-158">條件式計數器是有條件地具現化的計數器（微優化）。</span><span class="sxs-lookup"><span data-stu-id="b3f79-158">Conditional counters are counters that are conditionally instantiated, a micro-optimization.</span></span> <span data-ttu-id="b3f79-159">在通常不會使用計數器的情況下，執行時間會採用此模式，以節省毫秒的分數。</span><span class="sxs-lookup"><span data-stu-id="b3f79-159">The runtime adopts this pattern for scenarios where counters are normally not used, to save a fraction of a millisecond.</span></span>

### <a name="net-core-runtime-example-counters"></a><span data-ttu-id="b3f79-160">.NET Core 執行時間範例計數器</span><span class="sxs-lookup"><span data-stu-id="b3f79-160">.NET Core runtime example counters</span></span>

<span data-ttu-id="b3f79-161">.NET Core 執行時間中有許多絕佳的範例實現。</span><span class="sxs-lookup"><span data-stu-id="b3f79-161">There are many great example implementations in the .NET Core runtime.</span></span> <span data-ttu-id="b3f79-162">以下是用來追蹤應用程式工作集大小之計數器的執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="b3f79-162">Here is the runtime implementation for the counter that tracks the working set size of the application.</span></span>

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

<span data-ttu-id="b3f79-163"><xref:System.Diagnostics.Tracing.PollingCounter>會報告應用程式的目前對應至進程 (工作集) 的實體記憶體量，因為它會在一段時間內捕捉計量。</span><span class="sxs-lookup"><span data-stu-id="b3f79-163">The <xref:System.Diagnostics.Tracing.PollingCounter> reports the current amount of physical memory mapped to the process (working set) of the app, since it captures a metric at a moment in time.</span></span> <span data-ttu-id="b3f79-164">輪詢值的回呼是提供的 lambda 運算式，這只是對 API 的呼叫 <xref:System.Environment.WorkingSet?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-164">The callback for polling a value is the provided lambda expression, which is just a call to the <xref:System.Environment.WorkingSet?displayProperty=fullName> API.</span></span> <span data-ttu-id="b3f79-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName>和 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> 是選擇性屬性，可設定來協助計數器的取用者端更清楚地顯示值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> and <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> are optional properties that can be set to help the consumer side of the counter to display the value more clearly.</span></span> <span data-ttu-id="b3f79-166">例如， [dotnet 計數器](dotnet-counters.md)會使用這些屬性來顯示更容易顯示的計數器名稱版本。</span><span class="sxs-lookup"><span data-stu-id="b3f79-166">For example, [dotnet-counters](dotnet-counters.md) uses these properties to display the more display-friendly version of the counter names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3f79-167">`DisplayName`屬性未當地語系化。</span><span class="sxs-lookup"><span data-stu-id="b3f79-167">The `DisplayName` properties are not localized.</span></span>

<span data-ttu-id="b3f79-168">對於 <xref:System.Diagnostics.Tracing.PollingCounter> 、和，則 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 不需要執行任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="b3f79-168">For the <xref:System.Diagnostics.Tracing.PollingCounter>, and the <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>, nothing else needs to be done.</span></span> <span data-ttu-id="b3f79-169">它們都會以取用者要求的間隔來輪詢值本身。</span><span class="sxs-lookup"><span data-stu-id="b3f79-169">They both poll the values themselves at an interval requested by the consumer.</span></span>

<span data-ttu-id="b3f79-170">以下是使用所實作為執行時間計數器的範例 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-170">Here is an example of a runtime counter implemented using <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>.</span></span>

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

<span data-ttu-id="b3f79-171">會 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 使用 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API 來報告總鎖定爭用計數的增量。</span><span class="sxs-lookup"><span data-stu-id="b3f79-171">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses the <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API to report the increment of the total lock contention count.</span></span> <span data-ttu-id="b3f79-172"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>屬性是選擇性的，但在使用時，它可以針對最適合顯示計數器的時間間隔提供提示。</span><span class="sxs-lookup"><span data-stu-id="b3f79-172">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> property is optional, but when used it can provide a hint for what time interval the counter is best displayed at.</span></span> <span data-ttu-id="b3f79-173">例如，鎖定爭用計數最好顯示為_每秒計數_，因此其 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 設定為一秒。</span><span class="sxs-lookup"><span data-stu-id="b3f79-173">For example, the lock contention count is best displayed as _count per second_, so its <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is set to one second.</span></span> <span data-ttu-id="b3f79-174">顯示速率可以針對不同類型的速率計數器進行調整。</span><span class="sxs-lookup"><span data-stu-id="b3f79-174">The display rate can be adjusted for different types of rate counters.</span></span>

> [!NOTE]
> <span data-ttu-id="b3f79-175">不 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 是_not_由[dotnet 計數器](dotnet-counters.md)使用，而且事件接聽程式不需要使用它。</span><span class="sxs-lookup"><span data-stu-id="b3f79-175">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is _not_ used by [dotnet-counters](dotnet-counters.md), and event listeners are not required to use it.</span></span>

<span data-ttu-id="b3f79-176">在[.net 運行](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs)時間存放庫中，您可以使用更多的計數器來做為參考。</span><span class="sxs-lookup"><span data-stu-id="b3f79-176">There are more counter implementations to use as a reference in the [.NET runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) repo.</span></span>

## <a name="concurrency"></a><span data-ttu-id="b3f79-177">並行</span><span class="sxs-lookup"><span data-stu-id="b3f79-177">Concurrency</span></span>

> [!TIP]
> <span data-ttu-id="b3f79-178">EventCounters API 不保證執行緒的安全。</span><span class="sxs-lookup"><span data-stu-id="b3f79-178">The EventCounters API does not guarantee thread safety.</span></span> <span data-ttu-id="b3f79-179">當 <xref:System.Diagnostics.Tracing.PollingCounter> 多個執行緒呼叫傳遞給或實例的委派時 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> ，您必須負責確保委派的執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="b3f79-179">When the delegates passed to <xref:System.Diagnostics.Tracing.PollingCounter> or <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> instances are called by multiple threads, it's your responsibility to guarantee the delegates' thread-safety.</span></span>

<span data-ttu-id="b3f79-180">例如，請考慮下列事項 <xref:System.Diagnostics.Tracing.EventSource> 以追蹤要求。</span><span class="sxs-lookup"><span data-stu-id="b3f79-180">For example, consider the following <xref:System.Diagnostics.Tracing.EventSource> to keep track of requests.</span></span>

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

<span data-ttu-id="b3f79-181">`AddRequest()`方法可以從要求處理常式呼叫，而且會 `RequestRateCounter` 以計數器取用者所指定的間隔來輪詢值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-181">The `AddRequest()` method can be called from a request handler, and the `RequestRateCounter` polls the value at the interval specified by the consumer of the counter.</span></span> <span data-ttu-id="b3f79-182">不過， `AddRequest()` 方法可以同時由多個執行緒呼叫，並將競爭條件放在 `_requestCount` 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-182">However, the `AddRequest()` method can be called by multiple threads at once, putting a race condition on `_requestCount`.</span></span> <span data-ttu-id="b3f79-183">以執行緒安全的替代方式，遞增 `_requestCount` 會使用 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-183">A thread-safe alternative way to increment the `_requestCount` is to use <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span>

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

## <a name="consume-eventcounters"></a><span data-ttu-id="b3f79-184">使用 EventCounters</span><span class="sxs-lookup"><span data-stu-id="b3f79-184">Consume EventCounters</span></span>

<span data-ttu-id="b3f79-185">有兩種主要的方式可使用 EventCounters （不論是在進程中或跨進程）。</span><span class="sxs-lookup"><span data-stu-id="b3f79-185">There are two primary ways of consuming EventCounters, either in-proc, or out-of-proc.</span></span> <span data-ttu-id="b3f79-186">EventCounters 的耗用量可以區別成各種取用技術的三層。</span><span class="sxs-lookup"><span data-stu-id="b3f79-186">The consumption of EventCounters can be distinguished into three layers of various consuming technologies.</span></span>

- <span data-ttu-id="b3f79-187">透過 ETW 或 EventPipe 傳輸原始資料流程中的事件：</span><span class="sxs-lookup"><span data-stu-id="b3f79-187">Transporting events in a raw stream via ETW or EventPipe:</span></span>
  - <span data-ttu-id="b3f79-188">ETW Api 隨附于 Windows 作業系統，而 EventPipe 可透過[.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)或診斷[IPC 通訊協定](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)來存取。</span><span class="sxs-lookup"><span data-stu-id="b3f79-188">ETW APIs come with the Windows OS, and EventPipe is accessible as a [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console), or the diagnostic [IPC protocol](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>
- <span data-ttu-id="b3f79-189">將二進位事件資料流程解碼成事件：</span><span class="sxs-lookup"><span data-stu-id="b3f79-189">Decoding the binary event stream into events:</span></span>
  - <span data-ttu-id="b3f79-190">[TraceEvent 程式庫](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)會同時處理 ETW 和 EventPipe 資料流程格式。</span><span class="sxs-lookup"><span data-stu-id="b3f79-190">The [TraceEvent library](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) handles both ETW and EventPipe stream formats.</span></span>
- <span data-ttu-id="b3f79-191">命令列和 GUI 工具：</span><span class="sxs-lookup"><span data-stu-id="b3f79-191">Command-line and GUI tools:</span></span>
  - <span data-ttu-id="b3f79-192">像是 PerfView (ETW 或 EventPipe) 的工具、dotnet 計數器 (僅 EventPipe) ，以及 dotnet 監視器 (僅) EventPipe。</span><span class="sxs-lookup"><span data-stu-id="b3f79-192">Tools like PerfView (ETW or EventPipe), dotnet-counters (EventPipe only), and dotnet-monitor (EventPipe only).</span></span>

### <a name="consume-out-of-proc"></a><span data-ttu-id="b3f79-193">耗用進程外</span><span class="sxs-lookup"><span data-stu-id="b3f79-193">Consume out-of-proc</span></span>

<span data-ttu-id="b3f79-194">使用 EventCounters 跨進程是非常常見的方法。</span><span class="sxs-lookup"><span data-stu-id="b3f79-194">Consuming EventCounters out-of-proc is a very common approach.</span></span> <span data-ttu-id="b3f79-195">您可以使用[dotnet](dotnet-counters.md) ，透過 EventPipe 以跨平臺方式取用這些計數器。</span><span class="sxs-lookup"><span data-stu-id="b3f79-195">You can use [dotnet-counters](dotnet-counters.md) to consume them in a cross-platform manner via an EventPipe.</span></span> <span data-ttu-id="b3f79-196">此 `dotnet-counters` 工具是一個跨平臺 DOTNET CLI 全域工具，可用來監視計數器值。</span><span class="sxs-lookup"><span data-stu-id="b3f79-196">The `dotnet-counters` tool is a cross-platform dotnet CLI global tool that can be used to monitor the counter values.</span></span> <span data-ttu-id="b3f79-197">若要瞭解如何使用 `dotnet-counters` 監視計數器，請參閱[dotnet-計數器](dotnet-counters.md)，或[使用 EventCounters 的測量效能](event-counter-perf.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="b3f79-197">To find out how to use `dotnet-counters` to monitor your counters, see [dotnet-counters](dotnet-counters.md), or work through the [Measure performance using EventCounters](event-counter-perf.md) tutorial.</span></span>

#### <a name="dotnet-trace"></a><span data-ttu-id="b3f79-198">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="b3f79-198">dotnet-trace</span></span>

<span data-ttu-id="b3f79-199">此 `dotnet-trace` 工具可用來透過 EventPipe 使用計數器資料。</span><span class="sxs-lookup"><span data-stu-id="b3f79-199">The `dotnet-trace` tool can be used to consume the counter data through an EventPipe.</span></span> <span data-ttu-id="b3f79-200">以下是使用 `dotnet-trace` 來收集計數器資料的範例。</span><span class="sxs-lookup"><span data-stu-id="b3f79-200">Here is an example using `dotnet-trace` to collect counter data.</span></span>

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

<span data-ttu-id="b3f79-201">如需有關如何在一段時間內收集計數器值的詳細資訊，請參閱[dotnet 追蹤](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time)檔。</span><span class="sxs-lookup"><span data-stu-id="b3f79-201">For more information on how to collect counter values over time, see the [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) documentation.</span></span>

#### <a name="azure-application-insights"></a><span data-ttu-id="b3f79-202">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="b3f79-202">Azure Application Insights</span></span>

<span data-ttu-id="b3f79-203">Azure 監視器可以使用 EventCounters，特別是 Azure 應用程式深入解析。</span><span class="sxs-lookup"><span data-stu-id="b3f79-203">EventCounters can be consumed by Azure Monitor, specifically Azure Application Insights.</span></span> <span data-ttu-id="b3f79-204">可以新增和移除計數器，您可以隨意指定自訂計數器或已知的計數器。</span><span class="sxs-lookup"><span data-stu-id="b3f79-204">Counters can be added and removed, and you're free to specify custom counters, or well-known counters.</span></span> <span data-ttu-id="b3f79-205">如需詳細資訊，請參閱[自訂要收集的計數器](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)。</span><span class="sxs-lookup"><span data-stu-id="b3f79-205">For more information, see [Customizing counters to be collected](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).</span></span>

#### <a name="dotnet-monitor"></a><span data-ttu-id="b3f79-206">dotnet-監視</span><span class="sxs-lookup"><span data-stu-id="b3f79-206">dotnet-monitor</span></span>

<span data-ttu-id="b3f79-207">此 `dotnet-monitor` 工具是一個實驗性工具，可讓您更輕鬆地存取 .net 進程中的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="b3f79-207">The `dotnet-monitor` tool is an experimental tool that makes it easier to get access to diagnostics information in a .NET process.</span></span> <span data-ttu-id="b3f79-208">此工具可做為所有診斷工具的超集合。</span><span class="sxs-lookup"><span data-stu-id="b3f79-208">The tool serves as a superset of all diagnostics tools.</span></span> <span data-ttu-id="b3f79-209">除了追蹤，它還可以監視計量、收集記憶體傾印，以及收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="b3f79-209">In addition to traces, it can monitor metrics, collect memory dumps, and collect GC dumps.</span></span> <span data-ttu-id="b3f79-210">它會同時散發為 CLI 工具和 docker 映射。</span><span class="sxs-lookup"><span data-stu-id="b3f79-210">It's distributed as both a CLI tool and a docker image.</span></span> <span data-ttu-id="b3f79-211">它會公開 REST API，而診斷成品的集合會透過 REST 呼叫進行。</span><span class="sxs-lookup"><span data-stu-id="b3f79-211">It exposes a REST API, and the collection of diagnostic artifacts occurs through REST calls.</span></span>

<span data-ttu-id="b3f79-212">如需詳細資訊，請參閱[dotnet-監視器簡介（實驗性工具）](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)。</span><span class="sxs-lookup"><span data-stu-id="b3f79-212">For more information, see [Introducing dotnet-monitor, an experimental tool](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).</span></span>

### <a name="consume-in-proc"></a><span data-ttu-id="b3f79-213">耗用內部進程</span><span class="sxs-lookup"><span data-stu-id="b3f79-213">Consume in-proc</span></span>

<span data-ttu-id="b3f79-214">您可以透過 API 取用計數器值 <xref:System.Diagnostics.Tracing.EventListener> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-214">You can consume the counter values via the <xref:System.Diagnostics.Tracing.EventListener> API.</span></span> <span data-ttu-id="b3f79-215"><xref:System.Diagnostics.Tracing.EventListener>是使用應用程式中所有實例所寫入之任何事件的同進程方式 <xref:System.Diagnostics.Tracing.EventSource> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-215">An <xref:System.Diagnostics.Tracing.EventListener> is an in-proc way of consuming any events written by all instances of an <xref:System.Diagnostics.Tracing.EventSource> in your application.</span></span> <span data-ttu-id="b3f79-216">如需有關如何使用 API 的詳細資訊 `EventListener` ，請參閱 <xref:System.Diagnostics.Tracing.EventListener> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-216">For more information on how to use the `EventListener` API, see <xref:System.Diagnostics.Tracing.EventListener>.</span></span>

<span data-ttu-id="b3f79-217">首先，必須 <xref:System.Diagnostics.Tracing.EventSource> 啟用產生計數器值的。</span><span class="sxs-lookup"><span data-stu-id="b3f79-217">First, the <xref:System.Diagnostics.Tracing.EventSource> that produces the counter value needs to be enabled.</span></span> <span data-ttu-id="b3f79-218">覆寫 <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> 方法以在建立時取得通知 <xref:System.Diagnostics.Tracing.EventSource> ，如果這是 <xref:System.Diagnostics.Tracing.EventSource> 您 EventCounters 的正確，您可以 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> 在其上呼叫。</span><span class="sxs-lookup"><span data-stu-id="b3f79-218">Override the <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> method to get a notification when an <xref:System.Diagnostics.Tracing.EventSource> is created, and if this is the correct <xref:System.Diagnostics.Tracing.EventSource> with your EventCounters, then you can call <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> on it.</span></span> <span data-ttu-id="b3f79-219">以下是範例覆寫：</span><span class="sxs-lookup"><span data-stu-id="b3f79-219">Here is an example override:</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a><span data-ttu-id="b3f79-220">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="b3f79-220">Sample code</span></span>

<span data-ttu-id="b3f79-221">以下範例類別會 <xref:System.Diagnostics.Tracing.EventListener> 從 .net 執行時間中列印出所有的計數器名稱和值 <xref:System.Diagnostics.Tracing.EventSource> ，以 `System.Runtime` 在某個間隔) 發佈其內部計數器 (。</span><span class="sxs-lookup"><span data-stu-id="b3f79-221">Here is a sample <xref:System.Diagnostics.Tracing.EventListener> class that prints out all the counter names and values from the .NET runtime's <xref:System.Diagnostics.Tracing.EventSource>, for publishing its internal counters (`System.Runtime`) at some interval.</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

<span data-ttu-id="b3f79-222">如上所示，當呼叫時，您_必須_確定引數 `"EventCounterIntervalSec"` 中已設定引數 `filterPayload` <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3f79-222">As shown above, you _must_ make sure the `"EventCounterIntervalSec"` argument is set in the `filterPayload` argument when calling <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>.</span></span> <span data-ttu-id="b3f79-223">否則，計數器將無法排清值，因為它不知道應該要清除的間隔。</span><span class="sxs-lookup"><span data-stu-id="b3f79-223">Otherwise the counters will not be able to flush out values since it doesn't know at which interval it should be getting flushed out.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3f79-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f79-224">See also</span></span>

- [<span data-ttu-id="b3f79-225">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b3f79-225">dotnet-counters</span></span>](dotnet-counters.md)
- [<span data-ttu-id="b3f79-226">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="b3f79-226">dotnet-trace</span></span>](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
