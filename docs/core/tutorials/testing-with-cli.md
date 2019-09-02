---
title: 使用 .NET Core 命令列組織和測試專案
description: 本教學課程說明如何從命令列組織和測試 .NET Core 專案。
author: cartermp
ms.date: 09/10/2018
ms.custom: seodec18
ms.openlocfilehash: a8724c971521b8d65700d61a1ce523c1dfdddf0a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202995"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>使用 .NET Core 命令列組織和測試專案

此教學課程遵循[使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core](using-with-xplat-cli.md)，讓您超越建立簡單主控台應用程式來開發進階且井然有序的應用程式。 此教學課程在示範如何使用資料夾來組織您的程式碼之後，會示範如何使用 [xUnit](https://xunit.github.io/) 測試架構來擴充主控台應用程式。

## <a name="using-folders-to-organize-code"></a>使用資料夾來組織程式碼

如果您想要將新類型引入主控台應用程式，則可以將包含類型的檔案新增至應用程式。 例如，如果您將包含 `AccountInformation` 及 `MonthlyReportRecords` 類型的檔案新增至專案，則專案檔案結構會是平面，而且容易進行巡覽︰

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

不過，只有在專案規模相當小時，這才會運作良好。 您可以想像將 20 種類型新增至專案時，會發生什麼事？ 如果有多個可將專案根目錄弄亂的檔案，則絕對無法輕鬆地巡覽及維護專案。

若要組織專案，請建立新的資料夾，並將它命名為 *Models* 以保留類型檔案。 將類型檔案放入 *Models* 資料夾︰

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

您也可以輕鬆地巡覽及維護以邏輯方式將檔案群組到資料夾的專案。 在下一節中，您會建立具有資料夾及單元測試的更複雜範例。

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>使用 NewTypes Pets 範例進行組織及測試

### <a name="building-the-sample"></a>建置範例

如需下列步驟，您可以遵循如何使用 [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) (NewTypes Pets 範例)，或建立自己的檔案及資料夾。 類型會以邏輯方式組織成資料夾結構以允許稍後新增更多類型，而且測試也會以邏輯方式放在允許稍後新增更多測試的資料夾中。

這個範例包含 `Dog` 及 `Cat` 這兩種類型，並讓它們實作公用介面 `IPet`。 針對 `NewTypes` 專案，您的目標是將寵物相關類型組織到 *Pets* 資料夾。 如果稍後新增另一組類型 (例如，*WildAnimals*)，則會將它們放入 *Pets* 資料夾旁邊的 *NewTypes* 資料夾。 *WildAnimals* 資料夾可能會包含不是寵物之動物的類型，例如 `Squirrel` 及 `Rabbit` 類型。 因此，新增類型時，專案會井然有序。

使用所指出的檔案內容來建立下列資料夾結構︰

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

*IPet.cs*：

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*：

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*：

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*：

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*：

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

執行下列命令：

```console
dotnet run
```

取得下列輸出：

```console
Woof!
Meow!
```

選擇性練習：您可以擴充此專案，以新增 `Bird` 這類寵物類型。 讓小鳥的 `TalkToOwner` 方法提供 `Tweet!` 給擁有者。 重新執行應用程式。 輸出會包含 `Tweet!`

### <a name="testing-the-sample"></a>測試範例

`NewTypes` 專案已經就緒，而且組織方式是將寵物相關類型保留在資料夾中。 接下來，建立測試專案，並開始撰寫具有 [xUnit](https://xunit.github.io/) 測試架構的測試。 單元測試可讓您自動檢查寵物類型的行為以確認它們正常運作。

巡覽回到 *src* 資料夾，並建立內含 *NewTypesTests* 資料夾的 *test* 資料夾。 在命令提示字元中，從 *NewTypesTests* 資料夾執行 `dotnet new xunit`。 這會產生兩個檔案：*NewTypesTests.csproj* 及 *UnitTest1.cs*。

測試專案目前無法測試 `NewTypes` 中的類型，並且需要 `NewTypes` 專案的專案參考。 若要新增專案參考，請使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令︰

```console
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

或者，您也可以選擇手動新增專案參考，方法是將 `<ItemGroup>` 節點新增至 *NewTypesTests.csproj* 檔案：

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*：

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* 檔案包含下列項目：

* `Microsoft.NET.Test.Sdk` (.NET 測試基礎結構) 的套件參考
* `xunit` (xUnit 測試架構) 的套件參考
* `xunit.runner.visualstudio` (測試執行器) 的套件參考
* `NewTypes` (要測試的程式碼) 的套件參考

將 *UnitTest1.cs* 的名稱變更為 *PetTests.cs*，並將檔案中的程式碼取代為下列內容：

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

選擇性練習：如果您稍早已將產生 `Tweet!` 的 `Bird` 類型新增至擁有者，請將測試方法新增至 *PetTests.cs* 檔案 `BirdTalkToOwnerReturnsTweet`，確認 `TalkToOwner` 方法正確作用於 `Bird` 類型。

> [!NOTE]
> 雖然您預期 `expected` 與 `actual` 值相等，但是具有 `Assert.NotEqual` 檢查的初始判斷提示指定這些值「不相等」  。 一開始一律會讓測試失敗，以檢查測試邏輯。 在您確認測試失敗之後，調整判斷提示以允許測試通過。

下列顯示完整專案結構：

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

從 *test/NewTypesTests* 目錄開始。 使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原測試專案。 使用 [`dotnet test`](../tools/dotnet-test.md) 命令執行測試。 這個命令會啟動專案檔中指定的測試執行器。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

如預期，測試會失敗，而且主控台會顯示下列輸出︰

```output
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

將您測試的判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`：

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

使用 `dotnet test` 命令重新執行測試，並取得下列輸出︰

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

通過測試。 與擁有者交談時，寵物類型的方法會傳回正確值。

您已了解使用 xUnit 來組織及測試專案的技術。 繼續使用這些技術，以將它們套用至您自己的專案。 *祝各位程式撰寫愉快！*
