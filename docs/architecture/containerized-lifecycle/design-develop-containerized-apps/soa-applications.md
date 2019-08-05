---
title: SOA 應用程式
description: 請記住，容器也是 SOA 應用程式的實用部署選項。
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672355"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="692c0-103">服務導向應用程式</span><span class="sxs-lookup"><span data-stu-id="692c0-103">Service-oriented applications</span></span>

<span data-ttu-id="692c0-104">服務導向架構 (SOA) 這個詞彙的使用有點過於氾濫，因此對不同人有不同的意義。</span><span class="sxs-lookup"><span data-stu-id="692c0-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="692c0-105">但其中關於 SOA 的共同點是：您將應用程式分解為若干服務 (通常是 HTTP 服務) 來建構應用程式的架構，而這些服務又歸為不同類型，例如子系統或層 (在某些情況下)。</span><span class="sxs-lookup"><span data-stu-id="692c0-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="692c0-106">現在，您可以將這些服務部署為 Docker 容器以解決部署相關問題，因為所有相依性都包含在容器映像中。</span><span class="sxs-lookup"><span data-stu-id="692c0-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="692c0-107">但是，如果您是根據單一執行個體進行部署，當您需要擴充 SOA 時可能會遇到困難。</span><span class="sxs-lookup"><span data-stu-id="692c0-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="692c0-108">您可以使用 Docker 叢集軟體或協調器來解決這個挑戰。</span><span class="sxs-lookup"><span data-stu-id="692c0-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="692c0-109">下一節探討微服務方法時，我們會詳細說明協調器。</span><span class="sxs-lookup"><span data-stu-id="692c0-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="692c0-110">Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。</span><span class="sxs-lookup"><span data-stu-id="692c0-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="692c0-111">綜觀各方面條件來看，針對傳統 SOA 架構以及更進階的微服務架構 (其中每個微服務擁有其資料模型) 均適用容器叢集解決方案。</span><span class="sxs-lookup"><span data-stu-id="692c0-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="692c0-112">由於採用多個資料庫，您可以擴充資料層，而不需使用由 SOA 服務共用的整合型資料庫。</span><span class="sxs-lookup"><span data-stu-id="692c0-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="692c0-113">不過，我們只會單純就架構和設計面來探討資料分割。</span><span class="sxs-lookup"><span data-stu-id="692c0-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="692c0-114">[上一頁](state-and-data-in-docker-applications.md)
>[下一頁](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="692c0-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
