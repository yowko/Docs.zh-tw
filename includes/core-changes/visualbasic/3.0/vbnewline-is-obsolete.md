---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555902"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>VbNewLine 已被淘汰

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>從 .Net Core 3.0 開始，常數會標示為[ \[ 過時 \] ](xref:System.ObsoleteAttribute) 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，已將 [過時](xref:System.ObsoleteAttribute) 的屬性套用到 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。 使用常數會產生編譯器警告。 在 .NET Framework 和舊版的 .NET Core 中，它並未標示為已淘汰。

這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。 <xref:Microsoft.VisualBasic.Constants.vbNewLine>常數相當於 `\r\n` Windows 上的換行字元序列。 在以 Unix 為基礎的系統上，換行字元是 `\n` 。

#### <a name="recommended-action"></a>建議的動作

的 [過時](xref:System.ObsoleteAttribute) 屬性訊息 <xref:Microsoft.VisualBasic.Constants.vbNewLine> 包含下列建議：

若為換行字元和換行字元，請使用 <xref:Microsoft.VisualBasic.Constants.vbCrLf> 。 針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
