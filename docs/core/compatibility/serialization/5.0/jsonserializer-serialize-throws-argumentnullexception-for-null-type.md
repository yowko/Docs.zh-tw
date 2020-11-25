---
title: 中斷性變更：當類型參數為 null 時，序列化擲回例外狀況
description: 瞭解 .NET 5.0 中的重大變更，其中具有類型參數的 JsonSerialize 序列化方法現在會在傳遞該參數的 null 時擲回例外狀況。
ms.date: 10/18/2020
ms.openlocfilehash: af2885394418072ad7efec5855490b5b80152fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760759"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType><xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 具有類型之參數的、和多載， <xref:System.Type> 現在會在 <xref:System.ArgumentNullException> 每次 `null` 傳遞該參數時擲回。

## <a name="change-description"></a>變更描述

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

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="reason-for-change"></a>變更的原因

傳入 `null` `Type inputType` 參數是無法接受的，而且一律會擲回 <xref:System.ArgumentNullException> 。

## <a name="recommended-action"></a>建議的動作

請確定您未傳遞 `null` `Type inputType` 這些方法的參數。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
