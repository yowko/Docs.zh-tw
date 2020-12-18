---
title: 使用 Ocelot 實作 API 閘道
description: 了解如何使用 Ocelot 實作 API 閘道，並了解如何在以容器為基礎的環境中使用 Ocelot。
ms.date: 03/02/2020
ms.openlocfilehash: 5da8533eff394b587d123970742727484a7236ad
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678118"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="cab1b-103">使用 Ocelot 實作 API 閘道</span><span class="sxs-lookup"><span data-stu-id="cab1b-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cab1b-104">參考微服務應用程式 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 目前使用 [Envoy](https://www.envoyproxy.io/) 所提供的功能來執行 API 閘道，而不是先前參考的 [Ocelot](https://github.com/ThreeMammals/Ocelot)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="cab1b-105">由於 Envoy 的內建支援 WebSocket 通訊協定，因此我們選擇了這種設計，這是在 eShopOnContainers 中執行的新 gRPC 服務間通訊所需。</span><span class="sxs-lookup"><span data-stu-id="cab1b-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="cab1b-106">不過，我們已在本指南中保留本節，讓您可以將 Ocelot 視為適合生產等級案例的簡單、功能和輕量 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="cab1b-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>
> <span data-ttu-id="cab1b-107">此外，最新的 Ocelot 版本也包含其 json 架構的重大變更。</span><span class="sxs-lookup"><span data-stu-id="cab1b-107">Also, latest Ocelot version contains a breaking change on its json schema.</span></span> <span data-ttu-id="cab1b-108">請考慮使用 Ocelot < v 16.0.0 版，或使用金鑰路由而非 route。</span><span class="sxs-lookup"><span data-stu-id="cab1b-108">Consider using Ocelot < v16.0.0, or use the key Routes instead of ReRoutes.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="cab1b-109">架構及設計您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="cab1b-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="cab1b-110">下列架構圖說明如何在 eShopOnContainers 中使用 Ocelot 來執行 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="cab1b-110">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![顯示 eShopOnContainers 架構的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="cab1b-112">**圖 6-28**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-112">**Figure 6-28**.</span></span> <span data-ttu-id="cab1b-113">使用 API 閘道的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="cab1b-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="cab1b-114">該圖表顯示如何將整個應用程式部署到具有 "適用於 Windows 的 Docker" 或 "Docker for Mac" 的單一 Docker 主機或開發電腦上。</span><span class="sxs-lookup"><span data-stu-id="cab1b-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="cab1b-115">不過，部署到任何 orchestrator 會很類似，但您可以在協調器中相應放大圖表中的任何容器。</span><span class="sxs-lookup"><span data-stu-id="cab1b-115">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="cab1b-116">此外，基礎結構資產 (例如資料庫、快取和訊息代理程式) 應該從協調器卸載，並部署到基礎結構的高可用性系統，例如 Azure SQL Database、Azure Cosmos DB、Azure Redis、Azure 服務匯流排或任何內部部署 HA 叢集解決方案。</span><span class="sxs-lookup"><span data-stu-id="cab1b-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="cab1b-117">您也可以在圖表中發現，有數個 API 閘道可讓多個開發小組成為自發 (在此案例中，行銷功能與購物功能) 在開發和部署微服務時，以及自己的相關 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="cab1b-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="cab1b-118">如果您有單一整合型 API 閘道，這會是要由多個開發小組更新的單一點，並可結合所有微服務與應用程式的單一組件。</span><span class="sxs-lookup"><span data-stu-id="cab1b-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="cab1b-119">更進一步設計時，有時也可以根據所選擇的架構，將微調 API 閘道限制為單一商務微服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="cab1b-120">擁有企業或網域所規定的 API 閘道界限，將可協助您取得更好的設計。</span><span class="sxs-lookup"><span data-stu-id="cab1b-120">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="cab1b-121">例如，API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="cab1b-122">我們有在先前的章節[建立以微服務為基礎的複合 UI](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)中進行更深入的探討。</span><span class="sxs-lookup"><span data-stu-id="cab1b-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="cab1b-123">作為關鍵重點，對於許多中型和大型應用程式而言，使用自訂的 API 閘道產品通常是很好的方法，而不是單一整合型匯總工具或唯一的中央自訂 API 閘道，除非該 API 閘道允許數個開發小組建立自發微服務的多個獨立設定區域。</span><span class="sxs-lookup"><span data-stu-id="cab1b-123">As a key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="cab1b-124">範例微服務/容器透過 API 閘道重設路徑</span><span class="sxs-lookup"><span data-stu-id="cab1b-124">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="cab1b-125">例如，eShopOnContainers 大約有六個內部微服務類型必須透過 API 閘道發佈，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![顯示其子資料夾的 [服務] 資料夾的螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="cab1b-127">**圖 6-29**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-127">**Figure 6-29**.</span></span> <span data-ttu-id="cab1b-128">Visual Studio 之 eShopOnContainers 方案中的微服務資料夾</span><span class="sxs-lookup"><span data-stu-id="cab1b-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="cab1b-129">關於識別服務，其設計是不包含在 API 閘道路由中，因為它是系統中的唯一跨領域考量，但使用 Ocelot 時，還可能包含它作為重設路徑清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="cab1b-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="cab1b-130">上述所有服務目前會實作為 ASP.NET Core Web API 服務，如程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="cab1b-131">讓我們將焦點放在其中一個微服務，例如目錄微服務程式代碼。</span><span class="sxs-lookup"><span data-stu-id="cab1b-131">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![顯示 Catalog. API 專案內容方案總管的螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="cab1b-133">**圖 6-30**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-133">**Figure 6-30**.</span></span> <span data-ttu-id="cab1b-134">範例 Web API 微服務 (目錄微服務)</span><span class="sxs-lookup"><span data-stu-id="cab1b-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="cab1b-135">如您所見，目錄微服務是一般 ASP.NET Core Web API 專案，其中包含數個控制器和方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="cab1b-136">HTTP 要求最終會執行該類型的 C# 程式碼來存取微服務資料庫，並執行任何其他必要動作。</span><span class="sxs-lookup"><span data-stu-id="cab1b-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="cab1b-137">關於微服務 URL，當容器部署在您的本機開發電腦 (本機 Docker 主機) 時，每個微服務的容器一律會有內部埠 (通常會在其 dockerfile 中指定埠 80) ，如下列 dockerfile 所示：</span><span class="sxs-lookup"><span data-stu-id="cab1b-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container always has an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="cab1b-138">程式碼中顯示的連接埠 80 位於 Docker 主機內部，因此用戶端應用程式無法連線到該連接埠。</span><span class="sxs-lookup"><span data-stu-id="cab1b-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="cab1b-139">用戶端應用程式只能存取使用 `docker-compose` 部署時所發佈的外部連接埠 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="cab1b-140">部署到生產環境時，不應該發佈這些外部連接埠。</span><span class="sxs-lookup"><span data-stu-id="cab1b-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="cab1b-141">基於這個特殊原因，為什麼您想要使用 API 閘道，以避免用戶端應用程式與微服務之間的直接通訊。</span><span class="sxs-lookup"><span data-stu-id="cab1b-141">For this specific reason, why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="cab1b-142">不過，開發時，您想要直接存取微服務/容器，並透過 Swagger 來執行。</span><span class="sxs-lookup"><span data-stu-id="cab1b-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="cab1b-143">這就是為什麼在 eShopOnContainers 中，即使 API 閘道或用戶端應用程式不會使用外部埠，仍會指定外部埠。</span><span class="sxs-lookup"><span data-stu-id="cab1b-143">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="cab1b-144">以下是目錄微服務檔案的範例 `docker-compose.override.yml` ：</span><span class="sxs-lookup"><span data-stu-id="cab1b-144">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

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

<span data-ttu-id="cab1b-145">如您所見，在 docker-compose.override.yml 設定中，目錄容器的內部連接埠是連接埠 80，但外部存取的連接埠是 5101。</span><span class="sxs-lookup"><span data-stu-id="cab1b-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="cab1b-146">但應用程式在使用 API 閘道時，不應使用此埠，只是要對目錄微服務進行僅限錯、執行和測試。</span><span class="sxs-lookup"><span data-stu-id="cab1b-146">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="cab1b-147">一般來說，您不會在生產環境中進行部署，因為適用于微服務的正確生產部署環境是協調器，例如 Kubernetes 或 Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="cab1b-147">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="cab1b-148">部署至這些環境時，您會使用不同的設定檔，而不會直接發佈微服務的任何外部埠，但您一律會從 API 閘道使用反向 proxy。</span><span class="sxs-lookup"><span data-stu-id="cab1b-148">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="cab1b-149">在本機 Docker 主機中執行目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-149">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="cab1b-150">從 Visual Studio 執行完整的 eShopOnContainers 解決方案， (它會執行 docker 組成檔案中的所有服務) ，或使用下列位於和放置所在資料夾的 CMD 或 PowerShell 中的下列 docker 撰寫命令，啟動目錄微服務 `docker-compose.yml` `docker-compose.override.yml` 。</span><span class="sxs-lookup"><span data-stu-id="cab1b-150">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="cab1b-151">此命令只會執行目錄 api 服務容器，再加上在 >docker-compose.yml. yml 中指定的相依性。</span><span class="sxs-lookup"><span data-stu-id="cab1b-151">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="cab1b-152">在本例中為 SQL Server 容器和 RabbitMQ 容器。</span><span class="sxs-lookup"><span data-stu-id="cab1b-152">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="cab1b-153">然後，您可以直接存取目錄微服務，並透過直接透過該「外部」埠存取的 Swagger UI 查看其方法，在此情況下 `http://localhost:5101/swagger` ：</span><span class="sxs-lookup"><span data-stu-id="cab1b-153">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Swagger UI 的螢幕擷取畫面，其中顯示 Catalog. API REST API。](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="cab1b-155">**圖 6-31**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-155">**Figure 6-31**.</span></span> <span data-ttu-id="cab1b-156">使用其 Swagger UI 測試目錄微服務</span><span class="sxs-lookup"><span data-stu-id="cab1b-156">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="cab1b-157">此時，您可以在 Visual Studio 的 C# 程式碼中設定中斷點、使用在 Swagger UI 中公開的方法測試微服務，最後使用 `docker-compose down` 命令清除所有內容。</span><span class="sxs-lookup"><span data-stu-id="cab1b-157">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="cab1b-158">不過，建議您在應用程式中避免微服務的直接存取通訊，在本例中是透過外部連接埠 5101。</span><span class="sxs-lookup"><span data-stu-id="cab1b-158">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="cab1b-159">您可以設定額外的 API 閘道間接層 (在本例中為 Ocelot) 來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="cab1b-159">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="cab1b-160">如此一來，用戶端應用程式就不會直接存取微服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-160">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="cab1b-161">使用 Ocelot 實作您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="cab1b-161">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="cab1b-162">Ocelot 基本上是可依特定順序套用的一組中介軟體。</span><span class="sxs-lookup"><span data-stu-id="cab1b-162">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="cab1b-163">Ocelot 設計成只能搭配 ASP.NET Core 使用。</span><span class="sxs-lookup"><span data-stu-id="cab1b-163">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="cab1b-164">封裝的最新版本 `.NETCoreApp 3.1` ，因此不適合 .NET Framework 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cab1b-164">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="cab1b-165">您可以從 Visual Studio 透過 [Ocelot 的 NuGet 套件](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 專案中安裝 Ocelot 及其相依性。</span><span class="sxs-lookup"><span data-stu-id="cab1b-165">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="cab1b-166">在 eShopOnContainers 中，其 API 閘道的執行是簡單的 ASP.NET Core WebHost 專案，而 Ocelot 的中介軟體會處理所有 API 閘道功能，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="cab1b-166">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![顯示 Ocelot API 閘道專案方案總管的螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="cab1b-168">**圖 6-32**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-168">**Figure 6-32**.</span></span> <span data-ttu-id="cab1b-169">eShopOnContainers 中的 OcelotApiGw 基底專案</span><span class="sxs-lookup"><span data-stu-id="cab1b-169">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="cab1b-170">此 ASP.NET Core WebHost 專案是以兩個簡單的檔案建立：  `Program.cs` 和 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="cab1b-170">This ASP.NET Core WebHost project is built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="cab1b-171">Program.cs 只需要建立及設定一般 ASP.NET Core BuildWebHost。</span><span class="sxs-lookup"><span data-stu-id="cab1b-171">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="cab1b-172">對於 Ocelot 而言，此處的重點是您必須透過 `AddJsonFile()` 方法提供給產生器的 `configuration.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="cab1b-172">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="cab1b-173">該 `configuration.json` 是您指定所有 API 閘道重設路徑的位置，表示具有特定連接埠的外部端點及相互關聯的內部端點 (通常使用不同的連接埠)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-173">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="cab1b-174">設定分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="cab1b-174">There are two sections to the configuration.</span></span> <span data-ttu-id="cab1b-175">重置和 GlobalConfiguration 的陣列。</span><span class="sxs-lookup"><span data-stu-id="cab1b-175">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="cab1b-176">重做是告訴 Ocelot 如何處理上游要求的物件。</span><span class="sxs-lookup"><span data-stu-id="cab1b-176">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="cab1b-177">全域設定允許覆寫重新路由的特定設定。</span><span class="sxs-lookup"><span data-stu-id="cab1b-177">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="cab1b-178">如果您不想要管理許多重新路由的特定設定，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="cab1b-178">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="cab1b-179">以下是從 eShopOnContainers 中的其中一個 API 閘道重新 [路由設定檔](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) 的簡化範例。</span><span class="sxs-lookup"><span data-stu-id="cab1b-179">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

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

<span data-ttu-id="cab1b-180">Ocelot API 閘道的主要功能是接受傳入 HTTP 要求並將其轉送到下游服務 (目前為另一個 HTTP 要求)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-180">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="cab1b-181">Ocelot 描述將某個要求路由傳送至另一個做為重新路由的要求。</span><span class="sxs-lookup"><span data-stu-id="cab1b-181">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="cab1b-182">例如，讓我們將焦點放在上述 configuration.js中的其中一個重做，這是購物籃微服務的設定。</span><span class="sxs-lookup"><span data-stu-id="cab1b-182">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

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

<span data-ttu-id="cab1b-183">DownstreamPathTemplate、Scheme 和 DownstreamHostAndPorts 會建立此要求將轉送的內部微服務 URL。</span><span class="sxs-lookup"><span data-stu-id="cab1b-183">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="cab1b-184">連接埠是服務所使用的內部連接埠。</span><span class="sxs-lookup"><span data-stu-id="cab1b-184">The port is the internal port used by the service.</span></span> <span data-ttu-id="cab1b-185">使用容器時，連接埠是在其 dockerfile 中指定。</span><span class="sxs-lookup"><span data-stu-id="cab1b-185">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="cab1b-186">`Host` 是相依於您使用之服務名稱解析的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="cab1b-186">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="cab1b-187">使用 docker-compose 時，服務名稱是由 Docker 主機提供，也就是使用 docker-compose 檔案所提供的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="cab1b-187">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="cab1b-188">如果使用 Kubernetes 或 Service Fabric 等協調器，該名稱應該透過 DNS 或每個協調器提供的名稱解析來解析。</span><span class="sxs-lookup"><span data-stu-id="cab1b-188">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="cab1b-189">DownstreamHostAndPorts 是包含您想要轉送要求的任何下游服務之主機和連接埠的陣列。</span><span class="sxs-lookup"><span data-stu-id="cab1b-189">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="cab1b-190">這項設定通常只會包含一個專案，但有時候您可能會想要對下游服務的要求進行負載平衡，而 Ocelot 可讓您新增多個專案，然後選取負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="cab1b-190">Usually this configuration will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="cab1b-191">但如果使用 Azure 及任何協調器，最好透過雲端和協調器基礎結構進行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="cab1b-191">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="cab1b-192">UpstreamPathTemplate 是 URL，可供 Ocelot 用來識別針對用戶端中的指定要求使用哪個 DownstreamPathTemplate。</span><span class="sxs-lookup"><span data-stu-id="cab1b-192">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="cab1b-193">最後，使用 UpstreamHttpMethod，讓 Ocelot 可以區別傳送至相同 URL 的不同要求 (GET、POST、PUT)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-193">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="cab1b-194">此時，您可能會有使用一或[多個合併 configuration.json 檔案](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)的單一 Ocelot API 閘道 (ASP.NET Core WebHost)，您也可以[在 Consul KV 存放區中儲存設定](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-194">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="cab1b-195">但如架構及設計一節所介紹，如果您真的想要有自發微服務，最好將單一整合型 API 閘道分割成多個 API 閘道及/或 BFF (前端的後端)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-195">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="cab1b-196">基於這個目的，讓我們來看看如何使用 Docker 容器來執行該方法。</span><span class="sxs-lookup"><span data-stu-id="cab1b-196">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="cab1b-197">使用單一 Docker 容器映像執行多個不同的 API 閘道/BFF 容器類型</span><span class="sxs-lookup"><span data-stu-id="cab1b-197">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="cab1b-198">在 eShopOnContainers 中，我們會使用單一 Docker 容器映射搭配 Ocelot API 閘道，但在執行時間，我們會為每個類型的 API-閘道/BFF 建立不同的服務/容器，configuration.js方法是使用 Docker 磁片區來存取每個服務的不同電腦資料夾。</span><span class="sxs-lookup"><span data-stu-id="cab1b-198">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![適用于所有 API 閘道的單一 Ocelot 閘道 Docker 映射圖表。](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="cab1b-200">**圖 6-33**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-200">**Figure 6-33**.</span></span> <span data-ttu-id="cab1b-201">在多個 API 閘道類型之間重複使用單一 Ocelot Docker 映像</span><span class="sxs-lookup"><span data-stu-id="cab1b-201">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="cab1b-202">在 eShopOnContainers 中，會使用名為 ' OcelotApiGw ' 的專案和 OcelotApiGw. >docker-compose.yml 檔案中指定的映射名稱 "eshop/yml" 來建立「一般 Ocelot API 閘道 Docker 映射」。</span><span class="sxs-lookup"><span data-stu-id="cab1b-202">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="cab1b-203">然後，當部署到 Docker 時，會從該相同的 Docker 映像建立四個 API 閘道容器，如下列 docker-compose.yml 檔案摘錄所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-203">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="cab1b-204">此外，如您在以下 docker-compose.override.yml 檔案中所見，這些 API 閘道容器之間的唯一差異是 Ocelot 設定檔，每個服務容器會有不同的檔案，而且該檔案會在執行階段透過 Docker 磁碟區指定。</span><span class="sxs-lookup"><span data-stu-id="cab1b-204">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

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

<span data-ttu-id="cab1b-205">基於上述程式碼，而且如下面的 Visual Studio 總管所示，定義每個特定業務/BFF API 閘道所需的唯一檔案只有 configuration.json 檔案，因為這四個 API 閘道是以相同的 Docker 映像為依據。</span><span class="sxs-lookup"><span data-stu-id="cab1b-205">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![螢幕擷取畫面，顯示檔案中包含 configuration.js的所有 API 閘道。](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="cab1b-207">**圖 6-34**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-207">**Figure 6-34**.</span></span> <span data-ttu-id="cab1b-208">使用 Ocelot 定義每個 API 閘道/BFF 所需的唯一檔案是設定檔</span><span class="sxs-lookup"><span data-stu-id="cab1b-208">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="cab1b-209">將 API 閘道分割成多個 API 閘道之後，著重於不同微服務子集的不同開發小組就可以使用獨立的 Ocelot 設定檔來管理自己的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="cab1b-209">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="cab1b-210">此外，他們還可以同時重複使用相同的 Ocelot Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="cab1b-210">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="cab1b-211">現在，如果您使用 API 網 (關執行 eShopOnContainers，則在開啟 eShopOnContainers-ServicesAndWebApps .sln 解決方案時，預設會包含在 VS 中，或者，如果執行 "docker-編寫 up" ) ，將會執行下列範例路由。</span><span class="sxs-lookup"><span data-stu-id="cab1b-211">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="cab1b-212">例如，瀏覽 webshoppingapigw API 閘道所提供的上游 URL `http://localhost:5202/api/v1/c/catalog/items/2/` 時，您會從 Docker 主機的內部下游 URL `http://catalog-api/api/v1/2` 取得相同結果，如下列瀏覽器所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-212">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![瀏覽器的螢幕擷取畫面，其中顯示透過 API 閘道的回應。](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="cab1b-214">**圖 6-35**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-214">**Figure 6-35**.</span></span> <span data-ttu-id="cab1b-215">透過 API 閘道提供的 URL 存取微服務</span><span class="sxs-lookup"><span data-stu-id="cab1b-215">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="cab1b-216">由於測試或偵測的原因，如果您只想要在開發環境中直接存取目錄 Docker 容器 (，) 而不是透過 API 閘道進行傳遞，因為 ' Catalog-API ' 是 docker 主機內部的 DNS 解析 (服務探索是由 docker 組成的服務名稱) ，直接存取容器的唯一方法是透過 >docker-compose.yml 中發佈的外部埠（僅針對開發測試提供，例如 `http://localhost:5101/api/v1/Catalog/items/1` 在下列瀏覽器中提供）。</span><span class="sxs-lookup"><span data-stu-id="cab1b-216">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![瀏覽器的螢幕擷取畫面，其中顯示目錄 api 的直接回應。](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="cab1b-218">**圖 6-36**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-218">**Figure 6-36**.</span></span> <span data-ttu-id="cab1b-219">直接存取微服務以進行測試</span><span class="sxs-lookup"><span data-stu-id="cab1b-219">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="cab1b-220">但會設定應用程式，讓它透過 API 閘道存取所有微服務，而不是透過直接埠「快捷方式」。</span><span class="sxs-lookup"><span data-stu-id="cab1b-220">But the application is configured so it accesses all the microservices through the API Gateways, not through the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="cab1b-221">eShopOnContainers 中的閘道彙總模式</span><span class="sxs-lookup"><span data-stu-id="cab1b-221">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="cab1b-222">如前所介紹，實作要求彙總的一個彈性方法，就是透過程式碼使用自訂服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-222">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="cab1b-223">您也可以使用 [Ocelot 中的 Request Aggregation](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation) (要求彙總) 功能來實作要求彙總，但其彈性可能不符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="cab1b-223">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="cab1b-224">因此，在 eShopOnContainers 中執行匯總的選取方式，是針對每個匯總工具使用明確 ASP.NET Core Web API 服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-224">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="cab1b-225">根據該方法，考量到上述簡化全域架構圖中未顯示的彙總工具服務，API 閘道組合圖實際上會涵蓋更大範圍。</span><span class="sxs-lookup"><span data-stu-id="cab1b-225">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="cab1b-226">在下圖中，您也可以查看彙總工具服務如何搭配其相關 API 閘道使用。</span><span class="sxs-lookup"><span data-stu-id="cab1b-226">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![顯示匯總工具服務的 eShopOnContainers 架構圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="cab1b-228">**圖 6-37**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-228">**Figure 6-37**.</span></span> <span data-ttu-id="cab1b-229">使用彙總工具服務的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="cab1b-229">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="cab1b-230">進一步放大，在下圖的「購物」商務區域中，您可以看到在使用 API 閘道中的匯總工具時，用戶端應用程式與微服務之間的對話會降低。</span><span class="sxs-lookup"><span data-stu-id="cab1b-230">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![顯示 eShopOnContainers 架構放大的圖表。](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="cab1b-232">**圖 6-38**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-232">**Figure 6-38**.</span></span> <span data-ttu-id="cab1b-233">放大檢視彙總工具服務</span><span class="sxs-lookup"><span data-stu-id="cab1b-233">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="cab1b-234">您可以注意到當圖表顯示來自 API 閘道的可能要求時，可能會變得複雜。</span><span class="sxs-lookup"><span data-stu-id="cab1b-234">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="cab1b-235">另一方面，當您使用匯總工具模式時，您可以看到藍色箭號如何簡化用戶端應用程式觀點的通訊。</span><span class="sxs-lookup"><span data-stu-id="cab1b-235">On the other hand, when you use the aggregator pattern, you can see how the arrows in blue would simplify the communication from a client app perspective.</span></span> <span data-ttu-id="cab1b-236">這種模式不僅有助於減少通訊中的對話和延遲，還可改善遠端應用程式 (行動和 SPA 應用程式) 的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="cab1b-236">This pattern not only helps to reduce the chattiness and latency in the communication, it also improves the user experience significantly for the remote apps (mobile and SPA apps).</span></span>

<span data-ttu-id="cab1b-237">在「行銷」商務領域和微服務的案例中，這是一個簡單的使用案例，因此不需要使用匯總工具，但如果有需要，也可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="cab1b-237">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="cab1b-238">Ocelot API 閘道中的驗證與授權</span><span class="sxs-lookup"><span data-stu-id="cab1b-238">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="cab1b-239">在 Ocelot API 閘道中，您可以將驗證服務 (例如使用 [IdentityServer](https://identityserver.io/) 提供驗證權杖的 ASP.NET Core Web API 服務) 放在 API 閘道外部或內部。</span><span class="sxs-lookup"><span data-stu-id="cab1b-239">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="cab1b-240">由於 eShopOnContainers 使用多個具有依據 BFF 和業務領域之界限的 API 閘道，因此識別/驗證服務不會包含在 API 閘道中 (在下圖中以黃色醒目提示)。</span><span class="sxs-lookup"><span data-stu-id="cab1b-240">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![顯示 API 閘道底下身分識別微服務的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="cab1b-242">**圖 6-39**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-242">**Figure 6-39**.</span></span> <span data-ttu-id="cab1b-243">識別服務在 eShopOnContainers 中的位置</span><span class="sxs-lookup"><span data-stu-id="cab1b-243">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="cab1b-244">不過，Ocelot 也支援將識別/驗證微服務放在 API 閘道界限內，如下面另一個圖所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-244">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![此圖顯示 Ocelot API 閘道中的驗證。](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="cab1b-246">**圖 6-40**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-246">**Figure 6-40**.</span></span> <span data-ttu-id="cab1b-247">Ocelot 的驗證</span><span class="sxs-lookup"><span data-stu-id="cab1b-247">Authentication in Ocelot</span></span>

<span data-ttu-id="cab1b-248">如上圖所示，當身分識別微服務低於 API 閘道時 (AG) ： 1) AG 會向身分識別微服務要求驗證權杖，2) 身分識別微服務會使用驗證權杖將權杖傳回給 AG，3-4) AG 要求（來自微服務）。</span><span class="sxs-lookup"><span data-stu-id="cab1b-248">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="cab1b-249">由於 eShopOnContainers 應用程式已將 API 閘道分割成前端) 和商務區域 API 閘道的多個 BFF (後端，另一個選項是建立額外的 API 閘道來進行跨領域考慮。</span><span class="sxs-lookup"><span data-stu-id="cab1b-249">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="cab1b-250">該選擇相當適合具有多個跨領域考量微服務的更複雜微服務型架構。</span><span class="sxs-lookup"><span data-stu-id="cab1b-250">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="cab1b-251">由於 eShopOnContainers 中只有一項跨領域的考慮，因此為了簡單起見，已決定只處理 API 閘道領域的安全性服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-251">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="cab1b-252">在任何情況下，如果在 API 閘道層級保護應用程式，當嘗試使用任何受保護的微服務時，會先瀏覽 Ocelot API 閘道的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="cab1b-252">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="cab1b-253">這會將 HTTP 要求重新導向至身分識別或驗證微服務以取得存取權杖，讓您可以使用 access_token 來流覽受保護的服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-253">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="cab1b-254">您在 API 閘道層級使用驗證保護任何服務的方式，就是在 configuration.json 中設定其相關設定的 AuthenticationProviderKey。</span><span class="sxs-lookup"><span data-stu-id="cab1b-254">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

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

<span data-ttu-id="cab1b-255">當 Ocelot 執行時，它會查看 [重排 AuthenticationOptions] AuthenticationProviderKey，並檢查是否有向指定的金鑰註冊的驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="cab1b-255">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="cab1b-256">如果沒有，則 Ocelot 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="cab1b-256">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="cab1b-257">如果有，則重設路徑將會在執行時使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="cab1b-257">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="cab1b-258">由於 Ocelot WebHost 是使用 `authenticationProviderKey = "IdentityApiKey"` 設定，因此只要服務有任何要求沒有任何驗證權杖，就需要驗證。</span><span class="sxs-lookup"><span data-stu-id="cab1b-258">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="cab1b-259">然後，您也需要在任何要存取的資源 (例如微服務) 上透過 [Authorize] 屬性設定授權，例如在下列購物籃微服務控制器中。</span><span class="sxs-lookup"><span data-stu-id="cab1b-259">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="cab1b-260">ValidAudiences （例如「購物籃」）與每個微服務中定義的物件相互關聯 `AddJwtBearer()` ，並在啟動類別的 ConfigureServices ( # A1，例如下列程式碼中。</span><span class="sxs-lookup"><span data-stu-id="cab1b-260">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="cab1b-261">如果您嘗試存取任何受保護的微服務，例如使用以 API 閘道作為基礎之重新路由 URL 的購物籃微服務 `http://localhost:5202/api/v1/b/basket/1` ，除非您提供有效的權杖，否則您將會收到401的未經授權。</span><span class="sxs-lookup"><span data-stu-id="cab1b-261">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="cab1b-262">另一方面，如果重新路由 URL 經過驗證，Ocelot 就會叫用任何與其相關聯的下游配置， (內部微服務 URL) 。</span><span class="sxs-lookup"><span data-stu-id="cab1b-262">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="cab1b-263">**在 Ocelot 的重排層級進行授權。**</span><span class="sxs-lookup"><span data-stu-id="cab1b-263">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="cab1b-264">Ocelot 支援在驗證後評估宣告式授權。</span><span class="sxs-lookup"><span data-stu-id="cab1b-264">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="cab1b-265">您可以透過將下列程式行新增至 ReRoute 組態，在路由層級設定授權。</span><span class="sxs-lookup"><span data-stu-id="cab1b-265">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="cab1b-266">在該範例中，當呼叫授權中介軟體時，Ocelot 會查明使用者在權杖中是否有宣告類型 'UserType'，以及該宣告的值是否為 'employee'。</span><span class="sxs-lookup"><span data-stu-id="cab1b-266">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="cab1b-267">如果不是，則不會授權使用者，而且回應將會是403禁止的。</span><span class="sxs-lookup"><span data-stu-id="cab1b-267">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="cab1b-268">使用 Kubernetes 輸入加上 Ocelot API 閘道</span><span class="sxs-lookup"><span data-stu-id="cab1b-268">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="cab1b-269">使用 Kubernetes (例如 Azure Kubernetes Service 叢集) 時，您通常會透過 *Nginx* 的 [Kubernetes 輸入層](https://kubernetes.io/docs/concepts/services-networking/ingress/)來統一所有 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="cab1b-269">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="cab1b-270">在 Kubernetes 中，如果您未使用任何輸入方法，則您的服務和 pod 只能透過叢集網路路由 Ip。</span><span class="sxs-lookup"><span data-stu-id="cab1b-270">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="cab1b-271">但如果您使用輸入方法，您就會在網際網路與服務 (包括 API 閘道) 之間有一個中介層作為反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="cab1b-271">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="cab1b-272">按照定義，輸入是允許輸入連線到達叢集服務的規則集合。</span><span class="sxs-lookup"><span data-stu-id="cab1b-272">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="cab1b-273">輸入設定為提供服務可從外部連線的 URL、負載平衡流量、SSL 終止等。</span><span class="sxs-lookup"><span data-stu-id="cab1b-273">An ingress is configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="cab1b-274">使用者透過將輸入資源張貼到 API 伺服器來要求輸入。</span><span class="sxs-lookup"><span data-stu-id="cab1b-274">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="cab1b-275">在 eShopOnContainers 中，當您在本機開發並只使用您的開發電腦作為 Docker 主機時，您不會使用任何輸入，而只會使用多個 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="cab1b-275">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="cab1b-276">不過，當目標為以 Kubernetes 為基礎的「生產」環境時，eShopOnContainers 會在 API 閘道前方使用輸入。</span><span class="sxs-lookup"><span data-stu-id="cab1b-276">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="cab1b-277">如此一來，用戶端仍會呼叫相同的基底 URL，但要求會路由至多個 API 閘道或 BFF。</span><span class="sxs-lookup"><span data-stu-id="cab1b-277">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="cab1b-278">API 閘道是前端或外觀只會呈現服務，而不會呈現通常不在其範圍內的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cab1b-278">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="cab1b-279">此外，API 閘道可能會隱藏特定內部微服務。</span><span class="sxs-lookup"><span data-stu-id="cab1b-279">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="cab1b-280">不過，輸入只會重新導向 HTTP，而不會嘗試隱藏任何微服務或 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cab1b-280">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="cab1b-281">在 Web 應用程式前端的 Kubernetes 中有一個輸入 Nginx 層加上數個 Ocelot API 閘道/BFF 是理想的架構，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cab1b-281">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![顯示輸入層如何融入 AKS 環境中的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="cab1b-283">**圖 6-41**。</span><span class="sxs-lookup"><span data-stu-id="cab1b-283">**Figure 6-41**.</span></span> <span data-ttu-id="cab1b-284">部署至 Kubernetes 時之 eShopOnContainers 中的輸入層</span><span class="sxs-lookup"><span data-stu-id="cab1b-284">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="cab1b-285">Kubernetes 輸入可作為應用程式的所有流量（包括 web 應用程式）的反向 proxy，而這些流量都不在 Api 閘道範圍內。</span><span class="sxs-lookup"><span data-stu-id="cab1b-285">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are out of the Api gateway scope.</span></span> <span data-ttu-id="cab1b-286">當您將 eShopOnContainers 部署到 Kubernetes 時，它只會透過「輸入」公開一些服務或端點，基本上包括 URL 上的下列後置詞清單：</span><span class="sxs-lookup"><span data-stu-id="cab1b-286">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="cab1b-287">`/` 代表用戶端 SPA Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="cab1b-287">`/` for the client SPA web application</span></span>
- <span data-ttu-id="cab1b-288">`/webmvc` 代表用戶端 MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="cab1b-288">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="cab1b-289">`/webstatus` 代表顯示狀態/健康狀態檢查的用戶端 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="cab1b-289">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="cab1b-290">`/webshoppingapigw` 代表 Web BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="cab1b-290">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="cab1b-291">`/webmarketingapigw` 代表 Web BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="cab1b-291">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="cab1b-292">`/mobileshoppingapigw` 代表行動 BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="cab1b-292">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="cab1b-293">`/mobilemarketingapigw` 代表行動 BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="cab1b-293">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="cab1b-294">部署至 Kubernetes 時，每個 Ocelot API 閘道都會針對執行 API 閘道的每個 _pod_ 使用不同的「configuration.js開啟」檔案。</span><span class="sxs-lookup"><span data-stu-id="cab1b-294">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="cab1b-295">這些 "configuration.json" 檔案是透過裝載 deploy.ps1 (來提供，) 以名為 ' ocelot ' 的 Kubernetes _config map_ 建立的磁片區為基礎。</span><span class="sxs-lookup"><span data-stu-id="cab1b-295">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="cab1b-296">每個容器會將其相關的設定檔掛接在名為的容器檔案夾中 `/app/configuration` 。</span><span class="sxs-lookup"><span data-stu-id="cab1b-296">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="cab1b-297">在 eShopOnContainers 的原始程式碼檔中，可以在資料夾內找到原始的「configuration.js」檔案 `k8s/ocelot/` 。</span><span class="sxs-lookup"><span data-stu-id="cab1b-297">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="cab1b-298">每個 BFF/APIGateway 都有一個檔案。</span><span class="sxs-lookup"><span data-stu-id="cab1b-298">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="cab1b-299">Ocelot API 閘道中的其他跨領域功能</span><span class="sxs-lookup"><span data-stu-id="cab1b-299">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="cab1b-300">使用 Ocelot API 閘道時，還有其他重要的功能可供探索及使用，下列連結將進行說明。</span><span class="sxs-lookup"><span data-stu-id="cab1b-300">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="cab1b-301">**用戶端中的服務探索與 Consul 或 Eureka 整合 Ocelot** </span><span class="sxs-lookup"><span data-stu-id="cab1b-301">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="cab1b-302">**API 閘道層的快取** </span><span class="sxs-lookup"><span data-stu-id="cab1b-302">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="cab1b-303">**API 閘道層的記錄** </span><span class="sxs-lookup"><span data-stu-id="cab1b-303">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="cab1b-304">**API 閘道層) 的服務品質 (重試和斷路器** </span><span class="sxs-lookup"><span data-stu-id="cab1b-304">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="cab1b-305">**速率限制** </span><span class="sxs-lookup"><span data-stu-id="cab1b-305">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="cab1b-306">[上一個](background-tasks-with-ihostedservice.md) 
> [下一步](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="cab1b-306">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
