---
title: 使用 CLI 開始使用 .NET Core
description: 本逐步教學課程說明如何使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 88e9501a776a026a311c5002674c15acf2324f2b
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868596"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="dcd30-103">使用命令列開始在 Windows/Linux/macOS 上使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="dcd30-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="dcd30-104">本主題將示範如何使用 .NET Core CLI 工具在電腦上開始開發跨平台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="dcd30-105">如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dcd30-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="dcd30-106">Prerequisites</span></span>

- <span data-ttu-id="dcd30-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="dcd30-108">您選擇的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="dcd30-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="dcd30-109">嗨，主控台應用程式！</span><span class="sxs-lookup"><span data-stu-id="dcd30-109">Hello, Console App!</span></span>

<span data-ttu-id="dcd30-110">您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="dcd30-111">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="dcd30-112">開啟命令提示字元，並建立名為 *Hello* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="dcd30-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="dcd30-113">巡覽至您已建立的資料夾，並鍵入下列內容：</span><span class="sxs-lookup"><span data-stu-id="dcd30-113">Navigate to the folder you created and type the following:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="dcd30-114">讓我們快速逐步解說︰</span><span class="sxs-lookup"><span data-stu-id="dcd30-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="dcd30-115">[`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。</span><span class="sxs-lookup"><span data-stu-id="dcd30-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="dcd30-116">它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="dcd30-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="dcd30-117">`Hello.csproj`：</span><span class="sxs-lookup"><span data-stu-id="dcd30-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="dcd30-118">專案檔會指定還原相依性和建置程式所需的所有內容。</span><span class="sxs-lookup"><span data-stu-id="dcd30-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="dcd30-119">`OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="dcd30-120">`TargetFramework` 標記會指定做為目標的 .NET 實作。</span><span class="sxs-lookup"><span data-stu-id="dcd30-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="dcd30-121">在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。</span><span class="sxs-lookup"><span data-stu-id="dcd30-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="dcd30-122">在本教學課程中，我們將著重於僅針對 .NET Core 2.1 來建置。</span><span class="sxs-lookup"><span data-stu-id="dcd30-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="dcd30-123">`Program.cs`：</span><span class="sxs-lookup"><span data-stu-id="dcd30-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="dcd30-124">程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。</span><span class="sxs-lookup"><span data-stu-id="dcd30-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="dcd30-125">`System` 命名空間會包含像是 `string` 的基本結構或數字類型。</span><span class="sxs-lookup"><span data-stu-id="dcd30-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="dcd30-126">然後，我們會定義稱為 `Hello` 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcd30-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="dcd30-127">您可以將其變更為任何所需的位置。</span><span class="sxs-lookup"><span data-stu-id="dcd30-127">You can change this to anything you want.</span></span> <span data-ttu-id="dcd30-128">名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="dcd30-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="dcd30-129">這個陣列包含呼叫已編譯的程式時傳入的引數清單。</span><span class="sxs-lookup"><span data-stu-id="dcd30-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="dcd30-130">事實上，並未使用這個陣列︰所有程式所做的只是將 "Hello World!" 寫入</span><span class="sxs-lookup"><span data-stu-id="dcd30-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="dcd30-131">到主控台。</span><span class="sxs-lookup"><span data-stu-id="dcd30-131">to the console.</span></span> <span data-ttu-id="dcd30-132">稍後，我們將變更程式碼以便使用此引數。</span><span class="sxs-lookup"><span data-stu-id="dcd30-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="dcd30-133">`dotnet new` 會隱含地呼叫 [`dotnet restore`](../tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="dcd30-134">`dotnet restore` 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="dcd30-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="dcd30-135">NuGet 會分析 Hello.csproj  檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 obj/project.assets.json  檔案，該檔案是編譯及執行範例的必要項目。</span><span class="sxs-lookup"><span data-stu-id="dcd30-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="dcd30-136">如果您使用 .NET Core 1.x 版本的 SDK，則必須在呼叫 `dotnet new` 之後自行呼叫 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="dcd30-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="dcd30-137">[`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="dcd30-138">或者，您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="dcd30-139">這會產生編譯成 DLL 檔案的應用程式，您可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp2.1\Hello.dll` (在非 Windows 系統上則使用 `/`) 來執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="dcd30-140">您也可以指定應用程式的引數，您將於稍後看到該主題。</span><span class="sxs-lookup"><span data-stu-id="dcd30-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="dcd30-141">在進階案例中，可以建置應用程式做為一組獨立的平台專屬檔案，您可以將其部署到不需安裝 .NET Core 的電腦上並加以執行。</span><span class="sxs-lookup"><span data-stu-id="dcd30-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="dcd30-142">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="dcd30-143">擴充程式</span><span class="sxs-lookup"><span data-stu-id="dcd30-143">Augmenting the program</span></span>

<span data-ttu-id="dcd30-144">讓我們稍微變更程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-144">Let's change the program a bit.</span></span> <span data-ttu-id="dcd30-145">Fibonacci 數字很有趣，因此讓我們也新增該數字，以使用引數來歡迎執行應用程式的人員。</span><span class="sxs-lookup"><span data-stu-id="dcd30-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="dcd30-146">以下列程式碼取代 *Program.cs* 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="dcd30-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="dcd30-147">執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。</span><span class="sxs-lookup"><span data-stu-id="dcd30-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="dcd30-148">執行將參數傳遞至應用程式的程式：</span><span class="sxs-lookup"><span data-stu-id="dcd30-148">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="dcd30-149">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="dcd30-149">And that's it!</span></span>  <span data-ttu-id="dcd30-150">您可以隨意擴充 `Program.cs`。</span><span class="sxs-lookup"><span data-stu-id="dcd30-150">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="dcd30-151">使用多個檔案</span><span class="sxs-lookup"><span data-stu-id="dcd30-151">Working with multiple files</span></span>

<span data-ttu-id="dcd30-152">單一檔案適用於簡單的一次性程式，但如果您要建置更複雜的應用程式，可能在專案上要具備多個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="dcd30-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="dcd30-153">請藉由快取某些 Fibonacci 值，再新增一些遞迴功能，從先前的 Fibonacci 範例開始建置。</span><span class="sxs-lookup"><span data-stu-id="dcd30-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="dcd30-154">使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：</span><span class="sxs-lookup"><span data-stu-id="dcd30-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="dcd30-155">變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="dcd30-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="dcd30-156">執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。</span><span class="sxs-lookup"><span data-stu-id="dcd30-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="dcd30-157">藉由執行 [`dotnet run`](../tools/dotnet-run.md) 來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="dcd30-158">以下顯示程式輸出：</span><span class="sxs-lookup"><span data-stu-id="dcd30-158">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="dcd30-159">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dcd30-159">Publish your app</span></span>

<span data-ttu-id="dcd30-160">一旦您準備好散發您的應用程式，請使用 [`dotnet publish`](../tools/dotnet-publish.md) 命令在 _bin\\debug\\netcoreapp2.1\\publish\\_ 中產生 _publish_ 資料夾 (針對非 Windows 系統，請使用 `/`)。</span><span class="sxs-lookup"><span data-stu-id="dcd30-160">Once you're ready to distribute your app, use the [`dotnet publish`](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp2.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="dcd30-161">您可以將 _publish_  資料夾的內容散發到其他平台，只要那些平台已安裝 dotnet 執行階段。</span><span class="sxs-lookup"><span data-stu-id="dcd30-161">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

<span data-ttu-id="dcd30-162">您可以使用 [dotnet](../tools/dotnet.md) 命令來執行已發佈的應用程式：</span><span class="sxs-lookup"><span data-stu-id="dcd30-162">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="dcd30-163">結論</span><span class="sxs-lookup"><span data-stu-id="dcd30-163">Conclusion</span></span>

<span data-ttu-id="dcd30-164">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="dcd30-164">And that's it!</span></span> <span data-ttu-id="dcd30-165">現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。</span><span class="sxs-lookup"><span data-stu-id="dcd30-165">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd30-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcd30-166">See also</span></span>

- [<span data-ttu-id="dcd30-167">使用 .NET Core CLI 工具組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="dcd30-167">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="dcd30-168">使用 CLI 發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="dcd30-168">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="dcd30-169">深入了解應用程式部署</span><span class="sxs-lookup"><span data-stu-id="dcd30-169">Learn more about app deployment</span></span>](../deploying/index.md)
