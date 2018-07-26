---
title: 在 macOS 上開始使用 .NET Core
description: 本文件提供使用 Visual Studio Code 建立 .NET Core 方案的步驟及工作流程。
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.openlocfilehash: 5a4b2734137f59b29535f302dd17fb94329d676f
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245581"
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="85f9c-103">在 macOS 上開始使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="85f9c-103">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="85f9c-104">本文件提供建立適用於 macOS 之 .NET Core 方案的步驟及工作流程。</span><span class="sxs-lookup"><span data-stu-id="85f9c-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="85f9c-105">了解如何建立專案、建立單元測試、使用偵錯工具，以及透過 [NuGet](https://www.nuget.org/) 納入協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="85f9c-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="85f9c-106">這篇文章會在 macOS 上使用 [Visual Studio Code](http://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-106">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85f9c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="85f9c-107">Prerequisites</span></span>

<span data-ttu-id="85f9c-108">安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/core)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="85f9c-109">.NET Core SDK 包含 .NET Core 架構和執行階段的最新版本。</span><span class="sxs-lookup"><span data-stu-id="85f9c-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="85f9c-110">安裝 [Visual Studio Code (英文)](http://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-110">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="85f9c-111">在這篇文章的過程中，您也將安裝能改善 .NET Core 開發體驗的 Visual Studio Code 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="85f9c-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="85f9c-112">請開啟 Visual Studio Code，並按下 <kbd>F1</kbd> 來開啟 Visual Studio Code 調色盤，以安裝 Visual Studio Code C# 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="85f9c-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="85f9c-113">鍵入 **ext install** 來查看延伸模組的清單。</span><span class="sxs-lookup"><span data-stu-id="85f9c-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="85f9c-114">選取 C# 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="85f9c-114">Select the C# extension.</span></span> <span data-ttu-id="85f9c-115">重新啟動 Visual Studio Code 以啟動延伸模組。</span><span class="sxs-lookup"><span data-stu-id="85f9c-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="85f9c-116">如需詳細資訊，請參閱 [Visual Studio Code C# 延伸模組文件](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="85f9c-117">使用者入門</span><span class="sxs-lookup"><span data-stu-id="85f9c-117">Getting started</span></span>

<span data-ttu-id="85f9c-118">在本教學課程中，您會建立三個專案︰程式庫專案、該程式庫專案的測試，以及利用程式庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="85f9c-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="85f9c-119">您可以在 GitHub 的 dotnet/samples 存放庫[檢視或下載來源](https://github.com/dotnet/samples/tree/master/core/getting-started/golden)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="85f9c-120">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="85f9c-121">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="85f9c-121">Start Visual Studio Code.</span></span> <span data-ttu-id="85f9c-122">按下 <kbd>Ctrl</kbd>+<kbd>\`</kbd> (倒引號字元)，或從功能表中選取 [檢視] > [整合式終端機]，以使用 Visual Studio Code 開啟內嵌終端機。</span><span class="sxs-lookup"><span data-stu-id="85f9c-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="85f9c-123">如果您想要在 Visual Studio Code 外部工作，則仍然可以使用總管 [在命令提示字元中開啟] 命令 (Mac 或 Linux 上的 [在終端機中開啟]) 來開啟外部殼層。</span><span class="sxs-lookup"><span data-stu-id="85f9c-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="85f9c-124">請從建立方案檔開始，而方案檔是作為一或多個 .NET Core 專案的容器。</span><span class="sxs-lookup"><span data-stu-id="85f9c-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="85f9c-125">在終端機中，建立 *golden* 資料夾，然後開啟該資料夾。</span><span class="sxs-lookup"><span data-stu-id="85f9c-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="85f9c-126">這個資料夾是您方案的根資料夾。</span><span class="sxs-lookup"><span data-stu-id="85f9c-126">This folder is the root of your solution.</span></span> <span data-ttu-id="85f9c-127">執行 [`dotnet new`](../tools/dotnet-new.md) 命令，建立新方案 *golden.sln*：</span><span class="sxs-lookup"><span data-stu-id="85f9c-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="85f9c-128">從 *golden* 資料夾中，執行下列命令來建立程式庫專案，這樣會在 *library* 資料夾中產生 library.csproj 及 Class1.cs 這兩個檔案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="85f9c-129">執行 [`dotnet sln`](../tools/dotnet-sln.md) 命令，將新建立的 *library.csproj* 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="85f9c-130">*library.csproj* 檔案包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="85f9c-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="85f9c-131">我們的程式庫方法會序列化及還原序列化 JSON 格式的物件。</span><span class="sxs-lookup"><span data-stu-id="85f9c-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="85f9c-132">若要支援 JSON 序列化及還原序列化，請新增 `Newtonsoft.Json` NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="85f9c-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="85f9c-133">`dotnet add` 命令會新增項目至專案。</span><span class="sxs-lookup"><span data-stu-id="85f9c-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="85f9c-134">若要新增 NuGet 套件的參考，請使用 [`dotnet add package`](../tools/dotnet-add-package.md) 命令，並指定套件的名稱：</span><span class="sxs-lookup"><span data-stu-id="85f9c-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="85f9c-135">這會將 `Newtonsoft.Json` 及其相依性新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="85f9c-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="85f9c-136">或者，手動編輯 *library.csproj* 檔案，並新增下列節點：</span><span class="sxs-lookup"><span data-stu-id="85f9c-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="85f9c-137">執行 [`dotnet restore`](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note))，以還原相依性，並在其中有三個檔案的 *library* 內建立 *obj* 資料夾，包含 *project.assets.json* 檔案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="85f9c-138">在 *library* 資料夾中，將檔案 *Class1.cs* 重新命名為 *Thing.cs*。</span><span class="sxs-lookup"><span data-stu-id="85f9c-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="85f9c-139">使用下列內容取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="85f9c-139">Replace the code with the following:</span></span>

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

<span data-ttu-id="85f9c-140">`Thing` 類別包含一個公用方法 `Get`，這個公用方法會傳回兩個數字的總和，而做法是將總和轉換成字串，然後將它還原序列化為整數。</span><span class="sxs-lookup"><span data-stu-id="85f9c-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="85f9c-141">這會利用一些現代 C# 功能，例如 [`using static`指示詞](../../csharp/language-reference/keywords/using-static.md)、[運算式主體成員](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)及[字串內插補點](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="85f9c-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="85f9c-142">使用 [`dotnet build`](../tools/dotnet-build.md) 命令建置程式庫。</span><span class="sxs-lookup"><span data-stu-id="85f9c-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="85f9c-143">這會在 *golden/library/bin/Debug/netstandard1.4* 底下產生 *library.dll* 檔案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="85f9c-144">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="85f9c-144">Create the test project</span></span>

<span data-ttu-id="85f9c-145">建置程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="85f9c-145">Build a test project for the library.</span></span> <span data-ttu-id="85f9c-146">從 *golden* 資料夾中，建立新的測試專案︰</span><span class="sxs-lookup"><span data-stu-id="85f9c-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="85f9c-147">將測試專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="85f9c-148">新增上一節中所建立之程式碼的專案參考，讓編譯器可以尋找及使用程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="85f9c-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="85f9c-149">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="85f9c-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="85f9c-150">或者，手動編輯 *test-library.csproj* 檔案，並新增下列節點：</span><span class="sxs-lookup"><span data-stu-id="85f9c-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="85f9c-151">既然已正確設定相依性，請建立您程式庫的測試。</span><span class="sxs-lookup"><span data-stu-id="85f9c-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="85f9c-152">開啟 *UnitTest1.cs* 並將其內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="85f9c-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="85f9c-153">請注意，當您第一次建立單元測試時，確認值 42 不等於 19+23 (或 42) (`Assert.NotEqual`)，而這項建立作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="85f9c-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="85f9c-154">建置單元測試的重要步驟是建立測試，以確認其邏輯在第一次時失敗一次。</span><span class="sxs-lookup"><span data-stu-id="85f9c-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="85f9c-155">從 *golden* 資料夾中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="85f9c-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="85f9c-156">這些命令會以遞迴方式尋找所有專案來還原相依性、建置相依性，並啟動 xUnit 測試執行器來執行測試。</span><span class="sxs-lookup"><span data-stu-id="85f9c-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="85f9c-157">如您所預期，單一測試失敗。</span><span class="sxs-lookup"><span data-stu-id="85f9c-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="85f9c-158">編輯 *UnitTest1.cs* 檔案，並將判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`。</span><span class="sxs-lookup"><span data-stu-id="85f9c-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="85f9c-159">從 *golden* 資料夾中執行下列命令，以重新執行測試，而這次測試會通過：</span><span class="sxs-lookup"><span data-stu-id="85f9c-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="85f9c-160">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="85f9c-160">Create the console app</span></span>

<span data-ttu-id="85f9c-161">您透過下列步驟所建立的主控台應用程式依存於您先前建立的程式庫專案，並在它執行時呼叫它的程式庫方法。</span><span class="sxs-lookup"><span data-stu-id="85f9c-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="85f9c-162">使用這種模式的開發，您會看到如何建立多個專案的可重複使用程式庫。</span><span class="sxs-lookup"><span data-stu-id="85f9c-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="85f9c-163">從 *golden* 資料夾中，建立新的主控台應用程式︰</span><span class="sxs-lookup"><span data-stu-id="85f9c-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="85f9c-164">將主控台應用程式專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="85f9c-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="85f9c-165">執行 `dotnet add reference` 命令，建立與程式庫的相依性︰</span><span class="sxs-lookup"><span data-stu-id="85f9c-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="85f9c-166">執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note))，還原方案中三個專案的相依性。</span><span class="sxs-lookup"><span data-stu-id="85f9c-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="85f9c-167">開啟 *Program.cs*，並將 `Main` 方法的內容取代為下行：</span><span class="sxs-lookup"><span data-stu-id="85f9c-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="85f9c-168">將兩個 `using` 指示詞新增至 *Program.cs* 檔案的頂端：</span><span class="sxs-lookup"><span data-stu-id="85f9c-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="85f9c-169">執行下列 `dotnet run` 命令來執行可執行檔，而 `dotnet run` 的 `-p` 選項指定主要應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="85f9c-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="85f9c-170">應用程式會產生 "The answer is 42" 字串。</span><span class="sxs-lookup"><span data-stu-id="85f9c-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="85f9c-171">進行應用程式偵錯</span><span class="sxs-lookup"><span data-stu-id="85f9c-171">Debug the application</span></span>

<span data-ttu-id="85f9c-172">在 `Main` 方法中的 `WriteLine` 陳述式設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="85f9c-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="85f9c-173">做法是在游標位於 `WriteLine` 行上方時按下 <kbd>F9</kbd> 鍵，或在您要設定中斷點之行的左邊界按一下滑鼠。</span><span class="sxs-lookup"><span data-stu-id="85f9c-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="85f9c-174">紅色圓圈會出現在程式碼行旁邊的邊界。</span><span class="sxs-lookup"><span data-stu-id="85f9c-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="85f9c-175">到達中斷點時，會在執行中斷點行「之前」停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="85f9c-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="85f9c-176">開啟偵錯工具索引標籤，方法是選取 Visual Studio Code 工具列中的偵錯圖示、選取功能表列中的 [檢視] > [偵錯]，或使用鍵盤快速鍵 <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>：</span><span class="sxs-lookup"><span data-stu-id="85f9c-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code 偵錯工具](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="85f9c-178">按下 [播放] 按鈕，在偵錯工具中啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="85f9c-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="85f9c-179">應用程式會開始執行，並執行至中斷點，然後停止。</span><span class="sxs-lookup"><span data-stu-id="85f9c-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="85f9c-180">逐步執行 `Get` 方法，並確定您已傳入正確的引數。</span><span class="sxs-lookup"><span data-stu-id="85f9c-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="85f9c-181">確認答案是 42。</span><span class="sxs-lookup"><span data-stu-id="85f9c-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]