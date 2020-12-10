---
title: .NET 中的程式碼分析
titleSuffix: ''
description: 瞭解 .NET SDK 中的原始程式碼分析。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 2f59b97de6f92e5a9bf927e1318286e400017dad
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009842"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET source 程式碼分析總覽

.NET 編譯器平台 (Roslyn) 分析器會檢查 C# 或 Visual Basic 程式碼以找出程式碼品質與程式碼樣式問題。 從 .NET 5.0 開始，這些分析器會隨附于 .NET SDK 中，您不需要個別安裝。 如果您的專案是以 .NET 5 或更新版本為目標，則預設會啟用程式碼分析。 如果您的專案以不同的 .NET 執行為目標（例如，.NET Core、.NET Standard 或 .NET Framework），您必須將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，以手動方式啟用程式碼分析 `true` 。

如果您不想要移至 .NET 5 + SDK，或您偏好以 NuGet 套件為基礎的模型，也可以在 [CodeAnalysis. NetAnalyzers NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)中找到分析器。 您可能偏好以套件為基礎的模型來進行隨選版本更新。

> [!NOTE]
> .NET 分析器與目標架構無關。 也就是說，您的專案不需要以特定的 .NET 實作為目標。 分析器適用于以 `net5.0` 和舊版 .net 版本為目標的專案，例如 `netcoreapp3.1` 和 `net472` 。

如果分析器發現規則違規，就會回報為建議、警告或錯誤，視每個規則的 [設定](configuration-options.md)方式而定。 程式碼分析違規的開頭會加上 "CA" 或 "IDE" 前置詞，以區別它們與編譯器錯誤。

## <a name="code-quality-analysis"></a>程式碼品質分析

程式 *代碼品質分析* ( "CAxxxx" ) 規則會檢查您的 c # 或 Visual Basic 程式碼，以取得安全性、效能、設計和其他問題。 依預設，針對以 .NET 5.0 或更新版本為目標的專案，會啟用分析。 您可以藉由將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，在以較早 .net 版本為目標的專案上啟用程式碼分析 `true` 。 您也可以將設定為，以停用專案的程式碼分析 `EnableNETAnalyzers` `false` 。

> [!TIP]
> 如果您使用 Visual Studio：
>
> - 許多分析器規則都有相關聯的 *程式碼修正* ，可讓您修正問題。 程式碼修正會顯示在燈泡圖示功能表中。
> - 您可以在方案總管中的專案上按一下滑鼠右鍵，然後選取 [**屬性** 程式  >  **代碼分析**] 索引標籤 >**啟用 .net 分析器**，藉以啟用或停用程式碼分析。

### <a name="enabled-rules"></a>啟用的規則

依預設，會在 .NET 5.0 中啟用下列規則。

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

您可以變更這些規則的嚴重性來停用它們，或將它們提升為錯誤。 您也可以 [啟用更多規則](#enable-additional-rules)。

- 如需每個 .NET SDK 版本所包含的規則清單，請參閱 [分析器版本](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。
- 如需所有程式碼品質規則的清單，請參閱程式 [代碼品質規則](quality-rules/index.md)。

### <a name="enable-additional-rules"></a>啟用其他規則

*分析模式* 指的是預先定義的程式碼分析設定，其中未啟用任何、部分或所有規則。 在預設的分析模式中，只會啟用少量的規則 [作為組建警告](#enabled-rules)。 您可以藉由在專案檔中設定 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) 屬性，來變更專案的分析模式。 允許的值為：

| 值 | 描述 |
| - | - |
| `AllDisabledByDefault` | 這是最保守的模式。 預設會停用所有規則。 您可以選擇性地 [選擇](configuration-options.md) 加入個別規則來啟用它們。<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | 這是最積極的模式。 所有規則都會啟用為組建警告。 您可以選擇性地 [退出宣告](configuration-options.md) 個別規則來停用它們。<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | 預設模式會啟用數個規則做為警告，其他則只會啟用為具有對應程式碼修正的 Visual Studio IDE 建議，其餘部分則會完全停用。 您可以選擇性地 [加入宣告或退出](configuration-options.md) 個別規則來停用它們。<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

若要尋找每個可用規則的預設嚴重性，以及是否在預設分析模式中啟用規則，請參閱 [完整的規則清單](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。

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

程式 *代碼樣式分析* ( "IDExxxx" ) 規則可讓您在程式碼基底中定義和維護一致的程式碼樣式。 預設啟用設定為：

- 命令列組建：針對命令列組建上的所有 .NET 專案，預設會停用程式碼樣式分析。
- Visual Studio：程式碼樣式分析預設會針對 Visual Studio 中的所有 .NET 專案啟用，因為程式 [代碼會重構快速動作](/visualstudio/ide/code-generation-in-visual-studio)。

從 .NET 5.0 開始，您可以在命令列和 Visual Studio 內啟用組建的程式碼樣式分析。 程式碼樣式違規會顯示為「IDE」前置詞的警告或錯誤。 這可讓您在組建階段強制執行一致的程式碼樣式。

如需程式碼樣式分析規則的完整清單，請參閱程式 [代碼樣式規則](style-rules/index.md)。

### <a name="enable-on-build"></a>在組建時啟用

遵循下列步驟來啟用組建的程式碼樣式分析：

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

> [!NOTE]
> 程式碼樣式分析功能是實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。

## <a name="suppress-a-warning"></a>隱藏警告

若要隱藏規則違規，請在 EditorConfig 檔案中將該規則識別碼的嚴重性選項設定為 `none` 。 例如：

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio 提供其他方式來隱藏程式碼分析規則的警告。 如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)。

如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](configuration-options.md#severity-level)。

## <a name="third-party-analyzers"></a>第三方分析器

除了正式的 .NET 分析器，您也可以安裝協力廠商分析器，例如 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和 [聲納 Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)。

## <a name="see-also"></a>請參閱

- [程式碼品質分析規則參考](quality-rules/index.md)
- [程式碼樣式分析規則參考](style-rules/index.md)
- [Visual Studio 中的程式碼分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [教學課程：撰寫您的第一個分析器和程式碼修正](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
