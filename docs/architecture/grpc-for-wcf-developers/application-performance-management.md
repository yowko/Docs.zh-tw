---
title: 應用程式效能管理-WCF 開發人員的 gRPC
description: ASP.NET Core gRPC 應用程式的記錄、計量和追蹤。
ms.date: 09/02/2019
ms.openlocfilehash: bccb5ba92e2dc8fa2def4dc192b0ca58b332861a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165906"
---
# <a name="application-performance-management"></a>應用程式效能管理

在 Kubernetes 之類的生產環境中，請務必監視應用程式，以確保它們能以最佳方式執行。 記錄和計量特別重要。 ASP.NET Core （包括 gRPC）提供內建支援來產生和記錄管理訊息和計量資料，以及 *追蹤* 資料。

## <a name="the-difference-between-logging-and-metrics"></a>記錄與計量之間的差異

*記錄* 涉及記錄系統中發生之事物的詳細資訊的文字訊息。 記錄訊息可能包括例外狀況資料，例如堆疊追蹤，或是提供訊息相關內容的結構化資料。 記錄輸出通常會寫入至可搜尋的文字存放區。

*計量* 指的是在儀表板中使用圖表和圖形來匯總和呈現的數值資料。 儀表板可讓您查看應用程式的整體健全狀況和效能。 當超過閾值時，計量資料也可以用來觸發自動警示。 以下是一些計量資料的範例：

- 處理要求所花費的時間。
- 服務實例每秒處理的要求數目。
- 實例上失敗的要求數目。

## <a name="logging-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 中的記錄

ASP.NET Core 提供記錄的內建支援，格式為「[記錄 NuGet 套件」。](https://www.nuget.org/packages/Microsoft.Extensions.Logging) 此程式庫的核心部分隨附于 Web SDK，因此不需要手動安裝。 根據預設，記錄訊息會寫入至標準輸出 (「主控台」 ) 和任何附加的偵錯工具。 若要將記錄寫入持續性的外部資料存放區，您可能需要匯入 [選擇性的記錄接收套件](/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)。

ASP.NET Core gRPC 架構會將詳細的診斷記錄訊息寫入此記錄架構中，因此可以處理和儲存應用程式本身的訊息。

### <a name="produce-log-messages"></a>產生記錄訊息

記錄延伸模組會自動向 ASP.NET Core 的相依性插入系統註冊，因此您可以在 gRPC 服務類型上指定記錄器做為函式參數。

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

許多記錄訊息（例如要求和例外狀況）都是由 ASP.NET Core 和 gRPC framework 元件所提供。 新增您自己的記錄檔訊息，以提供有關應用程式邏輯的詳細資料和內容，而不是較低層級的考慮。

如需撰寫記錄訊息和可用記錄接收和目標的詳細資訊，請參閱  [.Net Core 和 ASP.NET Core 中的記錄](/aspnet/core/fundamentals/logging/)。

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 中的計量

.NET Core 執行時間提供一組用來發出和觀察計量的元件。 這些包括 Api <xref:System.Diagnostics.Tracing.EventSource> ，例如和 <xref:System.Diagnostics.Tracing.EventCounter> 類別。 這些 Api 可以發出可供外部進程取用的基本數值資料，例如 [dotnet 計數器全域工具](../../core/diagnostics/dotnet-counters.md)或 Windows 事件追蹤。 如需 `EventCounter` 在您自己的程式碼中使用的詳細資訊，請參閱 [EventCounter 簡介](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。

如需更先進的計量，以及將計量資料寫入更廣泛的資料存放區，您可以嘗試一個稱為「 [應用程式計量](https://www.app-metrics.io)」的開放原始碼專案。 此程式庫套件提供一組廣泛的類型來檢測您的程式碼。 它也提供封裝，以將計量寫入不同類型的目標，包括時間序列資料庫，例如 Prometheus 和 InfluxDB，以及 [Application Insights](/azure/azure-monitor/app/app-insights-overview)。 [AspNetCore Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet 套件甚至會新增一組完整的基本計量，這些計量會透過與 ASP.NET Core framework 的整合自動產生。 專案網站提供的 [範本](https://www.app-metrics.io/samples/grafana/) 可讓您使用 [Grafana](https://grafana.com/) 視覺效果平臺來顯示這些計量。

### <a name="produce-metrics"></a>產生計量

大部分的計量平臺都支援下列類型：

| 度量類型 | 描述 |
| ----------- | ----------- |
| 計數器     | 追蹤發生某件事的頻率，例如要求和錯誤。 |
| 量測計       | 記錄會隨著時間而變更的單一值，例如使用中的連接。 |
| 長條圖   | 測量任意限制之間值的分佈。 例如，長條圖可以追蹤資料集大小、計算有多少包含 <10 筆記錄、包含的11-100 記錄數目、包含的101-1000 記錄數量，以及包含的 >1000 記錄數目。 |
| 計量       | 測量事件在不同時間範圍內發生的速率。 |
| 計時器       | 追蹤事件的持續時間和發生的速率，儲存為長條圖。 |

藉由使用 *應用程式計量*，您可以透過相依性 `IMetrics` 插入取得介面，也可以用來記錄 gRPC 服務的任何計量。 下列範例會示範如何計算一 `Get` 段時間內所提出的要求數目：

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

### <a name="store-and-visualize-metrics-data"></a>儲存和視覺化度量資料

儲存度量資料的最佳方式是在 *時間序列資料庫*中，這是專門用來記錄以時間戳記標記之數值資料數列的特殊資料存放區。 這些資料庫中最受歡迎的 [Prometheus](https://prometheus.io/) 和 [InfluxDB](https://www.influxdata.com/products/influxdb-overview/)。 Microsoft Azure 也會透過 [Azure 監視器](/azure/azure-monitor/overview) 服務提供專用的計量儲存體。

將計量資料視覺化的目前進入解決方案是 [Grafana](https://grafana.com)，可與各種不同的儲存提供者搭配運作。 下圖顯示範例 Grafana 儀表板，此儀表板會顯示執行 StockData 範例之 Linkerd 服務網格中的計量：

![Grafana 儀表板的螢幕擷取畫面](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>以計量為基礎的警示

計量資料的數值本質表示它最適合用來驅動警示系統，在某個值超出某些定義的容錯範圍時通知開發人員或支援工程師。 已提及的平臺可透過各種選項（包括電子郵件、文字訊息或儀表板內視覺效果）提供警示的支援。

## <a name="distributed-tracing"></a>分散式追蹤

分散式追蹤是在監視中的最新開發，零件出現了從增加使用微服務和分散式架構。 用戶端瀏覽器、應用程式或裝置的單一要求可以細分為許多步驟和子要求，並牽涉到跨網路使用許多服務。 這使得記錄訊息和計量與觸發這些訊息的特定要求很難相互關聯。 分散式追蹤會對要求套用識別碼，這可讓記錄和計量與特定作業相互關聯。 這類似于 [WCF 的端對端追蹤](../../framework/wcf/diagnostics/tracing/end-to-end-tracing.md)，但會在多個平臺上套用。

分散式追蹤迅速成長，而且開始標準化。 雲端原生運算基礎建立了 [開放的追蹤標準](https://opentracing.io)，並嘗試提供廠商中立的程式庫，以搭配 [JAEGER](https://www.jaegertracing.io/) 和 [彈性 APM](https://www.elastic.co/products/apm)等後端運作。 同時，Google 建立了 [OpenCensus 專案](https://opencensus.io/) 來解決一組相同的問題。 這兩個專案會合並到新的專案 [OpenTelemetry](https://opentelemetry.io)中，其目標是未來的產業標準。

### <a name="how-distributed-tracing-works"></a>分散式追蹤的運作方式

分散式追蹤是以 *範圍*的概念為基礎：命名為的計時作業，屬於單一 *追蹤*的一部分，這可能牽涉到在系統的多個節點上處理。 起始新的作業時，會使用唯一識別碼來建立追蹤。 針對每個子作業，會使用自己的識別碼和追蹤識別碼來建立範圍。 當要求在系統中傳遞時，不同的元件可以建立包含其*父系*識別碼的*子*範圍。 範圍具有 *內容*，其中包含追蹤和 span 識別碼，以及索引鍵/值組形式的有用資料 (稱為「 *行李*) 」。

### <a name="distributed-tracing-with-diagnosticsource"></a>分散式追蹤 `DiagnosticSource`

.NET Core 的內部模組可適當地對應到分散式追蹤和範圍： [DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide)。 除了提供簡單的方法，讓您在進程內產生和取用診斷， `DiagnosticSource` 模組也有 *活動*的概念。 活動實際上是分散式追蹤或追蹤內的範圍。 模組的內部負責處理父子式活動，包括配置識別碼。 如需使用此類型的詳細資訊 `Activity` ，請參閱 [GitHub 上的活動使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)。

因為 `DiagnosticSource` 是核心架構的一部分，所以有數個核心元件支援。 這些包括 <xref:System.Net.Http.HttpClient> 、Entity Framework Core 和 ASP.NET Core，包括 gRPC 架構中的明確支援。 當 ASP.NET Core 收到要求時，它會檢查符合 [W3C 追蹤內容](https://www.w3.org/TR/trace-context) 標準的一對 HTTP 標頭。 如果找不到標頭，則會使用標頭中的識別值和內容來啟動活動。 如果找不到標頭，則會使用符合標準格式之產生的識別值啟動活動。 在此活動存留期間，架構或應用程式程式碼所產生的任何診斷都可以使用追蹤和 span 識別碼標記。 `HttpClient`此支援會藉由檢查每個要求的目前活動，以及自動將追蹤標頭新增至傳出要求，來進一步延伸此功能。

ASP.NET Core gRPC 用戶端和伺服器程式庫包含對和的明確支援 `DiagnosticSource` `Activity` ，並會自動建立活動並套用和使用標頭資訊。

> [!NOTE]
> 只有當接聽程式取用診斷資訊時，才會發生這種情況。 如果沒有任何接聽程式，則不會寫入任何診斷，也不會建立任何活動。

### <a name="add-your-own-diagnosticsource-and-activity"></a>新增您自己 `DiagnosticSource` 的 `Activity`

若要在您的應用程式程式碼中新增您自己的診斷或建立明確的範圍，請參閱 [DiagnosticSource 使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) 和 [活動使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage)。

### <a name="store-distributed-trace-data"></a>儲存分散式追蹤資料

在撰寫本文時，OpenTelemetry 專案仍處於早期階段，而且只有 Alpha 品質套件適用于 .NET 應用程式。 OpenTracing 專案目前提供更成熟的程式庫。

下一節將說明 OpenTracing API。 如果您想要改為在應用程式中使用 OpenTelemetry API，請參閱 GitHub 上的 [OpenTelemetry .NET SDK 存放庫](https://github.com/open-telemetry/opentelemetry-dotnet) 。

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>使用 OpenTracing 封裝來儲存分散式追蹤資料

[OpenTracing NuGet 套件](https://www.nuget.org/packages/OpenTracing/)支援所有符合 OpenTracing 規範的後端 (，可獨立于) 之外使用 `DiagnosticSource` 。 OpenTracing API 投稿專案中還有另一個套件， [OpenTracing. Contrib. NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)。 此封裝會新增接聽程式 `DiagnosticSource` ，並自動將事件和活動寫入至後端。 啟用此封裝的方式就像從 NuGet 安裝它一樣簡單，並且將它新增為類別中的服務 `Startup` 。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing 套件是一個抽象層，因此它需要後端的特定執行。 下列開放原始碼後端可使用 OpenTracing API。

| 名稱 | Package | 網站 |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| 彈性 APM | [NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

如需適用于 .NET 的 OpenTracing API 的詳細資訊，請參閱 GitHub 上的 [OpenTracing For c #](https://github.com/opentracing/opentracing-csharp) 和 [OpenTracing Contrib c #/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) 存放庫。

>[!div class="step-by-step"]
>[上一個](load-balancing.md) 
>[下一步](appendix.md)
