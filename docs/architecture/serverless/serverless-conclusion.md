---
title: 重要的結論-無伺服器應用程式
description: 無伺服器提供許多優點, 而且有自己的挑戰。 本指南的重要結論摘要。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ae9fc47bf07a7e28688942b856b4743ae7aadc36
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577241"
---
# <a name="conclusion"></a><span data-ttu-id="3e39a-104">結論</span><span class="sxs-lookup"><span data-stu-id="3e39a-104">Conclusion</span></span>

<span data-ttu-id="3e39a-105">下列重要的是本指南中最重要的結論。</span><span class="sxs-lookup"><span data-stu-id="3e39a-105">The following key takeaways are the most important conclusions from this guide.</span></span>

<span data-ttu-id="3e39a-106">**使用無伺服器的優點。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-106">**Benefits of using serverless.**</span></span> <span data-ttu-id="3e39a-107">無伺服器解決方案提供節省成本的重要優點, 因為無伺服器是以每次使用付費的模式來執行。</span><span class="sxs-lookup"><span data-stu-id="3e39a-107">Serverless solutions provide the important benefit of cost savings because serverless is implemented in a pay-per-use model.</span></span> <span data-ttu-id="3e39a-108">無伺服器可獨立調整、測試及部署應用程式的個別元件。</span><span class="sxs-lookup"><span data-stu-id="3e39a-108">Serverless makes it possible to independently scale, test, and deploy individual components of your application.</span></span> <span data-ttu-id="3e39a-109">無伺服器唯一適合用來執行微服務架構, 並完全整合到 DevOps 管線中。</span><span class="sxs-lookup"><span data-stu-id="3e39a-109">Serverless is uniquely suited to implement microservices architectures and integrates fully into a DevOps pipeline.</span></span>

<span data-ttu-id="3e39a-110">**以部署的單位撰寫程式碼。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-110">**Code as a unit of deployment.**</span></span> <span data-ttu-id="3e39a-111">無伺服器會將硬體、作業系統和執行時間抽象化, 使其遠離應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e39a-111">Serverless abstracts the hardware, OS, and runtime away from the application.</span></span> <span data-ttu-id="3e39a-112">無伺服器可讓您專注于程式碼中的商務邏輯, 作為部署的單位。</span><span class="sxs-lookup"><span data-stu-id="3e39a-112">Serverless enables focusing on business logic in code as the unit of deployment.</span></span>

<span data-ttu-id="3e39a-113">**觸發程式和系結。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-113">**Triggers and bindings.**</span></span> <span data-ttu-id="3e39a-114">無伺服器與儲存體、Api 和其他雲端資源的整合。</span><span class="sxs-lookup"><span data-stu-id="3e39a-114">Serverless eases integration with storage, APIs, and other cloud resources.</span></span> <span data-ttu-id="3e39a-115">Azure Functions 提供觸發程式來執行程式碼和系結, 以與資源互動。</span><span class="sxs-lookup"><span data-stu-id="3e39a-115">Azure Functions provides triggers to execute code and bindings to interact with resources.</span></span>

<span data-ttu-id="3e39a-116">**微服務。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-116">**Microservices.**</span></span> <span data-ttu-id="3e39a-117">針對以自發服務形式的多個獨立子系統為基礎的分散式和大型或複雜任務關鍵性應用程式, 微服務架構會成為慣用的方法。</span><span class="sxs-lookup"><span data-stu-id="3e39a-117">The microservices architecture is becoming the preferred approach for distributed and large or complex mission-critical applications that are based on multiple independent subsystems in the form of autonomous services.</span></span> <span data-ttu-id="3e39a-118">在以微服務為基礎的架構中, 應用程式會建立為可獨立開發、測試、設定版本、部署及調整規模的服務集合。</span><span class="sxs-lookup"><span data-stu-id="3e39a-118">In a microservice-based architecture, the application is built as a collection of services that can be developed, tested, versioned, deployed, and scaled independently.</span></span> <span data-ttu-id="3e39a-119">無伺服器是非常適合用來建立這些服務的架構。</span><span class="sxs-lookup"><span data-stu-id="3e39a-119">Serverless is an architecture well-suited for building these services.</span></span>

<span data-ttu-id="3e39a-120">**無伺服器平臺。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-120">**Serverless platforms.**</span></span> <span data-ttu-id="3e39a-121">無伺服器與程式碼無關。</span><span class="sxs-lookup"><span data-stu-id="3e39a-121">Serverless isn't just about the code.</span></span> <span data-ttu-id="3e39a-122">支援無伺服器架構的平臺包括無伺服器工作流程和協調流程、無伺服器訊息和事件服務, 以及無伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e39a-122">Platforms that support serverless architectures include serverless workflows and orchestration, serverless messaging and event services, and serverless databases.</span></span>

<span data-ttu-id="3e39a-123">**無伺服器挑戰。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-123">**Serverless challenges.**</span></span> <span data-ttu-id="3e39a-124">無伺服器引進分散式應用程式開發的相關挑戰, 例如分散和獨立的資料模型、復原、版本控制和服務探索。</span><span class="sxs-lookup"><span data-stu-id="3e39a-124">Serverless introduces challenges related to distributed application development, such as fragmented and independent data models, resiliency, versioning, and service discovery.</span></span> <span data-ttu-id="3e39a-125">無伺服器可能不適合長時間執行的進程或元件, 而受益于更緊密的結合。</span><span class="sxs-lookup"><span data-stu-id="3e39a-125">Serverless may not be ideally suited to long running processes or components that benefit from tighter coupling.</span></span>

<span data-ttu-id="3e39a-126">**無伺服器的工具, 而不是工具箱。**</span><span class="sxs-lookup"><span data-stu-id="3e39a-126">**Serverless as a tool, not the toolbox.**</span></span> <span data-ttu-id="3e39a-127">無伺服器是應用程式架構專屬的解決方案。</span><span class="sxs-lookup"><span data-stu-id="3e39a-127">Serverless is not the exclusive solution to application architecture.</span></span> <span data-ttu-id="3e39a-128">這項工具可作為混合式應用程式的一部分, 其中可能包含傳統層、單體後端和容器。</span><span class="sxs-lookup"><span data-stu-id="3e39a-128">It is a tool that can be leveraged as part of a hybrid application that may contain traditional tiers, monolith back ends, and containers.</span></span> <span data-ttu-id="3e39a-129">無伺服器可用來增強現有的解決方案, 而不是應用程式開發的全部或無一種方法。</span><span class="sxs-lookup"><span data-stu-id="3e39a-129">Serverless can be used to enhance existing solutions and is not an all-or-nothing approach to application development.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="3e39a-130">上一步</span><span class="sxs-lookup"><span data-stu-id="3e39a-130">Previous</span></span>](serverless-business-scenarios.md)
