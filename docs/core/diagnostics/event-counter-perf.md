---
title: 使用 .NET Core 中的 EventCounters 測量效能
description: 在本教學課程中，您將瞭解如何使用 EventCounters 來測量效能。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 7b4940e17d01e7ec5a50d11e3c818ecdec2d48cf
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2020
ms.locfileid: "88025000"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="22a05-103">教學課程：使用 .NET Core 中的 EventCounters 測量效能</span><span class="sxs-lookup"><span data-stu-id="22a05-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="22a05-104">**本文適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="22a05-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="22a05-105">在本教學課程中，您將瞭解如何利用較 <xref:System.Diagnostics.Tracing.EventCounter> 高的事件頻率來測量效能。</span><span class="sxs-lookup"><span data-stu-id="22a05-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="22a05-106">您可以使用各種官方 .NET Core 套件、協力廠商提供者所發佈的[可用計數器](event-counters.md#available-counters)，或建立您自己的計量以進行監視。</span><span class="sxs-lookup"><span data-stu-id="22a05-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="22a05-107">在本教學課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="22a05-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="22a05-108">執行 <xref:System.Diagnostics.Tracing.EventSource> 。</span><span class="sxs-lookup"><span data-stu-id="22a05-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="22a05-109">使用[dotnet](dotnet-counters.md)監視計數器。</span><span class="sxs-lookup"><span data-stu-id="22a05-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22a05-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="22a05-110">Prerequisites</span></span>

<span data-ttu-id="22a05-111">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="22a05-111">The tutorial uses:</span></span>

- <span data-ttu-id="22a05-112">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更新版本。</span><span class="sxs-lookup"><span data-stu-id="22a05-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="22a05-113">[dotnet-](dotnet-counters.md)用來監視事件計數器的計數器。</span><span class="sxs-lookup"><span data-stu-id="22a05-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="22a05-114">要診斷的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a05-114">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="22a05-115">取得來源</span><span class="sxs-lookup"><span data-stu-id="22a05-115">Get the source</span></span>

<span data-ttu-id="22a05-116">範例應用程式將用來做為監視的基礎。</span><span class="sxs-lookup"><span data-stu-id="22a05-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="22a05-117">[範例 ASP.NET Core 存放庫](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)可從範例瀏覽器取得。</span><span class="sxs-lookup"><span data-stu-id="22a05-117">The [sample ASP.NET Core repository](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="22a05-118">您可以下載 zip 檔案，在下載後將它解壓縮，然後在您最愛的 IDE 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="22a05-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="22a05-119">建立並執行應用程式，以確保其正常運作，然後停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a05-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="22a05-120">執行 EventSource</span><span class="sxs-lookup"><span data-stu-id="22a05-120">Implement an EventSource</span></span>

<span data-ttu-id="22a05-121">對於每隔幾毫秒發生的事件，您會希望每個事件的額外負荷 (小於一毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="22a05-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="22a05-122">否則，對效能的影響將會很重要。</span><span class="sxs-lookup"><span data-stu-id="22a05-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="22a05-123">記錄事件表示您要將內容寫入磁片。</span><span class="sxs-lookup"><span data-stu-id="22a05-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="22a05-124">如果磁片的速度不夠快，您將會遺失事件。</span><span class="sxs-lookup"><span data-stu-id="22a05-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="22a05-125">除了記錄事件本身之外，您還需要解決方案。</span><span class="sxs-lookup"><span data-stu-id="22a05-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="22a05-126">處理大量事件時，瞭解每個事件的量值不太實用。</span><span class="sxs-lookup"><span data-stu-id="22a05-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="22a05-127">大部分的時候，您只需要一些統計資料。</span><span class="sxs-lookup"><span data-stu-id="22a05-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="22a05-128">因此，您可以取得進程本身的統計資料，然後在一段時間內寫入事件一次來報告統計資料，這就是 <xref:System.Diagnostics.Tracing.EventCounter> 這麼做。</span><span class="sxs-lookup"><span data-stu-id="22a05-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="22a05-129">以下是如何執行的範例 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="22a05-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="22a05-130">建立名為*MinimalEventCounterSource.cs*的新檔案，並使用程式碼片段作為其來源：</span><span class="sxs-lookup"><span data-stu-id="22a05-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="22a05-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>這一行是 <xref:System.Diagnostics.Tracing.EventSource> 元件，而且不是的一部分 <xref:System.Diagnostics.Tracing.EventCounter> ，它是為了顯示，您可以將訊息與事件計數器一起記錄在一起。</span><span class="sxs-lookup"><span data-stu-id="22a05-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="22a05-132">新增動作篩選準則</span><span class="sxs-lookup"><span data-stu-id="22a05-132">Add an action filter</span></span>

<span data-ttu-id="22a05-133">範例原始程式碼是 ASP.NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="22a05-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="22a05-134">您可以在全域加入[動作篩選準則](/aspnet/core/mvc/controllers/filters#action-filters)，以記錄總要求時間。</span><span class="sxs-lookup"><span data-stu-id="22a05-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="22a05-135">建立名為*LogRequestTimeFilterAttribute.cs*的新檔案，並使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="22a05-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

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

<span data-ttu-id="22a05-136">動作篩選準則會在 <xref:System.Diagnostics.Stopwatch> 要求開始時啟動，並在完成後停止，並捕捉經過的時間。</span><span class="sxs-lookup"><span data-stu-id="22a05-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="22a05-137">總毫秒數會記錄到 `MinimalEventCounterSource` 單一實例。</span><span class="sxs-lookup"><span data-stu-id="22a05-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="22a05-138">為了套用此篩選準則，您必須將它新增至篩選集合。</span><span class="sxs-lookup"><span data-stu-id="22a05-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="22a05-139">在*Startup.cs*檔案中，更新 `ConfigureServices` 包含此篩選準則中的方法。</span><span class="sxs-lookup"><span data-stu-id="22a05-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="22a05-140">監視事件計數器</span><span class="sxs-lookup"><span data-stu-id="22a05-140">Monitor event counter</span></span>

<span data-ttu-id="22a05-141">在 <xref:System.Diagnostics.Tracing.EventSource> 和自訂動作篩選準則上，建立並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a05-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="22a05-142">您已將計量記錄到 <xref:System.Diagnostics.Tracing.EventCounter> ，但除非您從它存取統計資料，否則不會很有用。</span><span class="sxs-lookup"><span data-stu-id="22a05-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="22a05-143">若要取得統計資料，您必須 <xref:System.Diagnostics.Tracing.EventCounter> 建立計時器，使其盡可能地引發事件，以及接聽程式來捕捉事件。</span><span class="sxs-lookup"><span data-stu-id="22a05-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="22a05-144">若要這麼做，您可以使用[dotnet 計數器](dotnet-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="22a05-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="22a05-145">使用 [ [dotnet-計數器 ps](dotnet-counters.md#dotnet-counters-ps) ] 命令，顯示可以監視的 .net 進程清單。</span><span class="sxs-lookup"><span data-stu-id="22a05-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="22a05-146">使用命令輸出中的處理常式識別碼 `dotnet-counters ps` ，您可以使用下列命令開始監視事件計數器 `dotnet-counters monitor` ：</span><span class="sxs-lookup"><span data-stu-id="22a05-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="22a05-147">執行 `dotnet-counters monitor` 命令時，請在瀏覽器上按住<kbd>F5</kbd> ，以開始對端點發出連續要求 `https://localhost:5001/api/values` 。</span><span class="sxs-lookup"><span data-stu-id="22a05-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="22a05-148">幾秒後按<kbd>q</kbd>停止</span><span class="sxs-lookup"><span data-stu-id="22a05-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

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

<span data-ttu-id="22a05-149">`dotnet-counters monitor`命令非常適合用於主動監視。</span><span class="sxs-lookup"><span data-stu-id="22a05-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="22a05-150">不過，您可能會想要收集這些診斷計量以進行後續處理和分析。</span><span class="sxs-lookup"><span data-stu-id="22a05-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="22a05-151">為此，請使用 `dotnet-counters collect` 命令。</span><span class="sxs-lookup"><span data-stu-id="22a05-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="22a05-152">`collect`Switch 命令與 `monitor` 命令類似，但會接受一些額外的參數。</span><span class="sxs-lookup"><span data-stu-id="22a05-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="22a05-153">您可以指定所需的輸出檔案名和格式。</span><span class="sxs-lookup"><span data-stu-id="22a05-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="22a05-154">針對名為*diagnostics.js*的 JSON 檔案，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="22a05-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="22a05-155">同樣地，當命令執行時，請在瀏覽器上按住<kbd>F5</kbd> ，以開始對端點發出連續要求 `https://localhost:5001/api/values` 。</span><span class="sxs-lookup"><span data-stu-id="22a05-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="22a05-156">幾秒後，按<kbd>q</kbd>鍵停止。</span><span class="sxs-lookup"><span data-stu-id="22a05-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="22a05-157">寫入檔案*上的diagnostics.js* 。</span><span class="sxs-lookup"><span data-stu-id="22a05-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="22a05-158">但寫入的 JSON 檔案不會縮排。為了方便閱讀，此處會縮排。</span><span class="sxs-lookup"><span data-stu-id="22a05-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="22a05-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="22a05-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22a05-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="22a05-160">EventCounters</span></span>](event-counters.md)
