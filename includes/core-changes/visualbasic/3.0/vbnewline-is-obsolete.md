---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116332"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>微軟.VisualBasic.Constants.vbNewline已經過時

常<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>量標記為[\[從\]](xref:System.ObsoleteAttribute).NET 核心 3.0 預覽 8 開始的過時。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 8

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 預覽 8 開始，已將<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>["過時"](xref:System.ObsoleteAttribute)屬性應用於常量。 使用常量會產生編譯器警告。 在 .NET 框架和 .NET Core 的早期版本中，它未標記為過時。

進行此更改是為了支援 Visual Basic 作為多平臺開發語言。 常<xref:Microsoft.VisualBasic.Constants.vbNewLine>量等效于`\r\n`Windows 上的折線字元序列。 在基於 Unix 的系統上，新線字元`\n`為 。

#### <a name="recommended-action"></a>建議的動作

<xref:Microsoft.VisualBasic.Constants.vbNewLine>的["過時](xref:System.ObsoleteAttribute)屬性"消息包括以下建議：

對於回車和換行，請使用<xref:Microsoft.VisualBasic.Constants.vbCrLf>。 對於當前平臺的新線，請使用<xref:System.Environment.NewLine?displayProperty=nameWithType>。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
