---
title: 使用 Docker 教學課程將應用程式容器化
description: 在此教學課程中，您將了解如何使用 Docker 來將 .NET Core 應用程式容器化。
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 16edb129be679179450c485ced2586cea9ed9763
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609290"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="99dac-103">教學課程：將 .NET Core 應用程式容器化</span><span class="sxs-lookup"><span data-stu-id="99dac-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="99dac-104">本教學課程將教您如何建置包含 .NET Core 應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="99dac-105">映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="99dac-106">您將了解：</span><span class="sxs-lookup"><span data-stu-id="99dac-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="99dac-107">建立及發佈簡單的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="99dac-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="99dac-108">建立及設定適用於 .NET Core 的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="99dac-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="99dac-109">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="99dac-109">Build a Docker image</span></span>
> * <span data-ttu-id="99dac-110">建立及執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="99dac-110">Create and run a Docker container</span></span>

<span data-ttu-id="99dac-111">您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。</span><span class="sxs-lookup"><span data-stu-id="99dac-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="99dac-112">「Docker 平台」  會使用「Docker 引擎」  快速建置應用程式，並將其封裝為「Docker 映像」  。</span><span class="sxs-lookup"><span data-stu-id="99dac-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="99dac-113">這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99dac-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="99dac-114">Prerequisites</span></span>

<span data-ttu-id="99dac-115">安裝下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="99dac-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="99dac-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="99dac-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="99dac-117">如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="99dac-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="99dac-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="99dac-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="99dac-119">*Dockerfile* 和 .NET Core 範例應用程式的暫存工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="99dac-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="99dac-120">在本教學課程中，`docker-working` 名稱會作為工作資料夾使用。</span><span class="sxs-lookup"><span data-stu-id="99dac-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="99dac-121">使用 SDK 版本 2.2</span><span class="sxs-lookup"><span data-stu-id="99dac-121">Use SDK version 2.2</span></span>

<span data-ttu-id="99dac-122">如果您使用較新的 SDK (例如 3.0)，請務必強制您的應用程式使用 2.2 SDK。</span><span class="sxs-lookup"><span data-stu-id="99dac-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="99dac-123">在您的工作資料夾中建立名為 `global.json` 的檔案，並貼到下列 json 程式碼：</span><span class="sxs-lookup"><span data-stu-id="99dac-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="99dac-124">儲存此檔案。</span><span class="sxs-lookup"><span data-stu-id="99dac-124">Save this file.</span></span> <span data-ttu-id="99dac-125">檔案的存在將強制 .NET Core 針對從此資料夾及以下資料夾呼叫的所有 `dotnet` 命令使用版本 2.2。</span><span class="sxs-lookup"><span data-stu-id="99dac-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="99dac-126">建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="99dac-126">Create .NET Core app</span></span>

<span data-ttu-id="99dac-127">您需要 Docker 容器將執行的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="99dac-128">開啟您的終端機，建立工作資料夾 (如果沒有)，並進入該資料夾。</span><span class="sxs-lookup"><span data-stu-id="99dac-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="99dac-129">在工作資料夾中執行下列命令，在名為 app 的子目錄中建立新專案：</span><span class="sxs-lookup"><span data-stu-id="99dac-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="99dac-130">您的資料夾樹狀目錄會如下所示：</span><span class="sxs-lookup"><span data-stu-id="99dac-130">Your folder tree will look like the following:</span></span>

```console
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="99dac-131">`dotnet new` 命令會建立名為 *app* 的新資料夾，並產生 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="99dac-132">請進入 *app* 資料夾，然後執行命令 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="99dac-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="99dac-133">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="99dac-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="99dac-134">預設範本所建立的應用程式會列印到終端機，然後結束。</span><span class="sxs-lookup"><span data-stu-id="99dac-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="99dac-135">針對此教學課程，您將使用無限期執行迴圈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="99dac-136">在文字編輯器中開啟 **Program.cs** 檔案。</span><span class="sxs-lookup"><span data-stu-id="99dac-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="99dac-137">它目前看起來應該像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="99dac-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="99dac-138">使用下列每秒計算數字的程式碼來取代檔案：</span><span class="sxs-lookup"><span data-stu-id="99dac-138">Replace the file with the following code that counts numbers every second:</span></span>

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="99dac-139">儲存檔案，然後使用 `dotnet run` 再次測試程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="99dac-140">請記住此應用程式會無限期執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="99dac-141">使用取消命令 <kbd>CTRL + C</kbd> 來停止它。</span><span class="sxs-lookup"><span data-stu-id="99dac-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="99dac-142">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="99dac-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="99dac-143">如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。</span><span class="sxs-lookup"><span data-stu-id="99dac-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="99dac-144">搭配 `dotnet run -- 5` 試用它以計算到五。</span><span class="sxs-lookup"><span data-stu-id="99dac-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="99dac-145">`--` 之後的任何參數都不會傳遞至 `dotnet run` 命令，而會改為傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="99dac-146">發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="99dac-146">Publish .NET Core app</span></span>

<span data-ttu-id="99dac-147">將 .NET Core 應用程式新增至 Docker 映像之前，請先發佈它。</span><span class="sxs-lookup"><span data-stu-id="99dac-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="99dac-148">建議您確定容器啟動時，會執行已發佈的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="99dac-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="99dac-149">從工作資料夾中，進入含有範例原始程式碼的 **app** 資料夾，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="99dac-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="99dac-150">此命令會將您的應用程式編譯至 **publish** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="99dac-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="99dac-151">從工作資料夾通往 **publish** 資料夾的路徑應該是 `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="99dac-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="99dac-152">取得 publish 資料夾的目錄清單，以確認 **myapp.dll** 已建立。</span><span class="sxs-lookup"><span data-stu-id="99dac-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="99dac-153">從 **app** 資料夾中，執行下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="99dac-153">From the **app** folder, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="99dac-154">建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="99dac-154">Create the Dockerfile</span></span>

<span data-ttu-id="99dac-155">`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="99dac-156">此檔案是名為 *Dockerfile* 且沒有副檔名的純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="99dac-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="99dac-157">在您的終端機中，瀏覽至您一開始時建立的工作資料夾目錄。</span><span class="sxs-lookup"><span data-stu-id="99dac-157">In your terminal, navigate to up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="99dac-158">在工作資料夾中建立名為 *Dockerfile* 的檔案，然後在文字編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="99dac-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="99dac-159">將下列命令新增為檔案的第一行：</span><span class="sxs-lookup"><span data-stu-id="99dac-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
```

<span data-ttu-id="99dac-160">`FROM` 命令會指示 Docker 從 **mcr.microsoft.com/dotnet/core/runtime** 存放庫提取標記為 **2.2** 的映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="99dac-161">確定您所提取的 .NET Core 執行階段符合您 SDK 以其為目標的執行階段。</span><span class="sxs-lookup"><span data-stu-id="99dac-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="99dac-162">例如，上一節中所建立的應用程式會使用 .NET Core 2.2 SDK，並建立目標為 .NET Core 2.2 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99dac-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="99dac-163">因此，*Dockerfile* 中所參考的基底映像會以 **2.2** 來標記。</span><span class="sxs-lookup"><span data-stu-id="99dac-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="99dac-164">儲存 *Dockerfile* 檔案。</span><span class="sxs-lookup"><span data-stu-id="99dac-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="99dac-165">工作資料夾的目錄結構應如下所示。</span><span class="sxs-lookup"><span data-stu-id="99dac-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="99dac-166">部分更下層的檔案和資料夾已省略，以節省文章空間：</span><span class="sxs-lookup"><span data-stu-id="99dac-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```console
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="99dac-167">從終端機中執行 `docker build -t myimage -f Dockerfile .`，而 Docker 將會處理 *Dockerfile* 中的每一行。</span><span class="sxs-lookup"><span data-stu-id="99dac-167">From your terminal, run `docker build -t myimage -f Dockerfile .` and Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="99dac-168">`docker build` 命令中的 `.` 會指示 Docker 使用目前的資料夾尋找 *Dockerfile*。</span><span class="sxs-lookup"><span data-stu-id="99dac-168">The `.` in the `docker build` command tells docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="99dac-169">此命令會建置映像，並建立名為 **myimage** 的本機存放庫以指向該映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="99dac-170">當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：</span><span class="sxs-lookup"><span data-stu-id="99dac-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="99dac-171">請注意，這兩個映像會共用相同的**映像識別碼**值。</span><span class="sxs-lookup"><span data-stu-id="99dac-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="99dac-172">此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。</span><span class="sxs-lookup"><span data-stu-id="99dac-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="99dac-173">讓我們在 *Dockerfile* 中新增兩個命令。</span><span class="sxs-lookup"><span data-stu-id="99dac-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="99dac-174">每個命令都會使用最後一個命令來建立新的映像圖層，其代表 **myimage** 存放庫將指向的映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-174">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="99dac-175">`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="99dac-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="99dac-176">在此範例中，會將 **publish** 資料夾複製到容器中名為 **app** 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="99dac-176">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="99dac-177">下一個命令 `ENTRYPOINT` 會指示 Docker，將容器設定為以可執行檔執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-177">The next command, `ENTRYPOINT`, tells docker to configure the container to run as an executable.</span></span> <span data-ttu-id="99dac-178">當容器啟動時，`ENTRYPOINT` 命令就會執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="99dac-179">當此命令結束時，容器將會自動停止。</span><span class="sxs-lookup"><span data-stu-id="99dac-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="99dac-180">從終端機中執行 `docker build -t myimage -f Dockerfile .`，並在該命令完成時，執行 `docker images`。</span><span class="sxs-lookup"><span data-stu-id="99dac-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest


> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="99dac-181">*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。</span><span class="sxs-lookup"><span data-stu-id="99dac-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="99dac-182">最終的**映像識別碼** (您的映像識別碼將會不同) 為 **ddcc6646461b**，接下來您將根據此映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="99dac-183">建立容器</span><span class="sxs-lookup"><span data-stu-id="99dac-183">Create a container</span></span>

<span data-ttu-id="99dac-184">您現在已有包含應用程式的映像，您可以建立一個容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="99dac-185">您可以兩種方式建立容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-185">You can create a container in two ways.</span></span> <span data-ttu-id="99dac-186">首先，建立已停止的新容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="99dac-187">上述的 `docker create` 命令將根據 **myimage** 映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="99dac-188">該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。</span><span class="sxs-lookup"><span data-stu-id="99dac-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="99dac-189">若要查看「所有」  容器的清單，請使用 `docker ps -a` 命令：</span><span class="sxs-lookup"><span data-stu-id="99dac-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="99dac-190">管理容器</span><span class="sxs-lookup"><span data-stu-id="99dac-190">Manage the container</span></span>

<span data-ttu-id="99dac-191">每個容器會被指派隨機的名稱，可供您用來參考該容器執行個體。</span><span class="sxs-lookup"><span data-stu-id="99dac-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="99dac-192">例如，已自動建立的容器選擇了名稱 **boring_matsumoto** (您的名稱將會不同)，而該名稱可用來啟動容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-192">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="99dac-193">您會使用 `docker create --name` 參數，利用特定的名稱來覆寫自動名稱。</span><span class="sxs-lookup"><span data-stu-id="99dac-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="99dac-194">下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：</span><span class="sxs-lookup"><span data-stu-id="99dac-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="99dac-195">同樣地，`docker stop` 命令將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="99dac-196">下列範例會使用 `docker stop` 命令來停止容器，然後使用 `docker ps` 命令顯示沒有任何容器正在執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="99dac-197">連線到容器</span><span class="sxs-lookup"><span data-stu-id="99dac-197">Connect to a container</span></span>

<span data-ttu-id="99dac-198">當容器正在執行之後，您可以連線到它以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="99dac-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="99dac-199">使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="99dac-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="99dac-200">在此範例中，會使用 <kbd>CTRL + C</kbd> 命令來將執行中的容器中斷連結。</span><span class="sxs-lookup"><span data-stu-id="99dac-200">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="99dac-201">這實際上可能會結束容器中的程序，其將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-201">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="99dac-202">`--sig-proxy=false` 參數可確保 <kbd>CTRL + C</kbd> 不會停止容器中的流程。</span><span class="sxs-lookup"><span data-stu-id="99dac-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="99dac-203">當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。</span><span class="sxs-lookup"><span data-stu-id="99dac-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="99dac-204">刪除容器</span><span class="sxs-lookup"><span data-stu-id="99dac-204">Delete a container</span></span>

<span data-ttu-id="99dac-205">基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。</span><span class="sxs-lookup"><span data-stu-id="99dac-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="99dac-206">刪除您先前建立的容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-206">Delete the container you previously created.</span></span> <span data-ttu-id="99dac-207">如果容器正在執行，請停止它。</span><span class="sxs-lookup"><span data-stu-id="99dac-207">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="99dac-208">下列範例會列出所有容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-208">The following example lists all containers.</span></span> <span data-ttu-id="99dac-209">它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="99dac-210">單一執行</span><span class="sxs-lookup"><span data-stu-id="99dac-210">Single run</span></span>

<span data-ttu-id="99dac-211">Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。</span><span class="sxs-lookup"><span data-stu-id="99dac-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="99dac-212">使用此命令，就不需依序執行 `docker create` 及 `docker start`。</span><span class="sxs-lookup"><span data-stu-id="99dac-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="99dac-213">您也可以設定此命令，在容器停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="99dac-214">例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：</span><span class="sxs-lookup"><span data-stu-id="99dac-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="99dac-215">搭配 `docker run -it`，則 <kbd>CTRL + C</kbd> 命令將會停止正在容器中執行的程序，接著停止容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="99dac-216">由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="99dac-217">確認它不存在：</span><span class="sxs-lookup"><span data-stu-id="99dac-217">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="99dac-218">變更 ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="99dac-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="99dac-219">`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="99dac-220">例如，使用下列命令來執行 `bash` 或 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="99dac-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="99dac-221">視需要編輯命令。</span><span class="sxs-lookup"><span data-stu-id="99dac-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="99dac-222">Windows</span><span class="sxs-lookup"><span data-stu-id="99dac-222">Windows</span></span>
<span data-ttu-id="99dac-223">在此範例中，`ENTRYPOINT` 會變更為 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="99dac-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="99dac-224">按下 <kbd>CTRL + C</kbd> 以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-224"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="99dac-225">Linux</span><span class="sxs-lookup"><span data-stu-id="99dac-225">Linux</span></span>

<span data-ttu-id="99dac-226">在此範例中，`ENTRYPOINT` 會變更為 `bash`。</span><span class="sxs-lookup"><span data-stu-id="99dac-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="99dac-227">執行 `quit` 命令以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="99dac-228">基本命令</span><span class="sxs-lookup"><span data-stu-id="99dac-228">Essential commands</span></span>

<span data-ttu-id="99dac-229">Docker 有許多不同的命令，其中涵蓋您想要使用容器和映像來執行的動作。</span><span class="sxs-lookup"><span data-stu-id="99dac-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="99dac-230">這些 Docker 命令對於管理容器而言非常重要：</span><span class="sxs-lookup"><span data-stu-id="99dac-230">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="99dac-231">docker build</span><span class="sxs-lookup"><span data-stu-id="99dac-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="99dac-232">docker run</span><span class="sxs-lookup"><span data-stu-id="99dac-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="99dac-233">docker ps</span><span class="sxs-lookup"><span data-stu-id="99dac-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="99dac-234">docker stop</span><span class="sxs-lookup"><span data-stu-id="99dac-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="99dac-235">docker rm</span><span class="sxs-lookup"><span data-stu-id="99dac-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="99dac-236">docker rmi</span><span class="sxs-lookup"><span data-stu-id="99dac-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="99dac-237">docker image</span><span class="sxs-lookup"><span data-stu-id="99dac-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="99dac-238">清除資源</span><span class="sxs-lookup"><span data-stu-id="99dac-238">Clean up resources</span></span>

<span data-ttu-id="99dac-239">在此教學課程中，您建立了容器與映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-239">During this tutorial you created containers and images.</span></span> <span data-ttu-id="99dac-240">您可以視需要刪除這些資源。</span><span class="sxs-lookup"><span data-stu-id="99dac-240">If you want, delete these resources.</span></span> <span data-ttu-id="99dac-241">使用下列命令</span><span class="sxs-lookup"><span data-stu-id="99dac-241">Use the following commands to</span></span>

01. <span data-ttu-id="99dac-242">列出所有容器</span><span class="sxs-lookup"><span data-stu-id="99dac-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="99dac-243">停止正在執行的容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-243">Stop containers that are running.</span></span> <span data-ttu-id="99dac-244">`CONTAINER_NAME` 代表自動指派給容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="99dac-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="99dac-245">刪除容器</span><span class="sxs-lookup"><span data-stu-id="99dac-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="99dac-246">接下來，在電腦上刪除您不再需要的任何映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="99dac-247">刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="99dac-248">您可以使用**映像識別碼**或**存放庫:標記**格式的字串。</span><span class="sxs-lookup"><span data-stu-id="99dac-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="99dac-249">使用 `docker images` 命令來查看已安裝的映像清單。</span><span class="sxs-lookup"><span data-stu-id="99dac-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="99dac-250">映像檔可能很大。</span><span class="sxs-lookup"><span data-stu-id="99dac-250">Image files can be large.</span></span> <span data-ttu-id="99dac-251">一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。</span><span class="sxs-lookup"><span data-stu-id="99dac-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="99dac-252">如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。</span><span class="sxs-lookup"><span data-stu-id="99dac-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="99dac-253">後續步驟</span><span class="sxs-lookup"><span data-stu-id="99dac-253">Next steps</span></span>

* <span data-ttu-id="99dac-254">[嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="99dac-254">[Try the ASP.NET Core Microservice Tutorial.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)</span></span>
* [<span data-ttu-id="99dac-255">檢閱支援容器的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="99dac-255">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* <span data-ttu-id="99dac-256">[了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="99dac-256">[Read about Dockerfile commands.](https://docs.docker.com/engine/reference/builder/)</span></span>
* [<span data-ttu-id="99dac-257">探索 Visual Studio 的容器工具</span><span class="sxs-lookup"><span data-stu-id="99dac-257">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
