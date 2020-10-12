---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955329"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>具有參數的、和多載， <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> <xref:System.Type> 現在會在 <xref:System.ArgumentNullException> 每次 `null` 傳遞參數時擲回 <xref:System.Type> 。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.1 中， <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 具有參數的、和多載 <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 會在 <xref:System.Type> <xref:System.ArgumentNullException> 傳遞給參數時擲回， `null` `Type inputType` 但是如果 `Object value` 參數也不是 `null` ，則不會擲回。 從 .NET 5.0 開始， *always* <xref:System.ArgumentNullException> 當 `null` 針對參數傳遞時，這些方法一律會擲回 <xref:System.Type> 。

.NET Core 3.1 中的行為：

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

.NET 5.0 和更新版本中的行為：

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="reason-for-change"></a>變更的原因

傳入 `null` `Type inputType` 參數是無法接受的，而且一律會擲回 <xref:System.ArgumentNullException> 。

#### <a name="recommended-action"></a>建議的動作

請確定您未傳遞 `null` `Type inputType` 這些方法的參數。

#### <a name="category"></a>類別

序列化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

-->
