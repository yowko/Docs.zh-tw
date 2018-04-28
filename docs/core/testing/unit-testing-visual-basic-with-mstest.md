---
title: 使用 dotnet test 與 MSTest 為 .NET Core 中的 Visual Basic 進行單元測試
description: 透過逐步使用 MSTest 建置範例 Visual Basic 方案的互動式體驗，了解 .NET Core 中的單元測試概念。
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: conceptual
dev_langs:
- vb
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: c573d0a4eae38a15f22730748022effdc00ff0a6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="65b0b-103">使用 dotnet test 與 MStest 為 Visual Basic .NET Core 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="65b0b-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="65b0b-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="65b0b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="65b0b-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/)。</span><span class="sxs-lookup"><span data-stu-id="65b0b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="65b0b-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="65b0b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="65b0b-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="65b0b-107">Creating the source project</span></span>

<span data-ttu-id="65b0b-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="65b0b-108">Open a shell window.</span></span> <span data-ttu-id="65b0b-109">建立名為 *unit-testing-vb-mstest* 的目錄來放置解決方案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="65b0b-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="65b0b-111">此練習可讓您更輕鬆地管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="65b0b-112">在方案目錄中，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="65b0b-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="65b0b-113">到目前為止，您有下列目錄與檔案結構：</span><span class="sxs-lookup"><span data-stu-id="65b0b-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="65b0b-114">將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="65b0b-115">將 *Class1.VB* 重新命名為 *PrimeService.VB*。</span><span class="sxs-lookup"><span data-stu-id="65b0b-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="65b0b-116">為了使用測試導向開發 (TDD)，您會建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="65b0b-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="65b0b-117">將目錄變更回 *unit-testing-vb-using-stest* 目錄。</span><span class="sxs-lookup"><span data-stu-id="65b0b-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="65b0b-118">執行 [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="65b0b-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="65b0b-119">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="65b0b-119">Creating the test project</span></span>

<span data-ttu-id="65b0b-120">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="65b0b-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="65b0b-121">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="65b0b-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="65b0b-122">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new mstest -lang VB`](../tools/dotnet-new.md) 建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="65b0b-123">此命令會建立將 MSTest 用作為測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="65b0b-124">產生的範本會在 *PrimeServiceTests.vbproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="65b0b-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="65b0b-125">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="65b0b-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="65b0b-126">上一個步驟中的 `dotnet new` 已新增 MSTest 和 MSTest 執行器。</span><span class="sxs-lookup"><span data-stu-id="65b0b-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="65b0b-127">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="65b0b-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="65b0b-128">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="65b0b-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="65b0b-129">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="65b0b-130">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="65b0b-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="65b0b-131">執行 *unit-testing-vb-mstest* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="65b0b-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="65b0b-132">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="65b0b-132">Creating the first test</span></span>

<span data-ttu-id="65b0b-133">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="65b0b-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="65b0b-134">將 *UnitTest1.vb* 從 *PrimeService.Tests* 目錄移除，並建立名為 *PrimeService_IsPrimeShould.VB* 的新 Visual Basic 檔案。</span><span class="sxs-lookup"><span data-stu-id="65b0b-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="65b0b-135">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="65b0b-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="65b0b-136">`<TestClass>` 屬性指出包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="65b0b-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="65b0b-137">`<TestMethod>` 屬性表示由測試執行器執行的方法。</span><span class="sxs-lookup"><span data-stu-id="65b0b-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="65b0b-138">從 *unit-testing-vb-mstest*，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試及類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="65b0b-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="65b0b-139">MSTest 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="65b0b-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="65b0b-140">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="65b0b-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="65b0b-141">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="65b0b-141">Your test fails.</span></span> <span data-ttu-id="65b0b-142">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="65b0b-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="65b0b-143">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以進行此測試：</span><span class="sxs-lookup"><span data-stu-id="65b0b-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="65b0b-144">在 *unit-testing-vb-mstest* 目錄中，再次執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="65b0b-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="65b0b-145">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="65b0b-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="65b0b-146">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="65b0b-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="65b0b-147">測試通過。</span><span class="sxs-lookup"><span data-stu-id="65b0b-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="65b0b-148">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="65b0b-148">Adding more features</span></span>

<span data-ttu-id="65b0b-149">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="65b0b-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="65b0b-150">還有一些其他適用於質數 0、-1 的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="65b0b-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="65b0b-151">您可以使用 `<TestMethod>` 屬性將那些案例新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="65b0b-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="65b0b-152">因此，還有其他 MSTest 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="65b0b-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="65b0b-153">`<DataTestMethod>` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="65b0b-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="65b0b-154">您可以使用 `<DataRow>` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="65b0b-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="65b0b-155">您不需要建立新測試，只要套用這兩個屬性以建立單一理論即可。</span><span class="sxs-lookup"><span data-stu-id="65b0b-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="65b0b-156">該理論是一種方法，這種方法會測試數個低於二 (最小的質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="65b0b-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="65b0b-157">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="65b0b-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="65b0b-158">若要使所有測試通過，請變更方法開頭的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="65b0b-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="65b0b-159">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="65b0b-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="65b0b-160">您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb)。</span><span class="sxs-lookup"><span data-stu-id="65b0b-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="65b0b-161">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="65b0b-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="65b0b-162">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="65b0b-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="65b0b-163">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="65b0b-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
