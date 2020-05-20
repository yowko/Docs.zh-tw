---
title: ''
description: 本文說明如何使用 System.Text.Json 命名空間，在 .net 中從 JSON 序列化和還原序列化。 其中包含範例程式碼。
ms.date: ''
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords: []
ms.openlocfilehash: f1a5da448b08f9b4f1cf3fa6cba67fb376b00a6f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702247"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="1cf6e-103">如何在 .NET 中序列化和還原序列化（封送處理和 unmarshal） JSON</span><span class="sxs-lookup"><span data-stu-id="1cf6e-103">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="1cf6e-104">本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）中進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-104">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="1cf6e-105">如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-105">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="1cf6e-106">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-106">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="1cf6e-107">大部分的序列化範例程式碼會將設 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為，以「整齊地列印」 `true` JSON （使用縮排和空白字元來進行人類可讀性）。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-107">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="1cf6e-108">針對生產環境使用，您通常會接受此設定的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-108">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="1cf6e-109">程式碼範例會參考下列類別和它的變體：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-109">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="1cf6e-110">命名空間</span><span class="sxs-lookup"><span data-stu-id="1cf6e-110">Namespaces</span></span>

<span data-ttu-id="1cf6e-111"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-111">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="1cf6e-112"><xref:System.Text.Json.Serialization>命名空間包含用於高階案例的屬性和 api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-112">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="1cf6e-113">本文中顯示的程式碼範例需要 `using` 其中一個或兩個命名空間的指示詞：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-113">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="1cf6e-114"><xref:System.Runtime.Serialization>目前不支援命名空間中的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-114">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="1cf6e-115">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="1cf6e-115">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="1cf6e-116">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-116">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1cf6e-117">下列範例會將 JSON 建立為字串：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-117">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-118">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-118">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-119">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-119">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-120">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-120">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="1cf6e-121">的多載 `Serialize()` 會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-121">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="1cf6e-122">序列化範例</span><span class="sxs-lookup"><span data-stu-id="1cf6e-122">Serialization example</span></span>

<span data-ttu-id="1cf6e-123">以下是包含集合和嵌套類別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-123">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="1cf6e-124">序列化上述型別之實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-124">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="1cf6e-125">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-125">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="1cf6e-126">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-126">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="1cf6e-127">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="1cf6e-127">Serialize to UTF-8</span></span>

<span data-ttu-id="1cf6e-128">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-128">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-129"><xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用接受的多載 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-129">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="1cf6e-130">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約5-10%。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-130">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="1cf6e-131">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-131">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="1cf6e-132">序列化行為</span><span class="sxs-lookup"><span data-stu-id="1cf6e-132">Serialization behavior</span></span>

* <span data-ttu-id="1cf6e-133">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-133">By default, all public properties are serialized.</span></span> <span data-ttu-id="1cf6e-134">您可以[指定要排除的屬性](#exclude-properties-from-serialization)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-134">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="1cf6e-135">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-135">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="1cf6e-136">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-136">By default, JSON is minified.</span></span> <span data-ttu-id="1cf6e-137">您可以[整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-137">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="1cf6e-138">根據預設，JSON 名稱的大小寫會符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-138">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="1cf6e-139">您可以[自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-139">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="1cf6e-140">偵測到迴圈參考，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-140">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="1cf6e-141">目前已排除欄位。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-141">Currently, fields are excluded.</span></span>

<span data-ttu-id="1cf6e-142">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-142">Supported types include:</span></span>

* <span data-ttu-id="1cf6e-143">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-143">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="1cf6e-144">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-144">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="1cf6e-145">一維和不規則陣列（ `ArrayName[][]` ）。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-145">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="1cf6e-146">`Dictionary<string,TValue>`其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-146">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="1cf6e-147">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-147">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="1cf6e-148">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)來處理其他類型，或提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="1cf6e-149">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="1cf6e-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="1cf6e-150">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1cf6e-151">下列範例會從字串讀取 JSON，並建立 `WeatherForecast` 先前針對[序列化範例](#serialization-example)所顯示的類別實例：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-151">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-152">若要使用同步程式碼從檔案還原序列化，請將檔案讀取到字串中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-153">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="1cf6e-154">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="1cf6e-154">Deserialize from UTF-8</span></span>

<span data-ttu-id="1cf6e-155">若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `Utf8JsonReader` 或的多載， `ReadOnlySpan<byte>` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-155">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="1cf6e-156">這些範例假設 JSON 位於名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-156">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="1cf6e-157">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="1cf6e-157">Deserialization behavior</span></span>

* <span data-ttu-id="1cf6e-158">根據預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-158">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="1cf6e-159">您可以[指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-159">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="1cf6e-160">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-160">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="1cf6e-161">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-161">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="1cf6e-162">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-162">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="1cf6e-163">根據預設，列舉會當做數位來支援。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="1cf6e-164">您可以將[列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="1cf6e-165">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-165">Fields aren't supported.</span></span>
* <span data-ttu-id="1cf6e-166">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="1cf6e-167">您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="1cf6e-168">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="1cf6e-169">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="1cf6e-170">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="1cf6e-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="1cf6e-171">若要以整齊的格式列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="1cf6e-172">以下是要序列化的範例型別，以及相當列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="1cf6e-173">自訂 JSON 名稱和值</span><span class="sxs-lookup"><span data-stu-id="1cf6e-173">Customize JSON names and values</span></span>

<span data-ttu-id="1cf6e-174">根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="1cf6e-175">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="1cf6e-176">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-176">This section explains how to:</span></span>

* [<span data-ttu-id="1cf6e-177">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1cf6e-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="1cf6e-178">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="1cf6e-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="1cf6e-179">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="1cf6e-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="1cf6e-180">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="1cf6e-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="1cf6e-181">將列舉轉換為字串和大小寫</span><span class="sxs-lookup"><span data-stu-id="1cf6e-181">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="1cf6e-182">針對需要對 JSON 屬性名稱和值進行特殊處理的其他案例，您可以[執行自訂轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="1cf6e-183">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1cf6e-183">Customize individual property names</span></span>

<span data-ttu-id="1cf6e-184">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="1cf6e-185">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1cf6e-186">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="1cf6e-187">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="1cf6e-188">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="1cf6e-189">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="1cf6e-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="1cf6e-190">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="1cf6e-191">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1cf6e-192">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="1cf6e-193">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="1cf6e-194">會由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="1cf6e-195">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 案例的原因。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="1cf6e-196">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="1cf6e-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="1cf6e-197">若要使用自訂 JSON 屬性命名原則，請建立衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="1cf6e-198">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-199">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1cf6e-200">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="1cf6e-201">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="1cf6e-202">會由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="1cf6e-203">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="1cf6e-204">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="1cf6e-204">Camel case dictionary keys</span></span>

<span data-ttu-id="1cf6e-205">如果要序列化之物件的屬性屬於型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="1cf6e-206">若要這麼做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-207">使用名為的字典序列化 `TemperatureRanges` 具有索引鍵/值組 `"ColdMinTemp", 20` 且 `"HotMinTemp", 40` 會產生 JSON 輸出的物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="1cf6e-208">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="1cf6e-209">如果您將字典還原序列化，則即使您針對指定了，索引鍵仍會符合 JSON 檔案 `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="1cf6e-210">做為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="1cf6e-210">Enums as strings</span></span>

<span data-ttu-id="1cf6e-211">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="1cf6e-212">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="1cf6e-213">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="1cf6e-214">如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="1cf6e-215">下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-216">產生的 JSON 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="1cf6e-217">列舉字串名稱也可以還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="1cf6e-218">排除序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-218">Exclude properties from serialization</span></span>

<span data-ttu-id="1cf6e-219">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="1cf6e-220">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="1cf6e-221">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="1cf6e-222">個別屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="1cf6e-223">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="1cf6e-224">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="1cf6e-225">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-225">Exclude individual properties</span></span>

<span data-ttu-id="1cf6e-226">若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="1cf6e-227">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="1cf6e-228">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-228">Exclude all read-only properties</span></span>

<span data-ttu-id="1cf6e-229">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="1cf6e-230">若要排除所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-231">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="1cf6e-232">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-232">This option applies only to serialization.</span></span> <span data-ttu-id="1cf6e-233">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="1cf6e-234">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-234">Exclude all null value properties</span></span>

<span data-ttu-id="1cf6e-235">若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-236">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="1cf6e-237">屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-237">Property</span></span> |<span data-ttu-id="1cf6e-238">值</span><span class="sxs-lookup"><span data-stu-id="1cf6e-238">Value</span></span>  |
|---
<span data-ttu-id="1cf6e-239">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-239">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-240">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-240">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-241">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-241">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-242">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-242">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-243">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-243">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="1cf6e-244">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-244">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-245">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-245">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-246">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-246">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-247">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-247">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-248">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-248">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="1cf6e-249">-----|---標題：描述： ' 本文說明如何使用 System.Text.Json 命名空間，在 .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-249">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-250">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-250">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-251">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-251">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-252">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-252">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-253">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-253">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="1cf6e-254">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-254">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-255">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-255">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-256">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-256">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-257">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-257">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-258">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-258">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="1cf6e-259">-----| |日期 |8/1/2019 12:00:00 AM-07:00 | |TemperatureCelsius |25 | |摘要 |null |</span><span class="sxs-lookup"><span data-stu-id="1cf6e-259">-----| | Date    | 8/1/2019 12:00:00 AM -07:00| | TemperatureCelsius| 25 | | Summary| null|</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="1cf6e-260">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-260">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="1cf6e-261">如需其對還原序列化之影響的詳細資訊，請參閱[在還原序列化時忽略 null](#ignore-null-when-deserializing)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-261">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="1cf6e-262">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="1cf6e-262">Customize character encoding</span></span>

<span data-ttu-id="1cf6e-263">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-263">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="1cf6e-264">也就是說，它會取代它們， `\uxxxx` 其中 `xxxx` 是字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-264">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="1cf6e-265">例如，如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 會序列化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-265">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="1cf6e-266">序列化語言字元集</span><span class="sxs-lookup"><span data-stu-id="1cf6e-266">Serialize language character sets</span></span>

<span data-ttu-id="1cf6e-267">若要序列化一或多個語言的字元集而不進行轉義，請在建立實例時指定[Unicode 範圍](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-267">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="1cf6e-268">這段程式碼不會將斯拉夫文或希臘文字元取消換用。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-268">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="1cf6e-269">如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 會序列化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-269">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="1cf6e-270">若要序列化所有語言集而不進行任何轉義，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-270">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="1cf6e-271">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="1cf6e-271">Serialize specific characters</span></span>

<span data-ttu-id="1cf6e-272">另一個替代方式是指定您想要允許通過的個別字元，而不會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-272">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="1cf6e-273">下列範例只會序列化жарко的前兩個字元：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-273">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="1cf6e-274">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-274">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="1cf6e-275">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="1cf6e-275">Serialize all characters</span></span>

<span data-ttu-id="1cf6e-276">若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-276">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="1cf6e-277">相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼器更寬鬆，可讓字元通過非預設的傳遞：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-277">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="1cf6e-278">它不會將 HTML 敏感的字元（例如 `<` 、 `>` 、和）換用 `&` `'` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-278">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="1cf6e-279">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深層防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在*字元集*上。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-279">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="1cf6e-280">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-280">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="1cf6e-281">例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-281">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="1cf6e-282">永遠不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-282">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="1cf6e-283">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-283">Serialize properties of derived classes</span></span>

<span data-ttu-id="1cf6e-284">不支援多型類型階層的序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-284">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="1cf6e-285">例如，如果屬性定義為介面或抽象類別，則即使執行時間類型有其他屬性，還是會序列化在介面或抽象類別上定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-285">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="1cf6e-286">這一節將說明此行為的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-286">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="1cf6e-287">例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-287">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="1cf6e-288">而且在編譯時期，假設方法的型別引數 `Serialize` 是 `WeatherForecast` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-288">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="1cf6e-289">在此案例中， `WindSpeed` 即使 `weatherForecast` 物件實際上是物件，也不會序列化屬性 `WeatherForecastDerived` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-289">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="1cf6e-290">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-290">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="1cf6e-291">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-291">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="1cf6e-292">若要在上述範例中序列化衍生型別的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-292">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="1cf6e-293">呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-293">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="1cf6e-294">宣告要序列化為的物件 `object` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-294">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="1cf6e-295">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-295">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="1cf6e-296">這些方法只會針對要序列化的根物件提供多型序列化，而不是針對該根物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-296">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="1cf6e-297">如果您將較低層級的物件定義為類型，則可以取得其多型序列化 `object` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-297">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="1cf6e-298">例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，可定義為類型 `WeatherForecast` 或 `object` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-298">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="1cf6e-299">如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-299">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="1cf6e-300">序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-300">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="1cf6e-301">序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-301">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="1cf6e-302">若要序列化 `WeatherForecastWithPreviousAsObject` ，則不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能屬於衍生類型的物件。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-302">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="1cf6e-303">下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-303">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="1cf6e-304">上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-304">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="1cf6e-305">將屬性定義為與 `object` 介面搭配使用的相同方法。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-305">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="1cf6e-306">假設您有下列介面和實作為，而且您想要使用包含實作為實例的屬性來序列化類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-306">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="1cf6e-307">當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-307">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="1cf6e-308">下列範例顯示上述程式碼所產生的 JSON：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-308">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="1cf6e-309">如需多型**序列化**的詳細資訊，以及還原序列化**的相關資訊**，請參閱[如何將從遷移 Newtonsoft.Json 至 System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-309">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="1cf6e-310">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="1cf6e-310">Allow comments and trailing commas</span></span>

<span data-ttu-id="1cf6e-311">根據預設，JSON 中不允許批註和尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-311">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="1cf6e-312">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-312">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="1cf6e-313">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-313">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="1cf6e-314">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-314">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-315">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-315">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="1cf6e-316">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="1cf6e-316">Case-insensitive property matching</span></span>

<span data-ttu-id="1cf6e-317">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-317">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="1cf6e-318">若要變更該行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-318">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-319">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-319">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="1cf6e-320">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-320">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="1cf6e-321">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="1cf6e-321">Handle overflow JSON</span></span>

<span data-ttu-id="1cf6e-322">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-322">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="1cf6e-323">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-323">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="1cf6e-324">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-324">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="1cf6e-325">如果您將顯示的 JSON 還原序列化為所顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-325">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="1cf6e-326">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至類型的屬性 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-326">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="1cf6e-327">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-327">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="1cf6e-328">屬性</span><span class="sxs-lookup"><span data-stu-id="1cf6e-328">Property</span></span> |<span data-ttu-id="1cf6e-329">值</span><span class="sxs-lookup"><span data-stu-id="1cf6e-329">Value</span></span>  |<span data-ttu-id="1cf6e-330">注意</span><span class="sxs-lookup"><span data-stu-id="1cf6e-330">Notes</span></span>  |
|---
<span data-ttu-id="1cf6e-331">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-331">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-332">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-332">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-333">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-333">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-334">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-334">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-335">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-335">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="1cf6e-336">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-336">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-337">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-337">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-338">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-338">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-339">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-339">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-340">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-340">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="1cf6e-341">-----|---標題：描述： ' 本文說明如何使用 System.Text.Json 命名空間，在 .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-341">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-342">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-342">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-343">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-343">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-344">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-344">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-345">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-345">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="1cf6e-346">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-346">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-347">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-347">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-348">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-348">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-349">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-349">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-350">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-350">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="1cf6e-351">-----|---標題：描述： ' 本文說明如何使用 System.Text.Json 命名空間，在 .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-351">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-352">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-352">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-353">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-353">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-354">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-354">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-355">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-355">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="1cf6e-356">title：描述： ' 本文說明如何使用命名空間，在 System.Text.Json .net 中從 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-356">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="1cf6e-357">其中包含範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-357">It includes sample code.'</span></span>
<span data-ttu-id="1cf6e-358">ms. date： no-loc：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-358">ms.date: no-loc:</span></span>
- <span data-ttu-id="1cf6e-359">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="1cf6e-359">'System.Text.Json'</span></span>
- <span data-ttu-id="1cf6e-360">' Newtonsoft.Json ' helpviewer_keywords：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-360">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="1cf6e-361">-----| |日期 |8/1/2019 12:00:00 AM-07:00 | ||TemperatureCelsius |0 |區分大小寫不相符（ `temperatureCelsius` 在 JSON 中），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-361">-----| | Date    | 8/1/2019 12:00:00 AM -07:00|| | TemperatureCelsius| 0 | Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> <span data-ttu-id="1cf6e-362">| |摘要 |熱門 | ||ExtensionData |temperatureCelsius： 25 |因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。 |||DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="1cf6e-362">| | Summary | Hot || | ExtensionData | temperatureCelsius: 25 |Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.| || DatesAvailable:</span></span><br>  <span data-ttu-id="1cf6e-363">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="1cf6e-363">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="1cf6e-364">8/2/2019 12:00:00 AM-07:00 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。 || |SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="1cf6e-364">8/2/2019 12:00:00 AM -07:00 |Extra property from the JSON becomes a key-value pair, with an array as the value object.| | |SummaryWords:</span></span><br><span data-ttu-id="1cf6e-365">非經常性存取</span><span class="sxs-lookup"><span data-stu-id="1cf6e-365">Cool</span></span><br><span data-ttu-id="1cf6e-366">風大</span><span class="sxs-lookup"><span data-stu-id="1cf6e-366">Windy</span></span><br><span data-ttu-id="1cf6e-367">潮濕 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。 |</span><span class="sxs-lookup"><span data-stu-id="1cf6e-367">Humid |Extra property from the JSON becomes a key-value pair, with an array as the value object.|</span></span>

<span data-ttu-id="1cf6e-368">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-368">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="1cf6e-369">請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-369">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="1cf6e-370">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-370">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="1cf6e-371">還原序列化時忽略 null</span><span class="sxs-lookup"><span data-stu-id="1cf6e-371">Ignore null when deserializing</span></span>

<span data-ttu-id="1cf6e-372">根據預設，如果 JSON 中的屬性是 null，則目標物件中的對應屬性會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-372">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="1cf6e-373">在某些情況下，目標屬性可能會有預設值，而且您不想要 null 值來覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-373">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="1cf6e-374">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-374">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="1cf6e-375">假設下列 JSON 已還原序列化：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-375">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="1cf6e-376">還原序列化之後， `Summary` 物件的屬性 `WeatherForecastWithDefault` 為 null。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-376">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="1cf6e-377">若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-377">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-378">使用此選項時， `Summary` 物件的屬性 `WeatherForecastWithDefault` 是還原序列化後的預設值「沒有摘要」。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-378">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="1cf6e-379">JSON 中的 Null 值只有在有效時才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-379">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="1cf6e-380">不可為 null 的實數值型別的 Null 值會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-380">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="1cf6e-381">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="1cf6e-381">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="1cf6e-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>是一種高效能、低配置、順向讀取器，適用于 UTF-8 編碼的 JSON 文字，從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="1cf6e-383">`Utf8JsonReader`是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-383">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="1cf6e-384"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會 `Utf8JsonReader` 在幕後使用。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-384">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="1cf6e-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>是從常見的 .NET 類型（例如、和）撰寫 UTF-8 編碼 JSON 文字的高效能 `String` 方式 `Int32` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="1cf6e-386">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-386">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="1cf6e-387"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會 `Utf8JsonWriter` 在幕後使用。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-387">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="1cf6e-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>提供使用來建立唯讀檔案物件模型（DOM）的功能 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="1cf6e-389">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-389">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="1cf6e-390">組成裝載的 JSON 元素可以透過類型來存取 <xref:System.Text.Json.JsonElement> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-390">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="1cf6e-391">`JsonElement`型別提供陣列和物件列舉值，以及用來將 JSON 文字轉換成常見 .net 類型的 api。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-391">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="1cf6e-392">`JsonDocument`公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-392">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="1cf6e-393">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-393">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="1cf6e-394">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="1cf6e-394">Use JsonDocument for access to data</span></span>

<span data-ttu-id="1cf6e-395">下列範例顯示如何使用 <xref:System.Text.Json.JsonDocument> 類別，以隨機存取 JSON 字串中的資料：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-395">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="1cf6e-396">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-396">The preceding code:</span></span>

* <span data-ttu-id="1cf6e-397">假設要分析的 JSON 是在名為的字串中 `jsonString` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-397">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="1cf6e-398">計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-398">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="1cf6e-399">為沒有成績的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-399">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="1cf6e-400">藉由遞增 `count` 變數與每個反復專案來計算學生數目。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-400">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="1cf6e-401">另一種方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-401">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="1cf6e-402">以下是此程式碼所處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-402">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="1cf6e-403">使用 JsonDocument 寫入 JSON</span><span class="sxs-lookup"><span data-stu-id="1cf6e-403">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="1cf6e-404">下列範例顯示如何從寫入 JSON <xref:System.Text.Json.JsonDocument> ：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-404">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="1cf6e-405">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-405">The preceding code:</span></span>

* <span data-ttu-id="1cf6e-406">讀取 JSON 檔案、將資料載入 `JsonDocument` ，並將格式化（已列印）的 JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-406">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="1cf6e-407">使用 <xref:System.Text.Json.JsonDocumentOptions> 來指定允許輸入 JSON 中的批註，但忽略。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-407">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="1cf6e-408">完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-408">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="1cf6e-409">另一個替代方式是讓寫入器在處置時 autoflush。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-409">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="1cf6e-410">以下是範例程式碼所要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-410">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="1cf6e-411">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-411">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="1cf6e-412">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="1cf6e-412">Use Utf8JsonWriter</span></span>

<span data-ttu-id="1cf6e-413">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-413">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="1cf6e-414">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="1cf6e-414">Use Utf8JsonReader</span></span>

<span data-ttu-id="1cf6e-415">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-415">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="1cf6e-416">上述程式碼假設 `jsonUtf8` 變數是包含有效 JSON 的位元組陣列，並以 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-416">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="1cf6e-417">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="1cf6e-417">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="1cf6e-418">下列範例示範如何以同步方式讀取檔案，並搜尋值：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-418">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="1cf6e-419">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-419">The preceding code:</span></span>

* <span data-ttu-id="1cf6e-420">假設 JSON 包含物件的陣列，而且每個物件都可以包含 string 類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-420">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="1cf6e-421">計算以 "大學" 結尾的物件和「名稱」屬性值。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-421">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="1cf6e-422">假設檔案是以 UTF-16 編碼，並將其轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-422">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="1cf6e-423">您可以 `ReadOnlySpan<byte>` 使用下列程式碼，直接將編碼為 utf-8 的檔案讀取至：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-423">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="1cf6e-424">如果檔案包含 UTF-8 位元組順序標記（BOM），請先將它移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器需要文字。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-424">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="1cf6e-425">否則，BOM 會被視為不正確 JSON，而讀取器會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-425">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="1cf6e-426">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-426">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="1cf6e-427">產生的摘要訊息為「2個以上的名稱，其結尾為 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-427">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="1cf6e-428">使用 Utf8JsonReader 從串流讀取</span><span class="sxs-lookup"><span data-stu-id="1cf6e-428">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="1cf6e-429">當讀取大型檔案（例如，大小為 gb 或以上）時，您可能會想要避免必須一次將整個檔案載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-429">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="1cf6e-430">在此案例中，您可以使用 <xref:System.IO.FileStream> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-430">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="1cf6e-431">使用 `Utf8JsonReader` 從資料流程讀取時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="1cf6e-431">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="1cf6e-432">包含部分 JSON 承載的緩衝區，必須至少與其中最大的 JSON 權杖一樣大，才能讓讀取器繼續進行。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-432">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="1cf6e-433">緩衝區的大小至少必須與 JSON 內最大的空白字元序列相同。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-433">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="1cf6e-434">讀取器不會追蹤其已讀取的資料，直到它完全讀取 JSON 裝載中的下一個 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-434">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="1cf6e-435">因此，當緩衝區中剩餘的位元組超過時，您必須將它們再次傳遞給讀取器。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-435">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="1cf6e-436">您可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 來判斷剩餘的位元組數。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-436">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="1cf6e-437">下列程式碼說明如何從資料流程讀取。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-437">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="1cf6e-438">此範例會顯示 <xref:System.IO.MemoryStream> 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-438">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="1cf6e-439">類似的程式碼可與搭配使用 <xref:System.IO.FileStream> ，除非在 `FileStream` 開始時包含 utf-8 BOM。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-439">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="1cf6e-440">在這種情況下，您必須先從緩衝區中去除這三個位元組，再將剩餘的位元組傳遞給 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-440">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="1cf6e-441">否則，讀取器會擲回例外狀況，因為 BOM 不會被視為 JSON 的有效部分。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-441">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="1cf6e-442">範例程式碼會以 4 KB 的緩衝區開頭，並在每次發現大小不足以符合完整的 JSON 權杖時，將緩衝區大小加倍，這是讀取器在 JSON 承載上做出向前進展的必要項。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-442">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="1cf6e-443">只有當您設定非常小的初始緩衝區大小（例如10個位元組）時，程式碼片段中提供的 JSON 範例才會觸發緩衝區大小的增加。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-443">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="1cf6e-444">如果您將初始緩衝區大小設定為10，語句就會 `Console.WriteLine` 說明緩衝區大小增加的原因和效果。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-444">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="1cf6e-445">在 4 KB 的初始緩衝區大小中，會顯示整個範例 JSON `Console.WriteLine` ，而且永遠不需要增加緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-445">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="1cf6e-446">上述範例會將緩衝區的大小限制設定為無法成長。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-446">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="1cf6e-447">如果權杖大小太大，程式碼可能會失敗併發生 <xref:System.OutOfMemoryException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-447">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="1cf6e-448">如果 JSON 包含大約 1 GB 或更大大小的權杖，就會發生這種情況，因為 1 GB 大小加倍會導致大小太大而無法放入 `int32` 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="1cf6e-448">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1cf6e-449">其他資源</span><span class="sxs-lookup"><span data-stu-id="1cf6e-449">Additional resources</span></span>

* <span data-ttu-id="1cf6e-450">[System.Text.Json簡要](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1cf6e-450">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="1cf6e-451">如何撰寫自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="1cf6e-451">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="1cf6e-452">[如何從進行遷移Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="1cf6e-452">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="1cf6e-453">[中的 DateTime 和 DateTimeOffset 支援System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="1cf6e-453">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="1cf6e-454">[System.Text.JsonAPI 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="1cf6e-454">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
