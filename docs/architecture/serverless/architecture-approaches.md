---
title: 架構方法 - 無伺服器應用
description: 構建基於雲的企業應用程式的體系結構方法簡介，從 N 層體系結構到無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522893"
---
# <a name="architecture-approaches"></a><span data-ttu-id="7d7e1-103">架構方法</span><span class="sxs-lookup"><span data-stu-id="7d7e1-103">Architecture approaches</span></span>

<span data-ttu-id="7d7e1-104">瞭解構建企業應用的現有方法有助於闡明無伺服器應用所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="7d7e1-105">有許多方法和模式在數十年的軟體發展中有所發展，它們都有各自的優缺點。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="7d7e1-106">在許多情況下，最終解決方案可能並不涉及決定單一方法，但可能集成了幾種方法。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="7d7e1-107">遷移方案通常涉及通過混合方法從一種體系結構方法轉移到另一種體系結構方法。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="7d7e1-108">本章概述了企業應用程式的邏輯和物理體系結構模式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="7d7e1-109">架構模式</span><span class="sxs-lookup"><span data-stu-id="7d7e1-109">Architecture patterns</span></span>

<span data-ttu-id="7d7e1-110">現代商務應用程式遵循各種體系結構模式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="7d7e1-111">本節表示對常見模式的調查。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="7d7e1-112">此處列出的模式不一定是所有最佳實踐，但說明了不同的方法。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="7d7e1-113">有關詳細資訊，請參閱[Azure 應用程式體系結構指南](https://docs.microsoft.com/azure/architecture/guide/)。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="7d7e1-114">單體</span><span class="sxs-lookup"><span data-stu-id="7d7e1-114">Monoliths</span></span>

<span data-ttu-id="7d7e1-115">許多商務應用程式遵循單一模式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="7d7e1-116">繼承應用程式通常作為整體實現。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="7d7e1-117">在單一模式中，所有應用程式問題都包含在單個部署中。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="7d7e1-118">從使用者介面到資料庫調用的所有內容都包含在相同的代碼庫中。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![單體架構](./media/monolith-architecture.png)

<span data-ttu-id="7d7e1-120">單體方法有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="7d7e1-121">通常很容易拉下單個代碼庫並開始工作。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="7d7e1-122">增加時間可能更少，創建測試環境就像提供新副本一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="7d7e1-123">單體可設計為包括多個元件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="7d7e1-124">不幸的是，單體圖案往往在比例上分解。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="7d7e1-125">單體方法的主要缺點包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="7d7e1-126">在同一代碼庫中難以並行工作。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="7d7e1-127">任何更改（無論多麼微不足道）都需要部署整個應用程式的新版本。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="7d7e1-128">重構可能會影響整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="7d7e1-129">通常，要擴展的唯一解決方案是創建單體的多個資源密集型副本。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="7d7e1-130">隨著系統擴展或獲取其他系統，集成可能很困難。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="7d7e1-131">由於需要配置整個單體，因此可能很難進行測試。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="7d7e1-132">代碼重用具有挑戰性，其他應用通常最終擁有自己的代碼副本。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="7d7e1-133">許多企業將雲視為遷移單體應用程式的機會，同時將它們重構到更可用的模式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="7d7e1-134">通常分解各個應用程式和元件，以允許它們單獨維護、部署和縮放。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="7d7e1-135">N 層應用</span><span class="sxs-lookup"><span data-stu-id="7d7e1-135">N-Layer applications</span></span>

<span data-ttu-id="7d7e1-136">N 層應用程式將應用程式邏輯分區到特定層中。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="7d7e1-137">最常見的圖層包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-137">The most common layers include:</span></span>

- <span data-ttu-id="7d7e1-138">使用者介面</span><span class="sxs-lookup"><span data-stu-id="7d7e1-138">User interface</span></span>
- <span data-ttu-id="7d7e1-139">商務邏輯</span><span class="sxs-lookup"><span data-stu-id="7d7e1-139">Business logic</span></span>
- <span data-ttu-id="7d7e1-140">資料存取</span><span class="sxs-lookup"><span data-stu-id="7d7e1-140">Data access</span></span>

<span data-ttu-id="7d7e1-141">其他層可能包括中介軟體、批次處理和 API。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="7d7e1-142">請務必注意圖層是合乎邏輯的。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="7d7e1-143">儘管它們是單獨開發的，但它們都可以部署到同一目標平臺。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N 層架構](./media/n-layer-architecture.png)

<span data-ttu-id="7d7e1-145">N 層方法有幾個優點，包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="7d7e1-146">重構被隔離到圖層。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="7d7e1-147">團隊可以獨立構建、測試、部署和維護單獨的圖層。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="7d7e1-148">可以換出圖層，例如，資料層可以訪問多個資料庫，而無需更改 UI 層。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="7d7e1-149">無伺服器可用於實現一個或多個圖層。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="7d7e1-150">微服務</span><span class="sxs-lookup"><span data-stu-id="7d7e1-150">Microservices</span></span>

<span data-ttu-id="7d7e1-151">**[微服務](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** 體系結構包含一些常見特徵，包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="7d7e1-152">應用程式由幾個小型服務組成。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="7d7e1-153">每個服務在其自己的進程中運行。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="7d7e1-154">服務在業務域周圍對齊。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="7d7e1-155">服務通過羽量級 API 進行通信，通常使用 HTTP 作為傳輸。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="7d7e1-156">服務可以獨立部署和升級。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="7d7e1-157">服務不依賴于單個資料存儲。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="7d7e1-158">系統的設計考慮到了故障，即使某些服務發生故障，應用仍可能繼續運行。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="7d7e1-159">微服務不必與其他體系結構方法相互排斥。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="7d7e1-160">例如，N-Tier 體系結構可能為中介層使用微服務。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="7d7e1-161">還可以以各種方式實現微服務，從 IIS 主機上的虛擬目錄到容器。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="7d7e1-162">微服務的特點使它們特別適合無伺服器實現。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![微服務架構](./media/microservices-architecture.png)

<span data-ttu-id="7d7e1-164">微服務體系結構的優點包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="7d7e1-165">重構通常與單個服務隔離。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="7d7e1-166">服務可以相互獨立升級。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="7d7e1-167">彈性和彈性可以調整到各個服務的需求。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="7d7e1-168">跨不同的團隊和平臺並行開發。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="7d7e1-169">為隔離服務編寫全面測試更容易。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="7d7e1-170">微服務也面臨自身挑戰，包括：</span><span class="sxs-lookup"><span data-stu-id="7d7e1-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="7d7e1-171">確定可用的服務以及如何調用它們。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="7d7e1-172">管理服務的生命週期。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="7d7e1-173">瞭解服務如何結合整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="7d7e1-174">跨不同服務進行的呼叫的完整系統測試。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="7d7e1-175">最終，有解決方案可以解決所有這些挑戰，包括利用後面討論的無伺服器優勢。</span><span class="sxs-lookup"><span data-stu-id="7d7e1-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7d7e1-176">[上一個](index.md)
>[下一個](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="7d7e1-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
