---
title: 使用 dotnet test 與 NUnit 為 .NET Core 中的 Visual Basic 進行單元測試
description: 使用 NUnit 逐步建置 Visual Basic 解決方案範例的互動式體驗，了解 .NET Core 中的單元測試概念。
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 2c8a6b86dd66b13faa242f94cf11cb940986fbd0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746872"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>使用 dotnet test 與 NUnit 為 Visual Basic .NET Core 程式庫進行單元測試

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件

- [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本。
- 您選擇的文字編輯器或程式碼編輯器。

## <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 建立名稱為 *unit-testing-vb-nunit* 的目錄來放置方案。 在此新目錄中，執行下列命令以針對類別庫與測試專案建立新方案檔：

```console
dotnet new sln
```

接著，建立 *PrimeService* 目錄。 下列大綱顯示到目前為止的檔案結構：

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

將 *PrimeService* 設為目前的目錄，然後執行下列命令以建立來源專案：

```console
dotnet new classlib -lang VB
```

將 *Class1.VB* 重新命名為 *PrimeService.VB*。 建立會失敗的 `PrimeService` 類別實作：

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

將目錄變更回 *unit-testing-vb-using-stest* 目錄。 執行下列命令，將類別庫專案新增至方案：

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>建立測試專案

接著，建立 *PrimeService.Tests* 目錄。 下列大綱顯示目錄結構：

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

將 *PrimeService.Tests* 目錄設為目前的目錄，然後使用下列命令建立新的專案：

```console
dotnet new nunit -lang VB
```

[dotnet new](../tools/dotnet-new.md) 命令會建立將 NUnit 用作測試程式庫的測試專案。 產生的範本會在 *PrimeServiceTests.vbproj* 檔案中設定測試執行器：

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。 現在，將 `PrimeService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj)中看到完整檔案。

您有下列最終方案配置：

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

在 *unit-testing-vb-nunit* 目錄中執行下列命令：

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>建立第一個測試

撰寫一個會失敗的測試，再使其通過，然後重複這個過程。 在 *PrimeService.Tests* 目錄中，將 *UnitTest1.vb* 檔案重新命名為 *PrimeService_IsPrimeShould.VB*，並將其整個內容取代為下列程式碼：

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestFixture>` 屬性指出包含測試的類別。 `<Test>` 屬性表示由測試執行器執行的方法。 從 *unit-testing-vb-nunit*，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試及類別庫，然後執行測試。 NUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 會使用您建立的單元測試專案來開始測試執行器。

您的測試失敗。 您尚未建立實作。 在可運作的 `PrimeService` 類別中撰寫最簡單的程式碼以進行此測試：

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

在 *unit-testing-vb-nunit* 目錄中，再次執行 `dotnet test`。 `dotnet test` 命令會依序執行 `PrimeService` 專案和 `PrimeService.Tests` 專案的建置。 建置這兩個專案之後，它將會執行此單一測試。 測試通過。

## <a name="adding-more-features"></a>新增更多功能

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 還有一些其他適用於下列質數的簡單案例：0、-1。 您可以使用 `<Test>` 屬性將那些案例新增為新測試，但很快就會單調乏味。 因此，還有其他 xUnit 屬性，可讓您撰寫類似的測試套件。  `<TestCase>` 屬性代表執行相同程式碼但有不同輸入引數的測試套件。 您可以使用 `<TestCase>` 屬性來指定這些輸入值。

您不需要建立新的測試，而可以改為套用這兩個屬性來建立一系列的測試，以測試數個小於 2 (最小質數) 的值：

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

執行 `dotnet test`，然後會有兩個測試失敗。 若要讓所有測試都能通過，請變更 *PrimeServices.cs* 檔案中 `Main` 方法開頭處的 `if` 子句：

```vb
if candidate < 2
```

繼續在主要程式庫中新增更多測試、更多理論和更多程式碼，以反覆執行。 您有[測試的完成版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb)和[程式庫的完整實作](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)。

您已建置好小型的程式庫和該程式庫的一組單元測試， 您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。 您已集中大部分的時間與精力以解決應用程式目標。
