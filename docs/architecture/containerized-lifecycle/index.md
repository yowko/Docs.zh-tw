---
title: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
description: 取得使用 Docker 和 Microsoft 平臺和工具開發和部署容器化應用程式的開發和部署流程概要。
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915167"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="9182f-103">Microsoft 平台和工具的容器化 Docker 應用程式生命週期</span><span class="sxs-lookup"><span data-stu-id="9182f-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![書籍封面](./media/devops-book-cover-large-we.png)

<span data-ttu-id="9182f-105">**版本 3.1** -更新為 ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="9182f-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="9182f-106">本指南是使用 Microsoft 平臺和工具，透過 Docker 開發和部署容器化 ASP.NET Core 應用程式的一般總覽。</span><span class="sxs-lookup"><span data-stu-id="9182f-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="9182f-107">本指南包含 Azure DevOps 的高階簡介，用於執行 CI/CD 管線，以及 Azure Container Registry (ACR) 和 Azure Kubernetes Services AKS 進行部署。</span><span class="sxs-lookup"><span data-stu-id="9182f-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="9182f-108">如需低層級、開發相關的詳細資料，您可以參閱[.Net 微服務：容器化 .Net 應用程式的架構](https://docs.microsoft.com/dotnet/architecture/microservices/)指南和 it 相關參考應用程式[eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)。</span><span class="sxs-lookup"><span data-stu-id="9182f-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="9182f-109">將您的意見反應傳送給我們！</span><span class="sxs-lookup"><span data-stu-id="9182f-109">Send us your feedback!</span></span>

<span data-ttu-id="9182f-110">本指南的撰寫目的是為了協助您了解 .NET 中的容器化應用程式和微服務架構。</span><span class="sxs-lookup"><span data-stu-id="9182f-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="9182f-111">本指南和相關參考應用程式會不斷改進，因此歡迎您提供寶貴的意見反應！</span><span class="sxs-lookup"><span data-stu-id="9182f-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="9182f-112">如果您有關于如何改進本指南的意見，請在中提交意見反應 <https://aka.ms/ebookfeedback> 。</span><span class="sxs-lookup"><span data-stu-id="9182f-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="9182f-113">學分</span><span class="sxs-lookup"><span data-stu-id="9182f-113">Credits</span></span>

<span data-ttu-id="9182f-114">作者︰</span><span class="sxs-lookup"><span data-stu-id="9182f-114">Author:</span></span>

> <span data-ttu-id="9182f-115">**Cesar de la Torre**，Sr. Microsoft Corp. .NET 產品小組 PM</span><span class="sxs-lookup"><span data-stu-id="9182f-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="9182f-116">收購的編輯器：</span><span class="sxs-lookup"><span data-stu-id="9182f-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="9182f-117">**Janine 的派翠克**</span><span class="sxs-lookup"><span data-stu-id="9182f-117">**Janine Patrick**</span></span>

<span data-ttu-id="9182f-118">開發編輯器：</span><span class="sxs-lookup"><span data-stu-id="9182f-118">Developmental Editor:</span></span>

> <span data-ttu-id="9182f-119">Microsoft 的解決方案專業人員**Bob Russell**</span><span class="sxs-lookup"><span data-stu-id="9182f-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="9182f-120">**八進位發行，Inc。**</span><span class="sxs-lookup"><span data-stu-id="9182f-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="9182f-121">編輯生產：</span><span class="sxs-lookup"><span data-stu-id="9182f-121">Editorial Production:</span></span>

> [<span data-ttu-id="9182f-122">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="9182f-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="9182f-123">**八進位發行，Inc。**</span><span class="sxs-lookup"><span data-stu-id="9182f-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="9182f-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="9182f-124">Copyeditor:</span></span>

> <span data-ttu-id="9182f-125">Microsoft 的解決方案專業人員**Bob Russell**</span><span class="sxs-lookup"><span data-stu-id="9182f-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="9182f-126">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="9182f-126">Participants and reviewers:</span></span>

> <span data-ttu-id="9182f-127">**Nish Anil**，Microsoft NET 小組資深方案經理</span><span class="sxs-lookup"><span data-stu-id="9182f-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9182f-128">以一般概念**Miguel veloso turing challenge**軟體發展工程師</span><span class="sxs-lookup"><span data-stu-id="9182f-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="9182f-129">**Sumit Ghosh**，neudesic 提供的首席顧問</span><span class="sxs-lookup"><span data-stu-id="9182f-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="9182f-130">著作權</span><span class="sxs-lookup"><span data-stu-id="9182f-130">Copyright</span></span>

<span data-ttu-id="9182f-131">發行者</span><span class="sxs-lookup"><span data-stu-id="9182f-131">PUBLISHED BY</span></span>

<span data-ttu-id="9182f-132">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="9182f-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="9182f-133">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="9182f-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="9182f-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9182f-134">One Microsoft Way</span></span>

<span data-ttu-id="9182f-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="9182f-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="9182f-136">&copy;Microsoft Corporation 的著作權2020</span><span class="sxs-lookup"><span data-stu-id="9182f-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="9182f-137">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="9182f-137">All rights reserved.</span></span> <span data-ttu-id="9182f-138">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="9182f-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="9182f-139">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="9182f-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="9182f-140">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="9182f-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="9182f-141">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="9182f-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="9182f-142">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="9182f-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="9182f-143">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="9182f-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="9182f-144">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="9182f-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="9182f-145">Docker whale 標誌是 Docker，Inc. 的注冊商標，由許可權使用。</span><span class="sxs-lookup"><span data-stu-id="9182f-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="9182f-146">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="9182f-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9182f-147">下一個</span><span class="sxs-lookup"><span data-stu-id="9182f-147">Next</span></span>](introduction-to-containers-and-docker.md)
