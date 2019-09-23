---
title: 應用程式效能管理-WCF 開發人員的 gRPC
description: ASP.NET Core gRPC 應用程式的記錄、計量和追蹤。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e4c32d057c1ac143e18a4a3ddc83dd8b1f62800
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184607"
---
# <a name="application-performance-management"></a><span data-ttu-id="a196f-103">應用程式效能管理</span><span class="sxs-lookup"><span data-stu-id="a196f-103">Application Performance Management</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a196f-104">在 Kubernetes 這類現代化生產環境中，必須能夠監視應用程式以確保其以最佳狀態執行，這點非常重要。</span><span class="sxs-lookup"><span data-stu-id="a196f-104">In modern production environments like Kubernetes, it's very important to be able to monitor applications to ensure they're running optimally.</span></span> <span data-ttu-id="a196f-105">記錄和計量等顧慮也不重要。</span><span class="sxs-lookup"><span data-stu-id="a196f-105">Concerns like logging and metrics have never been more important.</span></span> <span data-ttu-id="a196f-106">ASP.NET Core （包括 gRPC）具有產生和記錄管理檔訊息和計量資料的一流支援，以及*追蹤*資料。</span><span class="sxs-lookup"><span data-stu-id="a196f-106">ASP.NET Core, including gRPC, has first-class support for producing and managing log messages and metrics data, as well as *tracing* data.</span></span> <span data-ttu-id="a196f-107">本節將更詳細地探索這些區域。</span><span class="sxs-lookup"><span data-stu-id="a196f-107">This section will explore these areas in more details.</span></span>

## <a name="logging-vs-metrics"></a><span data-ttu-id="a196f-108">記錄與計量</span><span class="sxs-lookup"><span data-stu-id="a196f-108">Logging vs Metrics</span></span>

<span data-ttu-id="a196f-109">在查看執行詳細資料之前，必須先瞭解記錄與計量之間的差異。</span><span class="sxs-lookup"><span data-stu-id="a196f-109">Before looking at the implementation details, it's necessary to understand the difference between logging and metrics.</span></span>

<span data-ttu-id="a196f-110">記錄會考慮文字訊息，記錄系統中發生之專案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a196f-110">Logging is concerned with text messages that record detailed information about things that have happened in the system.</span></span> <span data-ttu-id="a196f-111">記錄檔訊息可能包含例外狀況資料（例如堆疊追蹤），或提供訊息內容的結構化資料。</span><span class="sxs-lookup"><span data-stu-id="a196f-111">Log messages may include exception data like stack traces, or structured data that provides context about the message.</span></span> <span data-ttu-id="a196f-112">記錄輸出通常會寫入可搜尋的文字存放區。</span><span class="sxs-lookup"><span data-stu-id="a196f-112">Logging output is commonly written to a searchable text store.</span></span>

<span data-ttu-id="a196f-113">計量是指設計成使用儀表板中的圖表和圖形來匯總和呈現的數值資料，可提供應用程式整體健全狀況和效能的觀點。</span><span class="sxs-lookup"><span data-stu-id="a196f-113">Metrics refers to numeric data that is designed to be aggregated and presented using charts and graphs in a dashboard that provides a view of the overall health and performance of an application.</span></span> <span data-ttu-id="a196f-114">計量資料也可以在超過閾值時用來觸發自動警示。</span><span class="sxs-lookup"><span data-stu-id="a196f-114">Metrics data can also be used to trigger automated alerts when a threshold is exceeded.</span></span> <span data-ttu-id="a196f-115">下列清單顯示計量資料的一些範例：</span><span class="sxs-lookup"><span data-stu-id="a196f-115">The following list shows some examples of metrics data:</span></span>

- <span data-ttu-id="a196f-116">處理要求所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="a196f-116">Time taken to process requests.</span></span>
- <span data-ttu-id="a196f-117">服務實例每秒處理的要求數目。</span><span class="sxs-lookup"><span data-stu-id="a196f-117">The number of requests per second being handled by an instance of a service.</span></span>
- <span data-ttu-id="a196f-118">實例上失敗的要求數目。</span><span class="sxs-lookup"><span data-stu-id="a196f-118">The number of failed requests on an instance.</span></span>

## <a name="logging-in-aspnet-core-grpc"></a><span data-ttu-id="a196f-119">在 ASP.NET Core gRPC 中登入</span><span class="sxs-lookup"><span data-stu-id="a196f-119">Logging in ASP.NET Core gRPC</span></span>

<span data-ttu-id="a196f-120">ASP.NET Core 提供記錄的內建支援，格式為[Microsoft. Extensions. 記錄](https://www.nuget.org/packages/Microsoft.Extensions.Logging)NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a196f-120">ASP.NET Core provides built-in support for logging, in the form of the [Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) NuGet package.</span></span> <span data-ttu-id="a196f-121">此程式庫的核心部分隨附于 Web SDK，因此不需要手動安裝。</span><span class="sxs-lookup"><span data-stu-id="a196f-121">The core parts of this library are included with the Web SDK, so there's no need to install it manually.</span></span> <span data-ttu-id="a196f-122">根據預設，記錄訊息會寫入標準輸出（「主控台」）和任何附加的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a196f-122">By default, log messages are written to the standard output (the "console") and to any attached debugger.</span></span> <span data-ttu-id="a196f-123">若要將記錄寫入持續性外部資料存放區，您可能需要匯入[選擇性的記錄接收封裝](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)。</span><span class="sxs-lookup"><span data-stu-id="a196f-123">To write logs to persistent external data stores, you may need to import [optional logging sink packages](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers).</span></span>

<span data-ttu-id="a196f-124">ASP.NET Core gRPC framework 會將詳細的診斷記錄訊息寫入此記錄架構，讓它們可以與您的應用程式本身的訊息一併處理/儲存。</span><span class="sxs-lookup"><span data-stu-id="a196f-124">The ASP.NET Core gRPC framework writes detailed diagnostic logging messages to this logging framework so they can be processed/stored along with your application's own messages.</span></span>

### <a name="produce-log-messages"></a><span data-ttu-id="a196f-125">產生記錄檔訊息</span><span class="sxs-lookup"><span data-stu-id="a196f-125">Produce log messages</span></span>

<span data-ttu-id="a196f-126">記錄延伸模組會自動向 ASP.NET Core 的相依性插入系統註冊，因此您可以將記錄器指定為 gRPC 服務類型上的函式參數。</span><span class="sxs-lookup"><span data-stu-id="a196f-126">The logging extension is automatically registered with ASP.NET Core's dependency injection system, so you can specify loggers as a constructor parameter on gRPC service types.</span></span>

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

<span data-ttu-id="a196f-127">ASP.NET Core 和 gRPC framework 元件會提供許多有關要求、例外狀況等等的記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="a196f-127">Many log messages around requests, exceptions, and so on, are provided by the ASP.NET Core and gRPC framework components.</span></span> <span data-ttu-id="a196f-128">新增您自己的記錄檔訊息，以提供應用程式邏輯的詳細資料和內容，而不是較低層級的顧慮。</span><span class="sxs-lookup"><span data-stu-id="a196f-128">Add your own log messages to provide detail and context about application logic rather than lower-level concerns.</span></span>

<span data-ttu-id="a196f-129">如需有關撰寫記錄檔訊息和可用記錄接收和目標的詳細資訊，請參閱在[.Net Core 中記錄和 ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0)一文。</span><span class="sxs-lookup"><span data-stu-id="a196f-129">For more information about writing log messages and available logging sinks and targets, see the [Logging in .NET Core and ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) article.</span></span>

## <a name="metrics-in-aspnet-core-grpc"></a><span data-ttu-id="a196f-130">ASP.NET Core gRPC 中的計量</span><span class="sxs-lookup"><span data-stu-id="a196f-130">Metrics in ASP.NET Core gRPC</span></span>

<span data-ttu-id="a196f-131">.Net Core 執行時間提供一組元件，用於發出和觀察包含 api （例如<xref:System.Diagnostics.Tracing.EventSource>和<xref:System.Diagnostics.Tracing.EventCounter>類別）的計量。</span><span class="sxs-lookup"><span data-stu-id="a196f-131">The .NET Core runtime provides a set of components for emitting and observing metrics that includes APIs such as the <xref:System.Diagnostics.Tracing.EventSource> and <xref:System.Diagnostics.Tracing.EventCounter> classes.</span></span> <span data-ttu-id="a196f-132">這些 Api 可用來發出可供外部進程使用的基本數值資料，例如[dotnet 計數器通用工具](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)或 Windows 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="a196f-132">These APIs can be used to emit basic numeric data that can be consumed by external processes like the [dotnet-counters global tool](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md), or Event Tracing for Windows.</span></span> <span data-ttu-id="a196f-133">如需在您自己`EventCounter`的程式碼中使用的詳細資訊，請參閱[EventCounter 簡介](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="a196f-133">For more information about using `EventCounter` in your own code, see the [EventCounter Introduction](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) tutorial.</span></span>

<span data-ttu-id="a196f-134">針對更先進的計量，以及將度量資料寫入更廣泛的資料存放區，有一個絕佳的開放原始碼專案，稱為[應用程式計量](https://www.app-metrics.io)。</span><span class="sxs-lookup"><span data-stu-id="a196f-134">For more advanced metrics and for writing metric data to a wider range of data stores, there's an excellent open-source project called [App Metrics](https://www.app-metrics.io).</span></span> <span data-ttu-id="a196f-135">此程式庫套件提供一組豐富的類型來檢測您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a196f-135">This suite of libraries provides an extensive set of types to instrument your code.</span></span> <span data-ttu-id="a196f-136">它也提供封裝，以將計量寫入包含時間序列資料庫的不同目標型別，例如 Prometheus 和 InfluxDB、 [Azure 應用程式 Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)等等。</span><span class="sxs-lookup"><span data-stu-id="a196f-136">It also offers packages to write metrics to different kinds of targets that include time-series databases, such as Prometheus and InfluxDB, [Azure Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview), and more.</span></span> <span data-ttu-id="a196f-137">[AspNetCore](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet 套件甚至會新增一組完整的基本計量，這些度量是透過與 ASP.NET Core 架構的整合自動產生的，而網站則提供[範本](https://www.app-metrics.io/samples/grafana/)來顯示這些計量使用[Grafana](https://grafana.com/)視覺化平臺。</span><span class="sxs-lookup"><span data-stu-id="a196f-137">The [App.Metrics.AspNetCore.Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet package even adds a comprehensive set of basic metrics that are automatically generated via integration with the ASP.NET Core framework, and the web site provides [templates](https://www.app-metrics.io/samples/grafana/) for displaying those metrics with the [Grafana](https://grafana.com/) visualization platform.</span></span>

<span data-ttu-id="a196f-138">如需有關應用程式計量的詳細資訊和檔，請參閱[app-metrics.io](https://app-metrics.io)網站。</span><span class="sxs-lookup"><span data-stu-id="a196f-138">For more information and documentation about App Metrics, see the [app-metrics.io](https://app-metrics.io) website.</span></span>

### <a name="produce-metrics"></a><span data-ttu-id="a196f-139">產生計量</span><span class="sxs-lookup"><span data-stu-id="a196f-139">Produce metrics</span></span>

<span data-ttu-id="a196f-140">大部分的計量平臺都支援五種基本類型的度量，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="a196f-140">Most metrics platforms support five basic types of metric, outlined in the following table:</span></span>

| <span data-ttu-id="a196f-141">度量類型</span><span class="sxs-lookup"><span data-stu-id="a196f-141">Metric type</span></span> | <span data-ttu-id="a196f-142">描述</span><span class="sxs-lookup"><span data-stu-id="a196f-142">Description</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="a196f-143">計數器</span><span class="sxs-lookup"><span data-stu-id="a196f-143">Counter</span></span>     | <span data-ttu-id="a196f-144">追蹤發生事件的頻率，例如要求、錯誤等等。</span><span class="sxs-lookup"><span data-stu-id="a196f-144">Tracks how often something happens, such as requests, errors, and so on.</span></span> |
| <span data-ttu-id="a196f-145">衡量</span><span class="sxs-lookup"><span data-stu-id="a196f-145">Gauge</span></span>       | <span data-ttu-id="a196f-146">記錄隨時間變更的單一值，例如使用中的連接。</span><span class="sxs-lookup"><span data-stu-id="a196f-146">Records a single value that changes over time, such as active connections.</span></span> |
| <span data-ttu-id="a196f-147">長條圖</span><span class="sxs-lookup"><span data-stu-id="a196f-147">Histogram</span></span>   | <span data-ttu-id="a196f-148">測量跨任意限制的值分佈。</span><span class="sxs-lookup"><span data-stu-id="a196f-148">Measures a distribution of values across arbitrary limits.</span></span> <span data-ttu-id="a196f-149">例如，長條圖可以追蹤資料集大小、計算有多少包含 < 10 筆記錄、有多少11-100 和101-1000，以及 > 1000 筆記錄。</span><span class="sxs-lookup"><span data-stu-id="a196f-149">For example, a histogram could track data set size, counting how many contained <10 records, how many 11-100 and 101-1000, and >1000 records.</span></span> |
| <span data-ttu-id="a196f-150">計數器</span><span class="sxs-lookup"><span data-stu-id="a196f-150">Meter</span></span>       | <span data-ttu-id="a196f-151">測量事件在各種時間範圍內發生的速率。</span><span class="sxs-lookup"><span data-stu-id="a196f-151">Measures the rate at which an event occurs in various time spans.</span></span> |
| <span data-ttu-id="a196f-152">計時器</span><span class="sxs-lookup"><span data-stu-id="a196f-152">Timer</span></span>       | <span data-ttu-id="a196f-153">追蹤事件的持續時間，以及其發生的速率（儲存為長條圖）。</span><span class="sxs-lookup"><span data-stu-id="a196f-153">Tracks the duration of events and the rate at which it occurs, stored as a histogram.</span></span> |

<span data-ttu-id="a196f-154">使用*應用程式計量*， `IMetrics`您可以透過相依性插入來取得介面，並用來記錄 gRPC 服務的任何這些計量。</span><span class="sxs-lookup"><span data-stu-id="a196f-154">Using *App Metrics*, an `IMetrics` interface can be obtained via dependency injection and used to record any of these metrics for a gRPC service.</span></span> <span data-ttu-id="a196f-155">下列範例示範如何計算經過一`Get`段時間後所提出的要求數目：</span><span class="sxs-lookup"><span data-stu-id="a196f-155">The following example shows how to count the number of `Get` requests made over time:</span></span>

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a><span data-ttu-id="a196f-156">儲存和視覺化計量資料</span><span class="sxs-lookup"><span data-stu-id="a196f-156">Store and visualize metrics data</span></span>

<span data-ttu-id="a196f-157">儲存計量資料的最佳方式是在*時間序列資料庫*中，這是專為記錄以時間戳記標示的數值資料數列而設計的特製化資料存放區。</span><span class="sxs-lookup"><span data-stu-id="a196f-157">The best way to store metrics data is in a *time-series database*, a specialized data store designed to record numerical data series marked with timestamps.</span></span> <span data-ttu-id="a196f-158">這些資料庫最受歡迎的是[Prometheus](https://prometheus.io/)和[InfluxDB](https://www.influxdata.com/products/influxdb-overview/)。</span><span class="sxs-lookup"><span data-stu-id="a196f-158">The most popular of these databases are [Prometheus](https://prometheus.io/) and [InfluxDB](https://www.influxdata.com/products/influxdb-overview/).</span></span> <span data-ttu-id="a196f-159">Microsoft Azure 也會透過[Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/overview)服務提供專用的計量儲存體。</span><span class="sxs-lookup"><span data-stu-id="a196f-159">Microsoft Azure also provides dedicated metrics storage through the [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) service.</span></span>

<span data-ttu-id="a196f-160">將計量資料視覺化的最新解決方案[Grafana](https://grafana.com)，可搭配廣泛的儲存提供者使用，包括 Azure 監視器、InfluxDB 和 Prometheus。</span><span class="sxs-lookup"><span data-stu-id="a196f-160">The current go-to solution for visualizing metrics data is [Grafana](https://grafana.com), which works with a wide range of storage providers including Azure Monitor, InfluxDB and Prometheus.</span></span> <span data-ttu-id="a196f-161">下圖顯示的範例 Grafana 儀表板，會顯示執行 StockData 範例之 Linkerd 服務網格中的計量：</span><span class="sxs-lookup"><span data-stu-id="a196f-161">The following image shows an example Grafana dashboard that displays metrics from the Linkerd service mesh running the StockData sample:</span></span>

![Grafana 儀表板](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a><span data-ttu-id="a196f-163">以計量為基礎的警示</span><span class="sxs-lookup"><span data-stu-id="a196f-163">Metrics-based alerting</span></span>

<span data-ttu-id="a196f-164">計量資料的數值本質表示它非常適合用來驅動警示系統，在某個值超出某些定義的容錯時，通知開發人員或支援工程師。</span><span class="sxs-lookup"><span data-stu-id="a196f-164">The numerical nature of metrics data means that it's ideally suited to drive alerting systems, notifying developers or support engineers when a value falls outside of some defined tolerance.</span></span> <span data-ttu-id="a196f-165">已提到的平臺都可透過各種選項（包括電子郵件、文字訊息或儀表板中的視覺效果）來提供警示的支援。</span><span class="sxs-lookup"><span data-stu-id="a196f-165">The platforms already mentioned all provide support for alerting via a range of options, including emails, text messages, or in-dashboard visualizations.</span></span>

## <a name="distributed-tracing"></a><span data-ttu-id="a196f-166">分散式追蹤</span><span class="sxs-lookup"><span data-stu-id="a196f-166">Distributed tracing</span></span>

<span data-ttu-id="a196f-167">*分散式追蹤*是一項相當近期的監視開發，其中的引起會增加微服務和分散式架構的使用。</span><span class="sxs-lookup"><span data-stu-id="a196f-167">*Distributed tracing* is a relatively recent development in monitoring, which has arisen from the increasing use of microservices and distributed architectures.</span></span> <span data-ttu-id="a196f-168">來自用戶端瀏覽器、應用程式或裝置的單一要求可能會細分成許多步驟和子要求，並牽涉到在網路上使用許多服務。</span><span class="sxs-lookup"><span data-stu-id="a196f-168">A single request from a client browser, application, or device may be broken down into many steps and sub-requests, and involve the use of many services across a network.</span></span> <span data-ttu-id="a196f-169">這使得記錄訊息和計量與觸發它們的特定要求相互關聯變得很容易。</span><span class="sxs-lookup"><span data-stu-id="a196f-169">This makes it difficult to correlate log messages and metrics with the specific request that triggered them.</span></span> <span data-ttu-id="a196f-170">分散式追蹤會將識別碼套用至允許記錄和計量與特定作業相互關聯的要求。</span><span class="sxs-lookup"><span data-stu-id="a196f-170">Distributed tracing applies identifiers to requests that allow logs and metrics to be correlated with a particular operation.</span></span> <span data-ttu-id="a196f-171">這類似于[WCF 的端對端追蹤](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing)，但會套用到多個平臺。</span><span class="sxs-lookup"><span data-stu-id="a196f-171">This is similar to [WCF's end-to-end tracing](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing), but applied across multiple platforms.</span></span>

<span data-ttu-id="a196f-172">雖然它仍然是發展技術領域，但分散式追蹤在熱門程度上快速成長，現在正在進行標準化程式。</span><span class="sxs-lookup"><span data-stu-id="a196f-172">Although it's still a nascent technology area, distributed tracing has grown quickly in popularity and is now going through a standardization process.</span></span> <span data-ttu-id="a196f-173">雲端原生運算基礎建立了[開放的追蹤標準](https://opentracing.io)，並嘗試提供廠商中立的程式庫，以使用[JAEGER](https://www.jaegertracing.io/)和[彈性 APM](https://www.elastic.co/products/apm)等後端。</span><span class="sxs-lookup"><span data-stu-id="a196f-173">The Cloud Native Computing Foundation created the [the Open Tracing standard](https://opentracing.io), attempting to provide vendor-neutral libraries for working with backends like [Jaeger](https://www.jaegertracing.io/) and [Elastic APM](https://www.elastic.co/products/apm).</span></span> <span data-ttu-id="a196f-174">同時，Google 建立了[OpenCensus 專案](https://opencensus.io/)來解決相同的一組問題。</span><span class="sxs-lookup"><span data-stu-id="a196f-174">At the same time, Google created the [OpenCensus project](https://opencensus.io/) to address the same set of problems.</span></span> <span data-ttu-id="a196f-175">這兩個專案現在會合並到新的專案（ [OpenTelemetry](https://opentelemetry.io)），其目標是未來的業界標準。</span><span class="sxs-lookup"><span data-stu-id="a196f-175">These two projects are now being merged into a new project, [OpenTelemetry](https://opentelemetry.io), which aims to be the future industry standard.</span></span>

### <a name="how-distributed-tracing-works"></a><span data-ttu-id="a196f-176">分散式追蹤的運作方式</span><span class="sxs-lookup"><span data-stu-id="a196f-176">How distributed tracing works</span></span>

<span data-ttu-id="a196f-177">分散式追蹤是以*跨越*的概念為基礎：名為的計時作業，屬於單一*追蹤*的一部分，可能牽涉到在系統的多個節點上處理。</span><span class="sxs-lookup"><span data-stu-id="a196f-177">Distributed tracing is based on the concept of *Spans*: named, timed operations that are part of a single *Trace*, which may involve processing on multiple nodes of a system.</span></span> <span data-ttu-id="a196f-178">起始新的作業時，會建立具有唯一識別碼的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a196f-178">When a new operation is initiated, a trace is created with a unique identifier.</span></span> <span data-ttu-id="a196f-179">針對每個子作業，會使用自己的識別碼和追蹤識別碼來建立範圍。</span><span class="sxs-lookup"><span data-stu-id="a196f-179">For each sub-operation, a span is created with its own identifier and trace identifier.</span></span> <span data-ttu-id="a196f-180">當要求通過系統時，各種元件可以建立包含其*父系*識別碼的*子*範圍。</span><span class="sxs-lookup"><span data-stu-id="a196f-180">As the request passes around the system, various components can create *child* spans that include the identifier of their *parent*.</span></span> <span data-ttu-id="a196f-181">Span 具有*內容*，其中包含追蹤和 span 識別碼，以及索引鍵/值組（稱為*行李*）格式的實用資料。</span><span class="sxs-lookup"><span data-stu-id="a196f-181">A span has a *context*, which contains the trace and span identifiers, as well as useful data in the form of key/value pairs (called *baggage*).</span></span>

### <a name="distributed-tracing-with-diagnosticsource"></a><span data-ttu-id="a196f-182">使用 DiagnosticSource 進行分散式追蹤</span><span class="sxs-lookup"><span data-stu-id="a196f-182">Distributed tracing with DiagnosticSource</span></span>

<span data-ttu-id="a196f-183">.NET Core 具有可妥善對應至分散式追蹤和範圍的內部模組：[DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide)。</span><span class="sxs-lookup"><span data-stu-id="a196f-183">.NET Core has an internal module that maps well to distributed traces and spans: [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide).</span></span> <span data-ttu-id="a196f-184">除了提供一個簡單的方法來產生和取用進程內的診斷， `DiagnosticSource`模組具有*活動*的概念，這實際上是分散式追蹤的執行，或是追蹤內的範圍。</span><span class="sxs-lookup"><span data-stu-id="a196f-184">As well as providing a simple way to produce and consume diagnostics within a process, the `DiagnosticSource` module has the concept of an *Activity*, which is effectively an implementation of a distributed trace, or a span within a trace.</span></span> <span data-ttu-id="a196f-185">模組的內部會負責處理父系/子活動，包括配置識別碼。</span><span class="sxs-lookup"><span data-stu-id="a196f-185">The internals of the module take care of parent/child activities, including allocating identifiers.</span></span> <span data-ttu-id="a196f-186">如需使用`Activity`類型的詳細資訊，請參閱[GitHub 上的活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)</span><span class="sxs-lookup"><span data-stu-id="a196f-186">For more information about using the `Activity` type, see the [Activity User Guide on GitHub](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)</span></span>

<span data-ttu-id="a196f-187">由於 DiagnosticSource 是核心架構的一部分，因此支援數個核心元件，包括<xref:System.Net.Http.HttpClient>、Entity Framework Core 和 ASP.NET Core，包括 gRPC 架構中的明確支援。</span><span class="sxs-lookup"><span data-stu-id="a196f-187">Because DiagnosticSource is a part of the core framework, it's supported by several core components, including <xref:System.Net.Http.HttpClient>, Entity Framework Core and ASP.NET Core, including explicit support in the gRPC framework.</span></span> <span data-ttu-id="a196f-188">當 ASP.NET Core 收到要求時，它會檢查是否有一對符合[W3C 追蹤內容](https://www.w3.org/TR/trace-context)標準的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="a196f-188">When ASP.NET Core receives a request, it  checks for a pair of HTTP headers matching the [W3C Trace Context](https://www.w3.org/TR/trace-context) standard.</span></span> <span data-ttu-id="a196f-189">如果找到標頭，則會使用標頭中的識別值和內容來啟動活動。</span><span class="sxs-lookup"><span data-stu-id="a196f-189">If the headers are found, an Activity is started using the identity values and context from the headers.</span></span> <span data-ttu-id="a196f-190">如果找不到任何標頭，則會啟動活動，並產生符合標準格式的識別值。</span><span class="sxs-lookup"><span data-stu-id="a196f-190">If no headers are found, an Activity is started with generated identity values that match the standard format.</span></span> <span data-ttu-id="a196f-191">在此活動的存留期內，架構或應用程式程式碼所產生的任何診斷，都可以使用追蹤和範圍識別碼來標記。</span><span class="sxs-lookup"><span data-stu-id="a196f-191">Any diagnostics generated by the framework or by application code during the lifetime of this Activity can be tagged with the trace and span identifiers.</span></span> <span data-ttu-id="a196f-192">`HttpClient`支援會藉由檢查每個要求的目前活動，並自動將追蹤標頭新增至傳出要求，進一步擴充此功能。</span><span class="sxs-lookup"><span data-stu-id="a196f-192">The `HttpClient` support extends this further by checking for a current Activity on every request and automatically adding the trace headers to the outgoing request.</span></span>

<span data-ttu-id="a196f-193">ASP.NET Core gRPC 用戶端和伺服器程式庫包括明確支援 DiagnosticSource 和活動，並會建立活動並自動套用和使用標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="a196f-193">The ASP.NET Core gRPC client and server libraries include explicit support for DiagnosticSource and Activity, and will create activities and apply and use header information automatically.</span></span>

> [!NOTE]
> <span data-ttu-id="a196f-194">只有在接聽程式正在使用診斷*資訊時，* 才會發生這一切。</span><span class="sxs-lookup"><span data-stu-id="a196f-194">All of this only happens if a *listener* is consuming the diagnostic information.</span></span> <span data-ttu-id="a196f-195">如果沒有接聽程式，就不會寫入任何診斷，也不會建立任何活動。</span><span class="sxs-lookup"><span data-stu-id="a196f-195">If there's no listener, no diagnostics are written and no activities are created.</span></span>

### <a name="add-your-own-diagnosticsources-and-activities"></a><span data-ttu-id="a196f-196">新增您自己的 DiagnosticSources 和活動</span><span class="sxs-lookup"><span data-stu-id="a196f-196">Add your own DiagnosticSources and Activities</span></span>

<span data-ttu-id="a196f-197">雖然良好的資料量會由 ASP.NET Core 自動產生（包括 gRPC），以及 Entity Framework Core 和`HttpClient`，但您可能會想要新增自己的診斷，或在應用程式程式碼中建立明確的範圍。</span><span class="sxs-lookup"><span data-stu-id="a196f-197">Although a good quantity of data is automatically generated by ASP.NET Core, including gRPC, as well as Entity Framework Core and `HttpClient`, you may wish to add your own diagnostics or create explicit spans within your application code.</span></span> <span data-ttu-id="a196f-198">如需如何執行自己的診斷的詳細資訊，請參閱[DiagnosticSource 使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener)和[活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage)。</span><span class="sxs-lookup"><span data-stu-id="a196f-198">Refer to the [DiagnosticSource User Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) and [Activity User Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) for details on how to implement your own diagnostics.</span></span>

### <a name="store-distributed-trace-data"></a><span data-ttu-id="a196f-199">儲存分散式追蹤資料</span><span class="sxs-lookup"><span data-stu-id="a196f-199">Store distributed trace data</span></span>

<span data-ttu-id="a196f-200">撰寫 OpenTelemetry 專案時，仍在早期階段，而且 .NET 應用程式只提供 Alpha 品質的套件。</span><span class="sxs-lookup"><span data-stu-id="a196f-200">At the time of writing the OpenTelemetry project is still in the early stages, and only alpha-quality packages are available for .NET applications.</span></span> <span data-ttu-id="a196f-201">OpenTracing 專案提供更成熟的程式庫，但未來將會取代 OpenTelemetry 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a196f-201">The OpenTracing project offers more mature libraries, but these will be superseded by the OpenTelemetry libraries in the future.</span></span>

<span data-ttu-id="a196f-202">OpenTracing API 如下所述。</span><span class="sxs-lookup"><span data-stu-id="a196f-202">The OpenTracing API is described below.</span></span> <span data-ttu-id="a196f-203">如果您想要在應用程式中使用較新的 OpenTelemetry API，請參閱[GitHub 上的 OpenTelemetry .NET SDK 存放庫](https://github.com/open-telemetry/opentelemetry-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a196f-203">If you would prefer to use the newer OpenTelemetry API in your application, refer to the [OpenTelemetry .NET SDK repository on GitHub](https://github.com/open-telemetry/opentelemetry-dotnet).</span></span>

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a><span data-ttu-id="a196f-204">使用 OpenTracing 封裝來儲存分散式追蹤資料</span><span class="sxs-lookup"><span data-stu-id="a196f-204">Use the OpenTracing package to store distributed trace data</span></span>

<span data-ttu-id="a196f-205">[OpenTracing NuGet 套件](https://www.nuget.org/packages/OpenTracing/)，支援所有符合 OpenTracing 標準的`DiagnosticSource`後端（可獨立使用）。</span><span class="sxs-lookup"><span data-stu-id="a196f-205">The [an OpenTracing NuGet package](https://www.nuget.org/packages/OpenTracing/) that supports all OpenTracing-compliant back-ends (which can be used independently of `DiagnosticSource`).</span></span> <span data-ttu-id="a196f-206">還有一個來自 OpenTracing API 投稿專案[OpenTracing. Contrib](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)的額外套件，它會新增`DiagnosticSource`接聽程式，並自動將事件和活動寫入後端。</span><span class="sxs-lookup"><span data-stu-id="a196f-206">There's an additional package from the OpenTracing API Contributions project, [OpenTracing.Contrib.NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), which adds a `DiagnosticSource` listener and writes events and activities to a back-end automatically.</span></span> <span data-ttu-id="a196f-207">啟用此套件的方式很簡單，只要從 NuGet 安裝它，再將它新增為`Startup`類別中的服務即可。</span><span class="sxs-lookup"><span data-stu-id="a196f-207">Enabling this package is as simple as installing it from NuGet and adding it as a service in your `Startup` class.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

<span data-ttu-id="a196f-208">OpenTracing 套件是抽象層，因此它需要後端特定的執行。</span><span class="sxs-lookup"><span data-stu-id="a196f-208">The OpenTracing package is an abstraction layer and as such it requires a back-end-specific implementation.</span></span> <span data-ttu-id="a196f-209">下列開放原始碼後端可以使用 OpenTracing API 部署。</span><span class="sxs-lookup"><span data-stu-id="a196f-209">OpenTracing API implementations are available for the following open source back-ends.</span></span>

| <span data-ttu-id="a196f-210">名稱</span><span class="sxs-lookup"><span data-stu-id="a196f-210">Name</span></span> | <span data-ttu-id="a196f-211">Package</span><span class="sxs-lookup"><span data-stu-id="a196f-211">Package</span></span> | <span data-ttu-id="a196f-212">網站</span><span class="sxs-lookup"><span data-stu-id="a196f-212">Web site</span></span> |
| ---- | ------- | -------- |
| <span data-ttu-id="a196f-213">Jaeger</span><span class="sxs-lookup"><span data-stu-id="a196f-213">Jaeger</span></span> | [<span data-ttu-id="a196f-214">Jaeger</span><span class="sxs-lookup"><span data-stu-id="a196f-214">Jaeger</span></span>](https://www.nuget.org/packages/Jaeger/) | [<span data-ttu-id="a196f-215">jaegertracing.io</span><span class="sxs-lookup"><span data-stu-id="a196f-215">jaegertracing.io</span></span>](https://jaegertracing.io) |
| <span data-ttu-id="a196f-216">彈性 APM</span><span class="sxs-lookup"><span data-stu-id="a196f-216">Elastic APM</span></span> | [<span data-ttu-id="a196f-217">NetCoreAll 的彈性</span><span class="sxs-lookup"><span data-stu-id="a196f-217">Elastic.Apm.NetCoreAll</span></span>](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [<span data-ttu-id="a196f-218">elastic.co/products/apm</span><span class="sxs-lookup"><span data-stu-id="a196f-218">elastic.co/products/apm</span></span>](https://www.elastic.co/products/apm) |

<span data-ttu-id="a196f-219">如需適用于 .net 的 OpenTracing API 的詳細資訊，請參閱[OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp)和 GitHub 上的[OpenTracing C#Contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore)存放庫。</span><span class="sxs-lookup"><span data-stu-id="a196f-219">For more information on the OpenTracing API for .NET, see the [OpenTracing for C#](https://github.com/opentracing/opentracing-csharp) and the [OpenTracing Contrib C#/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) repositories on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a196f-220">[上一頁](load-balancing.md)
>[下一頁](appendix.md)</span><span class="sxs-lookup"><span data-stu-id="a196f-220">[Previous](load-balancing.md)
[Next](appendix.md)</span></span>
