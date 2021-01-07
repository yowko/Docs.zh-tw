---
title: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
description: 取得使用 Docker 和 Microsoft 平臺和工具開發和部署容器化應用程式的開發和部署程式的概要說明。
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970111"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="05bca-103">Microsoft 平台和工具的容器化 Docker 應用程式生命週期</span><span class="sxs-lookup"><span data-stu-id="05bca-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![書籍封面](./media/devops-book-cover-large-we.png)

<span data-ttu-id="05bca-105">**版本5.0 版** -更新為 ASP.NET Core 5。0</span><span class="sxs-lookup"><span data-stu-id="05bca-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="05bca-106">請參閱 [變更記錄](https://aka.ms/DockerLifecycleEbookChangelog) ，以取得書籍更新和社區貢獻。</span><span class="sxs-lookup"><span data-stu-id="05bca-106">Refer [changelog](https://aka.ms/DockerLifecycleEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="05bca-107">本指南是使用 Microsoft 平臺和工具，透過 Docker 開發和部署容器化 ASP.NET Core 應用程式的一般總覽。</span><span class="sxs-lookup"><span data-stu-id="05bca-107">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="05bca-108">本指南包含 Azure DevOps 的高階簡介，可用於執行 CI/CD 管線，以及 Azure Container Registry (ACR) 和 Azure Kubernetes Services 部署的 AKS。</span><span class="sxs-lookup"><span data-stu-id="05bca-108">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="05bca-109">針對低層級、開發相關的詳細資料，您可以看到 [.Net 微服務：容器化 .Net 應用程式的架構](../microservices/index.md) 指南和 it 相關的參考應用程式 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)。</span><span class="sxs-lookup"><span data-stu-id="05bca-109">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="05bca-110">將您的意見反應傳送給我們！</span><span class="sxs-lookup"><span data-stu-id="05bca-110">Send us your feedback!</span></span>

<span data-ttu-id="05bca-111">本指南的撰寫目的是為了協助您了解 .NET 中的容器化應用程式和微服務架構。</span><span class="sxs-lookup"><span data-stu-id="05bca-111">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="05bca-112">本指南和相關參考應用程式會不斷改進，因此歡迎您提供寶貴的意見反應！</span><span class="sxs-lookup"><span data-stu-id="05bca-112">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="05bca-113">如果您有關于如何改進本指南的意見，請在中提交意見反應 <https://aka.ms/ebookfeedback> 。</span><span class="sxs-lookup"><span data-stu-id="05bca-113">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="05bca-114">學分</span><span class="sxs-lookup"><span data-stu-id="05bca-114">Credits</span></span>

<span data-ttu-id="05bca-115">作者︰</span><span class="sxs-lookup"><span data-stu-id="05bca-115">Author:</span></span>

> <span data-ttu-id="05bca-116">**Cesar de la Torre**，Sr. Microsoft Corp. .NET 產品小組 PM</span><span class="sxs-lookup"><span data-stu-id="05bca-116">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="05bca-117">收購編輯器：</span><span class="sxs-lookup"><span data-stu-id="05bca-117">Acquisitions Editor:</span></span>

> <span data-ttu-id="05bca-118">**Janine 派翠克**</span><span class="sxs-lookup"><span data-stu-id="05bca-118">**Janine Patrick**</span></span>

<span data-ttu-id="05bca-119">開發編輯器：</span><span class="sxs-lookup"><span data-stu-id="05bca-119">Developmental Editor:</span></span>

> <span data-ttu-id="05bca-120">Microsoft 的 Microsoft 解決方案專業人員 **Bob Russell**</span><span class="sxs-lookup"><span data-stu-id="05bca-120">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="05bca-121">**八進位發行，Inc。**</span><span class="sxs-lookup"><span data-stu-id="05bca-121">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="05bca-122">編輯生產：</span><span class="sxs-lookup"><span data-stu-id="05bca-122">Editorial Production:</span></span>

> [<span data-ttu-id="05bca-123">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="05bca-123">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="05bca-124">**八進位發行，Inc。**</span><span class="sxs-lookup"><span data-stu-id="05bca-124">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="05bca-125">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="05bca-125">Copyeditor:</span></span>

> <span data-ttu-id="05bca-126">Microsoft 的 Microsoft 解決方案專業人員 **Bob Russell**</span><span class="sxs-lookup"><span data-stu-id="05bca-126">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="05bca-127">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="05bca-127">Participants and reviewers:</span></span>

> <span data-ttu-id="05bca-128">**Nish Anil**，Microsoft NET 小組資深方案經理</span><span class="sxs-lookup"><span data-stu-id="05bca-128">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="05bca-129">以簡單的概念 **Miguel Veloso** 軟體發展工程師</span><span class="sxs-lookup"><span data-stu-id="05bca-129">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="05bca-130">Neudesic 提供的首席顧問 **Sumit Ghosh**</span><span class="sxs-lookup"><span data-stu-id="05bca-130">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="05bca-131">著作權</span><span class="sxs-lookup"><span data-stu-id="05bca-131">Copyright</span></span>

<span data-ttu-id="05bca-132">發行者</span><span class="sxs-lookup"><span data-stu-id="05bca-132">PUBLISHED BY</span></span>

<span data-ttu-id="05bca-133">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="05bca-133">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="05bca-134">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="05bca-134">A division of Microsoft Corporation</span></span>

<span data-ttu-id="05bca-135">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="05bca-135">One Microsoft Way</span></span>

<span data-ttu-id="05bca-136">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="05bca-136">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="05bca-137">&copy;Microsoft Corporation 的著作權2021</span><span class="sxs-lookup"><span data-stu-id="05bca-137">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="05bca-138">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="05bca-138">All rights reserved.</span></span> <span data-ttu-id="05bca-139">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="05bca-139">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="05bca-140">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="05bca-140">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="05bca-141">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="05bca-141">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="05bca-142">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="05bca-142">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="05bca-143">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="05bca-143">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="05bca-144">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="05bca-144">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="05bca-145">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="05bca-145">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="05bca-146">Docker whale 標誌是 Docker，Inc. 所用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="05bca-146">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="05bca-147">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="05bca-147">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="05bca-148">下一步</span><span class="sxs-lookup"><span data-stu-id="05bca-148">Next</span></span>](introduction-to-containers-and-docker.md)
