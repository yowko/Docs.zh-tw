---
title: 使用程式碼涵蓋範圍進行單元測試
description: 瞭解如何使用適用于 .NET 單元測試的程式碼涵蓋範圍功能。
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.openlocfilehash: 98652de8e8b5c3765dfee8e1b511399bc5a0be25
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189651"
---
# <a name="use-code-coverage-for-unit-testing"></a>使用程式碼涵蓋範圍進行單元測試

單元測試有助於確保功能，並提供重構工作的驗證方法。 程式碼涵蓋範圍是測量單元測試所執行的程式碼數量，也就是行、分支或方法。 舉例來說，如果您有一個簡單的應用程式，其中只有兩個程式碼的條件式分支 (_分支 a_ 和 _分支 b_) ，則驗證條件 _分支 a_ 的單元測試將會報告分支程式碼涵蓋範圍50%。

本文討論如何使用程式碼涵蓋範圍來進行使用 Coverlet 的單元測試，以及使用 ReportGenerator 產生報表。 雖然本文著重于以 c # 和 xUnit 作為測試架構，但 MSTest 和 NUnit 也可以運作。 Coverlet 是 [GitHub 上的開放原始碼專案](https://github.com/coverlet-coverage/coverlet) ，可提供適用于 c # 的跨平臺程式碼涵蓋範圍架構。 [Coverlet](https://dotnetfoundation.org/projects/coverlet) 是 .net foundation 的一部分。 Coverlet 會收集 Cobertura 涵蓋範圍測試回合資料，用於產生報告。

此外，本文將詳細說明如何使用從 Coverlet 測試回合收集來產生報表的程式碼涵蓋範圍資訊。 您可以使用 GitHub 上的另一個 [開放原始碼專案](https://github.com/danielpalme/ReportGenerator)來產生報表 ReportGenerator。 ReportGenerator 會將 Cobertura 所產生的涵蓋範圍報表，轉換成各種格式的人類可閱讀報表。

本文是以範例瀏覽器提供的 [範例原始程式碼專案](/samples/dotnet/samples/unit-testing-code-coverage-cs)為基礎。

## <a name="system-under-test"></a>受測試的系統

「受測試的系統」指的是您撰寫單元測試的程式碼，這可能是物件、服務或任何其他可公開可測試功能的物件。 基於本文的目的，您將建立類別庫，該程式庫將會是待測系統，以及兩個對應的單元測試專案。

### <a name="create-a-class-library"></a>建立類別庫

從名為的新目錄中的命令提示字元 `UnitTestingCodeCoverage` ，使用下列命令建立新的 .net standard 類別庫 [`dotnet new classlib`](../tools/dotnet-new.md#classlib) ：

```dotnetcli
dotnet new classlib -n Numbers
```

下列程式碼片段會定義簡單的 `PrimeService` 類別，以提供檢查數位是否為質數的功能。 複製下列程式碼片段，並取代在 [*數位*] 目錄中自動建立的 *Class1.cs* 檔案內容。 將 *Class1.cs* 檔案重新命名為 *PrimeService.cs*。

```csharp
namespace System.Numbers
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            if (candidate < 2)
            {
                return false;
            }

            for (int divisor = 2; divisor <= Math.Sqrt(candidate); ++divisor)
            {
                if (candidate % divisor == 0)
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

> [!TIP]
> 值得一提的是，該 `Numbers` 類別庫已刻意新增至 `System` 命名空間。 這允許 <xref:System.Math?displayProperty=fullName> 在沒有命名空間宣告的情況下存取 `using System;` 。 如需詳細資訊，請參閱 [命名空間 (c # 參考) ](../../csharp/language-reference/keywords/namespace.md)。

### <a name="create-test-projects"></a>建立測試專案

使用下列命令，從相同的命令提示字元建立兩個新的 **XUnit 測試專案 ( .Net Core)** 範本 [`dotnet new xunit`](../tools/dotnet-new.md#test) ：

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.Collector
```

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.MSBuild
```

這兩個新建立的 xUnit 測試專案都需要加入 *數位* 類別庫的專案參考。 這是為了讓測試專案可以存取 *>primeservice* 進行測試。 從命令提示字元中，使用 [`dotnet add`](../tools/dotnet-add-reference.md) 下列命令：

```dotnetcli
dotnet add XUnit.Coverlet.Collector\XUnit.Coverlet.Collector.csproj reference Numbers\Numbers.csproj
```

```dotnetcli
dotnet add XUnit.Coverlet.MSBuild\XUnit.Coverlet.MSBuild.csproj reference Numbers\Numbers.csproj
```

*Msbuild* 專案的命名方式正確，因為它將相依于 [coverlet msbuild](https://www.nuget.org/packages/coverlet.msbuild) NuGet 套件。 藉由執行下列命令來新增此套件相依性 [`dotnet add package`](../tools/dotnet-add-package.md) ：

```dotnetcli
cd XUnit.Coverlet.MSBuild && dotnet add package coverlet.msbuild && cd ..
```

先前的命令變更目錄會有效地範圍設定為 *MSBuild* 測試專案，然後加入 NuGet 套件。 完成之後，它會接著變更目錄，逐步執行一個層級。

開啟這兩個 *UnitTest1.cs* 檔案，並將其內容取代為下列程式碼片段。 將 *UnitTest1.cs* 檔案重新命名為 *PrimeServiceTests.cs*。

```csharp
using System.Numbers;
using Xunit;

namespace XUnit.Coverlet
{
    public class PrimeServiceTests
    {
        readonly PrimeService _primeService;

        public PrimeServiceTests() => _primeService = new PrimeService();

        [
            Theory,
            InlineData(-1), InlineData(0), InlineData(1)
        ]
        public void IsPrime_ValuesLessThan2_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");

        [
            Theory,
            InlineData(2), InlineData(3), InlineData(5), InlineData(7)
        ]
        public void IsPrime_PrimesLessThan10_ReturnTrue(int value) =>
            Assert.True(_primeService.IsPrime(value), $"{value} should be prime");

        [
            Theory,
            InlineData(4), InlineData(6), InlineData(8), InlineData(9)
        ]
        public void IsPrime_NonPrimesLessThan10_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");
    }
}
```

### <a name="create-a-solution"></a>建立方案

從命令提示字元建立新的方案，以封裝類別庫和兩個測試專案。 使用 [`dotnet sln`](../tools/dotnet-sln.md) 命令：

```dotnetcli
dotnet new sln -n XUnit.Coverage
```

這會 `XUnit.Coverage` 在 *UnitTestingCodeCoverage* 目錄中建立新的解決方案檔案名。 將專案新增至方案的根。

## <a name="linux"></a>[Linux](#tab/linux)

```dotnetcli
dotnet sln XUnit.Coverage.sln add **/*.csproj --in-root
```

## <a name="windows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet sln XUnit.Coverage.sln add (ls **/*.csproj) --in-root
```

---

使用下列命令來建立方案 [`dotnet build`](../tools/dotnet-build.md) ：

```dotnetcli
dotnet build
```

如果組建成功，您已建立三個專案、適當參考的專案和套件，並正確地更新原始程式碼。 做得好！

## <a name="tooling"></a>Tooling

程式碼涵蓋範圍工具有兩種類型：

- **DataCollectors：** DataCollectors 監視測試執行，並收集測試回合的相關資訊。 他們會以各種輸出格式報告收集的資訊，例如 XML 和 JSON。 如需詳細資訊，請參閱 [您的第一個 DataCollector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/datacollector.md)。
- **報表** 產生器：使用從測試回合收集而來的資料，通常是以樣式的 HTML 來產生報表。

在本節中，焦點是在資料收集器工具上。 若要針對程式碼涵蓋範圍使用 Coverlet，現有的單元測試專案必須具有適當的封裝相依性，或是依賴 [.net 全域工具](../tools/global-tools.md) 和對應的 [Coverlet](https://www.nuget.org/packages/coverlet.console) NuGet 套件。

## <a name="integrate-with-net-test"></a>與 .NET 測試整合

XUnit 測試專案範本預設已與[coverlet 整合。](https://www.nuget.org/packages/coverlet.collector)
從命令提示字元，將目錄變更為 *XUnit. Coverlet 收集器* 專案，然後執行 [`dotnet test`](../tools/dotnet-test.md) 下列命令：

```dotnetcli
cd XUnit.Coverlet.Collector && dotnet test --collect:"XPlat Code Coverage"
```

> [!NOTE]
> `"XPlat Code Coverage"`引數是相當於 Coverlet 中資料收集器的易記名稱。 這個名稱是必要的，但不區分大小寫。

在 `dotnet test` 執行過程中，產生的 *coverage.cobertura.xml* 檔案會輸出至 *TestResults* 目錄。 XML 檔案包含結果。 這是依賴 .NET Core CLI 的跨平臺選項，很適合使用 MSBuild 的組建系統。

以下是 *coverage.cobertura.xml* 檔案的範例。

```xml
<?xml version="1.0" encoding="utf-8"?>
<coverage line-rate="1" branch-rate="1" version="1.9" timestamp="1592248008"
          lines-covered="12" lines-valid="12" branches-covered="6" branches-valid="6">
  <sources>
    <source>C:\</source>
  </sources>
  <packages>
    <package name="Numbers" line-rate="1" branch-rate="1" complexity="6">
      <classes>
        <class name="Numbers.PrimeService" line-rate="1" branch-rate="1" complexity="6"
               filename="Numbers\PrimeService.cs">
          <methods>
            <method name="IsPrime" signature="(System.Int32)" line-rate="1"
                    branch-rate="1" complexity="6">
              <lines>
                <line number="8" hits="11" branch="False" />
                <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="7" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="10" hits="3" branch="False" />
                <line number="11" hits="3" branch="False" />
                <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="57" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="15" hits="7" branch="False" />
                <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="27" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="17" hits="4" branch="False" />
                <line number="18" hits="4" branch="False" />
                <line number="20" hits="3" branch="False" />
                <line number="21" hits="4" branch="False" />
                <line number="23" hits="11" branch="False" />
              </lines>
            </method>
          </methods>
          <lines>
            <line number="8" hits="11" branch="False" />
            <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="7" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="10" hits="3" branch="False" />
            <line number="11" hits="3" branch="False" />
            <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="57" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="15" hits="7" branch="False" />
            <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="27" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="17" hits="4" branch="False" />
            <line number="18" hits="4" branch="False" />
            <line number="20" hits="3" branch="False" />
            <line number="21" hits="4" branch="False" />
            <line number="23" hits="11" branch="False" />
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
```

> [!TIP]
> 或者，如果您的組建系統已經使用 MSBuild，您也可以使用 MSBuild 封裝。 從命令提示字元，將目錄變更為 *XUnit. Coverlet* 的專案，然後執行 `dotnet test` 下列命令：
>
> ```dotnetcli
> dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=cobertura
> ```
>
> 產生的 *coverage.cobertura.xml* 檔案是輸出。  
> 您可以遵循[這裡](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/MSBuildIntegration.md)的 msbuild 整合指南

## <a name="generate-reports"></a>產生報表

現在您可以從單元測試回合收集資料，您可以使用 [ReportGenerator](https://github.com/danielpalme/ReportGenerator)來產生報表。 若要安裝 [ReportGenerator](https://www.nuget.org/packages/dotnet-reportgenerator-globaltool) NuGet 套件作為 [.net 通用工具](../tools/global-tools.md)，請使用 [`dotnet tool install`](../tools/dotnet-tool-install.md) 下列命令：

```dotnetcli
dotnet tool install -g dotnet-reportgenerator-globaltool
```

執行工具並提供所需的選項，並提供先前測試回合的輸出 *coverage.cobertura.xml* 檔案。

```console
reportgenerator
"-reports:Path\To\TestProject\TestResults\{guid}\coverage.cobertura.xml"
"-targetdir:coveragereport"
-reporttypes:Html
```

執行此命令之後，HTML 檔案表示產生的報告。

:::image type="content" source="media/test-report.png" lightbox="media/test-report.png" alt-text="單元測試產生的報表":::

## <a name="see-also"></a>另請參閱

- [Visual Studio 單元測試程式碼涵蓋範圍](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)
- [GitHub-Coverlet 儲存機制](https://github.com/coverlet-coverage/coverlet)
- [GitHub-ReportGenerator 儲存機制](https://github.com/danielpalme/ReportGenerator)
- [ReportGenerator 專案網站](https://danielpalme.github.io/ReportGenerator)
- [.NET Core CLI 測試命令](../tools/dotnet-test.md)
- [範例原始程式碼](/samples/dotnet/samples/unit-testing-code-coverage-cs)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [單元測試最佳做法](unit-testing-best-practices.md)
