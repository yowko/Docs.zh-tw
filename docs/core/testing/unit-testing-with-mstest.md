---
title: 使用 MSTest 與 .NET Core 為 C# 進行單元測試
description: 透過逐步使用 dotnet test 和 MSTest 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: c396be926d743b672cb4611dc5569ecb48b09fec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397477"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="732a6-103">使用 MSTest 與 .NET Core 為 C# 進行單元測試</span><span class="sxs-lookup"><span data-stu-id="732a6-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="732a6-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="732a6-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="732a6-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/)。</span><span class="sxs-lookup"><span data-stu-id="732a6-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="732a6-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="732a6-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="732a6-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="732a6-107">Creating the source project</span></span>

<span data-ttu-id="732a6-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="732a6-108">Open a shell window.</span></span> <span data-ttu-id="732a6-109">建立名稱為 *unit-testing-using-mstest* 的目錄來放置解決方案。</span><span class="sxs-lookup"><span data-stu-id="732a6-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="732a6-110">在此新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以針對類別庫與測試專案建立新方案檔。</span><span class="sxs-lookup"><span data-stu-id="732a6-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="732a6-111">接著，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="732a6-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="732a6-112">下列大綱顯示到目前為止的目錄與檔案結構：</span><span class="sxs-lookup"><span data-stu-id="732a6-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="732a6-113">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="732a6-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="732a6-114">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="732a6-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="732a6-115">建立會失敗的 `PrimeService` 類別實作：</span><span class="sxs-lookup"><span data-stu-id="732a6-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="732a6-116">將目錄變更回 *unit-testing-using-mstest* 目錄。</span><span class="sxs-lookup"><span data-stu-id="732a6-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="732a6-117">執行 [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="732a6-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="732a6-118">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="732a6-118">Creating the test project</span></span>

<span data-ttu-id="732a6-119">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="732a6-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="732a6-120">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="732a6-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="732a6-121">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new mstest`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="732a6-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="732a6-122">dotnet new 命令會建立將 MSTest 作為測試程式庫使用的測試專案。</span><span class="sxs-lookup"><span data-stu-id="732a6-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="732a6-123">產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="732a6-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="732a6-124">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="732a6-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="732a6-125">上一個步驟中的 `dotnet new` 已新增 MSTest SDK、MSTest 測試架構和 MSTest 執行器。</span><span class="sxs-lookup"><span data-stu-id="732a6-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="732a6-126">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="732a6-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="732a6-127">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="732a6-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="732a6-128">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="732a6-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="732a6-129">下列大綱顯示最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="732a6-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="732a6-130">執行 *unit-testing-using-mstest* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="732a6-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="732a6-131">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="732a6-131">Creating the first test</span></span>

<span data-ttu-id="732a6-132">撰寫一個會失敗的測試，再使其通過，然後重複這個過程。</span><span class="sxs-lookup"><span data-stu-id="732a6-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="732a6-133">從 *PrimeService.Tests* 目錄移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="732a6-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="732a6-134">`[TestClass]` 屬性代表包含單元測試的類別。</span><span class="sxs-lookup"><span data-stu-id="732a6-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="732a6-135">`[TestMethod]` 屬性指出方法是測試方法。</span><span class="sxs-lookup"><span data-stu-id="732a6-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="732a6-136">儲存此檔案並執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="732a6-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="732a6-137">MSTest 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="732a6-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="732a6-138">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="732a6-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="732a6-139">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="732a6-139">Your test fails.</span></span> <span data-ttu-id="732a6-140">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="732a6-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="732a6-141">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以讓此測試成功：</span><span class="sxs-lookup"><span data-stu-id="732a6-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="732a6-142">在 *unit-testing-using-mstest* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="732a6-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="732a6-143">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="732a6-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="732a6-144">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="732a6-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="732a6-145">測試通過。</span><span class="sxs-lookup"><span data-stu-id="732a6-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="732a6-146">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="732a6-146">Adding more features</span></span>

<span data-ttu-id="732a6-147">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="732a6-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="732a6-148">還有一些其他適用於下列質數的簡單案例：0、-1。</span><span class="sxs-lookup"><span data-stu-id="732a6-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="732a6-149">您可以使用 `[TestMethod]` 屬性來加入新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="732a6-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="732a6-150">因此，還有其他 MSTest 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="732a6-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="732a6-151">`[DataTestMethod]` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="732a6-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="732a6-152">您可以使用 `[DataRow]` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="732a6-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="732a6-153">您不需要建立新測試，只要套用這兩個屬性以建立單一資料驅動測試即可。</span><span class="sxs-lookup"><span data-stu-id="732a6-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="732a6-154">資料驅動型測試是一種測試方法，其會測試數個低於二 (最小質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="732a6-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="732a6-155">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="732a6-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="732a6-156">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="732a6-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="732a6-157">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="732a6-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="732a6-158">您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="732a6-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="732a6-159">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="732a6-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="732a6-160">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="732a6-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="732a6-161">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="732a6-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
