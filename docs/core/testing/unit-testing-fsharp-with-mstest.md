---
title: 使用 dotnet test 與 MSTest 為 .NET Core 中的 F# 進行單元測試
description: 透過逐步使用 dotnet test 和 MSTest 建置範例方案的互動式體驗，了解 .NET Core 中 F# 的單元測試概念。
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 3b93f4ed21d9d5eccf1dd02f253e7456aec02807
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626472"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="7c6b3-103">使用 dotnet test 與 MSTest 為 .NET Core 中的 F# 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="7c6b3-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="7c6b3-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="7c6b3-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/)。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="7c6b3-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="7c6b3-107">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="7c6b3-107">Creating the source project</span></span>

<span data-ttu-id="7c6b3-108">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-108">Open a shell window.</span></span> <span data-ttu-id="7c6b3-109">建立名為 *unit-testing-with-fsharp* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="7c6b3-110">在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="7c6b3-111">這樣可讓您更輕鬆地管理類別庫與單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="7c6b3-112">在方案目錄中，建立 *MathService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="7c6b3-113">到目前為止，目錄與檔案結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="7c6b3-114">將 *MathService* 設定為目前的目錄，然後執行 [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) 以建立來源專案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="7c6b3-115">您建立會失敗的數學服務實作：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="7c6b3-116">將目錄變更回 *unit-testing-with-fsharp* 目錄。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="7c6b3-117">執行 [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="7c6b3-118">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="7c6b3-118">Creating the test project</span></span>

<span data-ttu-id="7c6b3-119">接著，建立 *MathService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="7c6b3-120">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="7c6b3-121">將 *MathService.Tests* 目錄設定為目前的目錄，然後使用 [`dotnet new mstest -lang F#`](../tools/dotnet-new.md) 建立新專案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="7c6b3-122">這會建立將 MStest 作為測試架構使用的測試專案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="7c6b3-123">產生的範本會在 *MathServiceTests.fsproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="7c6b3-124">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="7c6b3-125">上一個步驟中的 `dotnet new` 已新增 MSTest 和 MSTest 執行器。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="7c6b3-126">現在，將 `MathService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="7c6b3-127">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="7c6b3-128">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="7c6b3-129">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="7c6b3-130">執行 *unit-testing-with-fsharp* 目錄中的 [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="7c6b3-131">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="7c6b3-131">Creating the first test</span></span>

<span data-ttu-id="7c6b3-132">您會撰寫一個失敗測試，讓它通過，然後重複此程序。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="7c6b3-133">開啟 *Tests.fs* 並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="7c6b3-134">`[<TestClass>]` 屬性表示包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="7c6b3-135">`[<TestMethod>]` 屬性表示由測試執行器執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="7c6b3-136">從 *unit-testing-with-fsharp* 目錄，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="7c6b3-137">MSTest 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="7c6b3-138">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="7c6b3-139">這兩個測試會顯示最基本的成功和失敗測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="7c6b3-140">`My test` 成功，而 `Fail every time` 失敗。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="7c6b3-141">現在，針對 `squaresOfOdds` 方法建立測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="7c6b3-142">`squaresOfOdds` 方法會傳回屬於輸入序列一部分的所有奇數整數值平方清單。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="7c6b3-143">您能以反覆方式建立會驗證功能的測試，而不需要嘗試一次撰寫所有那些函式。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="7c6b3-144">將每個測試設定為通過表示為方法建立必要功能。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="7c6b3-145">我們所能撰寫的最簡單測試是呼叫 `squaresOfOdds` 並傳遞所有偶數，其中結果應該是空整數序列。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="7c6b3-146">該測試如下：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="7c6b3-147">請注意，`expected` 序列已被轉換為清單。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="7c6b3-148">MSTest 程式庫仰賴許多標準 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="7c6b3-149">該相依性表示您的公用介面與預期結果支援 <xref:System.Collections.ICollection>，而非 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="7c6b3-150">當您執行該測試時，您會看到您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="7c6b3-151">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="7c6b3-152">在可運作的 `Mathservice` 類別中撰寫最簡單的程式碼以讓此測試成功：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="7c6b3-153">在 *unit-testing-with-fsharp* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="7c6b3-154">`dotnet test` 命令會依序執行 `MathService` 專案和 `MathService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="7c6b3-155">建置這兩個專案之後，它將會執行此單一測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="7c6b3-156">測試通過。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="7c6b3-157">完成需求</span><span class="sxs-lookup"><span data-stu-id="7c6b3-157">Completing the requirements</span></span>

<span data-ttu-id="7c6b3-158">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="7c6b3-159">下一個簡單案例可搭配所具有的唯一奇數是 `1` 的序列運作。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="7c6b3-160">數字 1 比較簡單，因為 1 的平方是 1。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="7c6b3-161">該下一個測試如下：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="7c6b3-162">執行 `dotnet test` 會使得新測試失敗。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="7c6b3-163">您必須更新 `squaresOfOdds` 方法以處理此新測試。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="7c6b3-164">您必須將所有偶數從序列中篩選出來，以使此測試通過。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="7c6b3-165">您可以透過撰寫小型篩選函式並使用 `Seq.filter` 來完成此動作：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="7c6b3-166">請注意對 `Seq.toList` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="7c6b3-167">那會建立清單，該清單會實作 <xref:System.Collections.ICollection> 介面。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="7c6b3-168">還有一個步驟必須執行：計算每個奇數的平方。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="7c6b3-169">透過撰寫新測試以開始：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="7c6b3-170">您可以透過將已篩選的序列以管線方式傳遞到對應作業，以計算每個奇數的平方，來修正測試：</span><span class="sxs-lookup"><span data-stu-id="7c6b3-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="7c6b3-171">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="7c6b3-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="7c6b3-172">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="7c6b3-173">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="7c6b3-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
