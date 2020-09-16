---
title: 使用 .NET Core 中的 EventCounters 測量效能
description: 在本教學課程中，您將瞭解如何使用 EventCounters 來測量效能。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: db9a0889d46cc4db02baac60cbed6f6e0ba6856b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538562"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>教學課程：在 .NET Core 中使用 EventCounters 測量效能

本文**適用于：✔️** .net CORE 3.0 SDK 和更新版本

在本教學課程中，您將瞭解如何 <xref:System.Diagnostics.Tracing.EventCounter> 使用高頻率的事件來測量效能。 您可以使用各種官方 .NET Core 套件、協力廠商提供者所發行的 [可用計數器](event-counters.md#available-counters) ，或建立您自己的計量來進行監視。

在本教學課程中，您將：

> [!div class="checklist"]
>
> - 執行 <xref:System.Diagnostics.Tracing.EventSource> 。
> - 使用 [dotnet 計數器](dotnet-counters.md)監視計數器。

## <a name="prerequisites"></a>Prerequisites

教學課程會使用：

- [.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。
- [dotnet-](dotnet-counters.md) 監視事件計數器的計數器。
- 要診斷的 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios) 應用程式。

## <a name="get-the-source"></a>取得來源

範例應用程式將用來作為監視的基礎。 範例瀏覽器提供 [範例 ASP.NET Core 存放庫](/samples/dotnet/samples/diagnostic-scenarios) 。 您可以下載 zip 檔案，並在下載之後將它解壓縮，然後在您最愛的 IDE 中開啟它。 建立並執行應用程式，以確保其正常運作，然後停止應用程式。

## <a name="implement-an-eventsource"></a>執行 EventSource

針對每隔幾毫秒發生的事件，您會希望每個事件的額外負荷 (小於一毫秒的) 。 否則，對效能的影響將會很重要。 記錄事件表示您即將寫入磁片。 如果磁片的速度不夠快，您將會遺失事件。 您需要記錄事件本身以外的解決方案。

處理大量事件時，瞭解每個事件的量值並不實用。 在大部分的情況中，您只需要其中的一些統計資料。 因此，您可以取得程式本身的統計資料，然後在一段時間內撰寫一次事件來報告統計資料，這就是 <xref:System.Diagnostics.Tracing.EventCounter> 這麼做的。

以下是如何執行的範例 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 。 建立名為 *MinimalEventCounterSource.cs* 的新檔案，並使用程式碼片段作為其來源：

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>這一行是 <xref:System.Diagnostics.Tracing.EventSource> 元件，而且不屬於的一部分 <xref:System.Diagnostics.Tracing.EventCounter> ，而是要說明您可以同時記錄訊息與事件計數器。

## <a name="add-an-action-filter"></a>新增動作篩選

範例原始程式碼是 ASP.NET Core 專案。 您可以在全域新增可記錄要求時間總計的 [動作篩選準則](/aspnet/core/mvc/controllers/filters#action-filters) 。 建立名為 *LogRequestTimeFilterAttribute.cs*的新檔案，並使用下列程式碼：

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

動作篩選準則會在 <xref:System.Diagnostics.Stopwatch> 要求開始時啟動，並在完成後停止，以捕捉經過的時間。 總毫秒數會記錄到 `MinimalEventCounterSource` 單一實例。 為了套用此篩選準則，您必須將它新增至篩選集合。 在 *Startup.cs* 檔案中，更新 `ConfigureServices` 中的方法，包括這個篩選準則。

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>Monitor 事件計數器

在 <xref:System.Diagnostics.Tracing.EventSource> 和自訂動作篩選準則上執行時，建立並啟動應用程式。
您將計量記錄至 <xref:System.Diagnostics.Tracing.EventCounter> ，但除非您存取它的統計資料，否則不會很有用。 若要取得統計資料，您必須 <xref:System.Diagnostics.Tracing.EventCounter> 建立一個會隨著您想要的事件而引發的計時器，以及用來捕捉事件的接聽程式，以啟用。 若要這樣做，您可以使用 [dotnet 計數器](dotnet-counters.md)。

使用 [dotnet 計數器 ps](dotnet-counters.md#dotnet-counters-ps) 命令可顯示可監視的 .net 進程清單。

```console
dotnet-counters ps
```

從命令的輸出使用程式識別碼 `dotnet-counters ps` ，您可以使用下列命令來開始監視事件計數器 `dotnet-counters monitor` ：

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

當命令執行時 `dotnet-counters monitor` ，請在瀏覽器上保留 <kbd>F5</kbd> 以開始向端點發出持續要求 `https://localhost:5001/api/values` 。 在幾秒鐘後按<kbd>q</kbd>鍵停止

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

此 `dotnet-counters monitor` 命令非常適合主動監視。 不過，您可能會想要收集這些診斷計量以進行後置處理和分析。 若要這樣做，請使用 `dotnet-counters collect` 命令。 `collect`Switch 命令與 `monitor` 命令類似，但可接受幾個額外的參數。 您可以指定所需的輸出檔案名和格式。 針對名為 *diagnostics.js* 的 JSON 檔案，請使用下列命令：

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

同樣地，當命令正在執行時，請在瀏覽器上保留 <kbd>F5</kbd> ，以開始向端點發出連續要求 `https://localhost:5001/api/values` 。 在幾秒鐘後，按 <kbd>q</kbd>鍵停止。 寫入檔案 * 上的diagnostics.js* 。 但是，寫入的 JSON 檔案不會縮排，為了方便閱讀，此處會縮排。

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
