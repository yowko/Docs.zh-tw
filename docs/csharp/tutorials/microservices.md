---
title: "在 Docker 中裝載的微服務 - C#"
description: "了解如何建立在 Docker 容器中執行的 ASP.NET Core 服務"
keywords: ".NET, .NET Core, Docker, C#, ASP.NET, 微服務"
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5585db33fb5020ed18c26f32ce0b63f97353d20f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="eaf11-104">在 Docker 中裝載的微服務</span><span class="sxs-lookup"><span data-stu-id="eaf11-104">Microservices hosted in Docker</span></span>

## <a name="introduction"></a><span data-ttu-id="eaf11-105">簡介</span><span class="sxs-lookup"><span data-stu-id="eaf11-105">Introduction</span></span>

<span data-ttu-id="eaf11-106">本教學課程詳細說明在 Docker 容器中建置和部署 ASP.NET Core 微服務所需的工作。</span><span class="sxs-lookup"><span data-stu-id="eaf11-106">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="eaf11-107">您將在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-107">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="eaf11-108">如何使用 Yeoman 產生 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="eaf11-108">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="eaf11-109">如何建立開發 Docker 的環境</span><span class="sxs-lookup"><span data-stu-id="eaf11-109">How to create a development Docker environment</span></span>
* <span data-ttu-id="eaf11-110">如何根據現有的映像來建立 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-110">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="eaf11-111">如何將您的服務部署到 Docker 容器中。</span><span class="sxs-lookup"><span data-stu-id="eaf11-111">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="eaf11-112">您也會在本教學課程當中看到一些 C# 語言功能︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-112">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="eaf11-113">如何將 C# 物件轉換成 JSON 裝載。</span><span class="sxs-lookup"><span data-stu-id="eaf11-113">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="eaf11-114">如何建置不可變的資料傳輸物件</span><span class="sxs-lookup"><span data-stu-id="eaf11-114">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="eaf11-115">如何處理傳入 HTTP 要求和產生 HTTP 回應</span><span class="sxs-lookup"><span data-stu-id="eaf11-115">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="eaf11-116">如何使用可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="eaf11-116">How to work with nullable value types</span></span>

<span data-ttu-id="eaf11-117">您可以[檢視或下載本主題的範例應用程式 (英文)](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-117">You can [view or download the sample app](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="eaf11-118">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="eaf11-119">為何要使用 Docker？</span><span class="sxs-lookup"><span data-stu-id="eaf11-119">Why Docker?</span></span>

<span data-ttu-id="eaf11-120">Docker 可讓您輕鬆地建立標準的機器映像，在資料中心或公用雲端裝載您的服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-120">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="eaf11-121">Docker 可讓您設定映像，並視需要複製來調整應用程式的安裝。</span><span class="sxs-lookup"><span data-stu-id="eaf11-121">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="eaf11-122">本教學課程中的所有程式碼可在任何 .NET Core 環境中運作。</span><span class="sxs-lookup"><span data-stu-id="eaf11-122">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="eaf11-123">Docker 安裝的其他工作均適用於 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-123">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="eaf11-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="eaf11-124">Prerequisites</span></span>
<span data-ttu-id="eaf11-125">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="eaf11-125">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="eaf11-126">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="eaf11-126">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="eaf11-127">您可以在 Windows、Ubuntu Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-127">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="eaf11-128">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-128">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="eaf11-129">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-129">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="eaf11-130">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="eaf11-130">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="eaf11-131">您也需要安裝 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="eaf11-131">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="eaf11-132">如需適用於您平台的指示，請參閱 [Docker 安裝頁面 (英文)](http://www.docker.com/products/docker)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-132">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="eaf11-133">Docker 可以安裝在許多 Linux 發行版本、macOS 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="eaf11-133">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="eaf11-134">上述的參考頁面包含每個可用安裝的相關章節。</span><span class="sxs-lookup"><span data-stu-id="eaf11-134">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="eaf11-135">大部分元件都是由封裝管理員來安裝。</span><span class="sxs-lookup"><span data-stu-id="eaf11-135">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="eaf11-136">如果您已安裝 node.js 的封裝管理員 `npm`，可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="eaf11-136">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="eaf11-137">否則，請從 [nodejs.org](https://nodejs.org) 安裝最新的 NodeJs ，以安裝 npm 封裝管理員。</span><span class="sxs-lookup"><span data-stu-id="eaf11-137">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="eaf11-138">此時，您必須安裝一些支援 ASP.NET Core 開發的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="eaf11-138">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="eaf11-139">命令列範本使用 Yeoman、Bower、Grunt 及 Gulp。</span><span class="sxs-lookup"><span data-stu-id="eaf11-139">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="eaf11-140">如果您已經安裝上述工具就已準備就緒，否則請將下列命令輸入到您慣用的殼層：</span><span class="sxs-lookup"><span data-stu-id="eaf11-140">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="eaf11-141">`-g` 選項指出它是全域安裝，而且可在全系統使用這些工具。</span><span class="sxs-lookup"><span data-stu-id="eaf11-141">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="eaf11-142">(封裝的本機安裝範圍為單一專案)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-142">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="eaf11-143">在您安裝這些核心工具之後，您必須安裝 Yeoman ASP.NET 範本產生器︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-143">Once you've installed those core tools, you need to install the yeoman asp.net template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="eaf11-144">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="eaf11-144">Create the Application</span></span>

<span data-ttu-id="eaf11-145">現在您已安裝完所有工具，請建立新的 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-145">Now that you've installed all the tools, create a new asp.net core application.</span></span> <span data-ttu-id="eaf11-146">若要使用命令列產生器，請在您慣用的殼層中執行下列 Yeoman 命令︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-146">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="eaf11-147">此命令會提示您選取想要建立哪種類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-147">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="eaf11-148">對於這個微服務，需要有盡可能簡單且最為輕量的 Web 應用程式，因此選取 [空白 Web 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="eaf11-148">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="eaf11-149">範本會提示您輸入一個名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf11-149">The template will prompt you for a name.</span></span> <span data-ttu-id="eaf11-150">選取 [WeatherMicroservice]。</span><span class="sxs-lookup"><span data-stu-id="eaf11-150">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="eaf11-151">這個範本會為您建立八個檔案︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-151">The template creates eight files for you:</span></span>

* <span data-ttu-id="eaf11-152">.gitignore，自訂的 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-152">A .gitignore, customized for asp.net core applications.</span></span>
* <span data-ttu-id="eaf11-153">Startup.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-153">A Startup.cs file.</span></span> <span data-ttu-id="eaf11-154">這當中包含應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="eaf11-154">This contains the basis of the application.</span></span>
* <span data-ttu-id="eaf11-155">Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-155">A Program.cs file.</span></span> <span data-ttu-id="eaf11-156">這當中包含應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="eaf11-156">This contains the entry point of the application.</span></span>
* <span data-ttu-id="eaf11-157">WeatherMicroservice.csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-157">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="eaf11-158">這是應用程式的組建檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-158">This is the build file for the application.</span></span>
* <span data-ttu-id="eaf11-159">Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="eaf11-159">A Dockerfile.</span></span> <span data-ttu-id="eaf11-160">此指令碼會建立應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-160">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="eaf11-161">README.md。</span><span class="sxs-lookup"><span data-stu-id="eaf11-161">A README.md.</span></span> <span data-ttu-id="eaf11-162">這包含其他 ASP.NET Core 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="eaf11-162">This contains links to other asp.net core resources.</span></span>
* <span data-ttu-id="eaf11-163">web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-163">A web.config file.</span></span> <span data-ttu-id="eaf11-164">這包含基本組態資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-164">This contains basic configuration information.</span></span>
* <span data-ttu-id="eaf11-165">runtimeconfig.template.json 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-165">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="eaf11-166">這包含 IDE 所使用的偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="eaf11-166">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="eaf11-167">現在，您可以執行範本產生的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-167">Now you can run the template generated application.</span></span> <span data-ttu-id="eaf11-168">這是從命令列使用一系列工具來完成。</span><span class="sxs-lookup"><span data-stu-id="eaf11-168">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="eaf11-169">`dotnet` 命令會執行 .NET 開發所需的工具。</span><span class="sxs-lookup"><span data-stu-id="eaf11-169">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="eaf11-170">每個動詞都會執行不同的命令</span><span class="sxs-lookup"><span data-stu-id="eaf11-170">Each verb executes a different command</span></span>

<span data-ttu-id="eaf11-171">第一步是還原所有相依性︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-171">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="eaf11-172">Dotnet restore 會使用 NuGet 封裝管理員，將所有必要的封裝安裝到應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="eaf11-172">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="eaf11-173">它也會產生 project.json.lock 檔案。</span><span class="sxs-lookup"><span data-stu-id="eaf11-173">It also generates a project.json.lock file.</span></span> <span data-ttu-id="eaf11-174">這個檔案包含所參考之每個封裝的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-174">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="eaf11-175">在還原所有相依性之後，您就可以建置應用程式︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-175">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```

<span data-ttu-id="eaf11-176">然後在您建置應用程式之後，可以從命令列來執行它︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-176">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="eaf11-177">預設組態會接聽 http://localhost:5000 。</span><span class="sxs-lookup"><span data-stu-id="eaf11-177">The default configuration listens to http://localhost:5000.</span></span> <span data-ttu-id="eaf11-178">您可以開啟瀏覽器，然後瀏覽至該頁面，就會看到「Hello World!」</span><span class="sxs-lookup"><span data-stu-id="eaf11-178">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="eaf11-179">訊息。</span><span class="sxs-lookup"><span data-stu-id="eaf11-179">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="eaf11-180">ASP.NET Core 應用程式的結構</span><span class="sxs-lookup"><span data-stu-id="eaf11-180">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="eaf11-181">既然您已經建置應用程式，現在讓我們來看看如何實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="eaf11-181">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="eaf11-182">此時，產生的檔案當中有兩個特別有趣︰project.json 和 Startup.cs。</span><span class="sxs-lookup"><span data-stu-id="eaf11-182">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="eaf11-183">Project.json 包含該專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-183">Project.json contains information about the project.</span></span> <span data-ttu-id="eaf11-184">您會經常使用的兩個節點為「相依性」和「架構」。</span><span class="sxs-lookup"><span data-stu-id="eaf11-184">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="eaf11-185">相依性節點會列出此應用程式所需的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="eaf11-185">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="eaf11-186">目前，這是一個小型節點，只需要執行 Web 伺服器的封裝。</span><span class="sxs-lookup"><span data-stu-id="eaf11-186">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="eaf11-187">「架構」節點會指定將執行此應用程式的 .NET Framework 版本和組態。</span><span class="sxs-lookup"><span data-stu-id="eaf11-187">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="eaf11-188">在 Startup.cs 中實作應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-188">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="eaf11-189">此檔案包含啟動類別。</span><span class="sxs-lookup"><span data-stu-id="eaf11-189">This file contains the startup class.</span></span>

<span data-ttu-id="eaf11-190">ASP.NET Core 基礎結構會呼叫這兩個方法，來設定和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-190">The two methods are called by the asp.net core infrastructure to configure and run the application.</span></span> <span data-ttu-id="eaf11-191">`ConfigureServices` 方法描述此應用程式所需的服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-191">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="eaf11-192">您正在建置精簡的微服務，因此它不需要設定任何相依性。</span><span class="sxs-lookup"><span data-stu-id="eaf11-192">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="eaf11-193">`Configure` 方法會設定傳入 HTTP 要求的處理常式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-193">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="eaf11-194">範本會產生能以「Hello World!」文字回應任何要求的簡單處理常式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-194">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="eaf11-195">建置微服務</span><span class="sxs-lookup"><span data-stu-id="eaf11-195">Build a microservice</span></span>

<span data-ttu-id="eaf11-196">您即將建置的服務可提供世界上任何地方的氣象報告。</span><span class="sxs-lookup"><span data-stu-id="eaf11-196">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="eaf11-197">在實際執行應用程式中，您會呼叫某些服務來擷取氣象資料。</span><span class="sxs-lookup"><span data-stu-id="eaf11-197">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="eaf11-198">對我們的範例而言，則將會產生隨機的氣象預報。</span><span class="sxs-lookup"><span data-stu-id="eaf11-198">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="eaf11-199">您必須執行數項工作，才能實作隨機的氣象服務︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-199">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="eaf11-200">剖析傳入要求以讀取緯度和經度。</span><span class="sxs-lookup"><span data-stu-id="eaf11-200">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="eaf11-201">產生一些隨機的預測資料。</span><span class="sxs-lookup"><span data-stu-id="eaf11-201">Generate some random forecast data.</span></span>
* <span data-ttu-id="eaf11-202">將隨機的預測資料從 C# 物件轉換為 JSON 封包。</span><span class="sxs-lookup"><span data-stu-id="eaf11-202">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="eaf11-203">設定回應標頭，指出您的服務會傳送回 JSON。</span><span class="sxs-lookup"><span data-stu-id="eaf11-203">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="eaf11-204">撰寫回應。</span><span class="sxs-lookup"><span data-stu-id="eaf11-204">Write the response.</span></span>

<span data-ttu-id="eaf11-205">下一節將逐步說明每一個步驟。</span><span class="sxs-lookup"><span data-stu-id="eaf11-205">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="eaf11-206">剖析查詢字串。</span><span class="sxs-lookup"><span data-stu-id="eaf11-206">Parsing the Query String.</span></span>

<span data-ttu-id="eaf11-207">一開始要先剖析查詢字串。</span><span class="sxs-lookup"><span data-stu-id="eaf11-207">You'll begin by parsing the query string.</span></span> <span data-ttu-id="eaf11-208">服務會接受下列格式查詢字串的 'lat' 和 'long' 引數：</span><span class="sxs-lookup"><span data-stu-id="eaf11-208">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="eaf11-209">您需要的所有變更都是針對啟動類別中的 `app.Run` 定義為引數的 Lambda 運算式中進行。</span><span class="sxs-lookup"><span data-stu-id="eaf11-209">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="eaf11-210">Lambda 運算式中的引數就是要求的 `HttpContext`。</span><span class="sxs-lookup"><span data-stu-id="eaf11-210">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="eaf11-211">它的其中一個屬性是 `Request` 物件。</span><span class="sxs-lookup"><span data-stu-id="eaf11-211">One of its properties is the `Request` object.</span></span> <span data-ttu-id="eaf11-212">`Request` 物件具有 `Query` 屬性，其中包含要求的查詢字串上所有值的字典。</span><span class="sxs-lookup"><span data-stu-id="eaf11-212">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="eaf11-213">首先要加入的內容是尋找緯度和經度值︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-213">The first addition is to find the latitude and longitude values:</span></span>

<span data-ttu-id="eaf11-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "讀取查詢字串中的變數")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]</span></span>

<span data-ttu-id="eaf11-215">查詢字典值為 `StringValue` 型別。</span><span class="sxs-lookup"><span data-stu-id="eaf11-215">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="eaf11-216">該型別可以包含字串集合。</span><span class="sxs-lookup"><span data-stu-id="eaf11-216">That type can contain a collection of strings.</span></span> <span data-ttu-id="eaf11-217">對於氣象服務而言，每個值都是單一字串。</span><span class="sxs-lookup"><span data-stu-id="eaf11-217">For your weather service, each value is a single string.</span></span> <span data-ttu-id="eaf11-218">這就是在上述程式碼中呼叫 `FirstOrDefault()` 的原因。</span><span class="sxs-lookup"><span data-stu-id="eaf11-218">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="eaf11-219">接著，您必須將字串轉換為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="eaf11-219">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="eaf11-220">您用來將字串轉換為雙精度浮點數的方法是 `double.TryParse()`：</span><span class="sxs-lookup"><span data-stu-id="eaf11-220">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="eaf11-221">此方法會利用 C# 的輸出參數，指出該輸入字串是否能轉換為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="eaf11-221">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="eaf11-222">如果字串的確是有效的雙精度浮點數表示法，該方法會傳回 true，`result` 引數也會包含值。</span><span class="sxs-lookup"><span data-stu-id="eaf11-222">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="eaf11-223">如果字串不代表有效的雙精度浮點數，則該方法會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="eaf11-223">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="eaf11-224">您可以採用該 API 搭配使用「擴充方法」，來傳回「可為 Null 的雙精度浮點數」。</span><span class="sxs-lookup"><span data-stu-id="eaf11-224">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="eaf11-225">「可為 Null 的實值型別」是代表一些實值型別的一種型別，它也可以保留遺漏值或 Null 值。</span><span class="sxs-lookup"><span data-stu-id="eaf11-225">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="eaf11-226">在型別宣告附加 `?` 字元，即表示它是可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="eaf11-226">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="eaf11-227">擴充方法是指定義為靜態方法，但在第一個參數加上 `this` 修飾詞的方法，可以如同是該類別的成員一般來呼叫。</span><span class="sxs-lookup"><span data-stu-id="eaf11-227">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="eaf11-228">擴充方法只能在靜態類別中定義。</span><span class="sxs-lookup"><span data-stu-id="eaf11-228">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="eaf11-229">以下的類別定義包含可用於剖析的擴充方法：</span><span class="sxs-lookup"><span data-stu-id="eaf11-229">Here's the definition of the class containing the extension method for parse:</span></span>

<span data-ttu-id="eaf11-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "嘗試剖析為可為 Null")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]</span></span>

<span data-ttu-id="eaf11-231">`default(double?)` 運算式會傳回 `double?` 型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="eaf11-231">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="eaf11-232">該預設值是 Null (或遺漏) 值。</span><span class="sxs-lookup"><span data-stu-id="eaf11-232">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="eaf11-233">您可以使用此擴充方法，將查詢字串引數轉換成 double 型別︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-233">You can use this extension method to convert the query string arguments into the double type:</span></span>

<span data-ttu-id="eaf11-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "使用嘗試剖析擴充方法")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]</span></span>

<span data-ttu-id="eaf11-235">更新回應以包含該引數的值，即可輕鬆地測試剖析程式碼︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-235">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

<span data-ttu-id="eaf11-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "撰寫輸出回應")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]</span></span>

<span data-ttu-id="eaf11-237">此時，您可以執行 Web 應用程式，並查看您的剖析程式碼是否可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="eaf11-237">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="eaf11-238">將值加入至瀏覽器中的 Web 要求後，您應該會看到更新的結果。</span><span class="sxs-lookup"><span data-stu-id="eaf11-238">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="eaf11-239">建立隨機的氣象預報</span><span class="sxs-lookup"><span data-stu-id="eaf11-239">Build a random weather forecast</span></span>

<span data-ttu-id="eaf11-240">您的下一個工作是建立隨機的氣象預報。</span><span class="sxs-lookup"><span data-stu-id="eaf11-240">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="eaf11-241">讓我們從保存您所想要氣象預報值的資料容器開始︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-241">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="eaf11-242">接下來，建置會隨機設定這些值的建構函式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-242">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="eaf11-243">此建構函式會使用經度和緯度的值來植入亂數產生器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-243">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="eaf11-244">這表示相同位置會有相同的預報。</span><span class="sxs-lookup"><span data-stu-id="eaf11-244">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="eaf11-245">如果您變更緯度和經度的引數，您會得到不同的預報 (因為您從不同的種子開始)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-245">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

<span data-ttu-id="eaf11-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "氣象報告建構函式")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]</span></span>

<span data-ttu-id="eaf11-247">您現在能以您的回應方法產生 5 天的預報︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-247">You can now generate the 5-day forecast in your response method:</span></span>

<span data-ttu-id="eaf11-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "產生隨機的氣象報告")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]</span></span>

### <a name="build-the-json-response"></a><span data-ttu-id="eaf11-249">建立 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="eaf11-249">Build the JSON response.</span></span>

<span data-ttu-id="eaf11-250">伺服器上最後的程式碼工作是將 WeatherReport 陣列轉換為 JSON 封包，並傳送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="eaf11-250">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="eaf11-251">現在就開始建立 JSON 封包。</span><span class="sxs-lookup"><span data-stu-id="eaf11-251">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="eaf11-252">您要將 NewtonSoft JSON 序列化程式加入至相依性清單。</span><span class="sxs-lookup"><span data-stu-id="eaf11-252">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="eaf11-253">您可以使用 `dotnet` CLI 來完成：</span><span class="sxs-lookup"><span data-stu-id="eaf11-253">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="eaf11-254">然後，您可以使用 `JsonConvert` 類別來將該物件撰寫為字串︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-254">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

<span data-ttu-id="eaf11-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "將物件轉換為 JSON")]</span><span class="sxs-lookup"><span data-stu-id="eaf11-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]</span></span>

<span data-ttu-id="eaf11-256">上述程式碼會將預報物件 (`WeatherForecast` 物件清單) 轉換為 JSON 封包。</span><span class="sxs-lookup"><span data-stu-id="eaf11-256">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="eaf11-257">在您完成建構回應封包之後，您可以將內容類型設定為 `application/json`，然後撰寫字串。</span><span class="sxs-lookup"><span data-stu-id="eaf11-257">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="eaf11-258">應用程式現在會執行，並傳回隨機的預測。</span><span class="sxs-lookup"><span data-stu-id="eaf11-258">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="eaf11-259">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="eaf11-259">Build a Docker image</span></span>

<span data-ttu-id="eaf11-260">最後一項工作是在 Docker 中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-260">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="eaf11-261">我們會建立 Docker 容器，執行代表應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-261">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="eaf11-262">「Docker 映像」這個檔案會定義用來執行應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="eaf11-262">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="eaf11-263">「Docker 容器」代表 Docker 映像的執行中執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaf11-263">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="eaf11-264">比方說，您可以將「Docker 映像」視為「類別」，而將「Docker 容器」視為物件，或該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaf11-264">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="eaf11-265">針對本文的目的，很適合使用 ASP.NET 範本所建立的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="eaf11-265">The Dockerfile created by the asp.net template will serve for our purposes.</span></span> <span data-ttu-id="eaf11-266">讓我們來看看它的內容。</span><span class="sxs-lookup"><span data-stu-id="eaf11-266">Let's go over its contents.</span></span>

<span data-ttu-id="eaf11-267">第一行會指定來源映像︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-267">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="eaf11-268">Docker 可讓您根據來源範本來設定機器映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-268">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="eaf11-269">這表示當您啟動時，不需要提供所有的機器參數，您只需要提供所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="eaf11-269">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="eaf11-270">此處的變更會包含在我們的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="eaf11-270">The changes here will be to include our application.</span></span>

<span data-ttu-id="eaf11-271">在這個第一個範例中，我們將使用 `1.1-sdk-msbuild` 版的 DotNet 映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-271">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="eaf11-272">這是建立 Docker 工作環境的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-272">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="eaf11-273">此映像包含 DotNet Core 執行階段和 DotNet SDK。</span><span class="sxs-lookup"><span data-stu-id="eaf11-273">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="eaf11-274">那樣可以更容易開始使用和建置，但會建立較大的映象。</span><span class="sxs-lookup"><span data-stu-id="eaf11-274">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="eaf11-275">接下來的五行會安裝並建置您的應用程式︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-275">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="eaf11-276">這會將目前目錄中的專案檔案複製到 Docker VM，並還原所有封裝。</span><span class="sxs-lookup"><span data-stu-id="eaf11-276">This will copy the project file from the  current directory to the docker VM, and restore all the packages.</span></span> <span data-ttu-id="eaf11-277">使用 DotNet CLI，表示 Docker 映像必須包含 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="eaf11-277">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="eaf11-278">之後，會複製您應用程式其餘的部分，然後 dotnet publish 命令會建置和封裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-278">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="eaf11-279">此檔案的最後一行會執行該應用程式︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-279">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="eaf11-280">此設定的連接埠是參考 Dockerfile 最後一行 `dotnet` 的 `--server.urls` 引數。</span><span class="sxs-lookup"><span data-stu-id="eaf11-280">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="eaf11-281">`ENTRYPOINT` 命令會通知 Docker 哪些命令和命令列選項啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-281">The `ENTRYPOINT` command informs Docker  what command and command line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="eaf11-282">建置和執行容器中的映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-282">Building and running the image in a container.</span></span>

<span data-ttu-id="eaf11-283">讓我們在 Docker 容器內建置映像並執行服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-283">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="eaf11-284">不建議將本機目錄中的所有檔案複製到映像中。</span><span class="sxs-lookup"><span data-stu-id="eaf11-284">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="eaf11-285">相反地，您要在容器中建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaf11-285">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="eaf11-286">您會建立 `.dockerignore` 檔案，以指定不要複製到映像中的目錄。</span><span class="sxs-lookup"><span data-stu-id="eaf11-286">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="eaf11-287">不建議複製任何的組建資產。</span><span class="sxs-lookup"><span data-stu-id="eaf11-287">You don't want any of the build assets copied.</span></span> <span data-ttu-id="eaf11-288">請在 `.dockerignore` 檔案中指定組建和發行目錄：</span><span class="sxs-lookup"><span data-stu-id="eaf11-288">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="eaf11-289">您會使用 docker build 命令來建置映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-289">You build the image using the docker build command.</span></span> <span data-ttu-id="eaf11-290">從包含您程式碼的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="eaf11-290">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="eaf11-291">此命令會根據 Dockerfile 中的所有資訊來建置容器映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-291">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="eaf11-292">`-t` 引數會提供此容器映像的標籤或名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf11-292">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="eaf11-293">在上述命令列中，Docker 容器所使用的標籤是 `weather-microservice`。</span><span class="sxs-lookup"><span data-stu-id="eaf11-293">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="eaf11-294">此命令完成時，容器已準備好可以執行新的服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-294">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="eaf11-295">執行下列命令以啟動容器並啟動您的服務︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-295">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="eaf11-296">`-d` 選項表示要執行和目前終端機中斷連結的容器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-296">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="eaf11-297">這表示您不會在終端機看到命令輸出。</span><span class="sxs-lookup"><span data-stu-id="eaf11-297">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="eaf11-298">`-p` 選項會指出服務和主機之間的連接埠對應。</span><span class="sxs-lookup"><span data-stu-id="eaf11-298">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="eaf11-299">這裡指出連接埠 80 上的任何傳入要求都應該轉送到容器上的連接埠 5000。</span><span class="sxs-lookup"><span data-stu-id="eaf11-299">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="eaf11-300">使用 5000 才會符合您的服務正在從上述 Dockerfile 中指定的命令列引數接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="eaf11-300">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="eaf11-301">`--name` 引數會命名執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-301">The `--name` argument names your running container.</span></span> <span data-ttu-id="eaf11-302">該名稱可方便您使用該容器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-302">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="eaf11-303">您可以透過檢查以下命令，來查看映像是否正在執行︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-303">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="eaf11-304">如果您的容器正在執行中，您會在執行中處理序看到當中有一行將它列出。</span><span class="sxs-lookup"><span data-stu-id="eaf11-304">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="eaf11-305">(它可能是唯一的一行)。</span><span class="sxs-lookup"><span data-stu-id="eaf11-305">(It may be the only one).</span></span>

<span data-ttu-id="eaf11-306">開啟瀏覽器並瀏覽到 localhost，然後指定緯度和經度來測試您的服務︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-306">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="eaf11-307">附加至執行中的容器</span><span class="sxs-lookup"><span data-stu-id="eaf11-307">Attaching to a running container</span></span>

<span data-ttu-id="eaf11-308">當您在命令視窗中執行服務時，您可以看到為每個要求印出的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-308">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="eaf11-309">當您的容器在中斷連結模式中執行時，您看不到該資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-309">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="eaf11-310">Docker attach 命令可讓您附加至執行中的容器，以便查看記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="eaf11-310">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="eaf11-311">請從命令視窗執行這個命令︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-311">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="eaf11-312">`--sig-proxy=false` 引數表示不會將 `Ctrl-C` 命令傳送到此容器處理序，但會停止 `docker attach` 命令。</span><span class="sxs-lookup"><span data-stu-id="eaf11-312">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="eaf11-313">最後一個引數是要在 `docker run` 命令中提供給容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf11-313">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="eaf11-314">您也可以使用 Docker 指派的容器 ID 來參考任何容器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-314">You can also use the docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="eaf11-315">如果您並未在 `docker run` 中為您的容器指定名稱 ，您必須使用容器的 ID。</span><span class="sxs-lookup"><span data-stu-id="eaf11-315">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="eaf11-316">開啟瀏覽器，並瀏覽到您的服務。</span><span class="sxs-lookup"><span data-stu-id="eaf11-316">Open a browser and navigate to your service.</span></span> <span data-ttu-id="eaf11-317">您會在命令視窗中看到來自所附加執行中容器的診斷訊息。</span><span class="sxs-lookup"><span data-stu-id="eaf11-317">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="eaf11-318">按下 `Ctrl-C` 可停止附加處理序。</span><span class="sxs-lookup"><span data-stu-id="eaf11-318">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="eaf11-319">當您完成使用容器，可以將它停止︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-319">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="eaf11-320">您仍然可以重新啟動該容器和映像。</span><span class="sxs-lookup"><span data-stu-id="eaf11-320">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="eaf11-321">如果您想要從機器中移除該容器，您可以使用此命令︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-321">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="eaf11-322">如果您想要從機器中移除未使用的映像，您可以使用此命令︰</span><span class="sxs-lookup"><span data-stu-id="eaf11-322">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="eaf11-323">結論</span><span class="sxs-lookup"><span data-stu-id="eaf11-323">Conclusion</span></span> 

<span data-ttu-id="eaf11-324">在本教學課程中，您已建置 ASP.NET Core 微服務，並加入一些簡單的功能。</span><span class="sxs-lookup"><span data-stu-id="eaf11-324">In this tutorial, you built an asp.net core microservice, and added a few simple features.</span></span>

<span data-ttu-id="eaf11-325">您為該服務建置了 Docker 容器映像，並在您的機器上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="eaf11-325">You built a docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="eaf11-326">您將終端機視窗附加至該服務，並看到來自您服務的診斷訊息。</span><span class="sxs-lookup"><span data-stu-id="eaf11-326">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="eaf11-327">過程中，您也看到一些 C# 語言功能的實際運作。</span><span class="sxs-lookup"><span data-stu-id="eaf11-327">Along the way, you saw several features of the C# language in action.</span></span>

