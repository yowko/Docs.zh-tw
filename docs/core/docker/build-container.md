---
title: 使用 Docker 教學課程將應用程式容器化
description: 在本教學課程中，您將瞭解如何使用 Docker 容器化 .NET Core 應用程式。
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200024"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="961a9-103">教學課程：容器化 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="961a9-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="961a9-104">在本教學課程中，您將瞭解如何使用 Docker 容器化 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="961a9-105">容器有許多功能和優點，例如成為不可變的基礎結構、提供可移植的架構，以及啟用擴充性。</span><span class="sxs-lookup"><span data-stu-id="961a9-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="961a9-106">映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="961a9-107">在本教學課程中，您：</span><span class="sxs-lookup"><span data-stu-id="961a9-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="961a9-108">建立及發佈簡單的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="961a9-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="961a9-109">建立及設定適用於 .NET Core 的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="961a9-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="961a9-110">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="961a9-110">Build a Docker image</span></span>
> - <span data-ttu-id="961a9-111">建立及執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="961a9-111">Create and run a Docker container</span></span>

<span data-ttu-id="961a9-112">您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。</span><span class="sxs-lookup"><span data-stu-id="961a9-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="961a9-113">*Docker 平臺*會使用*docker 引擎*來快速建立應用程式，並將其封裝為*Docker 映射*。</span><span class="sxs-lookup"><span data-stu-id="961a9-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="961a9-114">這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="961a9-115">本教學課程**不適**用於 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="961a9-116">如果您使用 ASP.NET Core，請參閱[瞭解如何容器化 ASP.NET Core 應用程式](/aspnet/core/host-and-deploy/docker/building-net-docker-images)教學課程。</span><span class="sxs-lookup"><span data-stu-id="961a9-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="961a9-117">先決條件</span><span class="sxs-lookup"><span data-stu-id="961a9-117">Prerequisites</span></span>

<span data-ttu-id="961a9-118">安裝下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="961a9-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="961a9-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="961a9-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="961a9-120">如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="961a9-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="961a9-121">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="961a9-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="961a9-122">*Dockerfile* 和 .NET Core 範例應用程式的暫存工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="961a9-123">在本教學課程中，會使用*docker-作用*中的名稱做為工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="961a9-124">建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="961a9-124">Create .NET Core app</span></span>

<span data-ttu-id="961a9-125">您需要 Docker 容器將執行的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="961a9-126">開啟您的終端機，建立工作資料夾 (如果沒有)，並進入該資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="961a9-127">在工作資料夾中，執行下列命令以在名為*app*的子目錄中建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="961a9-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="961a9-128">您的資料夾樹狀目錄會如下所示：</span><span class="sxs-lookup"><span data-stu-id="961a9-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="961a9-129">此`dotnet new`命令會建立名為*App*的新資料夾，並產生 "Hello World" 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="961a9-130">從您的終端機會話變更目錄，並流覽至*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="961a9-131">使用`dotnet run`命令來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="961a9-132">應用程式將會執行，並`Hello World!`在命令下方列印：</span><span class="sxs-lookup"><span data-stu-id="961a9-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="961a9-133">預設範本會建立會列印到終端機的應用程式，然後立即終止。</span><span class="sxs-lookup"><span data-stu-id="961a9-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="961a9-134">針對此教學課程，您將使用無限期執行迴圈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="961a9-135">在文字編輯器中開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="961a9-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="961a9-136">如果您使用的是 Visual Studio Code，請從先前的終端機會話輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="961a9-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```
> code .
> ```
>
> <span data-ttu-id="961a9-137">這會在 Visual Studio Code 中開啟包含專案的*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="961a9-138">*Program.cs*看起來應該像下列 c # 程式碼：</span><span class="sxs-lookup"><span data-stu-id="961a9-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="961a9-139">使用下列每秒計算數字的程式碼來取代檔案：</span><span class="sxs-lookup"><span data-stu-id="961a9-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="961a9-140">儲存檔案，然後使用 `dotnet run` 再次測試程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="961a9-141">請記住此應用程式會無限期執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="961a9-142">使用 [取消] 命令<kbd>Ctrl + C</kbd>來停止它。</span><span class="sxs-lookup"><span data-stu-id="961a9-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="961a9-143">以下是範例輸出：</span><span class="sxs-lookup"><span data-stu-id="961a9-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="961a9-144">如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。</span><span class="sxs-lookup"><span data-stu-id="961a9-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="961a9-145">搭配 `dotnet run -- 5` 試用它以計算到五。</span><span class="sxs-lookup"><span data-stu-id="961a9-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="961a9-146">`--` 之後的任何參數都不會傳遞至 `dotnet run` 命令，而會改為傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="961a9-147">發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="961a9-147">Publish .NET Core app</span></span>

<span data-ttu-id="961a9-148">將 .NET Core 應用程式新增至 Docker 映射之前，必須先將它發佈。</span><span class="sxs-lookup"><span data-stu-id="961a9-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="961a9-149">最好讓容器執行應用程式的已發佈版本。</span><span class="sxs-lookup"><span data-stu-id="961a9-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="961a9-150">若要發佈應用程式，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="961a9-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="961a9-151">此命令會將您的應用程式編譯至 *publish* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="961a9-152">從工作資料夾通往 *publish* 資料夾的路徑應該是 `.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="961a9-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="961a9-153">Windows</span><span class="sxs-lookup"><span data-stu-id="961a9-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="961a9-154">從*應用程式*資料夾中，取得 [發行] 資料夾的目錄清單，以確認已建立*NetCore*檔案。</span><span class="sxs-lookup"><span data-stu-id="961a9-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="961a9-155">Linux</span><span class="sxs-lookup"><span data-stu-id="961a9-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="961a9-156">使用`ls`命令來取得目錄清單，並確認已建立*NetCore*檔案。</span><span class="sxs-lookup"><span data-stu-id="961a9-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="961a9-157">建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="961a9-157">Create the Dockerfile</span></span>

<span data-ttu-id="961a9-158">`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。</span><span class="sxs-lookup"><span data-stu-id="961a9-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="961a9-159">此檔案是名為*Dockerfile*的文字檔，沒有副檔名。</span><span class="sxs-lookup"><span data-stu-id="961a9-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="961a9-160">在包含 *.csproj*的目錄中建立名為*Dockerfile*的檔案，並在文字編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="961a9-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="961a9-161">本教學課程將使用 ASP.NET Core 執行時間映射（其中包含 .NET Core 執行時間映射），並對應至 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="961a9-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="961a9-162">這裡會刻意使用 ASP.NET Core 執行時間映射，雖然`mcr.microsoft.com/dotnet/core/runtime:3.1`映射可能已經使用過了。</span><span class="sxs-lookup"><span data-stu-id="961a9-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/core/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="961a9-163">`FROM`關鍵字需要完整的 Docker 容器映射名稱。</span><span class="sxs-lookup"><span data-stu-id="961a9-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="961a9-164">Microsoft Container Registry （MCR，mcr.microsoft.com）是 Docker Hub 的聯合，可裝載可公開存取的容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="961a9-165">`dotnet/core`區段是容器存放庫，其中的`aspnet`區段是容器映射名稱。</span><span class="sxs-lookup"><span data-stu-id="961a9-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="961a9-166">影像會標記為`3.1`，用於版本控制。</span><span class="sxs-lookup"><span data-stu-id="961a9-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="961a9-167">因此， `mcr.microsoft.com/dotnet/core/aspnet:3.1`是 .net Core 3.1 執行時間。</span><span class="sxs-lookup"><span data-stu-id="961a9-167">Thus, `mcr.microsoft.com/dotnet/core/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="961a9-168">請確定您已提取符合 SDK 目標執行時間的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="961a9-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="961a9-169">例如，在上一節中建立的應用程式會使用 .NET Core 3.1 SDK，而*Dockerfile*中所參考的基底映射會加上**3.1**。</span><span class="sxs-lookup"><span data-stu-id="961a9-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="961a9-170">儲存 *Dockerfile* 檔案。</span><span class="sxs-lookup"><span data-stu-id="961a9-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="961a9-171">工作資料夾的目錄結構應如下所示。</span><span class="sxs-lookup"><span data-stu-id="961a9-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="961a9-172">已省略一些較深層的檔案和資料夾，以節省文章中的空間：</span><span class="sxs-lookup"><span data-stu-id="961a9-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="961a9-173">從終端機執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="961a9-173">From your terminal, run the following command:</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="961a9-174">Docker 將會處理 *Dockerfile* 中的每一行。</span><span class="sxs-lookup"><span data-stu-id="961a9-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="961a9-175">命令中的`.`會指示 Docker 使用目前的資料夾來尋找 Dockerfile。 *Dockerfile* `docker build`</span><span class="sxs-lookup"><span data-stu-id="961a9-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="961a9-176">此命令會建立映射，並建立名為**counter 映射**的本機存放庫，以指向該映射。</span><span class="sxs-lookup"><span data-stu-id="961a9-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="961a9-177">當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：</span><span class="sxs-lookup"><span data-stu-id="961a9-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="961a9-178">請注意，這兩個映像會共用相同的**映像識別碼**值。</span><span class="sxs-lookup"><span data-stu-id="961a9-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="961a9-179">此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。</span><span class="sxs-lookup"><span data-stu-id="961a9-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="961a9-180">讓我們在*Dockerfile*中新增三個命令。</span><span class="sxs-lookup"><span data-stu-id="961a9-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="961a9-181">每個命令都會使用最後一個命令來建立新的映射圖層，其代表**計數器映射**存放庫進入點。</span><span class="sxs-lookup"><span data-stu-id="961a9-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="961a9-182">`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="961a9-183">在此範例中，會將*publish*資料夾複製到容器中名為*App*的資料夾。</span><span class="sxs-lookup"><span data-stu-id="961a9-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="961a9-184">`WORKDIR`命令會將容器內的**目前目錄**變更為*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="961a9-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="961a9-185">下一個命令 `ENTRYPOINT` 會指示 Docker 將容器設定為以可執行檔的形式執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="961a9-186">當容器啟動時，`ENTRYPOINT` 命令就會執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="961a9-187">當此命令結束時，容器將會自動停止。</span><span class="sxs-lookup"><span data-stu-id="961a9-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="961a9-188">從終端機中執行 `docker build -t counter-image -f Dockerfile .`，並在該命令完成時，執行 `docker images`。</span><span class="sxs-lookup"><span data-stu-id="961a9-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="961a9-189">*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。</span><span class="sxs-lookup"><span data-stu-id="961a9-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="961a9-190">最終的**映射識別碼**（您的會不同）是**cd11c3df9b19** ，接下來您將根據此映射建立容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="961a9-191">建立容器</span><span class="sxs-lookup"><span data-stu-id="961a9-191">Create a container</span></span>

<span data-ttu-id="961a9-192">您現在已有包含應用程式的映像，您可以建立一個容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="961a9-193">您可以兩種方式建立容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-193">You can create a container in two ways.</span></span> <span data-ttu-id="961a9-194">首先，建立已停止的新容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-194">First, create a new container that is stopped.</span></span>

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="961a9-195">上述`docker create`命令會根據**計數器映射**映射來建立容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="961a9-196">該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。</span><span class="sxs-lookup"><span data-stu-id="961a9-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="961a9-197">若要查看「所有」\*\* 容器的清單，請使用 `docker ps -a` 命令：</span><span class="sxs-lookup"><span data-stu-id="961a9-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="961a9-198">管理容器</span><span class="sxs-lookup"><span data-stu-id="961a9-198">Manage the container</span></span>

<span data-ttu-id="961a9-199">容器是使用特定名稱`core-counter`建立的，此名稱可用來管理容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="961a9-200">下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：</span><span class="sxs-lookup"><span data-stu-id="961a9-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="961a9-201">同樣地，`docker stop` 命令將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="961a9-202">下列範例會使用`docker stop`命令來停止容器，然後使用`docker ps`命令來顯示沒有容器正在執行：</span><span class="sxs-lookup"><span data-stu-id="961a9-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="961a9-203">連線到容器</span><span class="sxs-lookup"><span data-stu-id="961a9-203">Connect to a container</span></span>

<span data-ttu-id="961a9-204">當容器正在執行之後，您可以連線到它以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="961a9-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="961a9-205">使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="961a9-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="961a9-206">在此範例中，會使用<kbd>Ctrl + C</kbd>鍵，從執行中的容器卸離。</span><span class="sxs-lookup"><span data-stu-id="961a9-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="961a9-207">除非另有指定，否則此按鍵會結束容器中的進程，這會停止容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="961a9-208">`--sig-proxy=false`參數可確保<kbd>Ctrl + C</kbd>不會停止容器中的進程。</span><span class="sxs-lookup"><span data-stu-id="961a9-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="961a9-209">當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。</span><span class="sxs-lookup"><span data-stu-id="961a9-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="961a9-210">刪除容器</span><span class="sxs-lookup"><span data-stu-id="961a9-210">Delete a container</span></span>

<span data-ttu-id="961a9-211">基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。</span><span class="sxs-lookup"><span data-stu-id="961a9-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="961a9-212">刪除您先前建立的容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-212">Delete the container you previously created.</span></span> <span data-ttu-id="961a9-213">如果容器正在執行，請停止它。</span><span class="sxs-lookup"><span data-stu-id="961a9-213">If the container is running, stop it.</span></span>

```Docker
docker stop core-counter
```

<span data-ttu-id="961a9-214">下列範例會列出所有容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-214">The following example lists all containers.</span></span> <span data-ttu-id="961a9-215">它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="961a9-216">單一執行</span><span class="sxs-lookup"><span data-stu-id="961a9-216">Single run</span></span>

<span data-ttu-id="961a9-217">Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="961a9-218">使用此命令，就不需依序執行 `docker create` 及 `docker start`。</span><span class="sxs-lookup"><span data-stu-id="961a9-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="961a9-219">您也可以設定此命令，在容器停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="961a9-220">例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：</span><span class="sxs-lookup"><span data-stu-id="961a9-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="961a9-221">容器也會將參數傳遞至 .NET Core 應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="961a9-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="961a9-222">指示 .NET Core 應用程式只計算3個階段。</span><span class="sxs-lookup"><span data-stu-id="961a9-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="961a9-223">使用`docker run -it`， <kbd>Ctrl + C</kbd>命令會停止在容器中執行的進程，進而停止容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="961a9-224">由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="961a9-225">確認它不存在：</span><span class="sxs-lookup"><span data-stu-id="961a9-225">Verify that it doesn't exist:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="961a9-226">變更 ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="961a9-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="961a9-227">`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="961a9-228">例如，使用下列命令來執行 `bash` 或 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="961a9-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="961a9-229">視需要編輯命令。</span><span class="sxs-lookup"><span data-stu-id="961a9-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="961a9-230">Windows</span><span class="sxs-lookup"><span data-stu-id="961a9-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="961a9-231">在此範例中，`ENTRYPOINT` 會變更為 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="961a9-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="961a9-232"><kbd>Ctrl + C</kbd>已按下以結束進程並停止容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="961a9-233">Linux</span><span class="sxs-lookup"><span data-stu-id="961a9-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="961a9-234">在此範例中，`ENTRYPOINT` 會變更為 `bash`。</span><span class="sxs-lookup"><span data-stu-id="961a9-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="961a9-235">執行 `exit` 命令以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="961a9-236">基本命令</span><span class="sxs-lookup"><span data-stu-id="961a9-236">Essential commands</span></span>

<span data-ttu-id="961a9-237">Docker 有許多不同的命令，可建立、管理及與容器和映射進行互動。</span><span class="sxs-lookup"><span data-stu-id="961a9-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="961a9-238">這些 Docker 命令對於管理容器而言非常重要：</span><span class="sxs-lookup"><span data-stu-id="961a9-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="961a9-239">docker build</span><span class="sxs-lookup"><span data-stu-id="961a9-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="961a9-240">docker run</span><span class="sxs-lookup"><span data-stu-id="961a9-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="961a9-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="961a9-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="961a9-242">docker stop</span><span class="sxs-lookup"><span data-stu-id="961a9-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="961a9-243">docker rm</span><span class="sxs-lookup"><span data-stu-id="961a9-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="961a9-244">docker rmi</span><span class="sxs-lookup"><span data-stu-id="961a9-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="961a9-245">docker 映射</span><span class="sxs-lookup"><span data-stu-id="961a9-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="961a9-246">清除資源</span><span class="sxs-lookup"><span data-stu-id="961a9-246">Clean up resources</span></span>

<span data-ttu-id="961a9-247">在本教學課程中，您已建立容器和映射。</span><span class="sxs-lookup"><span data-stu-id="961a9-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="961a9-248">您可以視需要刪除這些資源。</span><span class="sxs-lookup"><span data-stu-id="961a9-248">If you want, delete these resources.</span></span> <span data-ttu-id="961a9-249">使用下列命令</span><span class="sxs-lookup"><span data-stu-id="961a9-249">Use the following commands to</span></span>

01. <span data-ttu-id="961a9-250">列出所有容器</span><span class="sxs-lookup"><span data-stu-id="961a9-250">List all containers</span></span>

    ```Docker
    docker ps -a
    ```

02. <span data-ttu-id="961a9-251">停止依其名稱執行的容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-251">Stop containers that are running by their name.</span></span>

    ```Docker
    docker stop counter-image
    ```

03. <span data-ttu-id="961a9-252">刪除容器</span><span class="sxs-lookup"><span data-stu-id="961a9-252">Delete the container</span></span>

    ```Docker
    docker rm counter-image
    ```

<span data-ttu-id="961a9-253">接下來，在電腦上刪除您不再需要的任何映像。</span><span class="sxs-lookup"><span data-stu-id="961a9-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="961a9-254">刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="961a9-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="961a9-255">您可以使用**映像識別碼**或**存放庫:標記**格式的字串。</span><span class="sxs-lookup"><span data-stu-id="961a9-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="961a9-256">使用 `docker images` 命令來查看已安裝的映像清單。</span><span class="sxs-lookup"><span data-stu-id="961a9-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="961a9-257">映像檔可能很大。</span><span class="sxs-lookup"><span data-stu-id="961a9-257">Image files can be large.</span></span> <span data-ttu-id="961a9-258">一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。</span><span class="sxs-lookup"><span data-stu-id="961a9-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="961a9-259">如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。</span><span class="sxs-lookup"><span data-stu-id="961a9-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="961a9-260">後續步驟</span><span class="sxs-lookup"><span data-stu-id="961a9-260">Next steps</span></span>

- [<span data-ttu-id="961a9-261">了解如何將 ASP.NET Core 應用程式容器化。</span><span class="sxs-lookup"><span data-stu-id="961a9-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- <span data-ttu-id="961a9-262">[嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="961a9-262">[Try the ASP.NET Core Microservice Tutorial.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)</span></span>
- [<span data-ttu-id="961a9-263">檢閱支援容器的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="961a9-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- <span data-ttu-id="961a9-264">[了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="961a9-264">[Read about Dockerfile commands.](https://docs.docker.com/engine/reference/builder/)</span></span>
- [<span data-ttu-id="961a9-265">探索 Visual Studio 的容器工具</span><span class="sxs-lookup"><span data-stu-id="961a9-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
