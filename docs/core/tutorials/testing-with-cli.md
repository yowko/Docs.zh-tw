---
title: 使用 .NET CLI 組織和測試專案
description: 本教學課程說明如何從命令列組織和測試 .NET 專案。
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 93e8a6b8afd9f9405bf21488998a61c2e761bf1e
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512251"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a><span data-ttu-id="5496f-103">使用 .NET CLI 組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="5496f-103">Organizing and testing projects with the .NET CLI</span></span>

<span data-ttu-id="5496f-104">本教學課程會遵循 [教學課程：使用 Visual Studio Code 建立使用 .net 的主控台應用程式](with-visual-studio-code.md)，讓您超越建立簡單的主控台應用程式，以開發先進且妥善組織的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5496f-104">This tutorial follows [Tutorial: Create a console application with .NET using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="5496f-105">此教學課程在示範如何使用資料夾來組織您的程式碼之後，會示範如何使用 [xUnit](https://xunit.github.io/) 測試架構來擴充主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="5496f-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="5496f-106">使用資料夾來組織程式碼</span><span class="sxs-lookup"><span data-stu-id="5496f-106">Using folders to organize code</span></span>

<span data-ttu-id="5496f-107">如果您想要將新類型引入主控台應用程式，則可以將包含類型的檔案新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="5496f-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="5496f-108">例如，如果您將包含 `AccountInformation` 及 `MonthlyReportRecords` 類型的檔案新增至專案，則專案檔案結構會是平面，而且容易進行巡覽︰</span><span class="sxs-lookup"><span data-stu-id="5496f-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="5496f-109">不過，只有在專案規模相當小時，這才會運作良好。</span><span class="sxs-lookup"><span data-stu-id="5496f-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="5496f-110">您可以想像將 20 種類型新增至專案時，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="5496f-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="5496f-111">如果有多個可將專案根目錄弄亂的檔案，則絕對無法輕鬆地巡覽及維護專案。</span><span class="sxs-lookup"><span data-stu-id="5496f-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="5496f-112">若要組織專案，請建立新的資料夾，並將它命名為 *Models* 以保留類型檔案。</span><span class="sxs-lookup"><span data-stu-id="5496f-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="5496f-113">將類型檔案放入 *Models* 資料夾︰</span><span class="sxs-lookup"><span data-stu-id="5496f-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="5496f-114">您也可以輕鬆地巡覽及維護以邏輯方式將檔案群組到資料夾的專案。</span><span class="sxs-lookup"><span data-stu-id="5496f-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="5496f-115">在下一節中，您會建立具有資料夾及單元測試的更複雜範例。</span><span class="sxs-lookup"><span data-stu-id="5496f-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="5496f-116">使用 NewTypes Pets 範例進行組織及測試</span><span class="sxs-lookup"><span data-stu-id="5496f-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5496f-117">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5496f-117">Prerequisites</span></span>

* <span data-ttu-id="5496f-118">[.Net 5.0 SDK](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5496f-118">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="5496f-119">建置範例</span><span class="sxs-lookup"><span data-stu-id="5496f-119">Building the sample</span></span>

<span data-ttu-id="5496f-120">如需下列步驟，您可以遵循如何使用 [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) (NewTypes Pets 範例)，或建立自己的檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="5496f-120">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="5496f-121">類型會以邏輯方式組織成資料夾結構以允許稍後新增更多類型，而且測試也會以邏輯方式放在允許稍後新增更多測試的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5496f-121">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="5496f-122">這個範例包含 `Dog` 及 `Cat` 這兩種類型，並讓它們實作公用介面 `IPet`。</span><span class="sxs-lookup"><span data-stu-id="5496f-122">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="5496f-123">針對 `NewTypes` 專案，您的目標是將寵物相關類型組織到 *Pets* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5496f-123">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="5496f-124">如果稍後新增另一組類型 (例如，*WildAnimals*)，則會將它們放入 *Pets* 資料夾旁邊的 *NewTypes* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5496f-124">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="5496f-125">*WildAnimals* 資料夾可能會包含不是寵物之動物的類型，例如 `Squirrel` 及 `Rabbit` 類型。</span><span class="sxs-lookup"><span data-stu-id="5496f-125">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="5496f-126">因此，新增類型時，專案會井然有序。</span><span class="sxs-lookup"><span data-stu-id="5496f-126">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="5496f-127">使用所指出的檔案內容來建立下列資料夾結構︰</span><span class="sxs-lookup"><span data-stu-id="5496f-127">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="5496f-128">*IPet.cs*：</span><span class="sxs-lookup"><span data-stu-id="5496f-128">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="5496f-129">*Dog.cs*：</span><span class="sxs-lookup"><span data-stu-id="5496f-129">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="5496f-130">*Cat.cs*：</span><span class="sxs-lookup"><span data-stu-id="5496f-130">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="5496f-131">*Program.cs*：</span><span class="sxs-lookup"><span data-stu-id="5496f-131">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="5496f-132">*NewTypes.csproj*：</span><span class="sxs-lookup"><span data-stu-id="5496f-132">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="5496f-133">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="5496f-133">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5496f-134">取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5496f-134">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="5496f-135">選擇性練習︰您可以擴充此專案，以新增 `Bird` 這類寵物類型。</span><span class="sxs-lookup"><span data-stu-id="5496f-135">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="5496f-136">讓小鳥的 `TalkToOwner` 方法提供 `Tweet!` 給擁有者。</span><span class="sxs-lookup"><span data-stu-id="5496f-136">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="5496f-137">重新執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5496f-137">Run the app again.</span></span> <span data-ttu-id="5496f-138">輸出會包含 `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="5496f-138">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="5496f-139">測試範例</span><span class="sxs-lookup"><span data-stu-id="5496f-139">Testing the sample</span></span>

<span data-ttu-id="5496f-140">`NewTypes` 專案已經就緒，而且組織方式是將寵物相關類型保留在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5496f-140">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="5496f-141">接下來，建立測試專案，並開始撰寫具有 [xUnit](https://xunit.github.io/) 測試架構的測試。</span><span class="sxs-lookup"><span data-stu-id="5496f-141">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="5496f-142">單元測試可讓您自動檢查寵物類型的行為以確認它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="5496f-142">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="5496f-143">巡覽回到 *src* 資料夾，並建立內含 *NewTypesTests* 資料夾的 *test* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5496f-143">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="5496f-144">在命令提示字元中，從 *NewTypesTests* 資料夾執行 `dotnet new xunit`。</span><span class="sxs-lookup"><span data-stu-id="5496f-144">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="5496f-145">這會產生兩個檔案︰*NewTypesTests.csproj* 及 *UnitTest1.cs*。</span><span class="sxs-lookup"><span data-stu-id="5496f-145">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="5496f-146">測試專案目前無法測試 `NewTypes` 中的類型，並且需要 `NewTypes` 專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="5496f-146">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="5496f-147">若要加入專案參考，請使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 下列命令：</span><span class="sxs-lookup"><span data-stu-id="5496f-147">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="5496f-148">或者，您也可以選擇手動新增專案參考，方法是將 `<ItemGroup>` 節點新增至 *NewTypesTests.csproj* 檔案：</span><span class="sxs-lookup"><span data-stu-id="5496f-148">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="5496f-149">*NewTypesTests.csproj*：</span><span class="sxs-lookup"><span data-stu-id="5496f-149">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="5496f-150">*NewTypesTests.csproj* 檔案包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="5496f-150">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="5496f-151">`Microsoft.NET.Test.Sdk` (.NET 測試基礎結構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="5496f-151">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="5496f-152">`xunit` (xUnit 測試架構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="5496f-152">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="5496f-153">`xunit.runner.visualstudio` (測試執行器) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="5496f-153">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="5496f-154">`NewTypes` (要測試的程式碼) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="5496f-154">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="5496f-155">將 *UnitTest1.cs* 的名稱變更為 *PetTests.cs*，並將檔案中的程式碼取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="5496f-155">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="5496f-156">選擇性練習︰如果您稍早已將產生 `Tweet!` 的 `Bird` 類型新增至擁有者，請將測試方法新增至 PetTests.cs 檔案，並新增 `BirdTalkToOwnerReturnsTweet` 以確認 `TalkToOwner` 方法正確作用於 `Bird` 類型。</span><span class="sxs-lookup"><span data-stu-id="5496f-156">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="5496f-157">雖然您預期 `expected` 與 `actual` 值相等，但是具有 `Assert.NotEqual` 檢查的初始判斷提示指定這些值「不相等」。</span><span class="sxs-lookup"><span data-stu-id="5496f-157">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="5496f-158">一開始一律會讓測試失敗，以檢查測試邏輯。</span><span class="sxs-lookup"><span data-stu-id="5496f-158">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="5496f-159">在您確認測試失敗之後，調整判斷提示以允許測試通過。</span><span class="sxs-lookup"><span data-stu-id="5496f-159">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="5496f-160">下列顯示完整專案結構：</span><span class="sxs-lookup"><span data-stu-id="5496f-160">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="5496f-161">從 *test/NewTypesTests* 目錄開始。</span><span class="sxs-lookup"><span data-stu-id="5496f-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="5496f-162">使用命令執行測試 [`dotnet test`](../tools/dotnet-test.md) 。</span><span class="sxs-lookup"><span data-stu-id="5496f-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="5496f-163">這個命令會啟動專案檔中指定的測試執行器。</span><span class="sxs-lookup"><span data-stu-id="5496f-163">This command starts the test runner specified in the project file.</span></span>

<span data-ttu-id="5496f-164">如預期，測試會失敗，而且主控台會顯示下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="5496f-164">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="5496f-165">將您測試的判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`：</span><span class="sxs-lookup"><span data-stu-id="5496f-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="5496f-166">使用 `dotnet test` 命令重新執行測試，並取得下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="5496f-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="5496f-167">通過測試。</span><span class="sxs-lookup"><span data-stu-id="5496f-167">Testing passes.</span></span> <span data-ttu-id="5496f-168">與擁有者交談時，寵物類型的方法會傳回正確值。</span><span class="sxs-lookup"><span data-stu-id="5496f-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="5496f-169">您已了解使用 xUnit 來組織及測試專案的技術。</span><span class="sxs-lookup"><span data-stu-id="5496f-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="5496f-170">繼續使用這些技術，以將它們套用至您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="5496f-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="5496f-171">*祝各位編碼程式愉快！*</span><span class="sxs-lookup"><span data-stu-id="5496f-171">*Happy coding!*</span></span>
