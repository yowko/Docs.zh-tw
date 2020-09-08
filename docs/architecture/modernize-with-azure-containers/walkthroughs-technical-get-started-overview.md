---
title: 逐步解說和技術入門概觀
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |逐步解說和技術入門簡介
ms.date: 04/28/2018
ms.openlocfilehash: 4db6d449d27dcd4316d61305c8c2a8c2aa0bc65b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516121"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="753db-103">逐步解說和技術入門概觀</span><span class="sxs-lookup"><span data-stu-id="753db-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="753db-104">若要限制此電子書的大小，可在 GitHub 存放庫中取得額外的技術檔和完整的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="753db-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="753db-105">本章所述的《線上逐步解說》系列將逐步說明如何設定以 Windows 容器為基礎的多個環境，以及部署至 Azure。</span><span class="sxs-lookup"><span data-stu-id="753db-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="753db-106">下列各節說明每個逐步解說的內容、其目標和高階願景，並提供相關工作的圖表。</span><span class="sxs-lookup"><span data-stu-id="753db-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="753db-107">您可以在的 *eShopModernizing* apps GitHub 存放庫 wiki 中取得逐步解說 <https://github.com/dotnet-architecture/eShopModernizing/wiki> 。</span><span class="sxs-lookup"><span data-stu-id="753db-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="753db-108">技術逐步解說清單</span><span class="sxs-lookup"><span data-stu-id="753db-108">Technical walkthrough list</span></span>

<span data-ttu-id="753db-109">下列快速入門逐步解說針對您可以使用容器隨即轉移的範例應用程式，提供一致且完整的技術指引，然後在 Azure 中使用多個部署選項來移動。</span><span class="sxs-lookup"><span data-stu-id="753db-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="753db-110">下列每個逐步解說都會使用新的範例 eShopLegacy 和 eShopModernizing 應用程式，這些應用程式可在 GitHub 上取得 <https://github.com/dotnet-architecture/eShopModernizing> 。</span><span class="sxs-lookup"><span data-stu-id="753db-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="753db-111">\*\*EShop 繼承應用程式的導覽， (基準應用程式來現代化) \*\*</span><span class="sxs-lookup"><span data-stu-id="753db-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="753db-112">**使用 Windows 容器 (WebForms & MVC) 來將現有的 ASP.NET web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="753db-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="753db-113">**使用 Windows 容器 (多層式應用程式) 將現有的 WCF 服務**</span><span class="sxs-lookup"><span data-stu-id="753db-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="753db-114">**將 Windows 容器型應用程式部署至 Azure Vm**</span><span class="sxs-lookup"><span data-stu-id="753db-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="753db-115">**將您的 Windows 容器型應用程式部署至 Azure Container Service 中的 Kubernetes**</span><span class="sxs-lookup"><span data-stu-id="753db-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="753db-116">逐步解說1： eShop 繼承應用程式的導覽</span><span class="sxs-lookup"><span data-stu-id="753db-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="753db-117">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="753db-117">Technical walkthrough availability</span></span>

<span data-ttu-id="753db-118">EShopModernizing GitHub 存放庫 wiki 提供完整的技術逐步解說：</span><span class="sxs-lookup"><span data-stu-id="753db-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="753db-119">eShopModernizing wiki 逐步解說</span><span class="sxs-lookup"><span data-stu-id="753db-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="753db-120">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-120">Overview</span></span>

<span data-ttu-id="753db-121">在這個逐步解說中，您可以探索三個範例繼承應用程式的初始執行。</span><span class="sxs-lookup"><span data-stu-id="753db-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="753db-122">前兩個範例 web 應用程式具有整合型架構，並且是使用傳統 ASP.NET 所建立。</span><span class="sxs-lookup"><span data-stu-id="753db-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="753db-123">其中一個應用程式是以 ASP.NET 4.x MVC 為基礎;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。</span><span class="sxs-lookup"><span data-stu-id="753db-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="753db-124">第三個應用程式是由用戶端 WinForms 應用程式和伺服器端 [Windows Communication Foundation (WCF) ](../../framework/wcf/whats-wcf.md) 服務所組成的三層式應用程式。</span><span class="sxs-lookup"><span data-stu-id="753db-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="753db-125">這些應用程式都可以在 [EShopModernizing GitHub](https://github.com/dotnet-architecture/eShopModernizing)存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="753db-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="753db-126">目標</span><span class="sxs-lookup"><span data-stu-id="753db-126">Goals</span></span>

<span data-ttu-id="753db-127">本逐步解說的主要目標是要熟悉這些應用程式，以及其程式碼和設定。</span><span class="sxs-lookup"><span data-stu-id="753db-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="753db-128">您可以設定應用程式，使其產生和使用模擬資料，而不使用 SQL 資料庫進行測試。</span><span class="sxs-lookup"><span data-stu-id="753db-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="753db-129">這項選擇性設定是以分離的方式，以相依性插入為基礎。</span><span class="sxs-lookup"><span data-stu-id="753db-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="753db-130">案例1： ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="753db-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="753db-131">下圖顯示原始舊版 ASP.NET web 應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="753db-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![原始舊版 ASP.NET web 應用程式的簡單架構案例](./media/image5-1.png)

<span data-ttu-id="753db-133">從商務網域的觀點來看，這兩個應用程式都提供相同的目錄管理功能。</span><span class="sxs-lookup"><span data-stu-id="753db-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="753db-134">EShop enterprise 團隊的成員會使用此應用程式來查看和編輯產品目錄。</span><span class="sxs-lookup"><span data-stu-id="753db-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="753db-135">下圖顯示初始的應用程式螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="753db-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC 和 ASP.NET Web Forms 應用程式 (現有/舊版技術) ](./media/image5-2.png)

<span data-ttu-id="753db-137">ASP.NET 4.x 或舊版中的相依性 (針對 MVC 或 Web Form) 表示這些應用程式不會在 .NET Core 上執行，除非使用 ASP.NET Core MVC 完全重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="753db-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="753db-138">案例2： WCF 服務和 WinForms 用戶端應用程式 (3 層應用程式) </span><span class="sxs-lookup"><span data-stu-id="753db-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="753db-139">下圖顯示原始3層繼承應用程式的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="753db-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![使用 WCF 服務和 WinForms 用戶端應用程式之原始舊版3層應用程式的簡單架構案例](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="753db-141">優點</span><span class="sxs-lookup"><span data-stu-id="753db-141">Benefits</span></span>

<span data-ttu-id="753db-142">本逐步解說的優點很簡單：只要熟悉程式碼和初始應用程式即可。</span><span class="sxs-lookup"><span data-stu-id="753db-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-143">Next steps</span></span>

<span data-ttu-id="753db-144">深入探索 GitHub wiki 的這項內容：</span><span class="sxs-lookup"><span data-stu-id="753db-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="753db-145">ASP.NET MVC 和 Web Form "legacy" 應用程式的基準導覽</span><span class="sxs-lookup"><span data-stu-id="753db-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="753db-146">基準 WCF 服務和 WinForms (3 層) "legacy" 應用程式導覽</span><span class="sxs-lookup"><span data-stu-id="753db-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="753db-147">逐步解說2：使用 Windows 容器將現有的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="753db-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="753db-148">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-148">Overview</span></span>

<span data-ttu-id="753db-149">使用 Windows 容器改善現有 .NET 應用程式的部署，例如以 MVC、Web Form 或 WCF 為基礎、生產環境、開發和測試環境的部署。</span><span class="sxs-lookup"><span data-stu-id="753db-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="753db-150">目標</span><span class="sxs-lookup"><span data-stu-id="753db-150">Goals</span></span>

<span data-ttu-id="753db-151">本逐步解說的目的是要說明容器化現有 .NET Framework 應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="753db-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="753db-152">您可以：</span><span class="sxs-lookup"><span data-stu-id="753db-152">You can:</span></span>

- <span data-ttu-id="753db-153">使用 [Visual Studio 2017 Tools For Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 或更新版本) 來將您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="753db-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="753db-154">手動新增 [Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)來將您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="753db-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="753db-155">使用 [Img2Docker](https://github.com/docker/communitytools-image2docker-win) 工具 (Docker) 的開放原始碼工具來將您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="753db-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="753db-156">本逐步解說著重于適用于 Docker 方法的 Visual Studio 2017 工具，但其他兩種方法與使用 Dockerfile 相當類似。</span><span class="sxs-lookup"><span data-stu-id="753db-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="753db-157">案例1：容器化 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="753db-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="753db-158">下圖顯示容器化 eShop 舊版 web apps 應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="753db-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![簡化開發環境中容器化 ASP.NET 應用程式的架構圖](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="753db-160">案例2：容器化 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="753db-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="753db-161">下圖顯示具有容器化 WCF 服務的三層式應用程式案例。</span><span class="sxs-lookup"><span data-stu-id="753db-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![簡化開發環境中容器化 WCF 服務的架構圖](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="753db-163">優點</span><span class="sxs-lookup"><span data-stu-id="753db-163">Benefits</span></span>

<span data-ttu-id="753db-164">在容器中執行整合型應用程式的優點有很多種。</span><span class="sxs-lookup"><span data-stu-id="753db-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="753db-165">首先，您會建立應用程式的映射。</span><span class="sxs-lookup"><span data-stu-id="753db-165">First, you create an image for the application.</span></span> <span data-ttu-id="753db-166">從該時間點開始，每個部署都會在相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="753db-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="753db-167">每個容器都使用相同的作業系統版本、已安裝相同版本的相依性、使用相同的 .NET framework 版本，並使用相同的程式建立。</span><span class="sxs-lookup"><span data-stu-id="753db-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="753db-168">基本上，您可以使用 Docker 映射來控制應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="753db-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="753db-169">當您部署容器時，相依性會隨著應用程式移動。</span><span class="sxs-lookup"><span data-stu-id="753db-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="753db-170">另一個優點是，開發人員可以在 Windows 容器所提供的一致環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="753db-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="753db-171">只有特定版本才會出現的問題可以立即找出，而不是在預備環境或生產環境中呈現。</span><span class="sxs-lookup"><span data-stu-id="753db-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="753db-172">當應用程式在容器中執行時，開發小組成員所使用的開發環境差異較小。</span><span class="sxs-lookup"><span data-stu-id="753db-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="753db-173">容器化應用程式也有更簡維的相應放大麯線。</span><span class="sxs-lookup"><span data-stu-id="753db-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="753db-174">容器化應用程式可讓您根據 VM 或實體機器中) 的容器， (更多應用程式和服務實例，相較于每部機器的一般應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="753db-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="753db-175">這會轉譯為較高的密度和較少的必要資源，特別是當您使用協調器時，例如 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="753db-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="753db-176">容器化在理想的情況下，不需要對應用程式程式碼進行任何變更， (C \#) 。</span><span class="sxs-lookup"><span data-stu-id="753db-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="753db-177">在大部分的情況下，您只需要 (Dockerfile 和 Docker Compose 檔案) 的 Docker 部署中繼資料檔案。</span><span class="sxs-lookup"><span data-stu-id="753db-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-178">Next steps</span></span>

<span data-ttu-id="753db-179">深入探索 GitHub wiki 的這項內容：</span><span class="sxs-lookup"><span data-stu-id="753db-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="753db-180">如何使用 Windows 容器和 Docker 將 .NET Framework web 應用程式</span><span class="sxs-lookup"><span data-stu-id="753db-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="753db-181">將 Docker 支援新增至 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="753db-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="753db-182">逐步解說3：將 Windows 容器型應用程式部署至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="753db-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="753db-183">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="753db-183">Technical walkthrough availability</span></span>

<span data-ttu-id="753db-184">EShopModernizing GitHub 存放庫 wiki 提供完整的技術逐步解說： <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="753db-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="753db-185">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-185">Overview</span></span>

<span data-ttu-id="753db-186">部署至 Windows Server 2016 虛擬機器上的 Docker 主機 (VM) 在 Azure 中，可讓您快速設定開發/測試/預備環境。</span><span class="sxs-lookup"><span data-stu-id="753db-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="753db-187">它也可讓您在測試人員或商務使用者驗證應用程式時，提供一個共同的位置。</span><span class="sxs-lookup"><span data-stu-id="753db-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="753db-188">Vm 也可以是有效的基礎結構即服務 (IaaS) 生產環境。</span><span class="sxs-lookup"><span data-stu-id="753db-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="753db-189">目標</span><span class="sxs-lookup"><span data-stu-id="753db-189">Goals</span></span>

<span data-ttu-id="753db-190">本逐步解說的目標是要說明當您將 Windows 容器部署至以 Windows Server 2016 或更新版本為基礎的 Azure Vm 時，所擁有的多個替代方案。</span><span class="sxs-lookup"><span data-stu-id="753db-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="753db-191">案例</span><span class="sxs-lookup"><span data-stu-id="753db-191">Scenarios</span></span>

<span data-ttu-id="753db-192">本逐步解說涵蓋數個案例。</span><span class="sxs-lookup"><span data-stu-id="753db-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="753db-193">案例 A：透過 Docker 引擎連接從開發電腦部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![透過 Docker 引擎連接從開發電腦部署至 Azure VM](./media/image5-4.png)

<span data-ttu-id="753db-195">**圖5-4。**</span><span class="sxs-lookup"><span data-stu-id="753db-195">**Figure 5-4.**</span></span> <span data-ttu-id="753db-196">透過 Docker 引擎連接從開發電腦部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="753db-197">案例 B：透過 Docker 登錄部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![透過 Docker Registry 部署至 Azure VM](./media/image5-5.png)

<span data-ttu-id="753db-199">**圖5-5。**</span><span class="sxs-lookup"><span data-stu-id="753db-199">**Figure 5-5.**</span></span> <span data-ttu-id="753db-200">透過 Docker Registry 部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="753db-201">案例 C：從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

<span data-ttu-id="753db-203">**圖5-6。**</span><span class="sxs-lookup"><span data-stu-id="753db-203">**Figure 5-6.**</span></span> <span data-ttu-id="753db-204">從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM</span><span class="sxs-lookup"><span data-stu-id="753db-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="753db-205">適用于 Windows 容器的 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="753db-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="753db-206">適用于 Windows 容器的 Azure Vm 是以 Windows Server 2016、Windows 10 或更新版本為基礎的 Vm，並已設定 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="753db-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="753db-207">在大部分情況下，Azure Vm 會使用 Windows Server 2016。</span><span class="sxs-lookup"><span data-stu-id="753db-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="753db-208">Azure 目前提供名為 **Windows Server 2016 的 VM 與容器**。</span><span class="sxs-lookup"><span data-stu-id="753db-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="753db-209">您可以使用此 VM 來試用 Windows Server Core 或 Windows Nano Server 這項新的 Windows Server 容器功能。</span><span class="sxs-lookup"><span data-stu-id="753db-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="753db-210">已安裝容器 OS 映射，然後 VM 即可與 Docker 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="753db-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="753db-211">優點</span><span class="sxs-lookup"><span data-stu-id="753db-211">Benefits</span></span>

<span data-ttu-id="753db-212">雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm，但當您部署至 Azure 時，您可以更輕鬆地開始使用現成可用的 Windows Server 容器 Vm。</span><span class="sxs-lookup"><span data-stu-id="753db-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="753db-213">您也可以取得測試人員可存取的一般線上位置，以及透過 Azure 虛擬機器擴展集的自動調整規模。</span><span class="sxs-lookup"><span data-stu-id="753db-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-214">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-214">Next steps</span></span>

<span data-ttu-id="753db-215">深入探索 GitHub wiki 的這項內容：</span><span class="sxs-lookup"><span data-stu-id="753db-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="753db-216">逐步解說4：將您的 Windows 容器型應用程式部署至 Azure 容器實例 (ACI) </span><span class="sxs-lookup"><span data-stu-id="753db-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="753db-217">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="753db-217">Technical walkthrough availability</span></span>

<span data-ttu-id="753db-218">EShopModernizing GitHub 存放庫 wiki 提供完整的技術逐步解說：</span><span class="sxs-lookup"><span data-stu-id="753db-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="753db-219">[將應用程式部署到 ACI (Azure 容器實例) ](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="753db-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="753db-220">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-220">Overview</span></span>

<span data-ttu-id="753db-221">[Azure 容器實例 (ACI) ](https://docs.microsoft.com/azure/container-instances/) 是擁有容器開發/測試/預備環境的最快速方式，您可以在其中部署容器的單一實例。</span><span class="sxs-lookup"><span data-stu-id="753db-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="753db-222">目標</span><span class="sxs-lookup"><span data-stu-id="753db-222">Goals</span></span>

<span data-ttu-id="753db-223">本逐步解說將說明將 Windows 容器部署至 Azure 容器實例 (ACI) 的主要案例，以及如何將 eShopModernizing 應用程式部署至 ACI。</span><span class="sxs-lookup"><span data-stu-id="753db-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="753db-224">案例</span><span class="sxs-lookup"><span data-stu-id="753db-224">Scenarios</span></span>

<span data-ttu-id="753db-225">您可以將 eShopModernizing 應用程式部署到 ACI 中，例如只部署一個或所有應用程式 (MVC 應用程式、WebForms 應用程式或 WCF 服務) 。</span><span class="sxs-lookup"><span data-stu-id="753db-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="753db-226">在如下所示的案例中，您可以看到 ASP.NET MVC 應用程式加上 SQL Server 容器，並將它們部署為容器， (Azure 容器實例) 。</span><span class="sxs-lookup"><span data-stu-id="753db-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![從開發環境部署至 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="753db-228">優點</span><span class="sxs-lookup"><span data-stu-id="753db-228">Benefits</span></span>

<span data-ttu-id="753db-229">Azure Container Instances 能讓您在 Azure 中輕鬆建立及管理 Docker 容器，不需要佈建虛擬機器或採用高階服務即可完成。</span><span class="sxs-lookup"><span data-stu-id="753db-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="753db-230">使用 ACI，您可以在 Azure 中直接部署 Windows 容器，並使用完整功能變數名稱 (FQDN) 在幾秒鐘內， (前提是您已在 Docker 登錄中準備好 Windows 容器映射，例如 Docker Hub 或 Azure Container Registry) 。</span><span class="sxs-lookup"><span data-stu-id="753db-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="753db-231">考量</span><span class="sxs-lookup"><span data-stu-id="753db-231">Considerations</span></span>

<span data-ttu-id="753db-232">將具有完整 .NET Framework/ASP.NET 或 SQL Server 的 Windows 容器部署至 Azure 容器實例 (ACI) 並不像部署到一般 Docker 主機一樣快速，像是 Windows Server 2016 與 Windows 容器 (，因為您必須在每次從 Docker 登錄) 提取 (的 Docker 映射，以及 SQL 容器映射的大小 (15.1 GB) 和 ASP.NET 容器映射 (13.9 GB) 很大，不過，比起維護您自己的 Docker 主機， (在 Azure 中使用 Windows 容器 VM 永久的線上 Windows Server 2016) 不會在 Azure 中提及整個協調器，例如 Azure (AKS 中的 Kubernetes) 另一方面，是生產部署的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="753db-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="753db-233">總而言之，使用 Azure 容器實例是適用于開發/測試案例和 CI/CD 管線的極具吸引力選項。</span><span class="sxs-lookup"><span data-stu-id="753db-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-234">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-234">Next steps</span></span>

<span data-ttu-id="753db-235">深入探索 GitHub wiki 的這項內容：</span><span class="sxs-lookup"><span data-stu-id="753db-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="753db-236">逐步解說5：將您的 Windows 容器型應用程式部署至 Azure Container Service 中的 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="753db-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="753db-237">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="753db-237">Technical walkthrough availability</span></span>

<span data-ttu-id="753db-238">EShopModernizing GitHub 存放庫 wiki 提供完整的技術逐步解說：</span><span class="sxs-lookup"><span data-stu-id="753db-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="753db-239">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-239">Overview</span></span>

<span data-ttu-id="753db-240">以 Windows 容器為基礎的應用程式，很快就需要使用平臺，甚至是從 IaaS Vm 移離。</span><span class="sxs-lookup"><span data-stu-id="753db-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="753db-241">這是為了輕鬆達成高擴充性和更佳的自動化擴充性，並大幅改善自動化部署和版本設定的必要。</span><span class="sxs-lookup"><span data-stu-id="753db-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="753db-242">您可以使用[Azure Container service](https://azure.microsoft.com/services/container-service/)中提供的 orchestrator [Kubernetes](https://kubernetes.io/)來達成這些目標。</span><span class="sxs-lookup"><span data-stu-id="753db-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="753db-243">目標</span><span class="sxs-lookup"><span data-stu-id="753db-243">Goals</span></span>

<span data-ttu-id="753db-244">本逐步解說的目標是要瞭解如何將 Windows 容器型應用程式部署至 Kubernetes (在 Azure Container Service 中也稱為 *K8s*) 。</span><span class="sxs-lookup"><span data-stu-id="753db-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="753db-245">從頭開始部署至 Kubernetes 是兩個步驟的程式：</span><span class="sxs-lookup"><span data-stu-id="753db-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="753db-246">將 Kubernetes 叢集部署至 Azure Container Service。</span><span class="sxs-lookup"><span data-stu-id="753db-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="753db-247">將應用程式和相關資源部署至 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="753db-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="753db-248">案例</span><span class="sxs-lookup"><span data-stu-id="753db-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="753db-249">案例 A：從開發環境直接部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="753db-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![從開發環境直接部署至 Kubernetes 叢集](./media/image5-7.png)

<span data-ttu-id="753db-251">**圖5-7。**</span><span class="sxs-lookup"><span data-stu-id="753db-251">**Figure 5-7.**</span></span> <span data-ttu-id="753db-252">從開發環境直接部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="753db-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="753db-253">案例 B：從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="753db-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集](./media/image5-8.png)

<span data-ttu-id="753db-255">**圖5-8。**</span><span class="sxs-lookup"><span data-stu-id="753db-255">**Figure 5-8.**</span></span> <span data-ttu-id="753db-256">從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="753db-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="753db-257">優點</span><span class="sxs-lookup"><span data-stu-id="753db-257">Benefits</span></span>

<span data-ttu-id="753db-258">在 Kubernetes 中部署至叢集有許多優點。</span><span class="sxs-lookup"><span data-stu-id="753db-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="753db-259">最大的好處是您可以取得生產環境就緒的環境，在此環境中，您可以根據您想要使用的容器實例數目，在現有節點) 中，根據您想要使用 (內部擴充性來擴充應用程式，並根據叢集中的節點或 Vm 數目 (叢集) 的全域擴充性。</span><span class="sxs-lookup"><span data-stu-id="753db-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="753db-260">Azure Container Service 專為 Azure 優化常用的開放原始碼工具和技術。</span><span class="sxs-lookup"><span data-stu-id="753db-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="753db-261">您可以取得開放的解決方案，為您的容器和您的應用程式設定提供可攜性。</span><span class="sxs-lookup"><span data-stu-id="753db-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="753db-262">您可以選取大小、主機數目及 orchestrator 工具-Container Service 會處理所有其他專案。</span><span class="sxs-lookup"><span data-stu-id="753db-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="753db-263">有了 Kubernetes，開發人員可以從思考實體和虛擬機器著手，以規劃以容器為中心的基礎結構，以促進下列功能，還有其他功能：</span><span class="sxs-lookup"><span data-stu-id="753db-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="753db-264">以多個容器為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="753db-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="753db-265">複寫容器實例和水準自動調整</span><span class="sxs-lookup"><span data-stu-id="753db-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="753db-266">命名和探索 (例如內部 DNS) </span><span class="sxs-lookup"><span data-stu-id="753db-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="753db-267">平衡負載</span><span class="sxs-lookup"><span data-stu-id="753db-267">Balancing loads</span></span>

- <span data-ttu-id="753db-268">輪流更新</span><span class="sxs-lookup"><span data-stu-id="753db-268">Rolling updates</span></span>

- <span data-ttu-id="753db-269">散佈秘密</span><span class="sxs-lookup"><span data-stu-id="753db-269">Distributing secrets</span></span>

- <span data-ttu-id="753db-270">應用程式健康情況檢查</span><span class="sxs-lookup"><span data-stu-id="753db-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-271">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-271">Next steps</span></span>

<span data-ttu-id="753db-272">深入探索 GitHub wiki 的這項內容： <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="753db-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="753db-273">逐步解說6：將您的 Windows 容器型應用程式部署至適用于容器的 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="753db-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="753db-274">技術逐步解說可用性</span><span class="sxs-lookup"><span data-stu-id="753db-274">Technical walkthrough availability</span></span>

<span data-ttu-id="753db-275">EShopModernizing GitHub 存放庫 wiki 提供完整的技術逐步解說：</span><span class="sxs-lookup"><span data-stu-id="753db-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="753db-276">概觀</span><span class="sxs-lookup"><span data-stu-id="753db-276">Overview</span></span>

<span data-ttu-id="753db-277">使用 Windows 容器的簡單容器化應用程式可以輕鬆地部署到 Azure App Service 的容器。</span><span class="sxs-lookup"><span data-stu-id="753db-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="753db-278">這是大部分 Windows 容器型應用程式的建議方法。</span><span class="sxs-lookup"><span data-stu-id="753db-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="753db-279">目標</span><span class="sxs-lookup"><span data-stu-id="753db-279">Goals</span></span>

<span data-ttu-id="753db-280">本逐步解說的目標是要瞭解如何部署 Windows 容器型應用程式，以從登錄 (Docker Hub 或 Azure Container Registry) 的容器 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="753db-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="753db-281">案例</span><span class="sxs-lookup"><span data-stu-id="753db-281">Scenario</span></span>

![將 Windows 容器型應用程式部署至適用于容器的 Azure App Service](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="753db-283">優點</span><span class="sxs-lookup"><span data-stu-id="753db-283">Benefits</span></span>

<span data-ttu-id="753db-284">部署至適用于容器的 Azure App Service 可提供容器的優點，與 Azure App Service 的 PaaS 優點配對。</span><span class="sxs-lookup"><span data-stu-id="753db-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="753db-285">您可以輕鬆地垂直和水準調整 app service，也可以設定自動調整以符合不斷變化的需求。</span><span class="sxs-lookup"><span data-stu-id="753db-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="753db-286">您可以輕鬆地設定從登錄零停機和設定持續部署的更新。</span><span class="sxs-lookup"><span data-stu-id="753db-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="753db-287">後續步驟</span><span class="sxs-lookup"><span data-stu-id="753db-287">Next steps</span></span>

<span data-ttu-id="753db-288">深入探索 GitHub wiki 的這項內容： <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="753db-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="753db-289">[上一個](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md) 
> [下一步](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="753db-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
