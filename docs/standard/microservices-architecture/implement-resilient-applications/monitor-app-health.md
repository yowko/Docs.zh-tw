---
title: 健康情況監視
description: 瀏覽實作健康情況監視的其中一種方式。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362479"
---
# <a name="health-monitoring"></a><span data-ttu-id="0ebeb-103">健康情況監視</span><span class="sxs-lookup"><span data-stu-id="0ebeb-103">Health monitoring</span></span>

<span data-ttu-id="0ebeb-104">健康情況監視功能可提供近即時的容器和微服務狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="0ebeb-105">健康情況監視功能對微服務運作的各方面來說都非常重要，尤其當協調器要分階段執行部分應用程式升級時更是如此，如稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="0ebeb-106">微服務應用程式通常使用活動訊號或健康情況檢查，使其效能監視器、排程器及協調器可以追蹤許多服務。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="0ebeb-107">如果服務無法視需求或依排程傳送「運作正常」的訊號，當您部署更新時應用程式可能會面臨風險，或可能會太晚偵測到失敗，讓故障一發不可收拾，進而導致全面中斷。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="0ebeb-108">在一般模型中，服務會傳送其狀態報告，而該彙總資訊可提供應用程式健康情況的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="0ebeb-109">如果您是使用協調器，則可以提供健康情況資訊給協調器的叢集，使叢集可以據以採取行動。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="0ebeb-110">如果您為應用程式投入自訂的高品質健康情況報告，即可更輕鬆地偵測執行中的應用程式並修正問題。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="0ebeb-111">在 ASP.NET Core 服務中實作健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="0ebeb-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="0ebeb-112">開發 ASP.NET Core 微服務或 Web 應用程式時，您可以使用 ASP.NET 小組所提供、名為 *Health Checks* 的實驗性頻外程式庫 (不是 ASP.NETCore 中正式提供的，且現在已被取代)。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-112">When developing an ASP.NET Core microservice or web application, you can use an experimental out-of-band library (not official as part of ASP.NETCore and now deprecated) named *Health Checks* from the ASP.NET team.</span></span> <span data-ttu-id="0ebeb-113">您可以在這個 [dotnet 架構 GitHub 存放庫](https://github.com/dotnet-architecture/HealthChecks)中找到它。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-113">It's available at this [dotnet-architecture GitHub repository](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="0ebeb-114">不過，正式版本的*健康情況檢查*[將會在 ASP.NET Core 2.2 中發行](https://github.com/aspnet/Announcements/issues/307) (應該會在 2018 年底正式發行)。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-114">However, the official version of *Health Checks* [will be released in ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (Should be officially released by the end of 2018).</span></span>

<span data-ttu-id="0ebeb-115">這個程式庫不僅簡單易用，還提供功能讓您驗證任何應用程式所需的特定外部資源 (例如 SQL Server 資料庫或遠端 API) 是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="0ebeb-116">使用這個程式庫時，您也可以自行決定何種情況下表示資源狀況良好，如我們稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="0ebeb-117">若要使用這個程式庫，您必須先使用微服務中的程式庫。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="0ebeb-118">接著，您需要可查詢健康情況報告的前端應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="0ebeb-119">這裡的前端應用程式可能是自訂的報告應用程式，或能根據健康情況採取動作的協調器本身。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-119">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="0ebeb-120">在您的後端 ASP.NET 微服務中使用 HealthChecks 程式庫</span><span class="sxs-lookup"><span data-stu-id="0ebeb-120">Use the HealthChecks library in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="0ebeb-121">您可以看看 eShopOnContainers 範例應用程式如何使用 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="0ebeb-122">首先，您需要為每個微服務定義健康情況良好的構成項目。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="0ebeb-123">在範例應用程式中，如果可以透過 HTTP 存取微服務 API 且其相關 SQL Server 資料庫亦可供存取，即表示微服務健康情況良好。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="0ebeb-124">未來，您將能夠以 NuGet 套件形式安裝 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-124">In the future, you'll be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="0ebeb-125">但在本文撰寫當下，您仍必須下載並編譯程式碼以作為方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="0ebeb-126">複製位於 <https://github.com/dotnet-architecture/HealthChecks> 的程式碼並將下列資料夾複製到您的解決方案：</span><span class="sxs-lookup"><span data-stu-id="0ebeb-126">Clone the code available at <https://github.com/dotnet-architecture/HealthChecks> and copy the following folders to your solution:</span></span>

- <span data-ttu-id="0ebeb-127">src/common</span><span class="sxs-lookup"><span data-stu-id="0ebeb-127">src/common</span></span>
- <span data-ttu-id="0ebeb-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0ebeb-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
- <span data-ttu-id="0ebeb-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0ebeb-129">src/Microsoft.Extensions.HealthChecks</span></span>
- <span data-ttu-id="0ebeb-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="0ebeb-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="0ebeb-131">您也可以使用適用於 Azure 的額外檢查 (Microsoft.Extensions.HealthChecks.AzureStorage)，但因為這一版的 eShopOnContainers 對 Azure 沒有任何相依性，所以您並不需要。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="0ebeb-132">您也不需要 ASP.NET 健康情況檢查，因為 eShopOnContainers 是以 ASP.NET Core 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="0ebeb-133">圖 8-7 顯示 Visual Studio 中的 HealthChecks 程式庫，它已備妥可供任何微服務作為建置組塊。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-133">Figure 8-7 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![顯示三個專案的 HealthChecks 資料夾解決方案總管檢視。](./media/image6.png)

<span data-ttu-id="0ebeb-135">**圖 8-7**。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-135">**Figure 8-7**.</span></span> <span data-ttu-id="0ebeb-136">Visual Studio 方案中的 ASP.NET Core HealthChecks 程式庫原始程式碼</span><span class="sxs-lookup"><span data-stu-id="0ebeb-136">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="0ebeb-137">如前所述，您在每個微服務專案中的首要任務就是新增三個 HealthChecks 程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-137">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="0ebeb-138">接著，您即可新增要在該微服務中執行的健康情況檢查動作。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-138">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="0ebeb-139">這些動作基本上是相依於其他微服務 (HttpUrlCheck) 或資料庫 (針對 SQL Server 資料庫，目前為 SqlCheck\*)。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-139">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="0ebeb-140">接著，在每個 ASP.NET 微服務或 ASP.NET Web 應用程式的啟動類別中新增動作。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-140">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="0ebeb-141">若要為每個服務或 Web 應用程式進行設定，請使用一個 AddHealthCheck 方法來新增其所有的 HTTP 或資料庫相依性。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-141">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="0ebeb-142">例如，eShopOnContainers 的 MVC Web 應用程式仰賴許多服務，因此會新增數種 AddCheck 方法至健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-142">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="0ebeb-143">例如，您可以在下列 (已簡化) 程式碼中了解目錄微服務如何新增其對 SQL Server 資料庫的相依性。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-143">For instance, in the following (simplified) code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="0ebeb-144">不過，eShopOnContainers 的 MVC Web 應用程式對其餘微服務具有多個相依性。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-144">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="0ebeb-145">因此，它會為每個微服務呼叫一個 AddUrlCheck 方法，如下列 (已簡化) 範例所示：</span><span class="sxs-lookup"><span data-stu-id="0ebeb-145">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following (simplified) example:</span></span>

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

<span data-ttu-id="0ebeb-146">如此一來，微服務會在其所有檢查都是狀況良好時才會提供「狀況良好」狀態。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-146">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="0ebeb-147">如果微服務對服務或 SQL Server 沒有相依性，就只需新增 Healthy("Ok") 檢查。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-147">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="0ebeb-148">下列程式碼取自 eShopOnContainers `basket.api` 微服務。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-148">The following code is from the eShopOnContainers `basket.api` microservice.</span></span> <span data-ttu-id="0ebeb-149">(購物籃微服務會使用 Redis 快取，但程式庫並未包含 Redis 健康情況檢查提供者)。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-149">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="0ebeb-150">若要讓服務或 Web 應用程式公開健康情況檢查端點，就必須啟用 `UseHealthChecks([*url_for_health_checks*])` 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-150">For a service or web application to expose the health check endpoint, it has to enable the `UseHealthChecks([*url_for_health_checks*])` extension method.</span></span> <span data-ttu-id="0ebeb-151">如下列已簡化程式碼所示，這個方法用於 ASP.NET Core 服務或 Web 應用程式 `Program` 類別之主要方法的 `WebHostBuilder` 層級中，並緊接在 <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> 之後：</span><span class="sxs-lookup"><span data-stu-id="0ebeb-151">This method goes at the `WebHostBuilder` level in the main method of the `Program` class of your ASP.NET Core service or web application, right after <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> as shown in the following simplified code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

<span data-ttu-id="0ebeb-152">程序會以此方式運作：每個微服務都會公開端點 /hc。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-152">The process works this way: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="0ebeb-153">HealthChecks 程式庫 ASP.NET Core 中介軟體會建立該端點。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-153">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="0ebeb-154">叫用該端點時，它會執行啟動類別之 AddHealthChecks 方法中所設定的所有健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-154">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="0ebeb-155">UseHealthChecks 方法必須使用連接埠或路徑。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-155">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="0ebeb-156">該連接埠或路徑是用來檢查服務健康情況的端點。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-156">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="0ebeb-157">例如，目錄微服務會使用路徑 /hc。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-157">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="cache-health-check-responses"></a><span data-ttu-id="0ebeb-158">快取健康情況檢查回應</span><span class="sxs-lookup"><span data-stu-id="0ebeb-158">Cache health check responses</span></span>

<span data-ttu-id="0ebeb-159">如果您不想造成服務出現拒絕服務 (DoS) 的問題，或不希望太頻繁的資源檢查會影響服務效能，您可以快取傳回項目，並設定每個健康情況檢查的快取期間。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-159">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="0ebeb-160">內部預設的快取期間為 5 分鐘，但您可以變更每個健康情況檢查的快取期間，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0ebeb-160">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="0ebeb-161">查詢微服務以報告其健康情況</span><span class="sxs-lookup"><span data-stu-id="0ebeb-161">Query your microservices to report about their health status</span></span>

<span data-ttu-id="0ebeb-162">完成此文章中說明的健康情況檢查設定並在 Docker 中開始執行微服務之後，您就可以直接從瀏覽器檢查微服務的健康情況。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-162">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span>

<span data-ttu-id="0ebeb-163">您必須在 Docker 主機中發佈容器連接埠，以便透過外部 Docker 主機 IP 或 `localhost` 存取容器，如圖 8-8 所示。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-163">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![健康情況檢查所傳回 JSON 回應的瀏覽器檢視](./media/image7.png)

<span data-ttu-id="0ebeb-165">**圖 8-8**。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-165">**Figure 8-8**.</span></span> <span data-ttu-id="0ebeb-166">從瀏覽器檢查單一服務的健康情況</span><span class="sxs-lookup"><span data-stu-id="0ebeb-166">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="0ebeb-167">在這個測試中，您可以看到 catalog.api 微服務 (執行於連接埠 5101 上) 健康情況良好，並以 JSON 形式傳回 HTTP 狀態 200 和狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-167">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="0ebeb-168">這表示，服務也已內部檢查其 SQL Server 資料庫相依性的健康情況，而該健康情況檢查已自行回報健康情況良好。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-168">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="0ebeb-169">使用監視程式</span><span class="sxs-lookup"><span data-stu-id="0ebeb-169">Use watchdogs</span></span>

<span data-ttu-id="0ebeb-170">監視程式是一種可以跨服務監看健康情況和負載的個別服務，它會查詢稍早說明過的 `HealthChecks` 程式庫以回報微服務的健康情況。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-170">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="0ebeb-171">這可協助防止從單一服務角度無法偵測出的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-171">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="0ebeb-172">監視程式也是裝載程式碼的好地方，以針對已知情況執行修復動作，而不需使用者互動。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-172">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="0ebeb-173">eShopOnContainers 範例包含顯示範例健康情況檢查報告的網頁，如圖 8-9 所示。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-173">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="0ebeb-174">這是一種最簡單的監視程式，因為它只會顯示 eShopOnContainers 中的微服務和 Web 應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-174">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="0ebeb-175">通常監視程式也會在偵測到健康情況不良時採取動作。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-175">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![WebStatus 應用程式的瀏覽器檢視，顯示來自 eShopOnContainers 的五個微服務的健康情況狀態](./media/image8.png)

<span data-ttu-id="0ebeb-177">**圖 8-9**。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-177">**Figure 8-9**.</span></span> <span data-ttu-id="0ebeb-178">eShopOnContainers 中的範例健康情況檢查報告</span><span class="sxs-lookup"><span data-stu-id="0ebeb-178">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="0ebeb-179">簡單來說，ASP.NET Core HealthChecks 程式庫中的 ASP.NET 中介軟體會針對每個微服務提供單一的健康情況檢查端點。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-179">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="0ebeb-180">其會執行端點中定義的所有健康情況檢查，並根據這所有檢查傳回整體健康情況。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-180">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="0ebeb-181">HealthChecks 程式庫可透過未來外部資源的新健康情況檢查而進行擴充 。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-181">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="0ebeb-182">例如，我們預期未來程式庫必須針對 Redis 快取和其他資料庫進行健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-182">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="0ebeb-183">程式庫可按照多個服務或應用程式相依性來提供健康情況報告，以便您依據這些健康情況檢查採取動作。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-183">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="0ebeb-184">使用協調器時的健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="0ebeb-184">Health checks when using orchestrators</span></span>

<span data-ttu-id="0ebeb-185">為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-185">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="0ebeb-186">當協調器判斷某個服務/容器健康情況不良時，它會停止將要求路由至該執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-186">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="0ebeb-187">它通常也會建立該容器的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-187">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="0ebeb-188">例如，大部分協調器可以使用健康情況檢查來管理零停機部署。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-188">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="0ebeb-189">只有當服務/容器的狀態變更為健康情況良好時，協調器才會開始將流量路由到服務/容器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-189">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="0ebeb-190">當協調器執行應用程式升級時，健康情況監視尤為重要。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-190">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="0ebeb-191">某些協調器 (例如 Azure Service Fabric) 會分階段升級服務 — 例如，它們可能會為每個應用程式升級進行五分之一的叢集介面更新。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-191">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="0ebeb-192">在相同時間升級的一組節點即為一個「升級網域」。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-192">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="0ebeb-193">每個升級網域都已升級並可供使用者使用之後，該升級網域還必須通過健康情況檢查，部署才會移到下一個升級網域。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-193">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="0ebeb-194">服務健康情況的另一個重點是服務的報告計量。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-194">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="0ebeb-195">這是 Service Fabric 等協調器的一個健康情況模型進階功能。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-195">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="0ebeb-196">使用協調器時，計量非常重要，因為其可用來平衡資源使用狀況。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-196">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="0ebeb-197">計量也是系統健康情況的指標。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-197">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="0ebeb-198">例如，您的應用程式可能有許多微服務，而每個執行個體都會報告每秒要求數 (RPS) 計量。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-198">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="0ebeb-199">如果某一個服務比其他服務使用更多資源 (記憶體、處理器等)，協調器可以在叢集中移動服務執行個體，以嘗試維護平均的資源使用率。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-199">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="0ebeb-200">請注意，Azure Service Fabric 隨附的[健康情況監視模型](/azure/service-fabric/service-fabric-health-introduction)比簡單的健康情況檢查更進階。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-200">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="0ebeb-201">進階監視：視覺效果、分析和警示</span><span class="sxs-lookup"><span data-stu-id="0ebeb-201">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="0ebeb-202">監視的最後一個部分是視覺化事件資料流、報告服務效能，並在偵測到問題時發出警示。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-202">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="0ebeb-203">您可以使用不同解決方案來進行這方面的監視。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-203">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="0ebeb-204">您可以使用簡單的自訂應用程式以顯示服務狀態，例如我們在說明 [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks) 時介紹過的自訂頁面。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-204">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="0ebeb-205">或者，您可以使用 Azure Application Insights 這類更進階的工具，以依據事件資料流來發出警示。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-205">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="0ebeb-206">最後，如果您已儲存所有事件資料流，即可使用 Microsoft Power BI 或 Kibana 或 Splunk 等其他解決方案來視覺化資料。</span><span class="sxs-lookup"><span data-stu-id="0ebeb-206">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0ebeb-207">其他資源</span><span class="sxs-lookup"><span data-stu-id="0ebeb-207">Additional resources</span></span>

- <span data-ttu-id="0ebeb-208">**ASP.NET Core HealthChecks** (實驗性版本)\\</span><span class="sxs-lookup"><span data-stu-id="0ebeb-208">**ASP.NET Core HealthChecks** (experimental release)\\</span></span>
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- <span data-ttu-id="0ebeb-209">**Service Fabric 健康情況監視簡介**\\</span><span class="sxs-lookup"><span data-stu-id="0ebeb-209">**Introduction to Service Fabric health monitoring**\\</span></span>
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="0ebeb-210">**Azure Application Insights**\\</span><span class="sxs-lookup"><span data-stu-id="0ebeb-210">**Azure Application Insights**\\</span></span>
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- <span data-ttu-id="0ebeb-211">**Microsoft Operations Management Suite**\\</span><span class="sxs-lookup"><span data-stu-id="0ebeb-211">**Microsoft Operations Management Suite**\\</span></span>
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
><span data-ttu-id="0ebeb-212">[上一頁](implement-circuit-breaker-pattern.md)
>[下一頁](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="0ebeb-212">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>