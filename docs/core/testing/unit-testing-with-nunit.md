---
title: 利用 NUnit 與 .NET Core 進行 C# 單元測試
description: 使用 dotnet test 與 NUnit 逐步建置解決方案範例的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: rprouse
ms.date: 12/01/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: db11adf265b2a08456a1bd42bc8a6847ba70a2ce
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>利用 NUnit 與 .NET Core 進行 C# 單元測試

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 建立名稱為 *unit-testing-using-nunit* 的目錄來放置解決方案。 在此新目錄中，執行 [`dotnet new sln`](../tools/dotnet-new.md) 以針對類別庫與測試專案建立新方案檔。 接著，建立 *PrimeService* 目錄。 下列大綱顯示到目前為止的目錄與檔案結構：

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
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

將目錄變更回 *unit-testing-using-nunit* 目錄。 執行 [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) 以將類別庫專案加入方案中。

## <a name="install-the-nunit-project-template"></a>安裝 NUnit 專案範本

必須安裝 NUnit 專案範本，才可建立測試專案。 這項作業在您想要建立新的 NUnit 專案之每部開發人員電腦上，只需執行一次即可。 執行 [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) 以安裝 NUnit 範本。

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a>建立測試專案

接著，建立 *PrimeService.Tests* 目錄。 下列大綱顯示目錄結構：

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用 [`dotnet new nunit`](../tools/dotnet-new.md) 建立新的專案。 dotnet new 命令會建立將 NUnit 用作為測試程式庫的測試專案。 產生的範本會在 *PrimeServiceTests.csproj* 檔案中設定測試執行器：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new`，新增了 Microsoft 測試 SDK、NUnit 測試架構以及 NUnit 測試配接器。 現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj)中看到完整檔案。

下列大綱顯示最終方案配置：

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
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
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestFixture]` 屬性代表包含單元測試的類別。 `[Test]` 屬性指出方法是測試方法。

儲存此檔案並執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。 NUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 會使用您建立的單元測試專案來開始測試執行器。

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

在 *unit-testing-using-nunit* 目錄中，再次執行 `dotnet test`。 `dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。 建置這兩個專案之後，它將會執行此單一測試。 測試通過。

## <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 還有一些其他適用於質數 0、-1 的簡單案例。 您可以使用 `[Test]` 屬性來加入新測試，但很快就會單調乏味。 另有其他 NUnit 屬性可供您撰寫類似測試的套件。  `[TestCase]` 屬性可用於建立執行相同程式碼，但輸入引數不同的測試套件。 您可以使用 `[TestCase]` 屬性來指定這些輸入值。

您不需要建立新的測試，只要套用此屬性來建立單一資料驅動型測試即可。 資料驅動型測試是一種測試方法，其會測試數個低於二 (最小質數) 的值：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

執行 `dotnet test`，然後會有兩個測試失敗。 若要使所有測試通過，請變更方法開頭的 `if` 子句：

```csharp
if (candidate < 2)
```

繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)。

您已建置好小型的程式庫和該程式庫的一組單元測試， 您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。 您已集中大部分的時間與精力以解決應用程式目標。
