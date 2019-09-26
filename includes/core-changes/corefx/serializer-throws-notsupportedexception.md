---
ms.openlocfilehash: a35439efce25db94e70420fc6aeaf04816525758
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263308"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json 序列化程式例外狀況類型`JsonException`已從變更為`NotSupportedException`

在 .net Core 3.0 Preview 6 到8中， <xref:System.Text.Json.JsonException>當序列化程式遇到不受支援的衍生集合類型時，就會擲回。 從 .net Core 3.0 Preview 9 開始，序列化程式會擲<xref:System.NotSupportedException>回，改為擲回。

#### <a name="change-description"></a>變更描述

在 .net Core 3.0 preview 6 到 preview 8 中， <xref:System.Text.Json.JsonException>當序列化程式遇到不受支援的衍生集合類型時，就會擲回。 不*支援的衍生集合類型*是無法指派給下列其中一種類型的任何集合類型：

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>`
- <xref:System.Collections.IDictionary>
- [IDictionary\<字串，T >](xref:System.Collections.Generic.IDictionary%602)

從 .net Core 3.0 Preview 9 開始， <xref:System.NotSupportedException>當遇到不支援的集合類型時，序列化程式會擲回。 新的例外狀況類型更清楚地反映了還原序列化作業失敗的原因。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

如果您<xref:System.Text.Json.JsonException>在還原序列化時攔截到，您可能會想要<xref:System.NotSupportedException>考慮也要攔截。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
