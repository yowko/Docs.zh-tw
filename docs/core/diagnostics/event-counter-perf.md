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
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>教學課程：使用 .NET Core 中的 EventCounters 測量效能

**本文適用于：✔️** .net CORE 3.0 SDK 和更新版本

在本教學課程中，您將瞭解如何利用較 <xref:System.Diagnostics.Tracing.EventCounter> 高的事件頻率來測量效能。 您可以使用各種官方 .NET Core 套件、協力廠商提供者所發佈的[可用計數器](event-counters.md#available-counters)，或建立您自己的計量以進行監視。

在本教學課程中，您將：

> [!div class="checklist"]
>
> - 執行 <xref:System.Diagnostics.Tracing.EventSource> 。
> - 使用[dotnet](dotnet-counters.md)監視計數器。

## <a name="prerequisites"></a>必要條件

教學課程會使用：

- [.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更新版本。
- [dotnet-](dotnet-counters.md)用來監視事件計數器的計數器。
- 要診斷的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)應用程式。

## <a name="get-the-source"></a>取得來源

範例應用程式將用來做為監視的基礎。 [範例 ASP.NET Core 存放庫](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)可從範例瀏覽器取得。 您可以下載 zip 檔案，在下載後將它解壓縮，然後在您最愛的 IDE 中開啟它。 建立並執行應用程式，以確保其正常運作，然後停止應用程式。

## <a name="implement-an-eventsource"></a>執行 EventSource

對於每隔幾毫秒發生的事件，您會希望每個事件的額外負荷 (小於一毫秒) 。 否則，對效能的影響將會很重要。 記錄事件表示您要將內容寫入磁片。 如果磁片的速度不夠快，您將會遺失事件。 除了記錄事件本身之外，您還需要解決方案。

處理大量事件時，瞭解每個事件的量值不太實用。 大部分的時候，您只需要一些統計資料。 因此，您可以取得進程本身的統計資料，然後在一段時間內寫入事件一次來報告統計資料，這就是 <xref:System.Diagnostics.Tracing.EventCounter> 這麼做。

以下是如何執行的範例 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 。 建立名為*MinimalEventCounterSource.cs*的新檔案，並使用程式碼片段作為其來源：

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>這一行是 <xref:System.Diagnostics.Tracing.EventSource> 元件，而且不是的一部分 <xref:System.Diagnostics.Tracing.EventCounter> ，它是為了顯示，您可以將訊息與事件計數器一起記錄在一起。

## <a name="add-an-action-filter"></a>新增動作篩選準則

範例原始程式碼是 ASP.NET Core 專案。 您可以在全域加入[動作篩選準則](/aspnet/core/mvc/controllers/filters#action-filters)，以記錄總要求時間。 建立名為*LogRequestTimeFilterAttribute.cs*的新檔案，並使用下列程式碼：

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

動作篩選準則會在 <xref:System.Diagnostics.Stopwatch> 要求開始時啟動，並在完成後停止，並捕捉經過的時間。 總毫秒數會記錄到 `MinimalEventCounterSource` 單一實例。 為了套用此篩選準則，您必須將它新增至篩選集合。 在*Startup.cs*檔案中，更新 `ConfigureServices` 包含此篩選準則中的方法。

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>監視事件計數器

在 <xref:System.Diagnostics.Tracing.EventSource> 和自訂動作篩選準則上，建立並啟動應用程式。
您已將計量記錄到 <xref:System.Diagnostics.Tracing.EventCounter> ，但除非您從它存取統計資料，否則不會很有用。 若要取得統計資料，您必須 <xref:System.Diagnostics.Tracing.EventCounter> 建立計時器，使其盡可能地引發事件，以及接聽程式來捕捉事件。 若要這麼做，您可以使用[dotnet 計數器](dotnet-counters.md)。

使用 [ [dotnet-計數器 ps](dotnet-counters.md#dotnet-counters-ps) ] 命令，顯示可以監視的 .net 進程清單。

```console
dotnet-counters ps
```

使用命令輸出中的處理常式識別碼 `dotnet-counters ps` ，您可以使用下列命令開始監視事件計數器 `dotnet-counters monitor` ：

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

執行 `dotnet-counters monitor` 命令時，請在瀏覽器上按住<kbd>F5</kbd> ，以開始對端點發出連續要求 `https://localhost:5001/api/values` 。 幾秒後按<kbd>q</kbd>停止

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

`dotnet-counters monitor`命令非常適合用於主動監視。 不過，您可能會想要收集這些診斷計量以進行後續處理和分析。 為此，請使用 `dotnet-counters collect` 命令。 `collect`Switch 命令與 `monitor` 命令類似，但會接受一些額外的參數。 您可以指定所需的輸出檔案名和格式。 針對名為*diagnostics.js*的 JSON 檔案，請使用下列命令：

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

同樣地，當命令執行時，請在瀏覽器上按住<kbd>F5</kbd> ，以開始對端點發出連續要求 `https://localhost:5001/api/values` 。 幾秒後，按<kbd>q</kbd>鍵停止。 寫入檔案*上的diagnostics.js* 。 但寫入的 JSON 檔案不會縮排。為了方便閱讀，此處會縮排。

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

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [EventCounters](event-counters.md)
