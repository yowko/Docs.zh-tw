---
title: 設計 Docker 應用程式
description: 您可以在這裡找到微服務架構深入指南的參考資料，因為本指南並未詳細說明該主題。
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738468"
---
# <a name="design-docker-applications"></a><span data-ttu-id="02cf9-103">設計 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="02cf9-103">Design Docker applications</span></span>

<span data-ttu-id="02cf9-104">第 1 章介紹有關容器和 Docker 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="02cf9-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="02cf9-105">該資訊是您開始所需的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="02cf9-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="02cf9-106">但企業應用程式可能很複雜，且是由多個服務而不是單一服務或容器所組成。</span><span class="sxs-lookup"><span data-stu-id="02cf9-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="02cf9-107">針對這些選擇性使用案例，您必須了解其他設計方法，例如服務導向架構 (SOA)，以及更進階的微服務概念和容器協調流程概念。</span><span class="sxs-lookup"><span data-stu-id="02cf9-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="02cf9-108">本文檔的範圍不僅限於微服務,而是任何 Docker 應用程式生命週期,因此,它不深入探索微服務體系結構,因為您也可以將容器和 Docker 與常規 SOA、後台任務或作業,甚至整個應用程式部署方法使用。</span><span class="sxs-lookup"><span data-stu-id="02cf9-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="02cf9-109">**更多資訊**要深入瞭解企業應用程式和微服務體系結構,請閱讀[指南 NET 微服務:容器化 .NET 應用程式的體系結構](../../microservices/index.md),您也可以從<https://aka.ms/MicroservicesEbook>下載。</span><span class="sxs-lookup"><span data-stu-id="02cf9-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="02cf9-110">不過，在開始探討應用程式生命週期和 DevOps 之前，請務必了解您要如何設計及建構應用程式，以及您有哪些設計選擇。</span><span class="sxs-lookup"><span data-stu-id="02cf9-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02cf9-111">[前一個](index.md)
>[下一個](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="02cf9-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
