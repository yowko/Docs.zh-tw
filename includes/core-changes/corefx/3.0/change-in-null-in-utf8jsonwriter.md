---
ms.openlocfilehash: 13da0ef6155d65fbc894c5747cc36bb3483ba518
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721159"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="98ba4-101">`(string)null`在 Utf8JsonWriter 中變更的語義</span><span class="sxs-lookup"><span data-stu-id="98ba4-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="98ba4-102">在 .NET Core 3.0 Preview 7 中，會將 null 字串視為中的空字串 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="98ba4-103">從 .NET Core 3.0 Preview 8 開始，當 null 字串當做屬性名稱使用時，會擲回例外狀況，並在做為值使用時發出 JSON null token。</span><span class="sxs-lookup"><span data-stu-id="98ba4-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="98ba4-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="98ba4-104">Change description</span></span>

<span data-ttu-id="98ba4-105">在 .NET Core 3.0 Preview 7 中，在 `null` `""` 寫入屬性名稱和寫入值時，會將字串視為兩者。</span><span class="sxs-lookup"><span data-stu-id="98ba4-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="98ba4-106">從 .NET Core 3.0 Preview 8 開始， `null` 屬性名稱會擲回 `ArgumentNullException` ，並將 `null` 值視為或的呼叫 <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="98ba4-107">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="98ba4-107">Consider the following code:</span></span>

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

<span data-ttu-id="98ba4-108">如果使用 .NET Core 3.0 Preview 7 執行，寫入器會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="98ba4-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="98ba4-109">從 .NET Core 3.0 Preview 8 開始，對的呼叫會擲回 `writer.WriteString(propertyName1, propertyValue1)` <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="98ba4-110">如果 `propertyName1 = null` 取代為 `propertyName1 = string.Empty` ，則輸出現在會是：</span><span class="sxs-lookup"><span data-stu-id="98ba4-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="98ba4-111">進行這種變更的方式，是為了與呼叫者對值的期望更一致 `null` 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98ba4-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="98ba4-112">Version introduced</span></span>

<span data-ttu-id="98ba4-113">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="98ba4-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98ba4-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="98ba4-114">Recommended action</span></span>

<span data-ttu-id="98ba4-115">使用類別寫入屬性名稱和值時 <xref:System.Text.Json.Utf8JsonWriter> ：</span><span class="sxs-lookup"><span data-stu-id="98ba4-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="98ba4-116">請確定 `null` 使用非字串作為屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="98ba4-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="98ba4-117">如果需要先前的行為，請使用 null 聯合調用;例如， `writer.WriteString(propertyName1 ?? "", propertyValue1)` 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="98ba4-118">如果不想 `null` 要為 `null` 字串值撰寫常值，請使用 null 聯合調用，例如 `writer.WriteString(propertyName2, propertyValue2 ?? "")` 。</span><span class="sxs-lookup"><span data-stu-id="98ba4-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="98ba4-119">類別</span><span class="sxs-lookup"><span data-stu-id="98ba4-119">Category</span></span>

<span data-ttu-id="98ba4-120">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="98ba4-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98ba4-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="98ba4-121">Affected APIs</span></span>

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
