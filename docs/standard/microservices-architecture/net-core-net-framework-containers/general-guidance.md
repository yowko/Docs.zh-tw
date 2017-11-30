---
title: "一般指導方針"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |一般指導方針"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a><span data-ttu-id="c59ec-104">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="c59ec-104">General guidance</span></span>

<span data-ttu-id="c59ec-105">本節提供何時選擇.NET Core 或.NET Framework 的摘要。</span><span class="sxs-lookup"><span data-stu-id="c59ec-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="c59ec-106">我們提供更多詳細以下各節中的這些選項。</span><span class="sxs-lookup"><span data-stu-id="c59ec-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="c59ec-107">您應該使用.NET Core Linux 或 Windows 容器 Docker 伺服器應用程式容器化時：</span><span class="sxs-lookup"><span data-stu-id="c59ec-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="c59ec-108">您有跨平台需求。</span><span class="sxs-lookup"><span data-stu-id="c59ec-108">You have cross-platform needs.</span></span> <span data-ttu-id="c59ec-109">例如，您要使用 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="c59ec-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="c59ec-110">您的應用程式的架構根據 microservices。</span><span class="sxs-lookup"><span data-stu-id="c59ec-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="c59ec-111">您需要快速啟動容器，而且想以降低成本的每個容器，以達到更佳的密度或更多的容器，每個硬體單位佔空間很小。</span><span class="sxs-lookup"><span data-stu-id="c59ec-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="c59ec-112">簡單地說，當您建立新容器化的.NET 應用程式，您應該考慮.NET Core 以預設選項。</span><span class="sxs-lookup"><span data-stu-id="c59ec-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="c59ec-113">它有許多優點，並最符合的原理容器和工作樣式。</span><span class="sxs-lookup"><span data-stu-id="c59ec-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="c59ec-114">使用.NET Core 的另一個優點是，您可以執行並存的同一部電腦中的應用程式的.NET 版本。</span><span class="sxs-lookup"><span data-stu-id="c59ec-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="c59ec-115">這項優點是更重要的伺服器或不使用容器，容器的 Vm，因為容器隔離的應用程式所需的.NET 版本。</span><span class="sxs-lookup"><span data-stu-id="c59ec-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="c59ec-116">（只要它們是與基礎作業系統相容。）</span><span class="sxs-lookup"><span data-stu-id="c59ec-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="c59ec-117">您應該使用.NET Framework 中，使用 Windows 容器 Docker 伺服器應用程式容器化時：</span><span class="sxs-lookup"><span data-stu-id="c59ec-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="c59ec-118">目前應用程式會使用.NET Framework 和 Windows 具有強式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c59ec-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="c59ec-119">您需要使用.NET 核心不支援的 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="c59ec-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="c59ec-120">您要使用協力廠商.NET 程式庫或不適用於.NET Core 的 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="c59ec-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="c59ec-121">在 Docker 中使用.NET Framework 可以改善您的部署經驗部署問題降至最低。</span><span class="sxs-lookup"><span data-stu-id="c59ec-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="c59ec-122">這[ *「 提起和 shift 」 案例*](https://aka.ms/liftandshiftwithcontainersebook)是很重要的 containerizing 原本是開發與傳統.NET Framework 中，像 ASP.NET WebForms、 MVC web 應用程式或 WCF （的舊版應用程式Windows Communication Foundation) 服務。</span><span class="sxs-lookup"><span data-stu-id="c59ec-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c59ec-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="c59ec-123">Additional resources</span></span>

-   <span data-ttu-id="c59ec-124">**電子書： 現代化現有的.NET Framework 應用程式使用 Azure 和 Windows 容器**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="c59ec-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="c59ec-125">**範例應用程式： 現代化的舊版 ASP.NET web 應用程式，藉由使用 Windows 容器**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="c59ec-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c59ec-126">[上一個](index.md) [下一步] (net-核心-容器-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="c59ec-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>
