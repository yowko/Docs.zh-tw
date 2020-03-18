---
title: 使用 Docker 教學課程將應用程式容器化
description: 在本教程中，您將學習如何使用 Docker 對 .NET Core 應用程式進行容器化。
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157826"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="b2f8f-103">教程：容器化 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="b2f8f-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="b2f8f-104">本教學課程將教您如何建置包含 .NET Core 應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="b2f8f-105">映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="b2f8f-106">您將了解：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b2f8f-107">建立及發佈簡單的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2f8f-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="b2f8f-108">建立及設定適用於 .NET Core 的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="b2f8f-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="b2f8f-109">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="b2f8f-109">Build a Docker image</span></span>
> - <span data-ttu-id="b2f8f-110">建立及執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-110">Create and run a Docker container</span></span>

<span data-ttu-id="b2f8f-111">您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="b2f8f-112">*Docker 平臺*使用*Docker 引擎*快速構建和打包應用程式作為 Docker*映射*。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="b2f8f-113">這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!TIP]
> <span data-ttu-id="b2f8f-114">如果您正在使用現有的ASP.NET核心應用程式，請參閱[瞭解如何將ASP.NET核心應用程式教程容器化](/aspnet/core/host-and-deploy/docker/building-net-docker-images)。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-114">If you're working with an existing ASP.NET Core application, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2f8f-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="b2f8f-115">Prerequisites</span></span>

<span data-ttu-id="b2f8f-116">安裝下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-116">Install the following prerequisites:</span></span>

- <span data-ttu-id="b2f8f-117">[.NET 核心 3.1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="b2f8f-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="b2f8f-118">如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-118">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="b2f8f-119">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="b2f8f-119">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="b2f8f-120">*Dockerfile* 和 .NET Core 範例應用程式的暫存工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-120">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="b2f8f-121">在本教程中，名稱*docker 工作*用作工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-121">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="b2f8f-122">建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2f8f-122">Create .NET Core app</span></span>

<span data-ttu-id="b2f8f-123">您需要 Docker 容器將執行的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-123">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="b2f8f-124">開啟您的終端機，建立工作資料夾 (如果沒有)，並進入該資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-124">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="b2f8f-125">在工作資料夾中，運行以下命令以在名為 應用 的子目錄中創建新*專案*：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-125">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="b2f8f-126">您的資料夾樹狀目錄會如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-126">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="b2f8f-127">`dotnet new` 命令會建立名為 *app* 的新資料夾，並產生 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-127">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="b2f8f-128">請進入 *app* 資料夾，然後執行命令 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-128">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="b2f8f-129">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-129">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="b2f8f-130">預設範本所建立的應用程式會列印到終端機，然後結束。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-130">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="b2f8f-131">針對此教學課程，您將使用無限期執行迴圈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-131">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="b2f8f-132">在文字編輯器中開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-132">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="b2f8f-133">它目前看起來應該像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-133">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
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

<span data-ttu-id="b2f8f-134">使用下列每秒計算數字的程式碼來取代檔案：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-134">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="b2f8f-135">儲存檔案，然後使用 `dotnet run` 再次測試程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-135">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="b2f8f-136">請記住此應用程式會無限期執行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-136">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="b2f8f-137">使用取消命令<kbd>CTRL</kbd>+<kbd>C</kbd>停止它。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-137">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="b2f8f-138">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-138">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="b2f8f-139">如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-139">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="b2f8f-140">搭配 `dotnet run -- 5` 試用它以計算到五。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-140">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="b2f8f-141">`--` 之後的任何參數都不會傳遞至 `dotnet run` 命令，而會改為傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-141">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="b2f8f-142">發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2f8f-142">Publish .NET Core app</span></span>

<span data-ttu-id="b2f8f-143">將 .NET Core 應用程式新增至 Docker 映像之前，請先發佈它。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-143">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="b2f8f-144">建議您確定容器啟動時，會執行已發佈的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-144">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="b2f8f-145">從工作資料夾中，進入含有範例原始程式碼的 *app* 資料夾，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-145">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="b2f8f-146">此命令會將您的應用程式編譯至 *publish* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-146">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="b2f8f-147">從工作資料夾通往 *publish* 資料夾的路徑應該是 `.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="b2f8f-147">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="b2f8f-148">從*應用*資料夾中獲取發佈資料夾的目錄清單，以驗證是否創建了*myapp.dll*檔。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-148">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="b2f8f-149">如果您使用的是 Linux 或 macOS，請使用`ls`該命令獲取目錄清單並驗證是否創建了*myapp.dll*檔。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-149">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="b2f8f-150">建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="b2f8f-150">Create the Dockerfile</span></span>

<span data-ttu-id="b2f8f-151">`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-151">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="b2f8f-152">此檔是名為*Dockerfile*的文字檔，沒有副檔名。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-152">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="b2f8f-153">在您的終端機中，瀏覽至上一層目錄來移至您一開始建立的工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-153">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="b2f8f-154">在工作資料夾中建立名為 *Dockerfile* 的檔案，然後在文字編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-154">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="b2f8f-155">根據要容器化的應用程式類型，您將選擇ASP.NET核心運行時或 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-155">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="b2f8f-156">如有疑問，請選擇ASP.NET核心運行時，其中包括 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-156">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="b2f8f-157">本教程將使用ASP.NET核心運行時映射，但在前面各節中創建的應用程式是 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-157">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="b2f8f-158">ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="b2f8f-158">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="b2f8f-159">.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="b2f8f-159">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="b2f8f-160">該`FROM`命令告訴 Docker 從指定的存儲庫中下拉標記**為 3.1**的圖像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-160">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="b2f8f-161">請確保拉取與 SDK 目標運行時相匹配的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-161">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="b2f8f-162">例如，在上一節中創建的應用使用 .NET Core 3.1 *SDK，Dockerfile*中引用的基本映射用**3.1**標記。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-162">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="b2f8f-163">儲存 *Dockerfile* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-163">Save the *Dockerfile* file.</span></span> <span data-ttu-id="b2f8f-164">工作資料夾的目錄結構應如下所示。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-164">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="b2f8f-165">部分更下層的檔案和資料夾已省略，以節省文章空間：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-165">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="b2f8f-166">從終端機執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-166">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="b2f8f-167">Docker 將會處理 *Dockerfile* 中的每一行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-167">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="b2f8f-168">命令`.`中的`docker build`告訴 Docker 使用當前資料夾來查找*Dockerfile。*</span><span class="sxs-lookup"><span data-stu-id="b2f8f-168">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="b2f8f-169">此命令會建置映像，並建立名為 **myimage** 的本機存放庫以指向該映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="b2f8f-170">當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="b2f8f-171">請注意，這兩個映像會共用相同的**映像識別碼**值。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="b2f8f-172">此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="b2f8f-173">讓我們在 *Dockerfile* 中新增兩個命令。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="b2f8f-174">每個命令都創建一個新的圖像圖層，最終命令表示**圖像**存儲庫入口指向的圖像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-174">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="b2f8f-175">`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="b2f8f-176">在此範例中，會將 *publish* 資料夾複製到容器中名為 *app* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-176">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="b2f8f-177">下一個命令 `ENTRYPOINT` 會指示 Docker 將容器設定為以可執行檔的形式執行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-177">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="b2f8f-178">當容器啟動時，`ENTRYPOINT` 命令就會執行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="b2f8f-179">當此命令結束時，容器將會自動停止。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="b2f8f-180">從終端機中執行 `docker build -t myimage -f Dockerfile .`，並在該命令完成時，執行 `docker images`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="b2f8f-181">*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="b2f8f-182">最終的**映像識別碼** (您的映像識別碼將會不同) 為 **ddcc6646461b**，接下來您將根據此映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="b2f8f-183">建立容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-183">Create a container</span></span>

<span data-ttu-id="b2f8f-184">您現在已有包含應用程式的映像，您可以建立一個容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="b2f8f-185">您可以兩種方式建立容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-185">You can create a container in two ways.</span></span> <span data-ttu-id="b2f8f-186">首先，建立已停止的新容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="b2f8f-187">上述的 `docker create` 命令將根據 **myimage** 映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="b2f8f-188">該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="b2f8f-189">若要查看「所有」\*\* 容器的清單，請使用 `docker ps -a` 命令：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="b2f8f-190">管理容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-190">Manage the container</span></span>

<span data-ttu-id="b2f8f-191">每個容器會被指派隨機的名稱，可供您用來參考該容器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="b2f8f-192">例如，創建的容器會自動選擇**名稱gallant_lehmann（** 您的容器將不同），該名稱可用於啟動容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-192">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="b2f8f-193">您會使用 `docker create --name` 參數，利用特定的名稱來覆寫自動名稱。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="b2f8f-194">下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="b2f8f-195">同樣地，`docker stop` 命令將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="b2f8f-196">下面的示例使用 命令`docker stop`停止容器，然後使用 命令`docker ps`來顯示沒有正在運行的容器：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="b2f8f-197">連線到容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-197">Connect to a container</span></span>

<span data-ttu-id="b2f8f-198">當容器正在執行之後，您可以連線到它以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="b2f8f-199">使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="b2f8f-200">在此示例中<kbd>，CTRL + C</kbd>擊鍵用於從正在運行的容器分離。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-200">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="b2f8f-201">此擊鍵實際上可能會結束容器中的進程，這將停止容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-201">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="b2f8f-202">`--sig-proxy=false` 參數可確保 <kbd>CTRL + C</kbd> 不會停止容器中的流程。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="b2f8f-203">當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="b2f8f-204">刪除容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-204">Delete a container</span></span>

<span data-ttu-id="b2f8f-205">基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="b2f8f-206">刪除您先前建立的容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-206">Delete the container you previously created.</span></span> <span data-ttu-id="b2f8f-207">如果容器正在執行，請停止它。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-207">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="b2f8f-208">下列範例會列出所有容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-208">The following example lists all containers.</span></span> <span data-ttu-id="b2f8f-209">它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="b2f8f-210">單一執行</span><span class="sxs-lookup"><span data-stu-id="b2f8f-210">Single run</span></span>

<span data-ttu-id="b2f8f-211">Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="b2f8f-212">使用此命令，就不需依序執行 `docker create` 及 `docker start`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="b2f8f-213">您也可以設定此命令，在容器停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="b2f8f-214">例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="b2f8f-215">搭配 `docker run -it`，則 <kbd>CTRL + C</kbd> 命令將會停止正在容器中執行的程序，接著停止容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="b2f8f-216">由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="b2f8f-217">驗證它不存在：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-217">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="b2f8f-218">變更 ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="b2f8f-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="b2f8f-219">`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="b2f8f-220">例如，使用下列命令來執行 `bash` 或 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="b2f8f-221">視需要編輯命令。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="b2f8f-222">Windows</span><span class="sxs-lookup"><span data-stu-id="b2f8f-222">Windows</span></span>

<span data-ttu-id="b2f8f-223">在此範例中，`ENTRYPOINT` 會變更為 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="b2f8f-224"><kbd>按下 CTRL</kbd>+<kbd>C</kbd>以結束進程並停止容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-224"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a><span data-ttu-id="b2f8f-225">Linux</span><span class="sxs-lookup"><span data-stu-id="b2f8f-225">Linux</span></span>

<span data-ttu-id="b2f8f-226">在此範例中，`ENTRYPOINT` 會變更為 `bash`。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="b2f8f-227">執行 `quit` 命令以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="b2f8f-228">基本命令</span><span class="sxs-lookup"><span data-stu-id="b2f8f-228">Essential commands</span></span>

<span data-ttu-id="b2f8f-229">Docker 有許多不同的命令，其中涵蓋您想要使用容器和映像來執行的動作。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="b2f8f-230">這些 Docker 命令對於管理容器而言非常重要：</span><span class="sxs-lookup"><span data-stu-id="b2f8f-230">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="b2f8f-231">docker build</span><span class="sxs-lookup"><span data-stu-id="b2f8f-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="b2f8f-232">docker run</span><span class="sxs-lookup"><span data-stu-id="b2f8f-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="b2f8f-233">docker ps</span><span class="sxs-lookup"><span data-stu-id="b2f8f-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="b2f8f-234">docker stop</span><span class="sxs-lookup"><span data-stu-id="b2f8f-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="b2f8f-235">docker rm</span><span class="sxs-lookup"><span data-stu-id="b2f8f-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="b2f8f-236">docker rmi</span><span class="sxs-lookup"><span data-stu-id="b2f8f-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="b2f8f-237">碼頭映射</span><span class="sxs-lookup"><span data-stu-id="b2f8f-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="b2f8f-238">清除資源</span><span class="sxs-lookup"><span data-stu-id="b2f8f-238">Clean up resources</span></span>

<span data-ttu-id="b2f8f-239">在本教程中，您創建了容器和圖像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-239">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="b2f8f-240">您可以視需要刪除這些資源。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-240">If you want, delete these resources.</span></span> <span data-ttu-id="b2f8f-241">使用下列命令</span><span class="sxs-lookup"><span data-stu-id="b2f8f-241">Use the following commands to</span></span>

01. <span data-ttu-id="b2f8f-242">列出所有容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="b2f8f-243">停止正在執行的容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-243">Stop containers that are running.</span></span> <span data-ttu-id="b2f8f-244">`CONTAINER_NAME` 代表自動指派給容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="b2f8f-245">刪除容器</span><span class="sxs-lookup"><span data-stu-id="b2f8f-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="b2f8f-246">接下來，在電腦上刪除您不再需要的任何映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="b2f8f-247">刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="b2f8f-248">您可以使用**映像識別碼**或**存放庫:標記**格式的字串。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="b2f8f-249">使用 `docker images` 命令來查看已安裝的映像清單。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="b2f8f-250">映像檔可能很大。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-250">Image files can be large.</span></span> <span data-ttu-id="b2f8f-251">一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="b2f8f-252">如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2f8f-253">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2f8f-253">Next steps</span></span>

- [<span data-ttu-id="b2f8f-254">了解如何將 ASP.NET Core 應用程式容器化。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-254">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- <span data-ttu-id="b2f8f-255">[嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="b2f8f-255">[Try the ASP.NET Core Microservice Tutorial.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)</span></span>
- [<span data-ttu-id="b2f8f-256">檢閱支援容器的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="b2f8f-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- <span data-ttu-id="b2f8f-257">[了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="b2f8f-257">[Read about Dockerfile commands.](https://docs.docker.com/engine/reference/builder/)</span></span>
- [<span data-ttu-id="b2f8f-258">探索 Visual Studio 的容器工具</span><span class="sxs-lookup"><span data-stu-id="b2f8f-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
