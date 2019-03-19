---
title: 使用 .NET Core 命令列組織和測試專案
description: 此教學課程說明如何從命令列組織和測試 .NET Core 專案。
author: cartermp
ms.date: 09/10/2018
ms.custom: seodec18
ms.openlocfilehash: ffd15edc633142116089d206135eb16416eb14cb
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2019
ms.locfileid: "57845904"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="0fad2-103">使用 .NET Core 命令列組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="0fad2-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="0fad2-104">此教學課程遵循[使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core](using-with-xplat-cli.md)，讓您超越建立簡單主控台應用程式來開發進階且井然有序的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fad2-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="0fad2-105">此教學課程在示範如何使用資料夾來組織您的程式碼之後，會示範如何使用 [xUnit](https://xunit.github.io/) 測試架構來擴充主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fad2-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="0fad2-106">使用資料夾來組織程式碼</span><span class="sxs-lookup"><span data-stu-id="0fad2-106">Using folders to organize code</span></span>

<span data-ttu-id="0fad2-107">如果您想要將新類型引入主控台應用程式，則可以將包含類型的檔案新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fad2-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="0fad2-108">例如，如果您將包含 `AccountInformation` 及 `MonthlyReportRecords` 類型的檔案新增至專案，則專案檔案結構會是平面，而且容易進行巡覽︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="0fad2-109">不過，只有在專案規模相當小時，這才會運作良好。</span><span class="sxs-lookup"><span data-stu-id="0fad2-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="0fad2-110">您可以想像將 20 種類型新增至專案時，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="0fad2-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="0fad2-111">如果有多個可將專案根目錄弄亂的檔案，則絕對無法輕鬆地巡覽及維護專案。</span><span class="sxs-lookup"><span data-stu-id="0fad2-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="0fad2-112">若要組織專案，請建立新的資料夾，並將它命名為 *Models* 以保留類型檔案。</span><span class="sxs-lookup"><span data-stu-id="0fad2-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="0fad2-113">將類型檔案放入 *Models* 資料夾︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="0fad2-114">您也可以輕鬆地巡覽及維護以邏輯方式將檔案群組到資料夾的專案。</span><span class="sxs-lookup"><span data-stu-id="0fad2-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="0fad2-115">在下一節中，您會建立具有資料夾及單元測試的更複雜範例。</span><span class="sxs-lookup"><span data-stu-id="0fad2-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="0fad2-116">使用 NewTypes Pets 範例進行組織及測試</span><span class="sxs-lookup"><span data-stu-id="0fad2-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="0fad2-117">建置範例</span><span class="sxs-lookup"><span data-stu-id="0fad2-117">Building the sample</span></span>

<span data-ttu-id="0fad2-118">如需下列步驟，您可以遵循如何使用 [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) (NewTypes Pets 範例)，或建立自己的檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="0fad2-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="0fad2-119">類型會以邏輯方式組織成資料夾結構以允許稍後新增更多類型，而且測試也會以邏輯方式放在允許稍後新增更多測試的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0fad2-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="0fad2-120">這個範例包含 `Dog` 及 `Cat` 這兩種類型，並讓它們實作公用介面 `IPet`。</span><span class="sxs-lookup"><span data-stu-id="0fad2-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="0fad2-121">針對 `NewTypes` 專案，您的目標是將寵物相關類型組織到 *Pets* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0fad2-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="0fad2-122">如果稍後新增另一組類型 (例如，*WildAnimals*)，則會將它們放入 *Pets* 資料夾旁邊的 *NewTypes* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0fad2-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="0fad2-123">*WildAnimals* 資料夾可能會包含不是寵物之動物的類型，例如 `Squirrel` 及 `Rabbit` 類型。</span><span class="sxs-lookup"><span data-stu-id="0fad2-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="0fad2-124">因此，新增類型時，專案會井然有序。</span><span class="sxs-lookup"><span data-stu-id="0fad2-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="0fad2-125">使用所指出的檔案內容來建立下列資料夾結構︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="0fad2-126">*IPet.cs*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="0fad2-127">*Dog.cs*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="0fad2-128">*Cat.cs*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="0fad2-129">*Program.cs*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="0fad2-130">*NewTypes.csproj*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="0fad2-131">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0fad2-131">Execute the following command:</span></span>

```console
dotnet run
```

<span data-ttu-id="0fad2-132">取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0fad2-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="0fad2-133">選擇性練習：您可以擴充此專案，以新增 `Bird` 這類寵物類型。</span><span class="sxs-lookup"><span data-stu-id="0fad2-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="0fad2-134">讓小鳥的 `TalkToOwner` 方法提供 `Tweet!` 給擁有者。</span><span class="sxs-lookup"><span data-stu-id="0fad2-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="0fad2-135">重新執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fad2-135">Run the app again.</span></span> <span data-ttu-id="0fad2-136">輸出會包含 `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="0fad2-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="0fad2-137">測試範例</span><span class="sxs-lookup"><span data-stu-id="0fad2-137">Testing the sample</span></span>

<span data-ttu-id="0fad2-138">`NewTypes` 專案已經就緒，而且組織方式是將寵物相關類型保留在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0fad2-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="0fad2-139">接下來，建立測試專案，並開始撰寫具有 [xUnit](https://xunit.github.io/) 測試架構的測試。</span><span class="sxs-lookup"><span data-stu-id="0fad2-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="0fad2-140">單元測試可讓您自動檢查寵物類型的行為以確認它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="0fad2-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="0fad2-141">巡覽回到 *src* 資料夾，並建立內含 *NewTypesTests* 資料夾的 *test* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0fad2-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="0fad2-142">在命令提示字元中，從 *NewTypesTests* 資料夾執行 `dotnet new xunit`。</span><span class="sxs-lookup"><span data-stu-id="0fad2-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="0fad2-143">這會產生兩個檔案：*NewTypesTests.csproj* 及 *UnitTest1.cs*。</span><span class="sxs-lookup"><span data-stu-id="0fad2-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="0fad2-144">測試專案目前無法測試 `NewTypes` 中的類型，並且需要 `NewTypes` 專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="0fad2-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="0fad2-145">若要新增專案參考，請使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../NewTypes/NewTypes.csproj
```

<span data-ttu-id="0fad2-146">或者，您也可以選擇手動新增專案參考，方法是將 `<ItemGroup>` 節點新增至 *NewTypesTests.csproj* 檔案：</span><span class="sxs-lookup"><span data-stu-id="0fad2-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="0fad2-147">*NewTypesTests.csproj*：</span><span class="sxs-lookup"><span data-stu-id="0fad2-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="0fad2-148">*NewTypesTests.csproj* 檔案包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="0fad2-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="0fad2-149">`Microsoft.NET.Test.Sdk` (.NET 測試基礎結構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="0fad2-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="0fad2-150">`xunit` (xUnit 測試架構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="0fad2-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="0fad2-151">`xunit.runner.visualstudio` (測試執行器) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="0fad2-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="0fad2-152">`NewTypes` (要測試的程式碼) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="0fad2-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="0fad2-153">將 *UnitTest1.cs* 的名稱變更為 *PetTests.cs*，並將檔案中的程式碼取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="0fad2-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="0fad2-154">選擇性練習：如果您稍早已將產生 `Tweet!` 的 `Bird` 類型新增至擁有者，請將測試方法新增至 *PetTests.cs* 檔案 `BirdTalkToOwnerReturnsTweet`，確認 `TalkToOwner` 方法正確作用於 `Bird` 類型。</span><span class="sxs-lookup"><span data-stu-id="0fad2-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="0fad2-155">雖然您預期 `expected` 與 `actual` 值相等，但是具有 `Assert.NotEqual` 檢查的初始判斷提示指定這些值「不相等」。</span><span class="sxs-lookup"><span data-stu-id="0fad2-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="0fad2-156">一開始一律會讓測試失敗，以檢查測試邏輯。</span><span class="sxs-lookup"><span data-stu-id="0fad2-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="0fad2-157">在您確認測試失敗之後，調整判斷提示以允許測試通過。</span><span class="sxs-lookup"><span data-stu-id="0fad2-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="0fad2-158">下列顯示完整專案結構：</span><span class="sxs-lookup"><span data-stu-id="0fad2-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="0fad2-159">從 *test/NewTypesTests* 目錄開始。</span><span class="sxs-lookup"><span data-stu-id="0fad2-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="0fad2-160">使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原測試專案。</span><span class="sxs-lookup"><span data-stu-id="0fad2-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="0fad2-161">使用 [`dotnet test`](../tools/dotnet-test.md) 命令執行測試。</span><span class="sxs-lookup"><span data-stu-id="0fad2-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="0fad2-162">這個命令會啟動專案檔中指定的測試執行器。</span><span class="sxs-lookup"><span data-stu-id="0fad2-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0fad2-163">如預期，測試會失敗，而且主控台會顯示下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-163">As expected, testing fails, and the console displays the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="0fad2-164">將您測試的判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`：</span><span class="sxs-lookup"><span data-stu-id="0fad2-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="0fad2-165">使用 `dotnet test` 命令重新執行測試，並取得下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="0fad2-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="0fad2-166">通過測試。</span><span class="sxs-lookup"><span data-stu-id="0fad2-166">Testing passes.</span></span> <span data-ttu-id="0fad2-167">與擁有者交談時，寵物類型的方法會傳回正確值。</span><span class="sxs-lookup"><span data-stu-id="0fad2-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="0fad2-168">您已了解使用 xUnit 來組織及測試專案的技術。</span><span class="sxs-lookup"><span data-stu-id="0fad2-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="0fad2-169">繼續使用這些技術，以將它們套用至您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="0fad2-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="0fad2-170">*祝各位程式撰寫愉快！*</span><span class="sxs-lookup"><span data-stu-id="0fad2-170">*Happy coding!*</span></span>
