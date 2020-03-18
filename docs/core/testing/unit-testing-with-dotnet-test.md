---
title: 使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試
description: 透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240892"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="4ad60-103">使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試</span><span class="sxs-lookup"><span data-stu-id="4ad60-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="4ad60-104">本教程演示如何構建包含單元測試專案和原始程式碼專案的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="4ad60-105">要使用預構建的解決方案按照本教程進行操作，[請查看或下載示例代碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="4ad60-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="4ad60-106">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="4ad60-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="4ad60-107">建立方案</span><span class="sxs-lookup"><span data-stu-id="4ad60-107">Create the solution</span></span>

<span data-ttu-id="4ad60-108">在本節中，將創建包含源和測試專案的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="4ad60-109">已完成的解決方案具有以下目錄結構：</span><span class="sxs-lookup"><span data-stu-id="4ad60-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="4ad60-110">以下說明提供了創建測試解決方案的步驟。</span><span class="sxs-lookup"><span data-stu-id="4ad60-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="4ad60-111">請參閱[命令以創建測試解決方案](#create-test-cmd)，以便一步創建測試解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="4ad60-112">開啟 Shell 視窗。</span><span class="sxs-lookup"><span data-stu-id="4ad60-112">Open a shell window.</span></span>
* <span data-ttu-id="4ad60-113">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4ad60-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="4ad60-114">該[`dotnet new sln`](../tools/dotnet-new.md)命令在*單元測試-使用點-測試*目錄中創建新的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="4ad60-115">將目錄更改為*單元測試使用點網路測試*資料夾。</span><span class="sxs-lookup"><span data-stu-id="4ad60-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="4ad60-116">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4ad60-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="4ad60-117">該[`dotnet new classlib`](../tools/dotnet-new.md)命令在*PrimeService*資料夾中創建新的類庫專案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="4ad60-118">新的類庫將包含要測試的代碼。</span><span class="sxs-lookup"><span data-stu-id="4ad60-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="4ad60-119">將 *Class1.cs* 重新命名為 *PrimeService.cs*。</span><span class="sxs-lookup"><span data-stu-id="4ad60-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="4ad60-120">將*PrimeService.cs*中的代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="4ad60-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* <span data-ttu-id="4ad60-121">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="4ad60-121">The preceding code:</span></span>
  * <span data-ttu-id="4ad60-122">引發帶有<xref:System.NotImplementedException>消息的 ，指示其未實現。</span><span class="sxs-lookup"><span data-stu-id="4ad60-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="4ad60-123">在本教程的後面部分更新。</span><span class="sxs-lookup"><span data-stu-id="4ad60-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="4ad60-124">在*單元測試使用點-測試*目錄中，運行以下命令將類庫專案添加到解決方案：</span><span class="sxs-lookup"><span data-stu-id="4ad60-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="4ad60-125">通過運行以下命令創建*PrimeService.測試*專案：</span><span class="sxs-lookup"><span data-stu-id="4ad60-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="4ad60-126">上述命令會：</span><span class="sxs-lookup"><span data-stu-id="4ad60-126">The preceding command:</span></span>
  * <span data-ttu-id="4ad60-127">在*PrimeService.測試*目錄中創建*PrimeService.* 測試專案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="4ad60-128">測試專案使用[xUnit](https://xunit.github.io/)作為測試庫。</span><span class="sxs-lookup"><span data-stu-id="4ad60-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="4ad60-129">通過將以下`<PackageReference />`元素添加到專案檔案來配置測試流道：</span><span class="sxs-lookup"><span data-stu-id="4ad60-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="4ad60-130">"微軟.NET.Test.Sdk"</span><span class="sxs-lookup"><span data-stu-id="4ad60-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="4ad60-131">"xunit"</span><span class="sxs-lookup"><span data-stu-id="4ad60-131">"xunit"</span></span>
    * <span data-ttu-id="4ad60-132">"xunit.runner.Visualstudio"</span><span class="sxs-lookup"><span data-stu-id="4ad60-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="4ad60-133">通過運行以下命令將測試專案添加到解決方案檔：</span><span class="sxs-lookup"><span data-stu-id="4ad60-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="4ad60-134">將`PrimeService`類庫作為依賴項添加到*PrimeService.測試*專案：</span><span class="sxs-lookup"><span data-stu-id="4ad60-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="4ad60-135">創建解決方案的命令</span><span class="sxs-lookup"><span data-stu-id="4ad60-135">Commands to create the solution</span></span>

<span data-ttu-id="4ad60-136">本節匯總上一節中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="4ad60-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="4ad60-137">如果您已完成上一節中的步驟，請跳過此部分。</span><span class="sxs-lookup"><span data-stu-id="4ad60-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="4ad60-138">以下命令在視窗電腦上創建測試解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ad60-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="4ad60-139">對於 macOS 和 Unix，將`ren`命令更新到`ren`的作業系統版本以重命名檔：</span><span class="sxs-lookup"><span data-stu-id="4ad60-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="4ad60-140">按照上一節中有關"用以下代碼替換*PrimeService.cs*代碼"的說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="4ad60-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="4ad60-141">創建測試</span><span class="sxs-lookup"><span data-stu-id="4ad60-141">Create a test</span></span>

<span data-ttu-id="4ad60-142">測試驅動開發 （TDD） 中的一種常用方法是在實現目標代碼之前編寫測試。</span><span class="sxs-lookup"><span data-stu-id="4ad60-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="4ad60-143">本教程使用 TDD 方法。</span><span class="sxs-lookup"><span data-stu-id="4ad60-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="4ad60-144">該方法`IsPrime`是可調用的，但不可實現。</span><span class="sxs-lookup"><span data-stu-id="4ad60-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="4ad60-145">測試調用`IsPrime`失敗。</span><span class="sxs-lookup"><span data-stu-id="4ad60-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="4ad60-146">使用 TDD 時，將編寫已知失敗測試。</span><span class="sxs-lookup"><span data-stu-id="4ad60-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="4ad60-147">更新目標代碼以使測試通過。</span><span class="sxs-lookup"><span data-stu-id="4ad60-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="4ad60-148">您繼續重複此方法，編寫失敗的測試，然後更新目標代碼以通過。</span><span class="sxs-lookup"><span data-stu-id="4ad60-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="4ad60-149">更新*PrimeService.測試*專案：</span><span class="sxs-lookup"><span data-stu-id="4ad60-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="4ad60-150">刪除*主要服務.測試/單元測試1.cs*。</span><span class="sxs-lookup"><span data-stu-id="4ad60-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="4ad60-151">創建*PrimeService.測試/PrimeService_IsPrimeShould.cs*檔。</span><span class="sxs-lookup"><span data-stu-id="4ad60-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="4ad60-152">將*PrimeService_IsPrimeShould.cs*中的代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="4ad60-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="4ad60-153">該`[Fact]`屬性聲明由測試回合程式運行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="4ad60-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="4ad60-154">從*PrimeService.測試*資料夾，運行`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="4ad60-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="4ad60-155">[dotnet 測試](../tools/dotnet-test.md)命令同時生成兩個專案並運行測試。</span><span class="sxs-lookup"><span data-stu-id="4ad60-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="4ad60-156">xUnit 測試回合套裝程式含運行測試的程式進入點。</span><span class="sxs-lookup"><span data-stu-id="4ad60-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="4ad60-157">`dotnet test`使用單元測試專案啟動測試回合程式。</span><span class="sxs-lookup"><span data-stu-id="4ad60-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="4ad60-158">測試失敗，因為`IsPrime`尚未實現。</span><span class="sxs-lookup"><span data-stu-id="4ad60-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="4ad60-159">使用 TDD 方法，只編寫足夠的代碼，以便通過此測試。</span><span class="sxs-lookup"><span data-stu-id="4ad60-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="4ad60-160">使用`IsPrime`以下代碼進行更新：</span><span class="sxs-lookup"><span data-stu-id="4ad60-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="4ad60-161">執行 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="4ad60-161">Run `dotnet test`.</span></span> <span data-ttu-id="4ad60-162">測試會成功。</span><span class="sxs-lookup"><span data-stu-id="4ad60-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="4ad60-163">添加更多測試</span><span class="sxs-lookup"><span data-stu-id="4ad60-163">Add more tests</span></span>

<span data-ttu-id="4ad60-164">添加 0 和 -1 的質數測試。</span><span class="sxs-lookup"><span data-stu-id="4ad60-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="4ad60-165">您可以複製前面的測試並將以下代碼更改為使用 0 和 -1：</span><span class="sxs-lookup"><span data-stu-id="4ad60-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="4ad60-166">當只有參數更改時複製測試代碼會導致代碼重複和測試膨脹。</span><span class="sxs-lookup"><span data-stu-id="4ad60-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="4ad60-167">以下 xUnit 屬性允許編寫一組類似的測試：</span><span class="sxs-lookup"><span data-stu-id="4ad60-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="4ad60-168">`[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。</span><span class="sxs-lookup"><span data-stu-id="4ad60-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="4ad60-169">`[InlineData]` 屬性會指定這些輸入的值。</span><span class="sxs-lookup"><span data-stu-id="4ad60-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="4ad60-170">與其創建新測試，不如應用前面的 xUnit 屬性來創建單個理論。</span><span class="sxs-lookup"><span data-stu-id="4ad60-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="4ad60-171">將下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4ad60-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="4ad60-172">取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4ad60-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="4ad60-173">在前面的代碼中，`[Theory]`並`[InlineData]`啟用測試多個值小於兩個。</span><span class="sxs-lookup"><span data-stu-id="4ad60-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="4ad60-174">二是最小的質數。</span><span class="sxs-lookup"><span data-stu-id="4ad60-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="4ad60-175">運行`dotnet test`，兩個測試失敗。</span><span class="sxs-lookup"><span data-stu-id="4ad60-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="4ad60-176">要使所有測試都通過，`IsPrime`請使用以下代碼更新該方法：</span><span class="sxs-lookup"><span data-stu-id="4ad60-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="4ad60-177">按照 TDD 方法，添加更多失敗的測試，然後更新目標代碼。</span><span class="sxs-lookup"><span data-stu-id="4ad60-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="4ad60-178">請參閱[測試的已完成版本](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[庫的完整實現](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。</span><span class="sxs-lookup"><span data-stu-id="4ad60-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="4ad60-179">完整的`IsPrime`方法不是測試原始性的有效演算法。</span><span class="sxs-lookup"><span data-stu-id="4ad60-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4ad60-180">其他資源</span><span class="sxs-lookup"><span data-stu-id="4ad60-180">Additional resources</span></span>

- [<span data-ttu-id="4ad60-181">xUnit.net 官方網站</span><span class="sxs-lookup"><span data-stu-id="4ad60-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="4ad60-182">測試 ASP.NET Core 中的控制器邏輯</span><span class="sxs-lookup"><span data-stu-id="4ad60-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
