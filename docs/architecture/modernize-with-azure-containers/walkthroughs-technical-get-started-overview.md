---
title: 逐步解說和技術入門概觀
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |演練和技術入門概述
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660890"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="b2856-103">逐步解說和技術入門概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="b2856-104">為了限制此電子書的大小，在 GitHub 存儲庫中提供了其他技術文檔和完整的演練。</span><span class="sxs-lookup"><span data-stu-id="b2856-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="b2856-105">本章中描述的線上系列演練介紹了基於 Windows 容器的多個環境的分步設置以及部署到 Azure。</span><span class="sxs-lookup"><span data-stu-id="b2856-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="b2856-106">以下各節介紹每個演練的內容、目標和高級願景，並提供所涉及的任務的圖表。</span><span class="sxs-lookup"><span data-stu-id="b2856-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="b2856-107">你可以在*eShop 現代化*應用程式 GitHub 存儲庫 wiki 的<https://github.com/dotnet-architecture/eShopModernizing/wiki>eShop 現代化應用程式中獲得演練。</span><span class="sxs-lookup"><span data-stu-id="b2856-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="b2856-108">技術演練清單</span><span class="sxs-lookup"><span data-stu-id="b2856-108">Technical walkthrough list</span></span>

<span data-ttu-id="b2856-109">以下入門演練為示例應用提供一致且全面的技術指導，您可以使用容器提升和移動，然後在 Azure 中使用多個部署選項進行移動。</span><span class="sxs-lookup"><span data-stu-id="b2856-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="b2856-110">以下每個演練都使用新的示例 eShopLegacy 和 eShop 現代化應用，這些應用程式可在 GitHub 上<https://github.com/dotnet-architecture/eShopModernizing>提供。</span><span class="sxs-lookup"><span data-stu-id="b2856-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="b2856-111">**參觀 eShop 舊版應用（要進行現代化的基線應用）**</span><span class="sxs-lookup"><span data-stu-id="b2856-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="b2856-112">**使用 Windows 容器將現有ASP.NET Web 應用（Web 表單& MVC）容器化**</span><span class="sxs-lookup"><span data-stu-id="b2856-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="b2856-113">**使用 Windows 容器將現有 WCF 服務（N 層應用）容器化**</span><span class="sxs-lookup"><span data-stu-id="b2856-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="b2856-114">**將基於 Windows 容器的應用部署到 Azure VM**</span><span class="sxs-lookup"><span data-stu-id="b2856-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="b2856-115">**在 Azure 容器服務中將基於 Windows 容器的應用部署到庫伯內斯**</span><span class="sxs-lookup"><span data-stu-id="b2856-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="b2856-116">演練 1：eShop 傳統應用之旅</span><span class="sxs-lookup"><span data-stu-id="b2856-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b2856-117">技術演練可用性</span><span class="sxs-lookup"><span data-stu-id="b2856-117">Technical walkthrough availability</span></span>

<span data-ttu-id="b2856-118">完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：</span><span class="sxs-lookup"><span data-stu-id="b2856-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="b2856-119">eShop 現代化維琪演練</span><span class="sxs-lookup"><span data-stu-id="b2856-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="b2856-120">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-120">Overview</span></span>

<span data-ttu-id="b2856-121">在本演練中，您可以探討三個示例遺留應用程式的初始實現。</span><span class="sxs-lookup"><span data-stu-id="b2856-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="b2856-122">前兩個示例 Web 應用具有整體體系結構，並使用經典ASP.NET創建。</span><span class="sxs-lookup"><span data-stu-id="b2856-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="b2856-123">一個應用程式基於ASP.NET 4.x MVC;第二個應用程式基於ASP.NET 4.x Web 表單。</span><span class="sxs-lookup"><span data-stu-id="b2856-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="b2856-124">第三個應用是由用戶端 WinForms 應用和伺服器端[Windows 通信基礎 （WCF）](../../framework/wcf/whats-wcf.md)服務組成的 3 層應用。</span><span class="sxs-lookup"><span data-stu-id="b2856-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="b2856-125">所有這些應用程式都可以在[eShop現代化GitHub存儲庫](https://github.com/dotnet-architecture/eShopModernizing)中使用。</span><span class="sxs-lookup"><span data-stu-id="b2856-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-126">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-126">Goals</span></span>

<span data-ttu-id="b2856-127">本演練的主要目標是熟悉這些應用及其代碼和配置。</span><span class="sxs-lookup"><span data-stu-id="b2856-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="b2856-128">您可以配置應用，以便它們生成和使用類比資料，而無需使用 SQL 資料庫進行測試。</span><span class="sxs-lookup"><span data-stu-id="b2856-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="b2856-129">此可選配置基於依賴項注入，以分離方式使用。</span><span class="sxs-lookup"><span data-stu-id="b2856-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="b2856-130">方案 1：ASP.NET Web 應用</span><span class="sxs-lookup"><span data-stu-id="b2856-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="b2856-131">下圖顯示了原始遺留ASP.NET Web 應用程式的簡單方案。</span><span class="sxs-lookup"><span data-stu-id="b2856-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![原始遺留ASP.NET Web 應用程式的簡單體系結構方案](./media/image5-1.png)

<span data-ttu-id="b2856-133">從業務域的角度來看，這兩個應用都提供相同的目錄管理功能。</span><span class="sxs-lookup"><span data-stu-id="b2856-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="b2856-134">eShop 企業團隊的成員將使用該應用程式查看和編輯產品目錄。</span><span class="sxs-lookup"><span data-stu-id="b2856-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="b2856-135">下圖顯示了初始應用螢幕截圖。</span><span class="sxs-lookup"><span data-stu-id="b2856-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC 和ASP.NET Web 表單應用程式（現有/遺留技術）](./media/image5-2.png)

<span data-ttu-id="b2856-137">ASP.NET 4.x 或早期版本中的依賴項（對於 MVC 或 Web 表單）意味著這些應用程式不會在 .NET Core 上運行，除非使用 ASP.NET 核心 MVC 完全重寫代碼。</span><span class="sxs-lookup"><span data-stu-id="b2856-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="b2856-138">方案 2：WCF 服務和 WinForms 用戶端應用（3 層應用）</span><span class="sxs-lookup"><span data-stu-id="b2856-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="b2856-139">下圖顯示了原始 3 層舊應用程式的簡單方案。</span><span class="sxs-lookup"><span data-stu-id="b2856-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![具有 WCF 服務和 WinForms 用戶端應用的原始傳統 3 層應用的簡單體系結構方案](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="b2856-141">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-141">Benefits</span></span>

<span data-ttu-id="b2856-142">本演練的好處很簡單：只需熟悉代碼和初始應用即可。</span><span class="sxs-lookup"><span data-stu-id="b2856-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="b2856-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-143">Next steps</span></span>

<span data-ttu-id="b2856-144">在 GitHub wiki 上更深入地流覽此內容：</span><span class="sxs-lookup"><span data-stu-id="b2856-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="b2856-145">在 MVC 和 Web 表單"舊"應用ASP.NET基線進行巡視</span><span class="sxs-lookup"><span data-stu-id="b2856-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="b2856-146">流覽基線 WCF 服務和 WinForms（3 層）"舊"應用程式</span><span class="sxs-lookup"><span data-stu-id="b2856-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="b2856-147">演練 2：使用 Windows 容器對現有的 .NET 應用程式進行容器化</span><span class="sxs-lookup"><span data-stu-id="b2856-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="b2856-148">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-148">Overview</span></span>

<span data-ttu-id="b2856-149">使用 Windows 容器改進現有 .NET 應用程式的部署，例如基於 MVC、Web 表單或 WCF 的應用程式，以生產、開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="b2856-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-150">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-150">Goals</span></span>

<span data-ttu-id="b2856-151">本演練的目標是向您展示用於容器化現有 .NET 框架應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="b2856-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="b2856-152">您可以：</span><span class="sxs-lookup"><span data-stu-id="b2856-152">You can:</span></span>

- <span data-ttu-id="b2856-153">使用 Visual Studio [2017 Docker 工具](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)（Visual Studio 2017 或更高版本）對應用程式進行容器化。</span><span class="sxs-lookup"><span data-stu-id="b2856-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="b2856-154">通過手動添加[Docker 檔](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)來容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2856-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="b2856-155">使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具（Docker 的開源工具）對應用程式進行容器化。</span><span class="sxs-lookup"><span data-stu-id="b2856-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="b2856-156">本演練重點介紹 Visual Studio 2017 Docker 工具方法，但其他兩種方法在使用 Dockerfile 方面相當相似。</span><span class="sxs-lookup"><span data-stu-id="b2856-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="b2856-157">方案 1：容器化ASP.NET Web 應用</span><span class="sxs-lookup"><span data-stu-id="b2856-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="b2856-158">下圖顯示了容器化 eShop 舊版 Web 應用程式的方案。</span><span class="sxs-lookup"><span data-stu-id="b2856-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![簡化開發環境中的容器化ASP.NET應用程式的體系結構圖](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="b2856-160">方案 2：容器化 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b2856-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="b2856-161">下圖顯示了具有容器化 WCF 服務的 3 層應用的方案。</span><span class="sxs-lookup"><span data-stu-id="b2856-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![開發環境中容器化 WCF 服務的簡化體系結構圖](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="b2856-163">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-163">Benefits</span></span>

<span data-ttu-id="b2856-164">在容器中運行整體應用程式具有優勢。</span><span class="sxs-lookup"><span data-stu-id="b2856-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="b2856-165">首先，為應用程式創建映射。</span><span class="sxs-lookup"><span data-stu-id="b2856-165">First, you create an image for the application.</span></span> <span data-ttu-id="b2856-166">從那時起，每個部署都在同一環境中運行。</span><span class="sxs-lookup"><span data-stu-id="b2856-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="b2856-167">每個容器使用相同的作業系統版本，安裝相同的依賴項版本，使用相同的 .NET 框架版本，並且使用相同的進程構建。</span><span class="sxs-lookup"><span data-stu-id="b2856-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="b2856-168">基本上，您可以使用 Docker 映射來控制應用程式的依賴項。</span><span class="sxs-lookup"><span data-stu-id="b2856-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="b2856-169">部署容器時，依賴項隨應用程式一起移動。</span><span class="sxs-lookup"><span data-stu-id="b2856-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="b2856-170">另一個好處是，開發人員可以在 Windows 容器提供的一致環境中運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2856-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="b2856-171">可以立即發現僅在某些版本中顯示的問題，而不是在暫存或生產環境中出現。</span><span class="sxs-lookup"><span data-stu-id="b2856-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="b2856-172">當應用程式在容器中運行時，開發團隊成員使用的開發環境的差異就不那麼重要了。</span><span class="sxs-lookup"><span data-stu-id="b2856-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="b2856-173">容器化應用也有平坦的橫向擴展曲線。</span><span class="sxs-lookup"><span data-stu-id="b2856-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="b2856-174">與每台電腦的常規應用程式部署相比，容器化應用使您能夠在 VM 或物理電腦中有更多的應用程式和服務實例（基於容器）。</span><span class="sxs-lookup"><span data-stu-id="b2856-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="b2856-175">這轉化為更高的密度和更少的所需資源，特別是當您使用像 Kubernetes 這樣的協調器時。</span><span class="sxs-lookup"><span data-stu-id="b2856-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="b2856-176">在理想情況下，容器化不需要對應用程式代碼 （C\#） 進行任何更改。</span><span class="sxs-lookup"><span data-stu-id="b2856-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="b2856-177">在大多數情況下，您只需要 Docker 部署元資料檔案（Dockerfile 和 Docker 撰寫檔）。</span><span class="sxs-lookup"><span data-stu-id="b2856-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="b2856-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-178">Next steps</span></span>

<span data-ttu-id="b2856-179">在 GitHub wiki 上更深入地流覽此內容：</span><span class="sxs-lookup"><span data-stu-id="b2856-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="b2856-180">如何使用 Windows 容器和 Docker 對 .NET 框架 Web 應用進行容器化</span><span class="sxs-lookup"><span data-stu-id="b2856-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="b2856-181">將 Docker 支援添加到 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b2856-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="b2856-182">演練 3：將基於 Windows 容器的應用部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b2856-183">技術演練可用性</span><span class="sxs-lookup"><span data-stu-id="b2856-183">Technical walkthrough availability</span></span>

<span data-ttu-id="b2856-184">完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="b2856-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="b2856-185">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-185">Overview</span></span>

<span data-ttu-id="b2856-186">部署到 Azure 中的 Windows Server 2016 虛擬機器 （VM） 上的 Docker 主機，可以快速設置開發/測試/暫存環境。</span><span class="sxs-lookup"><span data-stu-id="b2856-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="b2856-187">它還為測試人員或企業用戶提供了驗證應用的常見位置。</span><span class="sxs-lookup"><span data-stu-id="b2856-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="b2856-188">VM 也可以是有效的基礎架構即服務 （IaaS） 生產環境。</span><span class="sxs-lookup"><span data-stu-id="b2856-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-189">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-189">Goals</span></span>

<span data-ttu-id="b2856-190">本演練的目標是向您展示將 Windows 容器部署到基於 Windows Server 2016 或更高版本的 Azure VM 時具有的多種替代方法。</span><span class="sxs-lookup"><span data-stu-id="b2856-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b2856-191">案例</span><span class="sxs-lookup"><span data-stu-id="b2856-191">Scenarios</span></span>

<span data-ttu-id="b2856-192">本演練將介紹幾種方案。</span><span class="sxs-lookup"><span data-stu-id="b2856-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="b2856-193">方案 A：通過 Docker 引擎連接從開發 PC 部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![通過 Docker 引擎連接從開發 PC 部署到 Azure VM](./media/image5-4.png)

<span data-ttu-id="b2856-195">**圖 5-4。**</span><span class="sxs-lookup"><span data-stu-id="b2856-195">**Figure 5-4.**</span></span> <span data-ttu-id="b2856-196">通過 Docker 引擎連接從開發 PC 部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="b2856-197">方案 B：通過 Docker 註冊表部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![通過 Docker 註冊表部署到 Azure VM](./media/image5-5.png)

<span data-ttu-id="b2856-199">**圖 5-5。**</span><span class="sxs-lookup"><span data-stu-id="b2856-199">**Figure 5-5.**</span></span> <span data-ttu-id="b2856-200">通過 Docker 註冊表部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="b2856-201">方案 C：從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM](./media/image5-6.png)

<span data-ttu-id="b2856-203">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="b2856-203">**Figure 5-6.**</span></span> <span data-ttu-id="b2856-204">從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="b2856-205">用於 Windows 容器的 Azure VM</span><span class="sxs-lookup"><span data-stu-id="b2856-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="b2856-206">Windows 容器的 Azure VM 是基於 Windows 伺服器 2016、Windows 10 或更高版本的 VM，兩者都設置了 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="b2856-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="b2856-207">在大多數情況下，Windows Server 2016 在 Azure VM 中使用。</span><span class="sxs-lookup"><span data-stu-id="b2856-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="b2856-208">Azure 目前提供一個名為**Windows Server 2016 的 VM，其中包含容器**。</span><span class="sxs-lookup"><span data-stu-id="b2856-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="b2856-209">您可以使用此 VM 嘗試新的 Windows 伺服器容器功能，使用 Windows 伺服器核心或 Windows Nano 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b2856-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="b2856-210">安裝容器作業系統映射，然後 VM 即可與 Docker 一起使用。</span><span class="sxs-lookup"><span data-stu-id="b2856-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="b2856-211">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-211">Benefits</span></span>

<span data-ttu-id="b2856-212">儘管 Windows 容器可以部署到本地 Windows Server 2016 VM，但當您部署到 Azure 時，您可以通過隨時使用的 Windows Server 容器 VM 獲得一種更簡單的入門方法。</span><span class="sxs-lookup"><span data-stu-id="b2856-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="b2856-213">您還可以獲得測試人員可訪問的常見連線位置，以及通過 Azure 虛擬機器縮放集自動可伸縮。</span><span class="sxs-lookup"><span data-stu-id="b2856-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="b2856-214">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-214">Next steps</span></span>

<span data-ttu-id="b2856-215">在 GitHub wiki 上更深入地流覽此內容：</span><span class="sxs-lookup"><span data-stu-id="b2856-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="b2856-216">演練 4：將基於 Windows 容器的應用部署到 Azure 容器實例 （ACI）</span><span class="sxs-lookup"><span data-stu-id="b2856-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b2856-217">技術演練可用性</span><span class="sxs-lookup"><span data-stu-id="b2856-217">Technical walkthrough availability</span></span>

<span data-ttu-id="b2856-218">完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：</span><span class="sxs-lookup"><span data-stu-id="b2856-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="b2856-219">[將應用部署到 ACI（Azure 容器實例）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="b2856-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="b2856-220">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-220">Overview</span></span>

<span data-ttu-id="b2856-221">[Azure 容器實例 （ACI）](https://docs.microsoft.com/azure/container-instances/)是具有容器開發/測試/暫存環境的最快方法，您可以在其中部署容器的單個實例。</span><span class="sxs-lookup"><span data-stu-id="b2856-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-222">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-222">Goals</span></span>

<span data-ttu-id="b2856-223">本演練將 Windows 容器部署到 Azure 容器實例 （ACI） 時的主要方案，以及如何將 eShop 現代化應用部署到 ACI 中。</span><span class="sxs-lookup"><span data-stu-id="b2856-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b2856-224">案例</span><span class="sxs-lookup"><span data-stu-id="b2856-224">Scenarios</span></span>

<span data-ttu-id="b2856-225">在將 eShop 現代化應用部署到 ACI 方面可能會有一些差異，例如只部署一個或多個應用（MVC 應用、WebForms 應用或 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="b2856-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="b2856-226">在下面顯示的以下方案中，您可以看到ASP.NET MVC 應用以及 SQL Server 容器都作為容器部署到 ACI（Azure 容器實例）中。</span><span class="sxs-lookup"><span data-stu-id="b2856-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![從開發環境部署到 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="b2856-228">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-228">Benefits</span></span>

<span data-ttu-id="b2856-229">Azure Container Instances 能讓您在 Azure 中輕鬆建立及管理 Docker 容器，不需要佈建虛擬機器或採用高階服務即可完成。</span><span class="sxs-lookup"><span data-stu-id="b2856-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="b2856-230">使用 ACI，可以直接在 Azure 中部署 Windows 容器，並在數秒內使用完全限定的功能變數名稱 （FQDN） 將其公開到 Internet 上（前提是您在 Docker Hub 或 Azure 容器等 Docker 註冊表中準備好 Windows 容器映射註冊表）。</span><span class="sxs-lookup"><span data-stu-id="b2856-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="b2856-231">考量</span><span class="sxs-lookup"><span data-stu-id="b2856-231">Considerations</span></span>

<span data-ttu-id="b2856-232">將具有完整 .NET 框架/ASP.NET或 SQL Server 的 Windows 容器部署到 Azure 容器實例 （ACI） 的速度不如部署到常規 Docker 主機（如 Windows Server 2016 與 Windows 容器一起），因為每次必須下載 Docker 映射（從 Docker 註冊表中拉出），SQL 容器映射（15.1 GB）和ASP.NET容器映射（13.9 GB）的大小明顯較大， 然而，它比維護自己的 Docker 主機（永久線上 Windows）便宜得多伺服器 2016 在 Azure 中包含 Windows 容器 VM），更不用說像 Azure （AKS） 中的 Kubernetes 這樣的整個協調器，這是生產部署的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="b2856-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="b2856-233">作為主要結論，對於開發人員/測試方案和 CI/CD 管道，使用 Azure 容器實例是一個非常引人注目的選項。</span><span class="sxs-lookup"><span data-stu-id="b2856-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2856-234">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-234">Next steps</span></span>

<span data-ttu-id="b2856-235">在 GitHub wiki 上更深入地流覽此內容：</span><span class="sxs-lookup"><span data-stu-id="b2856-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="b2856-236">演練 5：將基於 Windows 容器的應用部署到 Azure 容器服務中的庫伯內斯</span><span class="sxs-lookup"><span data-stu-id="b2856-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b2856-237">技術演練可用性</span><span class="sxs-lookup"><span data-stu-id="b2856-237">Technical walkthrough availability</span></span>

<span data-ttu-id="b2856-238">完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：</span><span class="sxs-lookup"><span data-stu-id="b2856-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="b2856-239">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-239">Overview</span></span>

<span data-ttu-id="b2856-240">基於 Windows 容器的應用程式將快速使用平臺，甚至遠離 IaaS VM。</span><span class="sxs-lookup"><span data-stu-id="b2856-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="b2856-241">這一點對於輕鬆實現高可擴充性和更好的自動化可擴充性，以及自動化部署和版本控制的重大改進，需要這樣做。</span><span class="sxs-lookup"><span data-stu-id="b2856-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="b2856-242">您可以使用[Azure 容器服務](https://azure.microsoft.com/services/container-service/)中可用的協調器[Kubernetes](https://kubernetes.io/)來實現這些目標。</span><span class="sxs-lookup"><span data-stu-id="b2856-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-243">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-243">Goals</span></span>

<span data-ttu-id="b2856-244">本演練的目標是瞭解如何在 Azure 容器服務中將基於 Windows 容器的應用程式部署到 Kubernetes（也稱為*K8s）。*</span><span class="sxs-lookup"><span data-stu-id="b2856-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="b2856-245">從頭開始部署到庫伯奈斯是一個兩步過程：</span><span class="sxs-lookup"><span data-stu-id="b2856-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="b2856-246">將庫伯內斯群集部署到 Azure 容器服務。</span><span class="sxs-lookup"><span data-stu-id="b2856-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="b2856-247">將應用程式和相關資源部署到庫伯奈斯群集。</span><span class="sxs-lookup"><span data-stu-id="b2856-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b2856-248">案例</span><span class="sxs-lookup"><span data-stu-id="b2856-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="b2856-249">方案 A：直接從開發環境部署到庫伯奈斯群集</span><span class="sxs-lookup"><span data-stu-id="b2856-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![直接從開發環境部署到庫伯奈斯群集](./media/image5-7.png)

<span data-ttu-id="b2856-251">**圖 5-7。**</span><span class="sxs-lookup"><span data-stu-id="b2856-251">**Figure 5-7.**</span></span> <span data-ttu-id="b2856-252">直接從開發環境部署到庫伯奈斯群集</span><span class="sxs-lookup"><span data-stu-id="b2856-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="b2856-253">方案 B：從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="b2856-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集](./media/image5-8.png)

<span data-ttu-id="b2856-255">**圖 5-8。**</span><span class="sxs-lookup"><span data-stu-id="b2856-255">**Figure 5-8.**</span></span> <span data-ttu-id="b2856-256">從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="b2856-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="b2856-257">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-257">Benefits</span></span>

<span data-ttu-id="b2856-258">部署到庫貝內斯的群集有很多好處。</span><span class="sxs-lookup"><span data-stu-id="b2856-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="b2856-259">最大的好處是，您可以獲得一個生產就緒的環境，您可以在其中根據要使用的容器實例數（現有節點中的內部可伸縮性）以及群集中的節點或 VM 數量來擴展應用程式（群集的全域可伸縮性）。</span><span class="sxs-lookup"><span data-stu-id="b2856-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="b2856-260">Azure 容器服務優化了專為 Azure 而使用的熱門開源工具和技術。</span><span class="sxs-lookup"><span data-stu-id="b2856-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="b2856-261">您將獲得一個開放的解決方案，既為您的容器提供可攜性，也可用於應用程式佈建。</span><span class="sxs-lookup"><span data-stu-id="b2856-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="b2856-262">您可以選擇大小、主機數，協調器工具-容器服務處理其他所有內容。</span><span class="sxs-lookup"><span data-stu-id="b2856-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="b2856-263">借助 Kubernetes，開發人員可以從考慮物理和虛擬機器，到規劃以容器為中心的基礎結構，從而促進以下功能，等等：</span><span class="sxs-lookup"><span data-stu-id="b2856-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="b2856-264">基於多個容器的應用程式</span><span class="sxs-lookup"><span data-stu-id="b2856-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="b2856-265">複製容器實例和水準自動縮放</span><span class="sxs-lookup"><span data-stu-id="b2856-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="b2856-266">命名和發現（例如，內部 DNS）</span><span class="sxs-lookup"><span data-stu-id="b2856-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="b2856-267">平衡負載</span><span class="sxs-lookup"><span data-stu-id="b2856-267">Balancing loads</span></span>

- <span data-ttu-id="b2856-268">滾動更新</span><span class="sxs-lookup"><span data-stu-id="b2856-268">Rolling updates</span></span>

- <span data-ttu-id="b2856-269">分發機密</span><span class="sxs-lookup"><span data-stu-id="b2856-269">Distributing secrets</span></span>

- <span data-ttu-id="b2856-270">應用程式運行狀況檢查</span><span class="sxs-lookup"><span data-stu-id="b2856-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2856-271">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-271">Next steps</span></span>

<span data-ttu-id="b2856-272">在 GitHub wiki 上更深入地流覽此內容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="b2856-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="b2856-273">演練 6：將基於 Windows 容器的應用部署到容器的 Azure 應用服務</span><span class="sxs-lookup"><span data-stu-id="b2856-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b2856-274">技術演練可用性</span><span class="sxs-lookup"><span data-stu-id="b2856-274">Technical walkthrough availability</span></span>

<span data-ttu-id="b2856-275">完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：</span><span class="sxs-lookup"><span data-stu-id="b2856-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="b2856-276">概觀</span><span class="sxs-lookup"><span data-stu-id="b2856-276">Overview</span></span>

<span data-ttu-id="b2856-277">使用 Windows 容器的簡單容器化應用程式可以輕鬆地部署到容器的 Azure 應用服務。</span><span class="sxs-lookup"><span data-stu-id="b2856-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="b2856-278">對於大多數基於 Windows 容器的應用程式，這是推薦的方法。</span><span class="sxs-lookup"><span data-stu-id="b2856-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="b2856-279">目標</span><span class="sxs-lookup"><span data-stu-id="b2856-279">Goals</span></span>

<span data-ttu-id="b2856-280">本演練的目標是瞭解如何從註冊表（Docker Hub 或 Azure 容器註冊表）將基於 Windows 容器的應用程式部署到適用于容器的 Azure 應用服務。</span><span class="sxs-lookup"><span data-stu-id="b2856-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="b2856-281">狀況</span><span class="sxs-lookup"><span data-stu-id="b2856-281">Scenario</span></span>

![將基於 Windows 容器的應用部署到容器的 Azure 應用服務](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="b2856-283">優點</span><span class="sxs-lookup"><span data-stu-id="b2856-283">Benefits</span></span>

<span data-ttu-id="b2856-284">為容器部署到 Azure 應用服務提供了與 Azure 應用服務的 PaaS 優勢配對的容器的優勢。</span><span class="sxs-lookup"><span data-stu-id="b2856-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="b2856-285">應用服務可以輕鬆垂直和水準縮放，並可配置為自動縮放以滿足不斷變化的需求。</span><span class="sxs-lookup"><span data-stu-id="b2856-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="b2856-286">更新可以在零停機時間下執行，並且從註冊表進行連續部署的配置也很容易配置。</span><span class="sxs-lookup"><span data-stu-id="b2856-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2856-287">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2856-287">Next steps</span></span>

<span data-ttu-id="b2856-288">在 GitHub wiki 上更深入地流覽此內容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="b2856-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="b2856-289">[上一個](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [下一個](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="b2856-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
