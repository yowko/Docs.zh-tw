---
title: 程式碼分析規則的設定檔
description: 瞭解不同的設定檔，以設定程式碼分析規則。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0d64df42ffb1763afed3e883c4f043755e158489
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633984"
---
# <a name="configuration-files-for-code-analysis-rules"></a>程式碼分析規則的設定檔

程式碼分析規則有各種不同的設定 [選項](configuration-options.md)。 您可以在下列其中一個分析器設定檔中，將這些選項指定為索引鍵/值組：

- [EditorConfig](#editorconfig) 檔案：以檔案為基礎或以資料夾為基礎的設定選項。
- [全域 AnalyzerConfig](#global-analyzerconfig) 檔：專案層級的設定選項。

## EditorConfig

[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) 檔案是用來提供 **適用于特定原始程式檔或資料夾的選項**。 選項會放置在區段標頭下，以識別適用的檔案和資料夾。 為您要設定的每個規則加入一個專案，並將它放在對應的副檔名區段下，例如 `[*.cs]` 。

```ini
[*.cs]
<option_name> = <option_value>
```

在上述範例中， `[*.cs]` 是一個 editorconfig 區段標頭，可選取目前資料夾內副檔名為 file 的所有 c # 檔案 `.cs` ，包括子資料夾。 後續的專案 `<option_name> = <option_value>` 是分析器選項，將會套用至所有 c # 檔案。

您可以藉 EditorConfig 由將檔案放在對應的目錄中，將檔案慣例套用至資料夾、專案或整個存放庫。 這些選項會在組建階段執行分析時，以及您在 Visual Studio 中編輯程式碼時套用。

如果您有現有的 *editorconfig* 檔案可用於編輯器設定，例如縮排大小或是否要修剪尾端空白字元，則可以將您的程式碼分析設定選項放在相同的檔案中。

> [!TIP]
> Visual Studio 提供 *editorconfig* 專案範本，可讓您輕鬆地將其中一個檔案新增至您的專案。 如需詳細資訊，請參閱 [將檔案新增 EditorConfig 至專案](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)。

### <a name="example"></a>範例

以下是 EditorConfig 設定選項和規則嚴重性的範例檔案：

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a>Global AnalyzerConfig

從支援 Visual Studio 2019 16.8 版和更新版本) 的 .NET 5 SDK (，您也可以使用全域 _AnalyzerConfig_ 檔來設定分析器選項。 這些檔案是用來提供套用 **至專案中所有原始** 程式檔的選項，而不論其檔案名或檔案路徑為何。

與檔案不同的 [EditorConfig](#editorconfig) 是，全域設定檔案不能用來設定 ide 的編輯器樣式設定，例如縮排大小或是否修剪尾端空白。 相反地，它們是專門用來指定專案層級的分析器設定選項。

### <a name="format"></a>格式

不同 EditorConfig 于需要區段標頭的檔案，例如 `[*.cs]` ，若要識別適用的檔案和資料夾，全域 AnalyzerConfig 檔案沒有區段標頭。 相反地，他們需要表單的最上層專案， `is_global = true` 才能與一般檔案區別 EditorConfig 。 這表示檔案中的所有選項都適用于整個專案。 例如：

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>命名

不同 EditorConfig 于必須命名的檔案， `.editorconfig` 全域設定檔不需要有特定的名稱或副檔名。 但是，如果您將這些檔案命名為，就會隱含地將這些檔案套用 `.globalconfig` 至目前資料夾（包括子資料夾）中的所有 c # 和 Visual Basic 專案。 否則，您必須明確地將 `GlobalAnalyzerConfigFiles` 專案新增至 MSBuild 專案檔：

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> 即使檔案已命名，也需要最上層專案 `is_global = true` `.globalconfig` 。

### <a name="example"></a>範例

以下是在專案層級設定選項和規則嚴重性的範例全域 AnalyzerConfig 檔案：

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a>優先順序

檔案 EditorConfig 和全域 AnalyzerConfig 檔都會指定每個選項的機碼值組。 如果有多個專案具有相同的索引鍵，但有不同的值，就會發生衝突。

### <a name="general-options"></a>一般選項

當選項之間發生衝突時，會使用下列優先順序規則來解決衝突：

- 相同設定檔中的衝突專案：在檔案中稍後出現的專案會獲勝。 這適用于單一檔案中的衝突專案 EditorConfig ，也適用于單一全域 AnalyzerConfig 檔案內。

- 兩個檔案中有衝突的專案 EditorConfig ：檔案系統中更深入的檔案專案 EditorConfig ，因此有較長的檔案路徑，wins。

- 兩個全域 AnalyzerConfig 檔中的衝突專案：會報告編譯器警告，並忽略這兩個專案。

- 檔案 EditorConfig 和全域 AnalyzerConfig 檔中的衝突專案：檔案中的專案 EditorConfig 獲勝。

### <a name="severity-options"></a>嚴重性選項

先前的 [一般優先順序規則](#general-options) 適用于設定檔中指定的所有選項。 針對 [嚴重性](configuration-options.md#severity-level) 設定選項，適用下列額外的優先順序規則：

- 在命令列中指定為編譯器選項的嚴重性選項 (`/nowarn` 或 `/warnaserror`) 一律覆寫在和全域 AnalyzerConfig 檔中指定的 [嚴重性](configuration-options.md#severity-level) 設定選項 EditorConfig 。

- 您也可以使用 [規則集](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) 檔案來指定嚴重性選項。 不過，規則集檔案已被取代 EditorConfig ，並使用全域 AnalyzerConfig 檔。 建議您 [將規則集檔案轉換成相等的檔案 EditorConfig ](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)。 規則集檔案和或全域 AnalyzerConfig 檔中的衝突嚴重性專案的優先順序未 EditorConfig _定義_。

- 如需具有不同索引鍵的相關嚴重性選項之優先順序規則的相關資訊（例如，針對單一規則指定不同的嚴重性，以及規則所屬的類別），請參閱程式 [代碼分析](configuration-options.md#precedence)的設定選項。

## <a name="see-also"></a>請參閱

- [EditorConfig vs global AnalyzerConfig 設計問題](https://github.com/dotnet/roslyn/issues/47707)
