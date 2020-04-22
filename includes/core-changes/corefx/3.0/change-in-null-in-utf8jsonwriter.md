---
ms.openlocfilehash: c9547cdc2f127cf13a3610118a26736930fcd8bd
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021674"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="c4a4d-101">Utf8JonWriter 中語義`(string)null`的變化</span><span class="sxs-lookup"><span data-stu-id="c4a4d-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="c4a4d-102">在 .NET Core 3.0 預覽 7 中<xref:System.Text.Json.Utf8JsonWriter>,空字串被視為 中的空字串。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="c4a4d-103">從 .NET Core 3.0 預覽 8 開始,空字串在用作屬性名稱時引發異常,當用作值時,它將發出 JSON null 令牌。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4a4d-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="c4a4d-104">Change description</span></span>

<span data-ttu-id="c4a4d-105">在 .NET Core`null`3.0`""`預覽 7 中,字串在編寫屬性名稱和編寫值時都被視為兩者。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="c4a4d-106">從 .NET`null`Core 3.0`ArgumentNullException`預覽`null`8 開始 ,<xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType>屬性<xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>名稱 將引發 , 並將值 視為 對 或的調用。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c4a4d-107">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c4a4d-107">Consider the following code:</span></span>

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

<span data-ttu-id="c4a4d-108">如果使用 .NET Core 3.0 預覽 7 執行,則編寫器將產生以下輸出:</span><span class="sxs-lookup"><span data-stu-id="c4a4d-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="c4a4d-109">從 .NET 核心 3.0`writer.WriteString(propertyName1, propertyValue1)`<xref:System.ArgumentNullException>預覽 8 開始 ,要引發 的呼叫將引發 。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="c4a4d-110">如果`propertyName1 = null`取代`propertyName1 = string.Empty`為 ,輸出現在將為:</span><span class="sxs-lookup"><span data-stu-id="c4a4d-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="c4a4d-111">進行此更改是為了更好地與調用方對值的期望`null`保持一致。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4a4d-112">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="c4a4d-112">Version introduced</span></span>

<span data-ttu-id="c4a4d-113">3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="c4a4d-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4a4d-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c4a4d-114">Recommended action</span></span>

<span data-ttu-id="c4a4d-115">使用<xref:System.Text.Json.Utf8JsonWriter>類別寫屬性名稱與值時:</span><span class="sxs-lookup"><span data-stu-id="c4a4d-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="c4a4d-116">確保非`null`字串用作屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="c4a4d-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="c4a4d-117">如果需要上一個行為,請使用空合併調用;如果需要上述行為,則使用空合併調用;例如, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="c4a4d-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="c4a4d-118">如果不需要為`null``null`字串值編寫文本,請使用空合併調用;例如, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="c4a4d-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="c4a4d-119">類別</span><span class="sxs-lookup"><span data-stu-id="c4a4d-119">Category</span></span>

<span data-ttu-id="c4a4d-120">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="c4a4d-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4a4d-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c4a4d-121">Affected APIs</span></span>

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

### Affected APIs

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
