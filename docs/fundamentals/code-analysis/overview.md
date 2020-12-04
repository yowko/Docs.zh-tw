---
title: .NET 中的程式碼分析
titleSuffix: ''
description: 瞭解 .NET SDK 中的原始程式碼分析。
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: ca3a9cb914befbc8e0982070b818b27ee3143793
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "96586567"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET source 程式碼分析總覽

.NET 編譯器平台 (Roslyn) 分析器會檢查 C# 或 Visual Basic 程式碼以找出程式碼品質與程式碼樣式問題。 從 .NET 5.0 開始，這些分析器即隨附於 .NET SDK。  (之前，您已將程式碼品質分析器安裝為 [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)，且程式碼樣式分析器已安裝 Visual Studio。 ) 

- [程式碼品質分析 ( "CAxxxx" 規則) ](#code-quality-analysis)
- [程式碼樣式分析 ( "IDExxxx" 規則) ](#code-style-analysis)

如果分析器發現規則違規，就會回報為建議、警告或錯誤，視每個規則的 [設定](configuration-options.md)方式而定。 程式碼分析違規的開頭會加上 "CA" 或 "IDE" 前置詞，以區別它們與編譯器錯誤。

> [!TIP]
>
> - 您也可以安裝協力廠商分析器，例如 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和 [聲納 Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)。
> - 如果您使用 Visual Studio，許多分析器規則都有相關聯的 *程式碼修正* ，可讓您套用以修正問題。 程式碼修正會顯示在燈泡圖示功能表中。

## <a name="code-quality-analysis"></a>程式碼品質分析

程式 _代碼品質分析 ( 「CA」 ) 規則_ 會檢查您的 c # 或 Visual Basic 的程式碼，以取得安全性、效能、設計和其他問題。 依預設，針對以 .NET 5.0 或更新版本為目標的專案，會啟用分析。 您可以藉由將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，在以較早 .net 版本為目標的專案上啟用程式碼分析 `true` 。 您也可以將設定為，以停用專案的程式碼分析 `EnableNETAnalyzers` `false` 。

> [!TIP]
> 在 Visual Studio 中，您可以使用 [專案屬性視窗] 來啟用或停用程式碼分析。 若要屬性視窗存取專案，請以滑鼠右鍵按一下方案總管內的專案，然後選取 [ **屬性**]。 接下來，選取 [程式 **代碼分析** ] 索引標籤，然後選取或清除核取方塊以 **啟用 .net 分析器**。

### <a name="enabled-rules"></a>啟用的規則

依預設，會在 .NET 5.0 Preview 8 中啟用下列規則。

| 診斷識別碼 | 類別 | 嚴重性 | 描述 |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | 互通性 | 警告 | 平台相容性分析器 |
| [CA1417](/visualstudio/code-quality/ca1417) | 互通性 | 警告 | 請勿 `OutAttribute` 在 P/invoke 的字串參數上使用 |
| [CA1831](/visualstudio/code-quality/ca1831) | 效能 | 警告 | `AsSpan`適當時，請使用而不是字串以範圍為基礎的索引子 |
| [CA2013](/visualstudio/code-quality/ca2013) | 可靠性 | 警告 | 請勿搭配實 `ReferenceEquals` 數值型別使用 |
| [CA2014](/visualstudio/code-quality/ca2014) | 可靠性 | 警告 | 不要 `stackalloc` 在迴圈中使用 |
| [CA2015](/visualstudio/code-quality/ca2015) | 可靠性 | 警告 | 請勿針對衍生自的類型定義完成項 <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | 使用方式 | 警告 | 必須重新擲回以保存堆疊詳細資料
| [CA2247](/visualstudio/code-quality/ca2247) | 使用方式 | 警告 | 傳遞至 >taskcompletionsource 函式的引數應該是 <xref:System.Threading.Tasks.TaskCreationOptions> 列舉，而不是 <xref:System.Threading.Tasks.TaskContinuationOptions> |

您可以變更這些規則的嚴重性來停用它們，或將它們提升為錯誤。

如需可用程式碼品質規則的完整清單，請參閱程式 [代碼品質規則](quality-rules/index.md)。

### <a name="enable-additional-rules"></a>啟用其他規則

從 .NET 5.0 RC2 開始，.NET SDK 隨附所有「CA」程式 [代碼品質規則](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)。 如需每個 .NET SDK 版本所包含之規則的完整清單，請參閱 [分析器版本](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。

#### <a name="default-analysis-mode"></a>預設分析模式

在預設的分析模式中，有些規則 [預設會啟用](#enabled-rules) 為組建警告。 某些其他規則預設為啟用，但 Visual Studio IDE 建議的對應程式碼修正。 其餘規則預設為停用。 [規則的完整清單](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)包含每個規則的預設嚴重性，以及預設的分析模式是否啟用規則。

#### <a name="custom-analysis-mode"></a>自訂分析模式

您可以 [設定程式碼分析規則](configuration-options.md) ，以啟用或停用個別規則或規則類別。 此外，您可以使用 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) 屬性來切換至下列其中一個自訂分析模式：

- _積極_ 或 _退出_ 模式：依預設會啟用所有規則作為組建警告。 您可以選擇性地 [退出宣告](configuration-options.md) 個別規則來停用它們。
- _保守_ 或 _加入宣告_ 模式：預設會停用所有規則。 您可以選擇性地 [選擇](configuration-options.md) 加入個別規則來啟用它們。

### <a name="treat-warnings-as-errors"></a>將警告視為錯誤

如果您在 `-warnaserror` 建立專案時使用旗標，則也會將所有程式碼分析警告視為錯誤。 如果您不想要將程式碼品質警告 (CAxxxx) 要被視為存在的錯誤 `-warnaserror` ，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

您仍然會看到任何程式碼分析警告，但不會中斷您的組建。

### <a name="latest-updates"></a>最新的更新

依預設，當您升級至較新版本的 .NET SDK 時，您將會取得最新的程式碼分析規則和預設規則嚴重性。 如果您不想要此行為，例如，如果您想要確保沒有啟用或停用任何新規則，您可以透過下列其中一種方式來覆寫它：

- 將 `AnalysisLevel` MSBuild 屬性設定為特定值，以將警告鎖定至該集合。 當您升級至較新的 SDK 時，仍會收到這些警告的錯誤修正，但不會啟用任何新的警告，也不會停用任何現有的警告。 例如，若要將規則集鎖定為 .NET SDK 5.0 版隨附的規則，請將下列專案新增至您的專案檔。

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > 屬性的預設值 `AnalysisLevel` 是 `latest` ，這表示當您移至較新版本的 .net SDK 時，一律會取得最新的程式碼分析規則。

  如需詳細資訊，以及查看可能值的清單，請參閱 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)。

- 安裝 [CodeAnalysis NetAnalyzers NuGet 套件](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) ，以從 .net SDK 更新分離規則更新。 如果 SDK 包含的分析器元件版本比 NuGet 套件還新，則安裝套件會關閉內建的 SDK 分析器，並產生組建警告。

## <a name="code-style-analysis"></a>程式碼樣式分析

程式[代碼樣式分析](/visualstudio/ide/editorconfig-code-style-settings-reference) ( "IDExxxx" 規則) 可讓您在程式碼基底中定義和維護一致的程式碼樣式。 以下是預設設定：

- 命令列組建：針對命令列組建上的所有 .NET 專案，預設會停用程式碼樣式分析。
- Visual Studio：程式碼樣式分析預設會針對 Visual Studio 中的所有 .NET 專案啟用，因為程式 [代碼會重構快速動作](/visualstudio/ide/code-generation-in-visual-studio)。

從 .NET 5.0 RC2 開始，您可以在命令列和 Visual Studio 內啟用組建的程式碼樣式分析。 程式碼樣式違規會顯示為「IDE」前置詞的警告或錯誤。 這可讓您在組建階段強制執行一致的程式碼樣式。

> [!NOTE]
> 程式碼樣式分析功能是實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。

在組建上啟用程式碼樣式分析的步驟：

1. 將 MSBuild 屬性 [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) 設定為 `true` 。

1. 在 *editorconfig* 檔案中，將您想要在組建上執行的每個「IDE」程式碼樣式規則 [設定](configuration-options.md) 為警告或錯誤。 例如：

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   或者，您可以將整個「樣式」類別設定為警告或錯誤（依預設，），然後選擇性地關閉您不想在組建上執行的規則。 例如：

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a>隱藏警告

若要隱藏規則違規，請在 EditorConfig 檔案中將該規則識別碼的嚴重性選項設定為 `none` 。 例如：

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio 提供其他方式來隱藏程式碼分析規則的警告。 如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)。

如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](configuration-options.md#severity-level)。

## <a name="see-also"></a>另請參閱

- [程式碼品質分析規則參考](quality-rules/index.md)
- [程式碼樣式分析規則參考](style-rules/index.md)
- [Visual Studio 中的程式碼分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [教學課程：撰寫您的第一個分析器和程式碼修正](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
