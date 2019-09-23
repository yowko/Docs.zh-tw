---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182081"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>VbNewLine 已過時。

從<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> .net Core 3.0 Preview 8 開始，常數會標示為[過時](xref:System.ObsoleteAttribute)。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="details"></a>詳細資料

從 .net Core 3.0 Preview 8 開始，已將[過時](xref:System.ObsoleteAttribute)屬性套用至<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>常數。 使用常數會產生編譯器警告。 在舊版的 .NET Core 和 .NET Framework 中，它未標示為已淘汰。

這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。 常數相當於`\r\n`，也就是 Windows 上的分行符號序列。 `vbNewLine` 在以 Unix 為基礎的系統上，換`\n`行字元是。
 
#### <a name="recommended-action"></a>建議的動作

的[過時](xref:System.ObsoleteAttribute)屬性訊息`vbNewLine`包含下列建議：

> 若為回車和換行，請使用[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)。 針對目前平臺的新行，請<xref:System.Environment.NewLine?displayProperty=nameWithType>使用。

#### <a name="category"></a>分類

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

