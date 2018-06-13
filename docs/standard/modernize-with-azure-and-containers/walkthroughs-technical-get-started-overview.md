---
title: 逐步解說和技術取得已啟動的概觀
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows Containers |逐步解說和技術取得已啟動的概觀
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027385"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="9be69-103">逐步解說和技術取得已啟動的概觀</span><span class="sxs-lookup"><span data-stu-id="9be69-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="9be69-104">若要限制此的電子書的大小，其他技術文件和完整的逐步解說所提供的 GitHub 儲存機制中。</span><span class="sxs-lookup"><span data-stu-id="9be69-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="9be69-105">此章節所述的逐步解說線上系列涵蓋 Windows 容器和部署至 Azure 為基礎的多個環境的逐步安裝。</span><span class="sxs-lookup"><span data-stu-id="9be69-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="9be69-106">下列各節說明每個逐步解說是有關它的目的和高層級的願景，並提供所涉及的工作的圖表。</span><span class="sxs-lookup"><span data-stu-id="9be69-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="9be69-107">您可以取得自己的逐步解說中*eShopModernizing*在應用程式 GitHub 儲存機制 wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki)。</span><span class="sxs-lookup"><span data-stu-id="9be69-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="9be69-108">技術的逐步解說清單</span><span class="sxs-lookup"><span data-stu-id="9be69-108">Technical walkthrough list</span></span>

<span data-ttu-id="9be69-109">下列 get 開始逐步解說提供一致且完整的範例應用程式，您可以拿起和移位藉由使用容器，並接著在 Azure 中使用多個部署選項之間移動技術的指引。</span><span class="sxs-lookup"><span data-stu-id="9be69-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="9be69-110">下列逐步解說使用的新範例 eShopLegacy 和 eShopModernizing 應用程式，可在 GitHub 上[ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="9be69-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="9be69-111">**教學課程的資格舊版應用程式 （如來現代化的應用程式基準）**</span><span class="sxs-lookup"><span data-stu-id="9be69-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="9be69-112">**使用 Windows 容器化現有 ASP.NET web 應用程式 (WebForms & MVC)**</span><span class="sxs-lookup"><span data-stu-id="9be69-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="9be69-113">**化現有的 WCF 服務 （多層式架構應用程式） 使用 Windows 容器**</span><span class="sxs-lookup"><span data-stu-id="9be69-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="9be69-114">**將 Windows 容器基礎應用程式部署至 Azure Vm**</span><span class="sxs-lookup"><span data-stu-id="9be69-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="9be69-115">**將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中**</span><span class="sxs-lookup"><span data-stu-id="9be69-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="9be69-116">**將 Windows 容器基礎應用程式部署至 Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="9be69-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="9be69-117">逐步解說 1： 教學課程的資格舊版應用程式</span><span class="sxs-lookup"><span data-stu-id="9be69-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9be69-118">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-118">Technical walkthrough availability</span></span>

<span data-ttu-id="9be69-119">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="9be69-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="9be69-120">eShopModernizing wiki 逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="9be69-121">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-121">Overview</span></span>

<span data-ttu-id="9be69-122">在本逐步解說中，您可以瀏覽初始實作中的三個範例舊版應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="9be69-123">前兩個範例 web 應用程式整合的架構，並使用傳統 ASP.NET 所建立的。</span><span class="sxs-lookup"><span data-stu-id="9be69-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="9be69-124">一個應用程式根據 ASP.NET 4.x MVC;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。</span><span class="sxs-lookup"><span data-stu-id="9be69-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="9be69-125">第三個應用程式是由用戶端 WinForms 應用程式和伺服器端的 3 層應用程式[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)服務。</span><span class="sxs-lookup"><span data-stu-id="9be69-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="9be69-126">所有這些應用程式位於[eShopModernizing GitHub 儲存機制](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="9be69-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-127">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-127">Goals</span></span>

<span data-ttu-id="9be69-128">本逐步解說的主要目的是只要取得熟悉這些應用程式，以及其程式碼和組態。</span><span class="sxs-lookup"><span data-stu-id="9be69-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="9be69-129">您可以設定應用程式，以便產生並使用模擬的資料，而不需要使用 SQL database 中，基於測試目的。</span><span class="sxs-lookup"><span data-stu-id="9be69-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="9be69-130">這個選用的設定根據相依性插入解除解合的方式。</span><span class="sxs-lookup"><span data-stu-id="9be69-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="9be69-131">案例 1: ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9be69-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="9be69-132">下圖顯示原始的舊版 ASP.NET web 應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="9be69-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![原始的舊版 ASP.NET web 應用程式的簡單架構案例](./media/image5-1.png)
>

<span data-ttu-id="9be69-134">商務網域的觀點而言，這兩個應用程式會提供在相同的目錄管理功能。</span><span class="sxs-lookup"><span data-stu-id="9be69-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="9be69-135">資格企業小組的成員可使用應用程式來檢視和編輯產品類別目錄。</span><span class="sxs-lookup"><span data-stu-id="9be69-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="9be69-136">下圖將顯示的初始應用程式螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="9be69-136">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC 與 ASP.NET Web Form 應用程式 （舊版現有技術）](./media/image5-2.png)

<span data-ttu-id="9be69-138">相依性中 ASP.NET 4.x 或更早的版本 （無論是 MVC 或 Web Form） 表示除非使用 ASP.NET Core MVC 完全重寫程式碼，將不會在.NET Core 上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="9be69-139">案例 2: WCF 服務和 WinForms 用戶端應用程式 （3 層應用程式）</span><span class="sxs-lookup"><span data-stu-id="9be69-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="9be69-140">下圖顯示原始 3 層式架構的舊版應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="9be69-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![簡單的架構案例中的原始舊版 3 層應用程式與 WCF 服務和 WinForms 用戶端應用程式](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="9be69-142">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-142">Benefits</span></span>

<span data-ttu-id="9be69-143">本逐步解說的好處是簡單： 只讓您熟悉的程式碼和初始應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9be69-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-144">Next steps</span></span>

<span data-ttu-id="9be69-145">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="9be69-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="9be69-146">基準 ASP.NET MVC 的教學課程和 Web Form 「 舊版 」 的應用程式</span><span class="sxs-lookup"><span data-stu-id="9be69-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="9be69-147">基準 WCF 服務，然後 WinForms （3 層） 的 「 舊版 」 應用程式的教學課程</span><span class="sxs-lookup"><span data-stu-id="9be69-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="9be69-148">逐步解說 2： 化您現有的.NET 應用程式與 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="9be69-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="9be69-149">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-149">Overview</span></span>

<span data-ttu-id="9be69-150">您可以使用 Windows 容器來改善現有的.NET 應用程式，例如根據 MVC、 Web Form 或 WCF、 生產、 開發和測試環境的部署。</span><span class="sxs-lookup"><span data-stu-id="9be69-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-151">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-151">Goals</span></span>

<span data-ttu-id="9be69-152">本逐步解說的目標是示範幾個選項用於 containerizing 現有的.NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="9be69-153">您可以：</span><span class="sxs-lookup"><span data-stu-id="9be69-153">You can:</span></span>

- <span data-ttu-id="9be69-154">化您的應用程式使用[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) （Visual Studio 2017 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="9be69-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="9be69-155">化您的應用程式透過手動方式新增[Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)。</span><span class="sxs-lookup"><span data-stu-id="9be69-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="9be69-156">化您的應用程式使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 （從 Docker 開放原始碼工具）。</span><span class="sxs-lookup"><span data-stu-id="9be69-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="9be69-157">本逐步解說著重於 Visual Studio 2017 Tools for Docker 方法，但其他兩種方法是使用 Dockerfiles 方面相當類似。</span><span class="sxs-lookup"><span data-stu-id="9be69-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="9be69-158">案例 1： 進行容器化的 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="9be69-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="9be69-159">下圖顯示容器化的資格舊版 web 應用程式的應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="9be69-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![簡化的架構圖表的容器化在開發環境中的 ASP.NET 應用程式](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="9be69-161">案例 2： 進行容器化的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="9be69-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="9be69-162">下圖顯示以進行容器化的 WCF 服務的 3 層應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="9be69-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![簡化的開發環境中進行容器化的 WCF 服務的架構圖](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="9be69-164">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-164">Benefits</span></span>

<span data-ttu-id="9be69-165">有許多優點容器中執行應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="9be69-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="9be69-166">首先，您會建立應用程式的映像。</span><span class="sxs-lookup"><span data-stu-id="9be69-166">First, you create an image for the application.</span></span> <span data-ttu-id="9be69-167">從該點上，每個部署在相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="9be69-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="9be69-168">每個容器會使用相同的作業系統版本、 具有相同版本的相依性安裝、 使用相同的.NET framework 版本和建置使用相同的程序。</span><span class="sxs-lookup"><span data-stu-id="9be69-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="9be69-169">基本上，您可以控制您的應用程式的相依性使用 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="9be69-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="9be69-170">相依性會隨著應用程式，當您部署容器。</span><span class="sxs-lookup"><span data-stu-id="9be69-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="9be69-171">另一個優點是開發人員可以在 Windows 容器所提供一致性的環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="9be69-172">僅與特定版本一起出現的問題可以立即發現，而不是預備或生產環境的。</span><span class="sxs-lookup"><span data-stu-id="9be69-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="9be69-173">在容器中執行的應用程式時，開發小組的成員使用的開發環境中的差異重要小於。</span><span class="sxs-lookup"><span data-stu-id="9be69-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="9be69-174">容器化應用程式也會有更平面的向外延展曲線。</span><span class="sxs-lookup"><span data-stu-id="9be69-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="9be69-175">容器化應用程式可讓您有多個應用程式和服務執行個體 （根據容器） 中 VM 或實體機器相較於每部電腦的一般應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="9be69-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="9be69-176">這會轉譯成更高的密度和較少的所需的資源，特別是當您使用 orchestrators Kubernetes 等服務網狀架構。</span><span class="sxs-lookup"><span data-stu-id="9be69-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="9be69-177">集裝箱化，在理想的情況下，不需要對應用程式程式碼進行任何變更 (C\#)。</span><span class="sxs-lookup"><span data-stu-id="9be69-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="9be69-178">在大部分情況下，您只需要 Docker 部署中繼資料檔案 （Dockerfiles 和 Docker Compose 檔案）。</span><span class="sxs-lookup"><span data-stu-id="9be69-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="9be69-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-179">Next steps</span></span>

<span data-ttu-id="9be69-180">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="9be69-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="9be69-181">如何化 .NET Framework web 應用程式與 Windows 容器和 Docker</span><span class="sxs-lookup"><span data-stu-id="9be69-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="9be69-182">將 Docker 的支援加入至 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="9be69-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="9be69-183">逐步解說 3： 將 Windows 容器基礎應用程式部署至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="9be69-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9be69-184">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-184">Technical walkthrough availability</span></span>

<span data-ttu-id="9be69-185">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說： [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="9be69-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="9be69-186">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-186">Overview</span></span>

<span data-ttu-id="9be69-187">部署至 Docker 主機上 Windows Server 2016 的虛擬機器 (VM) 在 Azure 中，可讓您快速地設定開發/測試/預備環境。</span><span class="sxs-lookup"><span data-stu-id="9be69-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="9be69-188">它也可讓您為一般測試人員或商務使用者驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="9be69-189">Vm 也很有效 Infrastucture 即服務 (IaaS) 」 生產環境。</span><span class="sxs-lookup"><span data-stu-id="9be69-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-190">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-190">Goals</span></span>

<span data-ttu-id="9be69-191">本逐步解說的目標在於說明您到 Windows Server 2016 或更新版本為基礎的 Azure Vm 中部署 Windows 容器時，您有多個替代項目。</span><span class="sxs-lookup"><span data-stu-id="9be69-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9be69-192">案例</span><span class="sxs-lookup"><span data-stu-id="9be69-192">Scenarios</span></span>

<span data-ttu-id="9be69-193">在本逐步解說涵蓋數個案例。</span><span class="sxs-lookup"><span data-stu-id="9be69-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="9be69-194">從開發人員電腦透過 Docker 引擎連線的案例 a： 部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="9be69-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![從透過 Docker 引擎連線的開發電腦部署到 Azure VM](./media/image5-4.png)

> <span data-ttu-id="9be69-196">**圖 5-4.**</span><span class="sxs-lookup"><span data-stu-id="9be69-196">**Figure 5-4.**</span></span> <span data-ttu-id="9be69-197">從透過 Docker 引擎連線的開發電腦部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="9be69-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="9be69-198">案例 b： 部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="9be69-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![部署至 Azure VM 透過 Docker 登錄](./media/image5-5.png)

> <span data-ttu-id="9be69-200">**圖 5-5.**</span><span class="sxs-lookup"><span data-stu-id="9be69-200">**Figure 5-5.**</span></span> <span data-ttu-id="9be69-201">部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="9be69-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="9be69-202">案例 c： 將部署至 Azure VM 從 Visual Studio Team Services 中的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="9be69-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

> <span data-ttu-id="9be69-204">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="9be69-204">**Figure 5-6.**</span></span> <span data-ttu-id="9be69-205">從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="9be69-205">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="9be69-206">Windows 容器的 azure Vm</span><span class="sxs-lookup"><span data-stu-id="9be69-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="9be69-207">為 Windows 容器 azure Vm 是根據 Windows Server 2016、 Windows 10 或更新版本的 Vm，同時具有 Docker 引擎設定。</span><span class="sxs-lookup"><span data-stu-id="9be69-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="9be69-208">在大部分情況下，Windows Server 2016 會在 Azure Vm 中。</span><span class="sxs-lookup"><span data-stu-id="9be69-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="9be69-209">Azure 目前提供名為的 VM**與容器的 Windows Server 2016**。</span><span class="sxs-lookup"><span data-stu-id="9be69-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="9be69-210">您可以使用此 VM 試用新的 Windows Server 容器功能，與 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="9be69-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="9be69-211">安裝容器 OS 映像，然後就可以開始使用 docker VM。</span><span class="sxs-lookup"><span data-stu-id="9be69-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="9be69-212">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-212">Benefits</span></span>

<span data-ttu-id="9be69-213">雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm 部署至 Azure 時，您會收到更簡單的方法，若要開始使用已備妥要使用 Windows Server 容器 Vm。</span><span class="sxs-lookup"><span data-stu-id="9be69-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="9be69-214">您也可以存取測試人員，並透過 Azure 虛擬機器擴展集自動延展性的一般線上位置。</span><span class="sxs-lookup"><span data-stu-id="9be69-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9be69-215">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-215">Next steps</span></span>

<span data-ttu-id="9be69-216">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="9be69-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="9be69-217">逐步解說 4： 將 Windows 容器基礎應用程式部署至 Azure 容器執行個體 (ACI)</span><span class="sxs-lookup"><span data-stu-id="9be69-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9be69-218">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-218">Technical walkthrough availability</span></span>

<span data-ttu-id="9be69-219">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="9be69-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="9be69-220">[將應用程式部署至 ACI （Azure 容器執行個體）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="9be69-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="9be69-221">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-221">Overview</span></span>

<span data-ttu-id="9be69-222">[Azure 容器執行個體 (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/)是最快的方式有容器開發/測試/預備環境，您可以在其中部署容器的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="9be69-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-223">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-223">Goals</span></span>

<span data-ttu-id="9be69-224">本逐步解說示範您的主要案例 Azure 容器執行個體 (ACI) 和您如何部署到 ACI eShopModernizing 應用程式部署 Windows 容器時。</span><span class="sxs-lookup"><span data-stu-id="9be69-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9be69-225">案例</span><span class="sxs-lookup"><span data-stu-id="9be69-225">Scenarios</span></span>

<span data-ttu-id="9be69-226">可以部署到 ACI eShopModernizing 應用程式，例如部署下列其中一個或所有應用程式 （MVC 應用程式、 WebForms 應用程式或 WCF 服務） 相關的變化。</span><span class="sxs-lookup"><span data-stu-id="9be69-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="9be69-227">在下列案例中如下所示您可以看到 ASP.NET MVC 應用程式加上這兩種部署的 SQL Server 容器做為容器 ACI （Azure 容器執行個體）。</span><span class="sxs-lookup"><span data-stu-id="9be69-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![從開發環境部署至 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="9be69-229">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-229">Benefits</span></span>

<span data-ttu-id="9be69-230">Azure 容器執行個體，可讓您輕鬆地建立及管理 Docker 容器，在 Azure 中，不需要重新佈建虛擬機器，或採用較高層級的服務。</span><span class="sxs-lookup"><span data-stu-id="9be69-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="9be69-231">使用 ACI，您可以直接部署在 Azure 中的 Windows 容器，並將它公開至網際網路的完整的網域名稱 (FQDN) 會在幾秒 （前提是您在 Docker Hub 或 Azure 容器 Docker 登錄 Windows 容器映像準備登錄中）。</span><span class="sxs-lookup"><span data-stu-id="9be69-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="9be69-232">考量</span><span class="sxs-lookup"><span data-stu-id="9be69-232">Considerations</span></span>

<span data-ttu-id="9be69-233">部署 Windows 容器，以其中一個完整的.NET Framework / ASP.NET 或 SQL Server 到 Azure 容器執行個體 (ACI) 不是完全一樣快速，因為 Docker 映像必須部署至規則的 Docker 主機 （例如 Windows Server 2016 與 Windows 容器)每次下載 （提取從 Docker 登錄） 和 SQL 容器映像 (15.1 GB) 和 ASP.NET 的容器映像 (13.9 GB) 的大小為相當龐大，不過，它是比維持您自己的 docker 主機 （永久線上成本更低Windows Server 2016 與 Windows Azure 中的容器 VM) 更別說像在 Azure (AKS/ACS) 或 Azure Service Fabric Kubernetes，也就是，相反地，對於實際執行部署的絕佳選擇整個 orchestrator。</span><span class="sxs-lookup"><span data-stu-id="9be69-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="9be69-234">做為主要結束時，使用 Azure 容器執行個體是極具說服力的選項為開發/測試案例和 CI/CD 管線。</span><span class="sxs-lookup"><span data-stu-id="9be69-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9be69-235">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-235">Next steps</span></span>

<span data-ttu-id="9be69-236">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="9be69-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="9be69-237">逐步解說 5： 將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中</span><span class="sxs-lookup"><span data-stu-id="9be69-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9be69-238">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-238">Technical walkthrough availability</span></span>

<span data-ttu-id="9be69-239">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="9be69-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="9be69-240">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-240">Overview</span></span>

<span data-ttu-id="9be69-241">應用程式為基礎的 Windows 容器快速必須使用平台，移動離開更進一步的 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="9be69-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="9be69-242">這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="9be69-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="9be69-243">您可以使用 orchestrator 來達成這些目標[Kubernetes](https://kubernetes.io/)，可用於[Azure 容器服務](https://azure.microsoft.com/services/container-service/)。</span><span class="sxs-lookup"><span data-stu-id="9be69-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-244">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-244">Goals</span></span>

<span data-ttu-id="9be69-245">本逐步解說的目標是要了解如何部署 Kubernetes – 基礎 Windows 容器功能的應用程式 (也稱為*K8s*) Azure 容器服務中。</span><span class="sxs-lookup"><span data-stu-id="9be69-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="9be69-246">重新部署至 Kubernetes 是兩步驟程序：</span><span class="sxs-lookup"><span data-stu-id="9be69-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="9be69-247">將 Kubernetes 叢集部署至 Azure 容器服務。</span><span class="sxs-lookup"><span data-stu-id="9be69-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="9be69-248">Kubernetes 叢集部署的應用程式和相關的資源。</span><span class="sxs-lookup"><span data-stu-id="9be69-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9be69-249">案例</span><span class="sxs-lookup"><span data-stu-id="9be69-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="9be69-250">從開發環境的案例 a： 部署直接到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="9be69-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![直接將部署到 Kubernetes 叢集從開發環境](./media/image5-7.png)

> <span data-ttu-id="9be69-252">**圖 5-7.**</span><span class="sxs-lookup"><span data-stu-id="9be69-252">**Figure 5-7.**</span></span> <span data-ttu-id="9be69-253">直接將部署到 Kubernetes 叢集從開發環境</span><span class="sxs-lookup"><span data-stu-id="9be69-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="9be69-254">在 Team Services 中的案例 b： 從將部署至 Kubernetes 叢集 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="9be69-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集](./media/image5-8.png)

> <span data-ttu-id="9be69-256">**圖 5-8.**</span><span class="sxs-lookup"><span data-stu-id="9be69-256">**Figure 5-8.**</span></span> <span data-ttu-id="9be69-257">從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="9be69-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="9be69-258">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-258">Benefits</span></span>

<span data-ttu-id="9be69-259">有許多優點，部署至 Kubernetes 中的叢集。</span><span class="sxs-lookup"><span data-stu-id="9be69-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="9be69-260">最大的好處是，您會取得在其中您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據叢集 （中的節點或 Vm 數目的容器執行個體數目在可實際執行環境全域延展性的叢集）。</span><span class="sxs-lookup"><span data-stu-id="9be69-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="9be69-261">Azure 容器服務，特別針對 Azure 最佳化熱門的開放原始碼工具和技術。</span><span class="sxs-lookup"><span data-stu-id="9be69-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="9be69-262">您會取得開啟的方案，提供可攜性，您的容器和應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="9be69-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="9be69-263">您選取的大小，主機的數目和 orchestrator 工具-容器服務會處理所有其他項目。</span><span class="sxs-lookup"><span data-stu-id="9be69-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="9be69-264">與 Kubernetes，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：</span><span class="sxs-lookup"><span data-stu-id="9be69-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="9be69-265">根據多個容器的應用程式</span><span class="sxs-lookup"><span data-stu-id="9be69-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="9be69-266">複寫容器執行個體和水平的自動調整</span><span class="sxs-lookup"><span data-stu-id="9be69-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="9be69-267">命名及探索 (例如，內部 DNS)</span><span class="sxs-lookup"><span data-stu-id="9be69-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="9be69-268">平衡負載</span><span class="sxs-lookup"><span data-stu-id="9be69-268">Balancing loads</span></span>

- <span data-ttu-id="9be69-269">輪流更新</span><span class="sxs-lookup"><span data-stu-id="9be69-269">Rolling updates</span></span>

- <span data-ttu-id="9be69-270">散發密碼</span><span class="sxs-lookup"><span data-stu-id="9be69-270">Distributing secrets</span></span>

- <span data-ttu-id="9be69-271">應用程式健全狀況檢查</span><span class="sxs-lookup"><span data-stu-id="9be69-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="9be69-272">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-272">Next steps</span></span>

<span data-ttu-id="9be69-273">瀏覽更深入了解此內容上的 GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="9be69-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="9be69-274">逐步解說 6： 將 Windows 容器基礎應用程式部署至 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="9be69-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9be69-275">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="9be69-275">Technical walkthrough availability</span></span>

<span data-ttu-id="9be69-276">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="9be69-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="9be69-277">總覽</span><span class="sxs-lookup"><span data-stu-id="9be69-277">Overview</span></span>

<span data-ttu-id="9be69-278">根據 Windows 容器快速的應用程式必須使用平台，移動離開更進一步的 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="9be69-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="9be69-279">這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="9be69-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="9be69-280">使用 orchestrator Azure Service Fabric 是用於 Azure 的雲端，但也可以使用內部部署，或甚至在不同的公用雲端中，您就可以達成這些目標。</span><span class="sxs-lookup"><span data-stu-id="9be69-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="9be69-281">目標</span><span class="sxs-lookup"><span data-stu-id="9be69-281">Goals</span></span>

<span data-ttu-id="9be69-282">本逐步解說的目標是了解如何部署 Windows 容器型應用程式至 Azure Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="9be69-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="9be69-283">部署 Service fabric 從頭是兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="9be69-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="9be69-284">將 Service Fabric 叢集部署至 Azure （或不同的環境）。</span><span class="sxs-lookup"><span data-stu-id="9be69-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="9be69-285">應用程式和相關的資源部署到 Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="9be69-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9be69-286">案例</span><span class="sxs-lookup"><span data-stu-id="9be69-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="9be69-287">從開發環境的案例 a： 部署直接到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="9be69-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![從開發環境部署直接到 Service Fabric 叢集](./media/image5-9.png)

> <span data-ttu-id="9be69-289">**圖 5-9.**</span><span class="sxs-lookup"><span data-stu-id="9be69-289">**Figure 5-9.**</span></span> <span data-ttu-id="9be69-290">從開發環境部署直接到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="9be69-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="9be69-291">在 Team Services 中的案例 b： 從將部署到 Service Fabric 叢集 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="9be69-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集](./media/image5-10.png)

> <span data-ttu-id="9be69-293">**圖 5-10.**</span><span class="sxs-lookup"><span data-stu-id="9be69-293">**Figure 5-10.**</span></span> <span data-ttu-id="9be69-294">從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="9be69-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="9be69-295">優點</span><span class="sxs-lookup"><span data-stu-id="9be69-295">Benefits</span></span>

<span data-ttu-id="9be69-296">部署至 Service Fabric 叢集的優點是類似於使用 Kubernetes 的優點。</span><span class="sxs-lookup"><span data-stu-id="9be69-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="9be69-297">一項的差異是，Service Fabric 是 Windows 應用程式相較於 Kubernetes，是在測試階段中 Kubernetes 1.9 版版本的 Windows 容器的成熟實際執行環境 (年 12 月 2017)。</span><span class="sxs-lookup"><span data-stu-id="9be69-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="9be69-298">Kubernetes 是適用於 Linux 的成熟環境。</span><span class="sxs-lookup"><span data-stu-id="9be69-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="9be69-299">使用 Azure Service Fabric 的主要優點是，您會取得在其中您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據數目的容器執行個體數目在可實際執行環境節點或叢集中 （全域延展性的叢集） Vm。</span><span class="sxs-lookup"><span data-stu-id="9be69-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="9be69-300">Azure Service Fabric 提供了適用於您的容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="9be69-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="9be69-301">您可以讓 Service Fabric 叢集在 Azure 中，或將它安裝在內部部署在自己的資料中心。</span><span class="sxs-lookup"><span data-stu-id="9be69-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="9be69-302">可以甚至在您安裝 Service Fabric 叢集不同的雲端，例如[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)。</span><span class="sxs-lookup"><span data-stu-id="9be69-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="9be69-303">使用 Service Fabric，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：</span><span class="sxs-lookup"><span data-stu-id="9be69-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="9be69-304">根據多個容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be69-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="9be69-305">複寫容器執行個體和水平的自動調整。</span><span class="sxs-lookup"><span data-stu-id="9be69-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="9be69-306">命名和探索 (例如，內部 DNS)。</span><span class="sxs-lookup"><span data-stu-id="9be69-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="9be69-307">平衡負載。</span><span class="sxs-lookup"><span data-stu-id="9be69-307">Balancing loads.</span></span>

- <span data-ttu-id="9be69-308">輪流更新。</span><span class="sxs-lookup"><span data-stu-id="9be69-308">Rolling updates.</span></span>

- <span data-ttu-id="9be69-309">散發密碼。</span><span class="sxs-lookup"><span data-stu-id="9be69-309">Distributing secrets.</span></span>

- <span data-ttu-id="9be69-310">應用程式健全狀況檢查。</span><span class="sxs-lookup"><span data-stu-id="9be69-310">Application health checks.</span></span>

<span data-ttu-id="9be69-311">獨佔 （相較於其他 orchestrators） 的 Service Fabric 中有下列功能：</span><span class="sxs-lookup"><span data-stu-id="9be69-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="9be69-312">可設定狀態的服務功能，透過可靠的服務應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="9be69-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="9be69-313">動作項目模式，透過 Reliable Actors 應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="9be69-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="9be69-314">部署 / 骨處理程序，除了 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="9be69-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="9be69-315">進階輪流更新和健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="9be69-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9be69-316">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9be69-316">Next steps</span></span>

<span data-ttu-id="9be69-317">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="9be69-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="9be69-318">[上一頁](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[下一頁](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="9be69-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
