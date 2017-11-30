---
title: "決策表。 要用於 Docker 的.NET framework"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |決定資料表中，用於 Docker 的.NET framework"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="b91a2-105">決定資料表： 用於 Docker 的.NET framework</span><span class="sxs-lookup"><span data-stu-id="b91a2-105">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="b91a2-106">以下摘述是否要使用.NET Framework 或.NET Core 和 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="b91a2-106">The following summarizes whether to use .NET Framework or .NET Core, and Windows or Linux containers.</span></span> <span data-ttu-id="b91a2-107">請記住，對於 Linux 容器，您需要以 Linux 為基礎的 Docker 主機 （Vm 或伺服器），Windows 容器您需要 Windows Server 為基礎的 Docker 主機 （Vm 或伺服器）。</span><span class="sxs-lookup"><span data-stu-id="b91a2-107">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

<span data-ttu-id="b91a2-108">有數個會影響您的決定應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="b91a2-108">There are several features of your application that affect your decision.</span></span> <span data-ttu-id="b91a2-109">在做決定時，您應該衡量這些功能的重要性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-109">You should weigh the importance of these features when making your decision.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b91a2-110">您的開發電腦將會執行一部 Docker 主機，Linux 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="b91a2-110">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="b91a2-111">您想要執行和一起測試在單一解決方案中的相關的 microservices 所有必須在相同的容器平台上執行。</span><span class="sxs-lookup"><span data-stu-id="b91a2-111">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

* <span data-ttu-id="b91a2-112">您的應用程式架構的選擇是**容器 Microservices**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-112">Your application architecture choice is **Microservices on containers**.</span></span>
    - <span data-ttu-id="b91a2-113">您的.NET 實作選擇應該是*.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-113">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="b91a2-114">容器的平台選擇可以是*Linux 容器*或*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-114">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="b91a2-115">您的應用程式架構的選擇是**整合型應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-115">Your application architecture choice is a **Monolithic application**.</span></span>
    - <span data-ttu-id="b91a2-116">您的.NET 實作選擇可以是*.NET Core*或*.NET Framework*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-116">Your .NET implementation choice can be either *.NET Core* or *.NET Framework*.</span></span>
    - <span data-ttu-id="b91a2-117">如果您已選擇*.NET Core*，容器平台的選擇可以是*Linux 容器*或*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-117">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="b91a2-118">如果您已選擇*.NET Framework*，必須是容器的平台選擇*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-118">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="b91a2-119">您的應用程式**新容器為基礎的開發工作 （「 綠色欄位 」）**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-119">Your application is a  **New container-based development ("green-field")**.</span></span>
    - <span data-ttu-id="b91a2-120">您的.NET 實作選擇應該是*.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-120">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="b91a2-121">容器的平台選擇可以是*Linux 容器*或*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-121">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="b91a2-122">您的應用程式**Windows Server 容器的舊版應用程式 ("brown-field") 移轉**</span><span class="sxs-lookup"><span data-stu-id="b91a2-122">Your application is a **Windows Server legacy app ("brown-field") migration to containers**</span></span>
    - <span data-ttu-id="b91a2-123">在.NET 實作選擇時*.NET Framework*基礎架構相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-123">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="b91a2-124">必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-124">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="b91a2-125">您的應用程式的設計目的是**最高等級效能和延展性**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-125">Your application's design goal is **Best-in-class performance and scalability**.</span></span>
    - <span data-ttu-id="b91a2-126">您的.NET 實作選擇應該是*.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-126">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="b91a2-127">容器的平台選擇可以是*Linux 容器*或*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-127">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="b91a2-128">您建立應用程式使用**ASP.NET Core**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-128">You built your application using **ASP.NET Core**.</span></span>
    - <span data-ttu-id="b91a2-129">您的.NET 實作選擇應該是*.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-129">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="b91a2-130">您可以使用*.NET Framework*實作中，如果您有其他架構相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-130">You can use the *.NET Framework* implementation, if you have other framework dependencies.</span></span>
    - <span data-ttu-id="b91a2-131">如果您已選擇*.NET Core*，容器平台的選擇可以是*Linux 容器*或*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-131">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="b91a2-132">如果您已選擇*.NET Framework*，必須是容器的平台選擇*Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-132">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="b91a2-133">您建立應用程式使用**（MVC 5、 Web API 2 和 Web Form） 的 ASP.NET 4**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-133">You built your application using **ASP.NET 4 (MVC 5, Web API 2, and Web Forms)**.</span></span>
    - <span data-ttu-id="b91a2-134">在.NET 實作選擇時*.NET Framework*基礎架構相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-134">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="b91a2-135">必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-135">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="b91a2-136">您的應用程式會使用**SignalR 服務**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-136">Your application uses **SignalR services**.</span></span>
    - <span data-ttu-id="b91a2-137">.NET 的實作做出選擇可能很*.NET Framework*，或*（發行時），.NET Core 2.1 或更新版本*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-137">Your .NET implementation choice can be *.NET Framework*, or *.NET Core 2.1 (when released) or later*.</span></span>
    - <span data-ttu-id="b91a2-138">必須是容器的平台選擇*Windows 容器*如果您選擇.NET Framework 中的 SignalR 實作。</span><span class="sxs-lookup"><span data-stu-id="b91a2-138">Your container platform choice must be *Windows containers* if you chose the SignalR implementation in .NET Framework.</span></span>
    - <span data-ttu-id="b91a2-139">如果您選擇的 SignalR 實作.NET Core 2.1 或更新版本 （發行時），Linux 容器或 Windows 容器可以是容器平台的選擇。</span><span class="sxs-lookup"><span data-stu-id="b91a2-139">Your container platform choice can be either Linux containers or Windows containers if you chose the SignalR implementation in .NET Core 2.1 or later (when released).</span></span>  
    - <span data-ttu-id="b91a2-140">當**SignalR 服務**上執行*.NET Core*，您可以使用*Linux 容器或 Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-140">When **SignalR services** run on *.NET Core*, you can use *Linux containers or Windows Containers*.</span></span>
* <span data-ttu-id="b91a2-141">您的應用程式會使用**WCF、 WF、 和其他舊版架構**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-141">Your application uses **WCF, WF, and other legacy frameworks**.</span></span>
    - <span data-ttu-id="b91a2-142">在.NET 實作選擇時*.NET Framework*，或*.NET Core （在未來的版本藍圖）*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-142">Your .NET implementation choice is *.NET Framework*, or *.NET Core (in the roadmap for a future release)*.</span></span>
    - <span data-ttu-id="b91a2-143">必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。</span><span class="sxs-lookup"><span data-stu-id="b91a2-143">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="b91a2-144">您的應用程式牽涉到**耗用量的 Azure 服務**。</span><span class="sxs-lookup"><span data-stu-id="b91a2-144">Your application involves **Consumption of Azure services**.</span></span>
    - <span data-ttu-id="b91a2-145">在.NET 實作選擇時*.NET Framework*，或*（最終所有 Azure 服務會提供用戶端 Sdk 適用於.NET Core） 的.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-145">Your .NET implementation choice is *.NET Framework*, or *.NET Core (eventually all Azure services will provide client SDKs for .NET Core)*.</span></span>
    - <span data-ttu-id="b91a2-146">必須是容器的平台選擇*Windows 容器*如果您使用.NET Framework 用戶端應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="b91a2-146">Your container platform choice must be *Windows containers* if you use .NET Framework client APIs.</span></span>
    - <span data-ttu-id="b91a2-147">如果您使用用戶端應用程式開發介面可供*.NET Core*，您也可以選擇*Linux 容器和 Windows 容器*。</span><span class="sxs-lookup"><span data-stu-id="b91a2-147">If you use client APIs available for *.NET Core*, you can also choose between *Linux containers and Windows containers*.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b91a2-148">[上一個](net-framework 的容器-scenarios.md) [下一步] (net-容器-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="b91a2-148">[Previous] (net-framework-container-scenarios.md) [Next] (net-container-os-targets.md)</span></span>
