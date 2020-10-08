---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844498"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a>JsonSerializer。還原序列化需要單一字元字串

當型別參數是時 <xref:System.Char> ，的字串引數 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 必須包含單一字元才能成功還原序列化。

#### <a name="change-description"></a>變更描述

在先前的 .NET 版本中，如果您將多個字元的字串傳遞至 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ，且類型參數是，則還原序列化會 <xref:System.Char> 成功，而且只會還原序列化第一個字元。

在 .NET 5.0 和更新版本中，當型別參數是時 <xref:System.Char> ，傳遞單一字元字串以外的任何字元都會導致擲回 <xref:System.Text.Json.JsonException> 。

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="reason-for-change"></a>變更的原因

<xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 將表示單一 JSON 值的文字，剖析成泛型型別參數所指定之類型的實例。 只有當提供的裝載對指定的泛型型別參數有效時，才會成功剖析。 對於實 <xref:System.Char> 值型別而言，有效承載是單一字元字串。

#### <a name="recommended-action"></a>建議的動作

使用將字串剖析為 <xref:System.Char> 型別時 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ，請確定字串是由單一字元所組成。

#### <a name="category"></a>類別

序列化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->
