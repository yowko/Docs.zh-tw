---
title: 架構方法-無伺服器應用程式
description: 介紹建立雲端式企業應用程式的架構方法，從多層式架構到無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 0ab84d1f3425c1fda787756b73fd8315fe6d4231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171971"
---
# <a name="architecture-approaches"></a><span data-ttu-id="d6d54-103">架構方法</span><span class="sxs-lookup"><span data-stu-id="d6d54-103">Architecture approaches</span></span>

<span data-ttu-id="d6d54-104">瞭解架構企業應用程式的現有方法有助於說明無伺服器所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="d6d54-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="d6d54-105">在數十年的軟體發展中，有許多方法和模式都有發展，而且全都有自己的優缺點。</span><span class="sxs-lookup"><span data-stu-id="d6d54-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="d6d54-106">在許多情況下，終極解決方案可能不需要決定單一方法，但可能會整合數個方法。</span><span class="sxs-lookup"><span data-stu-id="d6d54-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="d6d54-107">遷移案例通常會牽涉到透過混合式方法，從某個架構的方法轉移到另一個架構。</span><span class="sxs-lookup"><span data-stu-id="d6d54-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="d6d54-108">本章概要說明企業應用程式的邏輯與實體架構模式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="d6d54-109">架構模式</span><span class="sxs-lookup"><span data-stu-id="d6d54-109">Architecture patterns</span></span>

<span data-ttu-id="d6d54-110">新式商務應用程式遵循各種不同的架構模式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="d6d54-111">本節代表一般模式的問卷。</span><span class="sxs-lookup"><span data-stu-id="d6d54-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="d6d54-112">此處所列的模式不一定都是最佳作法，而是說明不同的方法。</span><span class="sxs-lookup"><span data-stu-id="d6d54-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="d6d54-113">如需詳細資訊，請參閱 [Azure 應用程式架構指南](/azure/architecture/guide/)。</span><span class="sxs-lookup"><span data-stu-id="d6d54-113">For more information, see [Azure application architecture guide](/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="d6d54-114">是開化</span><span class="sxs-lookup"><span data-stu-id="d6d54-114">Monoliths</span></span>

<span data-ttu-id="d6d54-115">許多商務應用程式都遵循單體模式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="d6d54-116">繼承應用程式通常會實作為是開化。</span><span class="sxs-lookup"><span data-stu-id="d6d54-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="d6d54-117">在單體模式中，所有應用程式考慮都包含在單一部署中。</span><span class="sxs-lookup"><span data-stu-id="d6d54-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="d6d54-118">從使用者介面到資料庫呼叫的所有專案都包含在相同的程式碼基底中。</span><span class="sxs-lookup"><span data-stu-id="d6d54-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![單體架構](./media/monolith-architecture.png)

<span data-ttu-id="d6d54-120">單體方法有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="d6d54-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="d6d54-121">通常很容易就能提取單一程式碼基底並開始運作。</span><span class="sxs-lookup"><span data-stu-id="d6d54-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="d6d54-122">遞增時間可能較少，而建立測試環境就像提供新的複本一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="d6d54-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="d6d54-123">單體可能是設計來包含多個元件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="d6d54-124">可惜的是，單體模式常常會大規模細分。</span><span class="sxs-lookup"><span data-stu-id="d6d54-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="d6d54-125">單體方法的主要缺點包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="d6d54-126">很難在相同的程式碼基底中平行處理。</span><span class="sxs-lookup"><span data-stu-id="d6d54-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="d6d54-127">無論多麼簡單，任何變更都需要部署整個應用程式的新版本。</span><span class="sxs-lookup"><span data-stu-id="d6d54-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="d6d54-128">重構可能會影響整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="d6d54-129">唯一要調整的解決方案通常是建立多個耗用大量資源的單體複本。</span><span class="sxs-lookup"><span data-stu-id="d6d54-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="d6d54-130">當系統擴展或取得其他系統時，整合可能很困難。</span><span class="sxs-lookup"><span data-stu-id="d6d54-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="d6d54-131">由於需要設定整個單體，因此可能很難進行測試。</span><span class="sxs-lookup"><span data-stu-id="d6d54-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="d6d54-132">重複使用程式碼是一項挑戰，而其他應用程式最終會有自己的程式碼複本。</span><span class="sxs-lookup"><span data-stu-id="d6d54-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="d6d54-133">許多企業都希望雲端成為遷移單體應用程式的機會，同時將其重構為更有用的模式。</span><span class="sxs-lookup"><span data-stu-id="d6d54-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="d6d54-134">通常會中斷個別的應用程式和元件，讓它們能夠分別進行維護、部署及調整。</span><span class="sxs-lookup"><span data-stu-id="d6d54-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="d6d54-135">多層式應用程式</span><span class="sxs-lookup"><span data-stu-id="d6d54-135">N-Layer applications</span></span>

<span data-ttu-id="d6d54-136">多層式應用程式分割應用程式邏輯分成特定層。</span><span class="sxs-lookup"><span data-stu-id="d6d54-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="d6d54-137">最常見的層包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-137">The most common layers include:</span></span>

- <span data-ttu-id="d6d54-138">使用者介面</span><span class="sxs-lookup"><span data-stu-id="d6d54-138">User interface</span></span>
- <span data-ttu-id="d6d54-139">商務邏輯</span><span class="sxs-lookup"><span data-stu-id="d6d54-139">Business logic</span></span>
- <span data-ttu-id="d6d54-140">資料存取</span><span class="sxs-lookup"><span data-stu-id="d6d54-140">Data access</span></span>

<span data-ttu-id="d6d54-141">其他層可能包括中介軟體、批次處理和 API。</span><span class="sxs-lookup"><span data-stu-id="d6d54-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="d6d54-142">請務必注意，圖層是邏輯的。</span><span class="sxs-lookup"><span data-stu-id="d6d54-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="d6d54-143">雖然它們是以隔離方式開發，但它們可能全都部署到相同的目標平臺。</span><span class="sxs-lookup"><span data-stu-id="d6d54-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N 層架構](./media/n-layer-architecture.png)

<span data-ttu-id="d6d54-145">多層式方法有幾個優點，包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="d6d54-146">重構會隔離到圖層。</span><span class="sxs-lookup"><span data-stu-id="d6d54-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="d6d54-147">小組可以獨立建立、測試、部署及維護不同的層級。</span><span class="sxs-lookup"><span data-stu-id="d6d54-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="d6d54-148">圖層可以交換，例如資料層可能會存取多個資料庫，而不需要變更 UI 層。</span><span class="sxs-lookup"><span data-stu-id="d6d54-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="d6d54-149">無伺服器可用來執行一或多個層級。</span><span class="sxs-lookup"><span data-stu-id="d6d54-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="d6d54-150">微服務</span><span class="sxs-lookup"><span data-stu-id="d6d54-150">Microservices</span></span>

<span data-ttu-id="d6d54-151">**[微服務](/azure/architecture/guide/architecture-styles/microservices)** 架構包含一般特性，包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-151">**[Microservices](/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="d6d54-152">應用程式是由數個小型服務所組成。</span><span class="sxs-lookup"><span data-stu-id="d6d54-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="d6d54-153">每個服務會在自己的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="d6d54-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="d6d54-154">服務會在商務網域方面保持一致。</span><span class="sxs-lookup"><span data-stu-id="d6d54-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="d6d54-155">服務會透過輕量 Api 進行通訊，通常會使用 HTTP 做為傳輸。</span><span class="sxs-lookup"><span data-stu-id="d6d54-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="d6d54-156">服務可以獨立部署和升級。</span><span class="sxs-lookup"><span data-stu-id="d6d54-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="d6d54-157">服務不會相依于單一資料存放區。</span><span class="sxs-lookup"><span data-stu-id="d6d54-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="d6d54-158">系統已設計為失敗，而且即使特定服務失敗，應用程式仍然可以執行。</span><span class="sxs-lookup"><span data-stu-id="d6d54-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="d6d54-159">微服務不必與其他架構方法互相排斥。</span><span class="sxs-lookup"><span data-stu-id="d6d54-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="d6d54-160">例如，多層式架構可將微服務用於中介層。</span><span class="sxs-lookup"><span data-stu-id="d6d54-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="d6d54-161">您也可以透過各種方式來執行微服務，從 IIS 主機上的虛擬目錄到容器。</span><span class="sxs-lookup"><span data-stu-id="d6d54-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="d6d54-162">微服務的特性讓它們特別適用于無伺服器的執行。</span><span class="sxs-lookup"><span data-stu-id="d6d54-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![微服務架構](./media/microservices-architecture.png)

<span data-ttu-id="d6d54-164">微服務架構的優點包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="d6d54-165">重構通常會隔離到單一服務。</span><span class="sxs-lookup"><span data-stu-id="d6d54-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="d6d54-166">服務可以獨立升級。</span><span class="sxs-lookup"><span data-stu-id="d6d54-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="d6d54-167">復原能力和彈性可以調整為個別服務的需求。</span><span class="sxs-lookup"><span data-stu-id="d6d54-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="d6d54-168">開發可以跨不同的小組和平臺平行發生。</span><span class="sxs-lookup"><span data-stu-id="d6d54-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="d6d54-169">您可以更輕鬆地為隔離的服務撰寫全方位的測試。</span><span class="sxs-lookup"><span data-stu-id="d6d54-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="d6d54-170">微服務帶來自己的挑戰，包括：</span><span class="sxs-lookup"><span data-stu-id="d6d54-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="d6d54-171">判斷有哪些服務可供使用，以及如何呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="d6d54-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="d6d54-172">管理服務的生命週期。</span><span class="sxs-lookup"><span data-stu-id="d6d54-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="d6d54-173">瞭解服務如何在整體應用程式中彼此配合。</span><span class="sxs-lookup"><span data-stu-id="d6d54-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="d6d54-174">跨不同服務進行之呼叫的完整系統測試。</span><span class="sxs-lookup"><span data-stu-id="d6d54-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="d6d54-175">最後還有解決這些挑戰的解決方案，包括利用稍後討論之無伺服器的優點。</span><span class="sxs-lookup"><span data-stu-id="d6d54-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d6d54-176">[上一個](index.md) 
>[下一步](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="d6d54-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
