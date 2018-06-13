---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0e384fabca88d8ad6f93ae626140fb3d5dcaf971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589318"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="9b68c-104">決策資料表：用於 Docker 的 .NET Frameworks</span><span class="sxs-lookup"><span data-stu-id="9b68c-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="9b68c-105">以下摘述要使用 .NET Framework 或 .NET Core，以及 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="9b68c-105">The following summarizes whether to use .NET Framework or .NET Core, and Windows or Linux containers.</span></span> <span data-ttu-id="9b68c-106">請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。</span><span class="sxs-lookup"><span data-stu-id="9b68c-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

<span data-ttu-id="9b68c-107">您的應用程式有幾項功能會影響您的決定。</span><span class="sxs-lookup"><span data-stu-id="9b68c-107">There are several features of your application that affect your decision.</span></span> <span data-ttu-id="9b68c-108">在做決定時，您應該衡量這些功能的重要性。</span><span class="sxs-lookup"><span data-stu-id="9b68c-108">You should weigh the importance of these features when making your decision.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b68c-109">您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="9b68c-109">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="9b68c-110">您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。</span><span class="sxs-lookup"><span data-stu-id="9b68c-110">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

* <span data-ttu-id="9b68c-111">您的應用程式架構選擇是**容器上的微服務**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-111">Your application architecture choice is **Microservices on containers**.</span></span>
    - <span data-ttu-id="9b68c-112">您的 .NET 實作選擇應該是 *.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-112">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="9b68c-113">您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-113">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="9b68c-114">您的應用程式架構選擇是**整合型應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-114">Your application architecture choice is a **Monolithic application**.</span></span>
    - <span data-ttu-id="9b68c-115">您的 .NET 實作選擇可以是 *.NET Core* 或 *.NET Framework*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-115">Your .NET implementation choice can be either *.NET Core* or *.NET Framework*.</span></span>
    - <span data-ttu-id="9b68c-116">如已選擇 *.NET Core*，則您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-116">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="9b68c-117">如已選擇 *.NET Framework*，則您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-117">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="9b68c-118">您的應用程式是**新的容器型開發 (「綠燈區」)**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-118">Your application is a  **New container-based development ("green-field")**.</span></span>
    - <span data-ttu-id="9b68c-119">您的 .NET 實作選擇應該是 *.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-119">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="9b68c-120">您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-120">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="9b68c-121">您的應用程式是 **Windows Server 舊版應用程式 (「棕地」) 移轉至容器**</span><span class="sxs-lookup"><span data-stu-id="9b68c-121">Your application is a **Windows Server legacy app ("brown-field") migration to containers**</span></span>
    - <span data-ttu-id="9b68c-122">您的 .NET 實作選擇是以架構相依性為基礎的 *.NET Framework*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-122">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="9b68c-123">因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-123">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="9b68c-124">您的應用程式設計目的是**最高等級的效能和延展性**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-124">Your application's design goal is **Best-in-class performance and scalability**.</span></span>
    - <span data-ttu-id="9b68c-125">您的 .NET 實作選擇應該是 *.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-125">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="9b68c-126">您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-126">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="9b68c-127">您使用 **ASP.NET Core** 組建應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b68c-127">You built your application using **ASP.NET Core**.</span></span>
    - <span data-ttu-id="9b68c-128">您的 .NET 實作選擇應該是 *.NET Core*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-128">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="9b68c-129">如果您有其他架構相依性，可以使用 *.NET Framework* 實作。</span><span class="sxs-lookup"><span data-stu-id="9b68c-129">You can use the *.NET Framework* implementation, if you have other framework dependencies.</span></span>
    - <span data-ttu-id="9b68c-130">如已選擇 *.NET Core*，則您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-130">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="9b68c-131">如已選擇 *.NET Framework*，則您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-131">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="9b68c-132">您使用 **ASP.NET 4 (MVC 5、Web API 2 和 Web Forms)** 組建應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b68c-132">You built your application using **ASP.NET 4 (MVC 5, Web API 2, and Web Forms)**.</span></span>
    - <span data-ttu-id="9b68c-133">您的 .NET 實作選擇是以架構相依性為基礎的 *.NET Framework*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-133">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="9b68c-134">因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-134">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="9b68c-135">您的應用程式使用 **SignalR 服務**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-135">Your application uses **SignalR services**.</span></span>
    - <span data-ttu-id="9b68c-136">您的 .NET 實作選擇可以是 *.NET Framework* 或 *.NET Core 2.1 (發行後) 或更新版本*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-136">Your .NET implementation choice can be *.NET Framework*, or *.NET Core 2.1 (when released) or later*.</span></span>
    - <span data-ttu-id="9b68c-137">如果在 .NET Framework 中選擇 SignalR 實作，您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-137">Your container platform choice must be *Windows containers* if you chose the SignalR implementation in .NET Framework.</span></span>
    - <span data-ttu-id="9b68c-138">如果您在 .NET Core 2.1 或更新版本 (發行後) 中選擇 SignalR 實作，您的容器平台選擇可以是 Linux 容器或 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="9b68c-138">Your container platform choice can be either Linux containers or Windows containers if you chose the SignalR implementation in .NET Core 2.1 or later (when released).</span></span>  
    - <span data-ttu-id="9b68c-139">在 *.NET Core* 執行 **SignalR 服務**時，您可以使用「Linux 容器或 Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-139">When **SignalR services** run on *.NET Core*, you can use *Linux containers or Windows Containers*.</span></span>
* <span data-ttu-id="9b68c-140">您的應用程式使用 **WCF、WF 和其他舊版架構**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-140">Your application uses **WCF, WF, and other legacy frameworks**.</span></span>
    - <span data-ttu-id="9b68c-141">您的 .NET 實作選擇是 *.NET Framework* 或 *.NET Core (未來的版本藍圖)*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-141">Your .NET implementation choice is *.NET Framework*, or *.NET Core (in the roadmap for a future release)*.</span></span>
    - <span data-ttu-id="9b68c-142">因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-142">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="9b68c-143">您的應用程式牽涉到**取用 Azure 服務**。</span><span class="sxs-lookup"><span data-stu-id="9b68c-143">Your application involves **Consumption of Azure services**.</span></span>
    - <span data-ttu-id="9b68c-144">您的 .NET 實作選擇是 *.NET Framework* 或 *.NET Core (所有 Azure 服務最終都會提供適用於 .NET Core 的用戶端 SDK)*。</span><span class="sxs-lookup"><span data-stu-id="9b68c-144">Your .NET implementation choice is *.NET Framework*, or *.NET Core (eventually all Azure services will provide client SDKs for .NET Core)*.</span></span>
    - <span data-ttu-id="9b68c-145">如果使用 .NET Framework 用戶端 API，您的容器平台選擇必須是「Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-145">Your container platform choice must be *Windows containers* if you use .NET Framework client APIs.</span></span>
    - <span data-ttu-id="9b68c-146">如果使用 *.NET Core* 可用的用戶端 API，您也可以選擇「Linux 容器或 Windows 容器」。</span><span class="sxs-lookup"><span data-stu-id="9b68c-146">If you use client APIs available for *.NET Core*, you can also choose between *Linux containers and Windows containers*.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9b68c-147">[上一頁] (net-framework-container-scenarios.md) [下一頁] (net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="9b68c-147">[Previous] (net-framework-container-scenarios.md) [Next] (net-container-os-targets.md)</span></span>
