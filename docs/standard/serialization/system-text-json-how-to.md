---
title: 如何使用C# -.net 序列化和還原序列化 JSON
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a9c690e736a08c729a4099d5e7a519ed17ec282c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705791"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="8d8d0-102">如何在 .NET 中序列化和還原序列化 JSON</span><span class="sxs-lookup"><span data-stu-id="8d8d0-102">How to serialize and deserialize JSON in .NET</span></span>

<span data-ttu-id="8d8d0-103">本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="8d8d0-104">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="8d8d0-105">大部分的序列化範例程式碼會將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true` 「美觀」的 JSON （以縮排和空白字元來進行人類可讀性）。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="8d8d0-106">針對生產環境使用，您通常會接受此設定的預設值 `false`。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="8d8d0-107">命名空間</span><span class="sxs-lookup"><span data-stu-id="8d8d0-107">Namespaces</span></span>

<span data-ttu-id="8d8d0-108"><xref:System.Text.Json> 命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="8d8d0-109"><xref:System.Text.Json.Serialization> 命名空間包含用於高階案例的屬性和 Api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="8d8d0-110">本文中所示的程式碼範例需要其中一個或兩個命名空間的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="8d8d0-111">`System.Text.Json`目前不支援來自 <xref:System.Runtime.Serialization> 命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="8d8d0-112">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="8d8d0-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="8d8d0-113">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="8d8d0-114">下列範例會將 JSON 建立為字串：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-115">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-116">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-117">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="8d8d0-118">`Serialize()` 的多載會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="8d8d0-119">序列化範例</span><span class="sxs-lookup"><span data-stu-id="8d8d0-119">Serialization example</span></span>

<span data-ttu-id="8d8d0-120">以下是包含集合和嵌套類別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="8d8d0-121">序列化上述型別之實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="8d8d0-122">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="8d8d0-123">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="8d8d0-124">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="8d8d0-124">Serialize to UTF-8</span></span>

<span data-ttu-id="8d8d0-125">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-126">也可以使用接受 <xref:System.Text.Json.Utf8JsonWriter> 的 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 多載。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="8d8d0-127">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約5-10%。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="8d8d0-128">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="8d8d0-129">序列化行為</span><span class="sxs-lookup"><span data-stu-id="8d8d0-129">Serialization behavior</span></span>

* <span data-ttu-id="8d8d0-130">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="8d8d0-131">您可以[指定要排除的屬性](#exclude-properties-from-serialization)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="8d8d0-132">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="8d8d0-133">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-133">By default, JSON is minified.</span></span> <span data-ttu-id="8d8d0-134">您可以[整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="8d8d0-135">根據預設，JSON 名稱的大小寫會符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="8d8d0-136">您可以[自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="8d8d0-137">偵測到迴圈參考，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-137">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="8d8d0-138">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的[迴圈參考問題 38579](https://github.com/dotnet/corefx/issues/38579) 。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-138">For more information, see [issue 38579 on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="8d8d0-139">目前已排除欄位。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-139">Currently, fields are excluded.</span></span>

<span data-ttu-id="8d8d0-140">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-140">Supported types include:</span></span>

* <span data-ttu-id="8d8d0-141">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-141">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="8d8d0-142">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-142">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="8d8d0-143">一維和不規則陣列（`ArrayName[][]`）。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-143">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="8d8d0-144">`Dictionary<string,TValue>`，其中 `TValue` 是 `object`、`JsonElement`或 POCO。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-144">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="8d8d0-145">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-145">Collections from the following namespaces.</span></span> <span data-ttu-id="8d8d0-146">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的[集合支援問題](https://github.com/dotnet/corefx/issues/36643)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-146">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="8d8d0-147">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)來處理其他類型，或提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="8d8d0-148">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="8d8d0-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="8d8d0-149">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="8d8d0-150">下列範例會從字串讀取 JSON，並建立先前針對[序列化範例](#serialization-example)所顯示 `WeatherForecast` 類別的實例：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-151">若要使用同步程式碼從檔案還原序列化，請將檔案讀取到字串中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-152">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="8d8d0-153">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="8d8d0-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="8d8d0-154">若要從 UTF-8 還原序列化，請呼叫採用 `Utf8JsonReader` 或 `ReadOnlySpan<byte>`的 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 多載，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="8d8d0-155">這些範例假設 JSON 位於名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="8d8d0-156">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="8d8d0-156">Deserialization behavior</span></span>

* <span data-ttu-id="8d8d0-157">根據預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="8d8d0-158">您可以[指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="8d8d0-159">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="8d8d0-160">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="8d8d0-161">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="8d8d0-162">如需詳細資訊，請參閱 github[問題 38569 on 不可變物件支援](https://github.com/dotnet/corefx/issues/38569)和問題38163上的 dotnet/corefx 存放庫中的[唯讀屬性支援](https://github.com/dotnet/corefx/issues/38163)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-162">For more information, see GitHub [issue 38569 on immutable object support](https://github.com/dotnet/corefx/issues/38569) and [issue 38163 on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="8d8d0-163">根據預設，列舉會當做數位來支援。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="8d8d0-164">您可以將[列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="8d8d0-165">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-165">Fields aren't supported.</span></span>
* <span data-ttu-id="8d8d0-166">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="8d8d0-167">您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="8d8d0-168">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="8d8d0-169">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="8d8d0-170">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="8d8d0-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="8d8d0-171">若要以整齊的格式列印 JSON 輸出，請將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="8d8d0-172">以下是要序列化的範例型別，以及相當列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="8d8d0-173">自訂 JSON 名稱和值</span><span class="sxs-lookup"><span data-stu-id="8d8d0-173">Customize JSON names and values</span></span>

<span data-ttu-id="8d8d0-174">根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="8d8d0-175">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="8d8d0-176">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-176">This section explains how to:</span></span>

* [<span data-ttu-id="8d8d0-177">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8d8d0-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="8d8d0-178">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d8d0-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="8d8d0-179">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="8d8d0-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="8d8d0-180">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d8d0-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="8d8d0-181">將列舉轉換為字串和大小寫</span><span class="sxs-lookup"><span data-stu-id="8d8d0-181">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="8d8d0-182">針對需要對 JSON 屬性名稱和值進行特殊處理的其他案例，您可以[執行自訂轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="8d8d0-183">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8d8d0-183">Customize individual property names</span></span>

<span data-ttu-id="8d8d0-184">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="8d8d0-185">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d8d0-186">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="8d8d0-187">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="8d8d0-188">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="8d8d0-189">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d8d0-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="8d8d0-190">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="8d8d0-191">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d8d0-192">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="8d8d0-193">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="8d8d0-194">會由 `[JsonPropertyName]` 屬性來覆寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="8d8d0-195">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="8d8d0-196">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="8d8d0-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="8d8d0-197">若要使用自訂 JSON 屬性命名原則，請建立衍生自 <xref:System.Text.Json.JsonNamingPolicy> 的類別，並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="8d8d0-198">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-199">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d8d0-200">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="8d8d0-201">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="8d8d0-202">會由 `[JsonPropertyName]` 屬性來覆寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="8d8d0-203">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="8d8d0-204">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="8d8d0-204">Camel case dictionary keys</span></span>

<span data-ttu-id="8d8d0-205">如果要序列化之物件的屬性是 `Dictionary<string,TValue>`類型，則 `string` 索引鍵可以轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="8d8d0-206">若要這麼做，請將 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-207">使用名為 `TemperatureRanges` 的字典序列化物件，其中具有 `"ColdMinTemp", 20` 的索引鍵/值組，而 `"HotMinTemp", 40` 會產生如下列範例所示的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="8d8d0-208">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="8d8d0-209">如果您將字典還原序列化，則即使您指定 `DictionaryKeyPolicy`的 `JsonNamingPolicy.CamelCase`，索引鍵仍會符合 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="8d8d0-210">做為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="8d8d0-210">Enums as strings</span></span>

<span data-ttu-id="8d8d0-211">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="8d8d0-212">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter>。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="8d8d0-213">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="8d8d0-214">如果摘要是 `Hot`，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="8d8d0-215">下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-216">產生的 JSON 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="8d8d0-217">列舉字串名稱也可以還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="8d8d0-218">排除序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-218">Exclude properties from serialization</span></span>

<span data-ttu-id="8d8d0-219">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="8d8d0-220">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="8d8d0-221">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="8d8d0-222">個別屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="8d8d0-223">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="8d8d0-224">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="8d8d0-225">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-225">Exclude individual properties</span></span>

<span data-ttu-id="8d8d0-226">若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="8d8d0-227">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="8d8d0-228">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-228">Exclude all read-only properties</span></span>

<span data-ttu-id="8d8d0-229">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="8d8d0-230">若要排除所有唯讀屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-231">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="8d8d0-232">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-232">This option applies only to serialization.</span></span> <span data-ttu-id="8d8d0-233">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="8d8d0-234">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-234">Exclude all null value properties</span></span>

<span data-ttu-id="8d8d0-235">若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-236">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="8d8d0-237">屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-237">Property</span></span> |<span data-ttu-id="8d8d0-238">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="8d8d0-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="8d8d0-239">日期</span><span class="sxs-lookup"><span data-stu-id="8d8d0-239">Date</span></span>    | <span data-ttu-id="8d8d0-240">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="8d8d0-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="8d8d0-241">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="8d8d0-241">TemperatureCelsius</span></span>| <span data-ttu-id="8d8d0-242">25</span><span class="sxs-lookup"><span data-stu-id="8d8d0-242">25</span></span> |
| <span data-ttu-id="8d8d0-243">總結</span><span class="sxs-lookup"><span data-stu-id="8d8d0-243">Summary</span></span>| <span data-ttu-id="8d8d0-244">null</span><span class="sxs-lookup"><span data-stu-id="8d8d0-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="8d8d0-245">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="8d8d0-246">如需其對還原序列化之影響的詳細資訊，請參閱[在還原序列化時忽略 null](#ignore-null-when-deserializing)。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-246">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="8d8d0-247">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="8d8d0-247">Customize character encoding</span></span>

<span data-ttu-id="8d8d0-248">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-248">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="8d8d0-249">也就是說，它會以 `\uxxxx` 取代它們，其中 `xxxx` 是字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-249">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="8d8d0-250">例如，如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-250">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="8d8d0-251">序列化語言字元集</span><span class="sxs-lookup"><span data-stu-id="8d8d0-251">Serialize language character sets</span></span>

<span data-ttu-id="8d8d0-252">若要序列化一或多個語言的字元集而不進行轉義，請在建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>的實例時指定[Unicode 範圍](xref:System.Text.Unicode.UnicodeRanges)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-252">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="8d8d0-253">這段程式碼不會將斯拉夫文或希臘文字元取消換用。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-253">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="8d8d0-254">如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-254">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="8d8d0-255">若要序列化所有語言集而不進行任何轉義，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-255">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="8d8d0-256">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="8d8d0-256">Serialize specific characters</span></span>

<span data-ttu-id="8d8d0-257">另一個替代方式是指定您想要允許通過的個別字元，而不會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-257">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="8d8d0-258">下列範例只會序列化жарко的前兩個字元：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-258">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="8d8d0-259">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-259">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="8d8d0-260">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="8d8d0-260">Serialize all characters</span></span>

<span data-ttu-id="8d8d0-261">若要最小化進行的轉義，您可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-261">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="8d8d0-262">相較于預設編碼器，`UnsafeRelaxedJsonEscaping` 編碼器更寬鬆，可讓字元通過非預設的傳遞：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-262">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="8d8d0-263">它不會將 HTML 敏感的字元（例如 `<`、`>`、`&`和 `'`）換用。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-263">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="8d8d0-264">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深層防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在*字元集*上。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-264">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="8d8d0-265">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-265">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="8d8d0-266">例如，如果伺服器正在傳送回應標頭 `Content-Type: application/json; charset=utf-8`，您可以使用它。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-266">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="8d8d0-267">永遠不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-267">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="8d8d0-268">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-268">Serialize properties of derived classes</span></span>

<span data-ttu-id="8d8d0-269">當您在編譯時期指定要序列化的型別時，不支援多型序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-269">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="8d8d0-270">例如，假設您有 `WeatherForecast` 類別和衍生類別 `WeatherForecastDerived`：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-270">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="8d8d0-271">而且在編譯時期，假設 `Serialize` 方法的型別引數是 `WeatherForecast`：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-271">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="8d8d0-272">在此案例中，即使 `weatherForecast` 物件實際上是 `WeatherForecastDerived` 物件，`WindSpeed` 屬性也不會序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-272">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="8d8d0-273">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-273">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="8d8d0-274">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-274">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="8d8d0-275">若要序列化衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-275">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="8d8d0-276">呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 的多載，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-276">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="8d8d0-277">宣告要序列化為 `object`的物件。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-277">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="8d8d0-278">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-278">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="8d8d0-279">如需多型還原序列化的詳細資訊，請參閱[支援](system-text-json-converters-how-to.md#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-279">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="8d8d0-280">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="8d8d0-280">Allow comments and trailing commas</span></span>

<span data-ttu-id="8d8d0-281">根據預設，JSON 中不允許批註和尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-281">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="8d8d0-282">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設為 `JsonCommentHandling.Skip`。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-282">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="8d8d0-283">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-283">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="8d8d0-284">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-284">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-285">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-285">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="8d8d0-286">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="8d8d0-286">Case-insensitive property matching</span></span>

<span data-ttu-id="8d8d0-287">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-287">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="8d8d0-288">若要變更該行為，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-288">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-289">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-289">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="8d8d0-290">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-290">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="8d8d0-291">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="8d8d0-291">Handle overflow JSON</span></span>

<span data-ttu-id="8d8d0-292">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-292">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="8d8d0-293">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-293">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="8d8d0-294">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-294">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="8d8d0-295">如果您將顯示的 JSON 還原序列化為所顯示的類型，`DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-295">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="8d8d0-296">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>`類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-296">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="8d8d0-297">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成 `ExtensionData` 屬性的機碼值組：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-297">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="8d8d0-298">屬性</span><span class="sxs-lookup"><span data-stu-id="8d8d0-298">Property</span></span> |<span data-ttu-id="8d8d0-299">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="8d8d0-299">Value</span></span>  |<span data-ttu-id="8d8d0-300">注意事項</span><span class="sxs-lookup"><span data-stu-id="8d8d0-300">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="8d8d0-301">日期</span><span class="sxs-lookup"><span data-stu-id="8d8d0-301">Date</span></span>    | <span data-ttu-id="8d8d0-302">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="8d8d0-302">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="8d8d0-303">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="8d8d0-303">TemperatureCelsius</span></span>| <span data-ttu-id="8d8d0-304">0</span><span class="sxs-lookup"><span data-stu-id="8d8d0-304">0</span></span> | <span data-ttu-id="8d8d0-305">區分大小寫不相符（`temperatureCelsius` 在 JSON 中），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-305">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="8d8d0-306">總結</span><span class="sxs-lookup"><span data-stu-id="8d8d0-306">Summary</span></span> | <span data-ttu-id="8d8d0-307">熱</span><span class="sxs-lookup"><span data-stu-id="8d8d0-307">Hot</span></span> ||
| <span data-ttu-id="8d8d0-308">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="8d8d0-308">ExtensionData</span></span> | <span data-ttu-id="8d8d0-309">temperatureCelsius：25</span><span class="sxs-lookup"><span data-stu-id="8d8d0-309">temperatureCelsius: 25</span></span> |<span data-ttu-id="8d8d0-310">因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-310">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="8d8d0-311">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="8d8d0-311">DatesAvailable:</span></span><br>  <span data-ttu-id="8d8d0-312">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="8d8d0-312">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="8d8d0-313">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="8d8d0-313">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="8d8d0-314">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-314">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="8d8d0-315">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="8d8d0-315">SummaryWords:</span></span><br><span data-ttu-id="8d8d0-316">酷</span><span class="sxs-lookup"><span data-stu-id="8d8d0-316">Cool</span></span><br><span data-ttu-id="8d8d0-317">風大</span><span class="sxs-lookup"><span data-stu-id="8d8d0-317">Windy</span></span><br><span data-ttu-id="8d8d0-318">潮濕</span><span class="sxs-lookup"><span data-stu-id="8d8d0-318">Humid</span></span> |<span data-ttu-id="8d8d0-319">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-319">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="8d8d0-320">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-320">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="8d8d0-321">請注意，`ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-321">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="8d8d0-322">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-322">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="8d8d0-323">還原序列化時忽略 null</span><span class="sxs-lookup"><span data-stu-id="8d8d0-323">Ignore null when deserializing</span></span>

<span data-ttu-id="8d8d0-324">根據預設，如果 JSON 中的屬性是 null，則目標物件中的對應屬性會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-324">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="8d8d0-325">在某些情況下，目標屬性可能會有預設值，而且您不想要 null 值來覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-325">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="8d8d0-326">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-326">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="8d8d0-327">假設下列 JSON 已還原序列化：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-327">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="8d8d0-328">還原序列化之後，`WeatherForecastWithDefault` 物件的 `Summary` 屬性為 null。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-328">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="8d8d0-329">若要變更此行為，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-329">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-330">使用此選項時，`WeatherForecastWithDefault` 物件的 `Summary` 屬性是還原序列化後的預設值「沒有摘要」。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-330">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="8d8d0-331">JSON 中的 Null 值只有在有效時才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-331">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="8d8d0-332">不可為 null 的實數值型別的 Null 值會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-332">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="8d8d0-333">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的針對[不可為 null 的實數值型別問題 40922](https://github.com/dotnet/corefx/issues/40922) 。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-333">For more information, see [issue 40922 on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="8d8d0-334">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="8d8d0-334">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="8d8d0-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="8d8d0-336">`Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-336">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="8d8d0-337"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-337">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="8d8d0-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="8d8d0-339">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-339">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="8d8d0-340"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonWriter`。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-340">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="8d8d0-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用 `Utf8JsonReader`建立唯讀檔案物件模型（DOM）的功能。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="8d8d0-342">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-342">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="8d8d0-343">組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-343">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="8d8d0-344">`JsonElement` 類型提供陣列和物件列舉值，以及用來將 JSON 文字轉換成常見 .NET 類型的 Api。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-344">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="8d8d0-345">`JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-345">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="8d8d0-346">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-346">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="8d8d0-347">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="8d8d0-347">Use JsonDocument for access to data</span></span>

<span data-ttu-id="8d8d0-348">下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別來隨機存取 JSON 字串中的資料：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-348">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="8d8d0-349">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-349">The preceding code:</span></span>

* <span data-ttu-id="8d8d0-350">假設要分析的 JSON 是在名為 `jsonString`的字串中。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-350">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="8d8d0-351">計算 `Students` 陣列中具有 `Grade` 屬性之物件的平均等級。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-351">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="8d8d0-352">為沒有成績的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-352">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="8d8d0-353">藉由遞增 `count` 變數與每個反復專案來計算學生數目。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-353">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="8d8d0-354">另一種方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-354">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="8d8d0-355">以下是此程式碼所處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-355">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="8d8d0-356">使用 JsonDocument 寫入 JSON</span><span class="sxs-lookup"><span data-stu-id="8d8d0-356">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="8d8d0-357">下列範例顯示如何從 <xref:System.Text.Json.JsonDocument>寫入 JSON：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-357">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="8d8d0-358">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-358">The preceding code:</span></span>

* <span data-ttu-id="8d8d0-359">讀取 JSON 檔案、將資料載入 `JsonDocument`，並將格式化（已列印）的 JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-359">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="8d8d0-360">會使用 <xref:System.Text.Json.JsonDocumentOptions> 來指定允許輸入 JSON 中的批註，但會忽略它。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-360">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="8d8d0-361">完成時，會在寫入器上呼叫 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A>。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-361">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="8d8d0-362">另一個替代方式是讓寫入器在處置時 autoflush。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-362">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="8d8d0-363">以下是範例程式碼所要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-363">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="8d8d0-364">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-364">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="8d8d0-365">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="8d8d0-365">Use Utf8JsonWriter</span></span>

<span data-ttu-id="8d8d0-366">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-366">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="8d8d0-367">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="8d8d0-367">Use Utf8JsonReader</span></span>

<span data-ttu-id="8d8d0-368">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-368">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="8d8d0-369">上述程式碼假設 `jsonUtf8` 變數是包含有效 JSON 的位元組陣列，並以 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-369">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="8d8d0-370">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="8d8d0-370">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="8d8d0-371">下列範例示範如何以同步方式讀取檔案，並搜尋值：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-371">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="8d8d0-372">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-372">The preceding code:</span></span>

* <span data-ttu-id="8d8d0-373">假設檔案是以 UTF-16 編碼，並將其轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-373">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="8d8d0-374">您可以使用下列程式碼，直接將編碼為 UTF-8 的檔案讀入 `ReadOnlySpan<byte>`中：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-374">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="8d8d0-375">假設 JSON 包含物件的陣列，而且每個物件都可以包含 string 類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-375">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="8d8d0-376">計算物件，並 `name` 以「大學」結尾的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-376">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="8d8d0-377">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="8d8d0-377">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="8d8d0-378">產生的摘要訊息為「2個以上的名稱，其結尾為 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="8d8d0-378">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="8d8d0-379">其他資源</span><span class="sxs-lookup"><span data-stu-id="8d8d0-379">Additional resources</span></span>

* [<span data-ttu-id="8d8d0-380">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="8d8d0-380">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8d8d0-381">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="8d8d0-381">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="8d8d0-382">撰寫 System.object 的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="8d8d0-382">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="8d8d0-383">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="8d8d0-383">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="8d8d0-384">Dotnet/corefx 存放庫中標示為 json-功能的 GitHub 問題-doc</span><span class="sxs-lookup"><span data-stu-id="8d8d0-384">GitHub issues in the dotnet/corefx repository labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
