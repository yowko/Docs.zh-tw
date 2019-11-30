---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643953"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>已從某些 Windows Forms 類型中移除 SerializableAttribute

<xref:System.SerializableAttribute> 已從某些沒有已知二進位序列化案例的 Windows Forms 類別中移除。

#### <a name="change-description"></a>變更描述

下列型別會使用 .NET Framework 中的 <xref:System.SerializableAttribute> 裝飾，但已在 .NET Core 中移除該屬性：

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

在過去，這個序列化機制已經有嚴重的維護和安全性考慮。 維護類型 `SerializableAttribute` 表示這些類型必須經過測試，才能進行版本對版本的序列化變更，以及可能的架構對架構序列化變更。 這會讓您更難演變這些類型，而且維護成本可能會很高。 這些類型沒有已知的二進位序列化案例，可將移除屬性的影響降至最低。

如需詳細資訊，請參閱[二進位序列化](~/docs/standard/serialization/binary-serialization.md)。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

更新可能相依于標記為 serializable 之這些類型的任何程式碼。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
