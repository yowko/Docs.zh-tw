---
title: 使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 進行單元測試
description: 使用 dotnet test 與 NUnit 逐步建置解決方案範例的互動式體驗，了解 .NET Core 中 F# 的單元測試概念。
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: cf313f8197280bdbb943c12ef0c7a29284ec01a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849771"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="3e028-103">使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="3e028-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="3e028-104">本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。</span><span class="sxs-lookup"><span data-stu-id="3e028-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3e028-105">如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/)。</span><span class="sxs-lookup"><span data-stu-id="3e028-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="3e028-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="3e028-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="3e028-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="3e028-107">Prerequisites</span></span>

- <span data-ttu-id="3e028-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3e028-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="3e028-109">您選擇的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="3e028-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3e028-110">建立來源專案</span><span class="sxs-lookup"><span data-stu-id="3e028-110">Creating the source project</span></span>

<span data-ttu-id="3e028-111">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="3e028-111">Open a shell window.</span></span> <span data-ttu-id="3e028-112">建立名為 *unit-testing-with-fsharp* 的目錄來放置方案。</span><span class="sxs-lookup"><span data-stu-id="3e028-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="3e028-113">在此新目錄中，執行下列命令以針對類別庫與測試專案建立新方案檔：</span><span class="sxs-lookup"><span data-stu-id="3e028-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="3e028-114">接下來，建立 *MathService* 目錄。</span><span class="sxs-lookup"><span data-stu-id="3e028-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="3e028-115">下列大綱顯示到目前為止的目錄與檔案結構：</span><span class="sxs-lookup"><span data-stu-id="3e028-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="3e028-116">將 *MathService* 設為目前的目錄，然後執行下列命令以建立來源專案：</span><span class="sxs-lookup"><span data-stu-id="3e028-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang F#
```

<span data-ttu-id="3e028-117">您建立數學服務的失敗實作：</span><span class="sxs-lookup"><span data-stu-id="3e028-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="3e028-118">將目錄變更回 *unit-testing-with-fsharp* 目錄。</span><span class="sxs-lookup"><span data-stu-id="3e028-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="3e028-119">執行下列命令，將類別庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="3e028-119">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="3e028-120">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="3e028-120">Creating the test project</span></span>

<span data-ttu-id="3e028-121">接著，建立 *MathService.Tests* 目錄。</span><span class="sxs-lookup"><span data-stu-id="3e028-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="3e028-122">下列大綱顯示目錄結構：</span><span class="sxs-lookup"><span data-stu-id="3e028-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="3e028-123">將 *MathService.Tests* 目錄設為目前的目錄，然後使用下列命令建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="3e028-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang F#
```

<span data-ttu-id="3e028-124">如此會建立將 NUnit 用作為測試架構的測試專案。</span><span class="sxs-lookup"><span data-stu-id="3e028-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="3e028-125">產生的範本會在 *MathServiceTests.fsproj* 中設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="3e028-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="3e028-126">測試專案需要其他套件來建立和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3e028-127">上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3e028-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="3e028-128">現在，將 `MathService` 類別庫新增為專案的另一個相依性。</span><span class="sxs-lookup"><span data-stu-id="3e028-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="3e028-129">使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="3e028-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="3e028-130">您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)中看到完整檔案。</span><span class="sxs-lookup"><span data-stu-id="3e028-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="3e028-131">您有下列最終方案配置：</span><span class="sxs-lookup"><span data-stu-id="3e028-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="3e028-132">在 *unit-testing-with-fsharp* 目錄中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3e028-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="3e028-133">建立第一個測試</span><span class="sxs-lookup"><span data-stu-id="3e028-133">Creating the first test</span></span>

<span data-ttu-id="3e028-134">您會撰寫一個失敗測試，讓它通過，然後重複此程序。</span><span class="sxs-lookup"><span data-stu-id="3e028-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="3e028-135">開啟 *UnitTest1.fs* 並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3e028-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="3e028-136">`[<TestFixture>]` 屬性表示包含測試的類別。</span><span class="sxs-lookup"><span data-stu-id="3e028-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="3e028-137">`[<Test>]` 屬性表示由測試執行器執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="3e028-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="3e028-138">從 *unit-testing-with-fsharp* 目錄，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3e028-139">NUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="3e028-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3e028-140">`dotnet test` 會使用您建立的單元測試專案來開始測試執行器。</span><span class="sxs-lookup"><span data-stu-id="3e028-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3e028-141">這兩個測試會顯示最基本的成功和失敗測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="3e028-142">`My test` 成功，而 `Fail every time` 失敗。</span><span class="sxs-lookup"><span data-stu-id="3e028-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="3e028-143">現在，針對 `squaresOfOdds` 方法建立測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="3e028-144">`squaresOfOdds` 方法會傳回屬於輸入序列一部分的所有奇數整數值平方序列。</span><span class="sxs-lookup"><span data-stu-id="3e028-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="3e028-145">您能以反覆方式建立會驗證功能的測試，而不需要嘗試一次撰寫所有那些函式。</span><span class="sxs-lookup"><span data-stu-id="3e028-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="3e028-146">將每個測試設定為通過表示為方法建立必要功能。</span><span class="sxs-lookup"><span data-stu-id="3e028-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="3e028-147">我們所能撰寫的最簡單測試是呼叫 `squaresOfOdds` 並傳遞所有偶數，其中結果應該是空整數序列。</span><span class="sxs-lookup"><span data-stu-id="3e028-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="3e028-148">該測試如下：</span><span class="sxs-lookup"><span data-stu-id="3e028-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3e028-149">請注意，`expected` 序列已被轉換為清單。</span><span class="sxs-lookup"><span data-stu-id="3e028-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="3e028-150">NUnit 架構依賴數個標準 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="3e028-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="3e028-151">該相依性表示您的公用介面與預期結果支援 <xref:System.Collections.ICollection>，而非 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="3e028-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="3e028-152">當您執行該測試時，您會看到您的測試失敗。</span><span class="sxs-lookup"><span data-stu-id="3e028-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="3e028-153">您尚未建立實作。</span><span class="sxs-lookup"><span data-stu-id="3e028-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="3e028-154">透過在可運作之 MathService 專案的 *Library.fs* 類別中撰寫最簡單的程式碼，來使此測試通過：</span><span class="sxs-lookup"><span data-stu-id="3e028-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="3e028-155">在 *unit-testing-with-fsharp* 目錄中，重新執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="3e028-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3e028-156">`dotnet test` 命令會依序執行 `MathService` 專案和 `MathService.Tests` 專案的建置。</span><span class="sxs-lookup"><span data-stu-id="3e028-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="3e028-157">建置這兩個專案之後，它會執行您的測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="3e028-158">現在通過兩個測試了。</span><span class="sxs-lookup"><span data-stu-id="3e028-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="3e028-159">完成需求</span><span class="sxs-lookup"><span data-stu-id="3e028-159">Completing the requirements</span></span>

<span data-ttu-id="3e028-160">現在，您已經讓一個測試順利通過，您可以撰寫更多測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3e028-161">下一個簡單案例可搭配所具有的唯一奇數是 `1` 的序列運作。</span><span class="sxs-lookup"><span data-stu-id="3e028-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="3e028-162">數字 1 比較簡單，因為 1 的平方是 1。</span><span class="sxs-lookup"><span data-stu-id="3e028-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="3e028-163">該下一個測試如下：</span><span class="sxs-lookup"><span data-stu-id="3e028-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3e028-164">執行 `dotnet test` 會使得新測試失敗。</span><span class="sxs-lookup"><span data-stu-id="3e028-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="3e028-165">您必須更新 `squaresOfOdds` 方法以處理此新測試。</span><span class="sxs-lookup"><span data-stu-id="3e028-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="3e028-166">您必須將所有偶數從序列中篩選出來，以使此測試通過。</span><span class="sxs-lookup"><span data-stu-id="3e028-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="3e028-167">您可以透過撰寫小型篩選函式並使用 `Seq.filter` 來完成此動作：</span><span class="sxs-lookup"><span data-stu-id="3e028-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="3e028-168">請注意對 `Seq.toList` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3e028-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="3e028-169">那會建立清單，該清單會實作 <xref:System.Collections.ICollection> 介面。</span><span class="sxs-lookup"><span data-stu-id="3e028-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="3e028-170">還有一個步驟必須執行：計算每個奇數的平方。</span><span class="sxs-lookup"><span data-stu-id="3e028-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="3e028-171">透過撰寫新測試以開始：</span><span class="sxs-lookup"><span data-stu-id="3e028-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3e028-172">您可以透過將已篩選的序列以管線方式傳遞到對應作業，以計算每個奇數的平方，來修正測試：</span><span class="sxs-lookup"><span data-stu-id="3e028-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="3e028-173">您已建置好小型的程式庫和該程式庫的一組單元測試，</span><span class="sxs-lookup"><span data-stu-id="3e028-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3e028-174">您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="3e028-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3e028-175">您已集中大部分的時間與精力以解決應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="3e028-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
