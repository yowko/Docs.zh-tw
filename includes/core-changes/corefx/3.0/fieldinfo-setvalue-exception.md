---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720980"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況

從 .NET Core 3.0 開始，當您嘗試藉由呼叫來設定靜態欄位的值時，就會擲回例外狀況（exception） <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。

#### <a name="change-description"></a>變更描述

在3.0 之前的 .NET Core .NET Framework 和版本中，您可以藉由呼叫，設定在初始化後是常數的靜態欄位值（[c # 中為 readonly](~/docs/csharp/language-reference/keywords/readonly.md)） <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。 不過，以這種方式設定這類欄位，會根據目標 framework 和優化設定導致無法預期的行為。

在 .NET Core 3.0 和更新版本中，當您在 <xref:System.Reflection.FieldInfo.SetValue%2A> 靜態、欄位上呼叫時，會擲回 <xref:System.Reflection.FieldAttributes.InitOnly> 例外狀況 <xref:System.FieldAccessException?displayProperty=nameWithType> 。

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly>欄位是只能在宣告時或在包含類別的函式中設定的欄位。 換句話說，它會在初始化後保持不變。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

在靜態的函式中初始化靜態、 <xref:System.Reflection.FieldAttributes.InitOnly> 欄位。 這同時適用于動態和非動態類型。

或者，您可以 <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 從欄位移除屬性，然後呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
