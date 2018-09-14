---
title: 逐步解說和技術開始入門的概觀
description: 將現有.NET 應用程式與 Azure 雲端和 Windows 容器現代化 |逐步解說和技術開始入門的概觀
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 41fbeb3abc201ef03cf0c237a069e7687c98dd18
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519771"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="71124-103">逐步解說和技術開始入門的概觀</span><span class="sxs-lookup"><span data-stu-id="71124-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="71124-104">若要限制此電子書的大小，其他的技術文件和完整的逐步解說所提供的 GitHub 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="71124-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="71124-105">線上系列這一章所述的逐步解說涵蓋 Windows 容器和部署至 Azure 為基礎的多個環境的逐步安裝程式。</span><span class="sxs-lookup"><span data-stu-id="71124-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="71124-106">下列各節說明每個逐步解說是什麼相關高階的願景，其目標，提供所涉及的工作的圖表。</span><span class="sxs-lookup"><span data-stu-id="71124-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="71124-107">您可以取得自己的逐步解說中*eShopModernizing*在應用程式 GitHub 儲存機制的 wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki)。</span><span class="sxs-lookup"><span data-stu-id="71124-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="71124-108">技術逐步解說清單</span><span class="sxs-lookup"><span data-stu-id="71124-108">Technical walkthrough list</span></span>

<span data-ttu-id="71124-109">下列快速入門逐步解說提供一致且完整的範例應用程式，您可以隨即轉移藉由使用容器，和在 Azure 中使用多個部署選項然後移動的技術指導。</span><span class="sxs-lookup"><span data-stu-id="71124-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="71124-110">每個下列逐步解說使用的新範例 eShopLegacy 和 eShopModernizing 應用程式，也就是在 GitHub 上的可用[ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="71124-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="71124-111">**教學課程的 eShop 舊版應用程式 （如將現代化的應用程式基準）**</span><span class="sxs-lookup"><span data-stu-id="71124-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="71124-112">**將現有 ASP.NET web 應用程式 （WebForms 和 MVC） 與 Windows 容器的容器化**</span><span class="sxs-lookup"><span data-stu-id="71124-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="71124-113">**將現有的 WCF 服務 （多層式架構應用程式） 與 Windows 容器的容器化**</span><span class="sxs-lookup"><span data-stu-id="71124-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="71124-114">**將 Windows 容器型應用程式部署至 Azure Vm**</span><span class="sxs-lookup"><span data-stu-id="71124-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="71124-115">**在 Azure Container Service 的 kubernetes 部署 Windows 容器型應用程式**</span><span class="sxs-lookup"><span data-stu-id="71124-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="71124-116">**部署到 Azure Service Fabric Windows 容器型應用程式**</span><span class="sxs-lookup"><span data-stu-id="71124-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="71124-117">逐步解說 1: EShop 舊版應用程式教學課程</span><span class="sxs-lookup"><span data-stu-id="71124-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="71124-118">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="71124-118">Technical walkthrough availability</span></span>

<span data-ttu-id="71124-119">完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:</span><span class="sxs-lookup"><span data-stu-id="71124-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="71124-120">eShopModernizing wiki 逐步解說</span><span class="sxs-lookup"><span data-stu-id="71124-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="71124-121">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-121">Overview</span></span>

<span data-ttu-id="71124-122">在本逐步解說中，您可以瀏覽三個範例的舊版應用程式的初始實作。</span><span class="sxs-lookup"><span data-stu-id="71124-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="71124-123">前兩個範例 web 應用程式已整合型架構，並使用傳統的 ASP.NET 所建立的。</span><span class="sxs-lookup"><span data-stu-id="71124-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="71124-124">一個應用程式根據 ASP.NET 4.x MVC;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。</span><span class="sxs-lookup"><span data-stu-id="71124-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="71124-125">第三個應用程式是由用戶端 WinForms 應用程式和伺服器端所組成的 3 層式架構應用程式[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)服務。</span><span class="sxs-lookup"><span data-stu-id="71124-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="71124-126">所有這些應用程式位於[eShopModernizing GitHub 存放庫](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="71124-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="71124-127">目標</span><span class="sxs-lookup"><span data-stu-id="71124-127">Goals</span></span>

<span data-ttu-id="71124-128">本逐步解說中的主要目標是只取得熟悉這些應用程式，以及其程式碼和組態。</span><span class="sxs-lookup"><span data-stu-id="71124-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="71124-129">您可以設定應用程式，以便產生並使用模擬 （mock） 的資料，而不需使用 SQL database 中，基於測試目的。</span><span class="sxs-lookup"><span data-stu-id="71124-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="71124-130">此選擇性的組態根據相依性插入的低耦合的方式。</span><span class="sxs-lookup"><span data-stu-id="71124-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="71124-131">案例 1: ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="71124-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="71124-132">下圖顯示原始的舊版 ASP.NET web 應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="71124-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![原始的舊版 ASP.NET web 應用程式的簡單架構案例](./media/image5-1.png)
>

<span data-ttu-id="71124-134">商務網域的觀點而言，這兩個應用程式會提供相同的目錄管理功能。</span><span class="sxs-lookup"><span data-stu-id="71124-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="71124-135">EShop 企業小組成員會使用應用程式，來檢視和編輯產品目錄。</span><span class="sxs-lookup"><span data-stu-id="71124-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="71124-136">下圖顯示的初始應用程式螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="71124-136">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC 和 ASP.NET Web Forms 應用程式 （現有/舊版技術）](./media/image5-2.png)

<span data-ttu-id="71124-138">相依性在 ASP.NET 4.x 或更早版本 （無論是 MVC 或 Web Form） 表示除非使用 ASP.NET Core MVC 會完全重寫程式碼，不會在.NET Core 上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="71124-139">案例 2: WCF 服務與 WinForms 用戶端應用程式 （3 層式架構應用程式）</span><span class="sxs-lookup"><span data-stu-id="71124-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="71124-140">下圖顯示原始 3 層式架構的舊版應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="71124-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![原始的 WCF 服務與舊版 3 層式架構應用程式和 WinForms 用戶端應用程式的簡單架構案例](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="71124-142">優點</span><span class="sxs-lookup"><span data-stu-id="71124-142">Benefits</span></span>

<span data-ttu-id="71124-143">本逐步解說的好處很簡單： 只要熟悉的程式碼與初始的應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="71124-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-144">Next steps</span></span>

<span data-ttu-id="71124-145">探索 GitHub wiki 上的此更深入的內容：</span><span class="sxs-lookup"><span data-stu-id="71124-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="71124-146">基準 ASP.NET MVC 教學課程和 Web Forms 「 舊版 」 應用程式</span><span class="sxs-lookup"><span data-stu-id="71124-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="71124-147">基準 WCF 服務及 WinForms （3 層） 的 「 舊版 」 應用程式的教學課程</span><span class="sxs-lookup"><span data-stu-id="71124-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="71124-148">逐步解說 2： 將您現有的.NET 應用程式，Windows 容器和容器化</span><span class="sxs-lookup"><span data-stu-id="71124-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="71124-149">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-149">Overview</span></span>

<span data-ttu-id="71124-150">您可以使用 Windows 容器來改善現有的.NET 應用程式，例如生產、 開發和測試環境來根據 MVC、 Web Form 或 WCF 部署。</span><span class="sxs-lookup"><span data-stu-id="71124-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="71124-151">目標</span><span class="sxs-lookup"><span data-stu-id="71124-151">Goals</span></span>

<span data-ttu-id="71124-152">本逐步解說的目的是要說明幾個選項用於容器化現有的.NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="71124-153">您可以：</span><span class="sxs-lookup"><span data-stu-id="71124-153">You can:</span></span>

- <span data-ttu-id="71124-154">將您的應用程式使用容器化[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) （Visual Studio 2017 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="71124-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="71124-155">將您的應用程式容器化將手動新增[Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)。</span><span class="sxs-lookup"><span data-stu-id="71124-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="71124-156">將您的應用程式使用容器化[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 （從 Docker 開放原始碼工具）。</span><span class="sxs-lookup"><span data-stu-id="71124-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="71124-157">本逐步解說著重於 Visual Studio 2017 Tools for Docker 的方法，但其他兩種方法都使用 Dockerfile 方面相當類似。</span><span class="sxs-lookup"><span data-stu-id="71124-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="71124-158">案例 1： 容器化的 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="71124-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="71124-159">下圖顯示容器化的 eShop 舊版 web 應用程式的應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="71124-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![簡化的架構圖表的容器化的開發環境中的 ASP.NET 應用程式](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="71124-161">案例 2： 容器化的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="71124-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="71124-162">下圖顯示容器化的 WCF 服務的 3 層式架構應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="71124-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![簡化的開發環境中的容器化 WCF 服務的架構圖](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="71124-164">優點</span><span class="sxs-lookup"><span data-stu-id="71124-164">Benefits</span></span>

<span data-ttu-id="71124-165">有一些優點，以在容器中執行整合型應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="71124-166">首先，您會建立應用程式的映像。</span><span class="sxs-lookup"><span data-stu-id="71124-166">First, you create an image for the application.</span></span> <span data-ttu-id="71124-167">從那時起，每個部署相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="71124-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="71124-168">每個容器會使用相同的 OS 版本、 具有相同版本的相依性安裝、 使用相同的.NET framework 版本和建置使用相同的程序。</span><span class="sxs-lookup"><span data-stu-id="71124-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="71124-169">基本上，您可以控制您的應用程式的相依性所使用的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="71124-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="71124-170">相依性會跟著應用程式，當您部署容器。</span><span class="sxs-lookup"><span data-stu-id="71124-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="71124-171">另一個優點是開發人員可以在一致的環境所提供的 Windows 容器中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="71124-172">只能搭配特定版本出現的問題可以立即看出，而不是呈現在預備或生產環境中。</span><span class="sxs-lookup"><span data-stu-id="71124-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="71124-173">在容器中執行的應用程式時，開發小組的成員所用的開發環境中的差異重要小於。</span><span class="sxs-lookup"><span data-stu-id="71124-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="71124-174">容器化應用程式也會有 flatter 的向外延展曲線。</span><span class="sxs-lookup"><span data-stu-id="71124-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="71124-175">容器化應用程式可讓您有多個應用程式和服務執行個體 （以容器為基礎） 中的 VM 或實體機器相較於每部機器的一般應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="71124-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="71124-176">這會轉譯為密度增加且較少的所需的資源，特別是當您使用 Kubernetes 或 Service Fabric 等協調器。</span><span class="sxs-lookup"><span data-stu-id="71124-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="71124-177">容器化，在理想的情況下，不需要對應用程式程式碼進行任何變更 (C\#)。</span><span class="sxs-lookup"><span data-stu-id="71124-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="71124-178">在大部分情況下，您只需要 Docker 部署中繼資料檔案 （Dockerfiles 和 Docker Compose 檔案）。</span><span class="sxs-lookup"><span data-stu-id="71124-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="71124-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-179">Next steps</span></span>

<span data-ttu-id="71124-180">探索 GitHub wiki 上的此更深入的內容：</span><span class="sxs-lookup"><span data-stu-id="71124-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="71124-181">如何將容器化.NET Framework web 應用程式與 Windows 容器和 Docker</span><span class="sxs-lookup"><span data-stu-id="71124-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="71124-182">將 Docker 支援新增至 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="71124-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="71124-183">逐步解說 3： 將 Windows 容器型應用程式部署至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="71124-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="71124-184">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="71124-184">Technical walkthrough availability</span></span>

<span data-ttu-id="71124-185">完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="71124-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="71124-186">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-186">Overview</span></span>

<span data-ttu-id="71124-187">部署到 Docker 主機上 Windows Server 2016 虛擬機器 (VM) 在 Azure 中，可讓您快速地設定開發/測試/預備環境。</span><span class="sxs-lookup"><span data-stu-id="71124-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="71124-188">它也可讓您為通用測試人員或業務使用者來驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="71124-189">Vm 也可以有效的基礎結構即服務 (IaaS) 」 生產環境。</span><span class="sxs-lookup"><span data-stu-id="71124-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="71124-190">目標</span><span class="sxs-lookup"><span data-stu-id="71124-190">Goals</span></span>

<span data-ttu-id="71124-191">本逐步解說的目的是要說明您將 Windows 容器部署到 Windows Server 2016 或更新版本為基礎的 Azure Vm 時，您有多個替代項目。</span><span class="sxs-lookup"><span data-stu-id="71124-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="71124-192">案例</span><span class="sxs-lookup"><span data-stu-id="71124-192">Scenarios</span></span>

<span data-ttu-id="71124-193">在本逐步解說涵蓋數個案例。</span><span class="sxs-lookup"><span data-stu-id="71124-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="71124-194">從 透過 Docker 引擎連線的開發電腦的案例 a： 部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="71124-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![從 透過 Docker 引擎連線的開發電腦部署至 Azure VM](./media/image5-4.png)

> <span data-ttu-id="71124-196">**圖 5-4.**</span><span class="sxs-lookup"><span data-stu-id="71124-196">**Figure 5-4.**</span></span> <span data-ttu-id="71124-197">從 透過 Docker 引擎連線的開發電腦部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="71124-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="71124-198">案例 b： 部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="71124-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![部署至 Azure VM 透過 Docker 登錄](./media/image5-5.png)

> <span data-ttu-id="71124-200">**圖 5-5.**</span><span class="sxs-lookup"><span data-stu-id="71124-200">**Figure 5-5.**</span></span> <span data-ttu-id="71124-201">部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="71124-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="71124-202">案例 c： 部署至 Azure VM 從 Azure DevOps 服務中的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="71124-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

> <span data-ttu-id="71124-204">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="71124-204">**Figure 5-6.**</span></span> <span data-ttu-id="71124-205">從 Azure DevOps 服務中的 CI/CD 管線部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="71124-205">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="71124-206">適用於 Windows 容器的 azure Vm</span><span class="sxs-lookup"><span data-stu-id="71124-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="71124-207">Azure Vm 的 Windows 容器是根據 Windows Server 2016、 Windows 10 或更新版本的 Vm，都有 Docker 引擎設定。</span><span class="sxs-lookup"><span data-stu-id="71124-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="71124-208">在大部分情況下，Windows Server 2016 會在 Azure Vm。</span><span class="sxs-lookup"><span data-stu-id="71124-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="71124-209">Azure 目前提供的 VM **Windows Server 2016 with Containers**。</span><span class="sxs-lookup"><span data-stu-id="71124-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="71124-210">您可以試用新的 Windows Server 容器功能，與 Windows Server Core 或 Windows Nano Server 中使用此 VM。</span><span class="sxs-lookup"><span data-stu-id="71124-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="71124-211">安裝容器 OS 映像，並就準備好搭配 Docker VM。</span><span class="sxs-lookup"><span data-stu-id="71124-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="71124-212">優點</span><span class="sxs-lookup"><span data-stu-id="71124-212">Benefits</span></span>

<span data-ttu-id="71124-213">雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm，當您部署至 Azure 時，您會得到更簡單的方法，若要開始使用已準備好使用 Windows Server 容器的 Vm。</span><span class="sxs-lookup"><span data-stu-id="71124-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="71124-214">您也可以存取軟體測試人員，並透過 Azure 虛擬機器擴展集的自動延展性的一般線上位置。</span><span class="sxs-lookup"><span data-stu-id="71124-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="71124-215">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-215">Next steps</span></span>

<span data-ttu-id="71124-216">探索 GitHub wiki 上的此更深入的內容：</span><span class="sxs-lookup"><span data-stu-id="71124-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="71124-217">逐步解說 4： 將 Windows 容器型應用程式部署至 Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="71124-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="71124-218">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="71124-218">Technical walkthrough availability</span></span>

<span data-ttu-id="71124-219">完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:</span><span class="sxs-lookup"><span data-stu-id="71124-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="71124-220">[將應用程式部署至 ACI （Azure 容器執行個體）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="71124-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="71124-221">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-221">Overview</span></span>

<span data-ttu-id="71124-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/)最快的方式，讓您可以在其中部署容器的單一執行個體的容器開發/測試/預備環境。</span><span class="sxs-lookup"><span data-stu-id="71124-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="71124-223">目標</span><span class="sxs-lookup"><span data-stu-id="71124-223">Goals</span></span>

<span data-ttu-id="71124-224">本逐步解說會示範的主要案例將 Windows 容器部署至 Azure Container Instances (ACI) 以及您如何部署至 ACI eShopModernizing 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="71124-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="71124-225">案例</span><span class="sxs-lookup"><span data-stu-id="71124-225">Scenarios</span></span>

<span data-ttu-id="71124-226">可以有變化，需將 eShopModernizing 應用程式部署至 ACI 中，例如部署其中一個或所有應用程式 （MVC 應用程式、 WebForms 應用程式或 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="71124-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="71124-227">如下所示的下列案例中您所見的 ASP.NET MVC 應用程式加上這兩個部署的 SQL Server 容器做為容器至 ACI （Azure 容器執行個體）。</span><span class="sxs-lookup"><span data-stu-id="71124-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![從開發環境部署至 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="71124-229">優點</span><span class="sxs-lookup"><span data-stu-id="71124-229">Benefits</span></span>

<span data-ttu-id="71124-230">Azure Container Instances 可讓您輕鬆地建立及管理 Docker 容器，在 Azure 中，而不需要佈建虛擬機器或採用高階服務。</span><span class="sxs-lookup"><span data-stu-id="71124-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="71124-231">使用 ACI，您可以直接部署在 Azure 中的 Windows 容器並將它公開到網際網路的完整的網域名稱 (FQDN) 而幾秒內 （前提是您將 Windows 容器映像準備好在像 Docker Hub 或 Azure 容器的 Docker 登錄登錄中）。</span><span class="sxs-lookup"><span data-stu-id="71124-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="71124-232">考量</span><span class="sxs-lookup"><span data-stu-id="71124-232">Considerations</span></span>

<span data-ttu-id="71124-233">將 Windows 容器，使用任一個完整的.NET Framework 部署 / ASP.NET 或 SQL Server 到 Azure Container Instances (ACI) 不是相當一樣快速，因為 Docker 映像必須部署到一般的 Docker 主機 （例如 Windows Server 2016 和 Windows 容器)每次下載 （提取從 Docker 登錄） 和 SQL 容器映像 (15.1 GB) 和 ASP.NET 的容器映像 (13.9 GB) 的大小會相當龐大，不過它是比維護您自己的 docker 主機 （永久線上操作的成本更低Windows Server 2016 與 Windows 容器在 Azure 中的 VM) 在 Azure (AKS/ACS) 或 Azure Service Fabric 中，也就是，相反地，生產環境部署的絕佳選擇的 Kubernetes 等的整個 orchestrator 更是不在話下。</span><span class="sxs-lookup"><span data-stu-id="71124-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="71124-234">為主要的結束時，使用 Azure Container Instances 是令人信服選項適用於開發/測試案例及 CI/CD 管線。</span><span class="sxs-lookup"><span data-stu-id="71124-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="71124-235">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-235">Next steps</span></span>

<span data-ttu-id="71124-236">探索 GitHub wiki 上的此更深入的內容：</span><span class="sxs-lookup"><span data-stu-id="71124-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="71124-237">逐步解說 5： 將 Windows 容器型應用程式部署至 Azure Container Service 中的 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="71124-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="71124-238">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="71124-238">Technical walkthrough availability</span></span>

<span data-ttu-id="71124-239">完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:</span><span class="sxs-lookup"><span data-stu-id="71124-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="71124-240">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-240">Overview</span></span>

<span data-ttu-id="71124-241">應用程式為基礎的 Windows 容器快速必須使用平台，從 IaaS 虛擬機器移動更進一步地消失。</span><span class="sxs-lookup"><span data-stu-id="71124-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="71124-242">這即可以輕鬆地達到高延展性和更自動化延展性，並大幅提升的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="71124-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="71124-243">您可以使用協調器，以達成這些目標[Kubernetes](https://kubernetes.io/)，可用於[Azure Container Service](https://azure.microsoft.com/services/container-service/)。</span><span class="sxs-lookup"><span data-stu-id="71124-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="71124-244">目標</span><span class="sxs-lookup"><span data-stu-id="71124-244">Goals</span></span>

<span data-ttu-id="71124-245">本逐步解說的目標是要了解如何部署至 Kubernetes Windows 容器型應用程式 (也稱為*K8s*) 在 Azure Container Service 中。</span><span class="sxs-lookup"><span data-stu-id="71124-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="71124-246">重新部署至 Kubernetes 是兩步驟程序：</span><span class="sxs-lookup"><span data-stu-id="71124-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="71124-247">部署至 Azure Container Service 的 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="71124-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="71124-248">應用程式和相關的資源部署到 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="71124-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="71124-249">案例</span><span class="sxs-lookup"><span data-stu-id="71124-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="71124-250">從開發環境的案例 a： 部署直接到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="71124-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![將直接部署到 Kubernetes 叢集中從開發環境](./media/image5-7.png)

> <span data-ttu-id="71124-252">**圖 5-7.**</span><span class="sxs-lookup"><span data-stu-id="71124-252">**Figure 5-7.**</span></span> <span data-ttu-id="71124-253">將直接部署到 Kubernetes 叢集中從開發環境</span><span class="sxs-lookup"><span data-stu-id="71124-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="71124-254">Azure DevOps 服務中的案例 b： 從將部署至 Kubernetes 叢集的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="71124-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Kubernetes 叢集](./media/image5-8.png)

> <span data-ttu-id="71124-256">**圖 5-8.**</span><span class="sxs-lookup"><span data-stu-id="71124-256">**Figure 5-8.**</span></span> <span data-ttu-id="71124-257">從 Azure DevOps 服務中的 CI/CD 管線部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="71124-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="71124-258">優點</span><span class="sxs-lookup"><span data-stu-id="71124-258">Benefits</span></span>

<span data-ttu-id="71124-259">有許多好處，部署至 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="71124-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="71124-260">最大的好處是您在其中您可以相應放大您想要使用 （內部-現有的節點中的延展性），而且在叢集 （節點或 Vm 的數目為基礎的容器執行個體數目為基礎的應用程式的可實際執行環境全域延展性的叢集）。</span><span class="sxs-lookup"><span data-stu-id="71124-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="71124-261">Azure Container Service 會特別針對 Azure 最佳化熱門開放原始碼工具和技術。</span><span class="sxs-lookup"><span data-stu-id="71124-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="71124-262">您取得開啟的方案，提供可攜性，適用於您容器和應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="71124-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="71124-263">您選取的大小，主機的數目和 orchestrator 工具-容器服務會處理所有其他項目。</span><span class="sxs-lookup"><span data-stu-id="71124-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="71124-264">使用 Kubernetes，開發人員可以開始進行思考實體和虛擬機器，從規劃以容器為中心的基礎結構，可簡化下列功能，其他項目：</span><span class="sxs-lookup"><span data-stu-id="71124-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="71124-265">多個容器為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="71124-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="71124-266">複寫的容器執行個體和水平自動調整</span><span class="sxs-lookup"><span data-stu-id="71124-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="71124-267">命名和探索 (例如，內部 DNS)</span><span class="sxs-lookup"><span data-stu-id="71124-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="71124-268">平衡負載</span><span class="sxs-lookup"><span data-stu-id="71124-268">Balancing loads</span></span>

- <span data-ttu-id="71124-269">輪流更新</span><span class="sxs-lookup"><span data-stu-id="71124-269">Rolling updates</span></span>

- <span data-ttu-id="71124-270">散發祕密</span><span class="sxs-lookup"><span data-stu-id="71124-270">Distributing secrets</span></span>

- <span data-ttu-id="71124-271">應用程式健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="71124-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="71124-272">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-272">Next steps</span></span>

<span data-ttu-id="71124-273">探索 GitHub wiki 上的此更深入的內容： [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="71124-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="71124-274">逐步解說 6： 將 Windows 容器型應用程式部署至 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="71124-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="71124-275">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="71124-275">Technical walkthrough availability</span></span>

<span data-ttu-id="71124-276">完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:</span><span class="sxs-lookup"><span data-stu-id="71124-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="71124-277">總覽</span><span class="sxs-lookup"><span data-stu-id="71124-277">Overview</span></span>

<span data-ttu-id="71124-278">基礎 Windows 容器快速的應用程式必須使用平台，從 IaaS 虛擬機器移動更進一步地消失。</span><span class="sxs-lookup"><span data-stu-id="71124-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="71124-279">這即可以輕鬆地達到高延展性和更自動化延展性，並大幅提升的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="71124-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="71124-280">若要達成這些目標，您即可使用 orchestrator Azure Service Fabric 中，也就是可在 Azure 雲端中，但也可以使用內部部署，或甚至在不同的公用雲端。</span><span class="sxs-lookup"><span data-stu-id="71124-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="71124-281">目標</span><span class="sxs-lookup"><span data-stu-id="71124-281">Goals</span></span>

<span data-ttu-id="71124-282">本逐步解說的目標是了解如何部署 Windows 容器型應用程式到 Azure 中 Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="71124-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="71124-283">重新部署至 Service Fabric 是兩個步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="71124-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="71124-284">將 Service Fabric 叢集部署至 Azure （或不同的環境）。</span><span class="sxs-lookup"><span data-stu-id="71124-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="71124-285">應用程式和相關的資源部署到 Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="71124-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="71124-286">案例</span><span class="sxs-lookup"><span data-stu-id="71124-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="71124-287">從開發環境的案例 a： 部署直接與 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="71124-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![將直接部署到 Service Fabric 叢集從開發環境](./media/image5-9.png)

> <span data-ttu-id="71124-289">**圖 5-9.**</span><span class="sxs-lookup"><span data-stu-id="71124-289">**Figure 5-9.**</span></span> <span data-ttu-id="71124-290">將直接部署到 Service Fabric 叢集從開發環境</span><span class="sxs-lookup"><span data-stu-id="71124-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="71124-291">Azure DevOps 服務中的案例 b： 從將部署至 Service Fabric 叢集的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="71124-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Service Fabric 叢集](./media/image5-10.png)

> <span data-ttu-id="71124-293">**圖 5-10.**</span><span class="sxs-lookup"><span data-stu-id="71124-293">**Figure 5-10.**</span></span> <span data-ttu-id="71124-294">從 Azure DevOps 服務中的 CI/CD 管線部署至 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="71124-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

## <a name="benefits"></a><span data-ttu-id="71124-295">優點</span><span class="sxs-lookup"><span data-stu-id="71124-295">Benefits</span></span>

<span data-ttu-id="71124-296">部署到 Service Fabric 中的叢集的優點是類似於使用 Kubernetes 的優點。</span><span class="sxs-lookup"><span data-stu-id="71124-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="71124-297">一項差異，不過是 Service Fabric 是成熟的生產環境，相較於 Kubernetes，是在 beta 階段，適用於在 Kubernetes 中 1.9 版的 Windows 容器的 Windows 應用程式 (12 月 2017)。</span><span class="sxs-lookup"><span data-stu-id="71124-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="71124-298">Kubernetes 是成熟的環境，適用於 Linux。</span><span class="sxs-lookup"><span data-stu-id="71124-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="71124-299">使用 Azure Service Fabric 的主要優點是您取得在其中您可以相應放大您想要使用 （內部-現有的節點中的延展性），並根據數目的容器執行個體數目為基礎的應用程式的可實際執行環境節點或叢集 （叢集的全域延展性） 中的 Vm。</span><span class="sxs-lookup"><span data-stu-id="71124-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="71124-300">Azure Service Fabric 會提供適用於您容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="71124-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="71124-301">您可以讓 Service Fabric 叢集在 Azure 中，或將它安裝在內部部署在自己的資料中心。</span><span class="sxs-lookup"><span data-stu-id="71124-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="71124-302">您可以更安裝 Service Fabric 叢集在不同的雲端，例如[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)。</span><span class="sxs-lookup"><span data-stu-id="71124-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="71124-303">Service fabric，開發人員就可以開始思考實體和虛擬機器從進行規劃以容器為中心的基礎結構，可簡化下列功能，其他項目：</span><span class="sxs-lookup"><span data-stu-id="71124-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="71124-304">多個容器為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="71124-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="71124-305">將容器執行個體和水平自動調整的複寫。</span><span class="sxs-lookup"><span data-stu-id="71124-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="71124-306">命名和探索 (例如，內部 DNS)。</span><span class="sxs-lookup"><span data-stu-id="71124-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="71124-307">平衡負載。</span><span class="sxs-lookup"><span data-stu-id="71124-307">Balancing loads.</span></span>

- <span data-ttu-id="71124-308">輪流更新。</span><span class="sxs-lookup"><span data-stu-id="71124-308">Rolling updates.</span></span>

- <span data-ttu-id="71124-309">散發祕密。</span><span class="sxs-lookup"><span data-stu-id="71124-309">Distributing secrets.</span></span>

- <span data-ttu-id="71124-310">應用程式健康狀態檢查。</span><span class="sxs-lookup"><span data-stu-id="71124-310">Application health checks.</span></span>

<span data-ttu-id="71124-311">獨佔 （相較於其他協調器） 的 Service Fabric 中的下列功能︰</span><span class="sxs-lookup"><span data-stu-id="71124-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="71124-312">具狀態服務功能，透過 Reliable Services 應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="71124-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="71124-313">動作項目模式，透過 Reliable Actors 應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="71124-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="71124-314">部署簡易的程序，除了 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="71124-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="71124-315">進階輪流更新和健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="71124-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="71124-316">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71124-316">Next steps</span></span>

<span data-ttu-id="71124-317">探索 GitHub wiki 上的此更深入的內容：</span><span class="sxs-lookup"><span data-stu-id="71124-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="71124-318">[上一頁](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[下一頁](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="71124-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
