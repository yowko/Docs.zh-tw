---
title: 重大變更：索引鍵/值組接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項
description: 瞭解在序列化和還原序列化索引鍵/值組實例的索引鍵和值屬性名稱時，可接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項的 .NET 5.0 中的重大變更。
ms.date: 10/18/2020
ms.openlocfilehash: 5d75cb7feea32cc4b942e5261c5b609e00a5082c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760758"
---
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a>序列化和還原序列化機碼值組時，會接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項

<xref:System.Text.Json.JsonSerializer> 現在會在 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 序列化 <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602.Key> 實例的和屬性名稱時，接受和選項 <xref:System.Collections.Generic.KeyValuePair%602.Value> <xref:System.Collections.Generic.KeyValuePair%602> 。 此外， <xref:System.Text.Json.JsonSerializer> 將實例還原序列化時，會接受 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 和 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> 選項 <xref:System.Collections.Generic.KeyValuePair%602> 。

## <a name="change-description"></a>變更描述

### <a name="serialization"></a>序列化

在 .NET Core 3.x 版和 [ NuGet 套件上System.Text.Js](https://www.nuget.org/packages/System.Text.Json)的 4.6.0-4.7.2 版本中，實例的屬性 <xref:System.Collections.Generic.KeyValuePair%602> 一律會正確序列化為 "Key" 和 "Value"，不論任何 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 和 <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> 選項為何。 下列程式碼範例會示範在 <xref:System.Collections.Generic.KeyValuePair%602.Key> 序列化之後，和屬性如何以 <xref:System.Collections.Generic.KeyValuePair%602.Value> camel 大小寫為大寫，即使指定的屬性命名原則表示如此。 *not*

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

從 .NET 5.0 開始， <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 當序列化 <xref:System.Text.Json.JsonSerializerOptions.Encoder> 實例時，會接受和選項 <xref:System.Collections.Generic.KeyValuePair%602> 。 下列程式碼範例示範如何 <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> 根據指定的屬性命名原則，在序列化之後，和屬性是以 camel 法為大寫。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a>還原序列化

在 .NET Core 3.x 版中，以及在 [ NuGet 套件](https://www.nuget.org/packages/System.Text.Json)的 4.7. x 版System.Text.Js中， <xref:System.Text.Json.JsonException> 如果 JSON 屬性名稱不是精確的，則會擲回 `Key` ， `Value` 例如，如果不是以大寫字母開頭，就會擲回。 即使指定的屬性命名原則明確允許，也會擲回例外狀況。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

從 .NET 5.0 開始， <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 使用還原 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> 序列化時，會接受和選項 <xref:System.Text.Json.JsonSerializer> 。 例如，下列程式碼片段會顯示成功的小寫 <xref:System.Collections.Generic.KeyValuePair%602.Key> 和屬性名稱還原序列化， <xref:System.Collections.Generic.KeyValuePair%602.Value> 因為指定的屬性命名原則允許它。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

為了容納使用先前版本序列化的承載，在還原序列化時，"Key" 和 "Value" 會符合特殊大小寫。 即使 <xref:System.Collections.Generic.KeyValuePair%602.Key> 和 <xref:System.Collections.Generic.KeyValuePair%602.Value> 屬性名稱不會根據下列程式碼範例中的 in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 選項，也會成功還原序列化。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="reason-for-change"></a>變更的原因

大量的客戶意見反應指出 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 應接受。 為求完整性， <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> 也會採用和選項，如此一來，就 <xref:System.Collections.Generic.KeyValuePair%602> 會將實例視為與任何其他單純的 CLR 物件相同， (POCO) 。

## <a name="recommended-action"></a>建議的動作

如果這項變更干擾您，您可以使用 [自訂轉換器](../../../../standard/serialization/system-text-json-converters-how-to.md) 來執行所需的語法。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
