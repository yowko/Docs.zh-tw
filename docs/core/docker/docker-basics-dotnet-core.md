---
title: "了解 Docker 與.NET Core 的基本概念"
description: "Docker 和.NET Core 的基本教學課程"
keywords: ".NET、.NET core、 Docker、 教學課程"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="30cd8-104">了解 Docker 與.NET Core 的基本概念</span><span class="sxs-lookup"><span data-stu-id="30cd8-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="30cd8-105">本教學課程將教導的 Docker 容器建置和部署.NET Core 應用程式的工作。</span><span class="sxs-lookup"><span data-stu-id="30cd8-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="30cd8-106">本教學課程的過程中，您了解：</span><span class="sxs-lookup"><span data-stu-id="30cd8-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="30cd8-107">如何建立 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="30cd8-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="30cd8-108">如何建立.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="30cd8-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="30cd8-109">如何將您的應用程式部署至 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="30cd8-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="30cd8-110">[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用[Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置並封裝為應用程式[Docker images](https://docs.docker.com/glossary/?term=image)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="30cd8-111">這些映像以撰寫[Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)部署和執行中的格式[分層容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="30cd8-112">若要開始使用.NET core： 最簡單的方式</span><span class="sxs-lookup"><span data-stu-id="30cd8-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="30cd8-113">之前建立 Docker 映像，您必須以化應用程式。</span><span class="sxs-lookup"><span data-stu-id="30cd8-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="30cd8-114">您可以在 Linux、 MacOS、 或 Windows 上建立它。</span><span class="sxs-lookup"><span data-stu-id="30cd8-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="30cd8-115">最快速而且簡單的方法是使用.NET 核心。</span><span class="sxs-lookup"><span data-stu-id="30cd8-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="30cd8-116">如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="30cd8-117">您可以建立具有 Windows 和 Linux 容器[多 arch 基礎標記](https://github.com/dotnet/announcements/issues/14)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="30cd8-118">第一個.NET Core Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="30cd8-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="30cd8-119">Prerequisites</span></span>

<span data-ttu-id="30cd8-120">若要完成本教學課程：</span><span class="sxs-lookup"><span data-stu-id="30cd8-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="30cd8-121">.NET 核心 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="30cd8-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="30cd8-122">安裝[.NET Core SDK 2.0](https://www.microsoft.com/net/core)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="30cd8-123">如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="30cd8-124">如果您還沒有這麼做，請安裝您最愛的程式碼編輯器 中。</span><span class="sxs-lookup"><span data-stu-id="30cd8-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="30cd8-125">需要安裝的程式碼編輯器？</span><span class="sxs-lookup"><span data-stu-id="30cd8-125">Need to install a code editor?</span></span> <span data-ttu-id="30cd8-126">再試一次[Visual Studio](https://visualstudio.com/downloads)！</span><span class="sxs-lookup"><span data-stu-id="30cd8-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="30cd8-127">安裝 Docker 用戶端</span><span class="sxs-lookup"><span data-stu-id="30cd8-127">Installing Docker Client</span></span>

<span data-ttu-id="30cd8-128">安裝[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)或更新版本的 Docker 用戶端。</span><span class="sxs-lookup"><span data-stu-id="30cd8-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="30cd8-129">Docker 用戶端可以安裝在：</span><span class="sxs-lookup"><span data-stu-id="30cd8-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="30cd8-130">Linux 散發套件</span><span class="sxs-lookup"><span data-stu-id="30cd8-130">Linux distributions</span></span>

   * [<span data-ttu-id="30cd8-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="30cd8-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="30cd8-132">Debian</span><span class="sxs-lookup"><span data-stu-id="30cd8-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="30cd8-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="30cd8-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="30cd8-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="30cd8-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="30cd8-135">macOS</span><span class="sxs-lookup"><span data-stu-id="30cd8-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="30cd8-136">[Windows](https://docs.docker.com/docker-for-windows/)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="30cd8-137">建立.NET Core 2.0 主控台應用程式，Dockerization</span><span class="sxs-lookup"><span data-stu-id="30cd8-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="30cd8-138">開啟命令提示字元，並建立名為 *Hello* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="30cd8-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="30cd8-139">導覽至您所建立的資料夾，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="30cd8-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="30cd8-140">讓我們快速逐步解說︰</span><span class="sxs-lookup"><span data-stu-id="30cd8-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="30cd8-141">[`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。</span><span class="sxs-lookup"><span data-stu-id="30cd8-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="30cd8-142">它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="30cd8-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="30cd8-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="30cd8-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="30cd8-144">專案檔會指定還原相依性和建置程式所需的所有內容。</span><span class="sxs-lookup"><span data-stu-id="30cd8-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="30cd8-145">`OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="30cd8-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="30cd8-146">`TargetFramework` 標記會指定做為目標的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="30cd8-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="30cd8-147">在進階案例中，您可以指定多個目標架構，並在單一作業中指定的架構來建置。</span><span class="sxs-lookup"><span data-stu-id="30cd8-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="30cd8-148">在本教學課程中，我們會建置.NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="30cd8-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="30cd8-149">`Program.cs`：</span><span class="sxs-lookup"><span data-stu-id="30cd8-149">`Program.cs`:</span></span>

   <span data-ttu-id="30cd8-150">藉由啟動程式`using System`。</span><span class="sxs-lookup"><span data-stu-id="30cd8-150">The program starts by `using System`.</span></span> <span data-ttu-id="30cd8-151">這個聲明意指，"的所有項目納入`System`進入範圍內，此檔案的命名空間。 」</span><span class="sxs-lookup"><span data-stu-id="30cd8-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="30cd8-152">`System` 命名空間會包含像是 `string` 的基本結構或數字類型。</span><span class="sxs-lookup"><span data-stu-id="30cd8-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="30cd8-153">然後，我們會定義稱為 `Hello` 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="30cd8-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="30cd8-154">您可以變更您想要的任何項目命名空間。</span><span class="sxs-lookup"><span data-stu-id="30cd8-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="30cd8-155">名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="30cd8-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="30cd8-156">這個陣列包含呼叫已編譯的程式時傳入的引數清單。</span><span class="sxs-lookup"><span data-stu-id="30cd8-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="30cd8-157">在本例中，程式只會寫入"Hello World ！"</span><span class="sxs-lookup"><span data-stu-id="30cd8-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="30cd8-158">到主控台。</span><span class="sxs-lookup"><span data-stu-id="30cd8-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="30cd8-159">在.NET Core 2.x， **dotnet 新**執行[ `dotnet restore` ](../tools/dotnet-restore.md)命令。</span><span class="sxs-lookup"><span data-stu-id="30cd8-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="30cd8-160">**Dotnet 還原**還原樹狀目錄中的相依性與[NuGet](https://www.nuget.org/)（.NET 封裝管理員） 呼叫。</span><span class="sxs-lookup"><span data-stu-id="30cd8-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="30cd8-161">NuGet 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="30cd8-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="30cd8-162">分析*Hello.csproj*檔案</span><span class="sxs-lookup"><span data-stu-id="30cd8-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="30cd8-163">會將檔案下載相依性 （或從您的電腦快取 grabs）</span><span class="sxs-lookup"><span data-stu-id="30cd8-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="30cd8-164">寫入*obj/project.assets.json*檔案</span><span class="sxs-lookup"><span data-stu-id="30cd8-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="30cd8-165">*Project.assets.json*檔案是一組完整的 NuGet 相依性圖形、 繫結解析度，以及其他應用程式中繼資料。</span><span class="sxs-lookup"><span data-stu-id="30cd8-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="30cd8-166">需要這個檔案由其他工具，例如[ `dotnet build` ](../tools/dotnet-build.md)和[ `dotnet run` ](../tools/dotnet-run.md)，才能正確地處理的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="30cd8-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="30cd8-167">[`dotnet run`](../tools/dotnet-run.md)呼叫[ `dotnet build` ](../tools/dotnet-build.md)確認建置成功，然後呼叫`dotnet <assembly.dll>`執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="30cd8-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="30cd8-168">進階案例中，請參閱[.NET Core 應用程式部署](../deploying/index.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="30cd8-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="30cd8-169">Dockerize.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="30cd8-170">Hello.NET Core 主控台應用程式成功地在本機執行。</span><span class="sxs-lookup"><span data-stu-id="30cd8-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="30cd8-171">現在讓我們更步驟進一步和建置和執行應用程式在 Docker 中。</span><span class="sxs-lookup"><span data-stu-id="30cd8-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="30cd8-172">您的第一個 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="30cd8-172">Your first Dockerfile</span></span>

<span data-ttu-id="30cd8-173">開啟文字編輯器，讓我們開始吧 ！</span><span class="sxs-lookup"><span data-stu-id="30cd8-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="30cd8-174">我們仍然使用我們建立了應用程式中的 Hello 目錄。</span><span class="sxs-lookup"><span data-stu-id="30cd8-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="30cd8-175">加入下列任一 Linux Docker 指示或[Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)到新的檔案。</span><span class="sxs-lookup"><span data-stu-id="30cd8-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="30cd8-176">完成後，請將它儲存為 Hello 目錄的根目錄中**Dockerfile**，不含副檔名 (您可能需要將檔案類型設定為`All types (*.*)`或類似)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="30cd8-177">Dockerfile 包含 Docker 建置的指示，以循序方式執行。</span><span class="sxs-lookup"><span data-stu-id="30cd8-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="30cd8-178">必須是第一個指令[ **FROM**](https://docs.docker.com/engine/reference/builder/#from)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="30cd8-179">這個指令會初始化新的組建階段，並設定基底映像的其餘指示進行。</span><span class="sxs-lookup"><span data-stu-id="30cd8-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="30cd8-180">多重 arch 標記提取 Windows 或 Linux 容器 Docker for Windows 根據[容器模式](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="30cd8-181">基底映像，我們的範例是 microsoft/dotnet 儲存機制中，從 2.0 sdk 映像</span><span class="sxs-lookup"><span data-stu-id="30cd8-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="30cd8-182">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir)指令集的工作目錄的任何其餘執行、 CMD、 進入點、 複製和新增 Dockerfile 指示。</span><span class="sxs-lookup"><span data-stu-id="30cd8-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="30cd8-183">如果此目錄不存在，它會建立它。</span><span class="sxs-lookup"><span data-stu-id="30cd8-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="30cd8-184">在此情況下，WORKDIR 設定應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="30cd8-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="30cd8-185">[**複製**](https://docs.docker.com/engine/reference/builder/#copy)指令會從來源路徑複製到新的檔案或目錄，並將它們加入到目的地容器檔案系統。</span><span class="sxs-lookup"><span data-stu-id="30cd8-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="30cd8-186">使用此指示中，我們會將 C# 專案檔複製到容器。</span><span class="sxs-lookup"><span data-stu-id="30cd8-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="30cd8-187">[**執行**](https://docs.docker.com/engine/reference/builder/#run)指令執行任何命令，在目前的映像之上一個新圖層中，並認可結果。</span><span class="sxs-lookup"><span data-stu-id="30cd8-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="30cd8-188">產生的認可映像用於 Dockerfile 的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="30cd8-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="30cd8-189">目前我們正在執行**dotnet 還原**取得所需的相依性的 C# 專案檔。</span><span class="sxs-lookup"><span data-stu-id="30cd8-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="30cd8-190">這**複製**指令將複製的其他檔案插入到我們容器新[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)。</span><span class="sxs-lookup"><span data-stu-id="30cd8-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="30cd8-191">我們會發佈應用程式與這個**執行**指令。</span><span class="sxs-lookup"><span data-stu-id="30cd8-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="30cd8-192">[ **Dotnet 發行**](../tools/dotnet-publish.md)命令編譯應用程式、 讀取整個專案檔中指定其相依性和目錄發佈設定檔的結果。</span><span class="sxs-lookup"><span data-stu-id="30cd8-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="30cd8-193">我們的應用程式一起發佈**發行**組態，以及輸出至預設的目錄。</span><span class="sxs-lookup"><span data-stu-id="30cd8-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="30cd8-194">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint)指示可讓容器執行可執行檔。</span><span class="sxs-lookup"><span data-stu-id="30cd8-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="30cd8-195">現在有了 Dockerfile 的：</span><span class="sxs-lookup"><span data-stu-id="30cd8-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="30cd8-196">將您的應用程式複製到映像</span><span class="sxs-lookup"><span data-stu-id="30cd8-196">copies your app to the image</span></span>
* <span data-ttu-id="30cd8-197">您的應用程式映像的相依性</span><span class="sxs-lookup"><span data-stu-id="30cd8-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="30cd8-198">建置可執行檔，以執行應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="30cd8-199">建置並執行 Hello.NET Core 2.0 應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="30cd8-200">必要的 Docker 命令</span><span class="sxs-lookup"><span data-stu-id="30cd8-200">Essential Docker commands</span></span>

<span data-ttu-id="30cd8-201">這些 Docker 命令是不可或缺：</span><span class="sxs-lookup"><span data-stu-id="30cd8-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="30cd8-202">docker 建置</span><span class="sxs-lookup"><span data-stu-id="30cd8-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="30cd8-203">執行的 docker</span><span class="sxs-lookup"><span data-stu-id="30cd8-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="30cd8-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="30cd8-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="30cd8-205">docker 停止</span><span class="sxs-lookup"><span data-stu-id="30cd8-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="30cd8-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="30cd8-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="30cd8-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="30cd8-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="30cd8-208">docker 映像</span><span class="sxs-lookup"><span data-stu-id="30cd8-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="30cd8-209">建置並執行</span><span class="sxs-lookup"><span data-stu-id="30cd8-209">Build and run</span></span>

<span data-ttu-id="30cd8-210">您已撰寫 dockerfile。現在 Docker 建置您的應用程式，並執行容器。</span><span class="sxs-lookup"><span data-stu-id="30cd8-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="30cd8-211">從輸出`docker build`命令應該類似下列的主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="30cd8-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="30cd8-212">您可以從輸出中看到，Docker 引擎會使用 Dockerfile 建立我們的容器。</span><span class="sxs-lookup"><span data-stu-id="30cd8-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="30cd8-213">從輸出`docker run`命令應該類似下列的主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="30cd8-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="30cd8-214">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="30cd8-214">Congratulations!</span></span> <span data-ttu-id="30cd8-215">只要有：</span><span class="sxs-lookup"><span data-stu-id="30cd8-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="30cd8-216">建立本機的.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="30cd8-217">建立 Dockerfile，以建置您的第一個容器</span><span class="sxs-lookup"><span data-stu-id="30cd8-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="30cd8-218">建置及執行 Dockerized 應用程式</span><span class="sxs-lookup"><span data-stu-id="30cd8-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="30cd8-219">後續步驟</span><span class="sxs-lookup"><span data-stu-id="30cd8-219">Next Steps</span></span>

<span data-ttu-id="30cd8-220">以下是一些您可以採取的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="30cd8-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="30cd8-221">.NET Docker 映像的影片簡介</span><span class="sxs-lookup"><span data-stu-id="30cd8-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="30cd8-222">Visual Studio、 Docker 和 Azure 容器執行個體一起提供更好 ！</span><span class="sxs-lookup"><span data-stu-id="30cd8-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="30cd8-223">Docker for Azure 快速入門</span><span class="sxs-lookup"><span data-stu-id="30cd8-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="30cd8-224">部署您的應用程式，azure docker</span><span class="sxs-lookup"><span data-stu-id="30cd8-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="30cd8-225">如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。</span><span class="sxs-lookup"><span data-stu-id="30cd8-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="30cd8-226">此範例中使用的 docker 映像</span><span class="sxs-lookup"><span data-stu-id="30cd8-226">Docker Images used in this sample</span></span>

<span data-ttu-id="30cd8-227">在此範例中使用下列的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="30cd8-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="30cd8-228">相關資源</span><span class="sxs-lookup"><span data-stu-id="30cd8-228">Related Resources</span></span>

* [<span data-ttu-id="30cd8-229">.NET core Docker 範例</span><span class="sxs-lookup"><span data-stu-id="30cd8-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="30cd8-230">Windows 容器上的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="30cd8-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="30cd8-231">.NET framework Docker 範例</span><span class="sxs-lookup"><span data-stu-id="30cd8-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="30cd8-232">ASP.NET Core DockerHub 上</span><span class="sxs-lookup"><span data-stu-id="30cd8-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="30cd8-233">Dockerize.NET Core 應用程式-Docker 教學課程</span><span class="sxs-lookup"><span data-stu-id="30cd8-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="30cd8-234">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="30cd8-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="30cd8-235">將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署</span><span class="sxs-lookup"><span data-stu-id="30cd8-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)