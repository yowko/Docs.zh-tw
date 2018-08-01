---
title: 使用 Ocelot 實作 API 閘道
description: 了解如何使用 Ocelot 實作 API 閘道，並了解如何在以容器為基礎的環境中使用 Ocelot。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 7400603aa11b2a741db727c97c2e4b2a17268ac0
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37878609"
---
# <a name="implementing-api-gateways-with-ocelot"></a><span data-ttu-id="decd3-103">使用 Ocelot 實作 API 閘道</span><span class="sxs-lookup"><span data-stu-id="decd3-103">Implementing API Gateways with Ocelot</span></span>

<span data-ttu-id="decd3-104">參考微服務應用程式 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 使用 [Ocelot](https://github.com/ThreeMammals/Ocelot) 的原因在於，Ocelot 是簡單且輕量型的 API 閘道，可連同您的微服務/容器一起部署到任何位置，例如 eShopOnContainers 所使用的下列任何環境中。</span><span class="sxs-lookup"><span data-stu-id="decd3-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot) because Ocelot is a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="decd3-105">您本機開發電腦、內部部署或雲端中的 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="decd3-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="decd3-106">內部部署或受控雲端 (例如 Azure Kubernetes Service (AKS)) 中的 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="decd3-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="decd3-107">內部部署或雲端中的 Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="decd3-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="decd3-108">在 Azure 中以 PaaS/無伺服器形式提供的 Service Fabric 網格。</span><span class="sxs-lookup"><span data-stu-id="decd3-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="decd3-109">架構及設計您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="decd3-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="decd3-110">下列架構圖說明如何在 eShopOnContainers 中使用 Ocelot 實作 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![eShopOnContainers 架構圖顯示用戶端應用程式、微服務及之間的 API 閘道](./media/image28.png)

<span data-ttu-id="decd3-112">**圖 8-27.**</span><span class="sxs-lookup"><span data-stu-id="decd3-112">**Figure 8-27.**</span></span> <span data-ttu-id="decd3-113">使用 API 閘道的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="decd3-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="decd3-114">該圖說明如何使用「適用於 Windows 的 Docker」或「適用於 Mac 的 Docker」，將整個應用程式部署到單一 Docker 主機或開發電腦。</span><span class="sxs-lookup"><span data-stu-id="decd3-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="decd3-115">不過，部署到任何協調器會相當類似，但您可以在協調器中擴充圖中的任何容器。</span><span class="sxs-lookup"><span data-stu-id="decd3-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span> 

<span data-ttu-id="decd3-116">此外，基礎結構資產 (例如資料庫、快取和訊息代理程式) 應該從協調器卸載，並部署到基礎結構的高可用性系統，例如 Azure SQL Database、Azure Cosmos DB、Azure Redis、Azure 服務匯流排或任何內部部署 HA 叢集解決方案。</span><span class="sxs-lookup"><span data-stu-id="decd3-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="decd3-117">您也可能在圖中注意到，擁有數個 API 閘道，可讓多個開發小組 (在本例中為行銷功能與購物功能) 獨立自主地開發和部署其微服務及其擁有的相關 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span> 

<span data-ttu-id="decd3-118">如果您有單一整合型 API 閘道，這會是要由多個開發小組更新的單一點，並可結合所有微服務與應用程式的單一組件。</span><span class="sxs-lookup"><span data-stu-id="decd3-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="decd3-119">更進一步設計時，有時也可以根據所選擇的架構，將微調 API 閘道限制為單一商務微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="decd3-120">擁有商務或領域所指出的 API 閘道界限可幫助您獲得更好的設計。</span><span class="sxs-lookup"><span data-stu-id="decd3-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span> 

<span data-ttu-id="decd3-121">例如，API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span> 

<span data-ttu-id="decd3-122">如需 UI 組合服務的詳細資訊，請參閱[根據微服務建立複合 UI](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout)。</span><span class="sxs-lookup"><span data-stu-id="decd3-122">For more information about UI composition services, see [Creating composite UI based on microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout).</span></span>

<span data-ttu-id="decd3-123">其重點在於，針對許多中型和大型應用程式，使用自訂建置的 API 閘道產品通常是不錯的方法，但不能作為單一整合型彙總工具或唯一中央自訂 API 閘道，除非該 API 閘道允許數個開發小組透過多個獨立設定區域建立自發微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="decd3-124">範例微服務/容器透過 API 閘道重設路徑</span><span class="sxs-lookup"><span data-stu-id="decd3-124">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="decd3-125">例如，`eShopOnContainers` 有大約六個內部微服務類型必須透過 API 閘道發佈，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-125">As an example, `eShopOnContainers` has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>
 
![](./media/image29.png)

<span data-ttu-id="decd3-126">**圖 8-28.**</span><span class="sxs-lookup"><span data-stu-id="decd3-126">**Figure 8-28.**</span></span> <span data-ttu-id="decd3-127">Visual Studio 之 eShopOnContainers 方案中的微服務資料夾</span><span class="sxs-lookup"><span data-stu-id="decd3-127">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="decd3-128">關於識別服務，其設計是不包含在 API 閘道路由中，因為它是系統中的唯一跨領域考量，但使用 Ocelot 時，還可能包含它作為重設路徑清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="decd3-128">About the Identity service, in the design it is left out of the API Gateway routing because it is the only cross-cutting concern in the system, but with Ocelot it is also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="decd3-129">上述所有服務目前會實作為 ASP.NET Core Web API 服務，如程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-129">All those services are currently implemented as ASP.NET Core Web API services, as you can tell because of the code.</span></span> <span data-ttu-id="decd3-130">讓我們專注於其中一個微服務，例如目錄微服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="decd3-130">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![](./media/image30.png)

<span data-ttu-id="decd3-131">**圖 8-29.**</span><span class="sxs-lookup"><span data-stu-id="decd3-131">**Figure 8-29.**</span></span> <span data-ttu-id="decd3-132">範例 Web API 微服務 (目錄微服務)</span><span class="sxs-lookup"><span data-stu-id="decd3-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="decd3-133">如您所見，目錄微服務是一般 ASP.NET Core Web API 專案，其中包含數個控制器和方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
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
<span data-ttu-id="decd3-134">HTTP 要求最終會執行該類型的 C# 程式碼來存取微服務資料庫，並執行任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="decd3-134">The HTTP request will end up running that kind of C# code accessing the microservice database plus any additional action.</span></span>

<span data-ttu-id="decd3-135">就微服務 URL 而言，當容器部署在您的本機開發電腦 (本機 Docker 主機) 時，每個微服務的容器一律會在其 dockerfile 中指定內部連接埠 (通常是連接埠 80)，如下列 dockerfile 所示：</span><span class="sxs-lookup"><span data-stu-id="decd3-135">In regards to the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port, usually port 80, specified in its dockerfile, as in the following dockerfile:</span></span>

```
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="decd3-136">程式碼中顯示的連接埠 80 位於 Docker 主機內部，因此用戶端應用程式無法連線到該連接埠。</span><span class="sxs-lookup"><span data-stu-id="decd3-136">The port 80 shown in the code is internal within the Docker host, so it cannot be reached by the client apps.</span></span> <span data-ttu-id="decd3-137">用戶端應用程式只能存取使用 `docker-compose` 部署時所發佈的外部連接埠 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="decd3-137">The client apps can access only to the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="decd3-138">部署到生產環境時，不應該發佈這些外部連接埠。</span><span class="sxs-lookup"><span data-stu-id="decd3-138">Those external ports shouldn't be published when deploying into a production environment.</span></span> <span data-ttu-id="decd3-139">這就是為什麼您想要使用 API 閘道來避免用戶端應用程式與微服務之間的直接通訊。</span><span class="sxs-lookup"><span data-stu-id="decd3-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="decd3-140">不過，開發時，您想要直接存取微服務/容器，並透過 Swagger 來執行。</span><span class="sxs-lookup"><span data-stu-id="decd3-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="decd3-141">這就是為什麼在 eShopOnContainers 中，即使 API 閘道或用戶端應用程式不會使用外部連接埠，仍會指定這些連接埠。</span><span class="sxs-lookup"><span data-stu-id="decd3-141">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="decd3-142">以下是目錄微服務的 `docker-compose.override.yml` 檔案範例：</span><span class="sxs-lookup"><span data-stu-id="decd3-142">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes. 
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="decd3-143">如您所見，在 docker-compose.override.yml 設定中，目錄容器的內部連接埠是連接埠 80，但外部存取的連接埠是 5101。</span><span class="sxs-lookup"><span data-stu-id="decd3-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="decd3-144">但此連接埠不應該供應用程式搭配 API 閘道使用，只能用來偵錯、執行及測試目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-144">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="decd3-145">一般來說，您無法使用 docker compose 部署到生產環境，因為微服務的正確生產部署環境是 Kubernetes 或 Service Fabric 等協調器。</span><span class="sxs-lookup"><span data-stu-id="decd3-145">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="decd3-146">部署到這些環境時，您會使用不同的設定檔，其中您不會直接發佈微服務的任何外部連接埠，但您一律會從 API 閘道使用反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="decd3-146">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="decd3-147">在您的本機 Docker 主機中執行目錄微服務，可透過從 Visual Studio 執行完整的 eShopOnContainers 方案 (它會執行 docker-compose 檔案中的所有服務)，或在位於放置 `docker-compose.yml` 和 docker-compose.override.yml 之資料夾的 CMD 或 PowerShell 中，使用下列 docker-compose 命令直接啟動目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-147">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="decd3-148">此命令只會執行 catalog.api 服務容器及 docker-compose.yml 中指定的相依性。</span><span class="sxs-lookup"><span data-stu-id="decd3-148">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="decd3-149">在本例中為 SQL Server 容器和 RabbitMQ 容器。</span><span class="sxs-lookup"><span data-stu-id="decd3-149">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="decd3-150">然後，您可以直接存取目錄微服務，並使用直接透過該「外部」連接埠 (在本例中為 `http://localhost:5101`) 存取的 Swagger UI 查看其方法。</span><span class="sxs-lookup"><span data-stu-id="decd3-150">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101`.</span></span> 

![](./media/image31.png)

<span data-ttu-id="decd3-151">**圖 8-30.**</span><span class="sxs-lookup"><span data-stu-id="decd3-151">**Figure 8-30.**</span></span> <span data-ttu-id="decd3-152">使用其 Swagger UI 測試目錄微服務</span><span class="sxs-lookup"><span data-stu-id="decd3-152">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="decd3-153">此時，您可以在 Visual Studio 的 C# 程式碼中設定中斷點、使用在 Swagger UI 中公開的方法測試微服務，最後使用 `docker-compose down` 命令清除所有內容。</span><span class="sxs-lookup"><span data-stu-id="decd3-153">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="decd3-154">不過，您想要在應用程式中避免微服務的這個直接存取通訊，在本例中是透過外部連接埠 5101。</span><span class="sxs-lookup"><span data-stu-id="decd3-154">However, this direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="decd3-155">您可以設定額外的 API 閘道間接層 (在本例中為 Ocelot) 來避免此問題。</span><span class="sxs-lookup"><span data-stu-id="decd3-155">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="decd3-156">如此一來，用戶端應用程式就不會直接存取微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-156">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="decd3-157">使用 Ocelot 實作您的 API 閘道</span><span class="sxs-lookup"><span data-stu-id="decd3-157">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="decd3-158">Ocelot 基本上是可依特定順序套用的一組中介軟體。</span><span class="sxs-lookup"><span data-stu-id="decd3-158">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="decd3-159">Ocelot 設計成只能搭配 ASP.NET Core 使用。</span><span class="sxs-lookup"><span data-stu-id="decd3-159">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="decd3-160">它以 netstandard2.0 為目標，因此可用於支援 .NET Standard 2.0 的任何位置，包括 .NET Core 2.0 執行階段以及 .NET Framework 4.6.1 執行階段和更新版本。</span><span class="sxs-lookup"><span data-stu-id="decd3-160">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="decd3-161">您可以從 Visual Studio 透過 [Ocelot 的 NuGet 套件](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 專案中安裝 Ocelot 及其相依性。</span><span class="sxs-lookup"><span data-stu-id="decd3-161">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```
Install-Package Ocelot
```

<span data-ttu-id="decd3-162">在 eShopOnContainers 中，其 API 閘道實作是簡單的 ASP.NET Core WebHost 專案，而且 Ocelot 的中介軟體會處理所有 API 閘道功能，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="decd3-162">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![](./media/image32.png)

<span data-ttu-id="decd3-163">**圖 8-31.**</span><span class="sxs-lookup"><span data-stu-id="decd3-163">**Figure 8-31.**</span></span> <span data-ttu-id="decd3-164">eShopOnContainers 中的 OcelotApiGw 基底專案</span><span class="sxs-lookup"><span data-stu-id="decd3-164">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="decd3-165">此 ASP.NET Core WebHost 專案是由兩個簡單的檔案所組成：`Program.cs` 和 `Startup.cs`。</span><span class="sxs-lookup"><span data-stu-id="decd3-165">This ASP.NET Core WebHost project is made by two simple files, the `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="decd3-166">Program.cs 只需要建立及設定一般 ASP.NET Core BuildWebHost。</span><span class="sxs-lookup"><span data-stu-id="decd3-166">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span> 

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

<span data-ttu-id="decd3-167">對於 Ocelot 而言，此處的重點是您必須透過 `AddJsonFile()` 方法提供給產生器的 `configuration.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="decd3-167">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="decd3-168">該 `configuration.json` 是您指定所有 API 閘道重設路徑的位置，表示具有特定連接埠的外部端點及相互關聯的內部端點 (通常使用不同的連接埠)。</span><span class="sxs-lookup"><span data-stu-id="decd3-168">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="decd3-169">設定分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="decd3-169">There are two sections to the configuration.</span></span> <span data-ttu-id="decd3-170">重設路徑和全域設定陣列。</span><span class="sxs-lookup"><span data-stu-id="decd3-170">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="decd3-171">重設路徑是指示 Ocelot 如何處理上游要求的物件。</span><span class="sxs-lookup"><span data-stu-id="decd3-171">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="decd3-172">全域設定可讓您覆寫重設路徑特定的設定。</span><span class="sxs-lookup"><span data-stu-id="decd3-172">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="decd3-173">它適用於您不想要管理許多重設路徑特定設定的情況。</span><span class="sxs-lookup"><span data-stu-id="decd3-173">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="decd3-174">以下是[重設路徑設定](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)檔的簡化範例，該檔案來自 eShopOnContainers 中的其中一個 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-174">Here’s a simplified example of [ReRoute configuration](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) file from one of the API Gateways from eShopOnContainers.</span></span>

```
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
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
          "Host": "basket.api",
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

<span data-ttu-id="decd3-175">Ocelot API 閘道的主要功能是接受傳入 HTTP 要求並將其轉送到下游服務 (目前為另一個 HTTP 要求)。</span><span class="sxs-lookup"><span data-stu-id="decd3-175">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="decd3-176">Ocelot 將一個要求路由至另一個要求的作業稱為重設路徑。</span><span class="sxs-lookup"><span data-stu-id="decd3-176">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="decd3-177">例如，讓我們將重點放在來自上述購物籃微服務設定之 configuration.json 中的其中一個重設路徑。</span><span class="sxs-lookup"><span data-stu-id="decd3-177">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
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

<span data-ttu-id="decd3-178">DownstreamPathTemplate、Scheme 和 DownstreamHostAndPorts 會建立此要求將轉送的內部微服務 URL。</span><span class="sxs-lookup"><span data-stu-id="decd3-178">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span> 

<span data-ttu-id="decd3-179">連接埠是服務所使用的內部連接埠。</span><span class="sxs-lookup"><span data-stu-id="decd3-179">The port is the internal port used by the service.</span></span> <span data-ttu-id="decd3-180">使用容器時，連接埠是在其 dockerfile 中指定。</span><span class="sxs-lookup"><span data-stu-id="decd3-180">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="decd3-181">`Host` 是相依於您使用之服務名稱解析的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="decd3-181">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="decd3-182">使用 docker-compose 時，服務名稱是由 Docker 主機提供，也就是使用 docker-compose 檔案所提供的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="decd3-182">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="decd3-183">如果使用 Kubernetes 或 Service Fabric 等協調器，該名稱應該透過 DNS 或每個協調器提供的名稱解析來解析。</span><span class="sxs-lookup"><span data-stu-id="decd3-183">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="decd3-184">DownstreamHostAndPorts 是包含您想要轉送要求的任何下游服務之主機和連接埠的陣列。</span><span class="sxs-lookup"><span data-stu-id="decd3-184">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="decd3-185">這通常只會包含一個項目，但有時您可能想要將要求負載平衡至您的下游服務，而 Ocelot 可讓您新增多個項目，然後選取負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="decd3-185">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="decd3-186">但如果使用 Azure 及任何協調器，最好透過雲端和協調器基礎結構進行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="decd3-186">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="decd3-187">UpstreamPathTemplate 是 URL，可供 Ocelot 用來識別針對用戶端中的指定要求使用哪個 DownstreamPathTemplate。</span><span class="sxs-lookup"><span data-stu-id="decd3-187">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="decd3-188">最後，使用 UpstreamHttpMethod，讓 Ocelot 可以區別傳送至相同 URL 的不同要求 (GET、POST、PUT)。</span><span class="sxs-lookup"><span data-stu-id="decd3-188">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="decd3-189">此時，您可能會有使用一或[多個合併 configuration.json 檔案](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)的單一 Ocelot API 閘道 (ASP.NET Core WebHost)，您也可以[在 Consul KV 存放區中儲存設定](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)。</span><span class="sxs-lookup"><span data-stu-id="decd3-189">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span> 

<span data-ttu-id="decd3-190">但如架構及設計一節所介紹，如果您真的想要有自發微服務，最好將單一整合型 API 閘道分割成多個 API 閘道及/或 BFF (前端的後端)。</span><span class="sxs-lookup"><span data-stu-id="decd3-190">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="decd3-191">針對該目的，讓我們來看如何使用 Docker 容器實作該方法。</span><span class="sxs-lookup"><span data-stu-id="decd3-191">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="decd3-192">使用單一 Docker 容器映像執行多個不同的 API 閘道/BFF 容器類型</span><span class="sxs-lookup"><span data-stu-id="decd3-192">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span> 

<span data-ttu-id="decd3-193">EShopOnContainers 中的設計使用 Ocelot API 閘道實作單一 Docker 容器映像；然後，當部署到 Docker 時，它會為透過為每個容器提供不同的 configuration.json 檔案，藉此為每種 API 閘道/BFF 類型建立不同的服務/容器。</span><span class="sxs-lookup"><span data-stu-id="decd3-193">The design in eShopOnContainers implements a single Docker container image with the Ocelot API Gateway but then, when deploying to Docker, it creates different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file for each container.</span></span>

![](./media/image33.png)

<span data-ttu-id="decd3-194">**圖 8-32.**</span><span class="sxs-lookup"><span data-stu-id="decd3-194">**Figure 8-32.**</span></span> <span data-ttu-id="decd3-195">在多個 API 閘道類型之間重複使用單一 Ocelot Docker 映像</span><span class="sxs-lookup"><span data-stu-id="decd3-195">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="decd3-196">在 eShopOnContainers 中，會使用名為 'OcelotApiGw' 的專案及 docker-compose.yml 檔案中指定的映像名稱 “eshop/ocelotapigw” 建立「泛型 Ocelot API 閘道 Docker 映像」。</span><span class="sxs-lookup"><span data-stu-id="decd3-196">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="decd3-197">然後，當部署到 Docker 時，會從該相同的 Docker 映像建立四個 API 閘道容器，如下列 docker-compose.yml 檔案摘錄所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-197">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```
PARTIAL DOCKER-COMPOSE.YML

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

<span data-ttu-id="decd3-198">此外，如您在 docker-compose.override.yml 檔案中所見，這些 API 閘道容器之間的唯一差異是 Ocelot 設定檔，每個服務容器會有不同的檔案，而且該檔案會在執行階段透過 Docker 磁碟區指定，如下列 docker-compose.override.yml 檔案所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-198">Additionally, and as you can see in the docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and is specified at runtime through a Docker volume, as shown in the following docker-compose.override.yml file.</span></span>

```
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5200:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration
 
mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5201:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5202:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5203:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="decd3-199">基於上述程式碼，而且如下面的 Visual Studio 總管所示，定義每個特定業務/BFF API 閘道所需的唯一檔案只有 configuration.json 檔案，因為這四個 API 閘道是以相同的 Docker 映像為依據。</span><span class="sxs-lookup"><span data-stu-id="decd3-199">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![](./media/image34.png)

<span data-ttu-id="decd3-200">**圖 8-33.**</span><span class="sxs-lookup"><span data-stu-id="decd3-200">**Figure 8-33.**</span></span> <span data-ttu-id="decd3-201">使用 Ocelot 定義每個 API 閘道/BFF 所需的唯一檔案是設定檔</span><span class="sxs-lookup"><span data-stu-id="decd3-201">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span> 

<span data-ttu-id="decd3-202">將 API 閘道分割成多個 API 閘道之後，著重於不同微服務子集的不同開發小組就可以使用獨立的 Ocelot 設定檔來管理自己的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-202">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="decd3-203">此外，他們還可以同時重複使用相同的 Ocelot Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="decd3-203">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span> 

<span data-ttu-id="decd3-204">現在，如果您執行使用 API 閘道的 eShopOnContainers (開啟 eShopOnContainers-ServicesAndWebApps.sln 方案時或如果執行 “docker-compose up”，預設會隨附於 VS)，就會執行下列範例路由。</span><span class="sxs-lookup"><span data-stu-id="decd3-204">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span> 

<span data-ttu-id="decd3-205">例如，瀏覽 webshoppingapigw API 閘道所提供的上游 URL http://localhost:5202/api/v1/c/catalog/items/2/ 時，您會從 Docker 主機的內部下游 URL http://catalog.api/api/v1/2 取得結果，如下列瀏覽器所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-205">For instance, when visiting the upstream URL http://localhost:5202/api/v1/c/catalog/items/2/ served by the webshoppingapigw API Gateway, you get the result from the internal Downstream URL http://catalog.api/api/v1/2 within the Docker host, as in the following browser.</span></span>

![](./media/image35.png)

<span data-ttu-id="decd3-206">**圖 8-34.**</span><span class="sxs-lookup"><span data-stu-id="decd3-206">**Figure 8-34.**</span></span> <span data-ttu-id="decd3-207">透過 API 閘道提供的 URL 存取微服務</span><span class="sxs-lookup"><span data-stu-id="decd3-207">Accessing a microservice through a URL provided by the API Gateway</span></span> 

<span data-ttu-id="decd3-208">基於測試或偵錯原因，如果您想要直接存取目錄 Docker 容器 (僅限開發環境) 而不透過 API 閘道傳遞，由於 'catalog.api' 是 Docker 主機內部的 DNS 解析 (由 docker-compose 服務名稱處理的服務探索)，因此直接存取容器的唯一方式是透過 docker-compose.override.yml 中發佈的外部連接埠，這只會提供給開發測試，例如下列瀏覽器中的 http://localhost:5101/api/v1/Catalog/items/1。</span><span class="sxs-lookup"><span data-stu-id="decd3-208">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as http://localhost:5101/api/v1/Catalog/items/1 in the following browser.</span></span>

![](./media/image36.png)

<span data-ttu-id="decd3-209">**圖 8-35.**</span><span class="sxs-lookup"><span data-stu-id="decd3-209">**Figure 8-35.**</span></span> <span data-ttu-id="decd3-210">直接存取微服務以進行測試</span><span class="sxs-lookup"><span data-stu-id="decd3-210">Direct access to a microservice for testing purposes</span></span> 

<span data-ttu-id="decd3-211">但應用程式設定成可透過 API 閘道存取所有微服務，而不是透過直接連接埠「捷徑」。</span><span class="sxs-lookup"><span data-stu-id="decd3-211">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span> 

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="decd3-212">eShopOnContainers 中的閘道彙總模式</span><span class="sxs-lookup"><span data-stu-id="decd3-212">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="decd3-213">如前所介紹，實作要求彙總的一個彈性方法，就是透過程式碼使用自訂服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-213">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="decd3-214">您也可以使用 Ocelot 中的 Request Aggregation (要求彙總) 功能來實作要求彙總，但其彈性可能不符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="decd3-214">You could also implement request aggregation with the Request Aggregation feature in Ocelot, but it might not be as flexible as you need.</span></span> <span data-ttu-id="decd3-215">因此，為了在 eShopOnContainers 中實作彙總所選取的方式，是針對每個彙總工具使用明確的 ASP.NET Core Web API 服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-215">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span> 

<span data-ttu-id="decd3-216">根據該方法，考量到上述簡化全域架構圖中未顯示的彙總工具服務，API 閘道組合圖實際上會涵蓋更大範圍。</span><span class="sxs-lookup"><span data-stu-id="decd3-216">According to that approach, the API Gateway composition diagram is in reality a bit more extended when taking into account the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span> 

<span data-ttu-id="decd3-217">在下圖中，您也可以查看彙總工具服務如何搭配其相關 API 閘道使用。</span><span class="sxs-lookup"><span data-stu-id="decd3-217">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![](./media/image37.png)

<span data-ttu-id="decd3-218">**圖 8-36.**</span><span class="sxs-lookup"><span data-stu-id="decd3-218">**Figure 8-36.**</span></span> <span data-ttu-id="decd3-219">使用彙總工具服務的 eShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="decd3-219">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="decd3-220">下圖進一步放大之後，您會注意到針對「購物」業務領域，在 API 閘道領域下使用這些彙總工具服務時，用戶端應用程式如何透過減少與微服務的頻繁交談獲得改善。</span><span class="sxs-lookup"><span data-stu-id="decd3-220">The following image is zooming in further, so you can notice how for the “Shopping” business area, the client apps could be improved by reducing chattiness with microservices when using those aggregator services under the realm of the API Gateways.</span></span> 

 ![](./media/image38.png)

<span data-ttu-id="decd3-221">**圖 8-37.**</span><span class="sxs-lookup"><span data-stu-id="decd3-221">**Figure 8-37.**</span></span> <span data-ttu-id="decd3-222">放大檢視彙總工具服務</span><span class="sxs-lookup"><span data-stu-id="decd3-222">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="decd3-223">您可能會注意到當圖中顯示從 API　閘道傳入可能要求時，會變得相當複雜。</span><span class="sxs-lookup"><span data-stu-id="decd3-223">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="decd3-224">雖然您可以看到藍色箭號如何簡化，但從用戶端應用程式觀點來看，當使用彙總工具模式時，若能減少通訊中的頻繁交談和延遲，最終特別會大幅改善遠端應用程式 (行動和 SPA 應用程式) 的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="decd3-224">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span> 

<span data-ttu-id="decd3-225">若是「行銷」業務領域和微服務，這是非常簡單的使用案例，因此不需要使用彙總工具，但如有需要也可以使用。</span><span class="sxs-lookup"><span data-stu-id="decd3-225">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="decd3-226">Ocelot API 閘道中的驗證與授權</span><span class="sxs-lookup"><span data-stu-id="decd3-226">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="decd3-227">在 Ocelot API 閘道中，您可以將驗證服務 (例如使用 [IdentityServer](http://identityserver.io/) 提供驗證權杖的 ASP.NET Core Web API 服務) 放在 API 閘道外部或內部。</span><span class="sxs-lookup"><span data-stu-id="decd3-227">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](http://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="decd3-228">由於 eShopOnContainers 使用多個具有依據 BFF 和業務領域之界限的 API 閘道，因此識別/驗證服務不會包含在 API 閘道中 (在下圖中以黃色醒目提示)。</span><span class="sxs-lookup"><span data-stu-id="decd3-228">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

 ![](./media/image39.png)

<span data-ttu-id="decd3-229">**圖 8-38.**</span><span class="sxs-lookup"><span data-stu-id="decd3-229">**Figure 8-38.**</span></span> <span data-ttu-id="decd3-230">識別服務在 eShopOnContainers 中的位置</span><span class="sxs-lookup"><span data-stu-id="decd3-230">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="decd3-231">不過，Ocelot 也支援將識別/驗證微服務放在 API 閘道界限內，如下面另一個圖所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-231">However, Ocelot also supports to sit the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

 ![](./media/image40.png)

<span data-ttu-id="decd3-232">**圖 8-39.**</span><span class="sxs-lookup"><span data-stu-id="decd3-232">**Figure 8-39.**</span></span> <span data-ttu-id="decd3-233">Ocelot API 閘道中的驗證</span><span class="sxs-lookup"><span data-stu-id="decd3-233">Authentication in Ocelot API Gateway</span></span>

<span data-ttu-id="decd3-234">由於 eShopOnContainers 應用程式已將 API 閘道分割成多個 BFF (前端的後端) 和業務領域 API 閘道，因此另一個選擇是為跨領域考量建立其他 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-234">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="decd3-235">該選擇相當適合具有多個跨領域考量微服務的更複雜微服務型架構。</span><span class="sxs-lookup"><span data-stu-id="decd3-235">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="decd3-236">由於 eShopOnContainers 中只有一個跨領域考量，因此為了簡單起見，決定只在 API 閘道領域外部處理安全性服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-236">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="decd3-237">在任何情況下，如果在 API 閘道層級保護應用程式，當嘗試使用任何受保護的微服務時，會先瀏覽 Ocelot API 閘道的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="decd3-237">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="decd3-238">這會重新導向 HTTP 要求瀏覽識別或驗證微服務以取得存取權杖，讓您可以使用存取權杖來瀏覽受保護的服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-238">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="decd3-239">您在 API 閘道層級使用驗證保護任何服務的方式，就是在 configuration.json 中設定其相關設定的 AuthenticationProviderKey。</span><span class="sxs-lookup"><span data-stu-id="decd3-239">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
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

<span data-ttu-id="decd3-240">當 Ocelot 執行時，它會查看重設路徑的 AuthenticationOptions.AuthenticationProviderKey，並確定有使用指定金鑰註冊的驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="decd3-240">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="decd3-241">如果沒有，則 Ocelot 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="decd3-241">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="decd3-242">如果有，則重設路徑將會在執行時使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="decd3-242">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="decd3-243">由於 Ocelot WebHost 是使用 `authenticationProviderKey = "IdentityApiKey"` 設定，因此只要服務有任何要求沒有任何驗證權杖，就需要驗證。</span><span class="sxs-lookup"><span data-stu-id="decd3-243">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span> 

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
```

<span data-ttu-id="decd3-244">然後，您也需要在任何要存取的資源 (例如微服務) 上透過 [Authorize] 屬性設定授權，例如在下列購物籃微服務控制器中。</span><span class="sxs-lookup"><span data-stu-id="decd3-244">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="decd3-245">ValidAudiences (例如「購物籃」) 會與每個微服務中定義的對象相互關聯，其中 `AddJwtBearer()` 位於啟動類別的 ConfigureServices()，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-245">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="decd3-246">在下一個步驟中，如果您嘗試存取任何受保護的微服務，例如其重設路徑 URL 依據 API 閘道 (例如 http://localhost:5202/api/v1/b/basket/1) 的購物籃微服務，除非您提供有效的權杖，否則您會收到 401 未經授權。</span><span class="sxs-lookup"><span data-stu-id="decd3-246">As next step, if you try to access any secured microservice like the Basket microservice with a Re-Route URL based on the API Gateway like http://localhost:5202/api/v1/b/basket/1 then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="decd3-247">相反地，如果重設路徑 URL 經過驗證，Ocelot 會叫用與其 (內部微服務 URL) 相關聯的任何下游配置。</span><span class="sxs-lookup"><span data-stu-id="decd3-247">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="decd3-248">**在 Ocelot 重設路徑層授權。**</span><span class="sxs-lookup"><span data-stu-id="decd3-248">**Authorization at Ocelot’s Re-Routes tier.**</span></span>  <span data-ttu-id="decd3-249">Ocelot 支援在驗證後評估宣告式授權。</span><span class="sxs-lookup"><span data-stu-id="decd3-249">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="decd3-250">您可以透過將下列程式碼新增至重設路徑設定，在路由層級設定授權。</span><span class="sxs-lookup"><span data-stu-id="decd3-250">You set the authorization at a route level by adding the following code to the re-route configuration.</span></span> 

```
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="decd3-251">在該範例中，當呼叫授權中介軟體時，Ocelot 會查明使用者在權杖中是否有宣告類型 'UserType'，以及該宣告的值是否為 'employee'。</span><span class="sxs-lookup"><span data-stu-id="decd3-251">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="decd3-252">如果不是，則不會授權使用者，而且回應會是 403 禁止。</span><span class="sxs-lookup"><span data-stu-id="decd3-252">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span> 

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="decd3-253">使用 Kubernetes 輸入加上 Ocelot API 閘道</span><span class="sxs-lookup"><span data-stu-id="decd3-253">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="decd3-254">使用 Kubernetes (例如 Azure Kubernetes Service 叢集) 時，您通常會透過以 *Nginx* 為基礎的 [Kuberentes 輸入層](https://kubernetes.io/docs/concepts/services-networking/ingress/)來整合所有 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="decd3-254">When using Kubernetes (like in an Azure Kubernetes Service cluster),, you usually unify all the HTTP requests through the [Kuberentes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span> 

<span data-ttu-id="decd3-255">在 Kuberentes 中，如果您未使用任何輸入方法，則您的服務和 Pod 只能透過叢集網路路由 IP。</span><span class="sxs-lookup"><span data-stu-id="decd3-255">In Kuberentes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span> 

<span data-ttu-id="decd3-256">但如果您使用輸入方法，您就會在網際網路與服務 (包括 API 閘道) 之間有一個中介層作為反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="decd3-256">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="decd3-257">按照定義，輸入是允許輸入連線到達叢集服務的規則集合。</span><span class="sxs-lookup"><span data-stu-id="decd3-257">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="decd3-258">輸入設定為提供服務可從外部連線的 URL、負載平衡流量、SSL 終止等。</span><span class="sxs-lookup"><span data-stu-id="decd3-258">An ingress is configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="decd3-259">使用者透過將輸入資源張貼到 API 伺服器來要求輸入。</span><span class="sxs-lookup"><span data-stu-id="decd3-259">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="decd3-260">在 eShopOnContainers 中，當您在本機開發並只使用您的開發電腦作為 Docker 主機時，您不會使用任何輸入，而只會使用多個 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="decd3-260">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span> 

<span data-ttu-id="decd3-261">不過，當目標為以 Kuberentes 為基礎的「生產」環境時，eShopOnCOntainers 會在 API 閘道前端使用輸入。</span><span class="sxs-lookup"><span data-stu-id="decd3-261">However, when targeting a “production” environment based on Kuberentes, eShopOnCOntainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="decd3-262">如此一來，用戶端仍會呼叫相同的基底 URL，但要求會路由至多個 API 閘道或 BFF。</span><span class="sxs-lookup"><span data-stu-id="decd3-262">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span> 

<span data-ttu-id="decd3-263">請注意，API 閘道是只會呈現服務，而不會呈現通常不在其範圍內之 Web 應用程式的前端 (或 Facade)。</span><span class="sxs-lookup"><span data-stu-id="decd3-263">Note that API Gateways are front-ends or facades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="decd3-264">此外，API 閘道可能會隱藏特定內部微服務。</span><span class="sxs-lookup"><span data-stu-id="decd3-264">In addition, the API Gateways might hide certain internal microservices.</span></span> 

<span data-ttu-id="decd3-265">不過，輸入只會重新導向 HTTP，而不會嘗試隱藏任何微服務或 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="decd3-265">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="decd3-266">在 Web 應用程式前端的 Kuberentes 中有一個輸入 Nginx 層加上數個 Ocelot API 閘道/BFF 是理想的架構，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="decd3-266">Having an ingress Nginx tier in Kuberentes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

 ![](./media/image41.png)

<span data-ttu-id="decd3-267">**圖 8-40.**</span><span class="sxs-lookup"><span data-stu-id="decd3-267">**Figure 8-40.**</span></span> <span data-ttu-id="decd3-268">部署至 Kubernetes 時之 eShopOnContainers 中的輸入層</span><span class="sxs-lookup"><span data-stu-id="decd3-268">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="decd3-269">當您將 eShopOnContainers 部署到 Kuberentes 時，它只會透過「輸入」公開一些服務或端點，基本上包括 URL 上的下列後置詞清單：</span><span class="sxs-lookup"><span data-stu-id="decd3-269">When you deploy eShopOnContainers into Kuberentes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

-   <span data-ttu-id="decd3-270">`/` 代表用戶端 SPA Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="decd3-270">`/` for the client SPA web application</span></span>
-   <span data-ttu-id="decd3-271">`/webmvc` 代表用戶端 MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="decd3-271">`/webmvc` for the client MVC web application</span></span>
-   <span data-ttu-id="decd3-272">`/webstatus` 代表顯示狀態/健康情況檢查的用戶端 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="decd3-272">`/webstatus` for the client web app showing the status/healchecks</span></span>
-   <span data-ttu-id="decd3-273">`/webshoppingapigw` 代表 Web BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="decd3-273">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
-   <span data-ttu-id="decd3-274">`/webmarketingapigw` 代表 Web BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="decd3-274">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
-   <span data-ttu-id="decd3-275">`/mobileshoppingapigw` 代表行動 BFF 和購物商務程序</span><span class="sxs-lookup"><span data-stu-id="decd3-275">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
-   <span data-ttu-id="decd3-276">`/mobilemarketingapigw` 代表行動 BFF 和行銷商務程序</span><span class="sxs-lookup"><span data-stu-id="decd3-276">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="decd3-277">部署到 Kubernetes 時，每個 Ocelot API 閘道會針對執行 API 閘道的每個 _Pod_ 使用不同的 “configuration.json” 檔案。</span><span class="sxs-lookup"><span data-stu-id="decd3-277">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="decd3-278">您可以透過掛接 (原本使用 deploy.ps1 指令碼) 根據名為 ‘ocelot’ 的 Kuberentes _config map_ 所建立的磁碟區，來提供這些 “configuration.json” 檔案。</span><span class="sxs-lookup"><span data-stu-id="decd3-278">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kuberentes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="decd3-279">每個容器會將其相關的設定檔掛接到名為 `/app/configuration` 的容器資料夾中。</span><span class="sxs-lookup"><span data-stu-id="decd3-279">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="decd3-280">在 eShopOnContainers 的原始程式碼檔中，原始 “configuration.json” 檔案位於 `k8s/ocelot/` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="decd3-280">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="decd3-281">每一個 BFF/API 閘道各有一個檔案。</span><span class="sxs-lookup"><span data-stu-id="decd3-281">There’s one file for each BFF/APIGateway.</span></span>


## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="decd3-282">Ocelot API 閘道中的其他跨領域功能</span><span class="sxs-lookup"><span data-stu-id="decd3-282">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="decd3-283">使用 Ocelot API 閘道時，還有其他重要的功能可供探索及使用，下列連結將進行說明。</span><span class="sxs-lookup"><span data-stu-id="decd3-283">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

-   <span data-ttu-id="decd3-284">**在整合 Ocelot 與 Consul 或 Eureka 的用戶端進行服務探索** 
    [*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)</span><span class="sxs-lookup"><span data-stu-id="decd3-284">**Service discovery in the client side integrating Ocelot with Consul or Eureka** 
[*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)</span></span>

-   <span data-ttu-id="decd3-285">**API 閘道層的快取** 
    [*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)</span><span class="sxs-lookup"><span data-stu-id="decd3-285">**Caching at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)</span></span>

-   <span data-ttu-id="decd3-286">**API 閘道層的記錄** 
    [*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)</span><span class="sxs-lookup"><span data-stu-id="decd3-286">**Logging at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)</span></span>

-   <span data-ttu-id="decd3-287">**API 閘道層的服務品質 (重試和斷路器)** 
    [*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)</span><span class="sxs-lookup"><span data-stu-id="decd3-287">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)</span></span>

-   <span data-ttu-id="decd3-288">**速率限制** 
    [*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )</span><span class="sxs-lookup"><span data-stu-id="decd3-288">**Rate limiting** 
[*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="decd3-289">[上一頁] (background-tasks-with-ihostedservice.md) [下一頁] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="decd3-289">[Previous] (background-tasks-with-ihostedservice.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
