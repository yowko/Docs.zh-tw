---
title: 將 eShopOnContainers 對應至 Azure 服務
description: 將 eShopOnContainers 對應至 Azure 服務，例如 Azure Kubernetes Service、API 閘道和 Azure 服務匯流排。
ms.date: 06/30/2019
ms.openlocfilehash: feb6d8f5ca05ab55ce4695d1200766a18b8f744a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182815"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a><span data-ttu-id="5bfbf-103">將 eShopOnContainers 對應至 Azure 服務</span><span class="sxs-lookup"><span data-stu-id="5bfbf-103">Mapping eShopOnContainers to Azure Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5bfbf-104">雖然並非必要，但 Azure 非常適合支援 eShopOnContainers，因為專案已建立為雲端原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-104">Although not required, Azure is well-suited to supporting the eShopOnContainers because the project was built to be a cloud-native application.</span></span> <span data-ttu-id="5bfbf-105">應用程式是以 .NET Core 為基礎，因此它可以在 Linux 或 Windows 容器上執行，視 Docker 主機而定。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-105">The application is built with .NET Core, so it can run on Linux or Windows containers depending on the Docker host.</span></span> <span data-ttu-id="5bfbf-106">應用程式是由多個自發微服務所組成，每個都有自己的資料。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-106">The application is made up of multiple autonomous microservices, each with its own data.</span></span> <span data-ttu-id="5bfbf-107">不同的微服務展示不同的方法，範圍從簡單的 CRUD 作業到更複雜的 DDD 和 CQRS 模式。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-107">The different microservices showcase different approaches, ranging from simple CRUD operations to more complex DDD and CQRS patterns.</span></span> <span data-ttu-id="5bfbf-108">微服務透過 HTTP 與用戶端通訊，透過以訊息為基礎的通訊彼此。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-108">Microservices communicate with clients over HTTP and with one another via message-based communication.</span></span> <span data-ttu-id="5bfbf-109">應用程式也支援多個用戶端平臺，因為它採用 HTTP 作為標準通訊協定，並包含在 Android、iOS 和 Windows 平臺上執行的 ASP.NET Core 和 Xamarin 行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-109">The application supports multiple platforms for clients as well, since it adopts HTTP as a standard communication protocol and includes ASP.NET Core and Xamarin mobile apps that run on Android, iOS, and Windows platforms.</span></span>

<span data-ttu-id="5bfbf-110">應用程式的架構如圖2-5 所示。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-110">The application's architecture is shown in Figure 2-5.</span></span> <span data-ttu-id="5bfbf-111">左側是用戶端應用程式，分成行動、傳統 Web 和 Web 單頁應用程式（SPA）等。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-111">On the left are the client apps, broken up into mobile, traditional Web, and Web Single Page Application (SPA) flavors.</span></span> <span data-ttu-id="5bfbf-112">右側是組成系統的伺服器端元件，每一個都可以裝載于 Docker 容器和 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-112">On the right are the server-side components that make up the system, each of which can be hosted in Docker containers and Kubernetes clusters.</span></span> <span data-ttu-id="5bfbf-113">傳統的 web 應用程式由以黃色顯示的 ASP.NET Core MVC 應用程式提供技術支援。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-113">The traditional web app is powered by the ASP.NET Core MVC application shown in yellow.</span></span> <span data-ttu-id="5bfbf-114">此應用程式和行動和 web SPA 應用程式會透過一或多個 API 閘道與個別微服務通訊。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-114">This app and the mobile and web SPA applications communicate with the individual microservices through one or more API gateways.</span></span> <span data-ttu-id="5bfbf-115">API 閘道會遵循「前端的後端」（BFF）模式，這表示每個閘道都是設計來支援指定的前端用戶端。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-115">The API gateways follow the "backends for front ends" (BFF) pattern, meaning that each gateway is designed to support a given front-end client.</span></span> <span data-ttu-id="5bfbf-116">個別的微服務會列在 API 閘道的右邊，同時包含商務邏輯和某種類型的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-116">The individual microservices are listed to the right of the API gateways and include both business logic and some kind of persistence store.</span></span> <span data-ttu-id="5bfbf-117">不同的服務會利用 SQL Server 資料庫、Redis 快取實例和 MongoDB/CosmosDB 存放區。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-117">The different services make use of SQL Server databases, Redis cache instances, and MongoDB/CosmosDB stores.</span></span> <span data-ttu-id="5bfbf-118">最右側的是系統的事件匯流排，用於微服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-118">On the far right is the system's Event Bus, which is used for communication between the microservices.</span></span>

<span data-ttu-id="5bfbf-119">![eShopOnContainers 架構](./media/eshoponcontainers-architecture.png)
**圖 2-5**。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-119">![eShopOnContainers Architecture](./media/eshoponcontainers-architecture.png)
**Figure 2-5**.</span></span> <span data-ttu-id="5bfbf-120">EShopOnContainers 架構。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-120">The eShopOnContainers Architecture.</span></span>

<span data-ttu-id="5bfbf-121">此架構的伺服器端元件可輕鬆地對應至 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-121">The server-side components of this architecture all map easily to Azure services.</span></span>

## <a name="container-orchestration-and-clustering"></a><span data-ttu-id="5bfbf-122">容器協調流程和叢集</span><span class="sxs-lookup"><span data-stu-id="5bfbf-122">Container orchestration and clustering</span></span>

<span data-ttu-id="5bfbf-123">應用程式的容器裝載服務（從 ASP.NET Core MVC 應用程式到個別目錄和排序微服務）可以在 Azure Kubernetes Service （AKS）中進行裝載和管理。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-123">The application's container-hosted services, from ASP.NET Core MVC apps to individual Catalog and Ordering microservices, can be hosted and managed in Azure Kubernetes Service (AKS).</span></span> <span data-ttu-id="5bfbf-124">應用程式可以在 Docker 和 Kubernetes 本機上執行，然後將相同的容器部署至裝載于 AKS 中的預備和生產環境。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-124">The application can run locally on Docker and Kubernetes, and the same containers can then be deployed to staging and production environments hosted in AKS.</span></span> <span data-ttu-id="5bfbf-125">此程式可以自動化，如我們在下一節中所見。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-125">This process can be automated as we'll see in the next section.</span></span>

<span data-ttu-id="5bfbf-126">AKS 為個別的容器叢集提供管理服務。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-126">AKS provides management services for individual clusters of containers.</span></span> <span data-ttu-id="5bfbf-127">應用程式會為上述架構圖中顯示的每個微服務部署個別的 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-127">The application will deploy separate AKS clusters for each microservice shown in the architecture diagram above.</span></span> <span data-ttu-id="5bfbf-128">這種方法可讓每個個別服務根據其資源需求各自獨立。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-128">This approach allows each individual service to each independently according to its resource demands.</span></span> <span data-ttu-id="5bfbf-129">每個微服務也可以獨立部署，而且在理想的情況下，這類部署應該會產生零的系統停機時間。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-129">Each microservice can also be deployed independently, and ideally such deployments should incur zero system downtime.</span></span>

## <a name="api-gateway"></a><span data-ttu-id="5bfbf-130">API 閘道</span><span class="sxs-lookup"><span data-stu-id="5bfbf-130">API Gateway</span></span>

<span data-ttu-id="5bfbf-131">EShopOnContainers 應用程式有多個前端用戶端和多個不同的後端服務。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-131">The eShopOnContainers application has multiple front-end clients and multiple different back-end services.</span></span> <span data-ttu-id="5bfbf-132">用戶端應用程式與支援它們的微服務之間不會有一對一的對應關係。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-132">There's no one-to-one correspondence between the client applications and the microservices that support them.</span></span> <span data-ttu-id="5bfbf-133">在這種情況下，以安全的方式撰寫用戶端軟體以與各種後端服務互動時，可能會有很大的複雜性。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-133">In such a scenario, there may be a great deal of complexity when writing client software to interface with the various back-end services in a secure manner.</span></span> <span data-ttu-id="5bfbf-134">每個用戶端都需要自行解決這項複雜性，因而導致重複，以及在服務變更或新原則執行時進行更新的許多位置。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-134">Each client would need to address this complexity on its own, resulting in duplication and many places in which to make updates as services change or new policies are implemented.</span></span>

<span data-ttu-id="5bfbf-135">Azure API 管理（APIM）可協助組織以一致且易於管理的方式發佈 Api。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-135">Azure API Management (APIM) helps organizations publish APIs in a consistent, manageable fashion.</span></span> <span data-ttu-id="5bfbf-136">APIM 是由三個元件所組成： API 閘道和系統管理入口網站（Azure 入口網站），以及開發人員入口網站。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-136">APIM consists of three components: the API Gateway, and administration portal (the Azure portal), and a developer portal.</span></span>

<span data-ttu-id="5bfbf-137">API 閘道會接受 API 呼叫，並將其路由傳送至適當的後端 API。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-137">The API Gateway accepts API calls and routes them to the appropriate back-end API.</span></span> <span data-ttu-id="5bfbf-138">它也可以在不修改程式碼的情況下，提供額外的服務（例如 API 金鑰或 JWT 權杖和 API 轉換），而不需修改程式碼（例如，為了配合需要較舊介面的用戶端）。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-138">It can also provide additional services like verification of API keys or JWT tokens and API transformation on the fly without code modifications (for instance, to accommodate clients expecting an older interface).</span></span>

<span data-ttu-id="5bfbf-139">Azure 入口網站，您可以在其中定義 API 架構，並將不同的 Api 封裝到產品中。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-139">The Azure portal is where you define the API schema and package different APIs into products.</span></span> <span data-ttu-id="5bfbf-140">您也可以設定使用者存取、查看報告，以及設定配額或轉換的原則。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-140">You also configure user access, view reports, and configure policies for quotas or transformations.</span></span>

<span data-ttu-id="5bfbf-141">開發人員入口網站作為開發人員的主要資源。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-141">The developer portal serves as the main resource for developers.</span></span> <span data-ttu-id="5bfbf-142">它會為開發人員提供 API 檔、互動式測試主控台，並報告自己的使用方式。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-142">It provides developers with API documentation, an interactive test console, and reports on their own usage.</span></span> <span data-ttu-id="5bfbf-143">開發人員也可以使用入口網站來建立及管理自己的帳戶，包括訂用帳戶和 API 金鑰支援。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-143">Developers also use the portal to create and manage their own accounts, including subscription and API key support.</span></span>

<span data-ttu-id="5bfbf-144">使用 APIM，應用程式可以公開數個不同的服務群組，每個都提供特定前端用戶端的後端。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-144">Using APIM, applications can expose several different groups of services, each providing a back end for a particular front-end client.</span></span> <span data-ttu-id="5bfbf-145">針對複雜的案例，建議使用 APIM。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-145">APIM is recommended for complex scenarios.</span></span> <span data-ttu-id="5bfbf-146">為了簡化需求，可以使用輕量 API 閘道 Ocelot。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-146">For simpler needs, the lightweight API Gateway Ocelot can be used.</span></span> <span data-ttu-id="5bfbf-147">EShopOnContainers 應用程式會使用 Ocelot，因為它是簡單的，而且可以部署到與應用程式本身相同的應用程式環境中。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-147">The eShopOnContainers app uses Ocelot because of its simplicity and because it can be deployed into the same application environment as the application itself.</span></span> [<span data-ttu-id="5bfbf-148">深入瞭解 eShopOnContainers、APIM 和 Ocelot。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-148">Learn more about eShopOnContainers, APIM, and Ocelot.</span></span>](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

<span data-ttu-id="5bfbf-149">如果您的應用程式使用 AKS，另一個選項是將 Azure 閘道輸入控制器部署為 AKS 叢集中的 pod。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-149">Another option if your application is using AKS is to deploy the Azure Gateway Ingress Controller as a pod within your AKS cluster.</span></span> <span data-ttu-id="5bfbf-150">這可讓您的叢集與 Azure 應用程式閘道整合，讓閘道能夠對 AKS pod 的流量進行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-150">This allows your cluster to integrate with an Azure Application Gateway, allowing the gateway to load-balance traffic to the AKS pods.</span></span> <span data-ttu-id="5bfbf-151">[深入瞭解適用于 AKS 的 Azure 閘道輸入控制器](https://github.com/Azure/application-gateway-kubernetes-ingress)。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-151">[Learn more about the Azure Gateway Ingress Controller for AKS](https://github.com/Azure/application-gateway-kubernetes-ingress).</span></span>

## <a name="data"></a><span data-ttu-id="5bfbf-152">資料</span><span class="sxs-lookup"><span data-stu-id="5bfbf-152">Data</span></span>

<span data-ttu-id="5bfbf-153">EShopOnContainers 所使用的各種後端服務會有不同的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-153">The various back-end services used by eShopOnContainers have different storage requirements.</span></span> <span data-ttu-id="5bfbf-154">有數個微服務使用 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-154">Several microservices use SQL Server databases.</span></span> <span data-ttu-id="5bfbf-155">購物籃微服務會利用 Redis 快取來保存其持續性。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-155">The Basket microservice leverages a Redis cache for its persistence.</span></span> <span data-ttu-id="5bfbf-156">位置微服務需要 MongoDB API 來取得其資料。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-156">The Locations microservice expects a MongoDB API for its data.</span></span> <span data-ttu-id="5bfbf-157">Azure 支援每種資料格式。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-157">Azure supports each of these data formats.</span></span>

<span data-ttu-id="5bfbf-158">針對 SQL Server 資料庫支援，Azure 提供從單一資料庫到可高度擴充 SQL Database 彈性集區之所有專案的產品。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-158">For SQL Server database support, Azure has products for everything from single databases up to highly scalable SQL Database elastic pools.</span></span> <span data-ttu-id="5bfbf-159">您可以設定個別的微服務，以便快速且輕鬆地與自己的個別 SQL Server 資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-159">Individual microservices can be configured to communicate with their own individual SQL Server databases quickly and easily.</span></span> <span data-ttu-id="5bfbf-160">這些資料庫可以視需要調整，以根據其需求來支援每個不同的微服務。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-160">These databases can be scaled as needed to support each separate microservice according to its needs.</span></span>

<span data-ttu-id="5bfbf-161">EShopOnContainers 應用程式會將使用者目前的購物籃儲存在要求之間。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-161">The eShopOnContainers application stores the user's current shopping basket between requests.</span></span> <span data-ttu-id="5bfbf-162">這是由將資料儲存在 Redis 快取中的購物籃微服務所管理。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-162">This is managed by the Basket microservice that stores the data in a Redis cache.</span></span> <span data-ttu-id="5bfbf-163">在開發中，此快取可以部署在容器中，而在生產環境中，它可以使用 Azure Cache for Redis。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-163">In development, this cache can be deployed in a container, while in production it can utilize Azure Cache for Redis.</span></span> <span data-ttu-id="5bfbf-164">Azure Cache for Redis 是完全受控的服務，可提供高效能和可靠性，而不需要自行部署和管理 Redis 實例或容器。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-164">Azure Cache for Redis is a fully managed service offering high performance and reliability without the need to deploy and manage Redis instances or containers on your own.</span></span>

<span data-ttu-id="5bfbf-165">[位置] 微服務會使用 MongoDB NoSQL 資料庫來保存其持續性。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-165">The Locations microservice uses a MongoDB NoSQL database for its persistence.</span></span> <span data-ttu-id="5bfbf-166">在開發期間，資料庫可以部署在自己的容器中，而在生產環境中，服務可以利用[Azure Cosmos DB 適用于 MongoDB 的 API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-166">During development, the database can be deployed in its own container, while in production the service can leverage [Azure Cosmos DB's API for MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> <span data-ttu-id="5bfbf-167">Azure Cosmos DB 的優點之一，就是能夠利用多個不同的通訊協定，包括 SQL API 和常見的 NoSQL Api，包括 MongoDB、Cassandra、Gremlin 和 Azure 表格儲存體。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-167">One of the benefits of Azure Cosmos DB is its ability to leverage multiple different communication protocols, including a SQL API and common NoSQL APIs including MongoDB, Cassandra, Gremlin, and Azure Table Storage.</span></span> <span data-ttu-id="5bfbf-168">Azure Cosmos DB 提供完全受控且全域散發的資料庫即服務，可進行調整以符合使用它的服務需求。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-168">Azure Cosmos DB offers a fully managed and globally distributed database as a service that can scale to meet the needs of the services that use it.</span></span>

<span data-ttu-id="5bfbf-169">[第5章](distributed-data.md)會詳細說明雲端原生應用程式中的分散式資料。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-169">Distributed data in cloud-native applications is covered in more detail in [chapter 5](distributed-data.md).</span></span>

## <a name="event-bus"></a><span data-ttu-id="5bfbf-170">事件匯流排</span><span class="sxs-lookup"><span data-stu-id="5bfbf-170">Event Bus</span></span>

<span data-ttu-id="5bfbf-171">應用程式會使用事件來傳達不同服務之間的變更。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-171">The application uses events to communicate changes between different services.</span></span> <span data-ttu-id="5bfbf-172">這項功能可以使用各種不同的實作為實作為，而在本機 eShopOnContainers 應用程式會使用[RabbitMQ](https://www.rabbitmq.com/)。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-172">This functionality can be implemented with a variety of implementations, and locally the eShopOnContainers application uses [RabbitMQ](https://www.rabbitmq.com/).</span></span> <span data-ttu-id="5bfbf-173">在 Azure 中裝載時，應用程式會利用[Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus/)來進行訊息處理。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-173">When hosted in Azure, the application would leverage [Azure Service Bus](https://docs.microsoft.com/azure/service-bus/) for its messaging.</span></span> <span data-ttu-id="5bfbf-174">Azure 服務匯流排是完全受控的整合訊息代理人，可讓應用程式和服務以分離、可靠且非同步方式彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-174">Azure Service Bus is a fully managed integration message broker that allows applications and services to communicate with one another in a decoupled, reliable, asynchronous manner.</span></span> <span data-ttu-id="5bfbf-175">Azure 服務匯流排支援個別的佇列，以及不同的*主題*來支援「發行者」訂閱者案例。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-175">Azure Service Bus supports individual queues as well as separate *topics* to support publisher-subscriber scenarios.</span></span> <span data-ttu-id="5bfbf-176">EShopOnContainers 應用程式會利用 Azure 服務匯流排的主題來支援將訊息從一個微服務散發到任何其他需要回應指定訊息的微服務。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-176">The eShopOnContainers application would leverage topics with Azure Service Bus to support distributing messages from one microservice to any other microservice that needed to react to a given message.</span></span>

## <a name="resiliency"></a><span data-ttu-id="5bfbf-177">恢復</span><span class="sxs-lookup"><span data-stu-id="5bfbf-177">Resiliency</span></span>

<span data-ttu-id="5bfbf-178">一旦部署到生產環境後，eShopOnContainers 應用程式就能夠利用數個可用的 Azure 服務來改善其復原能力。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-178">Once deployed to production, the eShopOnContainers application would be able to take advantage of several Azure services available to improve its resiliency.</span></span> <span data-ttu-id="5bfbf-179">應用程式會發佈健康情況檢查，其可與 Application Insights 整合，以根據應用程式的可用性提供報告和警示。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-179">The application publishes health checks, which can be integrated with Application Insights to provide reporting and alerts based on the app's availability.</span></span> <span data-ttu-id="5bfbf-180">Azure 資源也會提供診斷記錄，以用來識別及更正錯誤和效能問題。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-180">Azure resources also provide diagnostic logs that can be used to identify and correct bugs and performance issues.</span></span> <span data-ttu-id="5bfbf-181">資源記錄會提供應用程式使用不同 Azure 資源的時機和方式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-181">Resource logs provide detailed information on when and how different Azure resources are used by the application.</span></span> <span data-ttu-id="5bfbf-182">您將在[第6章](resiliency.md)深入瞭解雲端原生復原功能。</span><span class="sxs-lookup"><span data-stu-id="5bfbf-182">You'll learn more about cloud-native resiliency features in [chapter 6](resiliency.md).</span></span>

## <a name="references"></a><span data-ttu-id="5bfbf-183">reference</span><span class="sxs-lookup"><span data-stu-id="5bfbf-183">References</span></span>

- [<span data-ttu-id="5bfbf-184">EShopOnContainers 架構</span><span class="sxs-lookup"><span data-stu-id="5bfbf-184">The eShopOnContainers Architecture</span></span>](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [<span data-ttu-id="5bfbf-185">協調微服務和多容器應用程式的高延展性和可用性</span><span class="sxs-lookup"><span data-stu-id="5bfbf-185">Orchestrating microservices and multi-container applications for high scalability and availability</span></span>](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [<span data-ttu-id="5bfbf-186">Azure API 管理</span><span class="sxs-lookup"><span data-stu-id="5bfbf-186">Azure API Management</span></span>](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [<span data-ttu-id="5bfbf-187">Azure SQL Database 總覽</span><span class="sxs-lookup"><span data-stu-id="5bfbf-187">Azure SQL Database Overview</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [<span data-ttu-id="5bfbf-188">Azure Cache for Redis</span><span class="sxs-lookup"><span data-stu-id="5bfbf-188">Azure Cache for Redis</span></span>](https://azure.microsoft.com/services/cache/)
- [<span data-ttu-id="5bfbf-189">Azure Cosmos DB 適用于 MongoDB 的 API</span><span class="sxs-lookup"><span data-stu-id="5bfbf-189">Azure Cosmos DB's API for MongoDB</span></span>](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [<span data-ttu-id="5bfbf-190">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="5bfbf-190">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [<span data-ttu-id="5bfbf-191">Azure 監視器總覽</span><span class="sxs-lookup"><span data-stu-id="5bfbf-191">Azure Monitor overview</span></span>](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
><span data-ttu-id="5bfbf-192">[上一頁](introduce-eshoponcontainers-reference-app.md)
>[下一頁](deploy-eshoponcontainers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="5bfbf-192">[Previous](introduce-eshoponcontainers-reference-app.md)
[Next](deploy-eshoponcontainers-azure.md)</span></span>