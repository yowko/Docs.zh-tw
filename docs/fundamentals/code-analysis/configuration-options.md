---
title: 設定程式碼分析規則
description: 瞭解如何在分析器設定檔中設定程式碼分析規則。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 4f7b392a2b066023fec75c5295bd94651654d645
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851786"
---
# <a name="configuration-options-for-code-analysis"></a>程式碼分析的設定選項

程式碼分析規則有各種不同的設定選項。 這些選項會在 [分析器設定檔](configuration-files.md) 中使用語法指定為索引鍵/值組 `<option key> = <option value>` 。

您將設定的最常見選項是 [規則的嚴重性](#severity-level)。 您可以設定所有分析器規則的嚴重性層級，包括程式 [代碼品質規則](quality-rules/index.md) 和程式 [代碼樣式規則](style-rules/index.md)。 例如，若要啟用規則做為警告，您可以將下列索引鍵/值組新增至檔案 EditorConfig 。

`dotnet_diagnostic.<rule ID>.severity = warning`

您也可以設定其他選項來自訂規則行為：

- 程式碼品質規則有 [其他選項](code-quality-rule-options.md) 可設定行為，例如規則應套用的方法名稱。
- 程式碼樣式規則有 [自訂程式碼樣式選項](code-style-rule-options.md)。
- 協力廠商分析器規則可以使用自訂索引鍵名稱和值格式來定義自己的設定選項。

在 [分析器設定檔](configuration-files.md) 中設定特定規則嚴重性的語法如下：

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a>一般選項

這些選項適用于整個程式碼分析。 它們不能只套用至單一規則或一組規則。

### <a name="exclude-generated-code"></a>排除產生的程式碼

您可以藉由將 `generated_code = true | false` 專案新增至 [設定檔](configuration-files.md)，來將其他檔案和資料夾視為產生的程式碼。 .NET 程式碼分析器警告在產生的程式碼檔（例如，設計工具產生的檔案）上並不實用，使用者無法編輯這些檔案來修正任何違規。 在大多數情況下，程式碼分析器會略過產生的程式碼檔案，而不會報告這些檔案的違規。

依預設，具有特定副檔名或自動產生之檔案標頭的檔案會被視為產生的程式碼檔案。 例如，以或結尾的檔案名 `.designer.cs` `.generated.cs` 會視為產生的程式碼。 此設定選項可讓您指定其他命名模式。

例如，若要將名稱結尾為的所有檔案視為產生的程式 `.MyGenerated.cs` 代碼，請新增下列專案：

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a>規則特定選項

規則特定選項可以套用至單一規則、一組規則或所有規則。 規則特定的選項包括：

- [規則嚴重性層級](#severity-level)
- [*程式碼品質規則的* 特定選項](code-quality-rule-options.md)

### <a name="severity-level"></a>嚴重性層級

下表顯示您可以為所有分析器規則（包括程式 [代碼品質](quality-rules/index.md) 和程式 [代碼樣式](style-rules/index.md) 規則）設定的不同規則嚴重性。

| Severity | 組建階段行為 |
|-|-|
| `error` | 違規會顯示為組建 *錯誤* ，導致組建失敗。|
| `warning` | 違規會顯示為組建 *警告* ，但不會造成組建失敗 (除非您有選項設定為 [錯誤時將警告視為錯誤]) 。 |
| `suggestion` | 違規在 Visual Studio IDE 中會顯示為組建 *訊息* 和建議。 |
| `silent` | 使用者看不到違規。 |
| `none` | 規則已完全隱藏。 |
| `default` | 使用規則的預設嚴重性。 |

> [!TIP]
> 如需有關 Visual Studio 中的規則嚴重性如何呈現的詳細資訊，請參閱 [嚴重性層級](/visualstudio/ide/editorconfig-language-conventions#severity-levels)。

#### <a name="scope"></a>影響範圍

若要設定單一規則的規則嚴重性，請使用下列語法。

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

若要設定分析器規則類別的預設規則嚴重性，請使用下列語法。

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

若要設定所有分析器規則的預設規則嚴重性，請使用下列語法。

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a>優先順序

如果您有多個可套用至相同規則識別碼的嚴重性設定專案，則會依下列順序選擇優先級：

- 依識別碼個別規則的專案會優先于類別目錄的專案。
- 分類的專案優先于所有分析器規則的專案。

請考慮下列範例，其中 [CA1822](/visualstudio/code-quality/ca1822) 具有「效能」類別：

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

在上述範例中，這三個嚴重性專案都適用于 CA1822。 不過，使用指定的優先順序規則時，第一個以規則識別碼為基礎的專案會優先于下一個專案。 在此範例中，CA1822 會具有的有效嚴重性 `error` 。 「效能」類別中的所有其他規則都會具有的嚴重性 `warning` 。

如需有關如何決定檔案間優先順序的詳細資訊，請參閱 [設定檔檔的「優先順序」一節](configuration-files.md#precedence)。
