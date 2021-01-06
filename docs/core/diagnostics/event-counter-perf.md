---
title: 使用 .NET Core 中的 EventCounters 測量效能
description: 在本教學課程中，您將瞭解如何使用 EventCounters 來測量效能。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 2ed7f234b685dab91ab275105d26b474e3bd1a87
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700739"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="ba1bf-103">教學課程：在 .NET Core 中使用 EventCounters 測量效能</span><span class="sxs-lookup"><span data-stu-id="ba1bf-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="ba1bf-104">本文 **適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ba1bf-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="ba1bf-105">在本教學課程中，您將瞭解如何 <xref:System.Diagnostics.Tracing.EventCounter> 使用高頻率的事件來測量效能。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="ba1bf-106">您可以使用各種官方 .NET Core 套件、協力廠商提供者所發行的 [可用計數器](available-counters.md) ，或建立您自己的計量來進行監視。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-106">You can use the [available counters](available-counters.md) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="ba1bf-107">在本教學課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ba1bf-108">執行 <xref:System.Diagnostics.Tracing.EventSource> 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="ba1bf-109">使用 [dotnet 計數器](dotnet-counters.md)監視計數器。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba1bf-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="ba1bf-110">Prerequisites</span></span>

<span data-ttu-id="ba1bf-111">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-111">The tutorial uses:</span></span>

- <span data-ttu-id="ba1bf-112">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="ba1bf-113">[dotnet-](dotnet-counters.md) 監視事件計數器的計數器。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="ba1bf-114">要診斷的 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="ba1bf-115">取得來源</span><span class="sxs-lookup"><span data-stu-id="ba1bf-115">Get the source</span></span>

<span data-ttu-id="ba1bf-116">範例應用程式將用來作為監視的基礎。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="ba1bf-117">範例瀏覽器提供 [範例 ASP.NET Core 存放庫](/samples/dotnet/samples/diagnostic-scenarios) 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="ba1bf-118">您可以下載 zip 檔案，並在下載之後將它解壓縮，然後在您最愛的 IDE 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="ba1bf-119">建立並執行應用程式，以確保其正常運作，然後停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="ba1bf-120">執行 EventSource</span><span class="sxs-lookup"><span data-stu-id="ba1bf-120">Implement an EventSource</span></span>

<span data-ttu-id="ba1bf-121">針對每隔幾毫秒發生的事件，您會希望每個事件的額外負荷 (小於一毫秒的) 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="ba1bf-122">否則，對效能的影響將會很重要。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="ba1bf-123">記錄事件表示您即將寫入磁片。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="ba1bf-124">如果磁片的速度不夠快，您將會遺失事件。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="ba1bf-125">您需要記錄事件本身以外的解決方案。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="ba1bf-126">處理大量事件時，瞭解每個事件的量值並不實用。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="ba1bf-127">在大部分的情況中，您只需要其中的一些統計資料。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="ba1bf-128">因此，您可以取得程式本身的統計資料，然後在一段時間內撰寫一次事件來報告統計資料，這就是 <xref:System.Diagnostics.Tracing.EventCounter> 這麼做的。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="ba1bf-129">以下是如何執行的範例 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="ba1bf-130">建立名為 *MinimalEventCounterSource.cs* 的新檔案，並使用程式碼片段作為其來源：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="ba1bf-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>這一行是 <xref:System.Diagnostics.Tracing.EventSource> 元件，而且不屬於的一部分 <xref:System.Diagnostics.Tracing.EventCounter> ，而是要說明您可以同時記錄訊息與事件計數器。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="ba1bf-132">新增動作篩選</span><span class="sxs-lookup"><span data-stu-id="ba1bf-132">Add an action filter</span></span>

<span data-ttu-id="ba1bf-133">範例原始程式碼是 ASP.NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="ba1bf-134">您可以在全域新增可記錄要求時間總計的 [動作篩選準則](/aspnet/core/mvc/controllers/filters#action-filters) 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="ba1bf-135">建立名為 *LogRequestTimeFilterAttribute.cs* 的新檔案，並使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="ba1bf-136">動作篩選準則會在 <xref:System.Diagnostics.Stopwatch> 要求開始時啟動，並在完成後停止，以捕捉經過的時間。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="ba1bf-137">總毫秒數會記錄到 `MinimalEventCounterSource` 單一實例。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="ba1bf-138">為了套用此篩選準則，您必須將它新增至篩選集合。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="ba1bf-139">在 *Startup.cs* 檔案中，更新 `ConfigureServices` 中的方法，包括這個篩選準則。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="ba1bf-140">Monitor 事件計數器</span><span class="sxs-lookup"><span data-stu-id="ba1bf-140">Monitor event counter</span></span>

<span data-ttu-id="ba1bf-141">在 <xref:System.Diagnostics.Tracing.EventSource> 和自訂動作篩選準則上執行時，建立並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="ba1bf-142">您將計量記錄至 <xref:System.Diagnostics.Tracing.EventCounter> ，但除非您存取它的統計資料，否則不會很有用。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="ba1bf-143">若要取得統計資料，您必須 <xref:System.Diagnostics.Tracing.EventCounter> 建立一個會隨著您想要的事件而引發的計時器，以及用來捕捉事件的接聽程式，以啟用。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="ba1bf-144">若要這樣做，您可以使用 [dotnet 計數器](dotnet-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="ba1bf-145">使用 [dotnet 計數器 ps](dotnet-counters.md#dotnet-counters-ps) 命令可顯示可監視的 .net 進程清單。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="ba1bf-146">從命令的輸出使用程式識別碼 `dotnet-counters ps` ，您可以使用下列命令來開始監視事件計數器 `dotnet-counters monitor` ：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="ba1bf-147">當命令執行時 `dotnet-counters monitor` ，請在瀏覽器上保留 <kbd>F5</kbd> 以開始向端點發出持續要求 `https://localhost:5001/api/values` 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="ba1bf-148">在幾秒鐘後按<kbd>q</kbd>鍵停止</span><span class="sxs-lookup"><span data-stu-id="ba1bf-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="ba1bf-149">此 `dotnet-counters monitor` 命令非常適合主動監視。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="ba1bf-150">不過，您可能會想要收集這些診斷計量以進行後置處理和分析。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="ba1bf-151">若要這樣做，請使用 `dotnet-counters collect` 命令。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="ba1bf-152">`collect`Switch 命令與 `monitor` 命令類似，但可接受幾個額外的參數。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="ba1bf-153">您可以指定所需的輸出檔案名和格式。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="ba1bf-154">針對名為 *diagnostics.js* 的 JSON 檔案，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="ba1bf-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="ba1bf-155">同樣地，當命令正在執行時，請在瀏覽器上保留 <kbd>F5</kbd> ，以開始向端點發出連續要求 `https://localhost:5001/api/values` 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="ba1bf-156">在幾秒鐘後，按 <kbd>q</kbd>鍵停止。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="ba1bf-157">寫入檔案 *上的diagnostics.js* 。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="ba1bf-158">但是，寫入的 JSON 檔案不會縮排，為了方便閱讀，此處會縮排。</span><span class="sxs-lookup"><span data-stu-id="ba1bf-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="ba1bf-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ba1bf-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba1bf-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="ba1bf-160">EventCounters</span></span>](event-counters.md)
