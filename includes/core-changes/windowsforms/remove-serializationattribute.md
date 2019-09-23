---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181765"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>已從某些 Windows Forms 類型中移除 SerializableAttribute

<xref:System.SerializableAttribute>已從某些沒有已知二進位序列化案例的 Windows Forms 類別中移除。

#### <a name="change-description"></a>變更描述

下列型別會使用中的<xref:System.SerializableAttribute>來裝飾 .NET Framework 中的，但已移除 .net Core 中的屬性：

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

在過去，這個序列化機制已經有嚴重的維護和安全性考慮。 維護`SerializableAttribute`類型表示這些類型必須經過測試，才能進行版本對版本的序列化變更，以及可能的架構對架構序列化變更。 這會讓您更難演變這些類型，而且維護成本可能會很高。 這些類型沒有已知的二進位序列化案例，可將移除屬性的影響降至最低。

如需詳細資訊，請參閱<https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

更新可能相依于標記為 serializable 之這些類型的任何程式碼。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->