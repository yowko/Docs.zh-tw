---
title: "使用 DotNet 測試的 .NET Core 單元測試 | Microsoft Docs"
description: "使用 DotNet 測試的 .NET Core 單元測試"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 002/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: cd860241f5f20b6a4f1ccfec60e0c9cd5079152a
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>使用 DotNet 測試的 .NET Core 單元測試

作者 [Steve Smith](http://ardalis.com) 和 [Bill Wagner](https://github.com/BillWagner)

[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

## <a name="creating-the-projects"></a>建立專案

如需整理多專案方案的來源和測試資訊，可參閱[使用跨平台工具撰寫程式庫](../tutorials/libraries.md)。 這篇文章會遵循其中的慣例。 最終的專案結構會類似這樣：

```
/unit-testing-using-dotnet-test
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>建立來源專案

從 `unit-testing-using-dotnet-test` 目錄開始，建立 `PrimeService` 目錄。
移至該目錄，然後執行 `dotnet new classib` 以建立來源專案。


將 `Class1.cs` 重新命名為 `PrimeService.cs`。 為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：

```cs
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}

```

### <a name="creating-the-test-project"></a>建立測試專案

接下來，回到 'unit-testing-using-dotnet-test' 目錄，並建立 `PrimeServices.Tests` 目錄。
移至 `PrimeService.Tests` 目錄，並使用 `dotnet new xunit` 建立新的專案。 `dotnet xunit` 會建立將 xUnit 作為測試程式庫的測試專案。 

產生的範本會在 PrimeServiceTests.csproj 中設定測試執行器：

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170125-04" />
    <PackageReference Include="xunit" Version="2.2.0-beta5-build3474" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-beta5-build1225" />
  </ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。
`dotnet new` 會新增 xUnit 和 xUnit 執行器。 您需要新增 PrimeService 套件以作為專案的另一個相依性。 您可以使用 `dotnet` CLI 來完成：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

或者，您可以直接編輯 `PrimeService.Tests.csproj` 檔案。
在第一個 `<ItemGroup>` 節點的正下方，新增另一個參考至程式庫專案的 `<ItemGroup>` 節點：

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

準備好這個初始結構之後，您即可撰寫第一個測試。
只要您有好好確認第一個單元測試，所有項目就會妥善設定，並在您新增功能及進行測試時順利執行。

## <a name="creating-the-first-test"></a>建立第一個測試

建置程式庫或測試之前，您必須先在 `PrimeService` 和 `PrimeService.Tests` 目錄中執行 `dotnet restore`。 此命令會還原每個專案的所有必要 NuGet 套件。

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複此程序。 因此，我們就來撰寫這個失敗的測試。 從 `PrimeService.Tests` 目錄中移除 `UnitTest1.cs`，並使用下列內容建立名為 `PrimeService_IsPrimeShould.cs` 的新 C# 檔案：

```cs
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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

`[Fact]` 屬性會將方法表示為單一測試。 

儲存此檔案，然後執行 `dotnet build` 以建置測試專案。
建置系統會偵測是否已建置 `PrimeService` 專案並加以建置 (如果您尚未建置的話)，因為測試專案與其具有相依性。

現在，請執行 `dotnet test` 以從主控台執行測試。
xUnit 測試執行器具有從主控台執行測試的程式進入點。 `dotnet test` 會啟動測試執行器，並將命令列引數提供給測試執行器以指出測試中包含的組件。

您的測試失敗。 您尚未建立實作。
撰寫最簡單的程式碼，使這一個測試順利通過：

```cs
public bool IsPrime(int candidate) 
{
    if(candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

### <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，即可撰寫更多測試。
還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[Fact]` 屬性將這些項目新增為新測試，但很快就會單調乏味。 因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。  `Theory` 代表執行相同程式碼但有不同輸入引數的測試套件。
您可以使用 `[InlineData]` 屬性來指定這些輸入值。 
 
 與其建立新的測試，您可以改用這兩個屬性來建立單一的理論，以測試一些小於 2 (其為最小質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "第一個測試")]
```

Run `dotnet test` and you'll see that two of these tests fail.
You can make them pass by changing the service. You need to change
the `if` clause at the beginning of the method:

```cs
if(candidate < 2)
```

現在，這些測試都通過了。

您可繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 不久，您就可以得到[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試，
並已結構化這個方案，因此可以順暢地新增新套件和測試，專注地處理手邊的問題。 這些工具皆可自動執行。

