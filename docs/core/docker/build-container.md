---
title: 使用 Docker 教學課程將應用程式容器化
description: 在此教學課程中，您將了解如何使用 Docker 來將 .NET Core 應用程式容器化。
ms.date: 04/10/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: fcbac0e0d17d2481d42e715a7f2790586e31d085
ms.sourcegitcommit: 8080271c246b57f4fb68c28369634bff46843424
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59553832"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="fdbeb-103">教學課程：將 .NET Core 應用程式容器化</span><span class="sxs-lookup"><span data-stu-id="fdbeb-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="fdbeb-104">此教學課程將教您如何建置包含 .NET Core 應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="fdbeb-105">映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="fdbeb-106">您將了解：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="fdbeb-107">建立及發佈簡單的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="fdbeb-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="fdbeb-108">建立及設定適用於 .NET Core 的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="fdbeb-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="fdbeb-109">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="fdbeb-109">Build a Docker image</span></span>
> * <span data-ttu-id="fdbeb-110">建立及執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-110">Create and run a Docker container</span></span>

<span data-ttu-id="fdbeb-111">您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="fdbeb-112">「Docker 平台」會使用「Docker 引擎」快速建置應用程式，並將其封裝為「Docker 映像」。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="fdbeb-113">這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdbeb-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="fdbeb-114">Prerequisites</span></span>

<span data-ttu-id="fdbeb-115">安裝下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-115">Install the following prerequisites:</span></span>

- <span data-ttu-id="fdbeb-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)\\</span><span class="sxs-lookup"><span data-stu-id="fdbeb-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)\\</span></span>
<span data-ttu-id="fdbeb-117">如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="fdbeb-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="fdbeb-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="fdbeb-119">適用於 *Dockerfile* 和 .NET Core 範例應用程式的暫存工作目錄。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-119">A temporary working directory for the *Dockerfile* and .NET Core example app.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="fdbeb-120">使用 SDK 版本 2.2</span><span class="sxs-lookup"><span data-stu-id="fdbeb-120">Use SDK version 2.2</span></span>

<span data-ttu-id="fdbeb-121">如果您使用較新的 SDK (例如 3.0)，請務必強制您的應用程式使用 2.2 SDK。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-121">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="fdbeb-122">在您的工作目錄中建立名為 `global.json` 的檔案，並貼上下列 json 程式碼：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-122">Create a file named `global.json` in your working directory and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="fdbeb-123">儲存此檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-123">Save this file.</span></span> <span data-ttu-id="fdbeb-124">檔案的存在將強制 .NET Core 針對從此目錄及以下目錄呼叫的任何 `dotnet` 命令使用版本 2.2。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-124">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this directory and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="fdbeb-125">建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="fdbeb-125">Create .NET Core app</span></span>

<span data-ttu-id="fdbeb-126">您需要 Docker 容器將執行的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-126">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="fdbeb-127">開啟終端機、建立工作目錄，然後進入該目錄。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-127">Open your terminal, create a working directory, and enter it.</span></span> <span data-ttu-id="fdbeb-128">在工作目錄中執行下列命令，在名為 app 的子目錄中建立新專案：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-128">In the working directory, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="fdbeb-129">該命令會建立一個名為 *app* 的新目錄，並產生 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-129">That command creates a new directory named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="fdbeb-130">您可以測試此應用程式以查看其用途。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-130">You can test this app to see what it does.</span></span> <span data-ttu-id="fdbeb-131">進入 *app* 目錄，然後執行 `dotnet run` 命令。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-131">Enter the *app* directory and execute the command `dotnet run`.</span></span> <span data-ttu-id="fdbeb-132">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-132">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="fdbeb-133">預設範本所建立的應用程式會列印到終端機，然後結束。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-133">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="fdbeb-134">針對此教學課程，您將使用無限期執行迴圈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="fdbeb-135">在文字編輯器中開啟 **Program.cs** 檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-135">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="fdbeb-136">它目前看起來應該像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-136">It should currently look like the following code:</span></span>

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

<span data-ttu-id="fdbeb-137">使用下列每秒計算數字的程式碼來取代檔案：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-137">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="fdbeb-138">儲存檔案，然後使用 `dotnet run` 再次測試程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-138">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="fdbeb-139">請記住此應用程式會無限期執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-139">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="fdbeb-140">使用取消命令 <kbd>CTRL + C</kbd> 來停止它。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-140">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="fdbeb-141">您將會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-141">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="fdbeb-142">如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-142">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="fdbeb-143">搭配 `dotnet run -- 5` 試用它以計算到五。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-143">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="fdbeb-144">任何在 `--` 之後的參數都會傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-144">Any parameters after `--` are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="fdbeb-145">發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="fdbeb-145">Publish .NET Core app</span></span>

<span data-ttu-id="fdbeb-146">將 .NET Core 應用程式新增至 Docker 映像之前，請先發佈它。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-146">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="fdbeb-147">容器將在啟動時執行已發佈的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-147">The container will execute the published version of the app when it's started.</span></span>

<span data-ttu-id="fdbeb-148">從工作目錄中，進入含有範例原始程式碼的 **app** 目錄，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-148">From the working directory, enter the **app** directory with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="fdbeb-149">此命令會將應用程式編譯至應用程式輸出資料夾中的 **publish** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-149">This command compiles your app to the **publish** folder in the output folder of your app.</span></span> <span data-ttu-id="fdbeb-150">從工作目錄通往 **publish** 資料夾的路徑應該是 `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="fdbeb-150">The path to the **publish** folder from the working directory should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="fdbeb-151">取得 publish 資料夾的目錄清單，以確認 **myapp.dll** 已建立。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-151">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="fdbeb-152">從 **app** 目錄中，執行下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-152">From the **app** directory, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\path-to-working-dir\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/path-to-working-dir/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

<span data-ttu-id="fdbeb-153">在終端機中，將目錄往上切換到工作目錄。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-153">In your terminal, go up a directory to the working directory.</span></span>

## <a name="create-the-dockerfile"></a><span data-ttu-id="fdbeb-154">建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="fdbeb-154">Create the Dockerfile</span></span>

<span data-ttu-id="fdbeb-155">`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="fdbeb-156">此檔案是名為 *Dockerfile* 且沒有副檔名的純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span> <span data-ttu-id="fdbeb-157">在工作目錄中建立名為 *Dockerfile* 的檔案，然後在文字編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-157">Create a file named *Dockerfile* in your working directory and open it in a text editor.</span></span> <span data-ttu-id="fdbeb-158">將下列命令新增為檔案的第一行：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-158">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="fdbeb-159">`FROM` 命令會指示 Docker 從 **mcr.microsoft.com/dotnet/core/runtime** 存放庫提取標記為 **2.2** 的映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-159">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="fdbeb-160">確定您所提取的 .NET Core 執行階段符合您 SDK 以其為目標的執行階段。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-160">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="fdbeb-161">例如，上一節中所建立的應用程式會使用 .NET Core 2.2 SDK，並建立目標為 .NET Core 2.2 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-161">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="fdbeb-162">因此，*Dockerfile* 中所參考的基底映像會以 **2.2** 來標記。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-162">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="fdbeb-163">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-163">Save the file.</span></span> <span data-ttu-id="fdbeb-164">從終端機中執行 `docker build -t myimage .`，而 Docker 將會處理 *Dockerfile* 中的每一行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-164">From your terminal, run `docker build -t myimage .` and Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="fdbeb-165">`docker build` 命令中的 `.` 會指示 Docker 使用目前的目錄來尋找 *Dockerfile*。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-165">The `.` in the `docker build` command tells docker to use the current directory to find a *Dockerfile*.</span></span> <span data-ttu-id="fdbeb-166">此命令會建置映像，並建立名為 **myimage** 的本機存放庫以指向該映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-166">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="fdbeb-167">當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-167">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="fdbeb-168">請注意，這兩個映像會共用相同的**映像識別碼**值。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-168">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="fdbeb-169">此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-169">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="fdbeb-170">讓我們在 *Dockerfile* 中新增兩個命令。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-170">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="fdbeb-171">每個命令都會使用最後一個命令來建立新的映像圖層，其代表 **myimage** 存放庫將指向的映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-171">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="fdbeb-172">`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-172">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="fdbeb-173">在此範例中，會將 **publish** 資料夾複製到容器中名為 **app** 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-173">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="fdbeb-174">下一個命令 `ENTRYPOINT` 會指示 Docker，將容器設定為以可執行檔執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-174">The next command, `ENTRYPOINT`, tells docker to configure the container to run as an executable.</span></span> <span data-ttu-id="fdbeb-175">當容器啟動時，`ENTRYPOINT` 命令就會執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-175">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="fdbeb-176">當此命令結束時，容器將會自動停止。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-176">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="fdbeb-177">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-177">Save the file.</span></span> <span data-ttu-id="fdbeb-178">從終端機中執行 `docker build -t myimage .`，並在該命令完成時，執行 `docker images`。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-178">From your terminal, run `docker build -t myimage .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage .
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

<span data-ttu-id="fdbeb-179">*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-179">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="fdbeb-180">最終的**映像識別碼** (您的映像識別碼將會不同) 為 **ddcc6646461b**，接下來您將根據此映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-180">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="fdbeb-181">建立容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-181">Create a container</span></span>

<span data-ttu-id="fdbeb-182">您現在已有包含應用程式的映像，您可以建立一個容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-182">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="fdbeb-183">您可以兩種方式建立容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-183">You can create a container in two ways.</span></span> <span data-ttu-id="fdbeb-184">首先，建立已停止的新容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-184">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="fdbeb-185">上述的 `docker create` 命令將根據 **myimage** 映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-185">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="fdbeb-186">該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-186">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="fdbeb-187">若要查看「所有」容器的清單，請使用 `docker ps -a` 命令：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-187">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="fdbeb-188">管理容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-188">Manage the container</span></span>

<span data-ttu-id="fdbeb-189">每個容器會被指派隨機的名稱，可供您用來參考該容器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-189">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="fdbeb-190">例如，已自動建立的容器選擇了名稱 **boring_matsumoto** (您的名稱將會不同)，而該名稱可用來啟動容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-190">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="fdbeb-191">您會使用 `docker create --name` 參數，利用特定的名稱來覆寫自動名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-191">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="fdbeb-192">下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-192">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="fdbeb-193">同樣地，`docker stop` 命令將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-193">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="fdbeb-194">下列範例會使用 `docker stop` 命令來停止容器，然後使用 `docker ps` 命令顯示沒有任何容器正在執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-194">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="fdbeb-195">連線到容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-195">Connect to a container</span></span>

<span data-ttu-id="fdbeb-196">當容器正在執行之後，您可以連線到它以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-196">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="fdbeb-197">使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-197">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="fdbeb-198">在此範例中，會使用 <kbd>CTRL + C</kbd> 命令來將執行中的容器中斷連結。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-198">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="fdbeb-199">這實際上可能會結束容器中的程序，其將會停止容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-199">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="fdbeb-200">`--sig-proxy=false` 參數可確保 <kbd>CTRL + C</kbd> 將不會停止容器中的流程。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-200">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="fdbeb-201">當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-201">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="fdbeb-202">刪除容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-202">Delete a container</span></span>

<span data-ttu-id="fdbeb-203">基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-203">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="fdbeb-204">刪除您先前建立的容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-204">Delete the container you previously created.</span></span> <span data-ttu-id="fdbeb-205">如果容器正在執行，請停止它。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-205">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="fdbeb-206">下列範例會列出所有容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-206">The following example lists all containers.</span></span> <span data-ttu-id="fdbeb-207">它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-207">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="fdbeb-208">單一執行</span><span class="sxs-lookup"><span data-stu-id="fdbeb-208">Single run</span></span>

<span data-ttu-id="fdbeb-209">Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-209">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="fdbeb-210">使用此命令，就不需依序執行 `docker create` 及 `docker start`。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-210">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="fdbeb-211">您也可以設定此命令，在容器停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-211">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="fdbeb-212">例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-212">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="fdbeb-213">搭配 `docker run -it`，則 <kbd>CTRL + C</kbd> 命令將會停止正在容器中執行的程序，接著停止容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-213">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="fdbeb-214">由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-214">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="fdbeb-215">確認它不存在：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-215">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="fdbeb-216">變更 ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="fdbeb-216">Change the ENTRYPOINT</span></span>

<span data-ttu-id="fdbeb-217">`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-217">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="fdbeb-218">例如，使用下列命令來執行 `bash` 或 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-218">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="fdbeb-219">視需要編輯命令。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-219">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="fdbeb-220">Windows</span><span class="sxs-lookup"><span data-stu-id="fdbeb-220">Windows</span></span>
<span data-ttu-id="fdbeb-221">在此範例中，會將 `ENTRYPOINT` 變更為 `cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-221">In this example the `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="fdbeb-222">按下 <kbd>CTRL + C</kbd> 以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-222"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="fdbeb-223">Linux</span><span class="sxs-lookup"><span data-stu-id="fdbeb-223">Linux</span></span>

<span data-ttu-id="fdbeb-224">在此範例中，會將 `ENTRYPOINT` 變更為 `bash`。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-224">In this example the `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="fdbeb-225">執行 `quit` 命令以結束程序並停止容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-225">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="fdbeb-226">基本命令</span><span class="sxs-lookup"><span data-stu-id="fdbeb-226">Essential commands</span></span>

<span data-ttu-id="fdbeb-227">Docker 有許多不同的命令，其中涵蓋您想要使用容器和映像來執行的動作。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-227">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="fdbeb-228">這些 Docker 命令對於管理容器而言非常重要：</span><span class="sxs-lookup"><span data-stu-id="fdbeb-228">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="fdbeb-229">docker build</span><span class="sxs-lookup"><span data-stu-id="fdbeb-229">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="fdbeb-230">docker run</span><span class="sxs-lookup"><span data-stu-id="fdbeb-230">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="fdbeb-231">docker ps</span><span class="sxs-lookup"><span data-stu-id="fdbeb-231">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="fdbeb-232">docker stop</span><span class="sxs-lookup"><span data-stu-id="fdbeb-232">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="fdbeb-233">docker rm</span><span class="sxs-lookup"><span data-stu-id="fdbeb-233">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="fdbeb-234">docker rmi</span><span class="sxs-lookup"><span data-stu-id="fdbeb-234">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="fdbeb-235">docker image</span><span class="sxs-lookup"><span data-stu-id="fdbeb-235">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="fdbeb-236">清除資源</span><span class="sxs-lookup"><span data-stu-id="fdbeb-236">Clean up resources</span></span>

<span data-ttu-id="fdbeb-237">在此教學課程中，您建立了容器與映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-237">During this tutorial you created containers and images.</span></span> <span data-ttu-id="fdbeb-238">您可以視需要刪除這些資源。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-238">If you want, delete these resources.</span></span> <span data-ttu-id="fdbeb-239">使用下列命令</span><span class="sxs-lookup"><span data-stu-id="fdbeb-239">Use the following commands to</span></span>

01. <span data-ttu-id="fdbeb-240">列出所有容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-240">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="fdbeb-241">停止正在執行的容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-241">Stop containers that are running.</span></span> <span data-ttu-id="fdbeb-242">`CONTAINER_NAME` 代表自動指派給容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-242">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="fdbeb-243">刪除容器</span><span class="sxs-lookup"><span data-stu-id="fdbeb-243">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="fdbeb-244">接下來，在電腦上刪除您不再需要的任何映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-244">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="fdbeb-245">刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-245">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="fdbeb-246">您可以使用**映像識別碼**或**存放庫:標記**格式的字串。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-246">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="fdbeb-247">使用 `docker images` 命令來查看已安裝的映像清單。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-247">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="fdbeb-248">映像檔可能很大。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-248">Image files can be large.</span></span> <span data-ttu-id="fdbeb-249">一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-249">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="fdbeb-250">如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-250">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdbeb-251">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fdbeb-251">Next steps</span></span>

* <span data-ttu-id="fdbeb-252">[嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="fdbeb-252">[Try the ASP.NET Core Microservice Tutorial.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)</span></span>
* [<span data-ttu-id="fdbeb-253">檢閱支援容器的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="fdbeb-253">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/en-us/overview/containers/)
* <span data-ttu-id="fdbeb-254">[了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="fdbeb-254">[Read about Dockerfile commands.](https://docs.docker.com/engine/reference/builder/)</span></span>
