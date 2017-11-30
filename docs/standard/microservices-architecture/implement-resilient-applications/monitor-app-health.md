---
title: "健全狀況監視"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |健全狀況監視"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a><span data-ttu-id="a720c-104">健全狀況監視</span><span class="sxs-lookup"><span data-stu-id="a720c-104">Health monitoring</span></span>

<span data-ttu-id="a720c-105">健全狀況監視，可允許接近即時的容器和 microservices 狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="a720c-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="a720c-106">健全狀況監視，請務必使用多個層面的作業系統 microservices 和時尤其重要 orchestrators 部分應用程式升級中執行階段，如稍後所說明。</span><span class="sxs-lookup"><span data-stu-id="a720c-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="a720c-107">Microservices 為基礎的應用程式通常使用的活動訊號或健全狀況檢查，讓追蹤的許多的服務其效能監視器、 排程器及 orchestrators。</span><span class="sxs-lookup"><span data-stu-id="a720c-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="a720c-108">如果服務無法傳送某種 「 我運作 」 的訊號，視需要或依排程，您的應用程式可能會面臨風險，當您部署更新，或它可能只是偵測失敗太晚，而且無法停止收下的全面中斷的階層式失敗。</span><span class="sxs-lookup"><span data-stu-id="a720c-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="a720c-109">在一般模型中，服務傳送的報告及其狀態，而該資訊彙總提供您的應用程式的健全狀況狀態的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="a720c-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="a720c-110">如果您使用 orchestrator，您可以提供健全狀況資訊發給 orchestrator 的叢集，使叢集可以據此採取行動。</span><span class="sxs-lookup"><span data-stu-id="a720c-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="a720c-111">如果您進行投資高品質的健康情況報告，自訂您的應用程式，您可以偵測並執行應用程式中更輕鬆地修正問題。</span><span class="sxs-lookup"><span data-stu-id="a720c-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="a720c-112">ASP.NET 核心服務中實作健全狀況檢查</span><span class="sxs-lookup"><span data-stu-id="a720c-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="a720c-113">在開發 ASP.NET Core 微服務或 web 應用程式時，您可以使用 HealthChecks 中名為 ASP.NET 小組的程式庫。</span><span class="sxs-lookup"><span data-stu-id="a720c-113">When developing an ASP.NET Core microservice or web application, you can use a library named HealthChecks from the ASP.NET team.</span></span> <span data-ttu-id="a720c-114">（可能 2017 年最早的版本是可在 GitHub 上取得）。</span><span class="sxs-lookup"><span data-stu-id="a720c-114">(As of May 2017, an early release is available on GitHub).</span></span>

<span data-ttu-id="a720c-115">此文件庫不僅簡單易用，並提供功能，可讓您驗證任何特定的外部資源所需的應用程式 （例如 SQL Server 資料庫或遠端的應用程式開發介面中） 正常運作。</span><span class="sxs-lookup"><span data-stu-id="a720c-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="a720c-116">當您使用此程式庫時，您也可以決定其代表資源處於狀況良好，因為我們稍後說明。</span><span class="sxs-lookup"><span data-stu-id="a720c-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="a720c-117">若要使用此程式庫，您必須先使用您 microservices 中的程式庫。</span><span class="sxs-lookup"><span data-stu-id="a720c-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="a720c-118">其次，您需要查詢的前端應用程式的健康情況報告。</span><span class="sxs-lookup"><span data-stu-id="a720c-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="a720c-119">前端應用程式可能是自訂的報告應用程式，或可能的協調者本身可以據以採取動作的健全狀況狀態。</span><span class="sxs-lookup"><span data-stu-id="a720c-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="a720c-120">使用在您的後端 ASP.NET microservices HealthChecks 程式庫</span><span class="sxs-lookup"><span data-stu-id="a720c-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="a720c-121">您可以看到 eShopOnContainers 範例應用程式中使用 HealthChecks 程式庫的方式。</span><span class="sxs-lookup"><span data-stu-id="a720c-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="a720c-122">若要開始，您需要定義構成每個微服務狀況良好狀態的項目。</span><span class="sxs-lookup"><span data-stu-id="a720c-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="a720c-123">範例應用程式、 microservices 是狀況良好，如果微服務應用程式開發介面透過 HTTP 和其相關的 SQL Server 資料庫是否也可存取。</span><span class="sxs-lookup"><span data-stu-id="a720c-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="a720c-124">未來，您將能夠以 NuGet 套件安裝 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a720c-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="a720c-125">但是在撰寫本文時，您必須下載並編譯程式碼做為方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="a720c-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="a720c-126">複製位於 https://github.com/aspnet/HealthChecks 程式碼，並將下列資料夾複製到您的方案。</span><span class="sxs-lookup"><span data-stu-id="a720c-126">Clone the code available at https://github.com/aspnet/HealthChecks and copy the following folders to your solution.</span></span>

  - <span data-ttu-id="a720c-127">src/一般</span><span class="sxs-lookup"><span data-stu-id="a720c-127">src/common</span></span>
  - <span data-ttu-id="a720c-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="a720c-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="a720c-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="a720c-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="a720c-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="a720c-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="a720c-131">您也可以使用額外的檢查像 azure (Microsoft.Extensions.HealthChecks.AzureStorage)，但因為這一版的 eShopOnContainers 在 Azure 上沒有任何相依性，您不需要它。</span><span class="sxs-lookup"><span data-stu-id="a720c-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="a720c-132">因為 eShopOnContainers 以 ASP.NET Core 上不需要 ASP.NET 健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="a720c-133">圖 10-6 會顯示在 Visual Studio 中，準備好可作為建置組塊供任何 microservices HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a720c-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="a720c-134">**圖 10-6**。</span><span class="sxs-lookup"><span data-stu-id="a720c-134">**Figure 10-6**.</span></span> <span data-ttu-id="a720c-135">ASP.NET Core HealthChecks 程式庫原始程式碼的 Visual Studio 方案中</span><span class="sxs-lookup"><span data-stu-id="a720c-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="a720c-136">推出之前，若要在每個微服務專案中的第一件事就是加入三個 HealthChecks 文件庫的參考。</span><span class="sxs-lookup"><span data-stu-id="a720c-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="a720c-137">之後，您可以新增您想要執行的微服務中的健全狀況檢查動作。</span><span class="sxs-lookup"><span data-stu-id="a720c-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="a720c-138">這些動作基本上是在其他 microservices (HttpUrlCheck) 或資料庫上的相依性 (目前 SqlCheck\*的 SQL Server 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="a720c-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="a720c-139">您新增的每個 ASP.NET 微服務 」 或 「 ASP.NET web 應用程式啟動類別中的動作。</span><span class="sxs-lookup"><span data-stu-id="a720c-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="a720c-140">每個服務或 web 應用程式應該設定為一個 AddHealthCheck 方法將所有資料庫或 HTTP 的相依性。</span><span class="sxs-lookup"><span data-stu-id="a720c-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="a720c-141">例如，MVC web 應用程式，從 eShopOnContainers 取決於許多服務，因此會有數種 AddCheck 方法加入至健全狀況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="a720c-142">比方說，下列程式碼中您可以查看目錄微服務在 SQL Server 資料庫上加入相依性的方式。</span><span class="sxs-lookup"><span data-stu-id="a720c-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="a720c-143">不過，eShopOnContainers 的 MVC web 應用程式有多個相依性上 microservices 的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a720c-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="a720c-144">因此，它會呼叫其中一種 AddUrlCheck 方法的每個微服務，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a720c-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="a720c-145">因此，微服務不會提供 「 良好 」 狀態，直到其所有的檢查也是狀況良好。</span><span class="sxs-lookup"><span data-stu-id="a720c-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="a720c-146">如果微服務並沒有相依性，在服務上，或 SQL Server 上，您只應新增 Healthy("Ok") 核取。</span><span class="sxs-lookup"><span data-stu-id="a720c-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="a720c-147">下列程式碼取自 eShopOnContainers basket.api 微服務。</span><span class="sxs-lookup"><span data-stu-id="a720c-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="a720c-148">（購物籃微服務使用 Redis 快取，但文件庫尚未包含 Redis 健全狀況檢查提供者）。</span><span class="sxs-lookup"><span data-stu-id="a720c-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="a720c-149">公開健全狀況檢查端點是服務或 web 應用程式，它有啟用 UseHealthChecks (\[*url\_如\_健全狀況\_檢查*\]) 擴充功能方法。</span><span class="sxs-lookup"><span data-stu-id="a720c-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="a720c-150">這個方法會在 WebHostBuilder 層級中的 ASP.NET Core 服務或 web 應用程式，如下列程式碼所示的 UseKestrel 之後 Program 類別的主要方法。</span><span class="sxs-lookup"><span data-stu-id="a720c-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="a720c-151">處理程序的運作方式如下： 每個微服務會公開端點 /hc。</span><span class="sxs-lookup"><span data-stu-id="a720c-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="a720c-152">HealthChecks 程式庫 ASP.NET Core 中介軟體會建立該端點。</span><span class="sxs-lookup"><span data-stu-id="a720c-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="a720c-153">叫用該端點時，它會執行 AddHealthChecks 中的方法啟動類別中所設定的所有健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="a720c-154">UseHealthChecks 方法預期的連接埠或路徑。</span><span class="sxs-lookup"><span data-stu-id="a720c-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="a720c-155">該連接埠或路徑是用來檢查服務的健全狀況狀態的端點。</span><span class="sxs-lookup"><span data-stu-id="a720c-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="a720c-156">例如，類別目錄的微服務會使用路徑 /hc。</span><span class="sxs-lookup"><span data-stu-id="a720c-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="a720c-157">快取的健康情況檢查回應</span><span class="sxs-lookup"><span data-stu-id="a720c-157">Caching health check responses</span></span>

<span data-ttu-id="a720c-158">因為您不希望您的服務，會造成阻絕服務 (DoS) 或只是不想要藉由檢查資源會影響服務效能頻率太高，您可以快取傳回，設定每個健全狀況檢查的快取持續時間。</span><span class="sxs-lookup"><span data-stu-id="a720c-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="a720c-159">根據預設，快取持續時間在內部設定為 5 分鐘，但您可以變更該快取持續時間，在每個健全狀況檢查，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a720c-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="a720c-160">查詢您 microservices 要報告其健全狀況狀態</span><span class="sxs-lookup"><span data-stu-id="a720c-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="a720c-161">當您完成設定健康情況檢查，如下所述，在 Docker 中開始執行的微服務之後時，您直接可以檢查，從瀏覽器是否狀況良好。</span><span class="sxs-lookup"><span data-stu-id="a720c-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="a720c-162">（這需要，您要發行超出 Docker 主機時，容器連接埠，以便透過 localhost 或外部的 Docker 主機 IP，您可以存取容器。）圖 10-7 會顯示在瀏覽器和對應的回應中的要求。</span><span class="sxs-lookup"><span data-stu-id="a720c-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="a720c-163">**圖 10-7**。</span><span class="sxs-lookup"><span data-stu-id="a720c-163">**Figure 10-7**.</span></span> <span data-ttu-id="a720c-164">正在檢查從瀏覽器的單一服務的健全狀況狀態</span><span class="sxs-lookup"><span data-stu-id="a720c-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="a720c-165">在測試，您可以看到 （連接埠 5101 上執行） catalog.api 微服務狀況良好，在 JSON 中傳回 HTTP 狀態 200 和狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="a720c-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="a720c-166">這也表示，在內部服務也檢查其 SQL Server 資料庫相依性的健全狀況和健全狀況檢查已回報本身為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="a720c-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="a720c-167">使用 watchdogs</span><span class="sxs-lookup"><span data-stu-id="a720c-167">Using watchdogs</span></span>

<span data-ttu-id="a720c-168">監視是不同的服務，可以觀看健全狀況，並藉由查詢早導入的 HealthChecks 程式庫載入跨服務，以及有關 microservices 回報健全狀況。</span><span class="sxs-lookup"><span data-stu-id="a720c-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="a720c-169">這可協助防止將不會偵測根據檢視的單一服務的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a720c-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="a720c-170">Watchdogs 也都可以執行修復動作的已知的情況，而不需使用者互動的裝載程式碼的好地方。</span><span class="sxs-lookup"><span data-stu-id="a720c-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="a720c-171">EShopOnContainers 範例包含會顯示範例健全狀況檢查報表，如圖 10-8 所示的網頁。</span><span class="sxs-lookup"><span data-stu-id="a720c-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="a720c-172">這是最簡單的監視，您可以擁有，因為它已顯示 eShopOnContainers microservices 和 web 應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="a720c-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="a720c-173">通常監視也會採取動作時偵測到的狀況不良狀態。</span><span class="sxs-lookup"><span data-stu-id="a720c-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="a720c-174">**圖 10-8**。</span><span class="sxs-lookup"><span data-stu-id="a720c-174">**Figure 10-8**.</span></span> <span data-ttu-id="a720c-175">在 eShopOnContainers 範例健全狀況檢查報告</span><span class="sxs-lookup"><span data-stu-id="a720c-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="a720c-176">在 [摘要] ASP.NET Core HealthChecks 程式庫中的 ASP.NET 中介軟體會針對每個微服務提供單一的健全狀況檢查端點。</span><span class="sxs-lookup"><span data-stu-id="a720c-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="a720c-177">這將會執行在其中定義的所有健康情況檢查，並傳回根據所有這些檢查的整體健全狀況狀態。</span><span class="sxs-lookup"><span data-stu-id="a720c-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="a720c-178">可透過新的健全狀況檢查的未來外部的資源延伸 HealthChecks 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a720c-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="a720c-179">例如，我們預期時，在未來的程式庫必須 Redis 快取和其他資料庫的健全狀況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="a720c-180">程式庫可讓報表功能的多個服務或應用程式相依性的健全狀況，您可以接著依據採取動作的健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="a720c-181">使用 orchestrators 時的健全狀況檢查</span><span class="sxs-lookup"><span data-stu-id="a720c-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="a720c-182">若要監視您 microservices 的可用性，如 Docker Swarm、 Kubernetes，以及 Service Fabric orchestrators 定期藉由傳送要求以測試 microservices 執行健全狀況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="a720c-183">當 orchestrator 決定服務/容器會處於狀況不良，它會停止要求路由傳送到該執行個體。</span><span class="sxs-lookup"><span data-stu-id="a720c-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="a720c-184">它通常也會建立該容器的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="a720c-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="a720c-185">比方說，大部分 orchestrators 可以管理零停機時間部署使用健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="a720c-186">將服務/容器變更為狀況良好狀態時，才 orchestrator 會開始將流量傳送到服務/容器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a720c-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="a720c-187">當 orchestrator 執行應用程式升級時，健全狀況監視是特別重要。</span><span class="sxs-lookup"><span data-stu-id="a720c-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="a720c-188">某些 orchestrators （例如 Azure Service Fabric) 更新服務中的階段 — 比方說，他們可能會更新每個應用程式升級叢集介面的其中一個第五。</span><span class="sxs-lookup"><span data-stu-id="a720c-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="a720c-189">在相同的時間升級的節點集指*升級網域*。</span><span class="sxs-lookup"><span data-stu-id="a720c-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="a720c-190">每個升級網域已升級，並提供給使用者之後，該升級網域必須通過健全狀況檢查，之後再部署移到下一個升級網域。</span><span class="sxs-lookup"><span data-stu-id="a720c-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="a720c-191">服務健全狀況的另一個層面會報告從服務的度量資訊。</span><span class="sxs-lookup"><span data-stu-id="a720c-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="a720c-192">這是一項進階的功能的某些 orchestrators，例如服務網狀架構健全狀況模型。</span><span class="sxs-lookup"><span data-stu-id="a720c-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="a720c-193">度量資訊是很重要，因為它們用來平衡資源使用狀況，請使用 orchestrator 時。</span><span class="sxs-lookup"><span data-stu-id="a720c-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="a720c-194">度量也可以是系統健全狀況的指標。</span><span class="sxs-lookup"><span data-stu-id="a720c-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="a720c-195">比方說，您可能有許多 microservices，應用程式，每個執行個體報告每秒的要求 (RP) 度量資訊。</span><span class="sxs-lookup"><span data-stu-id="a720c-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="a720c-196">如果一項服務使用比其他服務的更多資源 （記憶體、 處理器等），orchestrator 無法服務執行個體中移動叢集，以嘗試維護甚至資源使用率。</span><span class="sxs-lookup"><span data-stu-id="a720c-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="a720c-197">請注意，是否您使用 Azure Service Fabric，它會提供它自己[監視健全狀況模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)，也就是更進階比簡單的健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="a720c-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="a720c-198">進階監視： 視覺效果、 分析和警示</span><span class="sxs-lookup"><span data-stu-id="a720c-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="a720c-199">監視的最後一個部分視覺化報表服務效能，並在偵測到的問題時發出警示的事件資料流。</span><span class="sxs-lookup"><span data-stu-id="a720c-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="a720c-200">您可以使用不同的解決方案，這方面的監視。</span><span class="sxs-lookup"><span data-stu-id="a720c-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="a720c-201">您可以使用簡單顯示您的服務狀態的自訂應用程式，像是自訂頁面介紹當我們解釋[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks)。</span><span class="sxs-lookup"><span data-stu-id="a720c-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="a720c-202">或者，您可以使用更進階的工具，像是 Azure Application Insights 和 Operations Management Suite 引發事件的資料流為基礎的警示。</span><span class="sxs-lookup"><span data-stu-id="a720c-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="a720c-203">最後，如果您已儲存的事件資料流，您可以使用 Microsoft Power BI 或類似 Kibana 或 Splunk 協力廠商解決方案來視覺化資料。</span><span class="sxs-lookup"><span data-stu-id="a720c-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a720c-204">其他資源</span><span class="sxs-lookup"><span data-stu-id="a720c-204">Additional resources</span></span>

-   <span data-ttu-id="a720c-205">**ASP.NET Core HealthChecks** （最早版本） [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="a720c-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="a720c-206">**服務網狀架構健全狀況監視簡介**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="a720c-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="a720c-207">**Azure 的 Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="a720c-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="a720c-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="a720c-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a720c-209">[上一個](實作-循環-分隔-pattern.md) [下一步] (.../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="a720c-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
