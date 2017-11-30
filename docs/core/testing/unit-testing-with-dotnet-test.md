---
title: "使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試"
description: "透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。"
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="d82f8-103">使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試</span><span class="sxs-lookup"><span data-stu-id="d82f8-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="d82f8-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="d82f8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d82f8-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="d82f8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="d82f8-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="d82f8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="d82f8-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="d82f8-107">Creating the source project</span></span>

<span data-ttu-id="d82f8-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="d82f8-108">Open a shell window.</span></span> <span data-ttu-id="d82f8-109">建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="d82f8-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="d82f8-111">這樣可讓您更輕鬆地管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="d82f8-112">在方案目錄中，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="d82f8-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="d82f8-113">到目前為止，目錄與檔案結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="d82f8-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="d82f8-114">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="d82f8-115">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="d82f8-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="d82f8-116">為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="d82f8-116">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="d82f8-117">將目錄變更回 *unit-testing-using-dotnet-test* 目錄。</span><span class="sxs-lookup"><span data-stu-id="d82f8-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span> <span data-ttu-id="d82f8-118">執行 [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="d82f8-118">Run [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="d82f8-119">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="d82f8-119">Creating the test project</span></span>

<span data-ttu-id="d82f8-120">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="d82f8-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d82f8-121">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="d82f8-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="d82f8-122">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new xunit`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="d82f8-123">這樣會建立將 xUnit 作為測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-123">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="d82f8-124">產生的範本會在 *PrimeServiceTests.csproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="d82f8-124">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="d82f8-125">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="d82f8-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d82f8-126">上一個步驟中的 `dotnet new` 已新增 xUnit 和 xUnit 執行器。</span><span class="sxs-lookup"><span data-stu-id="d82f8-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="d82f8-127">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="d82f8-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="d82f8-128">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="d82f8-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="d82f8-129">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="d82f8-130">下面顯示最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="d82f8-130">The following shows the final solution layout:</span></span>

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

<span data-ttu-id="d82f8-131">執行 *unit-testing-using-dotnet-test* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="d82f8-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="d82f8-132">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="d82f8-132">Creating the first test</span></span>

<span data-ttu-id="d82f8-133">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="d82f8-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="d82f8-134">將 *UnitTest1.cs* 從 *PrimeService.Tests* 目錄移除，並建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="d82f8-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="d82f8-135">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d82f8-135">Add the following code:</span></span>

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

<span data-ttu-id="d82f8-136">`[Fact]` 屬性指出由測試執行器執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="d82f8-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="d82f8-137">從 *unit-testing-using-dotnet-test*，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="d82f8-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d82f8-138">xUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="d82f8-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d82f8-139">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="d82f8-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="d82f8-140">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="d82f8-140">Your test fails.</span></span> <span data-ttu-id="d82f8-141">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="d82f8-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="d82f8-142">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以進行此測試：</span><span class="sxs-lookup"><span data-stu-id="d82f8-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="d82f8-143">在 *unit-testing-using-dotnet-test* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="d82f8-143">In the *unit-testing-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d82f8-144">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="d82f8-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="d82f8-145">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="d82f8-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d82f8-146">測試通過。</span><span class="sxs-lookup"><span data-stu-id="d82f8-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="d82f8-147">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="d82f8-147">Adding more features</span></span>

<span data-ttu-id="d82f8-148">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="d82f8-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d82f8-149">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="d82f8-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="d82f8-150">您可以使用 `[Fact]` 屬性將那些案例新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="d82f8-150">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="d82f8-151">因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="d82f8-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="d82f8-152">`[Theory]` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="d82f8-152">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="d82f8-153">您可以使用 `[InlineData]` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="d82f8-153">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="d82f8-154">您不需要建立新測試，只要套用這兩個屬性以建立單一理論即可。</span><span class="sxs-lookup"><span data-stu-id="d82f8-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="d82f8-155">該理論是一種方法，這種方法會測試數個低於二 (最小的質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="d82f8-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="d82f8-156">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="d82f8-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="d82f8-157">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="d82f8-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="d82f8-158">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="d82f8-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="d82f8-159">您有[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="d82f8-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d82f8-160">其他資源</span><span class="sxs-lookup"><span data-stu-id="d82f8-160">Additional resources</span></span>

[<span data-ttu-id="d82f8-161">在 ASP.NET Core 中測試控制器邏輯</span><span class="sxs-lookup"><span data-stu-id="d82f8-161">Testing controller logic in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
