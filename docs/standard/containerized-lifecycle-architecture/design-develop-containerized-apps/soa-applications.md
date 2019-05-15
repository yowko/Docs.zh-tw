---
title: SOA 應用程式
description: 請記住容器也可以是 SOA 應用程式的實用的部署選項。
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644754"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="53a33-103">服務導向應用程式</span><span class="sxs-lookup"><span data-stu-id="53a33-103">Service-oriented applications</span></span>

<span data-ttu-id="53a33-104">服務導向架構 (SOA) 是過度使用的詞彙，適合許多不同的因素，對不同的人。</span><span class="sxs-lookup"><span data-stu-id="53a33-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="53a33-105">但作為共同點，SOA 表示您藉由將它分解成 （通常為 HTTP 服務） 可以分類在不同的類型，例如子系統中，或在其他情況下，為層級的數個服務建構您的應用程式的架構。</span><span class="sxs-lookup"><span data-stu-id="53a33-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="53a33-106">現在，您可以部署這些服務以解決部署相關的問題，因為所有的相依性會包含在容器映像的 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="53a33-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="53a33-107">但是，當您需要相應放大 soa 都極為，您可能會遇到挑戰，如果您要部署根據的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="53a33-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="53a33-108">使用 Docker 叢集軟體或協調器可以處理這項挑戰。</span><span class="sxs-lookup"><span data-stu-id="53a33-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="53a33-109">當我們將探討微服務方法時，我們將探討下一節更詳細的協調器。</span><span class="sxs-lookup"><span data-stu-id="53a33-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="53a33-110">Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。</span><span class="sxs-lookup"><span data-stu-id="53a33-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="53a33-111">在一天結束時，容器叢集解決方案都適用於這兩種傳統的 SOA 架構以及更進階的微服務架構，在其中每個微服務擁有其資料模型。</span><span class="sxs-lookup"><span data-stu-id="53a33-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="53a33-112">多虧有多個資料庫，您也可以相應放大資料層，而不是使用由 SOA 服務所共用的單體式資料庫。</span><span class="sxs-lookup"><span data-stu-id="53a33-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="53a33-113">不過，討論將資料分割是純粹的相關架構和設計。</span><span class="sxs-lookup"><span data-stu-id="53a33-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53a33-114">[上一頁](state-and-data-in-docker-applications.md)
>[下一頁](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="53a33-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
