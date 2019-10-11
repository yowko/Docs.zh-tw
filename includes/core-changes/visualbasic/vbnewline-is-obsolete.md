---
ms.openlocfilehash: e476039ff9c8d33f54a2f7e4371dc09a3be557c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237307"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>VbNewLine 已過時。

從 .NET Core 3.0 Preview 8 開始，@no__t 0 常數會標示為[過時](xref:System.ObsoleteAttribute)。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 8

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 Preview 8 開始，已將[過時](xref:System.ObsoleteAttribute)屬性套用至 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。 使用常數會產生編譯器警告。 在舊版的 .NET Core 和 .NET Framework 中，它未標示為已淘汰。

這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。 @No__t-0 常數相當於 `\r\n`，也就是 Windows 上的分行符號序列。 在以 Unix 為基礎的系統上，分行符號為 `\n`。
 
#### <a name="recommended-action"></a>建議的動作

@No__t-1 的[過時](xref:System.ObsoleteAttribute)屬性訊息包含下列建議：

> 若為回車和換行，請使用[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)。 針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType>。

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
