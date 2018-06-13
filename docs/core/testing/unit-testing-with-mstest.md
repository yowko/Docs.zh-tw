---
title: 使用 MSTest 與 .NET Core 為 C# 進行單元測試
description: 透過逐步使用 dotnet test 和 MSTest 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: b76e577d3950dd13b038f47c1b133e3529867c38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216092"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>使用 MSTest 與 .NET Core 為 C# 進行單元測試

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

### <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 建立名稱為 *unit-testing-using-dotnet-test* 的目錄來放置方案。 在此新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以針對類別庫與測試專案建立新方案檔。 接著，建立 *PrimeService* 目錄。 下列大綱顯示到目前為止的目錄與檔案結構：

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

將 *PrimeService* 設為目前的目錄，然後執行 [`dotnet new classlib`](../tools/dotnet-new.md) 以建立來源專案。 將 *Class1.cs* 重新命名為 *PrimeService.cs*。 為了使用測試導向開發 (TDD)，您會建立 `PrimeService` 類別的失敗實作：

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

將目錄變更回 *unit-testing-using-mstest* 目錄。 執行 [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。 

### <a name="creating-the-test-project"></a>建立測試專案

接著，建立 *PrimeService.Tests* 目錄。 下列大綱顯示目錄結構：

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new mstest`](../tools/dotnet-new.md) 建立新的專案。 dotnet new 命令會建立將 MStest 作為測試程式庫使用的測試專案。 產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new` 已新增 MSTest SDK、MSTest 測試架構和 MSTest 執行器。 現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

下列大綱顯示最終方案配置：

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

執行 *unit-testing-using-dotnet-test* 目錄中的 [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md)。 

## <a name="creating-the-first-test"></a>建立第一個測試

TDD 方法需要寫入一個失敗的測試，使其通過，然後重複該程序。 從 *PrimeService.Tests* 目錄移除 *UnitTest1.cs*，然後使用下列內容建立名為 *PrimeService_IsPrimeShould.cs* 的新 C# 檔案：

```csharp
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

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestClass]` 屬性代表包含單元測試的類別。 `[TestMethod]` 屬性指出方法是測試方法。 

儲存此檔案並執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。 MSTest 測試執行器包含執行測試的程式進入點。 `dotnet test` 會使用您建立的單元測試專案來開始測試執行器。

您的測試失敗。 您尚未建立實作。 在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以讓此測試成功：

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

在 *unit-testing-using-mstest* 目錄中，重新執行 `dotnet test`。 `dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。 建置這兩個專案之後，它將會執行此單一測試。 測試通過。

## <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[TestMethod]` 屬性來加入新測試，但很快就會單調乏味。 因此，還有其他 MSTest 屬性，可讓您撰寫類似的測試套件。  `[DataTestMethod]` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。 您可以使用 `[DataRow]` 屬性來指定這些輸入值。

您不需要建立新測試，只要套用這兩個屬性以建立單一資料驅動測試即可。 資料驅動測試是一種方法，這種方法會測試數個低於二 (最小的質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

執行 `dotnet test`，然後會有兩個測試失敗。 若要使所有測試通過，請變更方法開頭的 `if` 子句：

```csharp
if (candidate < 2)
```

繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試， 您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。 您已集中大部分的時間與精力以解決應用程式目標。
