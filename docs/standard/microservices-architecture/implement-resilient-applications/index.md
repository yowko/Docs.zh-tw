---
title: 實作復原應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作復原應用程式
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ec79221f0238d61f1ca1b2b7c58b1e16be7f4df4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130790"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="1beb4-103">實作復原應用程式</span><span class="sxs-lookup"><span data-stu-id="1beb4-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="1beb4-104">*您的微服務和雲端應用程式都必須容許終究一定會發生的部分失敗。您必須將應用程式設計成可從這些部分失敗中復原。*</span><span class="sxs-lookup"><span data-stu-id="1beb4-104">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="1beb4-105">「復原」是指能夠從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="1beb4-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="1beb4-106">這不是為了避免失敗，而是要接受失敗將會發生的事實，並以避免停機或資料遺失的方式予以回應。</span><span class="sxs-lookup"><span data-stu-id="1beb4-106">It is not about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="1beb4-107">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="1beb4-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="1beb4-108">設計和部署微服務應用程式的挑戰性就已經很高。</span><span class="sxs-lookup"><span data-stu-id="1beb4-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="1beb4-109">但您還必須確保應用程式在必然會發生某些失敗的環境中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1beb4-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="1beb4-110">因此，您的應用程式應該能夠復原。</span><span class="sxs-lookup"><span data-stu-id="1beb4-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="1beb4-111">它應該設計成能夠回應部分失敗，如網路中斷，或是雲端中的節點或 VM 沒有回應。</span><span class="sxs-lookup"><span data-stu-id="1beb4-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="1beb4-112">即使是微服務 (容器) 移至叢集中的其他節點，也會導致應用程式內發生間歇且短暫性失敗。</span><span class="sxs-lookup"><span data-stu-id="1beb4-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="1beb4-113">您應用程式的許多個別元件也應該納入狀況監控功能。</span><span class="sxs-lookup"><span data-stu-id="1beb4-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="1beb4-114">您可以遵循本章中的指引，建立即使在複雜的雲端式部署中發生暫時性停機或一般延遲的情況下也能順暢運作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1beb4-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1beb4-115">[上一頁](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[下一頁](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="1beb4-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>