---
title: 使用 Ocelot 實作 API 閘道
description: 了解如何使用 Ocelot 實作 API 閘道，並了解如何在以容器為基礎的環境中使用 Ocelot。
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846942"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="de58d-103">使用 Ocelot 實作 API 閘道</span><span class="sxs-lookup"><span data-stu-id="de58d-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de58d-104">參考微服務應用程式[eShopOn容器](https://github.com/dotnet-architecture/eShopOnContainers)目前使用[特使](https://www.envoyproxy.io/)提供的功能來實現API閘道，而不是前面引用[的Ocelot。](https://github.com/ThreeMammals/Ocelot)</span><span class="sxs-lookup"><span data-stu-id="de58d-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="de58d-105">我們之所以做出此設計選擇，是因為特使對 WebSocket 協定的內置支援，這是 eShopOnContainers 中實現的新 gRPC 服務間通信所要求的。</span><span class="sxs-lookup"><span data-stu-id="de58d-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="de58d-106">但是，我們在指南中保留了此部分，因此您可以將 Ocelot 視為一種簡單、強大且羽量級的 API 閘道，適用于生產級方案。</span><span class="sxs-lookup"><span data-stu-id="de58d-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="de58d-107">架構及設計您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="de58d-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="de58d-108">下面的體系結構圖顯示了如何在 eShopOn 容器中使用 Ocelot 實現 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="de58d-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![顯示 eShopOn 容器體系結構的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="de58d-110">**圖 6-28**。</span><span class="sxs-lookup"><span data-stu-id="de58d-110">**Figure 6-28**.</span></span> <span data-ttu-id="de58d-111">使用 API 閘道的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="de58d-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="de58d-112">該圖顯示了如何將整個應用程式部署到具有"為 Windows 的 Docker"或"Mac 的 Docker"的單個 Docker 主機或開發 PC 中。</span><span class="sxs-lookup"><span data-stu-id="de58d-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="de58d-113">但是，部署到任何協調器都類似，但關係圖中的任何容器都可以在協調器中展開。</span><span class="sxs-lookup"><span data-stu-id="de58d-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="de58d-114">此外，基礎結構資產 (例如資料庫、快取和訊息代理程式) 應該從協調器卸載，並部署到基礎結構的高可用性系統，例如 Azure SQL Database、Azure Cosmos DB、Azure Redis、Azure 服務匯流排或任何內部部署 HA 叢集解決方案。</span><span class="sxs-lookup"><span data-stu-id="de58d-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="de58d-115">正如您在關係圖中也可以注意到的，在開發和部署其微服務以及自己的相關 API 閘道時，擁有多個 API 閘道允許多個開發團隊具有自主性（在本例中，行銷功能與購物功能）。</span><span class="sxs-lookup"><span data-stu-id="de58d-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="de58d-116">如果您有單一整合型 API 閘道，這會是要由多個開發小組更新的單一點，並可結合所有微服務與應用程式的單一組件。</span><span class="sxs-lookup"><span data-stu-id="de58d-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="de58d-117">更進一步設計時，有時也可以根據所選擇的架構，將微調 API 閘道限制為單一商務微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="de58d-118">讓 API 閘道的邊界由業務或域決定，將説明您獲得更好的設計。</span><span class="sxs-lookup"><span data-stu-id="de58d-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="de58d-119">例如，API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="de58d-120">我們有在先前的章節[建立以微服務為基礎的複合 UI](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)中進行更深入的探討。</span><span class="sxs-lookup"><span data-stu-id="de58d-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="de58d-121">其重點在於，針對許多中型和大型應用程式，使用自訂建置的 API 閘道產品通常是不錯的方法，但不能作為單一整合型彙總工具或唯一中央自訂 API 閘道，除非該 API 閘道允許數個開發小組透過多個獨立設定區域建立自發微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="de58d-122">範例微服務/容器透過 API 閘道重設路徑</span><span class="sxs-lookup"><span data-stu-id="de58d-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="de58d-123">例如，eShopOnContainers 大約有六個內部微服務類型必須透過 API 閘道發佈，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![顯示其子資料夾的服務資料夾的螢幕截圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="de58d-125">**圖 6-29**。</span><span class="sxs-lookup"><span data-stu-id="de58d-125">**Figure 6-29**.</span></span> <span data-ttu-id="de58d-126">Visual Studio 之 eShopOnContainers 方案中的微服務資料夾</span><span class="sxs-lookup"><span data-stu-id="de58d-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="de58d-127">關於識別服務，其設計是不包含在 API 閘道路由中，因為它是系統中的唯一跨領域考量，但使用 Ocelot 時，還可能包含它作為重設路徑清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="de58d-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="de58d-128">上述所有服務目前會實作為 ASP.NET Core Web API 服務，如程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="de58d-129">讓我們關注一個微服務，如目錄微服務代碼。</span><span class="sxs-lookup"><span data-stu-id="de58d-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![顯示目錄.API 專案內容的解決方案資源管理器螢幕截圖。](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="de58d-131">**圖 6-30**。</span><span class="sxs-lookup"><span data-stu-id="de58d-131">**Figure 6-30**.</span></span> <span data-ttu-id="de58d-132">範例 Web API 微服務 (目錄微服務)</span><span class="sxs-lookup"><span data-stu-id="de58d-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="de58d-133">如您所見，目錄微服務是一般 ASP.NET Core Web API 專案，其中包含數個控制器和方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="de58d-134">HTTP 要求最終會執行該類型的 C# 程式碼來存取微服務資料庫，並執行任何其他必要動作。</span><span class="sxs-lookup"><span data-stu-id="de58d-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="de58d-135">關於微服務 URL，當容器部署在本地開發 PC（本地 Docker 主機）中時，每個微服務的容器始終具有在其 dockerfile 中指定的內部埠（通常是埠 80），如以下 dockerfile 中：</span><span class="sxs-lookup"><span data-stu-id="de58d-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="de58d-136">程式碼中顯示的連接埠 80 位於 Docker 主機內部，因此用戶端應用程式無法連線到該連接埠。</span><span class="sxs-lookup"><span data-stu-id="de58d-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="de58d-137">用戶端應用程式只能存取使用 `docker-compose` 部署時所發佈的外部連接埠 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="de58d-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="de58d-138">部署到生產環境時，不應該發佈這些外部連接埠。</span><span class="sxs-lookup"><span data-stu-id="de58d-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="de58d-139">這就是為什麼您想要使用 API 閘道來避免用戶端應用程式與微服務之間的直接通訊。</span><span class="sxs-lookup"><span data-stu-id="de58d-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="de58d-140">不過，開發時，您想要直接存取微服務/容器，並透過 Swagger 來執行。</span><span class="sxs-lookup"><span data-stu-id="de58d-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="de58d-141">這就是為什麼在 eShopOn 容器中，即使 API 閘道或用戶端應用不會使用它們，也會指定外部埠。</span><span class="sxs-lookup"><span data-stu-id="de58d-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="de58d-142">下面是目錄微服務`docker-compose.override.yml`的檔示例：</span><span class="sxs-lookup"><span data-stu-id="de58d-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="de58d-143">如您所見，在 docker-compose.override.yml 設定中，目錄容器的內部連接埠是連接埠 80，但外部存取的連接埠是 5101。</span><span class="sxs-lookup"><span data-stu-id="de58d-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="de58d-144">但是，應用程式在使用 API 閘道時不應使用此埠，而只能調試、運行和測試目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="de58d-145">通常，您不會使用 Docker-compose 部署到生產環境中，因為微服務的正確生產部署環境是像 Kubernetes 或服務結構這樣的協調器。</span><span class="sxs-lookup"><span data-stu-id="de58d-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="de58d-146">部署到這些環境時，您使用不同的設定檔，在這些設定檔中，不會直接發佈微服務的任何外部埠，但始終使用 API 閘道的反向代理。</span><span class="sxs-lookup"><span data-stu-id="de58d-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="de58d-147">在本地 Docker 主機中運行目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="de58d-148">要麼從 Visual Studio 運行完整的 eShopOnContainers 解決方案（它運行 Docker-compose 檔中的所有服務），要麼在 CMD 或 PowerShell 中使用以下 docker 組合命令啟動目錄微服務`docker-compose.yml`，`docker-compose.override.yml`該命令位於 放置 和 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="de58d-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="de58d-149">此命令僅運行在 docker-compose.yml 中指定的目錄 api 服務容器以及依賴項。</span><span class="sxs-lookup"><span data-stu-id="de58d-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="de58d-150">在本例中為 SQL Server 容器和 RabbitMQ 容器。</span><span class="sxs-lookup"><span data-stu-id="de58d-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="de58d-151">然後，您可以直接存取目錄微服務，並通過 Swagger UI 直接通過該"外部"埠訪問其方法，在這種情況下`http://localhost:5101/swagger`：</span><span class="sxs-lookup"><span data-stu-id="de58d-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![顯示目錄.API REST API 的斯瓦格 UI 的螢幕截圖。](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="de58d-153">**圖 6-31**。</span><span class="sxs-lookup"><span data-stu-id="de58d-153">**Figure 6-31**.</span></span> <span data-ttu-id="de58d-154">使用其 Swagger UI 測試目錄微服務</span><span class="sxs-lookup"><span data-stu-id="de58d-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="de58d-155">此時，您可以在 Visual Studio 的 C# 程式碼中設定中斷點、使用在 Swagger UI 中公開的方法測試微服務，最後使用 `docker-compose down` 命令清除所有內容。</span><span class="sxs-lookup"><span data-stu-id="de58d-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="de58d-156">不過，建議您在應用程式中避免微服務的直接存取通訊，在本例中是透過外部連接埠 5101。</span><span class="sxs-lookup"><span data-stu-id="de58d-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="de58d-157">您可以設定額外的 API 閘道間接層 (在本例中為 Ocelot) 來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="de58d-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="de58d-158">這樣，用戶端應用將不會直接存取微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="de58d-159">使用 Ocelot 實作您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="de58d-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="de58d-160">Ocelot 基本上是可依特定順序套用的一組中介軟體。</span><span class="sxs-lookup"><span data-stu-id="de58d-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="de58d-161">Ocelot 設計成只能搭配 ASP.NET Core 使用。</span><span class="sxs-lookup"><span data-stu-id="de58d-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="de58d-162">包的最新版本面向目標`.NETCoreApp 3.1`，因此不適合 .NET 框架應用程式。</span><span class="sxs-lookup"><span data-stu-id="de58d-162">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="de58d-163">您可以從 Visual Studio 透過 [Ocelot 的 NuGet 套件](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 專案中安裝 Ocelot 及其相依性。</span><span class="sxs-lookup"><span data-stu-id="de58d-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="de58d-164">在 eShopOn容器中，其 API 閘道實現是一個簡單的ASP.NET核心 WebHost 專案，Ocelot 的中介軟體處理所有 API 閘道功能，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="de58d-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![顯示 Ocelot API 閘道專案的解決方案資源管理器螢幕截圖。](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="de58d-166">**圖 6-32**。</span><span class="sxs-lookup"><span data-stu-id="de58d-166">**Figure 6-32**.</span></span> <span data-ttu-id="de58d-167">eShopOnContainers 中的 OcelotApiGw 基底專案</span><span class="sxs-lookup"><span data-stu-id="de58d-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="de58d-168">此 ASP.NET Core WebHost 專案基本上由兩個簡單的檔案所組成：`Program.cs` 和 `Startup.cs`。</span><span class="sxs-lookup"><span data-stu-id="de58d-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="de58d-169">Program.cs 只需要建立及設定一般 ASP.NET Core BuildWebHost。</span><span class="sxs-lookup"><span data-stu-id="de58d-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="de58d-170">對於 Ocelot 而言，此處的重點是您必須透過 `AddJsonFile()` 方法提供給產生器的 `configuration.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="de58d-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="de58d-171">該 `configuration.json` 是您指定所有 API 閘道重設路徑的位置，表示具有特定連接埠的外部端點及相互關聯的內部端點 (通常使用不同的連接埠)。</span><span class="sxs-lookup"><span data-stu-id="de58d-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="de58d-172">設定分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="de58d-172">There are two sections to the configuration.</span></span> <span data-ttu-id="de58d-173">重新路由和全域配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="de58d-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="de58d-174">ReRoutes 是告訴 Ocelot 如何處理上游請求的物件。</span><span class="sxs-lookup"><span data-stu-id="de58d-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="de58d-175">全域配置允許重寫特定設置。</span><span class="sxs-lookup"><span data-stu-id="de58d-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="de58d-176">如果您不想管理大量重新路由特定設置，則此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="de58d-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="de58d-177">下面是從 eShopOn 容器的 API 閘道之一[重新路由設定檔](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)的簡化示例。</span><span class="sxs-lookup"><span data-stu-id="de58d-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="de58d-178">Ocelot API 閘道的主要功能是接受傳入 HTTP 要求並將其轉送到下游服務 (目前為另一個 HTTP 要求)。</span><span class="sxs-lookup"><span data-stu-id="de58d-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="de58d-179">Ocelot 將一個請求路由到另一個請求描述為"重新路由"。</span><span class="sxs-lookup"><span data-stu-id="de58d-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="de58d-180">例如，讓我們關注配置中的 ReRoutes 之一，即"購物籃"微服務的配置。</span><span class="sxs-lookup"><span data-stu-id="de58d-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="de58d-181">DownstreamPathTemplate、Scheme 和 DownstreamHostAndPorts 會建立此要求將轉送的內部微服務 URL。</span><span class="sxs-lookup"><span data-stu-id="de58d-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="de58d-182">連接埠是服務所使用的內部連接埠。</span><span class="sxs-lookup"><span data-stu-id="de58d-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="de58d-183">使用容器時，連接埠是在其 dockerfile 中指定。</span><span class="sxs-lookup"><span data-stu-id="de58d-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="de58d-184">`Host` 是相依於您使用之服務名稱解析的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="de58d-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="de58d-185">使用 docker-compose 時，服務名稱是由 Docker 主機提供，也就是使用 docker-compose 檔案所提供的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="de58d-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="de58d-186">如果使用 Kubernetes 或 Service Fabric 等協調器，該名稱應該透過 DNS 或每個協調器提供的名稱解析來解析。</span><span class="sxs-lookup"><span data-stu-id="de58d-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="de58d-187">DownstreamHostAndPorts 是包含您想要轉送要求的任何下游服務之主機和連接埠的陣列。</span><span class="sxs-lookup"><span data-stu-id="de58d-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="de58d-188">這通常只會包含一個項目，但有時您可能想要將要求負載平衡至您的下游服務，而 Ocelot 可讓您新增多個項目，然後選取負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="de58d-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="de58d-189">但如果使用 Azure 及任何協調器，最好透過雲端和協調器基礎結構進行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="de58d-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="de58d-190">UpstreamPathTemplate 是 URL，可供 Ocelot 用來識別針對用戶端中的指定要求使用哪個 DownstreamPathTemplate。</span><span class="sxs-lookup"><span data-stu-id="de58d-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="de58d-191">最後，使用 UpstreamHttpMethod，讓 Ocelot 可以區別傳送至相同 URL 的不同要求 (GET、POST、PUT)。</span><span class="sxs-lookup"><span data-stu-id="de58d-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="de58d-192">此時，您可能會有使用一或[多個合併 configuration.json 檔案](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)的單一 Ocelot API 閘道 (ASP.NET Core WebHost)，您也可以[在 Consul KV 存放區中儲存設定](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)。</span><span class="sxs-lookup"><span data-stu-id="de58d-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="de58d-193">但如架構及設計一節所介紹，如果您真的想要有自發微服務，最好將單一整合型 API 閘道分割成多個 API 閘道及/或 BFF (前端的後端)。</span><span class="sxs-lookup"><span data-stu-id="de58d-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="de58d-194">為此，讓我們看看如何使用 Docker 容器實現該方法。</span><span class="sxs-lookup"><span data-stu-id="de58d-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="de58d-195">使用單一 Docker 容器映像執行多個不同的 API 閘道/BFF 容器類型</span><span class="sxs-lookup"><span data-stu-id="de58d-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="de58d-196">在 eShopOn容器中，我們使用 Ocelot API 閘道的單個 Docker 容器映射，但在運行時，我們通過提供不同的配置.json 檔，使用 Docker 卷訪問每個服務的不同 PC 資料夾，為每種類型 API 閘道/BFF 創建不同的服務/容器。</span><span class="sxs-lookup"><span data-stu-id="de58d-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![所有 API 閘道的單個 Ocelot 閘道 Docker 映射圖。](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="de58d-198">**圖 6-33**。</span><span class="sxs-lookup"><span data-stu-id="de58d-198">**Figure 6-33**.</span></span> <span data-ttu-id="de58d-199">在多個 API 閘道類型之間重複使用單一 Ocelot Docker 映像</span><span class="sxs-lookup"><span data-stu-id="de58d-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="de58d-200">在 eShopOn 容器中，使用名為"OcelotApiGw"的專案和在 docker-compose.yml 檔中指定的映射名稱"eshop/ocelotapigw"創建"通用 Ocelot API 閘道 Docker 映射"。</span><span class="sxs-lookup"><span data-stu-id="de58d-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="de58d-201">然後，當部署到 Docker 時，會從該相同的 Docker 映像建立四個 API 閘道容器，如下列 docker-compose.yml 檔案摘錄所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="de58d-202">此外，如您在以下 docker-compose.override.yml 檔案中所見，這些 API 閘道容器之間的唯一差異是 Ocelot 設定檔，每個服務容器會有不同的檔案，而且該檔案會在執行階段透過 Docker 磁碟區指定。</span><span class="sxs-lookup"><span data-stu-id="de58d-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="de58d-203">基於上述程式碼，而且如下面的 Visual Studio 總管所示，定義每個特定業務/BFF API 閘道所需的唯一檔案只有 configuration.json 檔案，因為這四個 API 閘道是以相同的 Docker 映像為依據。</span><span class="sxs-lookup"><span data-stu-id="de58d-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![顯示所有具有配置.json 檔的 API 閘道的螢幕截圖。](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="de58d-205">**圖 6-34**。</span><span class="sxs-lookup"><span data-stu-id="de58d-205">**Figure 6-34**.</span></span> <span data-ttu-id="de58d-206">使用 Ocelot 定義每個 API 閘道/BFF 所需的唯一檔案是設定檔</span><span class="sxs-lookup"><span data-stu-id="de58d-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="de58d-207">將 API 閘道分割成多個 API 閘道之後，著重於不同微服務子集的不同開發小組就可以使用獨立的 Ocelot 設定檔來管理自己的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="de58d-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="de58d-208">此外，他們還可以同時重複使用相同的 Ocelot Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="de58d-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="de58d-209">現在，如果您使用 API 閘道運行 eShopOn 容器（在打開 eShopOnContainers-ServicesAndWebApps.sln 解決方案時預設包含在 VS 中，或者如果運行"docker-compose-up"），將執行以下示例路由。</span><span class="sxs-lookup"><span data-stu-id="de58d-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="de58d-210">例如，瀏覽 webshoppingapigw API 閘道所提供的上游 URL `http://localhost:5202/api/v1/c/catalog/items/2/` 時，您會從 Docker 主機的內部下游 URL `http://catalog-api/api/v1/2` 取得相同結果，如下列瀏覽器所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![顯示通過 API 閘道的回應的瀏覽器螢幕截圖。](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="de58d-212">**圖 6-35**。</span><span class="sxs-lookup"><span data-stu-id="de58d-212">**Figure 6-35**.</span></span> <span data-ttu-id="de58d-213">透過 API 閘道提供的 URL 存取微服務</span><span class="sxs-lookup"><span data-stu-id="de58d-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="de58d-214">由於測試或調試的原因，如果要直接存取目錄 Docker 容器（僅在開發環境中），而無需通過 API 閘道，因為"目錄 api"是 Docker 主機內部的 DNS 解析（由 Docker-compose 服務名稱處理的服務發現），直接存取該容器的唯一方法是通過 Docker-compose.override.yml 中發佈的外部埠，該容器僅提供用於開發測試，例如`http://localhost:5101/api/v1/Catalog/items/1`在以下瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="de58d-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![顯示對目錄的直接回應的瀏覽器螢幕截圖。](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="de58d-216">**圖 6-36**。</span><span class="sxs-lookup"><span data-stu-id="de58d-216">**Figure 6-36**.</span></span> <span data-ttu-id="de58d-217">直接存取微服務以進行測試</span><span class="sxs-lookup"><span data-stu-id="de58d-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="de58d-218">但是，應用程式被配置，所以它通過 API 閘道訪問所有微服務，而不是通過直接埠"快捷方式"。</span><span class="sxs-lookup"><span data-stu-id="de58d-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="de58d-219">eShopOnContainers 中的閘道彙總模式</span><span class="sxs-lookup"><span data-stu-id="de58d-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="de58d-220">如前所介紹，實作要求彙總的一個彈性方法，就是透過程式碼使用自訂服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="de58d-221">您也可以使用 [Ocelot 中的 Request Aggregation](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation) (要求彙總) 功能來實作要求彙總，但其彈性可能不符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="de58d-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="de58d-222">因此，在 eShopOn容器中實現聚合的選定方法是為每個聚合器提供顯式ASP.NET核心 Web API 服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="de58d-223">根據該方法，考量到上述簡化全域架構圖中未顯示的彙總工具服務，API 閘道組合圖實際上會涵蓋更大範圍。</span><span class="sxs-lookup"><span data-stu-id="de58d-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="de58d-224">在下圖中，您也可以查看彙總工具服務如何搭配其相關 API 閘道使用。</span><span class="sxs-lookup"><span data-stu-id="de58d-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![顯示聚合器服務的 eShopOn 容器體系結構圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="de58d-226">**圖 6-37**。</span><span class="sxs-lookup"><span data-stu-id="de58d-226">**Figure 6-37**.</span></span> <span data-ttu-id="de58d-227">使用彙總工具服務的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="de58d-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="de58d-228">在下圖中的"購物"業務區域上進一步放大，您可以看到，在 API 閘道中使用聚合器服務時，用戶端應用和微服務之間的聊天量會減少。</span><span class="sxs-lookup"><span data-stu-id="de58d-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![顯示 eShopOn 容器體系結構放大的圖表。](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="de58d-230">**圖 6-38**。</span><span class="sxs-lookup"><span data-stu-id="de58d-230">**Figure 6-38**.</span></span> <span data-ttu-id="de58d-231">放大檢視彙總工具服務</span><span class="sxs-lookup"><span data-stu-id="de58d-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="de58d-232">您可以注意到當關係圖顯示來自 API 閘道的可能請求時，它可能會變得複雜。</span><span class="sxs-lookup"><span data-stu-id="de58d-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="de58d-233">雖然您可以看到藍色箭號如何簡化，但從用戶端應用程式觀點來看，當使用彙總工具模式時，若能減少通訊中的頻繁交談和延遲，最終特別會大幅改善遠端應用程式 (行動和 SPA 應用程式) 的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="de58d-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="de58d-234">對於"行銷"業務領域和微服務，這是一個簡單的用例，因此無需使用聚合器，但如果需要，也可以使用聚合器。</span><span class="sxs-lookup"><span data-stu-id="de58d-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="de58d-235">Ocelot API 閘道中的驗證與授權</span><span class="sxs-lookup"><span data-stu-id="de58d-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="de58d-236">在 Ocelot API 閘道中，您可以將驗證服務 (例如使用 [IdentityServer](https://identityserver.io/) 提供驗證權杖的 ASP.NET Core Web API 服務) 放在 API 閘道外部或內部。</span><span class="sxs-lookup"><span data-stu-id="de58d-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="de58d-237">由於 eShopOnContainers 使用多個具有依據 BFF 和業務領域之界限的 API 閘道，因此識別/驗證服務不會包含在 API 閘道中 (在下圖中以黃色醒目提示)。</span><span class="sxs-lookup"><span data-stu-id="de58d-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![顯示 API 閘道下方的標識微服務圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="de58d-239">**圖 6-39**。</span><span class="sxs-lookup"><span data-stu-id="de58d-239">**Figure 6-39**.</span></span> <span data-ttu-id="de58d-240">識別服務在 eShopOnContainers 中的位置</span><span class="sxs-lookup"><span data-stu-id="de58d-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="de58d-241">不過，Ocelot 也支援將識別/驗證微服務放在 API 閘道界限內，如下面另一個圖所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![顯示 Ocelot API 閘道中身份驗證的圖表。](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="de58d-243">**圖 6-40**。</span><span class="sxs-lookup"><span data-stu-id="de58d-243">**Figure 6-40**.</span></span> <span data-ttu-id="de58d-244">Ocelot 的驗證</span><span class="sxs-lookup"><span data-stu-id="de58d-244">Authentication in Ocelot</span></span>

<span data-ttu-id="de58d-245">如上圖所示，當標識微服務位於 API 閘道 （AG） 下方時：1） AG 從標識微服務請求身份驗證權杖時，2） 標識微服務使用身份驗證權杖將權杖返回 AG，3-4） 使用 auth 權杖從微服務請求。</span><span class="sxs-lookup"><span data-stu-id="de58d-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="de58d-246">由於 eShopOn 容器應用程式將 API 閘道拆分為多個 BFF（前端後端）和業務區域 API 閘道，因此另一個選項是創建一個額外的 API 閘道，以便解決跨領域問題。</span><span class="sxs-lookup"><span data-stu-id="de58d-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="de58d-247">該選擇相當適合具有多個跨領域考量微服務的更複雜微服務型架構。</span><span class="sxs-lookup"><span data-stu-id="de58d-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="de58d-248">由於 eShopOnContainers 中只有一個貫穿各領域的問題，因此出於簡單起見，決定只處理 API 閘道領域之外的安全服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="de58d-249">在任何情況下，如果在 API 閘道層級保護應用程式，當嘗試使用任何受保護的微服務時，會先瀏覽 Ocelot API 閘道的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="de58d-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="de58d-250">這重定向了 HTTP 要求以訪問標識或身份驗證微服務以獲取訪問權杖，以便您可以使用access_token訪問受保護的服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="de58d-251">您在 API 閘道層級使用驗證保護任何服務的方式，就是在 configuration.json 中設定其相關設定的 AuthenticationProviderKey。</span><span class="sxs-lookup"><span data-stu-id="de58d-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="de58d-252">當 Ocelot 運行時，它將查看重新路由身份驗證選項.身份檢查器提供者金鑰，並檢查是否有使用給定金鑰註冊的身份檢查器提供者。</span><span class="sxs-lookup"><span data-stu-id="de58d-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="de58d-253">如果沒有，則 Ocelot 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="de58d-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="de58d-254">如果有，則重設路徑將會在執行時使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="de58d-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="de58d-255">由於 Ocelot WebHost 是使用 `authenticationProviderKey = "IdentityApiKey"` 設定，因此只要服務有任何要求沒有任何驗證權杖，就需要驗證。</span><span class="sxs-lookup"><span data-stu-id="de58d-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="de58d-256">然後，您也需要在任何要存取的資源 (例如微服務) 上透過 [Authorize] 屬性設定授權，例如在下列購物籃微服務控制器中。</span><span class="sxs-lookup"><span data-stu-id="de58d-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="de58d-257">"購物籃"等有效訪問群體與"啟動"類的"佈建服務（）"`AddJwtBearer()`中在每個微服務中定義的訪問群體相關，如下面的代碼。</span><span class="sxs-lookup"><span data-stu-id="de58d-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="de58d-258">如果您嘗試訪問任何安全的微服務，如基於 API 閘道的`http://localhost:5202/api/v1/b/basket/1`ReRoute URL 的購物籃微服務，則除非提供有效的權杖，否則您將獲得 401 未經授權的服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="de58d-259">另一方面，如果 ReRoute URL 已過身份驗證，Ocelot 將調用與其關聯的任何下游方案（內部微服務 URL）。</span><span class="sxs-lookup"><span data-stu-id="de58d-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="de58d-260">**在 Ocelot 的 ReRoutes 層授權。**</span><span class="sxs-lookup"><span data-stu-id="de58d-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="de58d-261">Ocelot 支援在驗證後評估宣告式授權。</span><span class="sxs-lookup"><span data-stu-id="de58d-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="de58d-262">您可以透過將下列程式行新增至 ReRoute 組態，在路由層級設定授權。</span><span class="sxs-lookup"><span data-stu-id="de58d-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="de58d-263">在該範例中，當呼叫授權中介軟體時，Ocelot 會查明使用者在權杖中是否有宣告類型 'UserType'，以及該宣告的值是否為 'employee'。</span><span class="sxs-lookup"><span data-stu-id="de58d-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="de58d-264">如果不是，則使用者將不獲得授權，並且將禁止回應 403。</span><span class="sxs-lookup"><span data-stu-id="de58d-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="de58d-265">使用 Kubernetes 輸入加上 Ocelot API 閘道</span><span class="sxs-lookup"><span data-stu-id="de58d-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="de58d-266">使用庫伯奈斯（如在 Azure 庫伯內斯服務群集中）時，通常基於*Nginx*通過[庫貝內斯入口層](https://kubernetes.io/docs/concepts/services-networking/ingress/)統一所有 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="de58d-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="de58d-267">在 Kubernetes 中，如果不使用任何入口方法，則服務和窗格的 IP 只能由群集網路路由。</span><span class="sxs-lookup"><span data-stu-id="de58d-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="de58d-268">但如果您使用輸入方法，您就會在網際網路與服務 (包括 API 閘道) 之間有一個中介層作為反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="de58d-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="de58d-269">按照定義，輸入是允許輸入連線到達叢集服務的規則集合。</span><span class="sxs-lookup"><span data-stu-id="de58d-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="de58d-270">輸入通常會設定為提供服務可從外部連線的 URL、負載平衡流量、SSL 終止等項目。</span><span class="sxs-lookup"><span data-stu-id="de58d-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="de58d-271">使用者透過將輸入資源張貼到 API 伺服器來要求輸入。</span><span class="sxs-lookup"><span data-stu-id="de58d-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="de58d-272">在 eShopOnContainers 中，當您在本機開發並只使用您的開發電腦作為 Docker 主機時，您不會使用任何輸入，而只會使用多個 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="de58d-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="de58d-273">但是，當針對基於 Kubernetes 的"生產"環境時，eShopOnContainers 正在 API 閘道前使用入口。</span><span class="sxs-lookup"><span data-stu-id="de58d-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="de58d-274">如此一來，用戶端仍會呼叫相同的基底 URL，但要求會路由至多個 API 閘道或 BFF。</span><span class="sxs-lookup"><span data-stu-id="de58d-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="de58d-275">API 閘道是前端或立面，僅顯示服務，而不是通常不在其範圍範圍內的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="de58d-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="de58d-276">此外，API 閘道可能會隱藏特定內部微服務。</span><span class="sxs-lookup"><span data-stu-id="de58d-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="de58d-277">不過，輸入只會重新導向 HTTP，而不會嘗試隱藏任何微服務或 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="de58d-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="de58d-278">在 Web 應用程式前端的 Kubernetes 中有一個輸入 Nginx 層加上數個 Ocelot API 閘道/BFF 是理想的架構，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de58d-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![顯示入口層如何適應 AKS 環境的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="de58d-280">**圖 6-41**。</span><span class="sxs-lookup"><span data-stu-id="de58d-280">**Figure 6-41**.</span></span> <span data-ttu-id="de58d-281">部署至 Kubernetes 時之 eShopOnContainers 中的輸入層</span><span class="sxs-lookup"><span data-stu-id="de58d-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="de58d-282">Kubernetes 輸入扮演著所有對應用程式流量的反向 Proxy 角色，其中包括通常不在 API 閘道範圍內的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="de58d-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="de58d-283">當您將 eShopOnContainers 部署到 Kubernetes 時，它只會透過「輸入」__ 公開一些服務或端點，基本上包括 URL 上的下列後置詞清單：</span><span class="sxs-lookup"><span data-stu-id="de58d-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="de58d-284">`/` 代表用戶端 SPA Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="de58d-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="de58d-285">`/webmvc` 代表用戶端 MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="de58d-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="de58d-286">`/webstatus` 代表顯示狀態/健康狀態檢查的用戶端 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="de58d-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="de58d-287">`/webshoppingapigw` 代表 Web BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="de58d-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="de58d-288">`/webmarketingapigw` 代表 Web BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="de58d-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="de58d-289">`/mobileshoppingapigw` 代表行動 BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="de58d-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="de58d-290">`/mobilemarketingapigw` 代表行動 BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="de58d-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="de58d-291">部署到 Kubernetes 時，每個 Ocelot API 閘道對運行 API 閘道的每個_Pod_使用不同的"配置.json"檔。</span><span class="sxs-lookup"><span data-stu-id="de58d-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="de58d-292">這些"配置.json"檔是通過安裝（最初使用 Deploy.ps1 腳本）基於名為"ocelot"的 Kubernetes_配置映射_創建的卷來提供的。</span><span class="sxs-lookup"><span data-stu-id="de58d-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="de58d-293">每個容器都將其相關設定檔裝載到名為`/app/configuration`的容器檔案夾中。</span><span class="sxs-lookup"><span data-stu-id="de58d-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="de58d-294">在 eShopOnContainers 的原始程式碼檔中，可以在`k8s/ocelot/`資料夾中找到原始的"配置.json"檔。</span><span class="sxs-lookup"><span data-stu-id="de58d-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="de58d-295">每個 BFF/APIGateway 都有一個檔。</span><span class="sxs-lookup"><span data-stu-id="de58d-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="de58d-296">Ocelot API 閘道中的其他跨領域功能</span><span class="sxs-lookup"><span data-stu-id="de58d-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="de58d-297">使用 Ocelot API 閘道時，還有其他重要的功能可供探索及使用，下列連結將進行說明。</span><span class="sxs-lookup"><span data-stu-id="de58d-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="de58d-298">**客戶方的服務發現 將 Ocelot 與領事或尤里卡整合** </span><span class="sxs-lookup"><span data-stu-id="de58d-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="de58d-299">**在 API 閘道層緩存** </span><span class="sxs-lookup"><span data-stu-id="de58d-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="de58d-300">**在 API 閘道層登錄** </span><span class="sxs-lookup"><span data-stu-id="de58d-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="de58d-301">**API 閘道層的服務品質（重試和斷路器）** </span><span class="sxs-lookup"><span data-stu-id="de58d-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="de58d-302">**速率限制** </span><span class="sxs-lookup"><span data-stu-id="de58d-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="de58d-303">[上一個](background-tasks-with-ihostedservice.md)
> [下一個](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="de58d-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
