---
title: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式
description: 本指南會提供使用 ASP.NET Core 和 Azure 建置整合型 Web 應用程式的端對端指引。
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: e2d2545108b55043c322baffbd609b2422d2743b
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936980"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="caa24-103">使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="caa24-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![封面影像](./media/cover.png)

<span data-ttu-id="caa24-105">發行者</span><span class="sxs-lookup"><span data-stu-id="caa24-105">PUBLISHED BY</span></span>

<span data-ttu-id="caa24-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="caa24-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="caa24-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="caa24-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="caa24-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="caa24-108">One Microsoft Way</span></span>

<span data-ttu-id="caa24-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="caa24-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="caa24-110">Copyright © 2018 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="caa24-110">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="caa24-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="caa24-111">All rights reserved.</span></span> <span data-ttu-id="caa24-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="caa24-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="caa24-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="caa24-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="caa24-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="caa24-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="caa24-115">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="caa24-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="caa24-116">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="caa24-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="caa24-117">Microsoft 與列於 https://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="caa24-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="caa24-118">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="caa24-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="caa24-119">Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。</span><span class="sxs-lookup"><span data-stu-id="caa24-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="caa24-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="caa24-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="caa24-121">作者: </span><span class="sxs-lookup"><span data-stu-id="caa24-121">Author:</span></span>

> <span data-ttu-id="caa24-122">軟體架構 Advisor **Steve Smith (@ardalis)**，[Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="caa24-122">**Steve Smith (@ardalis)**, Software Architecture Advisor, [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="caa24-123">編輯者：</span><span class="sxs-lookup"><span data-stu-id="caa24-123">Editors:</span></span>

> <span data-ttu-id="caa24-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="caa24-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="caa24-125">簡介</span><span class="sxs-lookup"><span data-stu-id="caa24-125">Introduction</span></span>

<span data-ttu-id="caa24-126">.NET Core 和 ASP.NET Core 提供許多優於傳統.NET 開發的優點。</span><span class="sxs-lookup"><span data-stu-id="caa24-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="caa24-127">如果下列部分或所有項目對應用程式成功而言十分重要，則您應該將 .NET Core 用於伺服器應用程式：</span><span class="sxs-lookup"><span data-stu-id="caa24-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="caa24-128">跨平台支援。</span><span class="sxs-lookup"><span data-stu-id="caa24-128">Cross-platform support.</span></span>

- <span data-ttu-id="caa24-129">使用微服務。</span><span class="sxs-lookup"><span data-stu-id="caa24-129">Use of microservices.</span></span>

- <span data-ttu-id="caa24-130">使用 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="caa24-130">Use of Docker containers.</span></span>

- <span data-ttu-id="caa24-131">高效能和延展性需求。</span><span class="sxs-lookup"><span data-stu-id="caa24-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="caa24-132">相同伺服器上應用程式之 .NET 版本的並存版本控制。</span><span class="sxs-lookup"><span data-stu-id="caa24-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="caa24-133">傳統 .NET 應用程式可以並確實支援這些需求，但 ASP.NET Core 和 .NET Core 已最佳化可提供針對上述案例的改善支援。</span><span class="sxs-lookup"><span data-stu-id="caa24-133">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="caa24-134">越來越多的組織會選擇使用 Microsoft Azure 這類服務，以在雲端中裝載其 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="caa24-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="caa24-135">如果下列對您的應用程式或組織十分重要，則您應該考慮將應用程式裝載在雲端中：</span><span class="sxs-lookup"><span data-stu-id="caa24-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="caa24-136">降低對資料中心成本的投資 (硬體、軟體、空間、公用程式等等)</span><span class="sxs-lookup"><span data-stu-id="caa24-136">Reduced investment in data center costs (hardware, software, space, utilities, etc.)</span></span>

- <span data-ttu-id="caa24-137">彈性定價 (根據使用量付費，而閒置容量不需付費)。</span><span class="sxs-lookup"><span data-stu-id="caa24-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="caa24-138">可靠性極高。</span><span class="sxs-lookup"><span data-stu-id="caa24-138">Extreme reliability.</span></span>

- <span data-ttu-id="caa24-139">改善的應用程式行動性；輕鬆地變更您應用程式的部署位置和方式。</span><span class="sxs-lookup"><span data-stu-id="caa24-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="caa24-140">彈性容量；根據實際需求相應增加或減少。</span><span class="sxs-lookup"><span data-stu-id="caa24-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="caa24-141">使用 ASP.NET Core 建置 Web 應用程式 (且其裝載於 Azure) 提供許多比傳統替代項目更具競爭性的優點。</span><span class="sxs-lookup"><span data-stu-id="caa24-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="caa24-142">ASP.NET Core 已針對現代化 Web 應用程式開發做法和雲端裝載案例最佳化。</span><span class="sxs-lookup"><span data-stu-id="caa24-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="caa24-143">在本指南中，您將學習如何架構 ASP.NET Core 應用程式，以善加利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="caa24-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="caa24-144">用途</span><span class="sxs-lookup"><span data-stu-id="caa24-144">Purpose</span></span>

<span data-ttu-id="caa24-145">本指南會提供使用 ASP.NET Core 和 Azure 建置整合型 Web 應用程式的端對端指引。</span><span class="sxs-lookup"><span data-stu-id="caa24-145">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="caa24-146">本指南是 ["_.NET Microservices.Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) 的補充說明，該書籍著重在 Docker、微服務及部署容器以裝載企業應用程式的部分。</span><span class="sxs-lookup"><span data-stu-id="caa24-146">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="caa24-147">.NET 微服務。</span><span class="sxs-lookup"><span data-stu-id="caa24-147">.NET Microservices.</span></span> <span data-ttu-id="caa24-148">容器化 .NET 應用程式的架構</span><span class="sxs-lookup"><span data-stu-id="caa24-148">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="caa24-149">**電子書**</span><span class="sxs-lookup"><span data-stu-id="caa24-149">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="caa24-150">**範例應用程式**</span><span class="sxs-lookup"><span data-stu-id="caa24-150">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="caa24-151">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="caa24-151">Who should use this guide</span></span>

<span data-ttu-id="caa24-152">本指南的對象主要是開發人員、開發負責人和架構設計人員，而他們對使用 Microsoft 技術和服務在雲端中建置現代化 Web 應用程式感興趣。</span><span class="sxs-lookup"><span data-stu-id="caa24-152">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="caa24-153">次要對象是技術決策者，其已熟悉 ASP.NET 或 Azure，並尋找是否可以升級為新專案或現有專案之 ASP.NET Core 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="caa24-153">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="caa24-154">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="caa24-154">How you can use this guide</span></span>

<span data-ttu-id="caa24-155">本指南已壓縮成相當小的文件，著重於使用現代化 .NET 技術和 Windows Azure 來建置 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="caa24-155">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="caa24-156">因此，可以完整讀取它，以提供對這類應用程式和其技術考量的基礎了解。</span><span class="sxs-lookup"><span data-stu-id="caa24-156">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="caa24-157">本指南與其範例應用程式也可以作為起點或參考。</span><span class="sxs-lookup"><span data-stu-id="caa24-157">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="caa24-158">使用相關聯的範例應用程式作為您專屬應用程式的範本，或查看如何組織應用程式的元件組件。</span><span class="sxs-lookup"><span data-stu-id="caa24-158">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="caa24-159">當您要為專屬應用程式權衡這些選擇時，請回頭參考指南內架構和技術選項的原則與說明還有決策考量。</span><span class="sxs-lookup"><span data-stu-id="caa24-159">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="caa24-160">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="caa24-160">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="caa24-161">讓所有人都使用一組共用術語和基礎原則，有助確保套用一致的架構模式和做法。</span><span class="sxs-lookup"><span data-stu-id="caa24-161">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="caa24-162">參考</span><span class="sxs-lookup"><span data-stu-id="caa24-162">References</span></span>

- <span data-ttu-id="caa24-163">**針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**</span><span class="sxs-lookup"><span data-stu-id="caa24-163">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
[<span data-ttu-id="caa24-164">下一步</span><span class="sxs-lookup"><span data-stu-id="caa24-164">Next</span></span>](modern-web-applications-characteristics.md)
