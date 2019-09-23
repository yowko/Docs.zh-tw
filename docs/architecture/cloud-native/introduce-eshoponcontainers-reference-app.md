---
title: EShopOnContainers 參考應用程式簡介
description: 介紹適用于 ASP.NET Core 和 Azure 的 eShopOnContainers Cloud Native 微服務 Reference 應用程式。
ms.date: 06/30/2019
ms.openlocfilehash: 20f9175ada2e5439be363781a2b187c10ba86d37
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182857"
---
# <a name="introducing-eshoponcontainers-reference-app"></a><span data-ttu-id="00a6b-103">EShopOnContainers 參考應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="00a6b-103">Introducing eShopOnContainers reference app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="00a6b-104">Microsoft 與領先的社區專家合作，已產生全功能的雲端原生微服務參考應用程式 eShopOnContainers。</span><span class="sxs-lookup"><span data-stu-id="00a6b-104">Microsoft, in partnership with leading community experts, has produced a full-featured cloud-native microservices reference application, eShopOnContainers.</span></span> <span data-ttu-id="00a6b-105">此應用程式建置於使用 .NET Core 和 Docker，並選擇性地建立 Azure、Kubernetes 和 Visual Studio，以打造線上店面。</span><span class="sxs-lookup"><span data-stu-id="00a6b-105">This application is built to showcase using .NET Core and Docker, and optionally Azure, Kubernetes, and Visual Studio, to build an online storefront.</span></span>

![eShopOnContainers 範例應用程式螢幕擷取畫面。](./media/eshoponcontainers-sample-app-screenshot.png)

<span data-ttu-id="00a6b-107">**圖 2-1**.</span><span class="sxs-lookup"><span data-stu-id="00a6b-107">**Figure 2-1**.</span></span> <span data-ttu-id="00a6b-108">eShopOnContainers 範例應用程式螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="00a6b-108">eShopOnContainers Sample App Screenshot.</span></span>

<span data-ttu-id="00a6b-109">在開始本章之前，建議您先下載[eShopOnContainers reference 應用程式](https://github.com/dotnet-architecture/eShopOnContainers)。</span><span class="sxs-lookup"><span data-stu-id="00a6b-109">Before starting this chapter, we recommend that you download the [eShopOnContainers reference application](https://github.com/dotnet-architecture/eShopOnContainers).</span></span> <span data-ttu-id="00a6b-110">如果您這樣做，您就可以更輕鬆地追蹤所呈現的資訊。</span><span class="sxs-lookup"><span data-stu-id="00a6b-110">If you do so, it should be easier for you to follow along with the information presented.</span></span>

## <a name="features-and-requirements"></a><span data-ttu-id="00a6b-111">功能和需求</span><span class="sxs-lookup"><span data-stu-id="00a6b-111">Features and requirements</span></span>

<span data-ttu-id="00a6b-112">讓我們先複習一下應用程式的功能和需求。</span><span class="sxs-lookup"><span data-stu-id="00a6b-112">Let's start with a review of the application's features and requirements.</span></span> <span data-ttu-id="00a6b-113">EShopOnContainers 應用程式代表銷售各種實體產品（例如 t 恤和咖啡馬克杯）的線上商店。</span><span class="sxs-lookup"><span data-stu-id="00a6b-113">The eShopOnContainers application represents an online store that sells various physical products like t-shirts and coffee mugs.</span></span> <span data-ttu-id="00a6b-114">如果您之前已在線上購買任何專案，使用存放區的體驗應該相當熟悉。</span><span class="sxs-lookup"><span data-stu-id="00a6b-114">If you've bought anything online before, the experience of using the store should be relatively familiar.</span></span> <span data-ttu-id="00a6b-115">以下是存放區所實行的一些基本功能：</span><span class="sxs-lookup"><span data-stu-id="00a6b-115">Here are some of the basic features the store implements:</span></span>

- <span data-ttu-id="00a6b-116">列出目錄專案</span><span class="sxs-lookup"><span data-stu-id="00a6b-116">List catalog items</span></span>
- <span data-ttu-id="00a6b-117">依類型篩選項目</span><span class="sxs-lookup"><span data-stu-id="00a6b-117">Filter items by type</span></span>
- <span data-ttu-id="00a6b-118">依品牌篩選項目</span><span class="sxs-lookup"><span data-stu-id="00a6b-118">Filter items by brand</span></span>
- <span data-ttu-id="00a6b-119">將專案新增至購物籃</span><span class="sxs-lookup"><span data-stu-id="00a6b-119">Add items to the shopping basket</span></span>
- <span data-ttu-id="00a6b-120">編輯或移除購物籃中的專案</span><span class="sxs-lookup"><span data-stu-id="00a6b-120">Edit or remove items from the basket</span></span>
- <span data-ttu-id="00a6b-121">準備</span><span class="sxs-lookup"><span data-stu-id="00a6b-121">Checkout</span></span>
- <span data-ttu-id="00a6b-122">註冊帳戶</span><span class="sxs-lookup"><span data-stu-id="00a6b-122">Register an account</span></span>
- <span data-ttu-id="00a6b-123">登入</span><span class="sxs-lookup"><span data-stu-id="00a6b-123">Sign in</span></span>
- <span data-ttu-id="00a6b-124">登出</span><span class="sxs-lookup"><span data-stu-id="00a6b-124">Sign out</span></span>
- <span data-ttu-id="00a6b-125">審查訂單</span><span class="sxs-lookup"><span data-stu-id="00a6b-125">Review orders</span></span>

<span data-ttu-id="00a6b-126">應用程式也具有下列非功能性需求：</span><span class="sxs-lookup"><span data-stu-id="00a6b-126">The application also has the following non-functional requirements:</span></span>

- <span data-ttu-id="00a6b-127">它必須具有高度可用性，而且必須自動調整以符合增加的流量（並在流量 contosoconcerthall 後相應減少）。</span><span class="sxs-lookup"><span data-stu-id="00a6b-127">It needs to be highly available and it must scale automatically to meet increased traffic (and scale back down once traffic subsides).</span></span> 
- <span data-ttu-id="00a6b-128">它應該提供容易使用的監視其健康情況和診斷記錄，以協助疑難排解其遇到的任何問題。</span><span class="sxs-lookup"><span data-stu-id="00a6b-128">It should provide easy-to-use monitoring of its health and diagnostic logs to help troubleshoot any issues it encounters.</span></span> 
- <span data-ttu-id="00a6b-129">它應該支援 agile 開發流程，包括支援持續整合和部署（CI/CD）。</span><span class="sxs-lookup"><span data-stu-id="00a6b-129">It should support an agile development process, including support for continuous integration and deployment (CI/CD).</span></span> 
- <span data-ttu-id="00a6b-130">除了兩個 web 前端（傳統和單頁應用程式）之外，應用程式也必須支援執行不同種類作業系統的行動用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="00a6b-130">In addition to the two web front ends (traditional and Single Page Application), the application must also support mobile client apps running different kinds of operating systems.</span></span> 
- <span data-ttu-id="00a6b-131">它應該支援跨平臺裝載和跨平臺開發。</span><span class="sxs-lookup"><span data-stu-id="00a6b-131">It should support cross-platform hosting and cross-platform development.</span></span>

![eShopOnContainers 參考應用程式開發架構。](./media/eshoponcontainers-development-architecture.png)

<span data-ttu-id="00a6b-133">**圖 2-2**。</span><span class="sxs-lookup"><span data-stu-id="00a6b-133">**Figure 2-2**.</span></span> <span data-ttu-id="00a6b-134">eShopOnContainers 參考應用程式開發架構。</span><span class="sxs-lookup"><span data-stu-id="00a6b-134">eShopOnContainers reference application development architecture.</span></span>

<span data-ttu-id="00a6b-135">EShopOnContainers 應用程式可從透過 HTTPS 存取應用程式的 web 或行動用戶端存取，其目標為 ASP.NET Core MVC 伺服器應用程式或適當的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="00a6b-135">The eShopOnContainers application is accessible from web or mobile clients that access the application over HTTPS targeting either the ASP.NET Core MVC server application or an appropriate API Gateway.</span></span> <span data-ttu-id="00a6b-136">API 閘道提供幾項優點，例如將後端服務與個別的前端用戶端分離，並提供更好的安全性。</span><span class="sxs-lookup"><span data-stu-id="00a6b-136">API Gateways offer several advantages, such as decoupling back-end services from individual front-end clients and providing better security.</span></span> <span data-ttu-id="00a6b-137">應用程式也會使用稱為後端前端（BFF）的相關模式，這會建議為每個前端用戶端建立個別的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="00a6b-137">The application also makes use of a related pattern known as Backends-for-Frontends (BFF), which recommends creating separate API gateways for each front-end client.</span></span> <span data-ttu-id="00a6b-138">參考架構會根據要求是否來自 web 或行動用戶端，來示範如何細分 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="00a6b-138">The reference architecture demonstrates breaking up the API gateways based on whether the request is coming from a web or mobile client.</span></span>

<span data-ttu-id="00a6b-139">應用程式的功能會分成多個不同的微服務。</span><span class="sxs-lookup"><span data-stu-id="00a6b-139">The application's functionality is broken up into a number of distinct microservices.</span></span> <span data-ttu-id="00a6b-140">有一些服務負責驗證和身分識別、列出產品目錄中的專案、管理使用者的購物籃，以及放置訂單。</span><span class="sxs-lookup"><span data-stu-id="00a6b-140">There are services responsible for authentication and identity, listing items from the product catalog, managing users' shopping baskets, and  placing orders.</span></span> <span data-ttu-id="00a6b-141">每個個別的服務都有自己的持續性儲存體。</span><span class="sxs-lookup"><span data-stu-id="00a6b-141">Each of these separate services has its own persistent storage.</span></span> <span data-ttu-id="00a6b-142">請注意，並非所有服務都有互動的單一主要資料存放區。</span><span class="sxs-lookup"><span data-stu-id="00a6b-142">Note that there's no single master data store with which all services interact.</span></span> <span data-ttu-id="00a6b-143">相反地，服務之間的協調和通訊是根據需要進行，並透過使用訊息匯流排來完成。</span><span class="sxs-lookup"><span data-stu-id="00a6b-143">Instead, coordination and communication between the services is done on an as-needed basis and through the use of a message bus.</span></span>

<span data-ttu-id="00a6b-144">每個不同的微服務都會根據其個別需求，以不同的方式設計。</span><span class="sxs-lookup"><span data-stu-id="00a6b-144">Each of the different microservices is designed differently, based on their individual requirements.</span></span> <span data-ttu-id="00a6b-145">這表示其技術堆疊可能不同，但它們都是使用 .NET Core 所建立，並專為雲端設計。</span><span class="sxs-lookup"><span data-stu-id="00a6b-145">This means their technology stack may differ, although they're all built using .NET Core and designed for the cloud.</span></span> <span data-ttu-id="00a6b-146">較簡單的服務提供基礎資料存放區的基本建立-讀取-更新-刪除（CRUD）存取，而更先進的服務則使用領域導向設計方法和模式來管理商務複雜度。</span><span class="sxs-lookup"><span data-stu-id="00a6b-146">Simpler services provide basic Create-Read-Update-Delete (CRUD) access to the underlying data stores, while more advanced services use Domain-Driven Design approaches and patterns to manage business complexity.</span></span>

![不同種類的微服務](./media/different-kinds-of-microservices.png)

<span data-ttu-id="00a6b-148">**圖 2-3**。</span><span class="sxs-lookup"><span data-stu-id="00a6b-148">**Figure 2-3**.</span></span> <span data-ttu-id="00a6b-149">不同種類的微服務。</span><span class="sxs-lookup"><span data-stu-id="00a6b-149">Different kinds of microservices.</span></span>

## <a name="overview-of-the-code"></a><span data-ttu-id="00a6b-150">程式碼的總覽</span><span class="sxs-lookup"><span data-stu-id="00a6b-150">Overview of the code</span></span>

<span data-ttu-id="00a6b-151">因為它會利用微服務，所以 eShopOnContainers 應用程式會在其 GitHub 存放庫中包含相當多的個別專案和解決方案。</span><span class="sxs-lookup"><span data-stu-id="00a6b-151">Because it leverages microservices, the eShopOnContainers app includes quite a few separate projects and solutions in its GitHub repository.</span></span> <span data-ttu-id="00a6b-152">除了個別的解決方案和可執行檔，各種服務都設計成在本機開發期間和生產環境中的執行時間，于自己的容器內執行。</span><span class="sxs-lookup"><span data-stu-id="00a6b-152">In addition to separate solutions and executable files, the various services are designed to run inside their own containers, both during local development and at runtime in production.</span></span> <span data-ttu-id="00a6b-153">圖2-4 顯示完整的 Visual Studio 方案，其中會組織各種不同的專案。</span><span class="sxs-lookup"><span data-stu-id="00a6b-153">Figure 2-4 shows the full Visual Studio solution, in which the various different projects are organized.</span></span>

![Visual Studio 方案中的專案。](./media/projects-in-visual-studio-solution.png)

<span data-ttu-id="00a6b-155">**圖 2-4**：</span><span class="sxs-lookup"><span data-stu-id="00a6b-155">**Figure 2-4**.</span></span> <span data-ttu-id="00a6b-156">Visual Studio 方案中的專案。</span><span class="sxs-lookup"><span data-stu-id="00a6b-156">Projects in Visual Studio solution.</span></span>

<span data-ttu-id="00a6b-157">程式碼會組織成支援不同的微服務，而在每個微服務中，程式碼會細分為領域邏輯、基礎結構考慮，以及使用者介面或服務端點。</span><span class="sxs-lookup"><span data-stu-id="00a6b-157">The code is organized to support the different microservices, and within each microservice, the code is broken up into domain logic, infrastructure concerns, and user interface or service endpoint.</span></span> <span data-ttu-id="00a6b-158">在許多情況下，Azure 服務會在生產環境中滿足每個服務的相依性，以及用於本機開發的替代選項。</span><span class="sxs-lookup"><span data-stu-id="00a6b-158">In many cases, each service's dependencies can be fulfilled by Azure services in production, as well as alternative options for local development.</span></span> <span data-ttu-id="00a6b-159">讓我們來檢查應用程式的需求如何對應至 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="00a6b-159">Let's examine how the application's requirements map to Azure services.</span></span>

## <a name="understanding-microservices"></a><span data-ttu-id="00a6b-160">瞭解微服務</span><span class="sxs-lookup"><span data-stu-id="00a6b-160">Understanding microservices</span></span>

<span data-ttu-id="00a6b-161">本書著重在使用 Azure 技術建立的雲端原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="00a6b-161">This book focuses on cloud-native applications built using Azure technology.</span></span> <span data-ttu-id="00a6b-162">若要深入瞭解微服務的最佳做法，以及如何架構微服務型應用程式，請閱讀隨附書[，.net 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/learn/aspnet/microservices-architecture)。</span><span class="sxs-lookup"><span data-stu-id="00a6b-162">To learn more about microservices best practices and how to architect microservice-based applications, read the companion book, [.NET Microservices: Architecture for Containerized .NET Applications](https://dotnet.microsoft.com/learn/aspnet/microservices-architecture).</span></span> <span data-ttu-id="00a6b-163">本書可從線上、PDF 或 eReader 格式取得。</span><span class="sxs-lookup"><span data-stu-id="00a6b-163">The book is available online, in PDF, or eReader formats.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00a6b-164">[上一頁](candidate-apps.md)
>[下一頁](map-eshoponcontainers-azure-services.md)</span><span class="sxs-lookup"><span data-stu-id="00a6b-164">[Previous](candidate-apps.md)
[Next](map-eshoponcontainers-azure-services.md)</span></span>
