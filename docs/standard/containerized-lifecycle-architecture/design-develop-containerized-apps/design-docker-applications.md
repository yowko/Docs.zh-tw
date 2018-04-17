---
title: 設計 Docker 應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f6f1ecdd89b85d4f44136da9a5ec9610f170a9
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="design-docker-applications"></a><span data-ttu-id="73fbe-103">設計 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="73fbe-103">Design Docker applications</span></span>

<span data-ttu-id="73fbe-104">第 1 導入了有關容器和 Docker 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="73fbe-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="73fbe-105">該資訊是資訊的基本的層級，若要開始使用您需要。</span><span class="sxs-lookup"><span data-stu-id="73fbe-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="73fbe-106">但是，企業應用程式可能很複雜，而不是單一服務或容器的多個服務所組成。</span><span class="sxs-lookup"><span data-stu-id="73fbe-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="73fbe-107">選擇性的使用情況下，您需要知道額外的方法，例如 Service-Oriented 架構 (SOA) 的設計，以及更多進階 microservices 概念和容器協調流程的概念。</span><span class="sxs-lookup"><span data-stu-id="73fbe-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="73fbe-108">本文件的範圍並不限於 microservices，但任何 Docker 應用程式生命週期 」，因此，它不會不瀏覽 microservices 架構深度因為您也可以使用容器和 Docker 規則聖多美、 背景工作或作業，或甚至使用整合型應用程式部署方法。</span><span class="sxs-lookup"><span data-stu-id="73fbe-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="73fbe-109">不過，我們 DevOps 與應用程式生命週期之前，務必了解如何您要設計並建構您的應用程式，以及您的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="73fbe-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="73fbe-110">[上一個] (index.md) [下一步] (常見的容器-設計-principles.md)</span><span class="sxs-lookup"><span data-stu-id="73fbe-110">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
