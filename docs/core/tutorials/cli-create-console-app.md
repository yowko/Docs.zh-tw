---
title: 使用 CLI 開始使用 .NET Core
description: 一個分步教程，演示如何使用 .NET Core CLI 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240853"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="a3bdd-103">使用 .NET 核心 CLI 開始使用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="a3bdd-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="a3bdd-104">本文將介紹如何使用 .NET Core CLI 開始開發在 Windows、Linux 和 macOS 上工作的 .NET 核心應用。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="a3bdd-105">如果您不熟悉 .NET 核心 CLI，請參閱[.NET 核心 CLI 概述](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3bdd-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="a3bdd-106">Prerequisites</span></span>

- <span data-ttu-id="a3bdd-107">[.NET 核心 SDK 3.1](https://dotnet.microsoft.com/download)或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="a3bdd-108">您偏好的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="a3bdd-109">嗨，主控台應用程式！</span><span class="sxs-lookup"><span data-stu-id="a3bdd-109">Hello, Console App!</span></span>

<span data-ttu-id="a3bdd-110">您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="a3bdd-111">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="a3bdd-112">開啟命令提示字元，並建立名為 *Hello* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="a3bdd-113">導航到您創建的資料夾並鍵入以下內容。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="a3bdd-114">讓我們快速逐步解說︰</span><span class="sxs-lookup"><span data-stu-id="a3bdd-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="a3bdd-115">[dotnet new](../tools/dotnet-new.md)創建最新的*Hello.csproj*專案檔案，該檔具有構建主控台應用所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="a3bdd-116">它還創建一個*Program.cs，* 一個基本檔，包含應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="a3bdd-117">*你好.csproj*：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="a3bdd-118">專案檔會指定還原相依性和建置程式所需的所有內容。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="a3bdd-119">該`<OutputType>`元素指定我們正在構建一個可執行檔，換句話說是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="a3bdd-120">該`<TargetFramework>`元素指定我們針對的 .NET 實現。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="a3bdd-121">在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="a3bdd-122">在本教程中，我們將堅持僅為 .NET Core 3.1 構建。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="a3bdd-123">*Program.cs*：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="a3bdd-124">程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="a3bdd-125">命名`System`空間包括類`Console`。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="a3bdd-126">然後，我們會定義稱為 `Hello` 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="a3bdd-127">您可以將其變更為任何所需的位置。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-127">You can change this to anything you want.</span></span> <span data-ttu-id="a3bdd-128">命名的`Program`類在命名空間中定義，`Main`該方法採用名為 的`args`字串陣列。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="a3bdd-129">此陣列包含運行程式時傳入的參數清單。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="a3bdd-130">因為它是，這個陣列不使用，程式只是寫文本"你好世界！</span><span class="sxs-lookup"><span data-stu-id="a3bdd-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="a3bdd-131">到主控台。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-131">to the console.</span></span> <span data-ttu-id="a3bdd-132">稍後，我們將變更程式碼以便使用此引數。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="a3bdd-133">`dotnet new`調用[點網](../tools/dotnet-restore.md)隱式還原。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="a3bdd-134">`dotnet restore` 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="a3bdd-135">NuGet 會分析 Hello.csproj\*\* 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 obj/project.assets.json\*\* 檔案，該檔案是編譯及執行範例的必要項目。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="a3bdd-136">[dotnet 運行](../tools/dotnet-run.md)調用[dotnet 生成](../tools/dotnet-build.md)以確保生成目標已生成，然後調用`dotnet <assembly.dll>`以運行目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="a3bdd-137">您將獲得以下輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="a3bdd-138">或者，您也可以運行`dotnet build`以編譯代碼，而無需運行生成主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="a3bdd-139">這將導致基於專案名稱的編譯應用程式（作為 DLL 檔）。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="a3bdd-140">在這種情況下，創建的檔案名為*Hello.dll*。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="a3bdd-141">此應用可以在 Windows`dotnet bin\Debug\netcoreapp3.1\Hello.dll`上運行（用於`/`非 Windows 系統）。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="a3bdd-142">您將獲得以下輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="a3bdd-143">編譯應用時，將和 創建`Hello.dll`特定于作業系統的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="a3bdd-144">在 Windows 上，`Hello.exe`這將是 ;在Linux或macOS上，這將是`hello`。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="a3bdd-145">使用上面的示例，檔案名為`Hello.exe`或`Hello`。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="a3bdd-146">您可以直接運行該可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="a3bdd-147">修改程式</span><span class="sxs-lookup"><span data-stu-id="a3bdd-147">Modify the program</span></span>

<span data-ttu-id="a3bdd-148">讓我們稍微變更程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-148">Let's change the program a bit.</span></span> <span data-ttu-id="a3bdd-149">斐波那契數位很有趣，所以讓我們添加，也使用參數來問候運行應用程式的人。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="a3bdd-150">以下列程式碼取代 *Program.cs* 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="a3bdd-151">運行[點網生成](../tools/dotnet-build.md)以編譯更改。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="a3bdd-152">運行將參數傳遞給應用的程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="a3bdd-153">使用 命令`dotnet`運行應用時，將添加到`--`末尾。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="a3bdd-154">右側的任何內容`--`都將作為參數傳遞給應用。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="a3bdd-155">在下面的示例中，該值`John`將傳遞給應用。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="a3bdd-156">您將獲得以下輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-156">You get the following output.</span></span>

    ```console
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

<span data-ttu-id="a3bdd-157">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="a3bdd-157">And that's it!</span></span> <span data-ttu-id="a3bdd-158">您可以修改*Program.cs*任何你喜歡的方式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="a3bdd-159">使用多個檔案</span><span class="sxs-lookup"><span data-stu-id="a3bdd-159">Working with multiple files</span></span>

<span data-ttu-id="a3bdd-160">單個檔對於簡單的一次性程式是可以的，但如果您要構建一個更複雜的應用程式，則專案上可能會有多個代碼檔。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="a3bdd-161">請藉由快取某些 Fibonacci 值，再新增一些遞迴功能，從先前的 Fibonacci 範例開始建置。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="a3bdd-162">使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="a3bdd-163">變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="a3bdd-164">運行[點網生成](../tools/dotnet-build.md)以編譯更改。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="a3bdd-165">通過執行[點網運行](../tools/dotnet-run.md)來運行你的應用。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="a3bdd-166">您將獲得以下輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-166">You get the following output.</span></span>

    ```console
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

## <a name="publish-your-app"></a><span data-ttu-id="a3bdd-167">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a3bdd-167">Publish your app</span></span>

<span data-ttu-id="a3bdd-168">準備好分發應用後，請使用[dotnet 發佈](../tools/dotnet-publish.md)命令在_bin\\調試\\netcoreapp3.1\\發佈\\_（用於`/`非 Windows 系統）生成_發佈_資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="a3bdd-169">您可以將 _publish_  資料夾的內容散發到其他平台，只要那些平台已安裝 dotnet 執行階段。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="a3bdd-170">您將獲得類似于以下內容的輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="a3bdd-171">上述輸出可能因當前資料夾和作業系統而異，但輸出應類似。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="a3bdd-172">您可以使用 [dotnet](../tools/dotnet.md) 命令來執行已發佈的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a3bdd-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="a3bdd-173">您將獲得以下輸出。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="a3bdd-174">如本文開頭所述，與`Hello.dll`創建作業系統特定的可執行檔一起創建。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="a3bdd-175">在 Windows 上，`Hello.exe`這將是 ;在Linux或macOS上，這將是`hello`。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="a3bdd-176">使用上面的示例，檔案名為`Hello.exe`或`Hello`。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="a3bdd-177">您可以直接運行此已發佈的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="a3bdd-178">結論</span><span class="sxs-lookup"><span data-stu-id="a3bdd-178">Conclusion</span></span>

<span data-ttu-id="a3bdd-179">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="a3bdd-179">And that's it!</span></span> <span data-ttu-id="a3bdd-180">現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。</span><span class="sxs-lookup"><span data-stu-id="a3bdd-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3bdd-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3bdd-181">See also</span></span>

- [<span data-ttu-id="a3bdd-182">使用 .NET 核心 CLI 組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="a3bdd-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="a3bdd-183">使用 .NET 核心 CLI 發佈 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="a3bdd-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="a3bdd-184">.NET 核心應用程式部署</span><span class="sxs-lookup"><span data-stu-id="a3bdd-184">.NET Core application deployment</span></span>](../deploying/index.md)
