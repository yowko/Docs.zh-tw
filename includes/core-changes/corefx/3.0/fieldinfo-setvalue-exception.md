---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021616"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>欄位資訊.SetValue 引發靜態、僅 it 欄位的異常

從 .NET Core 3.0 開始,當您<xref:System.Reflection.FieldAttributes.InitOnly><xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>嘗試通過調用 在靜態欄位上設置值時,將引發異常。

#### <a name="change-description"></a>變更描述

在 .NET 框架和 .NET Core 版本之前為 3.0,可以通過調用<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>來設置靜態欄位的值,該靜態欄位在初始化後為常量(在[C# 中唯讀](~/docs/csharp/language-reference/keywords/readonly.md))。 但是,以這種方式設置這樣的欄位會導致基於目標框架和優化設置的不可預知行為。

在 .NET Core 3.0<xref:System.Reflection.FieldInfo.SetValue%2A>和更高版本中 ,當<xref:System.Reflection.FieldAttributes.InitOnly>您調用靜<xref:System.FieldAccessException?displayProperty=nameWithType>態 欄位時, 將引發異常。

> [!TIP]
> 欄位<xref:System.Reflection.FieldAttributes.InitOnly>是只能在聲明欄位時或在包含類的構造函數中設置的欄位。 換句話說,它是在初始化后不變的。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

初始化靜態構造<xref:System.Reflection.FieldAttributes.InitOnly>函數中的靜態欄位。 這適用於動態類型和非動態類型。

或者,可以從欄位中刪除<xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType>該屬性,然後呼<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>叫 。

#### <a name="category"></a>類別

核心 .NET 函式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
