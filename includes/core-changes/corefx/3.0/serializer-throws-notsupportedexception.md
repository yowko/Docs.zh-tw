---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021572"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json 序列化器異常`JsonException`類型 從變更為`NotSupportedException`

在 .NET Core 3.0 預<xref:System.Text.Json.JsonException>覽 6 到 8 中,當序列化器遇到不支援的衍生集合類型時,將引發 。 從 .NET 核心 3.0<xref:System.NotSupportedException>預覽 9 開始 ,序列化器將拋出一個。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 預覽<xref:System.Text.Json.JsonException>6 到預覽 8 中,當序列化器遇到不支援的派生集合類型時,將引發 。 *不支援的衍生型態*是不能配置給以下類型之一的任何集合類型:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [I字典\<字串,T>](xref:System.Collections.Generic.IDictionary%602)

從 .NET Core 3.0<xref:System.NotSupportedException>預覽 9 開始 ,序列化程式將引發遇到不受支援的集合類型時。 新的異常類型更好地反映了反序列化操作失敗的原因。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

如果在反序列化時<xref:System.Text.Json.JsonException>正在捕捉,則可能需要考慮捕捉<xref:System.NotSupportedException>。

#### <a name="category"></a>類別

核心 .NET 函式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
