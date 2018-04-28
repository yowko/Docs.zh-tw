---
title: 利用 NUnit 與 .NET Core 進行 C# 單元測試
description: 使用 dotnet test 與 NUnit 逐步建置解決方案範例的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: rprouse
ms.date: 12/01/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: db11adf265b2a08456a1bd42bc8a6847ba70a2ce
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="5bb2f-103">利用 NUnit 與 .NET Core 進行 C# 單元測試</span><span class="sxs-lookup"><span data-stu-id="5bb2f-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="5bb2f-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5bb2f-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/)。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="5bb2f-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="5bb2f-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="5bb2f-107">Creating the source project</span></span>

<span data-ttu-id="5bb2f-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-108">Open a shell window.</span></span> <span data-ttu-id="5bb2f-109">建立名稱為 *unit-testing-using-nunit* 的目錄來放置解決方案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-109">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="5bb2f-110">在此新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以針對類別庫與測試專案建立新方案檔。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="5bb2f-111">接著，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="5bb2f-112">下列大綱顯示到目前為止的目錄與檔案結構：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="5bb2f-113">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="5bb2f-114">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="5bb2f-115">為了使用測試導向開發 (TDD)，您會建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="5bb2f-116">將目錄變更回 *unit-testing-using-nunit* 目錄。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-116">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="5bb2f-117">執行 [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="5bb2f-118">安裝 NUnit 專案範本</span><span class="sxs-lookup"><span data-stu-id="5bb2f-118">Install the NUnit project template</span></span>

<span data-ttu-id="5bb2f-119">必須安裝 NUnit 專案範本，才可建立測試專案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="5bb2f-120">這項作業在您想要建立新的 NUnit 專案之每部開發人員電腦上，只需執行一次即可。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="5bb2f-121">執行 [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) 以安裝 NUnit 範本。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="5bb2f-122">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="5bb2f-122">Creating the test project</span></span>

<span data-ttu-id="5bb2f-123">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-123">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5bb2f-124">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="5bb2f-125">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new nunit`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-125">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="5bb2f-126">dotnet new 命令會建立將 NUnit 用作為測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-126">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="5bb2f-127">產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-127">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="5bb2f-128">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5bb2f-129">上一個步驟中的 `dotnet new`，新增了 Microsoft 測試 SDK、NUnit 測試架構以及 NUnit 測試配接器。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-129">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="5bb2f-130">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-130">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5bb2f-131">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="5bb2f-132">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-132">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="5bb2f-133">下列大綱顯示最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-133">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="5bb2f-134">執行 *unit-testing-using-dotnet-test* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-134">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="5bb2f-135">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="5bb2f-135">Creating the first test</span></span>

<span data-ttu-id="5bb2f-136">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="5bb2f-137">從 *PrimeService.Tests* 目錄移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-137">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="5bb2f-138">`[TestFixture]` 屬性代表包含單元測試的類別。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-138">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="5bb2f-139">`[Test]` 屬性指出方法是測試方法。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-139">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="5bb2f-140">儲存此檔案並執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-140">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5bb2f-141">NUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5bb2f-142">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5bb2f-143">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-143">Your test fails.</span></span> <span data-ttu-id="5bb2f-144">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-144">You haven't created the implementation yet.</span></span> <span data-ttu-id="5bb2f-145">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以讓此測試成功：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-145">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="5bb2f-146">在 *unit-testing-using-nunit* 目錄中，再次執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-146">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5bb2f-147">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-147">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5bb2f-148">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-148">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5bb2f-149">測試通過。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-149">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5bb2f-150">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="5bb2f-150">Adding more features</span></span>

<span data-ttu-id="5bb2f-151">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-151">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5bb2f-152">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-152">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5bb2f-153">您可以使用 `[Test]` 屬性來加入新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-153">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5bb2f-154">另有其他 NUnit 屬性可供您撰寫類似測試的套件。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-154">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="5bb2f-155">`[TestCase]` 屬性可用於建立執行相同程式碼，但輸入引數不同的測試套件。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-155">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="5bb2f-156">您可以使用 `[TestCase]` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-156">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="5bb2f-157">您不需要建立新的測試，只要套用此屬性來建立單一資料驅動型測試即可。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-157">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="5bb2f-158">資料驅動型測試是一種測試方法，其會測試數個低於二 (最小質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-158">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="5bb2f-159">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-159">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="5bb2f-160">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="5bb2f-160">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="5bb2f-161">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-161">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5bb2f-162">您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-162">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="5bb2f-163">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="5bb2f-163">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5bb2f-164">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-164">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5bb2f-165">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="5bb2f-165">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
