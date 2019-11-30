---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568143"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json 序列化程式例外狀況類型已從 `JsonException` 變更為 `NotSupportedException`

在 .NET Core 3.0 Preview 6 到8中，當序列化程式遇到不受支援的衍生集合類型時，會擲回 <xref:System.Text.Json.JsonException>。 從 .NET Core 3.0 Preview 9 開始，序列化程式會改為擲回 <xref:System.NotSupportedException>。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 Preview 6 到 Preview 8 中，當序列化程式遇到不受支援的衍生集合類型時，會擲回 <xref:System.Text.Json.JsonException>。 不*支援的衍生集合類型*是無法指派給下列其中一種類型的任何集合類型：

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [IDictionary\<字串，T >](xref:System.Collections.Generic.IDictionary%602)

從 .NET Core 3.0 Preview 9 開始，當遇到不支援的集合類型時，序列化程式會擲回 <xref:System.NotSupportedException>。 新的例外狀況類型更清楚地反映了還原序列化作業失敗的原因。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

如果您要在還原序列化時攔截 <xref:System.Text.Json.JsonException>，您可能會想要考慮同時捕捉 <xref:System.NotSupportedException>。

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
