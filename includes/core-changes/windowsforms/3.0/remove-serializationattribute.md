---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643953"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>從某些 Windows 表單類型中刪除的可序列化屬性

<xref:System.SerializableAttribute>已從某些沒有已知二進位序列化方案的 Windows 表單類中刪除。

#### <a name="change-description"></a>變更描述

以下類型使用<xref:System.SerializableAttribute>in .NET 框架進行修飾，但在 .NET Core 中刪除了該屬性：

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

從歷史上看，這種序列化機制一直有著嚴重的維護和安全問題。 保持`SerializableAttribute`類型意味著必須測試這些類型的版本到版本序列化更改和潛在的框架到框架序列化更改。 這使得發展這些類型變得更加困難，而且維護成本可能很高。 這些類型沒有已知的二進位序列化方案，這最大限度地減少了刪除屬性的影響。

有關詳細資訊，請參閱[二進位序列化](~/docs/standard/serialization/binary-serialization.md)。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

更新可能依賴于標記為可序列化的任何代碼。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
