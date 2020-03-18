---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449545"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>欄位資訊.SetValue 引發靜態、僅 it 欄位的異常

從 .NET Core 3.0 開始，當您嘗試通過調用<xref:System.Reflection.FieldAttributes.InitOnly><xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>在靜態欄位上設置值時，將引發異常。

#### <a name="change-description"></a>變更描述

在 .NET 框架和 .NET Core 版本之前為 3.0，可以通過調用<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>來設置靜態欄位的值，該靜態欄位在初始化後為常量（在[C# 中唯讀](~/docs/csharp/language-reference/keywords/readonly.md)）。 但是，以這種方式設置這樣的欄位會導致基於目標框架和優化設置的不可預知行為。

在 .NET Core 3.0 和更高版本中<xref:System.Reflection.FieldInfo.SetValue%2A>，當您調用靜態<xref:System.Reflection.FieldAttributes.InitOnly>欄位時，<xref:System.FieldAccessException?displayProperty=nameWithType>將引發異常。

> [!TIP]
> 欄位<xref:System.Reflection.FieldAttributes.InitOnly>是只能在聲明欄位時或在包含類的建構函式中設置的欄位。 換句話說，它是在初始化後不變的。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

初始化靜態構造<xref:System.Reflection.FieldAttributes.InitOnly>函數中的靜態欄位。 這適用于動態類型和非動態類型。

或者，可以從欄位中刪除<xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType>該屬性，然後調用<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
