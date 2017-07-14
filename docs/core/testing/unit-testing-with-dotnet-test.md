---
title: "使用 dotnet test 和 xUnit 的 .NET Core 單元測試 | Microsoft Docs"
description: "使用 dotnet test 的 .NET Core 單元測試"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
ms.translationtype: Human Translation
ms.sourcegitcommit: 06e1ecc181847f87df9ed3a527638008ca6857fc
ms.openlocfilehash: b5c6d162adf363da41c4c60fdd9fe38e1d58d27a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# 使用 dotnet test 和 xUnit 的 .NET Core 單元測試
<a id="unit-testing-in-net-core-using-dotnet-test-and-xunit" class="xliff"></a>

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

### 建立來源專案
<a id="creating-the-source-project" class="xliff"></a>

開啟 Shell 視窗。 建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。 在這個新目錄中建立 *PrimeService* 目錄。 到目前為止的目錄結構如下所示：

```
/unit-testing-using-dotnet-test
    /PrimeService
```

將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。 將 *Class1.cs* 重新命名為 *PrimeService.cs*。 為了使用測試導向開發 (TDD)，您必須建立 `PrimeService` 類別的失敗實作：

```csharp
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

### 建立測試專案
<a id="creating-the-test-project" class="xliff"></a>

將目錄變更回 *unit-testing-using-dotnet-test* 目錄，然後建立 *PrimeService.Tests* 目錄。 目錄結構如下所示：

```
/unit-testing-using-dotnet-test
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new xunit`](../tools/dotnet-new.md) 建立新的專案。 這樣會建立將 xUnit 作為測試程式庫的測試專案。 產生的範本會在 *PrimeServiceTests.csproj* 中設定測試執行器：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new` 已新增 xUnit 和 xUnit 執行器。 現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

另一個選項是編輯 *PrimeService.Tests.csproj* 檔案。 在第一個 `<ItemGroup>` 節點的正下方，新增另一個參考至程式庫專案的 `<ItemGroup>` 節點：

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

最終的方案配置如下所示：

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## 建立第一個測試
<a id="creating-the-first-test" class="xliff"></a>

建置程式庫或測試之前，先在 *PrimeService.Tests* 目錄中執行 [`dotnet restore`](../tools/dotnet-restore.md)。 此命令會還原每個專案的所有必要 NuGet 套件。

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。 從 *PrimeService.Tests* 目錄移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

`[Fact]` 屬性會將方法表示為單一測試。 執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。 xUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 會啟動測試執行器，並將命令列引數提供給測試執行器以指出包含測試的組件。

您的測試失敗。 您尚未建立實作。 在 `PrimeService` 類別中撰寫最簡單的程式碼，使這個測試順利通過：

```csharp
public bool IsPrime(int candidate) 
{
    if (candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

在 *PrimeService.Tests* 目錄中，重新執行 `dotnet test`。 `dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。 建置這兩個專案之後，它將會執行此單一測試。 測試通過。

### 新增更多功能
<a id="adding-more-features" class="xliff"></a>

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[Fact]` 屬性將這些項目新增為新測試，但很快就會單調乏味。 因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。  `[Theory]` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。 您可以使用 `[InlineData]` 屬性來指定這些輸入值。 
 
您不需要建立新的測試，而可以改為使用這兩個屬性來建立單一的理論，以測試幾個小於 2 (最小質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

執行 `dotnet test`，然後會有兩個測試失敗。 若要使所有測試通過，請變更方法開頭的 `if` 子句：

```csharp
if (candidate < 2)
```

繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 您就可以得到[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試， 您已經將方案結構化，使新增套件和測試更順暢，因此您可以將大部分的時間和精力專注於解決應用程式的目標。

