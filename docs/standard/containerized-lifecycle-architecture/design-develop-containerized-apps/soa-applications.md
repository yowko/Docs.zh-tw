---
title: "SOA 應用程式"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 81d2b60303e051568b664ec20225d835a09187c0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="soa-applications"></a><span data-ttu-id="69486-104">SOA 應用程式</span><span class="sxs-lookup"><span data-stu-id="69486-104">SOA applications</span></span>

<span data-ttu-id="69486-105">SOA 已過度的詞彙，使用許多不同的項目對不同的人。</span><span class="sxs-lookup"><span data-stu-id="69486-105">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="69486-106">但最小值及共同分母、 SOA，或服務方向、 平均數該結構的應用程式將它分解 （通常為 HTTP 服務） 可以在不同的類型分類的多個服務的架構，例如子系統或者，在其他情況下，做為層。</span><span class="sxs-lookup"><span data-stu-id="69486-106">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="69486-107">現在，您可以部署這些服務做為 Docker 容器的可解決與部署相關的問題，因為所有的相依性，但包括容器映像。</span><span class="sxs-lookup"><span data-stu-id="69486-107">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="69486-108">不過，當您需要向外延展 SOAs，您可能會遇到的挑戰如果您要部署根據的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="69486-108">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="69486-109">這是 Docker，叢集軟體或 orchestrator 將會幫助您。</span><span class="sxs-lookup"><span data-stu-id="69486-109">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="69486-110">我們會探討這在下一節中更詳細地介紹 microservices 方法。</span><span class="sxs-lookup"><span data-stu-id="69486-110">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="69486-111">在一天結束時，容器叢集解決方案適合用於這兩種傳統 SOA 的架構，或用於更進階的 microservices 架構中的每個微服務擁有其資料模型。</span><span class="sxs-lookup"><span data-stu-id="69486-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="69486-112">此外，由於多個資料庫，您也可以向外延展資料層，而不是使用整合型 SOA 服務所共用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="69486-112">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="69486-113">不過，將資料分割的相關討論即將純粹架構和設計。</span><span class="sxs-lookup"><span data-stu-id="69486-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="69486-114">[上一個](state-and-data-in-docker-applications.md) [下一步] (協調-高的延展性-availability.md)</span><span class="sxs-lookup"><span data-stu-id="69486-114">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
