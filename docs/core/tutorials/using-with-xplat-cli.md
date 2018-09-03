---
title: 從使用 CLI 開始使用 .NET Core
description: 本逐步教學課程說明如何使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.technology: dotnet-cli
ms.openlocfilehash: 5ec7168ebc2ee4fc428d1ab520e986842f111ca7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256761"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="25f54-103">使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="25f54-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="25f54-104">本主題將示範如何使用 .NET Core CLI 工具在電腦上開始開發跨平台應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="25f54-105">如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="25f54-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25f54-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="25f54-106">Prerequisites</span></span>

- <span data-ttu-id="25f54-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="25f54-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="25f54-108">您選擇的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="25f54-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="25f54-109">嗨，主控台應用程式！</span><span class="sxs-lookup"><span data-stu-id="25f54-109">Hello, Console App!</span></span>

<span data-ttu-id="25f54-110">您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。</span><span class="sxs-lookup"><span data-stu-id="25f54-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="25f54-111">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="25f54-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="25f54-112">開啟命令提示字元，並建立名為 *Hello* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="25f54-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="25f54-113">巡覽至您已建立的資料夾，並鍵入下列內容：</span><span class="sxs-lookup"><span data-stu-id="25f54-113">Navigate to the folder you created and type the following:</span></span>

```console
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="25f54-114">讓我們快速逐步解說︰</span><span class="sxs-lookup"><span data-stu-id="25f54-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="25f54-115">[`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。</span><span class="sxs-lookup"><span data-stu-id="25f54-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="25f54-116">它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="25f54-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="25f54-117">`Hello.csproj`：</span><span class="sxs-lookup"><span data-stu-id="25f54-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="25f54-118">專案檔會指定還原相依性和建置程式所需的所有內容。</span><span class="sxs-lookup"><span data-stu-id="25f54-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="25f54-119">`OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="25f54-120">`TargetFramework` 標記會指定做為目標的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="25f54-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="25f54-121">在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。</span><span class="sxs-lookup"><span data-stu-id="25f54-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="25f54-122">在本教學課程中，我們將著重於僅針對 .NET Core 1.0 來建置。</span><span class="sxs-lookup"><span data-stu-id="25f54-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="25f54-123">`Program.cs`：</span><span class="sxs-lookup"><span data-stu-id="25f54-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="25f54-124">程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。</span><span class="sxs-lookup"><span data-stu-id="25f54-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="25f54-125">`System` 命名空間會包含像是 `string` 的基本結構或數字類型。</span><span class="sxs-lookup"><span data-stu-id="25f54-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="25f54-126">然後，我們會定義稱為 `Hello` 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="25f54-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="25f54-127">您可以將其變更為任何所需的位置。</span><span class="sxs-lookup"><span data-stu-id="25f54-127">You can change this to anything you want.</span></span> <span data-ttu-id="25f54-128">名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="25f54-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="25f54-129">這個陣列包含呼叫已編譯的程式時傳入的引數清單。</span><span class="sxs-lookup"><span data-stu-id="25f54-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="25f54-130">事實上，並未使用這個陣列︰所有程式所做的只是將 "Hello World!" 寫入</span><span class="sxs-lookup"><span data-stu-id="25f54-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="25f54-131">到主控台。</span><span class="sxs-lookup"><span data-stu-id="25f54-131">to the console.</span></span> <span data-ttu-id="25f54-132">稍後，我們將變更程式碼以便使用此引數。</span><span class="sxs-lookup"><span data-stu-id="25f54-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="25f54-133">[`dotnet restore`](../tools/dotnet-restore.md) 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="25f54-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="25f54-134">NuGet 會分析 *Hello.csproj* 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 *obj/project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="25f54-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="25f54-135">必須要有 *project.assets.json* 檔案才能夠編譯並執行。</span><span class="sxs-lookup"><span data-stu-id="25f54-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>

   <span data-ttu-id="25f54-136">*project.assets.json* 檔案是一組持續性且完整的 NuGet 相依性圖形，也包含了描述應用程式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="25f54-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="25f54-137">其他工具，例如 [`dotnet build`](../tools/dotnet-build.md) 和 [`dotnet run`](../tools/dotnet-run.md)，會讀取這個檔案，以便它們能用正確的 NuGet 相依性集合與繫結解析，處理原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="25f54-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>

3. `$ dotnet run`

   <span data-ttu-id="25f54-138">[`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="25f54-139">或者，您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="25f54-140">這會產生編譯成 DLL 檔案的應用程式，您可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp1.0\Hello.dll` (在非 Windows 系統上則使用 `/`) 來執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="25f54-141">您也可以指定應用程式的引數，您將於稍後看到該主題。</span><span class="sxs-lookup"><span data-stu-id="25f54-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="25f54-142">在進階案例中，可以建置應用程式做為一組獨立的平台專屬檔案，您可以將其部署到不需安裝 .NET Core 的電腦上並加以執行。</span><span class="sxs-lookup"><span data-stu-id="25f54-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="25f54-143">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="25f54-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="25f54-144">擴充程式</span><span class="sxs-lookup"><span data-stu-id="25f54-144">Augmenting the program</span></span>

<span data-ttu-id="25f54-145">讓我們稍微變更程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-145">Let's change the program a bit.</span></span> <span data-ttu-id="25f54-146">Fibonacci 數字很有趣，因此讓我們也新增該數字，以使用引數來歡迎執行應用程式的人員。</span><span class="sxs-lookup"><span data-stu-id="25f54-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="25f54-147">以下列程式碼取代 *Program.cs* 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="25f54-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="25f54-148">執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。</span><span class="sxs-lookup"><span data-stu-id="25f54-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="25f54-149">執行將參數傳遞至應用程式的程式：</span><span class="sxs-lookup"><span data-stu-id="25f54-149">Run the program passing a parameter to the app:</span></span>

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="25f54-150">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="25f54-150">And that's it!</span></span>  <span data-ttu-id="25f54-151">您可以隨意擴充 `Program.cs`。</span><span class="sxs-lookup"><span data-stu-id="25f54-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="25f54-152">使用多個檔案</span><span class="sxs-lookup"><span data-stu-id="25f54-152">Working with multiple files</span></span>

<span data-ttu-id="25f54-153">單一檔案很適合用於簡單的一次性程式，但如果您要建置更複雜的應用程式，您可能會在專案中使用多個原始程式檔。讓我們從上一個 Fibonacci 範例中快取一些 Fibonacci 值並新增一些遞迴功能，來建置此應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="25f54-154">使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：</span><span class="sxs-lookup"><span data-stu-id="25f54-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="25f54-155">變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="25f54-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="25f54-156">執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。</span><span class="sxs-lookup"><span data-stu-id="25f54-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="25f54-157">藉由執行 [`dotnet run`](../tools/dotnet-run.md) 來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="25f54-158">以下顯示程式輸出：</span><span class="sxs-lookup"><span data-stu-id="25f54-158">The following shows the program output:</span></span>

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="25f54-159">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="25f54-159">And that's it!</span></span> <span data-ttu-id="25f54-160">現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。</span><span class="sxs-lookup"><span data-stu-id="25f54-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="25f54-161">請注意，本教學課程中所示用於執行應用程式的命令和步驟，僅供開發階段期間使用。</span><span class="sxs-lookup"><span data-stu-id="25f54-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="25f54-162">準備好部署應用程式之後，您將需要檢視不同的 .NET Core 應用程式[部署策略](../deploying/index.md)及 [`dotnet publish`](../tools/dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="25f54-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="25f54-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25f54-163">See also</span></span>

* [<span data-ttu-id="25f54-164">使用 .NET Core CLI 工具組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="25f54-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
