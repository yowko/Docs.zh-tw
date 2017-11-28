---
title: "使用 .NET Core 命令列組織和測試專案"
description: "本教學課程說明如何從命令列組織和測試 .NET Core 專案。"
keywords: ".NET, .NET Core, 單元測試, .NET Core CLI, xUnit"
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.openlocfilehash: 62c81bf070a435f6105c313ae95340a5504233df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="2c246-104">使用 .NET Core 命令列組織和測試專案</span><span class="sxs-lookup"><span data-stu-id="2c246-104">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="2c246-105">本教學課程會遵循[使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core](using-with-xplat-cli.md)，讓您超越建立簡單主控台應用程式來開發進階且井然有序的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c246-105">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="2c246-106">此教學課程在示範如何使用資料夾來組織您的程式碼之後，會示範如何使用 [xUnit](https://xunit.github.io/) 測試架構來擴充主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c246-106">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="2c246-107">使用資料夾來組織程式碼</span><span class="sxs-lookup"><span data-stu-id="2c246-107">Using folders to organize code</span></span>

<span data-ttu-id="2c246-108">如果您想要將新類型引入主控台應用程式，則可以將包含類型的檔案新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c246-108">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="2c246-109">例如，如果您將包含 `AccountInformation` 及 `MonthlyReportRecords` 類型的檔案新增至專案，則專案檔案結構會是平面，而且容易進行巡覽︰</span><span class="sxs-lookup"><span data-stu-id="2c246-109">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="2c246-110">不過，只有在專案規模相當小時，這才會運作良好。</span><span class="sxs-lookup"><span data-stu-id="2c246-110">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="2c246-111">您可以想像將 20 種類型新增至專案時，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="2c246-111">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="2c246-112">如果有多個可將專案根目錄弄亂的檔案，則絕對無法輕鬆地巡覽及維護專案。</span><span class="sxs-lookup"><span data-stu-id="2c246-112">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="2c246-113">若要組織專案，請建立新的資料夾，並將它命名為 *Models* 以保留類型檔案。</span><span class="sxs-lookup"><span data-stu-id="2c246-113">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="2c246-114">將類型檔案放入 *Models* 資料夾︰</span><span class="sxs-lookup"><span data-stu-id="2c246-114">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="2c246-115">您也可以輕鬆地巡覽及維護以邏輯方式將檔案群組到資料夾的專案。</span><span class="sxs-lookup"><span data-stu-id="2c246-115">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="2c246-116">在下一節中，您會建立具有資料夾及單元測試的更複雜範例。</span><span class="sxs-lookup"><span data-stu-id="2c246-116">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="2c246-117">使用 NewTypes Pets 範例進行組織及測試</span><span class="sxs-lookup"><span data-stu-id="2c246-117">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="2c246-118">建置範例</span><span class="sxs-lookup"><span data-stu-id="2c246-118">Building the sample</span></span>

<span data-ttu-id="2c246-119">如需下列步驟，您可以遵循如何使用 [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) (NewTypes Pets 範例)，或建立自己的檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c246-119">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="2c246-120">類型會以邏輯方式組織成資料夾結構以允許稍後新增更多類型，而且測試也會以邏輯方式放在允許稍後新增更多測試的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2c246-120">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="2c246-121">這個範例包含 `Dog` 及 `Cat` 這兩種類型，並讓它們實作公用介面 `IPet`。</span><span class="sxs-lookup"><span data-stu-id="2c246-121">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="2c246-122">針對 `NewTypes` 專案，您的目標是將寵物相關類型組織到 *Pets* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c246-122">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="2c246-123">如果稍後新增另一組類型 (例如，*WildAnimals*)，則會將它們放入 *Pets* 資料夾旁邊的 *NewTypes* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c246-123">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="2c246-124">*WildAnimals* 資料夾可能會包含不是寵物之動物的類型，例如 `Squirrel` 及 `Rabbit` 類型。</span><span class="sxs-lookup"><span data-stu-id="2c246-124">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="2c246-125">因此，新增類型時，專案會井然有序。</span><span class="sxs-lookup"><span data-stu-id="2c246-125">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="2c246-126">使用所指出的檔案內容來建立下列資料夾結構︰</span><span class="sxs-lookup"><span data-stu-id="2c246-126">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="2c246-127">*IPet.cs*：</span><span class="sxs-lookup"><span data-stu-id="2c246-127">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="2c246-128">*Dog.cs*：</span><span class="sxs-lookup"><span data-stu-id="2c246-128">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="2c246-129">*Cat.cs*：</span><span class="sxs-lookup"><span data-stu-id="2c246-129">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="2c246-130">*Program.cs*：</span><span class="sxs-lookup"><span data-stu-id="2c246-130">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="2c246-131">*NewTypes.csproj*：</span><span class="sxs-lookup"><span data-stu-id="2c246-131">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="2c246-132">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c246-132">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="2c246-133">取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2c246-133">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="2c246-134">選擇性練習︰您可以擴充此專案，以新增 `Bird` 這類寵物類型。</span><span class="sxs-lookup"><span data-stu-id="2c246-134">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="2c246-135">讓小鳥的 `TalkToOwner` 方法提供 `Tweet!` 給擁有者。</span><span class="sxs-lookup"><span data-stu-id="2c246-135">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="2c246-136">重新執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c246-136">Run the app again.</span></span> <span data-ttu-id="2c246-137">輸出會包含 `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="2c246-137">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="2c246-138">測試範例</span><span class="sxs-lookup"><span data-stu-id="2c246-138">Testing the sample</span></span>

<span data-ttu-id="2c246-139">`NewTypes` 專案已經就緒，而且組織方式是將寵物相關類型保留在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2c246-139">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="2c246-140">接下來，建立測試專案，並開始撰寫具有 [xUnit](https://xunit.github.io/) 測試架構的測試。</span><span class="sxs-lookup"><span data-stu-id="2c246-140">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="2c246-141">單元測試可讓您自動檢查寵物類型的行為以確認它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="2c246-141">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="2c246-142">建立其內具有 *NewTypesTests* 資料夾的 *test* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c246-142">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="2c246-143">在命令提示字元中，從 *NewTypesTests* 資料夾執行 `dotnet new xunit`。</span><span class="sxs-lookup"><span data-stu-id="2c246-143">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="2c246-144">這會產生兩個檔案︰*NewTypesTests.csproj* 及 *UnitTest1.cs*。</span><span class="sxs-lookup"><span data-stu-id="2c246-144">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="2c246-145">測試專案目前無法測試 `NewTypes` 中的類型，並且需要 `NewTypes` 專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="2c246-145">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="2c246-146">若要新增專案參考，請使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令︰</span><span class="sxs-lookup"><span data-stu-id="2c246-146">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="2c246-147">您也可以選擇手動新增專案參考，方法是將 `<ItemGroup>` 節點新增至 *NewTypesTests.csproj* 檔案︰</span><span class="sxs-lookup"><span data-stu-id="2c246-147">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="2c246-148">*NewTypesTests.csproj*：</span><span class="sxs-lookup"><span data-stu-id="2c246-148">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="2c246-149">*NewTypesTests.csproj* 檔案包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="2c246-149">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="2c246-150">`Microsoft.NET.Test.Sdk` (.NET 測試基礎結構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="2c246-150">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="2c246-151">`xunit` (xUnit 測試架構) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="2c246-151">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="2c246-152">`xunit.runner.visualstudio` (測試執行器) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="2c246-152">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="2c246-153">`NewTypes` (要測試的程式碼) 的套件參考</span><span class="sxs-lookup"><span data-stu-id="2c246-153">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="2c246-154">將 *UnitTest1.cs* 的名稱變更為 *PetTests.cs*，並將檔案中的程式碼取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="2c246-154">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="2c246-155">選擇性練習︰如果您稍早已將產生 `Tweet!` 的 `Bird` 類型新增至擁有者，請將測試方法新增至 PetTests.cs 檔案，並新增 `BirdTalkToOwnerReturnsTweet` 以確認 `TalkToOwner` 方法正確作用於 `Bird` 類型。</span><span class="sxs-lookup"><span data-stu-id="2c246-155">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="2c246-156">雖然您預期 `expected` 與 `actual` 值相等，但是具有 `Assert.NotEqual` 檢查的初始判斷提示指定它們「不相等」。</span><span class="sxs-lookup"><span data-stu-id="2c246-156">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="2c246-157">一開始一律會讓您的測試失敗一次，以檢查測試邏輯。</span><span class="sxs-lookup"><span data-stu-id="2c246-157">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="2c246-158">這是測試導向設計 (TDD) 方法中的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="2c246-158">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="2c246-159">在您確認測試失敗之後，調整判斷提示以允許它們通過。</span><span class="sxs-lookup"><span data-stu-id="2c246-159">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="2c246-160">下列顯示完整專案結構：</span><span class="sxs-lookup"><span data-stu-id="2c246-160">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="2c246-161">從 *test/NewTypesTests* 目錄開始。</span><span class="sxs-lookup"><span data-stu-id="2c246-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="2c246-162">使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原測試專案。</span><span class="sxs-lookup"><span data-stu-id="2c246-162">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="2c246-163">使用 [`dotnet test`](../tools/dotnet-test.md) 命令執行測試。</span><span class="sxs-lookup"><span data-stu-id="2c246-163">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="2c246-164">這個命令會啟動專案檔中指定的測試執行器。</span><span class="sxs-lookup"><span data-stu-id="2c246-164">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="2c246-165">如預期，測試會失敗，而且主控台會顯示下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="2c246-165">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="2c246-166">將您測試的判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`：</span><span class="sxs-lookup"><span data-stu-id="2c246-166">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="2c246-167">使用 `dotnet test` 命令重新執行測試，並取得下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="2c246-167">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="2c246-168">通過測試。</span><span class="sxs-lookup"><span data-stu-id="2c246-168">Testing passes.</span></span> <span data-ttu-id="2c246-169">與擁有者交談時，寵物類型的方法會傳回正確值。</span><span class="sxs-lookup"><span data-stu-id="2c246-169">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="2c246-170">您已了解使用 xUnit 來組織及測試專案的技術。</span><span class="sxs-lookup"><span data-stu-id="2c246-170">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="2c246-171">繼續使用這些技術，以將它們套用至您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="2c246-171">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="2c246-172">*祝各位程式撰寫愉快！*</span><span class="sxs-lookup"><span data-stu-id="2c246-172">*Happy coding!*</span></span>

