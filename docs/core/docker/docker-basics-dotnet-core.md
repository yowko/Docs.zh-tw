---
title: 使用 Docker 將應用程式容器化
description: 本教學課程會教導如何建立基本的.NET Core 應用程式，並使用 Docker 對其進行容器化。
ms.date: 10/11/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: addaabb41e57e03a5cf4ec5b2fa3b8b4f3089b32
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372915"
---
# <a name="how-to-containerize-a-net-core-application"></a><span data-ttu-id="39914-103">如何將 .NET Core 應用程式容器化</span><span class="sxs-lookup"><span data-stu-id="39914-103">How to containerize a .NET Core application</span></span>

<span data-ttu-id="39914-104">本教學課程會教導 .NET Core 應用程式的 Docker 容器建置和部署作業。</span><span class="sxs-lookup"><span data-stu-id="39914-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="39914-105">[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用 [Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置應用程式並將其封裝為 [Docker 映像](https://docs.docker.com/glossary/?term=image)。</span><span class="sxs-lookup"><span data-stu-id="39914-105">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="39914-106">這些映像是使用 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 格式所撰寫，以在[分層式容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)中部署和執行。</span><span class="sxs-lookup"><span data-stu-id="39914-106">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="39914-107">您會在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="39914-107">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="39914-108">如何：建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="39914-108">How to create a Dockerfile</span></span>
> * <span data-ttu-id="39914-109">如何建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="39914-109">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="39914-110">如何將您的應用程式部署至 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="39914-110">How to deploy your app into a Docker container.</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="39914-111">.NET Core：最簡單的入門方式</span><span class="sxs-lookup"><span data-stu-id="39914-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="39914-112">建立 Docker 映像之前，您需要將應用程式容器化。</span><span class="sxs-lookup"><span data-stu-id="39914-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="39914-113">您可以在 Linux、MacOS 或 Windows 上建立它。</span><span class="sxs-lookup"><span data-stu-id="39914-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="39914-114">執行這項作業的最快速且最簡單方法是使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="39914-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="39914-115">如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="39914-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="39914-116">您可以使用[多架構標記](https://github.com/dotnet/announcements/issues/14)建置 Windows 和 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="39914-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="39914-117">第一個 .NET Core Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="39914-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="39914-118">Prerequisites</span></span>

<span data-ttu-id="39914-119">完成本教學課程：</span><span class="sxs-lookup"><span data-stu-id="39914-119">To complete this tutorial:</span></span>

#### <a name="net-core-sdk"></a><span data-ttu-id="39914-120">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="39914-120">.NET Core SDK</span></span>

* <span data-ttu-id="39914-121">安裝 [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="39914-121">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later.</span></span>

<span data-ttu-id="39914-122">如需 .NET Core 2.1 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="39914-122">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="39914-123">如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="39914-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="39914-124">需要安裝程式碼編輯器嗎？</span><span class="sxs-lookup"><span data-stu-id="39914-124">Need to install a code editor?</span></span> <span data-ttu-id="39914-125">請試用 [Visual Studio Code](https://code.visualstudio.com/download)！</span><span class="sxs-lookup"><span data-stu-id="39914-125">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="39914-126">安裝 Docker 用戶端</span><span class="sxs-lookup"><span data-stu-id="39914-126">Installing Docker Client</span></span>

<span data-ttu-id="39914-127">安裝 [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) 或更新版本的 Docker 用戶端。</span><span class="sxs-lookup"><span data-stu-id="39914-127">Install [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="39914-128">Docker 用戶端可以安裝於：</span><span class="sxs-lookup"><span data-stu-id="39914-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="39914-129">Linux 散發</span><span class="sxs-lookup"><span data-stu-id="39914-129">Linux distributions</span></span>

   * [<span data-ttu-id="39914-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="39914-130">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="39914-131">Debian</span><span class="sxs-lookup"><span data-stu-id="39914-131">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="39914-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="39914-132">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="39914-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="39914-133">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="39914-134">macOS</span><span class="sxs-lookup"><span data-stu-id="39914-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="39914-135">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="39914-135">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

### <a name="create-a-net-core-21-console-app-for-dockerization"></a><span data-ttu-id="39914-136">建立 .NET Core 2.1 主控台應用程式以進行 Docker 化</span><span class="sxs-lookup"><span data-stu-id="39914-136">Create a .NET Core 2.1 console app for Dockerization</span></span>

<span data-ttu-id="39914-137">開啟命令提示字元，並建立名為 *Hello* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="39914-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="39914-138">巡覽至您已建立的資料夾，並鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="39914-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="39914-139">讓我們快速逐步解說︰</span><span class="sxs-lookup"><span data-stu-id="39914-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="39914-140">[`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。</span><span class="sxs-lookup"><span data-stu-id="39914-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="39914-141">它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="39914-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="39914-142">`Hello.csproj`：</span><span class="sxs-lookup"><span data-stu-id="39914-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="39914-143">專案檔會指定還原相依性和建置程式所需的所有內容。</span><span class="sxs-lookup"><span data-stu-id="39914-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="39914-144">`OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="39914-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="39914-145">`TargetFramework` 標記會指定做為目標的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="39914-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="39914-146">在進階案例中，您可以指定多個目標架構，並透過單一作業建置所指定的架構。</span><span class="sxs-lookup"><span data-stu-id="39914-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="39914-147">在本教學課程中，我們會建置 .NET Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="39914-147">In this tutorial, we build for .NET Core 2.1.</span></span>

   <span data-ttu-id="39914-148">`Program.cs`：</span><span class="sxs-lookup"><span data-stu-id="39914-148">`Program.cs`:</span></span>

   <span data-ttu-id="39914-149">程式是從 `using System` 開始。</span><span class="sxs-lookup"><span data-stu-id="39914-149">The program starts by `using System`.</span></span> <span data-ttu-id="39914-150">此陳述式表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。</span><span class="sxs-lookup"><span data-stu-id="39914-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="39914-151">`System` 命名空間會包含像是 `string` 的基本結構或數字類型。</span><span class="sxs-lookup"><span data-stu-id="39914-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="39914-152">然後，我們會定義稱為 `Hello` 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="39914-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="39914-153">您可以將命名空間變更為任何所需的內容。</span><span class="sxs-lookup"><span data-stu-id="39914-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="39914-154">名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="39914-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="39914-155">這個陣列包含呼叫已編譯的程式時傳入的引數清單。</span><span class="sxs-lookup"><span data-stu-id="39914-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="39914-156">在本例中，程式只會撰寫 "Hello World"！</span><span class="sxs-lookup"><span data-stu-id="39914-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="39914-157">到主控台。</span><span class="sxs-lookup"><span data-stu-id="39914-157">to the console.</span></span>

   <span data-ttu-id="39914-158">**dotnet new** 會執行 [`dotnet restore`](../tools/dotnet-restore.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="39914-158">**dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="39914-159">**Dotnet restore** 會還原與 [NuGet](https://www.nuget.org/) (.NET 套件管理員) 呼叫之相依性的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="39914-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="39914-160">NuGet 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="39914-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="39914-161">分析 *Hello.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="39914-161">analyzes the *Hello.csproj* file.</span></span>
   * <span data-ttu-id="39914-162">下載檔案相依性 (或從您的電腦快取捕捉)。</span><span class="sxs-lookup"><span data-stu-id="39914-162">downloads the file dependencies (or grabs from your machine cache).</span></span>
   * <span data-ttu-id="39914-163">寫入 *obj/project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="39914-163">writes the *obj/project.assets.json* file.</span></span>

   <span data-ttu-id="39914-164">*project.assets.json* 檔案是一組完整 NuGet 相依性圖形、繫結解析和其他應用程式中繼資料。</span><span class="sxs-lookup"><span data-stu-id="39914-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="39914-165">[`dotnet build`](../tools/dotnet-build.md) 和 [`dotnet run`](../tools/dotnet-run.md) 這類其他工具會使用此必要檔案來正確處理原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="39914-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>

2. `$ dotnet run`

   <span data-ttu-id="39914-166">[`dotnet run`](../tools/dotnet-run.md) 會呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確認建置成功，然後呼叫 `dotnet <assembly.dll>` 以執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="39914-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>

    ```console
    $ dotnet run

    Hello World!
    ```

    <span data-ttu-id="39914-167">針對進階案例，如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="39914-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="39914-168">將 .NET Core 應用程式 Docker 化</span><span class="sxs-lookup"><span data-stu-id="39914-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="39914-169">Hello .NET Core 主控台應用程式會在本機成功地執行。</span><span class="sxs-lookup"><span data-stu-id="39914-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="39914-170">現在讓我們進行下一步，以及在 Docker 中建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="39914-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="39914-171">您的第一個 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="39914-171">Your first Dockerfile</span></span>

<span data-ttu-id="39914-172">開啟文字編輯器，並讓我們開始吧！</span><span class="sxs-lookup"><span data-stu-id="39914-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="39914-173">我們仍然從在其中建置應用程式的 Hello 目錄中工作。</span><span class="sxs-lookup"><span data-stu-id="39914-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="39914-174">將 Linux 或 [Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)的下列 Docker 指示新增至新檔案。</span><span class="sxs-lookup"><span data-stu-id="39914-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="39914-175">完成時，會以無副檔名的 **Dockerfile** 形式將它儲存至 Hello 目錄的根目錄 (您可能需要將檔案類型設定為 `All types (*.*)` 或類似項目)。</span><span class="sxs-lookup"><span data-stu-id="39914-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="39914-176">Dockerfile 包含循序執行的 Docker 建置指示。</span><span class="sxs-lookup"><span data-stu-id="39914-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="39914-177">第一個指令必須是 [**FROM**](https://docs.docker.com/engine/reference/builder/#from)。</span><span class="sxs-lookup"><span data-stu-id="39914-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="39914-178">此指令會初始化新的建置階段，並設定其餘指令的基底映像。</span><span class="sxs-lookup"><span data-stu-id="39914-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="39914-179">多架構標記會根據 Docker for Windows [容器模式](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)來提取 Windows 或 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="39914-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="39914-180">我們範例的基底映像是 microsoft/dotnet 存放庫中的 2.1-sdk 映像，</span><span class="sxs-lookup"><span data-stu-id="39914-180">The Base Image for our sample is the 2.1-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

<span data-ttu-id="39914-181">[**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) 指令會設定任何其餘 RUN、CMD、ENTRYPOINT、COPY 和 ADD Dockerfile 指令的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="39914-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="39914-182">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="39914-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="39914-183">在此情況下，WORKDIR 會設定為應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="39914-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="39914-184">[**COPY**](https://docs.docker.com/engine/reference/builder/#copy) 指令會從來源路徑中複製新檔案或目錄，並將它們新增至目的地容器檔案系統。</span><span class="sxs-lookup"><span data-stu-id="39914-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="39914-185">使用此指令，我們會將 C# 專案檔複製至容器。</span><span class="sxs-lookup"><span data-stu-id="39914-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="39914-186">[**RUN**](https://docs.docker.com/engine/reference/builder/#run) 指令會在目前映像的新層中執行任何命令，並認可結果。</span><span class="sxs-lookup"><span data-stu-id="39914-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="39914-187">產生的已認可映像用於 Dockerfile 中的下一步。</span><span class="sxs-lookup"><span data-stu-id="39914-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="39914-188">我們將執行 **dotnet restore** 來取得 C# 專案檔所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="39914-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="39914-189">這個 **COPY** 指令會將其餘的檔案複製至容器的新[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)。</span><span class="sxs-lookup"><span data-stu-id="39914-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="39914-190">我們會使用此 **RUN** 指令來發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="39914-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="39914-191">[**dotnet publish**](../tools/dotnet-publish.md) 命令會編譯應用程式，並讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。</span><span class="sxs-lookup"><span data-stu-id="39914-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="39914-192">我們的應用程式是使用**發行**組態所發行，並輸出至預設目錄。</span><span class="sxs-lookup"><span data-stu-id="39914-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="39914-193">[**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) 指令可讓容器執行為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="39914-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="39914-194">現在，您已經有 Dockerfile：</span><span class="sxs-lookup"><span data-stu-id="39914-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="39914-195">將您的應用程式複製至映像</span><span class="sxs-lookup"><span data-stu-id="39914-195">copies your app to the image</span></span>
* <span data-ttu-id="39914-196">您應用程式與映像的相依性</span><span class="sxs-lookup"><span data-stu-id="39914-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="39914-197">建置要執行為可執行檔的應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-app"></a><span data-ttu-id="39914-198">建置並執行 Hello .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-198">Build and run the Hello .NET Core app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="39914-199">必要 Docker 命令</span><span class="sxs-lookup"><span data-stu-id="39914-199">Essential Docker commands</span></span>

<span data-ttu-id="39914-200">這些 Docker 命令不可或缺：</span><span class="sxs-lookup"><span data-stu-id="39914-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="39914-201">docker build</span><span class="sxs-lookup"><span data-stu-id="39914-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="39914-202">docker run</span><span class="sxs-lookup"><span data-stu-id="39914-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="39914-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="39914-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="39914-204">docker stop</span><span class="sxs-lookup"><span data-stu-id="39914-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="39914-205">docker rm</span><span class="sxs-lookup"><span data-stu-id="39914-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="39914-206">docker rmi</span><span class="sxs-lookup"><span data-stu-id="39914-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="39914-207">docker image</span><span class="sxs-lookup"><span data-stu-id="39914-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="39914-208">建置並執行</span><span class="sxs-lookup"><span data-stu-id="39914-208">Build and run</span></span>

<span data-ttu-id="39914-209">您已撰寫 dockerfile；現在 Docker 會建置您的應用程式，然後執行容器。</span><span class="sxs-lookup"><span data-stu-id="39914-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="39914-210">`docker build` 命令的輸出應該類似下列主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="39914-210">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
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
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="39914-211">如您從輸出中所見，Docker 引擎已使用 Dockerfile 來建置我們的容器。</span><span class="sxs-lookup"><span data-stu-id="39914-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="39914-212">`docker run` 命令的輸出應該類似下列主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="39914-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="39914-213">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="39914-213">Congratulations!</span></span> <span data-ttu-id="39914-214">您已：</span><span class="sxs-lookup"><span data-stu-id="39914-214">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="39914-215">建立本機 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="39914-216">建立 Dockerfile 來建置您的第一個容器</span><span class="sxs-lookup"><span data-stu-id="39914-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="39914-217">建置並執行 Docker 化應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-217">Built and ran your Dockerized app</span></span>

## <a name="next-steps"></a><span data-ttu-id="39914-218">後續步驟</span><span class="sxs-lookup"><span data-stu-id="39914-218">Next steps</span></span>

<span data-ttu-id="39914-219">以下是一些您可以採取的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="39914-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="39914-220">.NET Docker 映像簡介影片</span><span class="sxs-lookup"><span data-stu-id="39914-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="39914-221">Visual Studio、Docker 和 Azure 容器執行個體更適合一起使用！</span><span class="sxs-lookup"><span data-stu-id="39914-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [<span data-ttu-id="39914-222">Docker for Azure 快速入門</span><span class="sxs-lookup"><span data-stu-id="39914-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="39914-223">在 Docker for Azure 上部署應用程式</span><span class="sxs-lookup"><span data-stu-id="39914-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> <span data-ttu-id="39914-224">如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。</span><span class="sxs-lookup"><span data-stu-id="39914-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="39914-225">此範例中所使用的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="39914-225">Docker Images used in this sample</span></span>

<span data-ttu-id="39914-226">在此範例中，使用下列 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="39914-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="39914-227">相關資源</span><span class="sxs-lookup"><span data-stu-id="39914-227">Related resources</span></span>

* [<span data-ttu-id="39914-228">.NET Core Docker 範例</span><span class="sxs-lookup"><span data-stu-id="39914-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [<span data-ttu-id="39914-229">Windows 容器上的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="39914-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="39914-230">.NET Framework Docker 範例</span><span class="sxs-lookup"><span data-stu-id="39914-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="39914-231">DockerHub 上的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39914-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="39914-232">將 .NET Core 應用程式 Docker 化 - Docker 教學課程</span><span class="sxs-lookup"><span data-stu-id="39914-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="39914-233">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="39914-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* <span data-ttu-id="39914-234">[將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="39914-234">[Deploying Docker Images from the Azure Container Registry to Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)</span></span>