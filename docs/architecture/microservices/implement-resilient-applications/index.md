---
title: 執行彈性應用程式
description: 了解彈性這個微服務架構中的核心概念。 您必須知道如何在發生暫時性失敗時進行正常處理。
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502648"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="77599-104">執行彈性應用程式</span><span class="sxs-lookup"><span data-stu-id="77599-104">Implement resilient applications</span></span>

<span data-ttu-id="77599-105">*您的微服務和雲端式應用程式必須接受最後才會發生的部分失敗。您必須將應用程式設計為可復原那些部分失敗。*</span><span class="sxs-lookup"><span data-stu-id="77599-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="77599-106">復原是從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="77599-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="77599-107">這不是為了避免失敗，而是要接受失敗將會發生的事實，並以避免停機或資料遺失的方式予以回應。</span><span class="sxs-lookup"><span data-stu-id="77599-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="77599-108">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="77599-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="77599-109">設計和部署微服務應用程式的挑戰性就已經很高。</span><span class="sxs-lookup"><span data-stu-id="77599-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="77599-110">但您還必須確保應用程式在必然會發生某些失敗的環境中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="77599-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="77599-111">因此，您的應用程式應該能夠復原。</span><span class="sxs-lookup"><span data-stu-id="77599-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="77599-112">它應該設計成能夠回應部分失敗，如網路中斷，或是雲端中的節點或 VM 沒有回應。</span><span class="sxs-lookup"><span data-stu-id="77599-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="77599-113">即使是微服務 (容器) 移至叢集中的其他節點，也會導致應用程式內發生間歇且短暫性失敗。</span><span class="sxs-lookup"><span data-stu-id="77599-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="77599-114">您應用程式的許多個別元件也應該納入狀況監控功能。</span><span class="sxs-lookup"><span data-stu-id="77599-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="77599-115">您可以遵循本章中的指引，建立即使在複雜的雲端式部署中發生暫時性停機或一般延遲的情況下也能順暢運作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="77599-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="77599-116">eShopOnContainer 已使用 Polly 連結[庫](http://www.thepollyproject.org/)，在發行3.0.0 之前，使用具[類型的用戶端](./use-httpclientfactory-to-implement-resilient-http-requests.md)來執行復原。</span><span class="sxs-lookup"><span data-stu-id="77599-116">eShopOnContainer had been using the [Polly library](http://www.thepollyproject.org/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="77599-117">從 release 3.0.0 開始，會使用[Linkerd 網格](https://linkerd.io/)來執行 HTTP 呼叫復原，以在 Kubernetes 叢集中以透明且可設定的方式處理重試，而不必處理常式代碼中的那些疑慮。</span><span class="sxs-lookup"><span data-stu-id="77599-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="77599-118">Polly 程式庫仍然用來增加資料庫連接的恢復功能，特別是在啟動服務時。</span><span class="sxs-lookup"><span data-stu-id="77599-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="77599-119">在使用 Linkerd 之前，本節中的所有程式碼範例都是有效的，而且不會更新以反映目前的實際程式碼。</span><span class="sxs-lookup"><span data-stu-id="77599-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="77599-120">因此，它們在本節內容中是合理的。</span><span class="sxs-lookup"><span data-stu-id="77599-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="77599-121">[上一頁](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[下一頁](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="77599-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
