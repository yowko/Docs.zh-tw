---
title: "使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試"
description: "透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。"
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: a9e64fe37f05b7bbe05b1c5878e4b31084a1c8b6
ms.sourcegitcommit: 7296449e03f747528f9bc59954c74bf4e359cc1e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。
在這個新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以建立新方案。 具備解決方案可讓您更輕鬆地同時管理類別庫與單元測試專案。
在方案目錄中，建立 *PrimeService* 目錄。 到目前為止，目錄與檔案結構應如下所示：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。 將 *Class1.cs* 重新命名為 *PrimeService.cs*。 若要使用測試驅動開發 (TDD)，請先建立 `PrimeService` 類別的失敗實作：

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

將目錄變更回 *unit-testing-using-dotnet-test* 目錄。

執行 [dotnet sln](../tools/dotnet-sln.md) 命令，將類別庫專案新增至解決方案：

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a>建立測試專案

接著，建立 *PrimeService.Tests* 目錄。 下列大綱顯示目錄結構：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new xunit`](../tools/dotnet-new.md) 建立新的專案。 此命令會建立將 xUnit 作為測試程式庫使用的測試專案。 產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器，類似如下程式碼：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new` 已新增 xUnit 和 xUnit 執行器。 現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

下面顯示最終方案配置：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

若要將測試專案新增至解決方案，請在 *unit-testing-using-dotnet-test* 目錄中執行 [dotnet sln](../tools/dotnet-sln.md) 命令：

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>建立第一個測試

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。 將 *UnitTest1.cs* 從 *PrimeService.Tests* 目錄移除，並建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案。 加入下列程式碼：

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

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` 屬性指出由測試執行器執行的測試方法。 從 *PrimeService.Tests* 資料夾執行 [`dotnet test`](../tools/dotnet-test.md)，建置測試及類別庫，然後執行測試。 xUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 會使用您建立的單元測試專案來開始測試執行器。

您的測試失敗。 您尚未建立實作。 請在可運作的 `PrimeService` 類別中，撰寫最簡易的程式碼來進行測試。 並使用下列程式碼取代現有的 `IsPrime` 方法實作：

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

## <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[Fact]` 屬性將那些案例新增為新測試，但很快就會單調乏味。 另有其他 xUnit 屬性可供您撰寫類似測試的套件：

- `[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。

- `[InlineData]` 屬性會指定這些輸入的值。

您無須建立新的測試，只要套用這兩個屬性 (`[Theory]` 和 `[InlineData]`)，即可在 *PrimeService_IsPrimeShould.cs* 檔案中建立單一理論。 該理論是一種方法，這種方法會測試數個低於二 (最小的質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

再次執行 `dotnet test`，這些測試的其中兩個應該會失敗。 若要讓所有測試都能通過，請變更 *PrimeService.cs* 檔案中 `IsPrime` 方法開頭處的 `if` 子句：

```csharp
if (candidate < 2)
```

繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 您有[測試的完成版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。

### <a name="additional-resources"></a>其他資源

[測試 ASP.NET Core 中的控制器邏輯](/aspnet/core/mvc/controllers/testing)
