---
title: "Azure 的開發程序"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |Azure 的開發程序"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 21826e2c90d234d873cc06bfae3bd22ce89a62d2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="development-process-for-azure"></a><span data-ttu-id="a02e3-103">Azure 的開發程序</span><span class="sxs-lookup"><span data-stu-id="a02e3-103">Development process for Azure</span></span>

> <span data-ttu-id="a02e3-104">_「 雲端，個人或小型企業可以貼齊其指並立即設定企業級服務 」 的。_</span><span class="sxs-lookup"><span data-stu-id="a02e3-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="a02e3-105">_-伊 Stephan_</span><span class="sxs-lookup"><span data-stu-id="a02e3-105">_- Roy Stephan_</span></span>

 ## <a name="vision"></a><span data-ttu-id="a02e3-106">Vision</span><span class="sxs-lookup"><span data-stu-id="a02e3-106">Vision</span></span>

> <span data-ttu-id="a02e3-107">*開發設計良好的 ASP.NET Core 應用程式的方式，使用 Visual Studio 或 dotnet CLI，Visual Studio 程式碼或您選擇的編輯器。*</span><span class="sxs-lookup"><span data-stu-id="a02e3-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="a02e3-108">ASP.NET Core 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="a02e3-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="a02e3-109">開發工具的選擇： IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="a02e3-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="a02e3-110">是否完整且功能強大的 IDE 或套輕量型且敏捷式軟體開發編輯器想，Microsoft 會具有您涵蓋開發 ASP.NET Core 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="a02e3-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="a02e3-111">**Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="a02e3-111">**Visual Studio 2017.**</span></span> <span data-ttu-id="a02e3-112">如果您使用*Visual Studio 2017* ASP.NET Core 應用程式，只要您有*.NET Core 跨平台開發*安裝的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a02e3-112">If you're using *Visual Studio 2017* you can build ASP.NET Core applications as long as you have the *.NET Core cross-platform development* workload installed.</span></span> <span data-ttu-id="a02e3-113">圖 10-1 會顯示在 Visual Studio 2017 的 [設定] 對話方塊所需的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a02e3-113">Figure 10-1 shows the required workload in the Visual Studio 2017 setup dialog.</span></span>

![](./media/image10-1.png)

<span data-ttu-id="a02e3-114">**圖 10-1。**</span><span class="sxs-lookup"><span data-stu-id="a02e3-114">**Figure 10-1.**</span></span> <span data-ttu-id="a02e3-115">在 Visual Studio 2017 安裝.NET Core 工作負載。</span><span class="sxs-lookup"><span data-stu-id="a02e3-115">Installing the .NET Core workload in Visual Studio 2017.</span></span>

[<span data-ttu-id="a02e3-116">下載 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a02e3-116">Download Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

<span data-ttu-id="a02e3-117">**Visual Studio 程式碼和 dotnet CLI** （適用於 Mac、 Linux 和 Windows 的跨平台工具）。</span><span class="sxs-lookup"><span data-stu-id="a02e3-117">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="a02e3-118">如果您想支援任何開發語言的輕量型和跨平台編輯器，您可以使用 Microsoft Visual Studio 程式碼及 dotnet CLI。</span><span class="sxs-lookup"><span data-stu-id="a02e3-118">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="a02e3-119">這些產品提供簡化的開發人員工作流程的簡單但強大體驗。</span><span class="sxs-lookup"><span data-stu-id="a02e3-119">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="a02e3-120">此外，Visual Studio 程式碼支援擴充功能的 C\#及 web 程式開發，提供 intellisense 和快顯的工作，在編輯器中。</span><span class="sxs-lookup"><span data-stu-id="a02e3-120">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="a02e3-121">下載.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a02e3-121">Download the .NET Core SDK</span></span>](https://www.microsoft.com/net/download/core)

[<span data-ttu-id="a02e3-122">下載 Visual Studio 程式碼</span><span class="sxs-lookup"><span data-stu-id="a02e3-122">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="a02e3-123">Azure 裝載的 ASP.NET Core 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="a02e3-123">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="a02e3-124">從每個開發人員的電腦，撰寫程式碼應用程式使用其偏好的語言，以及在本機測試它，啟動應用程式開發週期。</span><span class="sxs-lookup"><span data-stu-id="a02e3-124">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="a02e3-125">開發人員可以選擇其慣用的原始檔控制系統和持續整合 (CI) 及/或連續傳遞/部署 (CD) 使用的組建伺服器可以設定或根據內建的 Azure 功能。</span><span class="sxs-lookup"><span data-stu-id="a02e3-125">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="a02e3-126">若要開始開發使用 CI/CD 的 ASP.NET Core 應用程式，您可以使用 Visual Studio Team Services 或您的組織擁有 Team Foundation Server (TFS)。</span><span class="sxs-lookup"><span data-stu-id="a02e3-126">To get started with developing an ASP.NET Core application using CI/CD, you can use Visual Studio Team Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="a02e3-127">初始安裝</span><span class="sxs-lookup"><span data-stu-id="a02e3-127">Initial Setup</span></span>

<span data-ttu-id="a02e3-128">若要建立您的應用程式的發行管線，您需要有原始檔控制中的應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="a02e3-128">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="a02e3-129">設定本機儲存機制並將它連接至 team 專案中的遠端儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a02e3-129">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="a02e3-130">遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="a02e3-130">Follow these instructions:</span></span>

-   <span data-ttu-id="a02e3-131">[Visual Studio 與 Git 共用程式碼](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs)或</span><span class="sxs-lookup"><span data-stu-id="a02e3-131">[Share your code with Git and Visual Studio](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs) or</span></span>

-   [<span data-ttu-id="a02e3-132">與 TFVC 和 Visual Studio 共用程式碼</span><span class="sxs-lookup"><span data-stu-id="a02e3-132">Share your code with TFVC and Visual Studio</span></span>](https://docs.microsoft.com/vsts/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="a02e3-133">建立 Azure 應用程式服務，您要在其中部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="a02e3-133">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="a02e3-134">建立 Web 應用程式，請前往 Azure 入口網站上的 [應用程式服務] 刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="a02e3-134">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="a02e3-135">按一下 [+ 新增]，選取的 Web 應用程式範本、 按一下 [建立] 並提供名稱和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a02e3-135">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="a02e3-136">Web 應用程式仍可從 {name}。 名稱是.azurewebsites.net。</span><span class="sxs-lookup"><span data-stu-id="a02e3-136">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="a02e3-138">**圖 10-2。**</span><span class="sxs-lookup"><span data-stu-id="a02e3-138">**Figure 10-2.**</span></span> <span data-ttu-id="a02e3-139">在 Azure 入口網站建立新 Azure App Service Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a02e3-139">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="a02e3-140">CI 的建置程序將會執行自動化的組建，每當新的程式碼致力於專案的原始檔控制儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a02e3-140">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="a02e3-141">這可讓您建置程式碼的立即回應 （甚至是理想的情況下，會將自動化的測試的傳遞），而且可能部署。</span><span class="sxs-lookup"><span data-stu-id="a02e3-141">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="a02e3-142">這個 CI 組建將會產生 web 部署封裝成品並發佈它供您的 CD 程序。</span><span class="sxs-lookup"><span data-stu-id="a02e3-142">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="a02e3-143">定義 CI 建置流程</span><span class="sxs-lookup"><span data-stu-id="a02e3-143">Define your CI build process</span></span>](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#ci)

<span data-ttu-id="a02e3-144">請務必啟用連續整合，因此系統將組建排入佇列中的某個人您的小組認可新的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="a02e3-144">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="a02e3-145">測試建置，並確認它產生 web 部署套件做為其中一個及其成品。</span><span class="sxs-lookup"><span data-stu-id="a02e3-145">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="a02e3-146">建置成功時，您的 CD 程序會加入至 Azure web 應用程式部署 CI 組建的結果。</span><span class="sxs-lookup"><span data-stu-id="a02e3-146">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="a02e3-147">若要設定這種情況，您需要建立及設定*發行*，這會將部署到您的 Azure 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="a02e3-147">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="a02e3-148">定義您的 CD 發行流程</span><span class="sxs-lookup"><span data-stu-id="a02e3-148">Define your CD release process</span></span>](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#cd)

<span data-ttu-id="a02e3-149">CI/CD 管線設定之後，您就可以只讓 web 應用程式的更新，並將它們部署的原始檔控制中認可這些。</span><span class="sxs-lookup"><span data-stu-id="a02e3-149">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="a02e3-150">開發 Azure 裝載的 ASP.NET Core 應用程式的工作流程</span><span class="sxs-lookup"><span data-stu-id="a02e3-150">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="a02e3-151">一旦您已設定您的 Azure 帳戶和您 CI/CD 的程序，開發 Azure 裝載的 ASP.NET Core 應用程式很簡單。</span><span class="sxs-lookup"><span data-stu-id="a02e3-151">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="a02e3-152">以下是您通常會採用建置的說明圖 10-3 做為 Web 應用程式中，裝載在 Azure App Service 中的 ASP.NET Core 應用程式時的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="a02e3-152">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-3.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="a02e3-154">**圖 10-3。**</span><span class="sxs-lookup"><span data-stu-id="a02e3-154">**Figure 10-3.**</span></span> <span data-ttu-id="a02e3-155">逐步建立 ASP.NET Core 應用程式和其裝載在 Azure 中的工作流程</span><span class="sxs-lookup"><span data-stu-id="a02e3-155">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="a02e3-156">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="a02e3-156">Step 1.</span></span> <span data-ttu-id="a02e3-157">本機開發環境內部迴圈</span><span class="sxs-lookup"><span data-stu-id="a02e3-157">Local Dev Environment Inner Loop</span></span>

<span data-ttu-id="a02e3-158">開發您的 ASP.NET Core 應用程式部署至 Azure 並無不同否則開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="a02e3-158">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="a02e3-159">使用本機開發環境，您已經熟悉，不論是 Visual Studio 2017 或 dotnet CLI，Visual Studio 程式碼或您慣用的編輯器。</span><span class="sxs-lookup"><span data-stu-id="a02e3-159">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="a02e3-160">您可以撰寫程式碼、 執行和偵錯您的變更、 執行自動化的測試，及至原始檔控制，直到您準備好要將變更推送到您的共用原始檔控制儲存機制進行本機認可。</span><span class="sxs-lookup"><span data-stu-id="a02e3-160">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="a02e3-161">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="a02e3-161">Step 2.</span></span> <span data-ttu-id="a02e3-162">應用程式程式碼儲存機制</span><span class="sxs-lookup"><span data-stu-id="a02e3-162">Application Code Repository</span></span>

<span data-ttu-id="a02e3-163">當您準備好要與小組共用您的程式碼時，您應該從您的本機來源儲存機制推送變更至您的小組共用的原始程式碼儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a02e3-163">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="a02e3-164">如果您已在自訂的分支中，這個步驟通常包含您的程式碼合併到共用的分支 (可能是透過的方式[提取要求](https://docs.microsoft.com/vsts/git/pull-requests))。</span><span class="sxs-lookup"><span data-stu-id="a02e3-164">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](https://docs.microsoft.com/vsts/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="a02e3-165">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="a02e3-165">Step 3.</span></span> <span data-ttu-id="a02e3-166">持續整合組建伺服器:。</span><span class="sxs-lookup"><span data-stu-id="a02e3-166">Build Server: Continuous Integration.</span></span> <span data-ttu-id="a02e3-167">建置、 測試套件</span><span class="sxs-lookup"><span data-stu-id="a02e3-167">Build, Test, Package</span></span>

<span data-ttu-id="a02e3-168">只要新的認可對共用的應用程式程式碼儲存機制在組建伺服器上觸發新組建。</span><span class="sxs-lookup"><span data-stu-id="a02e3-168">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="a02e3-169">CI 程序的一部分，此組建應該完全編譯應用程式，並執行自動化的測試，以確認一切如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a02e3-169">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="a02e3-170">CI 程序的最終結果應為 web 應用程式，準備好進行部署的封裝的版本。</span><span class="sxs-lookup"><span data-stu-id="a02e3-170">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="a02e3-171">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="a02e3-171">Step 4.</span></span> <span data-ttu-id="a02e3-172">組建伺服器： 持續傳遞</span><span class="sxs-lookup"><span data-stu-id="a02e3-172">Build Server: Continuous Delivery</span></span>

<span data-ttu-id="a02e3-173">一次建置成功時，在 CD 程序將挑選所產生的組建成品。</span><span class="sxs-lookup"><span data-stu-id="a02e3-173">Once a build as succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="a02e3-174">這包括 web 部署套件。</span><span class="sxs-lookup"><span data-stu-id="a02e3-174">This will include a web deploy package.</span></span> <span data-ttu-id="a02e3-175">組建伺服器會將此封裝部署至 Azure App Service，以新建一個取代任何現有的服務。</span><span class="sxs-lookup"><span data-stu-id="a02e3-175">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="a02e3-176">此步驟通常為目標預備環境，但某些應用程式直接部署至實際執行透過 CD 的程序。</span><span class="sxs-lookup"><span data-stu-id="a02e3-176">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="a02e3-177">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="a02e3-177">Step 5.</span></span> <span data-ttu-id="a02e3-178">Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a02e3-178">Azure App Service.</span></span> <span data-ttu-id="a02e3-179">Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a02e3-179">Web App.</span></span>

<span data-ttu-id="a02e3-180">一旦部署之後，ASP.NET Core 應用程式會執行在 Azure App Service Web 應用程式的內容。</span><span class="sxs-lookup"><span data-stu-id="a02e3-180">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="a02e3-181">此 Web 應用程式可以監視，並進一步設定使用 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="a02e3-181">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="a02e3-182">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="a02e3-182">Step 6.</span></span> <span data-ttu-id="a02e3-183">實際執行監視和診斷</span><span class="sxs-lookup"><span data-stu-id="a02e3-183">Production Monitoring and Diagnostics</span></span>

<span data-ttu-id="a02e3-184">執行 Web 應用程式時，您可以監視應用程式的健全狀況和收集診斷和使用者行為資料。</span><span class="sxs-lookup"><span data-stu-id="a02e3-184">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="a02e3-185">Application Insights 隨附於 Visual Studio 中，並提供 ASP.NET 應用程式的自動檢測。</span><span class="sxs-lookup"><span data-stu-id="a02e3-185">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="a02e3-186">它可以提供您使用量、 例外狀況、 要求、 效能和記錄檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a02e3-186">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="a02e3-187">參考</span><span class="sxs-lookup"><span data-stu-id="a02e3-187">References</span></span>

<span data-ttu-id="a02e3-188">**建置和部署您的 ASP.NET Core 應用程式至 Azure**</span><span class="sxs-lookup"><span data-stu-id="a02e3-188">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core>


>[!div class="step-by-step"]
<span data-ttu-id="a02e3-189">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a02e3-189">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>
