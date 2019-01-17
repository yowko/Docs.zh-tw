---
title: Implementing Resilient Applications
description: Learn about resilience, a core concept in a microservices architecture. You must know how to handle transient failures gracefully because they will occur.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362739"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="46fef-104">Implement Resilient Applications</span><span class="sxs-lookup"><span data-stu-id="46fef-104">Implement Resilient Applications</span></span>

<span data-ttu-id="46fef-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span><span class="sxs-lookup"><span data-stu-id="46fef-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="46fef-106">Resiliency is the ability to recover from failures and continue to function.</span><span class="sxs-lookup"><span data-stu-id="46fef-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="46fef-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span><span class="sxs-lookup"><span data-stu-id="46fef-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="46fef-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span><span class="sxs-lookup"><span data-stu-id="46fef-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="46fef-109">It's challenging enough to design and deploy a microservices-based application.</span><span class="sxs-lookup"><span data-stu-id="46fef-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="46fef-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span><span class="sxs-lookup"><span data-stu-id="46fef-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="46fef-111">Therefore, your application should be resilient.</span><span class="sxs-lookup"><span data-stu-id="46fef-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="46fef-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span><span class="sxs-lookup"><span data-stu-id="46fef-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="46fef-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span><span class="sxs-lookup"><span data-stu-id="46fef-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="46fef-114">The many individual components of your application should also incorporate health monitoring features.</span><span class="sxs-lookup"><span data-stu-id="46fef-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="46fef-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span><span class="sxs-lookup"><span data-stu-id="46fef-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="46fef-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Next](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="46fef-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>