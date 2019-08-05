---
title: 健康狀態監視
description: 瀏覽實作健康情況監視的其中一種方式。
ms.date: 01/07/2019
ms.openlocfilehash: b03506972166eec1864de840c1abda05bc3e5277
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674495"
---
# <a name="health-monitoring"></a>健康狀態監視

健康狀態監視功能可提供近即時的容器和微服務狀態資訊。 健康狀態監視功能對微服務運作的各方面來說都非常重要，尤其當協調器要分階段執行部分應用程式升級時更是如此，如稍後所說明。

微服務應用程式通常使用活動訊號或健康狀態檢查，使其效能監視器、排程器及協調器可以追蹤許多服務。 如果服務無法視需求或依排程傳送「運作正常」的訊號，當您部署更新時應用程式可能會面臨風險，或可能會太晚偵測到失敗，讓故障一發不可收拾，進而導致全面中斷。

在一般模型中，服務會傳送其狀態報告，而該彙總資訊可提供應用程式健康狀態的整體檢視。 如果您是使用協調器，則可以提供健康情況資訊給協調器的叢集，使叢集可以據以採取行動。 如果您為應用程式投入自訂的高品質健康情況報告，即可更輕鬆地偵測執行中的應用程式並修正問題。

## <a name="implement-health-checks-in-aspnet-core-services"></a>在 ASP.NET Core 服務中實作健康情況檢查

在開發 ASP.NET Core 微服務或 Web 應用程式時，您可以使用 ASP.NET Core 2.2 中發佈的內建健康情況檢查功能。 如同許多 ASP.NET Core 功能，健康情況檢查隨附一組服務與中介軟體。

健康情況服務和中介軟體不僅簡單易用，還提供功能讓您驗證應用程式所需的任何外部資源 (例如 SQL Server 資料庫或遠端 API) 是否正常運作。 使用這個功能時，您也可以自行決定何種情況下表示資源狀況良好，如我們稍後所說明。

若要有效地使用這個功能，您需要先在微服務中設定服務。 接著，您需要可查詢健康狀態報告的前端應用程式。 這裡的前端應用程式可能是自訂的報告應用程式，或能根據健康情況採取動作的協調器本身。

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>在您的後端 ASP.NET 微服務中使用 HealthChecks 功能

在本節中，您將了解如何在樣本 ASP.NET Core 2.2 Web API 應用程式中使用 HealthChecks 功能。 在大規模微服務 (例如 eShopOnContainers) 實作這個功能，稍後章節將有所說明。 首先，您需要為每個微服務定義健康狀態良好的構成項目。 在範例應用程式中，如果可以透過 HTTP 存取微服務 API 且其相關 SQL Server 資料庫亦可供存取，即表示微服務健康狀態良好。

在 .NET Core 2.2 中，您可以使用內建 API 來設定服務，並以下列方式新增微服務及其相關 SQL Server 資料庫的健康情況檢查：

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

在上述程式碼中，`services.AddHealthChecks()` 方法會設定基本 HTTP 檢查，傳回狀態碼 **200**，表示「良好」。  此外，`AddCheck()` 擴充方法會設定一個自訂 `SqlConnectionHealthCheck`，檢查相關 SQL Database 的健康情況。

`AddCheck()` 方法會使用指定的名稱和類型為 `IHealthCheck` 的實作來新增健康情況檢查。 您可以使用 AddCheck 方法新增多個健康情況檢查，讓微服務不會提供「良好」狀態，直到其所有檢查皆為良好為止。

`SqlConnectionHealthCheck` 是一種自訂類別，其會實作 `IHealthCheck`，而此實作會採取連接字串作為建構函式參數，並執行簡單查詢，以檢查 SQL 資料庫的連線是否成功。 如果查詢執行成功，則它會傳回 `HealthCheckResult.Healthy()`，若失敗，則會傳回 `FailureStatus` 與實際例外狀況。

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

請注意，在上述程式碼中，`Select 1` 是用來檢查資料庫健康情況的查詢。 為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。 請務必讓您的資料庫查詢保持效率，以便這些作業可以快速執行，但不會產生更高的資源使用率。

最後，建立一個回應 url 路徑 "/hc" 的中介軟體：

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
} 
```

叫用端點 `<yourmicroservice>/hc` 時，它會執行啟動類別中 `AddHealthChecks()` 方法內所設定的所有健康狀態檢查，並顯示結果。

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>eShopOnContainers 中的 HealthChecks 實作

eShopOnContainers 中的微服務依賴多個服務來執行其工作。 例如，來自 eShopOnContainers 的 `Catalog.API` 微服務依賴多個服務，例如 Azure Blob 儲存體、SQL Server 和 RabbitMQ。 因此，它具有數個使用 `AddCheck()` 方法新增的健康情況檢查。 對於每個相依服務，需要新增一個自訂 `IHealthCheck`，定義其各自的健康情況狀態。

開放原始碼專案 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 解決了這個問題，方法為針對每個建立在.NET Core 2.2 之上的企業服務提供自訂的健康情況檢查實作，。 每個健康情況檢查都可當成個別 NuGet 套件提供，然後便可輕鬆地將其新增至專案。 eShopOnContainers 會在其所有的微服務中廣泛使用它們。

例如，在 `Catalog.API` 微服務中，已新增下列 NuGet 套件：

![Catalog.API 專案的解決方案總管檢視，可在其中參考 AspNetCore.Diagnostics.HealthChecks NuGet 套件](./media/image6.png)

**圖 8-7**。 目錄 API 中使用 AspNetCore.Diagnostics.HealthChecks 實作的自訂健康情況檢查

在下列程式碼中，已針對每個相依服務新增健康情況檢查實作，然後設定中介軟體：

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

最後，我們會新增 HealthCheck 中介軟體來接聽 "/hc" 端點：

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>查詢微服務以報告其健康情況

完成此文章中說明的健康情況檢查設定並在 Docker 中開始執行微服務之後，您就可以直接從瀏覽器檢查微服務的健康情況。 您必須在 Docker 主機中發佈容器連接埠，以便透過外部 Docker 主機 IP 或 `localhost` 存取容器，如圖 8-8 所示。

![健康情況檢查所傳回 JSON 回應的瀏覽器檢視](./media/image7.png)

**圖 8-8**。 從瀏覽器檢查單一服務的健康狀態

在這個測試中，您可以看到 `Catalog.API` 微服務 (執行於連接埠 5101 上) 良好，並以 JSON 形式傳回 HTTP 狀態 200 和狀態資訊。 服務也已內部檢查其 SQL Server 資料庫相依性和RabbitMQ 的健康情況，因此健康情況檢查已自行回報良好。

## <a name="use-watchdogs"></a>使用監視程式

監視程式是一種可以跨服務監看健康情況和負載的個別服務，它會查詢稍早說明過的 `HealthChecks` 程式庫以回報微服務的健康情況。 這可協助防止從單一服務角度無法偵測出的錯誤。 監視程式也是裝載程式碼的好地方，以針對已知情況執行修復動作，而不需使用者互動。

eShopOnContainers 範例包含顯示範例健康情況檢查報告的網頁，如圖 8-9 所示。 這是一種最簡單的監視程式，因為它只會顯示 eShopOnContainers 中的微服務和 Web 應用程式狀態。 通常監視程式也會在偵測到健康狀態不良時採取動作。

幸好，[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 也會提供 [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet 套件，其可用來顯示所設定 URI 中的健康情況檢查結果。

![WebStatus 應用程式的瀏覽器檢視，其中顯示 eShopOnContainers 中所有微服務的健康情況狀態](./media/image8.png)

**圖 8-9**。 eShopOnContainers 中的範例健康狀態檢查報告

總而言之，此監視程式服務會查詢每個微服務的 "/hc" 端點。 其會執行端點中定義的所有健康狀態檢查，並根據這所有檢查傳回整體健康狀態。 HealthChecksUI 輕鬆耗用幾個設定項目，以及兩行程式碼，而此程式碼需要新增至監視程式服務的 Startup.cs。

健康情況檢查 UI 的樣本組態檔：

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

新增 HealthChecksUI 的 Startup.cs 檔案：

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>使用協調器時的健康狀態檢查

為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。 當協調器判斷某個服務/容器健康狀態不良時，它會停止將要求路由至該執行個體。 它通常也會建立該容器的新執行個體。

比方說，大部分協調器可以使用健康狀態檢查來管理零停機部署。 只有當服務/容器的狀態變更為健康狀態良好時，協調器才會開始將流量路由到服務/容器的執行個體。

當協調器執行應用程式升級時，健康狀態監視尤為重要。 某些協調器 (例如 Azure Service Fabric) 會分階段升級服務 — 例如，它們可能會為每個應用程式升級進行五分之一的叢集介面更新。 在相同時間升級的一組節點即為一個「升級網域」  。 每個升級網域都已升級並可供使用者使用之後，該升級網域還必須通過健康狀態檢查，部署才會移到下一個升級網域。

服務健康狀態的另一個重點是服務的報告計量。 這是 Service Fabric 等協調器的一項健康狀態模型進階功能。 使用協調器時，計量非常重要，因為其可用來平衡資源使用狀況。 計量也是系統健康狀態的指標。 比方說，您的應用程式可能有許多微服務，而每個執行個體都會報告每秒要求數 (RPS) 計量。 如果某一個服務比其他服務使用更多資源 (記憶體、處理器等)，協調器可以在叢集中移動服務執行個體，以嘗試維護平均的資源使用率。

請注意，Azure Service Fabric 隨附的[健康情況監視模型](/azure/service-fabric/service-fabric-health-introduction)比簡單的健康情況檢查更進階。

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>進階監視：視覺效果、分析和警示

監視的最後一個部分是視覺化事件資料流、報告服務效能，並在偵測到問題時發出警示。 您可以使用不同解決方案來進行這方面的監視。

您可以使用簡單的自訂應用程式以顯示服務狀態，例如在說明 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 時介紹過的自訂頁面。 或者，您可以使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)這類更進階的工具，以依據事件資料流來發出警示。

最後，如果您已儲存所有事件資料流，即可使用 Microsoft Power BI 或 Kibana 或 Splunk 等其他解決方案來視覺化資料。

## <a name="additional-resources"></a>其他資源

- **適用於 ASP.NET Core 的 HealthChecks 和 HealthChecks UI** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Service Fabric 健康情況監視簡介** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure 監視器**
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[上一頁](implement-circuit-breaker-pattern.md)
>[下一頁](../secure-net-microservices-web-applications/index.md)
