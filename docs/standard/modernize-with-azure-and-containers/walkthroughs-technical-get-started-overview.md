---
title: 逐步解說和技術取得已啟動的概觀
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows Containers |逐步解說和技術取得已啟動的概觀
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0bad7e3afbdf3e55c447319b3756f2235b9e0a19
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="3f205-103">逐步解說和技術取得已啟動的概觀</span><span class="sxs-lookup"><span data-stu-id="3f205-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="3f205-104">若要限制此的電子書的大小，其他技術文件和完整的逐步解說所提供的 GitHub 儲存機制中。</span><span class="sxs-lookup"><span data-stu-id="3f205-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="3f205-105">此章節所述的逐步解說線上系列涵蓋 Windows 容器和部署至 Azure 為基礎的多個環境的逐步安裝。</span><span class="sxs-lookup"><span data-stu-id="3f205-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="3f205-106">下列各節說明每個逐步解說是有關它的目的和高層級的願景，並提供所涉及的工作的圖表。</span><span class="sxs-lookup"><span data-stu-id="3f205-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="3f205-107">您可以取得自己的逐步解說中*eShopModernizing*在應用程式 GitHub 儲存機制 wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki)。</span><span class="sxs-lookup"><span data-stu-id="3f205-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="3f205-108">技術的逐步解說清單</span><span class="sxs-lookup"><span data-stu-id="3f205-108">Technical walkthrough list</span></span>

<span data-ttu-id="3f205-109">下列 get 開始逐步解說提供一致且完整的範例應用程式，您可以拿起和移位藉由使用容器，並接著在 Azure 中使用多個部署選項之間移動技術的指引。</span><span class="sxs-lookup"><span data-stu-id="3f205-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="3f205-110">下列逐步解說使用的新範例 eShopLegacy 和 eShopModernizing 應用程式，可在 GitHub 上[ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="3f205-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="3f205-111">**教學課程的資格舊版應用程式**</span><span class="sxs-lookup"><span data-stu-id="3f205-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="3f205-112">**化您現有的.NET 應用程式與 Windows 容器**</span><span class="sxs-lookup"><span data-stu-id="3f205-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="3f205-113">**將 Windows 容器基礎應用程式部署至 Azure Vm**</span><span class="sxs-lookup"><span data-stu-id="3f205-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="3f205-114">**將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中**</span><span class="sxs-lookup"><span data-stu-id="3f205-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="3f205-115">**將 Windows 容器基礎應用程式部署至 Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="3f205-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="3f205-116">逐步解說 1： 教學課程的資格舊版應用程式</span><span class="sxs-lookup"><span data-stu-id="3f205-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3f205-117">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="3f205-117">Technical walkthrough availability</span></span>

<span data-ttu-id="3f205-118">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3f205-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="3f205-119">總覽</span><span class="sxs-lookup"><span data-stu-id="3f205-119">Overview</span></span>

<span data-ttu-id="3f205-120">在本逐步解說中，您可以瀏覽初始實作中的兩個範例舊版應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-120">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="3f205-121">兩個範例應用程式整合的架構，並使用傳統 ASP.NET 所建立的。</span><span class="sxs-lookup"><span data-stu-id="3f205-121">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="3f205-122">一個應用程式根據 ASP.NET 4.x MVC;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。</span><span class="sxs-lookup"><span data-stu-id="3f205-122">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="3f205-123">這兩個應用程式處於[eShopModernizing GitHub 儲存機制](https://github.com/dotnet-architecture/eShopModernizing)。</span><span class="sxs-lookup"><span data-stu-id="3f205-123">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="3f205-124">可以化兩個範例應用程式，其方式類似於可以化傳統[Windows Communication Foundation](../../framework/wcf/whats-wcf.md)取用做為桌面應用程式 (WCF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-124">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="3f205-125">如需範例，請參閱[eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms)。</span><span class="sxs-lookup"><span data-stu-id="3f205-125">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="3f205-126">目標</span><span class="sxs-lookup"><span data-stu-id="3f205-126">Goals</span></span>

<span data-ttu-id="3f205-127">本逐步解說的主要目的是只要取得熟悉這些應用程式，以及其程式碼和組態。</span><span class="sxs-lookup"><span data-stu-id="3f205-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="3f205-128">您可以設定應用程式，以便產生並使用模擬的資料，而不需要使用 SQL database 中，基於測試目的。</span><span class="sxs-lookup"><span data-stu-id="3f205-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="3f205-129">這個選用的設定根據相依性插入解除解合的方式。</span><span class="sxs-lookup"><span data-stu-id="3f205-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="3f205-130">情節</span><span class="sxs-lookup"><span data-stu-id="3f205-130">Scenario</span></span>

<span data-ttu-id="3f205-131">圖 5-1 會顯示原始的舊版應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="3f205-131">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![原始的舊版應用程式的簡單架構案例](./media/image5-1.png)
>
> <span data-ttu-id="3f205-133">**圖 5-1。**</span><span class="sxs-lookup"><span data-stu-id="3f205-133">**Figure 5-1.**</span></span> <span data-ttu-id="3f205-134">原始的舊版應用程式的簡單架構案例</span><span class="sxs-lookup"><span data-stu-id="3f205-134">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="3f205-135">商務網域的觀點而言，這兩個應用程式會提供在相同的目錄管理功能。</span><span class="sxs-lookup"><span data-stu-id="3f205-135">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="3f205-136">資格企業小組的成員可使用應用程式來檢視和編輯產品類別目錄。</span><span class="sxs-lookup"><span data-stu-id="3f205-136">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="3f205-137">圖 5-2 顯示的初始應用程式螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="3f205-137">Figure 5-2 shows the initial app screenshots.</span></span>

![ASP.NET MVC 與 ASP.NET Web Form 應用程式 （舊版現有技術）](./media/image5-2.png)

> <span data-ttu-id="3f205-139">**圖 5-2.**</span><span class="sxs-lookup"><span data-stu-id="3f205-139">**Figure 5-2.**</span></span> <span data-ttu-id="3f205-140">ASP.NET MVC 與 ASP.NET Web Form 應用程式 （舊版現有技術）</span><span class="sxs-lookup"><span data-stu-id="3f205-140">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="3f205-141">這些是 web 應用程式，可用來瀏覽並修改類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="3f205-141">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="3f205-142">兩個應用程式傳遞相同的功能/功能其實只是進行比較。</span><span class="sxs-lookup"><span data-stu-id="3f205-142">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="3f205-143">您可以看到類似的現代化程序所建立的 ASP.NET MVC 與 ASP.NET Web Form 架構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-143">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="3f205-144">相依性中 ASP.NET 4.x 或更早的版本 （無論是 MVC 或 Web Form） 表示除非使用 ASP.NET Core MVC 完全重寫程式碼，將不會在.NET Core 上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-144">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="3f205-145">這示範了，如果您不想要重新建構或重寫程式碼，您可以化現有的應用程式，並且仍然使用相同的.NET 技術和相同的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f205-145">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="3f205-146">您可以查看如何執行這類在容器中，不進行任何變更，舊版程式碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-146">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="3f205-147">優點</span><span class="sxs-lookup"><span data-stu-id="3f205-147">Benefits</span></span>

<span data-ttu-id="3f205-148">本逐步解說的好處是簡單： 只讓您熟悉的程式碼和應用程式的組態，根據相依性插入。</span><span class="sxs-lookup"><span data-stu-id="3f205-148">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="3f205-149">然後，您可以嘗試透過這種方式化和未來部署至多個環境時。</span><span class="sxs-lookup"><span data-stu-id="3f205-149">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="3f205-150">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f205-150">Next steps</span></span>

<span data-ttu-id="3f205-151">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="3f205-151">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="3f205-152">逐步解說 2： 化您現有的.NET 應用程式與 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="3f205-152">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3f205-153">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="3f205-153">Technical walkthrough availability</span></span>

<span data-ttu-id="3f205-154">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3f205-154">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="3f205-155">總覽</span><span class="sxs-lookup"><span data-stu-id="3f205-155">Overview</span></span>

<span data-ttu-id="3f205-156">您可以使用 Windows 容器來改善現有的.NET 應用程式，例如根據 MVC、 Web Form 或 WCF、 生產、 開發和測試環境的部署。</span><span class="sxs-lookup"><span data-stu-id="3f205-156">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="3f205-157">目標</span><span class="sxs-lookup"><span data-stu-id="3f205-157">Goals</span></span>

<span data-ttu-id="3f205-158">本逐步解說的目標是示範幾個選項用於 containerizing 現有的.NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-158">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="3f205-159">您可以：</span><span class="sxs-lookup"><span data-stu-id="3f205-159">You can:</span></span>

- <span data-ttu-id="3f205-160">化您的應用程式使用[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) （Visual Studio 2017 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="3f205-160">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="3f205-161">化您的應用程式透過手動方式新增[Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)。</span><span class="sxs-lookup"><span data-stu-id="3f205-161">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="3f205-162">化您的應用程式使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 （從 Docker 開放原始碼工具）。</span><span class="sxs-lookup"><span data-stu-id="3f205-162">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="3f205-163">本逐步解說著重於 Visual Studio 2017 Tools for Docker 方法，但其他兩種方法是使用 Dockerfiles 方面相當類似。</span><span class="sxs-lookup"><span data-stu-id="3f205-163">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="3f205-164">情節</span><span class="sxs-lookup"><span data-stu-id="3f205-164">Scenario</span></span>

<span data-ttu-id="3f205-165">圖 5-3 顯示容器化的資格舊版應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="3f205-165">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![在開發環境中的容器化應用程式的簡化的架構圖](./media/image5-3.png)
>
> <span data-ttu-id="3f205-167">**圖 5-3.**</span><span class="sxs-lookup"><span data-stu-id="3f205-167">**Figure 5-3.**</span></span> <span data-ttu-id="3f205-168">在開發環境中的容器化應用程式的簡化的架構圖</span><span class="sxs-lookup"><span data-stu-id="3f205-168">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="3f205-169">優點</span><span class="sxs-lookup"><span data-stu-id="3f205-169">Benefits</span></span>

<span data-ttu-id="3f205-170">有許多優點容器中執行應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="3f205-170">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="3f205-171">首先，您會建立應用程式的映像。</span><span class="sxs-lookup"><span data-stu-id="3f205-171">First, you create an image for the application.</span></span> <span data-ttu-id="3f205-172">從該點上，每個部署在相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="3f205-172">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="3f205-173">每個容器會使用相同的作業系統版本、 具有相同版本的相依性安裝、 使用相同的.NET framework 版本和建置使用相同的程序。</span><span class="sxs-lookup"><span data-stu-id="3f205-173">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="3f205-174">基本上，您可以控制您的應用程式的相依性使用 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="3f205-174">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="3f205-175">相依性會隨著應用程式，當您部署容器。</span><span class="sxs-lookup"><span data-stu-id="3f205-175">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="3f205-176">另一個優點是開發人員可以在 Windows 容器所提供一致性的環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-176">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="3f205-177">僅與特定版本一起出現的問題可以立即發現，而不是預備或生產環境的。</span><span class="sxs-lookup"><span data-stu-id="3f205-177">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="3f205-178">在容器中執行的應用程式時，開發小組的成員使用的開發環境中的差異重要小於。</span><span class="sxs-lookup"><span data-stu-id="3f205-178">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="3f205-179">容器化應用程式也會有更平面的向外延展曲線。</span><span class="sxs-lookup"><span data-stu-id="3f205-179">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="3f205-180">容器化應用程式可讓您有多個應用程式和服務執行個體 （根據容器） 中 VM 或實體機器相較於每部電腦的一般應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="3f205-180">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="3f205-181">這會轉譯成更高的密度和較少的所需的資源，特別是當您使用 orchestrators Kubernetes 等服務網狀架構。</span><span class="sxs-lookup"><span data-stu-id="3f205-181">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="3f205-182">集裝箱化，在理想的情況下，不需要對應用程式程式碼進行任何變更 (C\#)。</span><span class="sxs-lookup"><span data-stu-id="3f205-182">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="3f205-183">在大部分情況下，您只需要 Docker 部署中繼資料檔案 （Dockerfiles 和 Docker Compose 檔案）。</span><span class="sxs-lookup"><span data-stu-id="3f205-183">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="3f205-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f205-184">Next steps</span></span>

<span data-ttu-id="3f205-185">瀏覽更深入了解此內容上的 GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="3f205-185">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="3f205-186">逐步解說 3： 將 Windows 容器基礎應用程式部署至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="3f205-186">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3f205-187">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="3f205-187">Technical walkthrough availability</span></span>

<span data-ttu-id="3f205-188">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3f205-188">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="3f205-189">總覽</span><span class="sxs-lookup"><span data-stu-id="3f205-189">Overview</span></span>

<span data-ttu-id="3f205-190">部署至 Docker 主機上 Windows Server 2016 的虛擬機器 (VM) 在 Azure 中，可讓您快速地設定開發/測試/預備環境。</span><span class="sxs-lookup"><span data-stu-id="3f205-190">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="3f205-191">它也可讓您為一般測試人員或商務使用者驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-191">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="3f205-192">Vm 也很有效 Infrastucture 即服務 (IaaS) 」 生產環境。</span><span class="sxs-lookup"><span data-stu-id="3f205-192">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="3f205-193">目標</span><span class="sxs-lookup"><span data-stu-id="3f205-193">Goals</span></span>

<span data-ttu-id="3f205-194">本逐步解說的目標在於說明您到 Windows Server 2016 或更新版本為基礎的 Azure Vm 中部署 Windows 容器時，您有多個替代項目。</span><span class="sxs-lookup"><span data-stu-id="3f205-194">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3f205-195">案例</span><span class="sxs-lookup"><span data-stu-id="3f205-195">Scenarios</span></span>

<span data-ttu-id="3f205-196">在本逐步解說涵蓋數個案例。</span><span class="sxs-lookup"><span data-stu-id="3f205-196">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="3f205-197">從開發人員電腦透過 Docker 引擎連線的案例 a： 部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="3f205-197">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![從透過 Docker 引擎連線的開發電腦部署到 Azure VM](./media/image5-4.png)

> <span data-ttu-id="3f205-199">**圖 5-4.**</span><span class="sxs-lookup"><span data-stu-id="3f205-199">**Figure 5-4.**</span></span> <span data-ttu-id="3f205-200">從透過 Docker 引擎連線的開發電腦部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="3f205-200">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="3f205-201">案例 b： 部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="3f205-201">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![部署至 Azure VM 透過 Docker 登錄](./media/image5-5.png)

> <span data-ttu-id="3f205-203">**圖 5-5.**</span><span class="sxs-lookup"><span data-stu-id="3f205-203">**Figure 5-5.**</span></span> <span data-ttu-id="3f205-204">部署至 Azure VM 透過 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="3f205-204">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="3f205-205">案例 c： 將部署至 Azure VM 從 Visual Studio Team Services 中的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="3f205-205">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

> <span data-ttu-id="3f205-207">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="3f205-207">**Figure 5-6.**</span></span> <span data-ttu-id="3f205-208">從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="3f205-208">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="3f205-209">Windows 容器的 azure Vm</span><span class="sxs-lookup"><span data-stu-id="3f205-209">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="3f205-210">為 Windows 容器 azure Vm 是根據 Windows Server 2016、 Windows 10 或更新版本的 Vm，同時具有 Docker 引擎設定。</span><span class="sxs-lookup"><span data-stu-id="3f205-210">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="3f205-211">在大部分情況下，Windows Server 2016 會在 Azure Vm 中。</span><span class="sxs-lookup"><span data-stu-id="3f205-211">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="3f205-212">Azure 目前提供名為的 VM**與容器的 Windows Server 2016**。</span><span class="sxs-lookup"><span data-stu-id="3f205-212">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="3f205-213">您可以使用此 VM 試用新的 Windows Server 容器功能，與 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="3f205-213">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="3f205-214">安裝容器 OS 映像，然後就可以開始使用 docker VM。</span><span class="sxs-lookup"><span data-stu-id="3f205-214">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="3f205-215">優點</span><span class="sxs-lookup"><span data-stu-id="3f205-215">Benefits</span></span>

<span data-ttu-id="3f205-216">雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm 部署至 Azure 時，您會收到更簡單的方法，若要開始使用已備妥要使用 Windows Server 容器 Vm。</span><span class="sxs-lookup"><span data-stu-id="3f205-216">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="3f205-217">您也可以存取測試人員，並透過 Azure 虛擬機器擴展集自動延展性的一般線上位置。</span><span class="sxs-lookup"><span data-stu-id="3f205-217">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="3f205-218">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f205-218">Next steps</span></span>

<span data-ttu-id="3f205-219">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="3f205-219">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="3f205-220">逐步解說 4： 將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中</span><span class="sxs-lookup"><span data-stu-id="3f205-220">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3f205-221">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="3f205-221">Technical walkthrough availability</span></span>

<span data-ttu-id="3f205-222">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3f205-222">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="3f205-223">總覽</span><span class="sxs-lookup"><span data-stu-id="3f205-223">Overview</span></span>

<span data-ttu-id="3f205-224">應用程式為基礎的 Windows 容器快速必須使用平台，移動離開更進一步的 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="3f205-224">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="3f205-225">這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="3f205-225">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="3f205-226">您可以使用 orchestrator 來達成這些目標[Kubernetes](https://kubernetes.io/)，可用於[Azure 容器服務](https://azure.microsoft.com/services/container-service/)。</span><span class="sxs-lookup"><span data-stu-id="3f205-226">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="3f205-227">目標</span><span class="sxs-lookup"><span data-stu-id="3f205-227">Goals</span></span>

<span data-ttu-id="3f205-228">本逐步解說的目標是要了解如何部署 Kubernetes – 基礎 Windows 容器功能的應用程式 (也稱為*K8s*) Azure 容器服務中。</span><span class="sxs-lookup"><span data-stu-id="3f205-228">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="3f205-229">重新部署至 Kubernetes 是兩步驟程序：</span><span class="sxs-lookup"><span data-stu-id="3f205-229">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="3f205-230">將 Kubernetes 叢集部署至 Azure 容器服務。</span><span class="sxs-lookup"><span data-stu-id="3f205-230">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="3f205-231">Kubernetes 叢集部署的應用程式和相關的資源。</span><span class="sxs-lookup"><span data-stu-id="3f205-231">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3f205-232">案例</span><span class="sxs-lookup"><span data-stu-id="3f205-232">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="3f205-233">從開發環境的案例 a： 部署直接到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="3f205-233">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![直接將部署到 Kubernetes 叢集從開發環境](./media/image5-7.png)

> <span data-ttu-id="3f205-235">**圖 5-7.**</span><span class="sxs-lookup"><span data-stu-id="3f205-235">**Figure 5-7.**</span></span> <span data-ttu-id="3f205-236">直接將部署到 Kubernetes 叢集從開發環境</span><span class="sxs-lookup"><span data-stu-id="3f205-236">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="3f205-237">在 Team Services 中的案例 b： 從將部署至 Kubernetes 叢集 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="3f205-237">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集](./media/image5-8.png)

> <span data-ttu-id="3f205-239">**圖 5-8.**</span><span class="sxs-lookup"><span data-stu-id="3f205-239">**Figure 5-8.**</span></span> <span data-ttu-id="3f205-240">從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="3f205-240">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="3f205-241">優點</span><span class="sxs-lookup"><span data-stu-id="3f205-241">Benefits</span></span>

<span data-ttu-id="3f205-242">有許多優點，部署至 Kubernetes 中的叢集。</span><span class="sxs-lookup"><span data-stu-id="3f205-242">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="3f205-243">最大的好處是，您會取得在其中您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據叢集 （中的節點或 Vm 數目的容器執行個體數目在可實際執行環境全域延展性的叢集）。</span><span class="sxs-lookup"><span data-stu-id="3f205-243">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="3f205-244">Azure 容器服務，特別針對 Azure 最佳化熱門的開放原始碼工具和技術。</span><span class="sxs-lookup"><span data-stu-id="3f205-244">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="3f205-245">您會取得開啟的方案，提供可攜性，您的容器和應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="3f205-245">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="3f205-246">您選取的大小，主機的數目和 orchestrator 工具-容器服務會處理所有其他項目。</span><span class="sxs-lookup"><span data-stu-id="3f205-246">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="3f205-247">與 Kubernetes，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：</span><span class="sxs-lookup"><span data-stu-id="3f205-247">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="3f205-248">根據多個容器的應用程式</span><span class="sxs-lookup"><span data-stu-id="3f205-248">Applications based on multiple containers</span></span>

- <span data-ttu-id="3f205-249">複寫容器執行個體和水平的自動調整</span><span class="sxs-lookup"><span data-stu-id="3f205-249">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="3f205-250">命名及探索 (例如，內部 DNS)</span><span class="sxs-lookup"><span data-stu-id="3f205-250">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="3f205-251">平衡負載</span><span class="sxs-lookup"><span data-stu-id="3f205-251">Balancing loads</span></span>

- <span data-ttu-id="3f205-252">輪流更新</span><span class="sxs-lookup"><span data-stu-id="3f205-252">Rolling updates</span></span>

- <span data-ttu-id="3f205-253">散發密碼</span><span class="sxs-lookup"><span data-stu-id="3f205-253">Distributing secrets</span></span>

- <span data-ttu-id="3f205-254">應用程式健全狀況檢查</span><span class="sxs-lookup"><span data-stu-id="3f205-254">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f205-255">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f205-255">Next steps</span></span>

<span data-ttu-id="3f205-256">瀏覽更深入了解此內容上的 GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="3f205-256">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="3f205-257">逐步解說 5： 將 Windows 容器基礎應用程式部署至 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="3f205-257">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3f205-258">可用性技術的逐步解說</span><span class="sxs-lookup"><span data-stu-id="3f205-258">Technical walkthrough availability</span></span>

<span data-ttu-id="3f205-259">EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3f205-259">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="3f205-260">總覽</span><span class="sxs-lookup"><span data-stu-id="3f205-260">Overview</span></span>

<span data-ttu-id="3f205-261">根據 Windows 容器快速的應用程式必須使用平台，移動離開更進一步的 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="3f205-261">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="3f205-262">這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="3f205-262">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="3f205-263">使用 orchestrator Azure Service Fabric 是用於 Azure 的雲端，但也可以使用內部部署，或甚至在不同的公用雲端中，您就可以達成這些目標。</span><span class="sxs-lookup"><span data-stu-id="3f205-263">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="3f205-264">目標</span><span class="sxs-lookup"><span data-stu-id="3f205-264">Goals</span></span>

<span data-ttu-id="3f205-265">本逐步解說的目標是了解如何部署 Windows 容器型應用程式至 Azure Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="3f205-265">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="3f205-266">部署 Service fabric 從頭是兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="3f205-266">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="3f205-267">將 Service Fabric 叢集部署至 Azure （或不同的環境）。</span><span class="sxs-lookup"><span data-stu-id="3f205-267">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="3f205-268">應用程式和相關的資源部署到 Service Fabric 叢集。</span><span class="sxs-lookup"><span data-stu-id="3f205-268">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3f205-269">案例</span><span class="sxs-lookup"><span data-stu-id="3f205-269">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="3f205-270">從開發環境的案例 a： 部署直接到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="3f205-270">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![從開發環境部署直接到 Service Fabric 叢集](./media/image5-9.png)

> <span data-ttu-id="3f205-272">**圖 5-9.**</span><span class="sxs-lookup"><span data-stu-id="3f205-272">**Figure 5-9.**</span></span> <span data-ttu-id="3f205-273">從開發環境部署直接到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="3f205-273">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="3f205-274">在 Team Services 中的案例 b： 從將部署到 Service Fabric 叢集 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="3f205-274">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集](./media/image5-10.png)

> <span data-ttu-id="3f205-276">**圖 5-10.**</span><span class="sxs-lookup"><span data-stu-id="3f205-276">**Figure 5-10.**</span></span> <span data-ttu-id="3f205-277">從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集</span><span class="sxs-lookup"><span data-stu-id="3f205-277">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="3f205-278">優點</span><span class="sxs-lookup"><span data-stu-id="3f205-278">Benefits</span></span>

<span data-ttu-id="3f205-279">部署至 Service Fabric 叢集的優點是類似於使用 Kubernetes 的優點。</span><span class="sxs-lookup"><span data-stu-id="3f205-279">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="3f205-280">一項的差異是，Service Fabric 是 Windows 應用程式相較於 Kubernetes，是在測試階段中 Kubernetes 1.9 版版本的 Windows 容器的成熟實際執行環境 (年 12 月 2017)。</span><span class="sxs-lookup"><span data-stu-id="3f205-280">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="3f205-281">Kubernetes 是適用於 Linux 的成熟環境。</span><span class="sxs-lookup"><span data-stu-id="3f205-281">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="3f205-282">使用 Azure Service Fabric 的主要優點是，您會取得在其中您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據數目的容器執行個體數目在可實際執行環境節點或叢集中 （全域延展性的叢集） Vm。</span><span class="sxs-lookup"><span data-stu-id="3f205-282">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="3f205-283">Azure Service Fabric 提供了適用於您的容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="3f205-283">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="3f205-284">您可以讓 Service Fabric 叢集在 Azure 中，或將它安裝在內部部署在自己的資料中心。</span><span class="sxs-lookup"><span data-stu-id="3f205-284">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="3f205-285">可以甚至在您安裝 Service Fabric 叢集不同的雲端，例如[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)。</span><span class="sxs-lookup"><span data-stu-id="3f205-285">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="3f205-286">使用 Service Fabric，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：</span><span class="sxs-lookup"><span data-stu-id="3f205-286">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="3f205-287">根據多個容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f205-287">Applications based on multiple containers.</span></span>

- <span data-ttu-id="3f205-288">複寫容器執行個體和水平的自動調整。</span><span class="sxs-lookup"><span data-stu-id="3f205-288">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="3f205-289">命名和探索 (例如，內部 DNS)。</span><span class="sxs-lookup"><span data-stu-id="3f205-289">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="3f205-290">平衡負載。</span><span class="sxs-lookup"><span data-stu-id="3f205-290">Balancing loads.</span></span>

- <span data-ttu-id="3f205-291">輪流更新。</span><span class="sxs-lookup"><span data-stu-id="3f205-291">Rolling updates.</span></span>

- <span data-ttu-id="3f205-292">散發密碼。</span><span class="sxs-lookup"><span data-stu-id="3f205-292">Distributing secrets.</span></span>

- <span data-ttu-id="3f205-293">應用程式健全狀況檢查。</span><span class="sxs-lookup"><span data-stu-id="3f205-293">Application health checks.</span></span>

<span data-ttu-id="3f205-294">獨佔 （相較於其他 orchestrators） 的 Service Fabric 中有下列功能：</span><span class="sxs-lookup"><span data-stu-id="3f205-294">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="3f205-295">可設定狀態的服務功能，透過可靠的服務應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="3f205-295">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="3f205-296">動作項目模式，透過 Reliable Actors 應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="3f205-296">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="3f205-297">部署 / 骨處理程序，除了 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="3f205-297">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="3f205-298">進階輪流更新和健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="3f205-298">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="3f205-299">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f205-299">Next steps</span></span>

<span data-ttu-id="3f205-300">瀏覽更深入了解此內容上的 GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="3f205-300">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="3f205-301">[上一頁](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[下一頁](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="3f205-301">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
