---
title: 服務導向架構
description: 了解微服務和服務導向架構 (SOA) 的基本差異。
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674925"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="5d927-103">服務導向架構</span><span class="sxs-lookup"><span data-stu-id="5d927-103">Service-oriented architecture</span></span>

<span data-ttu-id="5d927-104">服務導向架構 (SOA) 是過度使用的詞彙，而且對不同的人有不同的意義。</span><span class="sxs-lookup"><span data-stu-id="5d927-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="5d927-105">但作為共同點，SOA 表示您透過將應用程式分解為多個服務 (通常是 HTTP 服務) 來建構應用程式，而服務可以分類為不同的型別 (例如子系統或層級)。</span><span class="sxs-lookup"><span data-stu-id="5d927-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="5d927-106">這些服務現在可以部署為 Docker 容器以解決部署問題，因為容器映像包含所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5d927-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="5d927-107">不過，當您需要相應增加 SOA 應用程式時，如果以單一 Docker 主機為基礎部署，可能會有延展性和可用性挑戰。</span><span class="sxs-lookup"><span data-stu-id="5d927-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you're deploying based on single Docker hosts.</span></span> <span data-ttu-id="5d927-108">Docker 叢集軟體或協調器可在這方面幫助您，後續各節所述之微服務部署方法會加以說明。</span><span class="sxs-lookup"><span data-stu-id="5d927-108">This is where Docker clustering software or an orchestrator can help you, as explained in later sections where deployment approaches for microservices are described.</span></span>

<span data-ttu-id="5d927-109">Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。</span><span class="sxs-lookup"><span data-stu-id="5d927-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="5d927-110">微服務衍生自 SOA，但 SOA 與微服務架構不同。</span><span class="sxs-lookup"><span data-stu-id="5d927-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="5d927-111">SOA 一般會提供大型的中央訊息代理程式、組織層級的中央協調器和[企業服務匯流排 (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) 這類功能。</span><span class="sxs-lookup"><span data-stu-id="5d927-111">Features like large central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="5d927-112">但在大部分情況下，這些是微服務社群中的反向模式。</span><span class="sxs-lookup"><span data-stu-id="5d927-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="5d927-113">事實上，有些人認為「微服務架構就是 SOA。」</span><span class="sxs-lookup"><span data-stu-id="5d927-113">In fact, some people argue that "The microservice architecture is SOA done right."</span></span>

<span data-ttu-id="5d927-114">本指南著重在微服務，因為 SOA 方法與微服務架構中所使用的需求和技術相較之下較不精準。</span><span class="sxs-lookup"><span data-stu-id="5d927-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="5d927-115">如果您知道如何建置微服務應用程式，則也會知道如何建置較簡單的服務導向應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d927-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d927-116">[上一頁](docker-application-state-data.md)
>[下一頁](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="5d927-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>
