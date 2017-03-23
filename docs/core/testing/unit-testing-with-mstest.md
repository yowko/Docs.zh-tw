---
title: "使用 MSTest 和 .NET Core | Microsoft Docs"
description: "如何使用 MSTest 和 .NET Core"
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 02/10/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 4ffc7dd4e11820a3c50ca83847a7ab418bf2faf3
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a>使用 MSTest 和 .NET Core 執行單元測試

## <a name="creating-the-projects"></a>建立專案

如需整理多專案方案的來源和測試資訊，可參閱[使用跨平台工具撰寫程式庫](../tutorials/libraries.md)。 這篇文章會遵循其中的慣例。 最終的專案結構會類似這樣：

```
/unit-testing-using-mstest
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 從 *unit-testing-using-mstest* 目錄開始，建立 *PrimeService* 目錄。
將 *PrimeService* 設為目前的目錄，然後執行 `dotnet new classlib` 以建立來源專案。

將 *Class1.cs* 重新命名為 *PrimeService.cs*。 為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：

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

接下來，將目錄變更回 *unit-testing-using-mstest* 目錄，然後建立 *PrimeServices.Tests* 目錄。
將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 `dotnet new mstest` 建立新的專案。 這會建立將 MStest 作為測試程式庫的測試專案。 

產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170123-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.10-rc2" />
  <PackageReference Include="MSTest.TestFramework" Version="1.0.8-rc2" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。
`dotnet new` 會新增 MSTest SDK、MSTest 測試架構和 MSTest 執行器。 您需要新增 PrimeService 套件以作為專案的另一個相依性。 您可以使用 `dotnet` CLI 來完成：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

或者，您可以手動編輯 *PrimeService.Tests.csproj* 檔案。
在第一個 `<ItemGroup>` 節點的正下方，新增另一個參考至程式庫專案的 `<ItemGroup>` 節點：

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

準備好這個初始結構之後，您即可撰寫第一個測試。
只要您有好好確認第一個單元測試，所有項目就會妥善設定，並在您新增功能及進行測試時順利執行。

## <a name="creating-the-first-test"></a>建立第一個測試

建置程式庫或測試之前，您必須先在 *PrimeService* 和 *PrimeService.Tests* 目錄中執行 `dotnet restore`。 此命令會還原每個專案的所有必要 NuGet 套件。

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複此程序。 因此，我們就來撰寫這個失敗的測試。 從 *PrimeService.Tests* 目錄中移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：

```cs
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;
        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

`[TestClass]` 屬性代表包含單元測試的類別。 `[TestMethod]` 屬性會將方法表示為單一測試。 

儲存此檔案，然後執行 `dotnet build` 以建置測試專案。
建置系統會偵測是否已建置 `PrimeService` 專案並加以建置 (如果您尚未建置的話)，因為測試專案與其具有相依性。

現在，請執行 `dotnet test` 以從主控台執行測試。
MSTest 測試執行器具有從主控台執行測試的程式進入點。 `dotnet test` 會啟動測試執行器，並將命令列引數提供給測試執行器以指出測試中包含的組件。

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

在 *PrimeService.Tests* 目錄中，重新執行 `dotnet test`。 `dotnet test` 命令會先執行 Prime.Services 專案的組建，再執行 PrimeService.Tests 專案的組建。 建置這兩個專案之後，它將會執行此單一測試。 測試通過。

## <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，即可撰寫更多測試。
還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[TestMethod]` 屬性將這些項目新增為新測試，但很快就會單調乏味。 因此，還有其他 MSTest 屬性，可讓您撰寫類似的測試套件。  `DataTestMethod` 代表執行相同程式碼但有不同輸入引數的測試套件。
您可以使用 `[DataRow]` 屬性來指定這些輸入值。 
 
 與其建立新的測試，您可以改用這兩個屬性來建立單一資料測試方法，以測試一些小於 2 (其為最小質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "第一個測試")]

執行 `dotnet test`，則會發現兩個測試都失敗。
您可以變更服務，以讓它們順利通過。 您需要變更方法開頭的 `if` 子句：

```cs
if(candidate < 2)
```

現在，這些測試都通過了。

您可繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 不久，您就可以得到[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試，
並已結構化這個方案，因此可以順暢地新增新套件和測試，專注地處理手邊的問題。 這些工具皆可自動執行。
