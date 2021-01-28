---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957932"
---
## <a name="suppress-a-warning"></a>隱藏警告

若要隱藏規則違規，請在 EditorConfig 檔案中將特定規則識別碼的嚴重性選項設定為 `none` 。 例如：

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio 提供其他方式來隱藏程式碼分析規則的警告。 如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)。

如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)。
