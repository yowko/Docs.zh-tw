---
title: "使用 dotnet test 和 xUnit 的 .NET Core 單元測試"
description: "透過逐步使用 dotnet 測試和 xUnit 建置範例方案的互動式體驗，了解 .NET Core 中的單元測試概念。"
author: ardalis
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: d989ee731d7ffd0439bac69afe1458e2aa10733a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/17/2017

---
# <a name="unit-testing-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="c326c-103">使用 dotnet test 和 xUnit 的 .NET Core 單元測試</span><span class="sxs-lookup"><span data-stu-id="c326c-103">Unit testing in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="c326c-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="c326c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="c326c-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="c326c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="c326c-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="c326c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="c326c-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="c326c-107">Creating the source project</span></span>

<span data-ttu-id="c326c-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="c326c-108">Open a shell window.</span></span> <span data-ttu-id="c326c-109">建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="c326c-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="c326c-110">在這個新目錄中建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="c326c-110">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="c326c-111">到目前為止的目錄結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="c326c-111">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
```

<span data-ttu-id="c326c-112">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="c326c-112">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="c326c-113">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="c326c-113">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="c326c-114">為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="c326c-114">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}
```

## <a name="creating-the-test-project"></a><span data-ttu-id="c326c-115">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="c326c-115">Creating the test project</span></span>

<span data-ttu-id="c326c-116">將目錄變更回 *unit-testing-using-dotnet-test* 目錄，然後建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="c326c-116">Change the directory back to the *unit-testing-using-dotnet-test* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="c326c-117">目錄結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="c326c-117">The directory structure is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="c326c-118">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new xunit`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="c326c-118">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="c326c-119">這樣會建立將 xUnit 作為測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="c326c-119">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="c326c-120">產生的範本會在 *PrimeServiceTests.csproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="c326c-120">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="c326c-121">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="c326c-121">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="c326c-122">上一個步驟中的 `dotnet new` 已新增 xUnit 和 xUnit 執行器。</span><span class="sxs-lookup"><span data-stu-id="c326c-122">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="c326c-123">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="c326c-123">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="c326c-124">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="c326c-124">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="c326c-125">另一個選項是編輯 *PrimeService.Tests.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="c326c-125">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="c326c-126">在第一個 `<ItemGroup>` 節點的正下方，新增另一個參考至程式庫專案的 `<ItemGroup>` 節點：</span><span class="sxs-lookup"><span data-stu-id="c326c-126">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="c326c-127">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="c326c-127">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="c326c-128">最終的方案配置如下所示：</span><span class="sxs-lookup"><span data-stu-id="c326c-128">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="c326c-129">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="c326c-129">Creating the first test</span></span>

<span data-ttu-id="c326c-130">建置程式庫或測試之前，先在 *PrimeService.Tests* 目錄中執行 [`dotnet restore`](../tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="c326c-130">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="c326c-131">此命令會還原每個專案的所有必要 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c326c-131">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="c326c-132">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="c326c-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="c326c-133">從 *PrimeService.Tests* 目錄移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="c326c-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="c326c-134">`[Fact]` 屬性會將方法表示為單一測試。</span><span class="sxs-lookup"><span data-stu-id="c326c-134">The `[Fact]` attribute denotes a method as a single test.</span></span> <span data-ttu-id="c326c-135">執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="c326c-135">Execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="c326c-136">xUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="c326c-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="c326c-137">`dotnet test` 會啟動測試執行器，並將命令列引數提供給測試執行器以指出包含測試的組件。</span><span class="sxs-lookup"><span data-stu-id="c326c-137">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="c326c-138">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="c326c-138">Your test fails.</span></span> <span data-ttu-id="c326c-139">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="c326c-139">You haven't created the implementation yet.</span></span> <span data-ttu-id="c326c-140">在 `PrimeService` 類別中撰寫最簡單的程式碼，使這個測試順利通過：</span><span class="sxs-lookup"><span data-stu-id="c326c-140">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

```csharp
public bool IsPrime(int candidate) 
{
    if (candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

<span data-ttu-id="c326c-141">在 *PrimeService.Tests* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="c326c-141">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="c326c-142">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="c326c-142">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="c326c-143">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="c326c-143">After building both projects, it runs this single test.</span></span> <span data-ttu-id="c326c-144">測試通過。</span><span class="sxs-lookup"><span data-stu-id="c326c-144">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="c326c-145">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="c326c-145">Adding more features</span></span>

<span data-ttu-id="c326c-146">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="c326c-146">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="c326c-147">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="c326c-147">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="c326c-148">您可以使用 `[Fact]` 屬性將這些項目新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="c326c-148">You could add those as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="c326c-149">因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="c326c-149">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="c326c-150">`[Theory]` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="c326c-150">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="c326c-151">您可以使用 `[InlineData]` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="c326c-151">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="c326c-152">您不需要建立新的測試，而可以改為使用這兩個屬性來建立單一的理論，以測試幾個小於 2 (最小質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="c326c-152">Instead of creating new tests, leverage these two attributes to create a single theory that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="c326c-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="c326c-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="c326c-154">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="c326c-154">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="c326c-155">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="c326c-155">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="c326c-156">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="c326c-156">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="c326c-157">您就可以得到[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="c326c-157">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="c326c-158">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="c326c-158">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="c326c-159">您已經將方案結構化，使新增套件和測試更順暢，因此您可以將大部分的時間和精力專注於解決應用程式的目標。</span><span class="sxs-lookup"><span data-stu-id="c326c-159">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>

