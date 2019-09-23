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
# <a name="application-performance-management"></a>應用程式效能管理

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在 Kubernetes 這類現代化生產環境中，必須能夠監視應用程式以確保其以最佳狀態執行，這點非常重要。 記錄和計量等顧慮也不重要。 ASP.NET Core （包括 gRPC）具有產生和記錄管理檔訊息和計量資料的一流支援，以及*追蹤*資料。 本節將更詳細地探索這些區域。

## <a name="logging-vs-metrics"></a>記錄與計量

在查看執行詳細資料之前，必須先瞭解記錄與計量之間的差異。

記錄會考慮文字訊息，記錄系統中發生之專案的詳細資訊。 記錄檔訊息可能包含例外狀況資料（例如堆疊追蹤），或提供訊息內容的結構化資料。 記錄輸出通常會寫入可搜尋的文字存放區。

計量是指設計成使用儀表板中的圖表和圖形來匯總和呈現的數值資料，可提供應用程式整體健全狀況和效能的觀點。 計量資料也可以在超過閾值時用來觸發自動警示。 下列清單顯示計量資料的一些範例：

- 處理要求所花費的時間。
- 服務實例每秒處理的要求數目。
- 實例上失敗的要求數目。

## <a name="logging-in-aspnet-core-grpc"></a>在 ASP.NET Core gRPC 中登入

ASP.NET Core 提供記錄的內建支援，格式為[Microsoft. Extensions. 記錄](https://www.nuget.org/packages/Microsoft.Extensions.Logging)NuGet 套件。 此程式庫的核心部分隨附于 Web SDK，因此不需要手動安裝。 根據預設，記錄訊息會寫入標準輸出（「主控台」）和任何附加的偵錯工具。 若要將記錄寫入持續性外部資料存放區，您可能需要匯入[選擇性的記錄接收封裝](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)。

ASP.NET Core gRPC framework 會將詳細的診斷記錄訊息寫入此記錄架構，讓它們可以與您的應用程式本身的訊息一併處理/儲存。

### <a name="produce-log-messages"></a>產生記錄檔訊息

記錄延伸模組會自動向 ASP.NET Core 的相依性插入系統註冊，因此您可以將記錄器指定為 gRPC 服務類型上的函式參數。

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

ASP.NET Core 和 gRPC framework 元件會提供許多有關要求、例外狀況等等的記錄訊息。 新增您自己的記錄檔訊息，以提供應用程式邏輯的詳細資料和內容，而不是較低層級的顧慮。

如需有關撰寫記錄檔訊息和可用記錄接收和目標的詳細資訊，請參閱在[.Net Core 中記錄和 ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0)一文。

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 中的計量

.Net Core 執行時間提供一組元件，用於發出和觀察包含 api （例如<xref:System.Diagnostics.Tracing.EventSource>和<xref:System.Diagnostics.Tracing.EventCounter>類別）的計量。 這些 Api 可用來發出可供外部進程使用的基本數值資料，例如[dotnet 計數器通用工具](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)或 Windows 事件追蹤。 如需在您自己`EventCounter`的程式碼中使用的詳細資訊，請參閱[EventCounter 簡介](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)教學課程。

針對更先進的計量，以及將度量資料寫入更廣泛的資料存放區，有一個絕佳的開放原始碼專案，稱為[應用程式計量](https://www.app-metrics.io)。 此程式庫套件提供一組豐富的類型來檢測您的程式碼。 它也提供封裝，以將計量寫入包含時間序列資料庫的不同目標型別，例如 Prometheus 和 InfluxDB、 [Azure 應用程式 Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)等等。 [AspNetCore](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet 套件甚至會新增一組完整的基本計量，這些度量是透過與 ASP.NET Core 架構的整合自動產生的，而網站則提供[範本](https://www.app-metrics.io/samples/grafana/)來顯示這些計量使用[Grafana](https://grafana.com/)視覺化平臺。

如需有關應用程式計量的詳細資訊和檔，請參閱[app-metrics.io](https://app-metrics.io)網站。

### <a name="produce-metrics"></a>產生計量

大部分的計量平臺都支援五種基本類型的度量，如下表所述：

| 度量類型 | 描述 |
| ----------- | ----------- |
| 計數器     | 追蹤發生事件的頻率，例如要求、錯誤等等。 |
| 衡量       | 記錄隨時間變更的單一值，例如使用中的連接。 |
| 長條圖   | 測量跨任意限制的值分佈。 例如，長條圖可以追蹤資料集大小、計算有多少包含 < 10 筆記錄、有多少11-100 和101-1000，以及 > 1000 筆記錄。 |
| 計數器       | 測量事件在各種時間範圍內發生的速率。 |
| 計時器       | 追蹤事件的持續時間，以及其發生的速率（儲存為長條圖）。 |

使用*應用程式計量*， `IMetrics`您可以透過相依性插入來取得介面，並用來記錄 gRPC 服務的任何這些計量。 下列範例示範如何計算經過一`Get`段時間後所提出的要求數目：

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

### <a name="store-and-visualize-metrics-data"></a>儲存和視覺化計量資料

儲存計量資料的最佳方式是在*時間序列資料庫*中，這是專為記錄以時間戳記標示的數值資料數列而設計的特製化資料存放區。 這些資料庫最受歡迎的是[Prometheus](https://prometheus.io/)和[InfluxDB](https://www.influxdata.com/products/influxdb-overview/)。 Microsoft Azure 也會透過[Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/overview)服務提供專用的計量儲存體。

將計量資料視覺化的最新解決方案[Grafana](https://grafana.com)，可搭配廣泛的儲存提供者使用，包括 Azure 監視器、InfluxDB 和 Prometheus。 下圖顯示的範例 Grafana 儀表板，會顯示執行 StockData 範例之 Linkerd 服務網格中的計量：

![Grafana 儀表板](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>以計量為基礎的警示

計量資料的數值本質表示它非常適合用來驅動警示系統，在某個值超出某些定義的容錯時，通知開發人員或支援工程師。 已提到的平臺都可透過各種選項（包括電子郵件、文字訊息或儀表板中的視覺效果）來提供警示的支援。

## <a name="distributed-tracing"></a>分散式追蹤

*分散式追蹤*是一項相當近期的監視開發，其中的引起會增加微服務和分散式架構的使用。 來自用戶端瀏覽器、應用程式或裝置的單一要求可能會細分成許多步驟和子要求，並牽涉到在網路上使用許多服務。 這使得記錄訊息和計量與觸發它們的特定要求相互關聯變得很容易。 分散式追蹤會將識別碼套用至允許記錄和計量與特定作業相互關聯的要求。 這類似于[WCF 的端對端追蹤](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing)，但會套用到多個平臺。

雖然它仍然是發展技術領域，但分散式追蹤在熱門程度上快速成長，現在正在進行標準化程式。 雲端原生運算基礎建立了[開放的追蹤標準](https://opentracing.io)，並嘗試提供廠商中立的程式庫，以使用[JAEGER](https://www.jaegertracing.io/)和[彈性 APM](https://www.elastic.co/products/apm)等後端。 同時，Google 建立了[OpenCensus 專案](https://opencensus.io/)來解決相同的一組問題。 這兩個專案現在會合並到新的專案（ [OpenTelemetry](https://opentelemetry.io)），其目標是未來的業界標準。

### <a name="how-distributed-tracing-works"></a>分散式追蹤的運作方式

分散式追蹤是以*跨越*的概念為基礎：名為的計時作業，屬於單一*追蹤*的一部分，可能牽涉到在系統的多個節點上處理。 起始新的作業時，會建立具有唯一識別碼的追蹤。 針對每個子作業，會使用自己的識別碼和追蹤識別碼來建立範圍。 當要求通過系統時，各種元件可以建立包含其*父系*識別碼的*子*範圍。 Span 具有*內容*，其中包含追蹤和 span 識別碼，以及索引鍵/值組（稱為*行李*）格式的實用資料。

### <a name="distributed-tracing-with-diagnosticsource"></a>使用 DiagnosticSource 進行分散式追蹤

.NET Core 具有可妥善對應至分散式追蹤和範圍的內部模組：[DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide)。 除了提供一個簡單的方法來產生和取用進程內的診斷， `DiagnosticSource`模組具有*活動*的概念，這實際上是分散式追蹤的執行，或是追蹤內的範圍。 模組的內部會負責處理父系/子活動，包括配置識別碼。 如需使用`Activity`類型的詳細資訊，請參閱[GitHub 上的活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)

由於 DiagnosticSource 是核心架構的一部分，因此支援數個核心元件，包括<xref:System.Net.Http.HttpClient>、Entity Framework Core 和 ASP.NET Core，包括 gRPC 架構中的明確支援。 當 ASP.NET Core 收到要求時，它會檢查是否有一對符合[W3C 追蹤內容](https://www.w3.org/TR/trace-context)標準的 HTTP 標頭。 如果找到標頭，則會使用標頭中的識別值和內容來啟動活動。 如果找不到任何標頭，則會啟動活動，並產生符合標準格式的識別值。 在此活動的存留期內，架構或應用程式程式碼所產生的任何診斷，都可以使用追蹤和範圍識別碼來標記。 `HttpClient`支援會藉由檢查每個要求的目前活動，並自動將追蹤標頭新增至傳出要求，進一步擴充此功能。

ASP.NET Core gRPC 用戶端和伺服器程式庫包括明確支援 DiagnosticSource 和活動，並會建立活動並自動套用和使用標頭資訊。

> [!NOTE]
> 只有在接聽程式正在使用診斷*資訊時，* 才會發生這一切。 如果沒有接聽程式，就不會寫入任何診斷，也不會建立任何活動。

### <a name="add-your-own-diagnosticsources-and-activities"></a>新增您自己的 DiagnosticSources 和活動

雖然良好的資料量會由 ASP.NET Core 自動產生（包括 gRPC），以及 Entity Framework Core 和`HttpClient`，但您可能會想要新增自己的診斷，或在應用程式程式碼中建立明確的範圍。 如需如何執行自己的診斷的詳細資訊，請參閱[DiagnosticSource 使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener)和[活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage)。

### <a name="store-distributed-trace-data"></a>儲存分散式追蹤資料

撰寫 OpenTelemetry 專案時，仍在早期階段，而且 .NET 應用程式只提供 Alpha 品質的套件。 OpenTracing 專案提供更成熟的程式庫，但未來將會取代 OpenTelemetry 程式庫。

OpenTracing API 如下所述。 如果您想要在應用程式中使用較新的 OpenTelemetry API，請參閱[GitHub 上的 OpenTelemetry .NET SDK 存放庫](https://github.com/open-telemetry/opentelemetry-dotnet)。

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>使用 OpenTracing 封裝來儲存分散式追蹤資料

[OpenTracing NuGet 套件](https://www.nuget.org/packages/OpenTracing/)，支援所有符合 OpenTracing 標準的`DiagnosticSource`後端（可獨立使用）。 還有一個來自 OpenTracing API 投稿專案[OpenTracing. Contrib](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)的額外套件，它會新增`DiagnosticSource`接聽程式，並自動將事件和活動寫入後端。 啟用此套件的方式很簡單，只要從 NuGet 安裝它，再將它新增為`Startup`類別中的服務即可。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing 套件是抽象層，因此它需要後端特定的執行。 下列開放原始碼後端可以使用 OpenTracing API 部署。

| 名稱 | Package | 網站 |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| 彈性 APM | [NetCoreAll 的彈性](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

如需適用于 .net 的 OpenTracing API 的詳細資訊，請參閱[OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp)和 GitHub 上的[OpenTracing C#Contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore)存放庫。

>[!div class="step-by-step"]
>[上一頁](load-balancing.md)
>[下一頁](appendix.md)
