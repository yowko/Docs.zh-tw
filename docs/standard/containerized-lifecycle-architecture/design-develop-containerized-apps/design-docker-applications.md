---
title: 設計 Docker 應用程式
description: 尋找以下微服務架構的深度指南的參考，因為這是主題，不在本指南詳細說明。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 858147883b3b4a5a5f487856028fdbfa84f6cca9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675182"
---
# <a name="design-docker-applications"></a><span data-ttu-id="fece0-103">設計 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="fece0-103">Design Docker applications</span></span>

<span data-ttu-id="fece0-104">第 1 章引進了有關容器和 Docker 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="fece0-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="fece0-105">這項資訊是資訊的基本的層級，若要開始您需要。</span><span class="sxs-lookup"><span data-stu-id="fece0-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="fece0-106">但是，企業應用程式很複雜，而不是單一服務或容器的多個服務所組成。</span><span class="sxs-lookup"><span data-stu-id="fece0-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="fece0-107">選擇性的使用情況下，您需要知道其他方法，例如服務導向架構 (SOA) 的設計，以及更進階微服務概念和容器協調流程概念。</span><span class="sxs-lookup"><span data-stu-id="fece0-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="fece0-108">本文件的範圍並不限於微服務，但若要任何 Docker 應用程式的生命週期，因此，它不會不探索深入了解微服務架構，因為您也可以使用容器和 Docker 與一般的 SOA、 背景工作或作業，或甚至是使用整合型應用程式部署方法。</span><span class="sxs-lookup"><span data-stu-id="fece0-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="fece0-109">**進一歩**企業應用程式與微服務架構，深入了解的詳細資訊，請閱讀本指南[NET 微服務：容器化.NET 應用程式架構](https://docs.microsoft.com/dotnet/standard/microservices-architecture)，您也可以從下載<https://aka.ms/MicroservicesEbook>。</span><span class="sxs-lookup"><span data-stu-id="fece0-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="fece0-110">不過，我們的應用程式生命週期和 DevOps 之前，務必知道您要如何設計及建構您的應用程式和您的設計選擇是什麼。</span><span class="sxs-lookup"><span data-stu-id="fece0-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fece0-111">[上一頁](index.md)
>[下一頁](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="fece0-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
