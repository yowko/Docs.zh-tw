---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032019"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況

從 .NET Core 3.0 開始，當您嘗試透過呼叫來設定靜態欄位的值時，就會擲回例外狀況 <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。

#### <a name="change-description"></a>變更描述

在3.0 之前的 .NET Core .NET Framework 和版本中，您可以藉由呼叫，設定在 [c #) 中](~/docs/csharp/language-reference/keywords/readonly.md) 初始化的靜態欄位值 (readonly <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。 不過，以此方式設定這類欄位，會根據目標 framework 和優化設定產生無法預期的行為。

在 .NET Core 3.0 和更新版本中，當您在 <xref:System.Reflection.FieldInfo.SetValue%2A> 靜態、欄位上呼叫時，會擲回 <xref:System.Reflection.FieldAttributes.InitOnly> 例外狀況 <xref:System.FieldAccessException?displayProperty=nameWithType> 。

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly>欄位是一個欄位，只能在宣告或包含類別的函式中設定時設定。 換句話說，它會在初始化之後是常數。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

初始化靜態函式中的靜態、 <xref:System.Reflection.FieldAttributes.InitOnly> 欄位。 這同時適用于動態和非動態類型。

或者，您可以 <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 從欄位中移除屬性，然後呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> 。

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
