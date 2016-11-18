---
title: "使用 DotNet 測試的 .NET Core 單元測試"
description: "使用 DotNet 測試的 .NET Core 單元測試"
keywords: .NET, .NET Core
author: ardalis
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: 0c98084786408a285111ae724ed404ce32160aea

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>使用 DotNet 測試的 .NET Core 單元測試

作者 [Steve Smith](http://ardalis.com) 和 [Bill Wagner](https://github.com/BillWagner)

[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

## <a name="creating-the-projects"></a>建立專案

如需整理多專案方案的來源和測試資訊，可參閱[使用跨平台工具撰寫程式庫](../tutorials/libraries.md)。 這篇文章會遵循其中的慣例。 最終的專案結構會類似這樣：

```
/unit-testing-using-dotnet-test
|__global.json
|__/src
   |__/PrimeService
      |__Source Files
      |__project.json
|__/test
   |__/PrimeService.Tests
      |__Test Files
      |__project.json
```

在根目錄中，您將需要建立 `global.json` 以包含您的 `src` 和 `test` 目錄的名稱：

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

### <a name="creating-the-source-project"></a>建立來源專案

然後，在 `src` 目錄中，建立 `PrimeService` 目錄。
移至該目錄，然後執行 `dotnet new -t lib` 以建立來源專案。


將 `Library.cs` 重新命名為 `PrimeService.cs`。 為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：

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

接下來，移至 'test' 目錄，並建立 `PrimeServices.Tests` 目錄。
移至 `PrimeServices.Tests` 目錄，並使用 `dotnet new -t xunittest` 建立新的專案。 `dotnet new -t xunittest` 會建立將 xunit 作為測試程式庫的測試專案。 

產生的範本會在 `project.json` 的根目錄中設定測試執行器：

```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",
  // ...
}
```

該範本也會將架構節點設為使用 `netcoreapp1.0`，並包含必要的匯入，以讓 xUnit.net 使用 .NET Core RTM：

```json
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dotnet54",
        "portable-net45+win8" 
      ]
    }
  }
```

測試專案需要其他套件來建立和執行單元測試。
`dotnet new` 會新增 xunit 和 xunit 執行器。 您需要新增 PrimeService 套件以做為專案的另一個相依性：

```json
"dependencies": {
  "Microsoft.NETCore.App": {
    "type":"platform",
    "version": "1.0.0"
  },
  "xunit":"2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "PrimeService": {
    "target": "project"
  }
}
```

請注意，`PrimeService` 專案不包含任何目錄路徑資訊。 這是因為您已建立專案結構，使其符合預期的 `src` 和 `test` 組織，而 `global.json` 檔案表示，建置系統將會找到專案的正確位置。 您會新增 `"target": "project"` 項目，告知 NuGet 應查看專案目錄而不是 NuGet 摘要。 若未使用這個索引鍵，您可能會下載到與您的內部程式庫同名的套件。

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/project.json)中看到完整檔案。

準備好這個初始結構之後，您即可撰寫第一個測試。
只要您有好好確認第一個單元測試，所有項目就會妥善設定，並在您新增功能及進行測試時順利執行。

## <a name="creating-the-first-test"></a>建立第一個測試

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複此程序。 因此，我們就來撰寫這個失敗的測試。 從 `PrimeService.Tests` 目錄中移除 `program.cs`，並使用下列內容建立新的 C# 檔案：

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
xunit 測試執行器具有從主控台執行測試的程式進入點。 `dotnet test` 會啟動測試執行器，並將命令列引數提供給測試執行器以指出測試中包含的組件。

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
還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[Fact]` 屬性將這些項目新增為新測試，但很快就會單調乏味。 因此，還有其他 xunit 屬性，可讓您撰寫類似的測試套件。  `Theory` 代表執行相同程式碼但有不同輸入引數的測試套件。
您可以使用 `[InlineData]` 屬性來指定這些輸入值。 
 
 與其建立新的測試，您可以改用這兩個屬性來建立單一的理論，以測試一些小於 2 (其為最小質數) 的值：

```cs
[Theory]
[InlineData(-1)]
[InlineData(0)]
[InlineData(1)]
public void ReturnFalseGivenValuesLessThan2(int value)
{
    var result = _primeService.IsPrime(value);

    Assert.False(result, $"{value} should not be prime");
}
```

執行 `dotnet test`，則會發現兩個測試都失敗。
您可以變更服務，以讓它們順利通過。 您需要變更方法開頭的 `if` 子句：

```cs
if(candidate < 2)
```

現在，這些測試都通過了。

您可繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 不久，您就可以得到[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeServie_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試，
並已結構化這個方案，因此可以順暢地新增新套件和測試，專注地處理手邊的問題。 這些工具皆可自動執行。
   
   > [!TIP]
   > 在 Windows 平台上，您可以使用 MSTest。 如需詳細資訊，請參閱[在 Windows 文件上使用 MSTest](./using-mstest-on-windows.md)。



<!--HONumber=Nov16_HO3-->


