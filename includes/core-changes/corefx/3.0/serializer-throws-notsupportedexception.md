---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568143"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json 序列化器異常類型`JsonException`從 更改為`NotSupportedException`

在 .NET Core 3.0 預覽 6 到 8<xref:System.Text.Json.JsonException>中，當序列化器遇到不支援的派生集合類型時，將引發 。 從 .NET 核心 3.0 預覽 9 開始<xref:System.NotSupportedException>，序列化器將拋出一個。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 預覽 6 到預覽 8<xref:System.Text.Json.JsonException>中，當序列化器遇到不支援的派生集合類型時，將引發 。 *不支援的派生集合類型*是不能分配給以下類型之一的任何集合類型：

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [I字典\<字串，T>](xref:System.Collections.Generic.IDictionary%602)

從 .NET Core 3.0 預覽 9 開始<xref:System.NotSupportedException>，序列化程式將引發遇到不受支援的集合類型時。 新的異常類型更好地反映了反序列化操作失敗的原因。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

如果在反序列化時<xref:System.Text.Json.JsonException>正在捕獲，則可能需要考慮捕獲<xref:System.NotSupportedException>。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
