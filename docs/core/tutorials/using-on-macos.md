---
title: 教程：使用視覺化工作室代碼在 macOS 中創建 .NET 核心解決方案
description: 本文件提供使用 Visual Studio Code 建立 .NET Core 方案的步驟及工作流程。
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156591"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="a1705-103">教程：使用視覺化工作室代碼在 macOS 中創建 .NET 核心解決方案</span><span class="sxs-lookup"><span data-stu-id="a1705-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="a1705-104">本文件提供建立適用於 macOS 之 .NET Core 方案的步驟及工作流程。</span><span class="sxs-lookup"><span data-stu-id="a1705-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="a1705-105">了解如何建立專案、建立單元測試、使用偵錯工具，以及透過 [NuGet](https://www.nuget.org/) 納入協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="a1705-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="a1705-106">這篇文章會在 macOS 上使用 [Visual Studio Code](https://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="a1705-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1705-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="a1705-107">Prerequisites</span></span>

<span data-ttu-id="a1705-108">安裝[.NET 核心 SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="a1705-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="a1705-109">.NET Core SDK 包含 .NET Core 架構和執行階段的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a1705-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="a1705-110">安裝[視覺化工作室代碼](https://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="a1705-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="a1705-111">在這篇文章的過程中，您也將安裝能改善 .NET Core 開發體驗的 Visual Studio Code 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a1705-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="a1705-112">通過打開視覺化工作室代碼並按<kbd>Fn</kbd>+<kbd>F1</kbd>打開視覺化工作室代碼調色板，安裝視覺化工作室代碼 C# 擴展。</span><span class="sxs-lookup"><span data-stu-id="a1705-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>Fn</kbd>+<kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="a1705-113">鍵入 **ext install** 來查看延伸模組的清單。</span><span class="sxs-lookup"><span data-stu-id="a1705-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="a1705-114">選取 C# 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a1705-114">Select the C# extension.</span></span> <span data-ttu-id="a1705-115">重新啟動 Visual Studio Code 以啟動延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a1705-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="a1705-116">如需詳細資訊，請參閱 [Visual Studio Code C# 延伸模組文件](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)。</span><span class="sxs-lookup"><span data-stu-id="a1705-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="a1705-117">開始使用</span><span class="sxs-lookup"><span data-stu-id="a1705-117">Get started</span></span>

<span data-ttu-id="a1705-118">在本教學課程中，您會建立三個專案︰程式庫專案、該程式庫專案的測試，以及利用程式庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1705-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="a1705-119">您可以在 GitHub 上的 dotnet/示例存儲庫[中查看或下載](https://github.com/dotnet/samples/tree/master/core/getting-started/golden)本文的源。</span><span class="sxs-lookup"><span data-stu-id="a1705-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this article at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="a1705-120">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="a1705-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="a1705-121">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="a1705-121">Start Visual Studio Code.</span></span> <span data-ttu-id="a1705-122">按<kbd>Ctrl（</kbd><kbd>\`</kbd>回引或回勾符）或從功能表中選擇 **"查看** > **終端**"以在 Visual Studio 代碼中打開嵌入式終端。</span><span class="sxs-lookup"><span data-stu-id="a1705-122">Press <kbd>Ctrl</kbd><kbd>\`</kbd> (the backquote or backtick character) or select **View** > **Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="a1705-123">如果您更喜歡在 Visual Studio 代碼之外工作，您仍可以使用"資源管理器**在命令提示符"命令提示符中打開**外部外殼（在 macOS 或 Linux 上的**終端中打開**）。</span><span class="sxs-lookup"><span data-stu-id="a1705-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on macOS or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="a1705-124">請從建立方案檔開始，而方案檔是作為一或多個 .NET Core 專案的容器。</span><span class="sxs-lookup"><span data-stu-id="a1705-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="a1705-125">在終端中，運行[`dotnet new`](../tools/dotnet-new.md)命令以在名為 Golden 的新資料夾中創建新的解決方案*golden.sln* ： *golden*</span><span class="sxs-lookup"><span data-stu-id="a1705-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="a1705-126">導航到新的*金資料夾*並執行以下命令以創建庫專案，該專案將在*庫*資料夾中生成兩個檔，*庫.csproj*和*Class1.cs：*</span><span class="sxs-lookup"><span data-stu-id="a1705-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="a1705-127">執行將[`dotnet sln`](../tools/dotnet-sln.md)新創建的*庫.csproj*專案添加到解決方案的命令：</span><span class="sxs-lookup"><span data-stu-id="a1705-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="a1705-128">*library.csproj* 檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="a1705-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a1705-129">我們的程式庫方法會序列化及還原序列化 JSON 格式的物件。</span><span class="sxs-lookup"><span data-stu-id="a1705-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="a1705-130">若要支援 JSON 序列化及還原序列化，請新增 `Newtonsoft.Json` NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="a1705-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="a1705-131">`dotnet add` 命令會新增項目至專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="a1705-132">要添加對 NuGet 包的引用，請使用[`dotnet add package`](../tools/dotnet-add-package.md)命令並指定包的名稱：</span><span class="sxs-lookup"><span data-stu-id="a1705-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="a1705-133">這會將 `Newtonsoft.Json` 及其相依性新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="a1705-134">或者，手動編輯 *library.csproj* 檔案，並新增下列節點：</span><span class="sxs-lookup"><span data-stu-id="a1705-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="a1705-135">執行[`dotnet restore`](../tools/dotnet-restore.md)（[參見 注釋](#dotnet-restore-note)）， 它還原依賴項並在*庫*內創建一個*obj*資料夾，其中包含三個檔，包括*project.assets.json*檔：</span><span class="sxs-lookup"><span data-stu-id="a1705-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="a1705-136">在 *library* 資料夾中，將檔案 *Class1.cs* 重新命名為 *Thing.cs*。</span><span class="sxs-lookup"><span data-stu-id="a1705-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="a1705-137">使用下列程式碼來取代此程式碼：</span><span class="sxs-lookup"><span data-stu-id="a1705-137">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="a1705-138">`Thing` 類別包含一個公用方法 `Get`，這個公用方法會傳回兩個數字的總和，而做法是將總和轉換成字串，然後將它還原序列化為整數。</span><span class="sxs-lookup"><span data-stu-id="a1705-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="a1705-139">這利用了許多現代 C# 功能，如[`using static`指令](../../csharp/language-reference/keywords/using-static.md)、[運算式體成員](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)和[字串插值](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="a1705-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="a1705-140">使用 命令[`dotnet build`](../tools/dotnet-build.md)生成庫。</span><span class="sxs-lookup"><span data-stu-id="a1705-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="a1705-141">這會在 *golden/library/bin/Debug/netstandard1.4* 底下產生 *library.dll* 檔案：</span><span class="sxs-lookup"><span data-stu-id="a1705-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="a1705-142">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="a1705-142">Create the test project</span></span>

<span data-ttu-id="a1705-143">建置程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-143">Build a test project for the library.</span></span> <span data-ttu-id="a1705-144">從 *golden* 資料夾中，建立新的測試專案︰</span><span class="sxs-lookup"><span data-stu-id="a1705-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="a1705-145">將測試專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="a1705-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="a1705-146">新增上一節中所建立之程式碼的專案參考，讓編譯器可以尋找及使用程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="a1705-147">使用以下[`dotnet add reference`](../tools/dotnet-add-reference.md)命令：</span><span class="sxs-lookup"><span data-stu-id="a1705-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="a1705-148">或者，手動編輯 *test-library.csproj* 檔案，並新增下列節點：</span><span class="sxs-lookup"><span data-stu-id="a1705-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="a1705-149">既然已正確設定相依性，請建立您程式庫的測試。</span><span class="sxs-lookup"><span data-stu-id="a1705-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="a1705-150">開啟 *UnitTest1.cs* 並將其內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a1705-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="a1705-151">請注意，當您第一次建立單元測試時，確認值 42 不等於 19+23 (或 42) (`Assert.NotEqual`)，而這項建立作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="a1705-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="a1705-152">建置單元測試的重要步驟是建立測試，以確認其邏輯在第一次時失敗一次。</span><span class="sxs-lookup"><span data-stu-id="a1705-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="a1705-153">從 *golden* 資料夾中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1705-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="a1705-154">這些命令會以遞迴方式尋找所有專案來還原相依性、建置相依性，並啟動 xUnit 測試執行器來執行測試。</span><span class="sxs-lookup"><span data-stu-id="a1705-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="a1705-155">如您所預期，單一測試失敗。</span><span class="sxs-lookup"><span data-stu-id="a1705-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="a1705-156">編輯 *UnitTest1.cs* 檔案，並將判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`。</span><span class="sxs-lookup"><span data-stu-id="a1705-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="a1705-157">從 *golden* 資料夾中執行下列命令，以重新執行測試，而這次測試會通過：</span><span class="sxs-lookup"><span data-stu-id="a1705-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="a1705-158">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a1705-158">Create the console app</span></span>

<span data-ttu-id="a1705-159">您透過下列步驟所建立的主控台應用程式依存於您先前建立的程式庫專案，並在它執行時呼叫它的程式庫方法。</span><span class="sxs-lookup"><span data-stu-id="a1705-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="a1705-160">使用這種模式的開發，您會看到如何建立多個專案的可重複使用程式庫。</span><span class="sxs-lookup"><span data-stu-id="a1705-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="a1705-161">從 *golden* 資料夾中，建立新的主控台應用程式︰</span><span class="sxs-lookup"><span data-stu-id="a1705-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="a1705-162">將主控台應用程式專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="a1705-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="a1705-163">執行 `dotnet add reference` 命令，建立與程式庫的相依性︰</span><span class="sxs-lookup"><span data-stu-id="a1705-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="a1705-164">執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note))，還原方案中三個專案的相依性。</span><span class="sxs-lookup"><span data-stu-id="a1705-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="a1705-165">開啟 *Program.cs*，並將 `Main` 方法的內容取代為下行：</span><span class="sxs-lookup"><span data-stu-id="a1705-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="a1705-166">將兩個 `using` 指示詞新增至 *Program.cs* 檔案的頂端：</span><span class="sxs-lookup"><span data-stu-id="a1705-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="a1705-167">執行下列 `dotnet run` 命令來執行可執行檔，而 `dotnet run` 的 `-p` 選項指定主要應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="a1705-168">應用程式會產生 "The answer is 42" 字串。</span><span class="sxs-lookup"><span data-stu-id="a1705-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="a1705-169">偵錯應用程式</span><span class="sxs-lookup"><span data-stu-id="a1705-169">Debug the application</span></span>

<span data-ttu-id="a1705-170">在 `Main` 方法中的 `WriteLine` 陳述式設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="a1705-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="a1705-171">為此，在游標位於`WriteLine`行上時按<kbd>Fn</kbd>+<kbd>F9</kbd>鍵，或者按一下要設置中斷點的行左距中的滑鼠。</span><span class="sxs-lookup"><span data-stu-id="a1705-171">Do this by either pressing the <kbd>Fn</kbd>+<kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="a1705-172">紅色圓圈會出現在程式碼行旁邊的邊界。</span><span class="sxs-lookup"><span data-stu-id="a1705-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="a1705-173">到達中斷點時，會在執行中斷點行「之前」\*\* 停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="a1705-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="a1705-174">通過在"視覺化工作室代碼"工具列中選擇調試圖示、從功能表列中選擇 **"查看** > **調試"** 或使用鍵盤快速鍵<kbd>&#8679;&#8984;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>打開調試器選項卡：</span><span class="sxs-lookup"><span data-stu-id="a1705-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View** > **Debug** from the menu bar, or using the keyboard shortcut <kbd>&#8679;</kbd><kbd>&#8984;</kbd><kbd>D</kbd>:</span></span>

![Visual Studio Code 偵錯工具](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="a1705-176">按下 [播放] 按鈕，在偵錯工具中啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1705-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="a1705-177">您已在此專案中創建了測試專案和應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1705-177">You've created both a test project and an application in this project.</span></span> <span data-ttu-id="a1705-178">調試器詢問要啟動哪個專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-178">The debugger asks which project you want to start.</span></span> <span data-ttu-id="a1705-179">選擇"應用"專案。</span><span class="sxs-lookup"><span data-stu-id="a1705-179">Select the "app" project.</span></span> <span data-ttu-id="a1705-180">應用程式會開始執行，並執行至中斷點，然後停止。</span><span class="sxs-lookup"><span data-stu-id="a1705-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="a1705-181">逐步執行 `Get` 方法，並確定您已傳入正確的引數。</span><span class="sxs-lookup"><span data-stu-id="a1705-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="a1705-182">確認答案是 42。</span><span class="sxs-lookup"><span data-stu-id="a1705-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
