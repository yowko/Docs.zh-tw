---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449545"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況

從 .NET Core 3.0 開始，當您嘗試藉由呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>來設定靜態、<xref:System.Reflection.FieldAttributes.InitOnly> 欄位的值時，就會擲回例外狀況（exception）。

#### <a name="change-description"></a>變更描述

在3.0 之前的 .net Core .NET Framework 和版本中，您可以藉由呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>，設定靜態欄位在初始化後為常數的值（[在C#中為 readonly ](~/docs/csharp/language-reference/keywords/readonly.md)）。 不過，以這種方式設定這類欄位，會根據目標 framework 和優化設定導致無法預期的行為。

在 .NET Core 3.0 和更新版本中，當您在靜態 <xref:System.Reflection.FieldAttributes.InitOnly> 欄位上呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A> 時，會擲回 <xref:System.FieldAccessException?displayProperty=nameWithType> 例外狀況。

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly> 欄位只能在宣告時或在包含類別的函式中進行設定。 換句話說，它會在初始化後保持不變。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

在靜態的函式中初始化 static、<xref:System.Reflection.FieldAttributes.InitOnly> 欄位。 這同時適用于動態和非動態類型。

或者，您可以從欄位移除 <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 屬性，然後呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>。

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
