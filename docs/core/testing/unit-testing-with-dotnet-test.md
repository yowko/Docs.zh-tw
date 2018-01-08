---
title: "使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試"
description: "透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。"
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 22f1f460ed87767768e806a85daab39f204db24f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="a70b3-103">使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試</span><span class="sxs-lookup"><span data-stu-id="a70b3-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="a70b3-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="a70b3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="a70b3-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="a70b3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="a70b3-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="a70b3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="a70b3-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="a70b3-107">Creating the source project</span></span>

<span data-ttu-id="a70b3-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="a70b3-108">Open a shell window.</span></span> <span data-ttu-id="a70b3-109">建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="a70b3-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="a70b3-111">具備解決方案可讓您更輕鬆地同時管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="a70b3-112">在方案目錄中，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="a70b3-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="a70b3-113">到目前為止，目錄與檔案結構應如下所示：</span><span class="sxs-lookup"><span data-stu-id="a70b3-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="a70b3-114">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="a70b3-115">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="a70b3-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="a70b3-116">若要使用測試驅動開發 (TDD)，請先建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="a70b3-116">To use test-driven development (TDD), you first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="a70b3-117">將目錄變更回 *unit-testing-using-dotnet-test* 目錄。</span><span class="sxs-lookup"><span data-stu-id="a70b3-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="a70b3-118">執行 [dotnet sln](../tools/dotnet-sln.md) 命令，將類別庫專案新增至解決方案：</span><span class="sxs-lookup"><span data-stu-id="a70b3-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="a70b3-119">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="a70b3-119">Creating the test project</span></span>

<span data-ttu-id="a70b3-120">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="a70b3-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="a70b3-121">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="a70b3-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="a70b3-122">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new xunit`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="a70b3-123">此命令會建立將 xUnit 作為測試程式庫使用的測試專案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="a70b3-124">產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器，類似如下程式碼：</span><span class="sxs-lookup"><span data-stu-id="a70b3-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="a70b3-125">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="a70b3-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="a70b3-126">上一個步驟中的 `dotnet new` 已新增 xUnit 和 xUnit 執行器。</span><span class="sxs-lookup"><span data-stu-id="a70b3-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="a70b3-127">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="a70b3-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="a70b3-128">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="a70b3-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="a70b3-129">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="a70b3-130">下面顯示最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="a70b3-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="a70b3-131">若要將測試專案新增至解決方案，請在 *unit-testing-using-dotnet-test* 目錄中執行 [dotnet sln](../tools/dotnet-sln.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="a70b3-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="a70b3-132">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="a70b3-132">Creating the first test</span></span>

<span data-ttu-id="a70b3-133">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="a70b3-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="a70b3-134">將 *UnitTest1.cs* 從 *PrimeService.Tests* 目錄移除，並建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="a70b3-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="a70b3-135">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a70b3-135">Add the following code:</span></span>

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

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="a70b3-136">`[Fact]` 屬性指出由測試執行器執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="a70b3-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="a70b3-137">從 *PrimeService.Tests* 資料夾執行 [`dotnet test`](../tools/dotnet-test.md)，建置測試及類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="a70b3-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="a70b3-138">xUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="a70b3-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="a70b3-139">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="a70b3-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="a70b3-140">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="a70b3-140">Your test fails.</span></span> <span data-ttu-id="a70b3-141">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="a70b3-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="a70b3-142">請在可運作的 `PrimeService` 類別中，撰寫最簡易的程式碼來進行測試。</span><span class="sxs-lookup"><span data-stu-id="a70b3-142">Make this test by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="a70b3-143">並使用下列程式碼取代現有的 `IsPrime` 方法實作：</span><span class="sxs-lookup"><span data-stu-id="a70b3-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="a70b3-144">在 *PrimeService.Tests* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="a70b3-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="a70b3-145">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="a70b3-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="a70b3-146">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="a70b3-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="a70b3-147">測試通過。</span><span class="sxs-lookup"><span data-stu-id="a70b3-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="a70b3-148">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="a70b3-148">Adding more features</span></span>

<span data-ttu-id="a70b3-149">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="a70b3-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="a70b3-150">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="a70b3-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="a70b3-151">您可以使用 `[Fact]` 屬性將那些案例新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="a70b3-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="a70b3-152">另有其他 xUnit 屬性可供您撰寫類似測試的套件：</span><span class="sxs-lookup"><span data-stu-id="a70b3-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="a70b3-153">`[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="a70b3-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="a70b3-154">`[InlineData]` 屬性會指定這些輸入的值。</span><span class="sxs-lookup"><span data-stu-id="a70b3-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="a70b3-155">您無須建立新的測試，只要套用這兩個屬性 (`[Theory]` 和 `[InlineData]`)，即可在 *PrimeService_IsPrimeShould.cs* 檔案中建立單一理論。</span><span class="sxs-lookup"><span data-stu-id="a70b3-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="a70b3-156">該理論是一種方法，這種方法會測試數個低於二 (最小的質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="a70b3-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="a70b3-157">再次執行 `dotnet test`，這些測試的其中兩個應該會失敗。</span><span class="sxs-lookup"><span data-stu-id="a70b3-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="a70b3-158">若要讓所有測試都能通過，請變更 *PrimeService.cs* 檔案中 `IsPrime` 方法開頭處的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="a70b3-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="a70b3-159">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="a70b3-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="a70b3-160">您有[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="a70b3-160">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a70b3-161">其他資源</span><span class="sxs-lookup"><span data-stu-id="a70b3-161">Additional resources</span></span>

[<span data-ttu-id="a70b3-162">測試 ASP.NET Core 中的控制器邏輯</span><span class="sxs-lookup"><span data-stu-id="a70b3-162">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
