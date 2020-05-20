---
title: 使用 dotnet test 與 xUnit 為 .NET Core 中的 Visual Basic 進行單元測試
description: 透過逐步使用 dotnet test 和 xUnit 建置範例 Visual Basic 方案的互動式體驗，了解 .NET Core 中的單元測試概念。
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: ed1291a980f9a39284525877bab8d0a93389fbd0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702953"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="19c23-103">使用 dotnet test 與 xUnit 為 Visual Basic .NET Core 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="19c23-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="19c23-104">本教學課程說明如何建立包含單元測試專案和程式庫專案的方案。</span><span class="sxs-lookup"><span data-stu-id="19c23-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="19c23-105">若要依照教學課程使用預先建立的解決方案，請[參閱或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="19c23-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="19c23-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="19c23-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="19c23-107">建立方案</span><span class="sxs-lookup"><span data-stu-id="19c23-107">Create the solution</span></span>

<span data-ttu-id="19c23-108">在本節中，會建立包含來源和測試專案的方案。</span><span class="sxs-lookup"><span data-stu-id="19c23-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="19c23-109">完成的解決方案具有下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="19c23-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="19c23-110">下列指示提供建立測試解決方案的步驟。</span><span class="sxs-lookup"><span data-stu-id="19c23-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="19c23-111">如需在一個步驟中建立測試解決方案的指示，請參閱[建立測試方案的命令](#create-test-cmd)。</span><span class="sxs-lookup"><span data-stu-id="19c23-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="19c23-112">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="19c23-112">Open a shell window.</span></span>
* <span data-ttu-id="19c23-113">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="19c23-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="19c23-114">此 [`dotnet new sln`](../tools/dotnet-new.md) 命令會在*單元測試-使用-dotnet-測試*目錄中建立新的解決方案。</span><span class="sxs-lookup"><span data-stu-id="19c23-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="19c23-115">將目錄變更為*單元測試-使用-dotnet-test*資料夾。</span><span class="sxs-lookup"><span data-stu-id="19c23-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="19c23-116">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="19c23-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="19c23-117">[`dotnet new classlib`](../tools/dotnet-new.md)命令會在*PrimeService*資料夾中建立新的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="19c23-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="19c23-118">新的類別庫將包含要測試的程式碼。</span><span class="sxs-lookup"><span data-stu-id="19c23-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="19c23-119">將*Class1* PrimeService 重新命名為 *.vb*。</span><span class="sxs-lookup"><span data-stu-id="19c23-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="19c23-120">將*PrimeService*中的程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19c23-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="19c23-121">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="19c23-121">The preceding code:</span></span>
  * <span data-ttu-id="19c23-122">擲回 <xref:System.NotImplementedException> 並顯示訊息，指出未執行。</span><span class="sxs-lookup"><span data-stu-id="19c23-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="19c23-123">稍後會在本教學課程中更新。</span><span class="sxs-lookup"><span data-stu-id="19c23-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="19c23-124">在 [*單元測試-使用-dotnet-測試*目錄] 中，執行下列命令以將類別庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="19c23-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="19c23-125">執行下列命令來建立*PrimeService*專案：</span><span class="sxs-lookup"><span data-stu-id="19c23-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="19c23-126">上述命令會：</span><span class="sxs-lookup"><span data-stu-id="19c23-126">The preceding command:</span></span>
  * <span data-ttu-id="19c23-127">在*PrimeService. 測試*目錄中建立*PrimeService*專案。</span><span class="sxs-lookup"><span data-stu-id="19c23-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="19c23-128">測試專案使用[xUnit](https://xunit.net/)做為測試程式庫。</span><span class="sxs-lookup"><span data-stu-id="19c23-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="19c23-129">將下列元素新增至專案檔， `<PackageReference />` 以設定測試執行器：</span><span class="sxs-lookup"><span data-stu-id="19c23-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="19c23-130">「Microsoft .NET. Test Sdk」</span><span class="sxs-lookup"><span data-stu-id="19c23-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="19c23-131">xunit</span><span class="sxs-lookup"><span data-stu-id="19c23-131">"xunit"</span></span>
    * <span data-ttu-id="19c23-132">"xunit. visualstudio"</span><span class="sxs-lookup"><span data-stu-id="19c23-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="19c23-133">執行下列命令，將測試專案新增至方案檔：</span><span class="sxs-lookup"><span data-stu-id="19c23-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="19c23-134">將 `PrimeService` 類別庫新增為*PrimeService*專案的相依性：</span><span class="sxs-lookup"><span data-stu-id="19c23-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="19c23-135">用來建立解決方案的命令</span><span class="sxs-lookup"><span data-stu-id="19c23-135">Commands to create the solution</span></span>

<span data-ttu-id="19c23-136">本節將摘要上一節中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="19c23-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="19c23-137">如果您已完成上一節中的步驟，請略過本節。</span><span class="sxs-lookup"><span data-stu-id="19c23-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="19c23-138">下列命令會在 windows 電腦上建立測試方案。</span><span class="sxs-lookup"><span data-stu-id="19c23-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="19c23-139">針對 macOS 和 Unix，請將 `ren` 命令更新為的 OS 版本， `ren` 以重新命名檔案：</span><span class="sxs-lookup"><span data-stu-id="19c23-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="19c23-140">請遵循上一節中「使用下列程式碼取代*PrimeService*中的程式碼」的指示。</span><span class="sxs-lookup"><span data-stu-id="19c23-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="19c23-141">建立測試</span><span class="sxs-lookup"><span data-stu-id="19c23-141">Create a test</span></span>

<span data-ttu-id="19c23-142">測試導向開發（TDD）中常見的方法是在執行目的程式代碼之前撰寫測試。</span><span class="sxs-lookup"><span data-stu-id="19c23-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="19c23-143">本教學課程使用 TDD 方法。</span><span class="sxs-lookup"><span data-stu-id="19c23-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="19c23-144">`IsPrime`方法是可呼叫的，但未實作為。</span><span class="sxs-lookup"><span data-stu-id="19c23-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="19c23-145">測試呼叫 `IsPrime` 失敗。</span><span class="sxs-lookup"><span data-stu-id="19c23-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="19c23-146">使用 TDD 時，會寫入已知失敗的測試。</span><span class="sxs-lookup"><span data-stu-id="19c23-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="19c23-147">更新目的程式代碼以進行測試。</span><span class="sxs-lookup"><span data-stu-id="19c23-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="19c23-148">您可以繼續重複此方法，撰寫失敗的測試，然後更新要傳遞的目的程式代碼。</span><span class="sxs-lookup"><span data-stu-id="19c23-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="19c23-149">更新*PrimeService*專案：</span><span class="sxs-lookup"><span data-stu-id="19c23-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="19c23-150">刪除*PrimeService/unittest1.cpp*。</span><span class="sxs-lookup"><span data-stu-id="19c23-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="19c23-151">建立*PrimeService 測試/PrimeService_IsPrimeShould .vb*檔案。</span><span class="sxs-lookup"><span data-stu-id="19c23-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="19c23-152">使用下列程式碼取代*PrimeService_IsPrimeShould .vb*中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="19c23-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="19c23-153">`[Fact]`屬性會宣告測試執行器所執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="19c23-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="19c23-154">從 [ *PrimeService* ] 資料夾中，執行 `dotnet test` 。</span><span class="sxs-lookup"><span data-stu-id="19c23-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="19c23-155">[Dotnet test](../tools/dotnet-test.md)命令會建立這兩個專案，並執行測試。</span><span class="sxs-lookup"><span data-stu-id="19c23-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="19c23-156">XUnit 測試執行器包含執行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="19c23-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="19c23-157">`dotnet test`使用單元測試專案啟動測試執行器。</span><span class="sxs-lookup"><span data-stu-id="19c23-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="19c23-158">測試失敗，因為 `IsPrime` 尚未執行。</span><span class="sxs-lookup"><span data-stu-id="19c23-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="19c23-159">使用 TDD 方法，只撰寫足夠的程式碼，讓此測試通過。</span><span class="sxs-lookup"><span data-stu-id="19c23-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="19c23-160">`IsPrime`使用下列程式碼更新：</span><span class="sxs-lookup"><span data-stu-id="19c23-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="19c23-161">執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="19c23-161">Run `dotnet test`.</span></span> <span data-ttu-id="19c23-162">測試會成功。</span><span class="sxs-lookup"><span data-stu-id="19c23-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="19c23-163">新增更多測試</span><span class="sxs-lookup"><span data-stu-id="19c23-163">Add more tests</span></span>

<span data-ttu-id="19c23-164">為0和-1 加入質數測試。</span><span class="sxs-lookup"><span data-stu-id="19c23-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="19c23-165">您可以複製上述測試，並將下列程式碼變更為使用0和-1：</span><span class="sxs-lookup"><span data-stu-id="19c23-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="19c23-166">只有在參數變更時複製測試程式碼，會導致程式碼重複和測試膨脹。</span><span class="sxs-lookup"><span data-stu-id="19c23-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="19c23-167">下列 xUnit 屬性可讓您撰寫類似測試的套件：</span><span class="sxs-lookup"><span data-stu-id="19c23-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="19c23-168">`[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="19c23-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="19c23-169">`[InlineData]` 屬性會指定這些輸入的值。</span><span class="sxs-lookup"><span data-stu-id="19c23-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="19c23-170">不需要建立新的測試，而是套用上述的 xUnit 屬性來建立單一的理論。</span><span class="sxs-lookup"><span data-stu-id="19c23-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="19c23-171">將下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19c23-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="19c23-172">取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19c23-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="19c23-173">在上述程式碼中， `[Theory]` 和可 `[InlineData]` 讓測試數個小於二的值。</span><span class="sxs-lookup"><span data-stu-id="19c23-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="19c23-174">兩個是最小的質數。</span><span class="sxs-lookup"><span data-stu-id="19c23-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="19c23-175">執行時 `dotnet test` ，兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="19c23-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="19c23-176">若要讓所有測試都通過，請 `IsPrime` 使用下列程式碼更新方法：</span><span class="sxs-lookup"><span data-stu-id="19c23-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="19c23-177">遵循 TDD 方法，新增更多失敗的測試，然後更新目的程式代碼。</span><span class="sxs-lookup"><span data-stu-id="19c23-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="19c23-178">請參閱[測試的完成版本](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb)和[完整的程式庫執行](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb)。</span><span class="sxs-lookup"><span data-stu-id="19c23-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="19c23-179">Completed `IsPrime` 方法不是用來測試 primality 的有效演算法。</span><span class="sxs-lookup"><span data-stu-id="19c23-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="19c23-180">其他資源</span><span class="sxs-lookup"><span data-stu-id="19c23-180">Additional resources</span></span>

- [<span data-ttu-id="19c23-181">xUnit.net 官方網站</span><span class="sxs-lookup"><span data-stu-id="19c23-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="19c23-182">測試 ASP.NET Core 中的控制器邏輯</span><span class="sxs-lookup"><span data-stu-id="19c23-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
