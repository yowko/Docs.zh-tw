---
title: 健康狀態監視
description: 瀏覽實作健康情況監視的其中一種方式。
ms.date: 01/07/2019
ms.openlocfilehash: 3b81537ca8e0c5cc7ce15ab64ab3235b699dc7a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040070"
---
# <a name="health-monitoring"></a><span data-ttu-id="2a63e-103">健康狀態監視</span><span class="sxs-lookup"><span data-stu-id="2a63e-103">Health monitoring</span></span>

<span data-ttu-id="2a63e-104">健康狀態監視功能可提供近即時的容器和微服務狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="2a63e-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="2a63e-105">健康狀態監視功能對微服務運作的各方面來說都非常重要，尤其當協調器要分階段執行部分應用程式升級時更是如此，如稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="2a63e-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="2a63e-106">微服務應用程式通常使用活動訊號或健康狀態檢查，使其效能監視器、排程器及協調器可以追蹤許多服務。</span><span class="sxs-lookup"><span data-stu-id="2a63e-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="2a63e-107">如果服務無法視需求或依排程傳送「運作正常」的訊號，當您部署更新時應用程式可能會面臨風險，或可能會太晚偵測到失敗，讓故障一發不可收拾，進而導致全面中斷。</span><span class="sxs-lookup"><span data-stu-id="2a63e-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="2a63e-108">在一般模型中，服務會傳送其狀態報告，而該彙總資訊可提供應用程式健康狀態的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="2a63e-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="2a63e-109">如果您是使用協調器，則可以提供健康情況資訊給協調器的叢集，使叢集可以據以採取行動。</span><span class="sxs-lookup"><span data-stu-id="2a63e-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="2a63e-110">如果您為應用程式投入自訂的高品質健康情況報告，即可更輕鬆地偵測執行中的應用程式並修正問題。</span><span class="sxs-lookup"><span data-stu-id="2a63e-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="2a63e-111">在 ASP.NET Core 服務中實作健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="2a63e-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="2a63e-112">在開發 ASP.NET Core 微服務或 Web 應用程式時，您可以使用 ASP.NET Core 2.2 中發佈的內建健康情況檢查功能。</span><span class="sxs-lookup"><span data-stu-id="2a63e-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="2a63e-113">如同許多 ASP.NET Core 功能，健康情況檢查隨附一組服務與中介軟體。</span><span class="sxs-lookup"><span data-stu-id="2a63e-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="2a63e-114">健康情況服務和中介軟體不僅簡單易用，還提供功能讓您驗證應用程式所需的任何外部資源 (例如 SQL Server 資料庫或遠端 API) 是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="2a63e-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="2a63e-115">使用這個功能時，您也可以自行決定何種情況下表示資源狀況良好，如我們稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="2a63e-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="2a63e-116">若要有效地使用這個功能，您需要先在微服務中設定服務。</span><span class="sxs-lookup"><span data-stu-id="2a63e-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="2a63e-117">接著，您需要可查詢健康狀態報告的前端應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a63e-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="2a63e-118">這裡的前端應用程式可能是自訂的報告應用程式，或能根據健康情況採取動作的協調器本身。</span><span class="sxs-lookup"><span data-stu-id="2a63e-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="2a63e-119">在您的後端 ASP.NET 微服務中使用 HealthChecks 功能</span><span class="sxs-lookup"><span data-stu-id="2a63e-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="2a63e-120">在本節中，您將了解如何在樣本 ASP.NET Core 2.2 Web API 應用程式中使用 HealthChecks 功能。</span><span class="sxs-lookup"><span data-stu-id="2a63e-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="2a63e-121">在大規模微服務 (例如 eShopOnContainers) 實作這個功能，稍後章節將有所說明。</span><span class="sxs-lookup"><span data-stu-id="2a63e-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="2a63e-122">首先，您需要為每個微服務定義健康狀態良好的構成項目。</span><span class="sxs-lookup"><span data-stu-id="2a63e-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="2a63e-123">在範例應用程式中，如果可以透過 HTTP 存取微服務 API 且其相關 SQL Server 資料庫亦可供存取，即表示微服務健康狀態良好。</span><span class="sxs-lookup"><span data-stu-id="2a63e-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="2a63e-124">在 .NET Core 2.2 中，您可以使用內建 API 來設定服務，並以下列方式新增微服務及其相關 SQL Server 資料庫的健康情況檢查：</span><span class="sxs-lookup"><span data-stu-id="2a63e-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="2a63e-125">在上述程式碼中，`services.AddHealthChecks()` 方法會設定基本 HTTP 檢查，傳回狀態碼 **200**，表示「良好」。</span><span class="sxs-lookup"><span data-stu-id="2a63e-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="2a63e-126">此外，`AddCheck()` 擴充方法會設定一個自訂 `SqlConnectionHealthCheck`，檢查相關 SQL Database 的健康情況。</span><span class="sxs-lookup"><span data-stu-id="2a63e-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="2a63e-127">`AddCheck()` 方法會使用指定的名稱和類型為 `IHealthCheck` 的實作來新增健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="2a63e-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="2a63e-128">您可以使用 AddCheck 方法新增多個健康情況檢查，讓微服務不會提供「良好」狀態，直到其所有檢查皆為良好為止。</span><span class="sxs-lookup"><span data-stu-id="2a63e-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="2a63e-129">`SqlConnectionHealthCheck` 是一種自訂類別，其會實作 `IHealthCheck`，而此實作會採取連接字串作為建構函式參數，並執行簡單查詢，以檢查 SQL 資料庫的連線是否成功。</span><span class="sxs-lookup"><span data-stu-id="2a63e-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="2a63e-130">如果查詢執行成功，則它會傳回 `HealthCheckResult.Healthy()`，若失敗，則會傳回 `FailureStatus` 與實際例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a63e-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="2a63e-131">請注意，在上述程式碼中，`Select 1` 是用來檢查資料庫健康情況的查詢。</span><span class="sxs-lookup"><span data-stu-id="2a63e-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="2a63e-132">為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="2a63e-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="2a63e-133">請務必讓您的資料庫查詢保持效率，以便這些作業可以快速執行，但不會產生更高的資源使用率。</span><span class="sxs-lookup"><span data-stu-id="2a63e-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="2a63e-134">最後，建立一個回應 url 路徑 "/hc" 的中介軟體：</span><span class="sxs-lookup"><span data-stu-id="2a63e-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

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

<span data-ttu-id="2a63e-135">叫用端點 `<yourmicroservice>/hc` 時，它會執行啟動類別中 `AddHealthChecks()` 方法內所設定的所有健康狀態檢查，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="2a63e-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="2a63e-136">eShopOnContainers 中的 HealthChecks 實作</span><span class="sxs-lookup"><span data-stu-id="2a63e-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="2a63e-137">eShopOnContainers 中的微服務依賴多個服務來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="2a63e-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="2a63e-138">例如，來自 eShopOnContainers 的 `Catalog.API` 微服務依賴多個服務，例如 Azure Blob 儲存體、SQL Server 和 RabbitMQ。</span><span class="sxs-lookup"><span data-stu-id="2a63e-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="2a63e-139">因此，它具有數個使用 `AddCheck()` 方法新增的健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="2a63e-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="2a63e-140">對於每個相依服務，需要新增一個自訂 `IHealthCheck`，定義其各自的健康情況狀態。</span><span class="sxs-lookup"><span data-stu-id="2a63e-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="2a63e-141">開放原始碼專案 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 解決了這個問題，方法為針對每個建立在.NET Core 2.2 之上的企業服務提供自訂的健康情況檢查實作，。</span><span class="sxs-lookup"><span data-stu-id="2a63e-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="2a63e-142">每個健康情況檢查都可當成個別 NuGet 套件提供，然後便可輕鬆地將其新增至專案。</span><span class="sxs-lookup"><span data-stu-id="2a63e-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="2a63e-143">eShopOnContainers 會在其所有的微服務中廣泛使用它們。</span><span class="sxs-lookup"><span data-stu-id="2a63e-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="2a63e-144">例如，在 `Catalog.API` 微服務中，已新增下列 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="2a63e-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Catalog.API 專案的解決方案總管檢視，可在其中參考 AspNetCore.Diagnostics.HealthChecks NuGet 套件](./media/image6.png)

<span data-ttu-id="2a63e-146">**圖 8-7**。</span><span class="sxs-lookup"><span data-stu-id="2a63e-146">**Figure 8-7**.</span></span> <span data-ttu-id="2a63e-147">目錄 API 中使用 AspNetCore.Diagnostics.HealthChecks 實作的自訂健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="2a63e-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="2a63e-148">在下列程式碼中，已針對每個相依服務新增健康情況檢查實作，然後設定中介軟體：</span><span class="sxs-lookup"><span data-stu-id="2a63e-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="2a63e-149">最後，我們會新增 HealthCheck 中介軟體來接聽 "/hc" 端點：</span><span class="sxs-lookup"><span data-stu-id="2a63e-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="2a63e-150">查詢微服務以報告其健康情況</span><span class="sxs-lookup"><span data-stu-id="2a63e-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="2a63e-151">完成此文章中說明的健康情況檢查設定並在 Docker 中開始執行微服務之後，您就可以直接從瀏覽器檢查微服務的健康情況。</span><span class="sxs-lookup"><span data-stu-id="2a63e-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="2a63e-152">您必須在 Docker 主機中發佈容器連接埠，以便透過外部 Docker 主機 IP 或 `localhost` 存取容器，如圖 8-8 所示。</span><span class="sxs-lookup"><span data-stu-id="2a63e-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![健康情況檢查所傳回 JSON 回應的瀏覽器檢視](./media/image7.png)

<span data-ttu-id="2a63e-154">**圖 8-8**。</span><span class="sxs-lookup"><span data-stu-id="2a63e-154">**Figure 8-8**.</span></span> <span data-ttu-id="2a63e-155">從瀏覽器檢查單一服務的健康狀態</span><span class="sxs-lookup"><span data-stu-id="2a63e-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="2a63e-156">在這個測試中，您可以看到 `Catalog.API` 微服務 (執行於連接埠 5101 上) 良好，並以 JSON 形式傳回 HTTP 狀態 200 和狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="2a63e-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="2a63e-157">服務也已內部檢查其 SQL Server 資料庫相依性和RabbitMQ 的健康情況，因此健康情況檢查已自行回報良好。</span><span class="sxs-lookup"><span data-stu-id="2a63e-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="2a63e-158">使用監視程式</span><span class="sxs-lookup"><span data-stu-id="2a63e-158">Use watchdogs</span></span>

<span data-ttu-id="2a63e-159">監視程式是一種可以跨服務監看健康情況和負載的個別服務，它會查詢稍早說明過的 `HealthChecks` 程式庫以回報微服務的健康情況。</span><span class="sxs-lookup"><span data-stu-id="2a63e-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="2a63e-160">這可協助防止從單一服務角度無法偵測出的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a63e-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="2a63e-161">監視程式也是裝載程式碼的好地方，以針對已知情況執行修復動作，而不需使用者互動。</span><span class="sxs-lookup"><span data-stu-id="2a63e-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="2a63e-162">eShopOnContainers 範例包含顯示範例健康情況檢查報告的網頁，如圖 8-9 所示。</span><span class="sxs-lookup"><span data-stu-id="2a63e-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="2a63e-163">這是一種最簡單的監視程式，因為它只會顯示 eShopOnContainers 中的微服務和 Web 應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="2a63e-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="2a63e-164">通常監視程式也會在偵測到健康狀態不良時採取動作。</span><span class="sxs-lookup"><span data-stu-id="2a63e-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="2a63e-165">幸好，[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 也會提供 [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet 套件，其可用來顯示所設定 URI 中的健康情況檢查結果。</span><span class="sxs-lookup"><span data-stu-id="2a63e-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![WebStatus 應用程式的瀏覽器檢視，其中顯示 eShopOnContainers 中所有微服務的健康情況狀態](./media/image8.png)

<span data-ttu-id="2a63e-167">**圖 8-9**。</span><span class="sxs-lookup"><span data-stu-id="2a63e-167">**Figure 8-9**.</span></span> <span data-ttu-id="2a63e-168">eShopOnContainers 中的範例健康狀態檢查報告</span><span class="sxs-lookup"><span data-stu-id="2a63e-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="2a63e-169">總而言之，此監視程式服務會查詢每個微服務的 "/hc" 端點。</span><span class="sxs-lookup"><span data-stu-id="2a63e-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="2a63e-170">其會執行端點中定義的所有健康狀態檢查，並根據這所有檢查傳回整體健康狀態。</span><span class="sxs-lookup"><span data-stu-id="2a63e-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="2a63e-171">HealthChecksUI 輕鬆耗用幾個設定項目，以及兩行程式碼，而此程式碼需要新增至監視程式服務的 Startup.cs。</span><span class="sxs-lookup"><span data-stu-id="2a63e-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="2a63e-172">健康情況檢查 UI 的樣本組態檔：</span><span class="sxs-lookup"><span data-stu-id="2a63e-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="2a63e-173">新增 HealthChecksUI 的 Startup.cs 檔案：</span><span class="sxs-lookup"><span data-stu-id="2a63e-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="2a63e-174">使用協調器時的健康狀態檢查</span><span class="sxs-lookup"><span data-stu-id="2a63e-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="2a63e-175">為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="2a63e-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="2a63e-176">當協調器判斷某個服務/容器健康狀態不良時，它會停止將要求路由至該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a63e-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="2a63e-177">它通常也會建立該容器的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a63e-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="2a63e-178">比方說，大部分協調器可以使用健康狀態檢查來管理零停機部署。</span><span class="sxs-lookup"><span data-stu-id="2a63e-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="2a63e-179">只有當服務/容器的狀態變更為健康狀態良好時，協調器才會開始將流量路由到服務/容器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a63e-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="2a63e-180">當協調器執行應用程式升級時，健康狀態監視尤為重要。</span><span class="sxs-lookup"><span data-stu-id="2a63e-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="2a63e-181">某些協調器 (例如 Azure Service Fabric) 會分階段升級服務 — 例如，它們可能會為每個應用程式升級進行五分之一的叢集介面更新。</span><span class="sxs-lookup"><span data-stu-id="2a63e-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="2a63e-182">在相同時間升級的一組節點即為一個「升級網域」。</span><span class="sxs-lookup"><span data-stu-id="2a63e-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="2a63e-183">每個升級網域都已升級並可供使用者使用之後，該升級網域還必須通過健康狀態檢查，部署才會移到下一個升級網域。</span><span class="sxs-lookup"><span data-stu-id="2a63e-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="2a63e-184">服務健康狀態的另一個重點是服務的報告計量。</span><span class="sxs-lookup"><span data-stu-id="2a63e-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="2a63e-185">這是 Service Fabric 等協調器的一項健康狀態模型進階功能。</span><span class="sxs-lookup"><span data-stu-id="2a63e-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="2a63e-186">使用協調器時，計量非常重要，因為其可用來平衡資源使用狀況。</span><span class="sxs-lookup"><span data-stu-id="2a63e-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="2a63e-187">計量也是系統健康狀態的指標。</span><span class="sxs-lookup"><span data-stu-id="2a63e-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="2a63e-188">比方說，您的應用程式可能有許多微服務，而每個執行個體都會報告每秒要求數 (RPS) 計量。</span><span class="sxs-lookup"><span data-stu-id="2a63e-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="2a63e-189">如果某一個服務比其他服務使用更多資源 (記憶體、處理器等)，協調器可以在叢集中移動服務執行個體，以嘗試維護平均的資源使用率。</span><span class="sxs-lookup"><span data-stu-id="2a63e-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="2a63e-190">請注意，Azure Service Fabric 隨附的[健康情況監視模型](/azure/service-fabric/service-fabric-health-introduction)比簡單的健康情況檢查更進階。</span><span class="sxs-lookup"><span data-stu-id="2a63e-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="2a63e-191">進階監視：視覺效果、分析和警示</span><span class="sxs-lookup"><span data-stu-id="2a63e-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="2a63e-192">監視的最後一個部分是視覺化事件資料流、報告服務效能，並在偵測到問題時發出警示。</span><span class="sxs-lookup"><span data-stu-id="2a63e-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="2a63e-193">您可以使用不同解決方案來進行這方面的監視。</span><span class="sxs-lookup"><span data-stu-id="2a63e-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="2a63e-194">您可以使用簡單的自訂應用程式以顯示服務狀態，例如在說明 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 時介紹過的自訂頁面。</span><span class="sxs-lookup"><span data-stu-id="2a63e-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="2a63e-195">或者，您可以使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)這類更進階的工具，以依據事件資料流來發出警示。</span><span class="sxs-lookup"><span data-stu-id="2a63e-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="2a63e-196">最後，如果您已儲存所有事件資料流，即可使用 Microsoft Power BI 或 Kibana 或 Splunk 等其他解決方案來視覺化資料。</span><span class="sxs-lookup"><span data-stu-id="2a63e-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2a63e-197">其他資源</span><span class="sxs-lookup"><span data-stu-id="2a63e-197">Additional resources</span></span>

- <span data-ttu-id="2a63e-198">**適用於 ASP.NET Core 的 HealthChecks 和 HealthChecks UI** </span><span class="sxs-lookup"><span data-stu-id="2a63e-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="2a63e-199">**Service Fabric 健康情況監視簡介** </span><span class="sxs-lookup"><span data-stu-id="2a63e-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="2a63e-200">**Azure 監視器**</span><span class="sxs-lookup"><span data-stu-id="2a63e-200">**Azure Monitor**</span></span>  
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="2a63e-201">[上一頁](implement-circuit-breaker-pattern.md)
>[下一頁](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="2a63e-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
