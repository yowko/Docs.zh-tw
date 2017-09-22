---
title: "使用 .NET Core 命令列組織和測試專案"
description: "本教學課程說明如何從命令列組織和測試 .NET Core 專案。"
keywords: ".NET, .NET Core, 單元測試, .NET Core CLI, xUnit"
author: cartermp
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a0a0554b28600821fb15f64d31c6bce74a17136
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>使用 .NET Core 命令列組織和測試專案

本教學課程會遵循[使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core](./using-with-xplat-cli.md)，以示範如何超越簡單的 "hello world" 案例，並為更進階且井然有序的應用程式打好基礎。

## <a name="using-folders-to-organize-code"></a>使用資料夾來組織程式碼

假設您想要引進一些新的類型來使用。 您可以藉由新增更多檔案，並確定給予它們可包含在您 *Program.cs* 檔案中的命名空間，來達到此目的。

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
```

這很適合您的專案相當小的時候。 不過，如果您有較大的應用程式，並且使用許多不同的資料類型，且可能有多個層時，您可能會想以邏輯方式來組織項目。 這就是資料夾派上用場的時刻。 您可以遵照本指南介紹的 [NewTypes 範例專案](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild)，或建立自己的檔案和資料夾。

若要開始，請在專案的根目錄下建立新的資料夾。 `/Model`在這裡選擇。

```
/NewTypes
|__/Model
|__Program.cs
|__NewTypes.csproj
```

現在，請新增一些新的類型到資料夾中︰

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__NewTypes.csproj
```

*IPet.cs*：

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

### <a name="example-pet-types"></a>範例︰寵物類型

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

資料夾結構：

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*：

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*：

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

執行下列命令：

```console
dotnet restore
dotnet run
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`NewTypes.csproj`:
```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

而且，如果您執行它︰

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

可以新增新的寵物類型 (例如 `Bird`)，擴充此專案。

## <a name="testing-your-console-app"></a>測試主控台應用程式

您可能會想要在某個時間點測試您的專案。 以下是很好的作法︰

1. 將現有專案的任何來源移至新的 `src` 資料夾。

   ```
   /Project
   |__/src
   ```

2. 建立 `/test` 目錄，然後 `cd` 到其中。

   ```
   /Project
   |__/src
   |__/test
   ```

3. 使用 `dotnet new xunit` 命令初始化目錄。 這假設的是 xUnit，但您也能夠藉由以 `mstest` 取代 `xunit` 來使用 MSTest。
   
### <a name="example-extending-the-newtypes-project"></a>範例︰擴充 NewTypes 專案

現在，專案系統已就緒，您可以建立測試專案，並開始撰寫測試！ 從現在開始，本指南會使用和擴充[範例 Types 專案](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild)。 此外，它會使用 [Xunit](https://xunit.github.io/) 測試架構。 請放心地依照指示進行，或建立自己的多專案系統與測試。

整個專案結構看起來應該像這樣︰

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

您的測試專案中需要確定有兩樣新的項目︰

1. 正確的 *NewTypesTests.csproj* 檔案，並具有下列各項：

   * 參考`xunit`
   * 參考`dotnet-test-xunit`
   * 對應至測試中程式碼的命名空間參考

   您可以在 *NewTypesTests* 目錄中的命令提示字元處輸入 `dotnet new xunit`，然後將專案參考新增至 `NewTypes` 專案，來建置此項。

    `NewTypesTests/NewTypesTests.csproj`:
    ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>netcoreapp1.0</TargetFramework>
      </PropertyGroup>

      <ItemGroup>
        <Compile Include="**\*.cs" />
        <EmbeddedResource Include="**\*.resx" />
      </ItemGroup>

      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161104-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Test.Sdk">
          <Version>15.0.0-preview-20161024-02</Version>
        </PackageReference>
        <PackageReference Include="xunit">
          <Version>2.2.0-beta3-build3402</Version>
        </PackageReference>
        <PackageReference Include="xunit.runner.visualstudio">
          <Version>2.2.0-beta4-build1188</Version>
        </PackageReference>
        <ProjectReference Include="../../src/NewTypes/NewTypes.csproj"/>
      </ItemGroup>

      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

2. xUnit 測試類別。

    `PetTests.cs`: 
    ```csharp
    using System;
    using Xunit;
    using Pets;
    public class PetTests
    {
        [Fact]
        public void DogTalkToOwnerTest()
        {
            string expected = "Woof!";
            string actual = new Dog().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
        
        [Fact]
        public void CatTalkToOwnerTest()
        {
            string expected = "Meow!";
            string actual = new Cat().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
    }
    ```
   
現在您可以執行測試了！ [`dotnet test`](../tools/dotnet-test.md) 命令會執行您的專案中所指定的測試執行器。 請確定您在最上層目錄啟動。
 
```
$ cd test/NewTypesTests
$ dotnet restore
$ dotnet test
```

將您測試的判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`：

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

使用 `dotnet test` 命令重新執行測試，並取得下列輸出︰

```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```

通過測試。 與擁有者交談時，寵物類型的方法會傳回正確值。

您已了解使用 xUnit 來組織及測試專案的技術。 繼續使用這些技術，以將它們套用至您自己的專案。 *祝各位程式撰寫愉快！*

