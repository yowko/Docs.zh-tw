---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: 本文說明如何使用 System.Text.Json 命名空間，在 .net 中從 JSON 序列化和還原序列化。 其中包含範例程式碼。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ad748508b73c3e141ae345efa0abb66c009740cd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378729"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="77eec-104">如何在 .NET 中序列化和還原序列化（封送處理和 unmarshal） JSON</span><span class="sxs-lookup"><span data-stu-id="77eec-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="77eec-105">本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）中進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="77eec-106">如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="77eec-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="77eec-107">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="77eec-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="77eec-108">大部分的序列化範例程式碼會將設 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為，以「整齊地列印」 `true` JSON （使用縮排和空白字元來進行人類可讀性）。</span><span class="sxs-lookup"><span data-stu-id="77eec-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="77eec-109">針對生產環境使用，您通常會接受此設定的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="77eec-110">程式碼範例會參考下列類別和它的變體：</span><span class="sxs-lookup"><span data-stu-id="77eec-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="77eec-111">命名空間</span><span class="sxs-lookup"><span data-stu-id="77eec-111">Namespaces</span></span>

<span data-ttu-id="77eec-112"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="77eec-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="77eec-113"><xref:System.Text.Json.Serialization>命名空間包含用於高階案例的屬性和 api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="77eec-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="77eec-114">本文中顯示的程式碼範例需要 `using` 其中一個或兩個命名空間的指示詞：</span><span class="sxs-lookup"><span data-stu-id="77eec-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="77eec-115"><xref:System.Runtime.Serialization>目前不支援命名空間中的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="77eec-116">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="77eec-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="77eec-117">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="77eec-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="77eec-118">下列範例會將 JSON 建立為字串：</span><span class="sxs-lookup"><span data-stu-id="77eec-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-119">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="77eec-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-120">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="77eec-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-121">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="77eec-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="77eec-122">的多載 `Serialize()` 會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="77eec-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="77eec-123">序列化範例</span><span class="sxs-lookup"><span data-stu-id="77eec-123">Serialization example</span></span>

<span data-ttu-id="77eec-124">以下是包含集合和嵌套類別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="77eec-125">序列化上述型別之實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77eec-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="77eec-126">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="77eec-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="77eec-127">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="77eec-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="77eec-128">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="77eec-128">Serialize to UTF-8</span></span>

<span data-ttu-id="77eec-129">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="77eec-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-130"><xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用接受的多載 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="77eec-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="77eec-131">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約5-10%。</span><span class="sxs-lookup"><span data-stu-id="77eec-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="77eec-132">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="77eec-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="77eec-133">序列化行為</span><span class="sxs-lookup"><span data-stu-id="77eec-133">Serialization behavior</span></span>

* <span data-ttu-id="77eec-134">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="77eec-135">您可以[指定要排除的屬性](#exclude-properties-from-serialization)。</span><span class="sxs-lookup"><span data-stu-id="77eec-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="77eec-136">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="77eec-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="77eec-137">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="77eec-137">By default, JSON is minified.</span></span> <span data-ttu-id="77eec-138">您可以[整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="77eec-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="77eec-139">根據預設，JSON 名稱的大小寫會符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="77eec-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="77eec-140">您可以[自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="77eec-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="77eec-141">偵測到迴圈參考，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="77eec-142">目前已排除欄位。</span><span class="sxs-lookup"><span data-stu-id="77eec-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="77eec-143">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="77eec-143">Supported types include:</span></span>

* <span data-ttu-id="77eec-144">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="77eec-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="77eec-145">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="77eec-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="77eec-146">一維和不規則陣列（ `ArrayName[][]` ）。</span><span class="sxs-lookup"><span data-stu-id="77eec-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="77eec-147">`Dictionary<string,TValue>`其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="77eec-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="77eec-148">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="77eec-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="77eec-149">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)來處理其他類型，或提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="77eec-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="77eec-150">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="77eec-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="77eec-151">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="77eec-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="77eec-152">下列範例會從字串讀取 JSON，並建立 `WeatherForecast` 先前針對[序列化範例](#serialization-example)所顯示的類別實例：</span><span class="sxs-lookup"><span data-stu-id="77eec-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-153">若要使用同步程式碼從檔案還原序列化，請將檔案讀取到字串中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-154">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="77eec-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="77eec-155">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="77eec-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="77eec-156">若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `Utf8JsonReader` 或的多載， `ReadOnlySpan<byte>` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77eec-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="77eec-157">這些範例假設 JSON 位於名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="77eec-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="77eec-158">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="77eec-158">Deserialization behavior</span></span>

* <span data-ttu-id="77eec-159">根據預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="77eec-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="77eec-160">您可以[指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="77eec-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="77eec-161">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="77eec-162">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="77eec-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="77eec-163">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="77eec-164">根據預設，列舉會當做數位來支援。</span><span class="sxs-lookup"><span data-stu-id="77eec-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="77eec-165">您可以將[列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="77eec-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="77eec-166">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="77eec-166">Fields aren't supported.</span></span>
* <span data-ttu-id="77eec-167">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="77eec-168">您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="77eec-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="77eec-169">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="77eec-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="77eec-170">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="77eec-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="77eec-171">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="77eec-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="77eec-172">若要以整齊的格式列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="77eec-173">以下是要序列化的範例型別，以及相當列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="77eec-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="77eec-174">自訂 JSON 名稱和值</span><span class="sxs-lookup"><span data-stu-id="77eec-174">Customize JSON names and values</span></span>

<span data-ttu-id="77eec-175">根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="77eec-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="77eec-176">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="77eec-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="77eec-177">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="77eec-177">This section explains how to:</span></span>

* [<span data-ttu-id="77eec-178">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="77eec-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="77eec-179">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="77eec-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="77eec-180">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="77eec-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="77eec-181">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="77eec-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="77eec-182">將列舉轉換為字串和大小寫</span><span class="sxs-lookup"><span data-stu-id="77eec-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="77eec-183">針對需要對 JSON 屬性名稱和值進行特殊處理的其他案例，您可以[執行自訂轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="77eec-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="77eec-184">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="77eec-184">Customize individual property names</span></span>

<span data-ttu-id="77eec-185">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="77eec-186">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="77eec-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="77eec-187">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="77eec-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="77eec-188">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="77eec-189">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="77eec-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="77eec-190">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="77eec-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="77eec-191">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="77eec-192">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="77eec-193">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="77eec-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="77eec-194">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="77eec-195">會由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="77eec-196">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 案例的原因。</span><span class="sxs-lookup"><span data-stu-id="77eec-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="77eec-197">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="77eec-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="77eec-198">若要使用自訂 JSON 屬性命名原則，請建立衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="77eec-199">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="77eec-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-200">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="77eec-201">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="77eec-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="77eec-202">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="77eec-203">會由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="77eec-204">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="77eec-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="77eec-205">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="77eec-205">Camel case dictionary keys</span></span>

<span data-ttu-id="77eec-206">如果要序列化之物件的屬性屬於型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="77eec-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="77eec-207">若要這麼做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-208">使用名為的字典序列化 `TemperatureRanges` 具有索引鍵/值組 `"ColdMinTemp", 20` 且 `"HotMinTemp", 40` 會產生 JSON 輸出的物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="77eec-209">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="77eec-210">如果您將字典還原序列化，則即使您針對指定了，索引鍵仍會符合 JSON 檔案 `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="77eec-211">做為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="77eec-211">Enums as strings</span></span>

<span data-ttu-id="77eec-212">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="77eec-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="77eec-213">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。</span><span class="sxs-lookup"><span data-stu-id="77eec-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="77eec-214">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="77eec-215">如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="77eec-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="77eec-216">下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="77eec-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-217">產生的 JSON 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="77eec-218">列舉字串名稱也可以還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="77eec-219">排除序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-219">Exclude properties from serialization</span></span>

<span data-ttu-id="77eec-220">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="77eec-221">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="77eec-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="77eec-222">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="77eec-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="77eec-223">個別屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="77eec-224">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="77eec-225">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="77eec-226">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-226">Exclude individual properties</span></span>

<span data-ttu-id="77eec-227">若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="77eec-228">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="77eec-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="77eec-229">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-229">Exclude all read-only properties</span></span>

<span data-ttu-id="77eec-230">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="77eec-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="77eec-231">若要排除所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-232">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="77eec-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="77eec-233">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-233">This option applies only to serialization.</span></span> <span data-ttu-id="77eec-234">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="77eec-235">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-235">Exclude all null value properties</span></span>

<span data-ttu-id="77eec-236">若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-237">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="77eec-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="77eec-238">屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-238">Property</span></span> |<span data-ttu-id="77eec-239">值</span><span class="sxs-lookup"><span data-stu-id="77eec-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="77eec-240">Date</span><span class="sxs-lookup"><span data-stu-id="77eec-240">Date</span></span>    | <span data-ttu-id="77eec-241">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="77eec-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="77eec-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="77eec-242">TemperatureCelsius</span></span>| <span data-ttu-id="77eec-243">25</span><span class="sxs-lookup"><span data-stu-id="77eec-243">25</span></span> |
| <span data-ttu-id="77eec-244">總結</span><span class="sxs-lookup"><span data-stu-id="77eec-244">Summary</span></span>| <span data-ttu-id="77eec-245">null</span><span class="sxs-lookup"><span data-stu-id="77eec-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="77eec-246">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="77eec-247">如需其對還原序列化之影響的詳細資訊，請參閱[在還原序列化時忽略 null](#ignore-null-when-deserializing)。</span><span class="sxs-lookup"><span data-stu-id="77eec-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="77eec-248">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="77eec-248">Customize character encoding</span></span>

<span data-ttu-id="77eec-249">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="77eec-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="77eec-250">也就是說，它會取代它們， `\uxxxx` 其中 `xxxx` 是字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="77eec-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="77eec-251">例如，如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 會序列化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="77eec-252">序列化語言字元集</span><span class="sxs-lookup"><span data-stu-id="77eec-252">Serialize language character sets</span></span>

<span data-ttu-id="77eec-253">若要序列化一或多個語言的字元集而不進行轉義，請在建立實例時指定[Unicode 範圍](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="77eec-254">這段程式碼不會將斯拉夫文或希臘文字元取消換用。</span><span class="sxs-lookup"><span data-stu-id="77eec-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="77eec-255">如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 會序列化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="77eec-256">若要序列化所有語言集而不進行任何轉義，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="77eec-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="77eec-257">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="77eec-257">Serialize specific characters</span></span>

<span data-ttu-id="77eec-258">另一個替代方式是指定您想要允許通過的個別字元，而不會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="77eec-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="77eec-259">下列範例只會序列化жарко的前兩個字元：</span><span class="sxs-lookup"><span data-stu-id="77eec-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="77eec-260">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="77eec-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="77eec-261">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="77eec-261">Serialize all characters</span></span>

<span data-ttu-id="77eec-262">若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="77eec-263">相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼器更寬鬆，可讓字元通過非預設的傳遞：</span><span class="sxs-lookup"><span data-stu-id="77eec-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="77eec-264">它不會將 HTML 敏感的字元（例如 `<` 、 `>` 、和）換用 `&` `'` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="77eec-265">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深層防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在*字元集*上。</span><span class="sxs-lookup"><span data-stu-id="77eec-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="77eec-266">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="77eec-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="77eec-267">例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="77eec-268">永遠不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="77eec-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="77eec-269">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="77eec-270">不支援多型類型階層的序列化。</span><span class="sxs-lookup"><span data-stu-id="77eec-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="77eec-271">例如，如果屬性定義為介面或抽象類別，則即使執行時間類型有其他屬性，還是會序列化在介面或抽象類別上定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="77eec-272">這一節將說明此行為的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="77eec-273">例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="77eec-274">而且在編譯時期，假設方法的型別引數 `Serialize` 是 `WeatherForecast` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="77eec-275">在此案例中， `WindSpeed` 即使 `weatherForecast` 物件實際上是物件，也不會序列化屬性 `WeatherForecastDerived` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="77eec-276">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="77eec-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="77eec-277">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="77eec-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="77eec-278">若要在上述範例中序列化衍生型別的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="77eec-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="77eec-279">呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="77eec-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="77eec-280">宣告要序列化為的物件 `object` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="77eec-281">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="77eec-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="77eec-282">這些方法只會針對要序列化的根物件提供多型序列化，而不是針對該根物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="77eec-283">如果您將較低層級的物件定義為類型，則可以取得其多型序列化 `object` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="77eec-284">例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，可定義為類型 `WeatherForecast` 或 `object` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="77eec-285">如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="77eec-286">序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="77eec-287">序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="77eec-288">若要序列化 `WeatherForecastWithPreviousAsObject` ，則不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能屬於衍生類型的物件。</span><span class="sxs-lookup"><span data-stu-id="77eec-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="77eec-289">下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="77eec-290">上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="77eec-291">將屬性定義為與 `object` 介面搭配使用的相同方法。</span><span class="sxs-lookup"><span data-stu-id="77eec-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="77eec-292">假設您有下列介面和實作為，而且您想要使用包含實作為實例的屬性來序列化類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="77eec-293">當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="77eec-294">下列範例顯示上述程式碼所產生的 JSON：</span><span class="sxs-lookup"><span data-stu-id="77eec-294">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="77eec-295">如需多型**序列化**的詳細資訊，以及還原序列化**的相關資訊**，請參閱[如何從 Newtonsoft 遷移至 system.object](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。</span><span class="sxs-lookup"><span data-stu-id="77eec-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="77eec-296">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="77eec-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="77eec-297">根據預設，JSON 中不允許批註和尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="77eec-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="77eec-298">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="77eec-299">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="77eec-300">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="77eec-300">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-301">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="77eec-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="77eec-302">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="77eec-302">Case-insensitive property matching</span></span>

<span data-ttu-id="77eec-303">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="77eec-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="77eec-304">若要變更該行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-305">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="77eec-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="77eec-306">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="77eec-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="77eec-307">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="77eec-307">Handle overflow JSON</span></span>

<span data-ttu-id="77eec-308">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="77eec-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="77eec-309">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="77eec-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="77eec-310">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="77eec-310">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="77eec-311">如果您將顯示的 JSON 還原序列化為所顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="77eec-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="77eec-312">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至類型的屬性 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="77eec-313">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：</span><span class="sxs-lookup"><span data-stu-id="77eec-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="77eec-314">屬性</span><span class="sxs-lookup"><span data-stu-id="77eec-314">Property</span></span> |<span data-ttu-id="77eec-315">值</span><span class="sxs-lookup"><span data-stu-id="77eec-315">Value</span></span>  |<span data-ttu-id="77eec-316">附註</span><span class="sxs-lookup"><span data-stu-id="77eec-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="77eec-317">Date</span><span class="sxs-lookup"><span data-stu-id="77eec-317">Date</span></span>    | <span data-ttu-id="77eec-318">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="77eec-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="77eec-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="77eec-319">TemperatureCelsius</span></span>| <span data-ttu-id="77eec-320">0</span><span class="sxs-lookup"><span data-stu-id="77eec-320">0</span></span> | <span data-ttu-id="77eec-321">區分大小寫不相符（ `temperatureCelsius` 在 JSON 中），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="77eec-322">總結</span><span class="sxs-lookup"><span data-stu-id="77eec-322">Summary</span></span> | <span data-ttu-id="77eec-323">經常性存取</span><span class="sxs-lookup"><span data-stu-id="77eec-323">Hot</span></span> ||
| <span data-ttu-id="77eec-324">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="77eec-324">ExtensionData</span></span> | <span data-ttu-id="77eec-325">temperatureCelsius：25</span><span class="sxs-lookup"><span data-stu-id="77eec-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="77eec-326">因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="77eec-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="77eec-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="77eec-327">DatesAvailable:</span></span><br>  <span data-ttu-id="77eec-328">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="77eec-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="77eec-329">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="77eec-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="77eec-330">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="77eec-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="77eec-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="77eec-331">SummaryWords:</span></span><br><span data-ttu-id="77eec-332">非經常性存取</span><span class="sxs-lookup"><span data-stu-id="77eec-332">Cool</span></span><br><span data-ttu-id="77eec-333">風大</span><span class="sxs-lookup"><span data-stu-id="77eec-333">Windy</span></span><br><span data-ttu-id="77eec-334">潮濕</span><span class="sxs-lookup"><span data-stu-id="77eec-334">Humid</span></span> |<span data-ttu-id="77eec-335">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="77eec-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="77eec-336">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="77eec-337">請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="77eec-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="77eec-338">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="77eec-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="77eec-339">還原序列化時忽略 null</span><span class="sxs-lookup"><span data-stu-id="77eec-339">Ignore null when deserializing</span></span>

<span data-ttu-id="77eec-340">根據預設，如果 JSON 中的屬性是 null，則目標物件中的對應屬性會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="77eec-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="77eec-341">在某些情況下，目標屬性可能會有預設值，而且您不想要 null 值來覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="77eec-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="77eec-342">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="77eec-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="77eec-343">假設下列 JSON 已還原序列化：</span><span class="sxs-lookup"><span data-stu-id="77eec-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="77eec-344">還原序列化之後， `Summary` 物件的屬性 `WeatherForecastWithDefault` 為 null。</span><span class="sxs-lookup"><span data-stu-id="77eec-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="77eec-345">若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-346">使用此選項時， `Summary` 物件的屬性 `WeatherForecastWithDefault` 是還原序列化後的預設值「沒有摘要」。</span><span class="sxs-lookup"><span data-stu-id="77eec-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="77eec-347">JSON 中的 Null 值只有在有效時才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="77eec-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="77eec-348">不可為 null 的實數值型別的 Null 值會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="77eec-349">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="77eec-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="77eec-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>是一種高效能、低配置、順向讀取器，適用于 UTF-8 編碼的 JSON 文字，從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="77eec-351">`Utf8JsonReader`是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="77eec-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="77eec-352"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會 `Utf8JsonReader` 在幕後使用。</span><span class="sxs-lookup"><span data-stu-id="77eec-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="77eec-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>是從常見的 .NET 類型（例如、和）撰寫 UTF-8 編碼 JSON 文字的高效能 `String` 方式 `Int32` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="77eec-354">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="77eec-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="77eec-355"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會 `Utf8JsonWriter` 在幕後使用。</span><span class="sxs-lookup"><span data-stu-id="77eec-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="77eec-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>提供使用來建立唯讀檔案物件模型（DOM）的功能 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="77eec-357">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="77eec-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="77eec-358">組成裝載的 JSON 元素可以透過類型來存取 <xref:System.Text.Json.JsonElement> 。</span><span class="sxs-lookup"><span data-stu-id="77eec-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="77eec-359">`JsonElement`型別提供陣列和物件列舉值，以及用來將 JSON 文字轉換成常見 .net 類型的 api。</span><span class="sxs-lookup"><span data-stu-id="77eec-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="77eec-360">`JsonDocument`公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="77eec-361">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="77eec-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="77eec-362">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="77eec-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="77eec-363">下列範例顯示如何使用 <xref:System.Text.Json.JsonDocument> 類別，以隨機存取 JSON 字串中的資料：</span><span class="sxs-lookup"><span data-stu-id="77eec-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="77eec-364">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="77eec-364">The preceding code:</span></span>

* <span data-ttu-id="77eec-365">假設要分析的 JSON 是在名為的字串中 `jsonString` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="77eec-366">計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。</span><span class="sxs-lookup"><span data-stu-id="77eec-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="77eec-367">為沒有成績的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="77eec-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="77eec-368">藉由遞增 `count` 變數與每個反復專案來計算學生數目。</span><span class="sxs-lookup"><span data-stu-id="77eec-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="77eec-369">另一種方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77eec-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="77eec-370">以下是此程式碼所處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="77eec-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="77eec-371">使用 JsonDocument 寫入 JSON</span><span class="sxs-lookup"><span data-stu-id="77eec-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="77eec-372">下列範例顯示如何從寫入 JSON <xref:System.Text.Json.JsonDocument> ：</span><span class="sxs-lookup"><span data-stu-id="77eec-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="77eec-373">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="77eec-373">The preceding code:</span></span>

* <span data-ttu-id="77eec-374">讀取 JSON 檔案、將資料載入 `JsonDocument` ，並將格式化（已列印）的 JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="77eec-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="77eec-375">使用 <xref:System.Text.Json.JsonDocumentOptions> 來指定允許輸入 JSON 中的批註，但忽略。</span><span class="sxs-lookup"><span data-stu-id="77eec-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="77eec-376">完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。</span><span class="sxs-lookup"><span data-stu-id="77eec-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="77eec-377">另一個替代方式是讓寫入器在處置時 autoflush。</span><span class="sxs-lookup"><span data-stu-id="77eec-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="77eec-378">以下是範例程式碼所要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="77eec-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="77eec-379">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="77eec-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="77eec-380">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="77eec-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="77eec-381">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="77eec-382">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="77eec-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="77eec-383">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="77eec-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="77eec-384">上述程式碼假設 `jsonUtf8` 變數是包含有效 JSON 的位元組陣列，並以 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="77eec-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="77eec-385">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="77eec-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="77eec-386">下列範例示範如何以同步方式讀取檔案，並搜尋值：</span><span class="sxs-lookup"><span data-stu-id="77eec-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="77eec-387">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="77eec-387">The preceding code:</span></span>

* <span data-ttu-id="77eec-388">假設 JSON 包含物件的陣列，而且每個物件都可以包含 string 類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="77eec-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="77eec-389">計算以 "大學" 結尾的物件和「名稱」屬性值。</span><span class="sxs-lookup"><span data-stu-id="77eec-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="77eec-390">假設檔案是以 UTF-16 編碼，並將其轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="77eec-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="77eec-391">您可以 `ReadOnlySpan<byte>` 使用下列程式碼，直接將編碼為 utf-8 的檔案讀取至：</span><span class="sxs-lookup"><span data-stu-id="77eec-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="77eec-392">如果檔案包含 UTF-8 位元組順序標記（BOM），請先將它移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器需要文字。</span><span class="sxs-lookup"><span data-stu-id="77eec-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="77eec-393">否則，BOM 會被視為不正確 JSON，而讀取器會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77eec-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="77eec-394">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="77eec-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="77eec-395">產生的摘要訊息為「2個以上的名稱，其結尾為 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="77eec-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="77eec-396">其他資源</span><span class="sxs-lookup"><span data-stu-id="77eec-396">Additional resources</span></span>

* <span data-ttu-id="77eec-397">[System.Text.Json簡要](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="77eec-397">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="77eec-398">如何撰寫自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="77eec-398">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="77eec-399">[如何從進行遷移Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="77eec-399">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="77eec-400">[中的 DateTime 和 DateTimeOffset 支援System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="77eec-400">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="77eec-401">[System.Text.JsonAPI 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="77eec-401">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
