---
title: Azure 開發程序
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | Azure 開發程序
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 8907c63f8dcd57ec22c3c196cbb1db52d91a3b5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169033"
---
# <a name="development-process-for-azure"></a><span data-ttu-id="a1a95-103">Azure 開發程序</span><span class="sxs-lookup"><span data-stu-id="a1a95-103">Development process for Azure</span></span>

> <span data-ttu-id="a1a95-104">_「借助雲端，個人和小型企業彈指之間就能立即設定企業級服務。」_</span><span class="sxs-lookup"><span data-stu-id="a1a95-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="a1a95-105">_- Roy Stephan_</span><span class="sxs-lookup"><span data-stu-id="a1a95-105">_- Roy Stephan_</span></span>

## <a name="vision"></a><span data-ttu-id="a1a95-106">願景</span><span class="sxs-lookup"><span data-stu-id="a1a95-106">Vision</span></span>

> <span data-ttu-id="a1a95-107">*以您喜歡的方式開發設計良好的 ASP.NET Core 應用程式，使用 Visual Studio 或 dotnet CLI 和 Visual Studio Code 或您選擇的編輯器。*</span><span class="sxs-lookup"><span data-stu-id="a1a95-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="a1a95-108">ASP.NET Core 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="a1a95-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="a1a95-109">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="a1a95-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="a1a95-110">不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都能支援您開發 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="a1a95-111">**Visual Studio 2019。**</span><span class="sxs-lookup"><span data-stu-id="a1a95-111">**Visual Studio 2019.**</span></span> <span data-ttu-id="a1a95-112">Visual Studio 2019 是針對 ASP.NET Core 開發應用程式的最佳 IDE。</span><span class="sxs-lookup"><span data-stu-id="a1a95-112">Visual Studio 2019 is the best-in-class IDE for developing applications for ASP.NET Core.</span></span> <span data-ttu-id="a1a95-113">它提供了許多功能，可提升開發人員的生產力。</span><span class="sxs-lookup"><span data-stu-id="a1a95-113">It offers a host of features that increase developer productivity.</span></span> <span data-ttu-id="a1a95-114">您可以使用它來開發應用程式，然後分析其效能和其他特性。</span><span class="sxs-lookup"><span data-stu-id="a1a95-114">You can use it to develop the application, then analyze its performance and other characteristics.</span></span> <span data-ttu-id="a1a95-115">整合式偵錯工具可讓您在程式碼執行時，暫停程式碼執行，並在程式碼前後逐步執行。</span><span class="sxs-lookup"><span data-stu-id="a1a95-115">The integrated debugger lets you pause code execution and step back and forth through code on the fly as it's running.</span></span> <span data-ttu-id="a1a95-116">內建的測試執行器可讓您組織您的測試及其結果，甚至可以在撰寫程式碼時執行即時單元測試。</span><span class="sxs-lookup"><span data-stu-id="a1a95-116">The built-in test runner lets you organize your tests and their results and can even perform live unit testing while you're coding.</span></span> <span data-ttu-id="a1a95-117">使用 Live Share 時，您可以與其他開發人員即時共同作業，並透過網路順暢地共用您的程式碼會話。</span><span class="sxs-lookup"><span data-stu-id="a1a95-117">Using Live Share, you can collaborate in real time with other developers, sharing your code session seamlessly over the network.</span></span> <span data-ttu-id="a1a95-118">當您準備好時，Visual Studio 包括將應用程式發佈至 Azure 所需的所有專案，或您可以裝載該應用程式的任何位置。</span><span class="sxs-lookup"><span data-stu-id="a1a95-118">And when you're ready, Visual Studio includes everything you need to publish your application to Azure or wherever you might host it.</span></span>

[<span data-ttu-id="a1a95-119">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a1a95-119">Download Visual Studio 2019</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

<span data-ttu-id="a1a95-120">**Visual Studio Code 和 dotnet CLI** (適用於 Mac、Linux 和 Windows 的跨平台工具)。</span><span class="sxs-lookup"><span data-stu-id="a1a95-120">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="a1a95-121">如果您偏好使用支援任何開發語言之輕量型且跨平台的編輯器，您可以使用 Microsoft Visual Studio Code 和 dotnet CLI。</span><span class="sxs-lookup"><span data-stu-id="a1a95-121">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="a1a95-122">這些產品提供簡單但強大的體驗，可簡化開發人員工作流程。</span><span class="sxs-lookup"><span data-stu-id="a1a95-122">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="a1a95-123">此外，Visual Studio Code 支援 C\# 及 Web 程式開發的延伸模組，並在編輯器中提供 Intellisense 和捷徑工作。</span><span class="sxs-lookup"><span data-stu-id="a1a95-123">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="a1a95-124">下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a1a95-124">Download the .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

[<span data-ttu-id="a1a95-125">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a1a95-125">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="a1a95-126">Azure 裝載之 ASP.NET Core 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="a1a95-126">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="a1a95-127">應用程式開發生命週期從每位開發人員的電腦開始，開發人員使用其偏好的語言撰寫應用程式的程式碼，並在本機進行測試。</span><span class="sxs-lookup"><span data-stu-id="a1a95-127">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="a1a95-128">開發人員可以選擇偏好的原始檔控制系統，並且可使用組建伺服器或根據內建的 Azure 功能，設定持續整合 (CI) 及/或持續傳遞/部署 (CD)。</span><span class="sxs-lookup"><span data-stu-id="a1a95-128">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="a1a95-129">若要使用 CI/CD 開始開發 ASP.NET Core 應用程式，您可以使用 Azure DevOps Services 或您組織自有的 Team Foundation Server (TFS)。</span><span class="sxs-lookup"><span data-stu-id="a1a95-129">To get started with developing an ASP.NET Core application using CI/CD, you can use Azure DevOps Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="a1a95-130">初始設定</span><span class="sxs-lookup"><span data-stu-id="a1a95-130">Initial setup</span></span>

<span data-ttu-id="a1a95-131">若要建立應用程式的發行管線，您需要讓應用程式程式碼進入原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="a1a95-131">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="a1a95-132">設定本機存放庫並在 Team 專案中將它連接至遠端存放庫。</span><span class="sxs-lookup"><span data-stu-id="a1a95-132">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="a1a95-133">遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="a1a95-133">Follow these instructions:</span></span>

- <span data-ttu-id="a1a95-134">[使用 Git 和 Visual Studio 共用程式碼](/azure/devops/git/share-your-code-in-git-vs)或</span><span class="sxs-lookup"><span data-stu-id="a1a95-134">[Share your code with Git and Visual Studio](/azure/devops/git/share-your-code-in-git-vs) or</span></span>

- [<span data-ttu-id="a1a95-135">使用 TFVC 和 Visual Studio 共用程式碼</span><span class="sxs-lookup"><span data-stu-id="a1a95-135">Share your code with TFVC and Visual Studio</span></span>](/azure/devops/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="a1a95-136">建立 Azure App Service，您將在其中部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-136">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="a1a95-137">前往 Azure 入口網站上的 [應用程式服務] 刀鋒視窗，建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-137">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="a1a95-138">按一下 [+新增]、選取 Web 應用程式範本、按一下 [建立]，然後提供名稱和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a1a95-138">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="a1a95-139">Web 應用程式將可從 {name}.azurewebsites.net 存取。</span><span class="sxs-lookup"><span data-stu-id="a1a95-139">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="a1a95-141">**圖10-1。**</span><span class="sxs-lookup"><span data-stu-id="a1a95-141">**Figure 10-1.**</span></span> <span data-ttu-id="a1a95-142">在 Azure 入口網站建立新的 Azure App Service Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-142">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="a1a95-143">每當新的程式碼認可到專案的原始檔控制存放庫時，CI 的建置程序將會執行自動化建置。</span><span class="sxs-lookup"><span data-stu-id="a1a95-143">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="a1a95-144">這可提供您程式碼建置 (以及在理想的情況下，通過自動化測試) 且可能部署的立即回應。</span><span class="sxs-lookup"><span data-stu-id="a1a95-144">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="a1a95-145">這個 CI 組建將會產生 Web 部署套件成品，並發佈它以供您的 CD 程序取用。</span><span class="sxs-lookup"><span data-stu-id="a1a95-145">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="a1a95-146">定義 CI 組建流程</span><span class="sxs-lookup"><span data-stu-id="a1a95-146">Define your CI build process</span></span>](/azure/devops/pipelines/ecosystems/dotnet-core)

<span data-ttu-id="a1a95-147">請務必啟用持續整合，以便每當您小組中有人認可新的程式碼時，系統便將建置排入佇列中。</span><span class="sxs-lookup"><span data-stu-id="a1a95-147">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="a1a95-148">測試組建，並確認它產生 Web 部署套件作為其中一個成品。</span><span class="sxs-lookup"><span data-stu-id="a1a95-148">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="a1a95-149">建置成功時，您的 CD 程序會將 CI 組建的結果部署至 Azure Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-149">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="a1a95-150">若要設定這種情況，您需要建立及設定「發行」\*\*，這會部署到您的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a1a95-150">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="a1a95-151">部署 Azure web 應用程式</span><span class="sxs-lookup"><span data-stu-id="a1a95-151">Deploy an Azure web app</span></span>](/azure/devops/pipelines/targets/webapp)

<span data-ttu-id="a1a95-152">CI/CD 管線設定之後，您就可以直接更新 Web 應用程式，並認可到原始檔控制中以便部署。</span><span class="sxs-lookup"><span data-stu-id="a1a95-152">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="a1a95-153">Azure 裝載之 ASP.NET Core 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="a1a95-153">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="a1a95-154">一旦您設定好 Azure 帳戶和 CI/CD 程序，開發 Azure 裝載的 ASP.NET Core 應用程式便很簡單。</span><span class="sxs-lookup"><span data-stu-id="a1a95-154">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="a1a95-155">以下是您在建立 ASP.NET Core 應用程式時，通常會採取的基本步驟，如圖10-2 中所示，以 Web 應用程式的形式裝載于 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a1a95-155">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-2.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="a1a95-157">**圖10-2。**</span><span class="sxs-lookup"><span data-stu-id="a1a95-157">**Figure 10-2.**</span></span> <span data-ttu-id="a1a95-158">建置 ASP.NET Core 應用程式並將其裝載在 Azure 中的逐步工作流程</span><span class="sxs-lookup"><span data-stu-id="a1a95-158">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="a1a95-159">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="a1a95-159">Step 1.</span></span> <span data-ttu-id="a1a95-160">本機開發環境內部迴圈</span><span class="sxs-lookup"><span data-stu-id="a1a95-160">Local dev environment inner loop</span></span>

<span data-ttu-id="a1a95-161">開發您的 ASP.NET Core 應用程式以便部署至 Azure，與用其他方式開發應用程式並無不同。</span><span class="sxs-lookup"><span data-stu-id="a1a95-161">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="a1a95-162">使用您慣用的本機開發環境，不論是 Visual Studio 2017 或 dotnet CLI 和 Visual Studio Code 或您偏好的編輯器。</span><span class="sxs-lookup"><span data-stu-id="a1a95-162">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="a1a95-163">您可以撰寫程式碼、執行變更並加以偵錯、執行自動化測試，以及本機認可至原始檔控制，直到您準備好要將變更推送到共用原始檔控制存放庫。</span><span class="sxs-lookup"><span data-stu-id="a1a95-163">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="a1a95-164">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="a1a95-164">Step 2.</span></span> <span data-ttu-id="a1a95-165">應用程式程式碼存放庫</span><span class="sxs-lookup"><span data-stu-id="a1a95-165">Application code repository</span></span>

<span data-ttu-id="a1a95-166">當您準備好要與小組共用程式碼時，您應該從您的本機來源存放庫推送變更至小組的共用原始程式碼存放庫。</span><span class="sxs-lookup"><span data-stu-id="a1a95-166">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="a1a95-167">如果您已在自訂的分支中工作，這個步驟通常牽涉到將您的程式碼合併到共用的分支 (可能是透過[提取要求](/azure/devops/git/pull-requests)的方式)。</span><span class="sxs-lookup"><span data-stu-id="a1a95-167">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](/azure/devops/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="a1a95-168">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="a1a95-168">Step 3.</span></span> <span data-ttu-id="a1a95-169">組建伺服器：持續整合。</span><span class="sxs-lookup"><span data-stu-id="a1a95-169">Build Server: Continuous integration.</span></span> <span data-ttu-id="a1a95-170">建置、測試、封裝</span><span class="sxs-lookup"><span data-stu-id="a1a95-170">build, test, package</span></span>

<span data-ttu-id="a1a95-171">每當對共用應用程式程式碼存放庫進行新的認可時，便會在組建伺服器上觸發新的建置。</span><span class="sxs-lookup"><span data-stu-id="a1a95-171">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="a1a95-172">在 CI 程序中，這項建置應該完整編譯應用程式，並執行自動化的測試，以確認一切如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a1a95-172">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="a1a95-173">CI 程序的最終結果應為 Web 應用程式的封裝版本，準備好進行部署。</span><span class="sxs-lookup"><span data-stu-id="a1a95-173">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="a1a95-174">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="a1a95-174">Step 4.</span></span> <span data-ttu-id="a1a95-175">組建伺服器：持續傳遞</span><span class="sxs-lookup"><span data-stu-id="a1a95-175">Build Server: Continuous delivery</span></span>

<span data-ttu-id="a1a95-176">建置成功之後，CD 程序會取得所產生的組建成品。</span><span class="sxs-lookup"><span data-stu-id="a1a95-176">Once a build has succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="a1a95-177">這會包括 Web 部署套件。</span><span class="sxs-lookup"><span data-stu-id="a1a95-177">This will include a web deploy package.</span></span> <span data-ttu-id="a1a95-178">組建伺服器會將此套件部署至 Azure App Service，以新建的服務來取代任何現有的服務。</span><span class="sxs-lookup"><span data-stu-id="a1a95-178">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="a1a95-179">此步驟通常以預備環境為目標，但某些應用程式會透過 CD 程序直接部署至生產環境。</span><span class="sxs-lookup"><span data-stu-id="a1a95-179">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="a1a95-180">步驟 5。</span><span class="sxs-lookup"><span data-stu-id="a1a95-180">Step 5.</span></span> <span data-ttu-id="a1a95-181">Azure App Service Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="a1a95-181">Azure App Service Web App</span></span>

<span data-ttu-id="a1a95-182">部署之後，ASP.NET Core 應用程式會在 Azure App Service Web 應用程式的內容裡執行。</span><span class="sxs-lookup"><span data-stu-id="a1a95-182">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="a1a95-183">可以使用 Azure 入口網站來監視及進一步設定此 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a95-183">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="a1a95-184">步驟 6.</span><span class="sxs-lookup"><span data-stu-id="a1a95-184">Step 6.</span></span> <span data-ttu-id="a1a95-185">生產環境監視及診斷</span><span class="sxs-lookup"><span data-stu-id="a1a95-185">Production monitoring and diagnostics</span></span>

<span data-ttu-id="a1a95-186">Web 應用程式在執行時，您可以監視應用程式的健康狀態，並收集診斷和使用者行為資料。</span><span class="sxs-lookup"><span data-stu-id="a1a95-186">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="a1a95-187">Application Insights 隨附於 Visual Studio 中，並提供 ASP.NET 應用程式的自動檢測。</span><span class="sxs-lookup"><span data-stu-id="a1a95-187">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="a1a95-188">它可以提供您使用方式、例外狀況、要求、效能和記錄檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a1a95-188">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="a1a95-189">參考資料</span><span class="sxs-lookup"><span data-stu-id="a1a95-189">References</span></span>

<span data-ttu-id="a1a95-190">**建置並部署 ASP.NET Core 應用程式至 Azure**</span><span class="sxs-lookup"><span data-stu-id="a1a95-190">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
><span data-ttu-id="a1a95-191">[上一個](test-asp-net-core-mvc-apps.md) 
>[下一步](azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a1a95-191">[Previous](test-asp-net-core-mvc-apps.md)
[Next](azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>
