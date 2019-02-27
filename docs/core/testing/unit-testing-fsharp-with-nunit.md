---
title: 使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 進行單元測試
description: 使用 dotnet test 與 NUnit 逐步建置解決方案範例的互動式體驗，了解 .NET Core 中 F# 的單元測試概念。
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 384d0ac9f36f9ef9daba851f52d577d97248cd67
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746042"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>使用 dotnet test 與 NUnit 為 .NET Core 中的 F# 程式庫進行單元測試

本教學課程會引導您逐步進行建置範例方案的互動式體驗，以了解單元測試概念。 如果您想要使用預先建置的方案進行教學課程，請在開始之前[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件

- [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本。
- 您選擇的文字編輯器或程式碼編輯器。

## <a name="creating-the-source-project"></a>建立來源專案

開啟 Shell 視窗。 建立名為 *unit-testing-with-fsharp* 的目錄來放置方案。
在此新目錄中，執行下列命令以針對類別庫與測試專案建立新方案檔：

```console
dotnet new sln
```

接下來，建立 *MathService* 目錄。 下列大綱顯示到目前為止的目錄與檔案結構：

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

將 *MathService* 設為目前的目錄，然後執行下列命令以建立來源專案：

```console
dotnet new classlib -lang F#
```

您建立數學服務的失敗實作：

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

將目錄變更回 *unit-testing-with-fsharp* 目錄。 執行下列命令，將類別庫專案新增至方案：

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a>建立測試專案

接著，建立 *MathService.Tests* 目錄。 下列大綱顯示目錄結構：

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

將 *MathService.Tests* 目錄設為目前的目錄，然後使用下列命令建立新的專案：

```console
dotnet new nunit -lang F#
```

如此會建立將 NUnit 用作為測試架構的測試專案。 產生的範本會在 *MathServiceTests.fsproj* 中設定測試執行器：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

測試專案需要其他套件來建立和執行單元測試。 上一個步驟中的 `dotnet new` 新增了 NUnit 與 NUnit 測試配接器。 現在，將 `MathService` 類別庫新增為專案的另一個相依性。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```console
dotnet add reference ../MathService/MathService.fsproj
```

您可以在 GitHub 的[範例存放庫](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)中看到完整檔案。

您有下列最終方案配置：

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

在 *unit-testing-with-fsharp* 目錄中執行下列命令：

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>建立第一個測試

您會撰寫一個失敗測試，讓它通過，然後重複此程序。 開啟 *UnitTest1.fs* 並新增下列程式碼：

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

`[<TestFixture>]` 屬性表示包含測試的類別。 `[<Test>]` 屬性表示由測試執行器執行的測試方法。 從 *unit-testing-with-fsharp* 目錄，執行 [`dotnet test`](../tools/dotnet-test.md) 來建置測試和類別庫，然後執行測試。 NUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 會使用您建立的單元測試專案來開始測試執行器。

這兩個測試會顯示最基本的成功和失敗測試。 `My test` 成功，而 `Fail every time` 失敗。 現在，針對 `squaresOfOdds` 方法建立測試。 `squaresOfOdds` 方法會傳回屬於輸入序列一部分的所有奇數整數值平方序列。 您能以反覆方式建立會驗證功能的測試，而不需要嘗試一次撰寫所有那些函式。 將每個測試設定為通過表示為方法建立必要功能。

我們所能撰寫的最簡單測試是呼叫 `squaresOfOdds` 並傳遞所有偶數，其中結果應該是空整數序列。  該測試如下：

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

請注意，`expected` 序列已被轉換為清單。 NUnit 架構依賴數個標準 .NET 類型。 該相依性表示您的公用介面與預期結果支援 <xref:System.Collections.ICollection>，而非 <xref:System.Collections.IEnumerable>。

當您執行該測試時，您會看到您的測試失敗。 您尚未建立實作。 透過在可運作之 MathService 專案的 *Library.fs* 類別中撰寫最簡單的程式碼，來使此測試通過：

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

在 *unit-testing-with-fsharp* 目錄中，重新執行 `dotnet test`。 `dotnet test` 命令會依序執行 `MathService` 專案和 `MathService.Tests` 專案的建置。 建置這兩個專案之後，它會執行您的測試。 現在通過兩個測試了。

## <a name="completing-the-requirements"></a>完成需求

現在，您已經讓一個測試順利通過，您可以撰寫更多測試。 下一個簡單案例可搭配所具有的唯一奇數是 `1` 的序列運作。 數字 1 比較簡單，因為 1 的平方是 1。 該下一個測試如下：

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

執行 `dotnet test` 會使得新測試失敗。 您必須更新 `squaresOfOdds` 方法以處理此新測試。 您必須將所有偶數從序列中篩選出來，以使此測試通過。 您可以透過撰寫小型篩選函式並使用 `Seq.filter` 來完成此動作：

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

請注意對 `Seq.toList` 的呼叫。 那會建立清單，該清單會實作 <xref:System.Collections.ICollection> 介面。

還有一個步驟必須執行：計算每個奇數的平方。 透過撰寫新測試以開始：

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

您可以透過將已篩選的序列以管線方式傳遞到對應作業，以計算每個奇數的平方，來修正測試：

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

您已建置好小型的程式庫和該程式庫的一組單元測試， 您已建立方案結構，因此加入新套件與測試是一般工作流程的一部分。 您已集中大部分的時間與精力以解決應用程式目標。