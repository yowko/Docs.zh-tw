---
title: 架構方法-無伺服器應用程式
description: 介紹用來建立雲端式企業應用程式的架構方法, 從多層式架構到無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ee529abd1f6955d4f542464dd9a2380dd663571f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577801"
---
# <a name="architecture-approaches"></a><span data-ttu-id="9bb7a-103">架構方法</span><span class="sxs-lookup"><span data-stu-id="9bb7a-103">Architecture approaches</span></span>

<span data-ttu-id="9bb7a-104">瞭解架構企業應用程式的現有方法, 有助於澄清無伺服器所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="9bb7a-105">有許多方法和模式在多年來的軟體發展演變, 而且全都有自己的優缺點。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="9bb7a-106">在許多情況下, 最終的解決方案可能不需要決定單一方法, 但可能會整合數種方法。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="9bb7a-107">遷移案例通常需要透過混合式方法, 從一個架構方法轉移到另一個。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="9bb7a-108">本章提供企業應用程式的邏輯和實體架構模式的總覽。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="9bb7a-109">架構模式</span><span class="sxs-lookup"><span data-stu-id="9bb7a-109">Architecture patterns</span></span>

<span data-ttu-id="9bb7a-110">現代化商務應用程式會遵循各種不同的架構模式。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="9bb7a-111">本章節代表常見模式的問卷調查。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="9bb7a-112">此處所列的模式不一定都是最佳作法, 而是說明不同的方法。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="9bb7a-113">如需詳細資訊, 請參閱[Azure 應用程式架構指南](https://docs.microsoft.com/azure/architecture/guide/)。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="9bb7a-114">是開化「</span><span class="sxs-lookup"><span data-stu-id="9bb7a-114">Monoliths</span></span>

<span data-ttu-id="9bb7a-115">許多商務應用程式都遵循單體模式。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="9bb7a-116">繼承應用程式通常會實作為是開化「。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="9bb7a-117">在單體模式中, 所有應用程式的顧慮都包含在單一部署中。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="9bb7a-118">從使用者介面到資料庫呼叫的所有內容都包含在相同的程式碼基底中。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![單體架構](./media/monolith-architecture.png)

<span data-ttu-id="9bb7a-120">單體方法有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="9bb7a-121">您通常可以輕鬆地拉出單一程式碼基底並開始工作。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="9bb7a-122">增加時間可能較少, 而建立測試環境就像提供新的複本一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="9bb7a-123">單體可以設計成包含多個元件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="9bb7a-124">可惜的是, 單體模式傾向于大規模細分。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="9bb7a-125">單體方法的主要缺點包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-125">Major disadvantages of the monolith approach include:</span></span>

* <span data-ttu-id="9bb7a-126">很容易在相同的程式碼基底中平行處理。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-126">Difficult to work in parallel in the same code base.</span></span>
* <span data-ttu-id="9bb7a-127">無論是什麼簡單的變更, 都需要部署整個應用程式的新版本。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
* <span data-ttu-id="9bb7a-128">重構可能會影響整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-128">Refactoring potentially impacts the entire application.</span></span>
* <span data-ttu-id="9bb7a-129">通常唯一能夠進行調整的解決方案, 是建立多個耗用大量資源的單體複本。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
* <span data-ttu-id="9bb7a-130">隨著系統擴展或其他系統的取得, 整合可能會很棘手。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
* <span data-ttu-id="9bb7a-131">因為需要設定整個單體, 所以可能很難以進行測試。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
* <span data-ttu-id="9bb7a-132">重複使用程式碼是一項挑戰, 而其他應用程式通常都有自己的程式碼複本。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="9bb7a-133">許多企業都有機會遷移單體應用程式, 同時將其重構為更多可用的模式。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="9bb7a-134">將個別的應用程式和元件分開加以維護、部署和調整, 是很常見的。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="9bb7a-135">多層式應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb7a-135">N-Layer applications</span></span>

<span data-ttu-id="9bb7a-136">多層式應用程式會將應用程式邏輯分割成特定層。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="9bb7a-137">最常見的層級包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-137">The most common layers include:</span></span>

* <span data-ttu-id="9bb7a-138">使用者介面</span><span class="sxs-lookup"><span data-stu-id="9bb7a-138">User interface</span></span>
* <span data-ttu-id="9bb7a-139">商務邏輯</span><span class="sxs-lookup"><span data-stu-id="9bb7a-139">Business logic</span></span>
* <span data-ttu-id="9bb7a-140">資料存取</span><span class="sxs-lookup"><span data-stu-id="9bb7a-140">Data access</span></span>

<span data-ttu-id="9bb7a-141">其他層可能包括中介軟體、批次處理和 API。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="9bb7a-142">請務必注意, 圖層是邏輯的。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="9bb7a-143">雖然它們是以隔離的方式開發, 但它們可能會部署到相同的目標平臺。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![多層式架構](./media/n-layer-architecture.png)

<span data-ttu-id="9bb7a-145">N 層式方法有幾個優點, 包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-145">There are several advantages to the N-Layer approach, including:</span></span>

* <span data-ttu-id="9bb7a-146">重構會隔離到圖層。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-146">Refactoring is isolated to a layer.</span></span>
* <span data-ttu-id="9bb7a-147">小組可以獨立建立、測試、部署和維護個別的層級。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
* <span data-ttu-id="9bb7a-148">層可以交換, 例如, 資料層可能會存取多個資料庫, 而不需要變更 UI 層。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="9bb7a-149">無伺服器可能用來執行一或多個層級。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="9bb7a-150">微服務</span><span class="sxs-lookup"><span data-stu-id="9bb7a-150">Microservices</span></span>

<span data-ttu-id="9bb7a-151">**[微服務](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** 架構包含常見的特性, 包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

* <span data-ttu-id="9bb7a-152">應用程式是由數個小型服務所組成。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-152">Applications are composed of several small services.</span></span>
* <span data-ttu-id="9bb7a-153">每個服務都會在自己的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-153">Each service runs in its own process.</span></span>
* <span data-ttu-id="9bb7a-154">服務會以商務網域為准。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-154">Services are aligned around business domains.</span></span>
* <span data-ttu-id="9bb7a-155">服務會透過輕量 Api 進行通訊, 通常會使用 HTTP 做為傳輸。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
* <span data-ttu-id="9bb7a-156">服務可以獨立部署及升級。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-156">Services can be deployed and upgraded independently.</span></span>
* <span data-ttu-id="9bb7a-157">服務不依存于單一資料存放區。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-157">Services aren't dependent on a single data store.</span></span>
* <span data-ttu-id="9bb7a-158">系統的設計會導致失敗, 而且即使特定服務失敗, 應用程式仍會執行。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="9bb7a-159">微服務不一定要與其他架構方法互斥。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="9bb7a-160">例如, 多層式架構可能會使用微服務作為仲介層。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="9bb7a-161">您也可以透過各種方式來執行微服務, 從 IIS 主機上的虛擬目錄到容器。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="9bb7a-162">微服務的特性讓它們特別適用于無伺服器的實施。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![微服務架構](./media/microservices-architecture.png)

<span data-ttu-id="9bb7a-164">微服務架構的優點包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-164">The pros of microservices architectures include:</span></span>

* <span data-ttu-id="9bb7a-165">重構通常會隔離到單一服務。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-165">Refactoring is often isolated to a single service.</span></span>
* <span data-ttu-id="9bb7a-166">服務可以彼此獨立進行升級。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-166">Services can be upgraded independently of each other.</span></span>
* <span data-ttu-id="9bb7a-167">復原和彈性可以調整為個別服務的需求。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
* <span data-ttu-id="9bb7a-168">開發可能會在不同的小組和平臺上平行進行。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-168">Development can happen in parallel across disparate teams and platforms.</span></span>
* <span data-ttu-id="9bb7a-169">撰寫隔離服務的完整測試比較容易。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="9bb7a-170">微服務帶來自己的挑戰, 包括:</span><span class="sxs-lookup"><span data-stu-id="9bb7a-170">Microservices come with their own challenges, including:</span></span>

* <span data-ttu-id="9bb7a-171">判斷哪些服務可供使用, 以及如何呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-171">Determining what services are available and how to call them.</span></span>
* <span data-ttu-id="9bb7a-172">管理服務的生命週期。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-172">Managing the lifecycle of services.</span></span>
* <span data-ttu-id="9bb7a-173">瞭解服務如何在整體應用程式中彼此配合。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-173">Understanding how services fit together in the overall application.</span></span>
* <span data-ttu-id="9bb7a-174">跨不同服務進行之呼叫的完整系統測試。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="9bb7a-175">最後有解決所有這些挑戰的解決方案, 包括進一步探討無伺服器的優勢。</span><span class="sxs-lookup"><span data-stu-id="9bb7a-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9bb7a-176">[上一頁](index.md)
>[下一頁](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="9bb7a-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
