---
title: "健康狀態監視"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 健康狀態監視"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76821e27613335609527b867a6b94dac551f6235
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="health-monitoring"></a><span data-ttu-id="8f80e-104">健康狀態監視</span><span class="sxs-lookup"><span data-stu-id="8f80e-104">Health monitoring</span></span>

<span data-ttu-id="8f80e-105">健康狀態監視功能可提供近即時的容器和微服務狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="8f80e-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="8f80e-106">健康狀態監視功能對微服務運作的各方面來說都非常重要，尤其當協調器要分階段執行部分應用程式升級時更是如此，如稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="8f80e-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="8f80e-107">微服務應用程式通常使用活動訊號或健康狀態檢查，使其效能監視器、排程器及協調器可以追蹤許多服務。</span><span class="sxs-lookup"><span data-stu-id="8f80e-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="8f80e-108">如果服務無法視需求或依排程傳送「運作正常」的訊號，當您部署更新時應用程式可能會面臨風險，或可能會太晚偵測到失敗，讓故障一發不可收拾，進而導致全面中斷。</span><span class="sxs-lookup"><span data-stu-id="8f80e-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="8f80e-109">在一般模型中，服務會傳送其狀態報告，而該彙總資訊可提供應用程式健康狀態的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="8f80e-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="8f80e-110">如果您是使用協調器，則可以提供健康狀態資訊給協調器的叢集，使叢集可以據此採取行動。</span><span class="sxs-lookup"><span data-stu-id="8f80e-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="8f80e-111">如果您為應用程式投入自訂的高品質健康狀態報告，即可更輕鬆地偵測執行中的應用程式並修正問題。</span><span class="sxs-lookup"><span data-stu-id="8f80e-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="8f80e-112">在 ASP.NET Core 服務中實作健康狀態檢查</span><span class="sxs-lookup"><span data-stu-id="8f80e-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="8f80e-113">開發 ASP.NET Core 微服務或 Web 應用程式時，您可以使用 ASP.NET 小組提供的 `HealthChecks` 程式庫。</span><span class="sxs-lookup"><span data-stu-id="8f80e-113">When developing an ASP.NET Core microservice or web application, you can use a library named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="8f80e-114">您可在這個 [GitHub 存放庫](https://github.com/dotnet-architecture/HealthChecks)中取得早期版本。</span><span class="sxs-lookup"><span data-stu-id="8f80e-114">Early release is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="8f80e-115">這個程式庫不僅簡單易用，還提供功能讓您驗證任何應用程式所需的特定外部資源 (例如 SQL Server 資料庫或遠端 API) 是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="8f80e-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="8f80e-116">使用這個程式庫時，您也可以自行決定何種情況下表示資源狀況良好，如我們稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="8f80e-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="8f80e-117">若要使用這個程式庫，您必須先使用微服務中的程式庫。</span><span class="sxs-lookup"><span data-stu-id="8f80e-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="8f80e-118">接著，您需要可查詢健康狀態報告的前端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8f80e-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="8f80e-119">這裡的前端應用程式可能是自訂的報告應用程式，或能根據健康狀態採取動作的協調器本身。</span><span class="sxs-lookup"><span data-stu-id="8f80e-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="8f80e-120">在您的後端 ASP.NET 微服務中使用 HealthChecks 程式庫</span><span class="sxs-lookup"><span data-stu-id="8f80e-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="8f80e-121">您可以看看 eShopOnContainers 範例應用程式如何使用 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="8f80e-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="8f80e-122">首先，您需要為每個微服務定義健康狀態良好的構成項目。</span><span class="sxs-lookup"><span data-stu-id="8f80e-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="8f80e-123">在範例應用程式中，如果可以透過 HTTP 存取微服務 API 且其相關 SQL Server 資料庫亦可供存取，即表示微服務健康狀態良好。</span><span class="sxs-lookup"><span data-stu-id="8f80e-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="8f80e-124">未來，您將能夠以 NuGet 套件形式安裝 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="8f80e-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="8f80e-125">但在本文撰寫當下，您仍必須下載並編譯程式碼以作為方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f80e-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="8f80e-126">複製程式碼位於https://github.com/dotnet-architecture/HealthChecks並將下列資料夾複製到您的方案：</span><span class="sxs-lookup"><span data-stu-id="8f80e-126">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="8f80e-127">src/common</span><span class="sxs-lookup"><span data-stu-id="8f80e-127">src/common</span></span>
  - <span data-ttu-id="8f80e-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="8f80e-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="8f80e-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="8f80e-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="8f80e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="8f80e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="8f80e-131">您也可以使用適用於 Azure 的額外檢查 (Microsoft.Extensions.HealthChecks.AzureStorage)，但因為這一版的 eShopOnContainers 對 Azure 沒有任何相依性，所以您並不需要。</span><span class="sxs-lookup"><span data-stu-id="8f80e-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="8f80e-132">您也不需要 ASP.NET 健康狀態檢查，因為 eShopOnContainers 是以 ASP.NET Core 為基礎。</span><span class="sxs-lookup"><span data-stu-id="8f80e-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="8f80e-133">圖 10-6 顯示 Visual Studio 的 HealthChecks 程式庫，其已備妥可供任何微服務作為建置組塊。</span><span class="sxs-lookup"><span data-stu-id="8f80e-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="8f80e-134">**圖 10-6**：</span><span class="sxs-lookup"><span data-stu-id="8f80e-134">**Figure 10-6**.</span></span> <span data-ttu-id="8f80e-135">Visual Studio 方案中的 ASP.NET Core HealthChecks 程式庫原始程式碼</span><span class="sxs-lookup"><span data-stu-id="8f80e-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="8f80e-136">如前所述，您在每個微服務專案中的首要任務就是新增三個 HealthChecks 程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="8f80e-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="8f80e-137">接著，您即可新增要在該微服務中執行的健康狀態檢查動作。</span><span class="sxs-lookup"><span data-stu-id="8f80e-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="8f80e-138">這些動作基本上是相依於其他微服務 (HttpUrlCheck) 或資料庫 (針對 SQL Server 資料庫，目前為 SqlCheck\*)。</span><span class="sxs-lookup"><span data-stu-id="8f80e-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="8f80e-139">接著，在每個 ASP.NET 微服務或 ASP.NET Web 應用程式的啟動類別中新增動作。</span><span class="sxs-lookup"><span data-stu-id="8f80e-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="8f80e-140">若要為每個服務或 Web 應用程式進行設定，請使用一個 AddHealthCheck 方法來新增其所有的 HTTP 或資料庫相依性。</span><span class="sxs-lookup"><span data-stu-id="8f80e-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="8f80e-141">例如，eShopOnContainers 的 MVC Web 應用程式仰賴許多服務，因此會新增數種 AddCheck 方法至健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="8f80e-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="8f80e-142">例如，您可以在下列程式碼中了解目錄微服務如何新增其對 SQL Server 資料庫的相依性。</span><span class="sxs-lookup"><span data-stu-id="8f80e-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="8f80e-143">不過，eShopOnContainers 的 MVC Web 應用程式對其餘微服務具有多個相依性。</span><span class="sxs-lookup"><span data-stu-id="8f80e-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="8f80e-144">因此，它會為每個微服務呼叫一個 AddUrlCheck 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8f80e-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="8f80e-145">如此一來，微服務會在其所有檢查都是狀況良好時才會提供「狀況良好」狀態。</span><span class="sxs-lookup"><span data-stu-id="8f80e-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="8f80e-146">如果微服務對服務或 SQL Server 沒有相依性，就只需新增 Healthy("Ok") 檢查。</span><span class="sxs-lookup"><span data-stu-id="8f80e-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="8f80e-147">下列程式碼取自 eShopOnContainers basket.api 微服務 </span><span class="sxs-lookup"><span data-stu-id="8f80e-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="8f80e-148">(購物籃微服務會使用 Redis 快取，但程式庫並未包含 Redis 健康狀態檢查提供者)。</span><span class="sxs-lookup"><span data-stu-id="8f80e-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="8f80e-149">若要讓服務或 Web 應用程式公開健康狀態檢查端點，就必須啟用 UseHealthChecks(\[*url\_for\_health\_checks*\]) 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="8f80e-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="8f80e-150">如下列程式碼所示，這個方法用於 ASP.NET Core 服務或 Web 應用程式 Program 類別之主要方法的 WebHostBuilder 層級中，並緊接在 UseKestrel 之後。</span><span class="sxs-lookup"><span data-stu-id="8f80e-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="8f80e-151">處理序的運作方式如下：每個微服務會公開端點 /hc。</span><span class="sxs-lookup"><span data-stu-id="8f80e-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="8f80e-152">HealthChecks 程式庫 ASP.NET Core 中介軟體會建立該端點。</span><span class="sxs-lookup"><span data-stu-id="8f80e-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="8f80e-153">叫用該端點時，它會執行啟動類別之 AddHealthChecks 方法中所設定的所有健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="8f80e-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="8f80e-154">UseHealthChecks 方法必須使用連接埠或路徑。</span><span class="sxs-lookup"><span data-stu-id="8f80e-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="8f80e-155">該連接埠或路徑是用來檢查服務健康狀態的端點。</span><span class="sxs-lookup"><span data-stu-id="8f80e-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="8f80e-156">例如，目錄微服務會使用路徑 /hc。</span><span class="sxs-lookup"><span data-stu-id="8f80e-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="8f80e-157">快取健康狀態檢查回應</span><span class="sxs-lookup"><span data-stu-id="8f80e-157">Caching health check responses</span></span>

<span data-ttu-id="8f80e-158">如果您不想造成服務出現拒絕服務 (DoS) 的問題，或不希望太頻繁的資源檢查會影響服務效能，您可以快取傳回項目，並設定每個健康狀態檢查的快取期間。</span><span class="sxs-lookup"><span data-stu-id="8f80e-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="8f80e-159">內部預設的快取期間為 5 分鐘，但您可以變更每個健康狀態檢查的快取期間，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="8f80e-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="8f80e-160">查詢微服務，使其報告其健康狀態</span><span class="sxs-lookup"><span data-stu-id="8f80e-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="8f80e-161">完成此處說明的健康狀態檢查設定後，一旦 Docker 中的微服務開始執行，您就可以直接從瀏覽器檢查微服務是否狀況良好 </span><span class="sxs-lookup"><span data-stu-id="8f80e-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="8f80e-162">(您必須在 Docker 主機之外發佈容器連接埠，以便透過 localhost 或外部的 Docker 主機 IP 來存取容器)。圖 10-7 顯示瀏覽器中的要求和對應的回應。</span><span class="sxs-lookup"><span data-stu-id="8f80e-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="8f80e-163">**圖 10-7**：</span><span class="sxs-lookup"><span data-stu-id="8f80e-163">**Figure 10-7**.</span></span> <span data-ttu-id="8f80e-164">從瀏覽器檢查單一服務的健康狀態</span><span class="sxs-lookup"><span data-stu-id="8f80e-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="8f80e-165">在這個測試中，您可以看到 catalog.api 微服務 (執行於連接埠 5101 上) 健康狀態良好，並以 JSON 形式傳回 HTTP 狀態 200 和狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="8f80e-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="8f80e-166">這表示，服務也已內部檢查其 SQL Server 資料庫相依性的健康狀態，而該健康狀態檢查已自行回報健康狀態良好。</span><span class="sxs-lookup"><span data-stu-id="8f80e-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="8f80e-167">使用監視程式</span><span class="sxs-lookup"><span data-stu-id="8f80e-167">Using watchdogs</span></span>

<span data-ttu-id="8f80e-168">監視程式是一種可以跨服務監看健康狀態和負載的個別服務，其會查詢稍早說明過的 HealthChecks 程式庫以回報微服務的健康狀態。</span><span class="sxs-lookup"><span data-stu-id="8f80e-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="8f80e-169">這可協助防止從單一服務角度無法偵測出的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f80e-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="8f80e-170">監視程式也是裝載程式碼的好地方，以針對已知情況執行修復動作，而不需使用者互動。</span><span class="sxs-lookup"><span data-stu-id="8f80e-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="8f80e-171">eShopOnContainers 範例包含顯示範例健康狀態檢查報告的網頁，如圖 10-8 所示。</span><span class="sxs-lookup"><span data-stu-id="8f80e-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="8f80e-172">這是一種最簡單的監視程式，因為它只會顯示 eShopOnContainers 中的微服務和 Web 應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="8f80e-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="8f80e-173">通常監視程式也會在偵測到健康狀態不良時採取動作。</span><span class="sxs-lookup"><span data-stu-id="8f80e-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="8f80e-174">**圖 10-8**：</span><span class="sxs-lookup"><span data-stu-id="8f80e-174">**Figure 10-8**.</span></span> <span data-ttu-id="8f80e-175">eShopOnContainers 中的範例健康狀態檢查報告</span><span class="sxs-lookup"><span data-stu-id="8f80e-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="8f80e-176">簡單來說，ASP.NET Core HealthChecks 程式庫中的 ASP.NET 中介軟體會針對每個微服務提供單一的健康狀態檢查端點。</span><span class="sxs-lookup"><span data-stu-id="8f80e-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="8f80e-177">其會執行端點中定義的所有健康狀態檢查，並根據這所有檢查傳回整體健康狀態。</span><span class="sxs-lookup"><span data-stu-id="8f80e-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="8f80e-178">HealthChecks 程式庫可透過未來外部資源的新健康狀態檢查而進行擴充 。</span><span class="sxs-lookup"><span data-stu-id="8f80e-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="8f80e-179">例如，我們預期未來程式庫必須針對 Redis 快取和其他資料庫進行健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="8f80e-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="8f80e-180">程式庫可按照多個服務或應用程式相依性來提供健康狀態報告，以便您依據這些健康狀態檢查採取動作。</span><span class="sxs-lookup"><span data-stu-id="8f80e-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="8f80e-181">使用協調器時的健康狀態檢查</span><span class="sxs-lookup"><span data-stu-id="8f80e-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="8f80e-182">為了監視您的微服務可用性，Docker Swarm、Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="8f80e-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="8f80e-183">當協調器判斷某個服務/容器健康狀態不良時，它會停止將要求路由至該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f80e-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="8f80e-184">它通常也會建立該容器的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f80e-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="8f80e-185">比方說，大部分協調器可以使用健康狀態檢查來管理零停機部署。</span><span class="sxs-lookup"><span data-stu-id="8f80e-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="8f80e-186">只有當服務/容器的狀態變更為健康狀態良好時，協調器才會開始將流量路由到服務/容器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f80e-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="8f80e-187">當協調器執行應用程式升級時，健康狀態監視尤為重要。</span><span class="sxs-lookup"><span data-stu-id="8f80e-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="8f80e-188">某些協調器 (例如 Azure Service Fabric) 會分階段升級服務 — 例如，它們可能會為每個應用程式升級進行五分之一的叢集介面更新。</span><span class="sxs-lookup"><span data-stu-id="8f80e-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="8f80e-189">在相同時間升級的一組節點即為一個「升級網域」。</span><span class="sxs-lookup"><span data-stu-id="8f80e-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="8f80e-190">每個升級網域都已升級並可供使用者使用之後，該升級網域還必須通過健康狀態檢查，部署才會移到下一個升級網域。</span><span class="sxs-lookup"><span data-stu-id="8f80e-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="8f80e-191">服務健康狀態的另一個重點是服務的報告計量。</span><span class="sxs-lookup"><span data-stu-id="8f80e-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="8f80e-192">這是 Service Fabric 等協調器的一項健康狀態模型進階功能。</span><span class="sxs-lookup"><span data-stu-id="8f80e-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="8f80e-193">使用協調器時，計量非常重要，因為其可用來平衡資源使用狀況。</span><span class="sxs-lookup"><span data-stu-id="8f80e-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="8f80e-194">計量也是系統健康狀態的指標。</span><span class="sxs-lookup"><span data-stu-id="8f80e-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="8f80e-195">比方說，您的應用程式可能有許多微服務，而每個執行個體都會報告每秒要求數 (RPS) 計量。</span><span class="sxs-lookup"><span data-stu-id="8f80e-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="8f80e-196">如果某一個服務比其他服務使用更多資源 (記憶體、處理器等)，協調器可以在叢集中移動服務執行個體，以嘗試維護平均的資源使用率。</span><span class="sxs-lookup"><span data-stu-id="8f80e-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="8f80e-197">請注意，如果您是使用 Azure Service Fabric，其隨附的[健康狀態監視模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)比簡單的健康狀態檢查更進階。</span><span class="sxs-lookup"><span data-stu-id="8f80e-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="8f80e-198">進階監視：視覺效果、分析和警示</span><span class="sxs-lookup"><span data-stu-id="8f80e-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="8f80e-199">監視的最後一個部分是視覺化事件資料流、報告服務效能，並在偵測到問題時發出警示。</span><span class="sxs-lookup"><span data-stu-id="8f80e-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="8f80e-200">您可以使用不同解決方案來進行這方面的監視。</span><span class="sxs-lookup"><span data-stu-id="8f80e-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="8f80e-201">您可以使用簡單的自訂應用程式以顯示服務狀態，例如我們在說明 [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks) 時介紹過的自訂頁面。</span><span class="sxs-lookup"><span data-stu-id="8f80e-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="8f80e-202">或者，您可以使用 Azure Application Insights 和 Operations Management Suite 這類更進階的工具，以依據事件資料流來發出警示。</span><span class="sxs-lookup"><span data-stu-id="8f80e-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="8f80e-203">最後，如果您已儲存所有事件資料流，即可使用 Microsoft Power BI 或 Kibana 或 Splunk 等協力廠商解決方案來視覺化資料。</span><span class="sxs-lookup"><span data-stu-id="8f80e-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8f80e-204">其他資源</span><span class="sxs-lookup"><span data-stu-id="8f80e-204">Additional resources</span></span>

-   <span data-ttu-id="8f80e-205">**ASP.NET Core HealthChecks** （最早版本） [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="8f80e-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="8f80e-206">**服務網狀架構健全狀況監視簡介**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="8f80e-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="8f80e-207">**Azure 的 Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="8f80e-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="8f80e-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="8f80e-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="8f80e-209">[上一頁] (implement-circuit-breaker-pattern.md) [下一頁] (../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="8f80e-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
