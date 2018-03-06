---
title: "使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式"
description: "使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 簡介"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1140a18aba685f3415d7c599d1b76648bf9924e7
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="c64e5-103">使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="c64e5-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![封面影像](./media/cover.jpg)


<span data-ttu-id="c64e5-105">.NET Core 和 ASP.NET Core 提供許多優於傳統.NET 開發的優點。</span><span class="sxs-lookup"><span data-stu-id="c64e5-105">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="c64e5-106">如果下列部分或所有項目對應用程式成功而言十分重要，則您應該將 .NET Core 用於伺服器應用程式：</span><span class="sxs-lookup"><span data-stu-id="c64e5-106">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="c64e5-107">跨平台支援</span><span class="sxs-lookup"><span data-stu-id="c64e5-107">Cross-platform support</span></span>

-   <span data-ttu-id="c64e5-108">使用微服務</span><span class="sxs-lookup"><span data-stu-id="c64e5-108">Use of microservices</span></span>

-   <span data-ttu-id="c64e5-109">使用 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="c64e5-109">Use of Docker containers</span></span>

-   <span data-ttu-id="c64e5-110">高效能和延展性需求</span><span class="sxs-lookup"><span data-stu-id="c64e5-110">High performance and scalability requirements</span></span>

-   <span data-ttu-id="c64e5-111">相同伺服器上應用程式之 .NET 版本的並存版本控制</span><span class="sxs-lookup"><span data-stu-id="c64e5-111">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="c64e5-112">傳統 .NET 應用程式可以並確實支援這些需求，但 ASP.NET Core 和 .NET Core 已最佳化可提供針對上述案例的改善支援。</span><span class="sxs-lookup"><span data-stu-id="c64e5-112">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="c64e5-113">越來越多的組織會選擇使用 Microsoft Azure 這類服務，以在雲端中裝載其 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c64e5-113">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="c64e5-114">如果下列對您的應用程式或組織十分重要，則您應該考慮將應用程式裝載在雲端中：</span><span class="sxs-lookup"><span data-stu-id="c64e5-114">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="c64e5-115">降低對資料中心成本的投資 (硬體、軟體、空間、公用程式等等)</span><span class="sxs-lookup"><span data-stu-id="c64e5-115">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="c64e5-116">彈性價格 (根據使用付費，而閒置容量不需付費)</span><span class="sxs-lookup"><span data-stu-id="c64e5-116">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="c64e5-117">極高可靠性</span><span class="sxs-lookup"><span data-stu-id="c64e5-117">Extreme reliability</span></span>

-   <span data-ttu-id="c64e5-118">改善的應用程式行動性；輕鬆地變更您應用程式的部署位置和方式</span><span class="sxs-lookup"><span data-stu-id="c64e5-118">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="c64e5-119">彈性容量；根據實際需求相應增加或減少</span><span class="sxs-lookup"><span data-stu-id="c64e5-119">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="c64e5-120">使用 ASP.NET Core 建置 Web 應用程式 (且其裝載於 Microsoft Azure) 提供許多優於傳統替代項目的具競爭性優點。</span><span class="sxs-lookup"><span data-stu-id="c64e5-120">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="c64e5-121">ASP.NET Core 已針對現代化 Web 應用程式開發做法和雲端裝載案例最佳化。</span><span class="sxs-lookup"><span data-stu-id="c64e5-121">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="c64e5-122">在本指南中，您將學習如何架構 ASP.NET Core 應用程式以善加利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="c64e5-122">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="c64e5-123">用途</span><span class="sxs-lookup"><span data-stu-id="c64e5-123">Purpose</span></span>

<span data-ttu-id="c64e5-124">本指南會提供使用 ASP.NET Core 和 Azure 建置整合型 Web 應用程式的端對端指引。</span><span class="sxs-lookup"><span data-stu-id="c64e5-124">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="c64e5-125">本指南可補充「使用 .NET 架構和開發容器化和以微服務為基礎的應用程式」，其較著重 Docker、微服務以及裝載企業應用程式的容器的部署。</span><span class="sxs-lookup"><span data-stu-id="c64e5-125">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="c64e5-126">在 .NET 中架構和開發以容器化微服務為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="c64e5-126">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="c64e5-127">**電子書**</span><span class="sxs-lookup"><span data-stu-id="c64e5-127">**e-book**</span></span>  
> <http://aka.ms/MicroservicesEbook>
> - <span data-ttu-id="c64e5-128">**範例應用程式**</span><span class="sxs-lookup"><span data-stu-id="c64e5-128">**Sample Application**</span></span>  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c64e5-129">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="c64e5-129">Who should use this guide</span></span>

<span data-ttu-id="c64e5-130">本指南的對象主要是開發人員、開發負責人和架構設計人員，而他們對使用 Microsoft 技術和服務在雲端中建置現代化 Web 應用程式感興趣。</span><span class="sxs-lookup"><span data-stu-id="c64e5-130">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="c64e5-131">次要對象是技術決策者，其已熟悉 ASP.NET 和 (或) Azure，並尋找是否可以升級為新或現有專案之 ASP.NET Core 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c64e5-131">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="c64e5-132">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="c64e5-132">How you can use this guide</span></span>

<span data-ttu-id="c64e5-133">本指南已壓縮成相當小的文件，著重於使用現代化 .NET 技術和 Windows Azure 來建置 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c64e5-133">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="c64e5-134">因此，可以完整讀取它，以提供對這類應用程式和其技術考量的基礎了解。</span><span class="sxs-lookup"><span data-stu-id="c64e5-134">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="c64e5-135">本指南與其範例應用程式也可以作為起點或參考。</span><span class="sxs-lookup"><span data-stu-id="c64e5-135">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="c64e5-136">使用相關聯的範例應用程式作為您專屬應用程式的範本，或查看如何組織應用程式的元件組件。</span><span class="sxs-lookup"><span data-stu-id="c64e5-136">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="c64e5-137">請回頭參考指南的原則、架構和技術選項的涵蓋範圍，以及權衡這些針對您專屬應用程式之選擇的決策考量。</span><span class="sxs-lookup"><span data-stu-id="c64e5-137">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="c64e5-138">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="c64e5-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="c64e5-139">讓所有人都使用一組共用術語和基礎原則，將有助於確保套用一致的架構模式和做法。</span><span class="sxs-lookup"><span data-stu-id="c64e5-139">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="c64e5-140">參考</span><span class="sxs-lookup"><span data-stu-id="c64e5-140">References</span></span>
- <span data-ttu-id="c64e5-141">**針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**</span><span class="sxs-lookup"><span data-stu-id="c64e5-141">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
<span data-ttu-id="c64e5-142">[下一個] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="c64e5-142">[Next] (modern-web-applications-characteristics.md)</span></span>
