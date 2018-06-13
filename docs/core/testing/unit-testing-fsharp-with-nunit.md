---
title: 使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 程式庫進行單元測試
description: 使用 dotnet test 與 NUnit 逐步建置解決方案範例的互動式體驗，了解 .NET Core 中 F# 的單元測試概念。
author: rprouse
ms.date: 12/01/2017
dev_langs:
- fsharp
ms.openlocfilehash: c5653463ce43ab8660753aa03ef79ba10f339fac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215744"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="ecc0d-103">使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="ecc0d-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="ecc0d-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ecc0d-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/)。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="ecc0d-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ecc0d-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="ecc0d-107">Creating the source project</span></span>

<span data-ttu-id="ecc0d-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-108">Open a shell window.</span></span> <span data-ttu-id="ecc0d-109">建立名為 *unit-testing-with-fsharp* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="ecc0d-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="ecc0d-111">這樣可讓您更輕鬆地管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="ecc0d-112">在方案目錄中，建立 *MathService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="ecc0d-113">到目前為止，目錄與檔案結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="ecc0d-114">將 *MathService* 設定為目前的目錄，然後執行 [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="ecc0d-115">為了使用測試導向開發 (TDD)，您將必須建立 math 服務的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="ecc0d-116">將目錄變更回 *unit-testing-with-fsharp* 目錄。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="ecc0d-117">執行 [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="ecc0d-118">安裝 NUnit 專案範本</span><span class="sxs-lookup"><span data-stu-id="ecc0d-118">Install the NUnit project template</span></span>

<span data-ttu-id="ecc0d-119">必須安裝 NUnit 專案範本，才可建立測試專案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="ecc0d-120">這項作業在您想要建立新的 NUnit 專案之每部開發人員電腦上，只需執行一次即可。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="ecc0d-121">執行 [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) 以安裝 NUnit 範本。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="ecc0d-122">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="ecc0d-122">Creating the test project</span></span>

<span data-ttu-id="ecc0d-123">接著，建立 *MathService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="ecc0d-124">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="ecc0d-125">將 *MathService.Tests* 目錄設定為目前的目錄，然後使用 [`dotnet new nunit -lang F#`](../tools/dotnet-new.md) 建立新專案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ecc0d-126">如此會建立將 NUnit 用作為測試架構的測試專案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="ecc0d-127">產生的範本會在 *MathServiceTests.fsproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="ecc0d-128">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ecc0d-129">上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="ecc0d-130">現在，將 `MathService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="ecc0d-131">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="ecc0d-132">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-132">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="ecc0d-133">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-133">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="ecc0d-134">執行 *unit-testing-with-fsharp* 目錄中的 [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="ecc0d-135">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="ecc0d-135">Creating the first test</span></span>

<span data-ttu-id="ecc0d-136">TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="ecc0d-137">開啟 *Tests.fs* 並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-137">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="ecc0d-138">`[<TestFixture>]` 屬性表示包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="ecc0d-139">`[<Test>]` 屬性表示由測試執行器執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="ecc0d-140">從 *unit-testing-with-fsharp* 目錄，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ecc0d-141">NUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ecc0d-142">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ecc0d-143">這兩個測試會顯示最基本的成功和失敗測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="ecc0d-144">`My test` 成功，而 `Fail every time` 失敗。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="ecc0d-145">現在，針對 `squaresOfOdds` 方法建立測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-145">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="ecc0d-146">`squaresOfOdds` 方法會傳回屬於輸入序列一部分的所有奇數整數值平方序列。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-146">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="ecc0d-147">您能以反覆方式建立會驗證功能的測試，而不需要嘗試一次撰寫所有那些函式。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="ecc0d-148">將每個測試設定為通過表示為方法建立必要功能。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="ecc0d-149">我們所能撰寫的最簡單測試是呼叫 `squaresOfOdds` 並傳遞所有偶數，其中結果應該是空整數序列。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-149">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="ecc0d-150">該測試如下：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ecc0d-151">請注意，`expected` 序列已被轉換為清單。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="ecc0d-152">NUnit 架構依賴數個標準 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="ecc0d-153">該相依性表示您的公用介面與預期結果支援 <xref:System.Collections.ICollection>，而非 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="ecc0d-154">當您執行該測試時，您會看到您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="ecc0d-155">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="ecc0d-156">在可運作的 `Mathservice` 類別中撰寫最簡單的程式碼以進行此測試：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="ecc0d-157">在 *unit-testing-with-fsharp* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ecc0d-158">`dotnet test` 命令會依序執行 `MathService` 專案和 `MathService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="ecc0d-159">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ecc0d-160">測試通過。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="ecc0d-161">完成需求</span><span class="sxs-lookup"><span data-stu-id="ecc0d-161">Completing the requirements</span></span>

<span data-ttu-id="ecc0d-162">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ecc0d-163">下一個簡單案例可搭配所具有的唯一奇數是 `1` 的序列運作。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="ecc0d-164">數字 1 比較簡單，因為 1 的平方是 1。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="ecc0d-165">該下一個測試如下：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ecc0d-166">執行 `dotnet test` 會使得新測試失敗。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="ecc0d-167">您必須更新 `squaresOfOdds` 方法以處理此新測試。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-167">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="ecc0d-168">您必須將所有偶數從序列中篩選出來，以使此測試通過。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="ecc0d-169">您可以透過撰寫小型篩選函式並使用 `Seq.filter` 來完成此動作：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="ecc0d-170">請注意對 `Seq.toList` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="ecc0d-171">那會建立清單，該清單會實作 <xref:System.Collections.ICollection> 介面。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="ecc0d-172">還有一個步驟必須執行：計算每個奇數的平方。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="ecc0d-173">透過撰寫新測試以開始：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ecc0d-174">您可以透過將已篩選的序列以管線方式傳遞到對應作業，以計算每個奇數的平方，來修正測試：</span><span class="sxs-lookup"><span data-stu-id="ecc0d-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="ecc0d-175">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="ecc0d-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ecc0d-176">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ecc0d-177">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="ecc0d-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
