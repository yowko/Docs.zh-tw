---
title: 應用程式效能管理-WCF 開發人員的 gRPC
description: ASP.NET Core gRPC 應用程式的記錄、計量和追蹤。
ms.date: 09/02/2019
ms.openlocfilehash: e8ec701af69e8ced674183ce0afa25547713c647
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711554"
---
# <a name="application-performance-management"></a>應用程式效能管理

在 Kubernetes 這類生產環境中，請務必監視應用程式，以確保它們能以最佳狀態執行。 記錄和計量特別重要。 ASP.NET Core （包括 gRPC）提供產生和記錄管理檔訊息和計量資料的內建支援，以及*追蹤*資料。

## <a name="the-difference-between-logging-and-metrics"></a>記錄與計量之間的差異

*記錄*會考慮文字訊息，記錄系統中發生之專案的詳細資訊。 記錄檔訊息可能包括例外狀況資料（例如堆疊追蹤），或提供訊息內容的結構化資料。 記錄輸出通常會寫入可搜尋的文字存放區。

*計量*是指設計成使用儀表板中的圖表和圖形來匯總和呈現的數值資料。 儀表板可讓您查看應用程式的整體健全狀況和效能。 計量資料也可以在超過閾值時用來觸發自動警示。 以下是一些計量資料的範例：

- 處理要求所花費的時間。
- 服務實例每秒處理的要求數目。
- 實例上失敗的要求數目。

## <a name="logging-in-aspnet-core-grpc"></a>在 ASP.NET Core gRPC 中登入

ASP.NET Core 提供記錄的內建支援，格式為[Microsoft. Extensions. 記錄](https://www.nuget.org/packages/Microsoft.Extensions.Logging)NuGet 套件。 此程式庫的核心部分隨附于 Web SDK，因此不需要手動安裝。 根據預設，記錄訊息會寫入標準輸出（「主控台」）和任何附加的偵錯工具。 若要將記錄寫入持續性外部資料存放區，您可能需要匯入[選擇性的記錄接收封裝](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)。

ASP.NET Core gRPC framework 會將詳細的診斷記錄訊息寫入此記錄架構，因此可以處理並與您應用程式本身的訊息一起儲存。

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

許多記錄訊息（例如要求和例外狀況）都是由 ASP.NET Core 和 gRPC 架構元件所提供。 新增您自己的記錄檔訊息，以提供有關應用程式邏輯的詳細資料和內容，而不是較低層級的顧慮。

如需有關撰寫記錄檔訊息和可用記錄接收和目標的詳細資訊，請參閱[在 .Net Core 中進行記錄和 ASP.NET Core](/aspnet/core/fundamentals/logging/)。

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 中的計量

.NET Core 執行時間提供一組元件，用於發出和觀察計量。 這些包括 Api，例如 <xref:System.Diagnostics.Tracing.EventSource> 和 <xref:System.Diagnostics.Tracing.EventCounter> 類別。 這些 Api 可以發出可供外部進程使用的基本數值資料，例如[dotnet 計數器通用工具](../../core/diagnostics/dotnet-counters.md)或 Windows 事件追蹤。 如需在您自己的程式碼中使用 `EventCounter` 的詳細資訊，請參閱[EventCounter 簡介](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。

如需更先進的計量，以及將度量資料寫入更廣泛的資料存放區，您可以嘗試稱為「[應用程式計量](https://www.app-metrics.io)」的開放原始碼專案。 此程式庫套件提供一組豐富的類型來檢測您的程式碼。 它也提供封裝，以將計量寫入包含時間序列資料庫的不同目標型別，例如 Prometheus 和 InfluxDB，以及[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)。 [AspNetCore](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet 套件甚至會新增一組完整的基本計量，這些度量會透過與 ASP.NET Core 架構的整合而自動產生。 專案網站提供的[範本](https://www.app-metrics.io/samples/grafana/)可讓您使用[Grafana](https://grafana.com/)視覺效果平臺來顯示這些計量。

### <a name="produce-metrics"></a>產生計量

大部分的計量平臺都支援下列類型：

| 度量類型 | 描述 |
| ----------- | ----------- |
| 計數器     | 追蹤發生事件的頻率，例如要求和錯誤。 |
| 衡量       | 記錄隨時間變更的單一值，例如使用中的連接。 |
| 長條圖   | 測量跨任意限制的值分佈。 例如，長條圖可以追蹤資料集大小、計算有多少包含 < 10 筆記錄、有多少包含11-100 記錄、有多少包含的101-1000 筆記錄，以及有多少包含的 > 1000 筆記錄。 |
| 計數器       | 測量事件在各種時間範圍內發生的速率。 |
| 計時器       | 追蹤事件的持續時間，以及其發生的速率（儲存為長條圖）。 |

藉由使用*應用程式計量*，您可以透過相依性插入來取得 `IMetrics` 介面，並用來記錄 gRPC 服務的任何這些計量。 下列範例示範如何計算經過一段時間後所提出的 `Get` 要求數目：

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

將計量資料視覺化的最新解決方案[Grafana](https://grafana.com)，可搭配廣泛的儲存提供者使用。 下圖顯示的範例 Grafana 儀表板，會顯示執行 StockData 範例之 Linkerd 服務網格中的計量：

![Grafana 儀表板的螢幕擷取畫面](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>以計量為基礎的警示

計量資料的數值本質表示它非常適合用來驅動警示系統，在某個值超出某些定義的容錯時，通知開發人員或支援工程師。 已提到的平臺都可透過各種選項（包括電子郵件、文字訊息或儀表板中的視覺效果）來提供警示的支援。

## <a name="distributed-tracing"></a>分散式追蹤

分散式追蹤是一項相當近期的監視開發，其中的引起會增加微服務和分散式架構的使用。 來自用戶端瀏覽器、應用程式或裝置的單一要求可以細分為多個步驟和子要求，並牽涉到在網路上使用許多服務。 這使得記錄訊息和計量與觸發它們的特定要求相互關聯變得很容易。 分散式追蹤會將識別碼套用至要求，而這可讓記錄和計量與特定作業相互關聯。 這類似于[WCF 的端對端追蹤](../../framework/wcf/diagnostics/tracing/end-to-end-tracing.md)，但它會套用到多個平臺。

分散式追蹤在熱門程度上快速成長，並開始標準化。 雲端原生運算基礎建立了[開放的追蹤標準](https://opentracing.io)，並嘗試提供廠商中立的程式庫來處理後端，例如[JAEGER](https://www.jaegertracing.io/)和[彈性 APM](https://www.elastic.co/products/apm)。 同時，Google 建立了[OpenCensus 專案](https://opencensus.io/)來解決相同的一組問題。 這兩個專案會合並成新的專案[OpenTelemetry](https://opentelemetry.io)，其目標是未來的業界標準。

### <a name="how-distributed-tracing-works"></a>分散式追蹤的運作方式

分散式追蹤是以*跨越*的概念為基礎：名為的計時作業，屬於單一*追蹤*的一部分，這可能牽涉到在系統的多個節點上處理。 起始新的作業時，會建立具有唯一識別碼的追蹤。 針對每個子作業，會使用自己的識別碼和追蹤識別碼來建立範圍。 當要求通過系統時，各種元件可以建立包含其*父系*識別碼的*子*範圍。 Span 具有*內容*，其中包含追蹤和範圍識別碼，以及索引鍵和值組（稱為*行李*）形式的實用資料。

### <a name="distributed-tracing-with-diagnosticsource"></a>使用 `DiagnosticSource` 的分散式追蹤

.NET Core 有一個內部模組，可妥善對應到分散式追蹤和涵蓋範圍： [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide)。 和提供一個簡單的方法來產生和取用程式中的診斷，`DiagnosticSource` 模組具有*活動*的概念。 活動實際上是分散式追蹤的執行，或是追蹤內的範圍。 模組的內部會負責處理父系/子活動，包括配置識別碼。 如需使用 `Activity` 類型的詳細資訊，請參閱[GitHub 上的活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)。

因為 `DiagnosticSource` 是核心架構的一部分，所以有數個核心元件支援。 其中包括 <xref:System.Net.Http.HttpClient>、Entity Framework Core 和 ASP.NET Core，包括 gRPC 架構中的明確支援。 當 ASP.NET Core 收到要求時，它會檢查是否有一對符合[W3C 追蹤內容](https://www.w3.org/TR/trace-context)標準的 HTTP 標頭。 如果找到標頭，則會使用標頭中的識別值和內容來啟動活動。 如果找不到任何標頭，則會啟動活動，並產生符合標準格式的識別值。 在此活動的存留期內，架構或應用程式程式碼所產生的任何診斷，都可以使用追蹤和範圍識別碼來標記。 `HttpClient` 支援會藉由檢查每個要求的目前活動，並自動將追蹤標頭新增至傳出要求，進一步擴充此功能。

ASP.NET Core gRPC 用戶端和伺服器程式庫包括 `DiagnosticSource` 和 `Activity`的明確支援，並建立活動並自動套用和使用標頭資訊。

> [!NOTE]
> 只有在接聽程式正在使用診斷資訊時，才會發生這種情況。 如果沒有接聽程式，就不會寫入任何診斷，也不會建立任何活動。

### <a name="add-your-own-diagnosticsource-and-activity"></a>新增您自己的 `DiagnosticSource` 和 `Activity`

若要新增您自己的診斷，或在應用程式程式碼中建立明確的範圍，請參閱[DiagnosticSource 使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener)和[活動使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage)。

### <a name="store-distributed-trace-data"></a>儲存分散式追蹤資料

在撰寫本文時，OpenTelemetry 專案仍在早期階段，只有 Alpha 品質的套件適用于 .NET 應用程式。 OpenTracing 專案目前提供更成熟的程式庫。

下一節將說明 OpenTracing API。 如果您想要改為在應用程式中使用 OpenTelemetry API，請參閱 GitHub 上的[OpenTelemetry .NET SDK 存放庫](https://github.com/open-telemetry/opentelemetry-dotnet)。

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>使用 OpenTracing 封裝來儲存分散式追蹤資料

[OpenTracing NuGet 套件](https://www.nuget.org/packages/OpenTracing/)支援所有與 OpenTracing 相容的後端（可獨立于 `DiagnosticSource`）。 還有另一個來自 OpenTracing API 投稿專案的套件[OpenTracing. Contrib. NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)。 此套件會新增 `DiagnosticSource` 接聽程式，並自動將事件和活動寫入後端。 啟用此套件的方式很簡單，只要從 NuGet 安裝它，再將它新增為 `Startup` 類別中的服務即可。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing 套件是抽象層，因此它需要後端的特定執行。 下列開放原始碼後端可以使用 OpenTracing API 部署。

| Name | 套件 | 網站 |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| 彈性 APM | [NetCoreAll 的彈性](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

如需適用于 .net 的 OpenTracing API 的詳細資訊，請參閱[OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp)和 GitHub 上的[OpenTracing C#Contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore)存放庫。

>[!div class="step-by-step"]
>[上一頁](load-balancing.md)
>[下一頁](appendix.md)
