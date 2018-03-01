---
title: "使用 dotnet test 與 NUnit 為 .NET Core 中的 Visual Basic 進行單元測試"
description: "使用 NUnit 逐步建置 Visual Basic 解決方案範例的互動式體驗，了解 .NET Core 中的單元測試概念。"
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.openlocfilehash: 2166da36fe9d0297f03e7c38249135d281b9a5d6
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="67124-103">使用 dotnet test 與 NUnit 為 Visual Basic .NET Core 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="67124-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="67124-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="67124-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="67124-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/)。</span><span class="sxs-lookup"><span data-stu-id="67124-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="67124-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="67124-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="67124-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="67124-107">Creating the source project</span></span>

<span data-ttu-id="67124-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="67124-108">Open a shell window.</span></span> <span data-ttu-id="67124-109">建立名稱為 *unit-testing-vb-nunit* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="67124-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="67124-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="67124-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="67124-111">此練習可讓您更輕鬆地管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="67124-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="67124-112">在方案目錄中，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="67124-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="67124-113">到目前為止，您有下列目錄與檔案結構：</span><span class="sxs-lookup"><span data-stu-id="67124-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="67124-114">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="67124-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="67124-115">將 *Class1.VB* 重新命名為 *PrimeService.VB*。</span><span class="sxs-lookup"><span data-stu-id="67124-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="67124-116">為了使用測試導向開發 (TDD)，您會建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="67124-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="67124-117">將目錄變更回 *unit-testing-vb-using-stest* 目錄。</span><span class="sxs-lookup"><span data-stu-id="67124-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="67124-118">執行 [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="67124-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="67124-119">安裝 NUnit 專案範本</span><span class="sxs-lookup"><span data-stu-id="67124-119">Install the NUnit project template</span></span>

<span data-ttu-id="67124-120">必須安裝 NUnit 專案範本，才可建立測試專案。</span><span class="sxs-lookup"><span data-stu-id="67124-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="67124-121">這項作業在您想要建立新的 NUnit 專案之每部開發人員電腦上，只需執行一次即可。</span><span class="sxs-lookup"><span data-stu-id="67124-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="67124-122">執行 [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) 以安裝 NUnit 範本。</span><span class="sxs-lookup"><span data-stu-id="67124-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="67124-123">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="67124-123">Creating the test project</span></span>

<span data-ttu-id="67124-124">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="67124-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="67124-125">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="67124-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="67124-126">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new nunit -lang VB`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="67124-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="67124-127">此命令會建立將 NUnit 用作為測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="67124-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="67124-128">產生的範本會在 *PrimeServiceTests.vbproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="67124-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="67124-129">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="67124-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="67124-130">上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。</span><span class="sxs-lookup"><span data-stu-id="67124-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="67124-131">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="67124-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="67124-132">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="67124-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="67124-133">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="67124-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="67124-134">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="67124-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="67124-135">執行 *unit-testing-vb-nunit* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="67124-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="67124-136">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="67124-136">Creating the first test</span></span>

<span data-ttu-id="67124-137">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="67124-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="67124-138">將 *UnitTest1.vb* 從 *PrimeService.Tests* 目錄移除，並建立名為 *PrimeService_IsPrimeShould.VB* 的新 Visual Basic 檔案。</span><span class="sxs-lookup"><span data-stu-id="67124-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="67124-139">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="67124-139">Add the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="67124-140">`<TestFixture>` 屬性指出包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="67124-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="67124-141">`<Test>` 屬性表示由測試執行器執行的方法。</span><span class="sxs-lookup"><span data-stu-id="67124-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="67124-142">從 *unit-testing-vb-nunit*，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試及類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="67124-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="67124-143">NUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="67124-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="67124-144">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="67124-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="67124-145">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="67124-145">Your test fails.</span></span> <span data-ttu-id="67124-146">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="67124-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="67124-147">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以進行此測試：</span><span class="sxs-lookup"><span data-stu-id="67124-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="67124-148">在 *unit-testing-vb-nunit* 目錄中，再次執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="67124-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="67124-149">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="67124-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="67124-150">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="67124-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="67124-151">測試通過。</span><span class="sxs-lookup"><span data-stu-id="67124-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="67124-152">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="67124-152">Adding more features</span></span>

<span data-ttu-id="67124-153">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="67124-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="67124-154">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="67124-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="67124-155">您可以使用 `<Test>` 屬性將那些案例新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="67124-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="67124-156">因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="67124-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="67124-157">`<TestCase>` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="67124-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="67124-158">您可以使用 `<TestCase>` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="67124-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="67124-159">您不需要建立新的測試，而可以改為套用這兩個屬性來建立一系列的測試，以測試數個小於 2 (最小質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="67124-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="67124-160">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="67124-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="67124-161">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="67124-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="67124-162">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="67124-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="67124-163">您有[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)。</span><span class="sxs-lookup"><span data-stu-id="67124-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="67124-164">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="67124-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="67124-165">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="67124-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="67124-166">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="67124-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
