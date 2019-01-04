---
title: 使用 dotnet test 與 NUnit 為 .NET Core 中的 Visual Basic 進行單元測試
description: 使用 NUnit 逐步建置 Visual Basic 解決方案範例的互動式體驗，了解 .NET Core 中的單元測試概念。
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 84f4b828bd1418f511b2bd82ef959002bc11ad0f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239145"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="32978-103">使用 dotnet test 與 NUnit 為 Visual Basic .NET Core 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="32978-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="32978-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="32978-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="32978-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/)。</span><span class="sxs-lookup"><span data-stu-id="32978-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="32978-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="32978-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32978-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="32978-107">Prerequisites</span></span>

- <span data-ttu-id="32978-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="32978-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="32978-109">您選擇的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="32978-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="32978-110">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="32978-110">Creating the source project</span></span>

<span data-ttu-id="32978-111">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="32978-111">Open a shell window.</span></span> <span data-ttu-id="32978-112">建立名稱為 *unit-testing-vb-nunit* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="32978-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="32978-113">在此新目錄中，執行下列命令以針對類別庫與測試專案建立新方案檔：</span><span class="sxs-lookup"><span data-stu-id="32978-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="32978-114">接著，建立 *PrimeService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="32978-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="32978-115">下列大綱顯示到目前為止的檔案結構：</span><span class="sxs-lookup"><span data-stu-id="32978-115">The following outline shows the file structure so far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="32978-116">將 *PrimeService* 設為目前的目錄，然後執行下列命令以建立來源專案：</span><span class="sxs-lookup"><span data-stu-id="32978-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="32978-117">將 *Class1.VB* 重新命名為 *PrimeService.VB*。</span><span class="sxs-lookup"><span data-stu-id="32978-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="32978-118">為了使用測試導向開發 (TDD)，您會建立 `PrimeService` 類別的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="32978-118">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="32978-119">將目錄變更回 *unit-testing-vb-using-stest* 目錄。</span><span class="sxs-lookup"><span data-stu-id="32978-119">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="32978-120">執行下列命令，將類別庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="32978-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="32978-121">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="32978-121">Creating the test project</span></span>

<span data-ttu-id="32978-122">接著，建立 *PrimeService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="32978-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="32978-123">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="32978-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="32978-124">將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用下列命令建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="32978-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="32978-125">[dotnet new](../tools/dotnet-new.md) 命令會建立將 NUnit 用作測試程式庫的測試專案。</span><span class="sxs-lookup"><span data-stu-id="32978-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="32978-126">產生的範本會在 *PrimeServiceTests.vbproj* 檔案中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="32978-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="32978-127">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="32978-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="32978-128">上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。</span><span class="sxs-lookup"><span data-stu-id="32978-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="32978-129">現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="32978-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="32978-130">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="32978-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="32978-131">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="32978-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="32978-132">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="32978-132">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="32978-133">在 *unit-testing-vb-nunit* 目錄中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="32978-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="32978-134">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="32978-134">Creating the first test</span></span>

<span data-ttu-id="32978-135">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="32978-135">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="32978-136">在 *PrimeService.Tests* 目錄中，將 *UnitTest1.vb* 檔案重新命名為 *PrimeService_IsPrimeShould.VB*，並將其整個內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="32978-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="32978-137">`<TestFixture>` 屬性指出包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="32978-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="32978-138">`<Test>` 屬性表示由測試執行器執行的方法。</span><span class="sxs-lookup"><span data-stu-id="32978-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="32978-139">從 *unit-testing-vb-nunit*，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試及類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="32978-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="32978-140">NUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="32978-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="32978-141">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="32978-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="32978-142">您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="32978-142">Your test fails.</span></span> <span data-ttu-id="32978-143">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="32978-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="32978-144">在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以進行此測試：</span><span class="sxs-lookup"><span data-stu-id="32978-144">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="32978-145">在 *unit-testing-vb-nunit* 目錄中，再次執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="32978-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="32978-146">`dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="32978-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="32978-147">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="32978-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="32978-148">測試通過。</span><span class="sxs-lookup"><span data-stu-id="32978-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="32978-149">新增更多功能</span><span class="sxs-lookup"><span data-stu-id="32978-149">Adding more features</span></span>

<span data-ttu-id="32978-150">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="32978-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="32978-151">還有一些其他適用於下列質數的簡單案例：0、-1。</span><span class="sxs-lookup"><span data-stu-id="32978-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="32978-152">您可以使用 `<Test>` 屬性將那些案例新增為新測試，但很快就會單調乏味。</span><span class="sxs-lookup"><span data-stu-id="32978-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="32978-153">因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。</span><span class="sxs-lookup"><span data-stu-id="32978-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="32978-154">`<TestCase>` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="32978-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="32978-155">您可以使用 `<TestCase>` 屬性來指定這些輸入值。</span><span class="sxs-lookup"><span data-stu-id="32978-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="32978-156">您不需要建立新的測試，而可以改為套用這兩個屬性來建立一系列的測試，以測試數個小於 2 (最小質數) 的值：</span><span class="sxs-lookup"><span data-stu-id="32978-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="32978-157">執行 `dotnet test`，然後會有兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="32978-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="32978-158">若要讓所有測試都能通過，請變更 *PrimeServices.cs* 檔案中 `Main` 方法開頭處的 `if` 子句：</span><span class="sxs-lookup"><span data-stu-id="32978-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="32978-159">繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。</span><span class="sxs-lookup"><span data-stu-id="32978-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="32978-160">您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)。</span><span class="sxs-lookup"><span data-stu-id="32978-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="32978-161">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="32978-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="32978-162">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="32978-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="32978-163">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="32978-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
