---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: '瞭解如何 System.Text.Json 在 .net 中使用命名空間進行序列化，並從 JSON 還原序列化。 包含範例程式碼。'
ms.date: 11/05/2020
no-loc:
- 'System.Text.Json'
- 'Newtonsoft.Json'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c1358b2b63a92cb50b853043adbfaae23ccd897
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329868"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="0f29a-104">如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON</span><span class="sxs-lookup"><span data-stu-id="0f29a-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="0f29a-105">本文說明如何使用 <xref:System.Text.Json?displayProperty=fullName> 命名空間，從 JavaScript 物件標記法 (JSON) 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="0f29a-106">如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="0f29a-107">指示和範例程式碼會直接使用程式庫，而不是透過 [ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="0f29a-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="0f29a-108">大部分的序列化程式碼範例會將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為「 `true` 美觀」的 JSON (，以縮排和空白字元來取得可讀性) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="0f29a-109">針對生產用途，您通常會接受此設定的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="0f29a-110">程式碼範例參考下列類別和它的變異：</span><span class="sxs-lookup"><span data-stu-id="0f29a-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="0f29a-111">命名空間</span><span class="sxs-lookup"><span data-stu-id="0f29a-111">Namespaces</span></span>

<span data-ttu-id="0f29a-112"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="0f29a-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="0f29a-113"><xref:System.Text.Json.Serialization>命名空間包含適用于進行序列化和還原序列化的 advanced 案例和自訂的屬性和 api。</span><span class="sxs-lookup"><span data-stu-id="0f29a-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="0f29a-114">本文中顯示的程式碼範例需要 `using` 下列其中一個或兩個命名空間的指示詞：</span><span class="sxs-lookup"><span data-stu-id="0f29a-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="0f29a-115"><xref:System.Runtime.Serialization>不支援命名空間中的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="0f29a-116">如何將 .NET 物件寫入 JSON (序列化) </span><span class="sxs-lookup"><span data-stu-id="0f29a-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="0f29a-117">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0f29a-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0f29a-118">下列範例會以字串形式建立 JSON：</span><span class="sxs-lookup"><span data-stu-id="0f29a-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-119">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="0f29a-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-120">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="0f29a-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-121">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="0f29a-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="0f29a-122">的多載 `Serialize()` 會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="0f29a-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="0f29a-123">序列化範例</span><span class="sxs-lookup"><span data-stu-id="0f29a-123">Serialization example</span></span>

<span data-ttu-id="0f29a-124">以下是包含集合類型屬性和使用者定義型別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="0f29a-125">"POCO" 代表 [純舊的 CLR 物件](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="0f29a-126">POCO 是一種 .NET 型別，其不相依于任何架構特定的類型，例如透過繼承或屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="0f29a-127">序列化上述型別的實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f29a-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="0f29a-128">JSON 輸出預設為縮減：</span><span class="sxs-lookup"><span data-stu-id="0f29a-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="0f29a-129">下列範例會顯示相同的 JSON，但格式化的 (也就是具有空白字元和縮排) 的整齊列印：</span><span class="sxs-lookup"><span data-stu-id="0f29a-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="0f29a-130">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="0f29a-130">Serialize to UTF-8</span></span>

<span data-ttu-id="0f29a-131">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="0f29a-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-132"><xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用採用的多載 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="0f29a-133">使用以字串為基礎的方法，序列化為 UTF-8 的速度大約是5-10%。</span><span class="sxs-lookup"><span data-stu-id="0f29a-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="0f29a-134">差異是因為 (為 UTF-8 的位元組) 不需要轉換成字串 (UTF-16) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="0f29a-135">序列化行為</span><span class="sxs-lookup"><span data-stu-id="0f29a-135">Serialization behavior</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="0f29a-136">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="0f29a-137">您可以 [指定要忽略的屬性](#ignore-properties)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-137">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="0f29a-138">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="0f29a-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="0f29a-139">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="0f29a-139">By default, JSON is minified.</span></span> <span data-ttu-id="0f29a-140">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="0f29a-141">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="0f29a-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="0f29a-142">您可以 [自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="0f29a-143">依預設，會偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="0f29a-144">您可以 [保留參考並處理迴圈參考](#preserve-references-and-handle-circular-references)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-144">You can [preserve references and handle circular references](#preserve-references-and-handle-circular-references).</span></span>
* <span data-ttu-id="0f29a-145">依預設，會忽略 [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="0f29a-146">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="0f29a-147">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="0f29a-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="0f29a-148">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-148">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="0f29a-149">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="0f29a-150">您可以 [指定要忽略的屬性](#ignore-properties)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-150">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="0f29a-151">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="0f29a-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="0f29a-152">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="0f29a-152">By default, JSON is minified.</span></span> <span data-ttu-id="0f29a-153">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="0f29a-154">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="0f29a-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="0f29a-155">您可以 [自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-155">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="0f29a-156">偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="0f29a-157">[欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="0f29a-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="0f29a-158">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="0f29a-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="0f29a-159">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="0f29a-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="0f29a-160">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="0f29a-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="0f29a-161">一維和不規則陣列 (`T[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="0f29a-162">下列命名空間中的集合和字典。</span><span class="sxs-lookup"><span data-stu-id="0f29a-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="0f29a-163">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="0f29a-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="0f29a-164">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="0f29a-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="0f29a-165">一維和不規則陣列 (`ArrayName[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="0f29a-166">`Dictionary<string,TValue>` 其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="0f29a-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="0f29a-167">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="0f29a-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="0f29a-168">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) 來處理其他類型，或是提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="0f29a-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="0f29a-169">如何將 JSON 讀入 .NET 物件 (還原序列化) </span><span class="sxs-lookup"><span data-stu-id="0f29a-169">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="0f29a-170">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0f29a-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0f29a-171">下列範例會從字串讀取 JSON，並 `WeatherForecastWithPOCOs` 為 [序列化範例](#serialization-example)建立稍早所示類別的實例：</span><span class="sxs-lookup"><span data-stu-id="0f29a-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="0f29a-172">若要使用同步程式碼從檔案還原序列化，請將檔案讀入字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="0f29a-173">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="0f29a-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="0f29a-174">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="0f29a-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="0f29a-175">若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `Utf8JsonReader` 或的多載， `ReadOnlySpan<byte>` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f29a-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="0f29a-176">這些範例假設 JSON 是在名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="0f29a-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="0f29a-177">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="0f29a-177">Deserialization behavior</span></span>

<span data-ttu-id="0f29a-178">將 JSON 還原序列化時，會套用下列行為：</span><span class="sxs-lookup"><span data-stu-id="0f29a-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="0f29a-179">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0f29a-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="0f29a-180">您可以 [指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-180">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="0f29a-181">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="0f29a-182">序列化程式會忽略非公用的函式。</span><span class="sxs-lookup"><span data-stu-id="0f29a-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="0f29a-183">支援還原序列化至不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="0f29a-184">請參閱 [不可變的類型和記錄](#immutable-types-and-records)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-184">See [Immutable types and Records](#immutable-types-and-records).</span></span>
* <span data-ttu-id="0f29a-185">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="0f29a-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="0f29a-186">您可以將 [列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-186">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="0f29a-187">依預設，會忽略欄位。</span><span class="sxs-lookup"><span data-stu-id="0f29a-187">By default, fields are ignored.</span></span> <span data-ttu-id="0f29a-188">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="0f29a-189">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="0f29a-190">您可以 [允許批註和結尾的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-190">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="0f29a-191">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="0f29a-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="0f29a-192">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="0f29a-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="0f29a-193">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-193">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="0f29a-194">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0f29a-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="0f29a-195">您可以 [指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-195">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span> <span data-ttu-id="0f29a-196">ASP.NET Core apps [預設會指定不區分大小寫](#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-196">ASP.NET Core apps [specify case-insensitivity by default](#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="0f29a-197">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="0f29a-198">無參數的函式（可以是公用、內部或私用）用於還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="0f29a-199">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="0f29a-200">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="0f29a-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="0f29a-201">您可以將 [列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-201">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="0f29a-202">不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="0f29a-202">Fields aren't supported.</span></span>
* <span data-ttu-id="0f29a-203">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="0f29a-204">您可以 [允許批註和結尾的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-204">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="0f29a-205">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="0f29a-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="0f29a-206">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="0f29a-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="0f29a-207">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-207">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="0f29a-208">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) ，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="0f29a-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="0f29a-209">序列化為格式化的 JSON</span><span class="sxs-lookup"><span data-stu-id="0f29a-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="0f29a-210">若要整齊列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="0f29a-211">以下是要序列化的範例型別，以及整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="0f29a-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="0f29a-212">包含欄位</span><span class="sxs-lookup"><span data-stu-id="0f29a-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-213"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>當序列化或還原序列化時，請使用全域設定或[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)屬性來包含欄位，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-213">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

<span data-ttu-id="0f29a-214">若要忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。</span><span class="sxs-lookup"><span data-stu-id="0f29a-214">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-215">System.Text.Json在 .Net Core 3.1 中不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="0f29a-215">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="0f29a-216">[自訂轉換器](system-text-json-converters-how-to.md) 可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="0f29a-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="customize-json-names-and-values"></a><span data-ttu-id="0f29a-217">自訂 JSON 名稱和值</span><span class="sxs-lookup"><span data-stu-id="0f29a-217">Customize JSON names and values</span></span>

<span data-ttu-id="0f29a-218">根據預設，JSON 輸出中的屬性名稱和字典索引鍵不會變更，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="0f29a-218">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="0f29a-219">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="0f29a-219">Enum values are represented as numbers.</span></span> <span data-ttu-id="0f29a-220">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="0f29a-220">This section explains how to:</span></span>

* [<span data-ttu-id="0f29a-221">自訂個別的屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0f29a-221">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="0f29a-222">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="0f29a-222">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="0f29a-223">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="0f29a-223">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="0f29a-224">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="0f29a-224">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="0f29a-225">將列舉轉換為字串和 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="0f29a-225">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="0f29a-226">對於需要特殊處理 JSON 屬性名稱和值的其他情況，您可以 [執行自訂的轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-226">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="0f29a-227">自訂個別的屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0f29a-227">Customize individual property names</span></span>

<span data-ttu-id="0f29a-228">若要設定個別屬性的名稱，請使用 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-228">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="0f29a-229">以下是要序列化並產生 JSON 的範例類型：</span><span class="sxs-lookup"><span data-stu-id="0f29a-229">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0f29a-230">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="0f29a-230">The property name set by this attribute:</span></span>

* <span data-ttu-id="0f29a-231">適用于雙向的序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-231">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="0f29a-232">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="0f29a-232">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="0f29a-233">針對所有 JSON 屬性名稱使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="0f29a-233">Use camel case for all JSON property names</span></span>

<span data-ttu-id="0f29a-234">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-234">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="0f29a-235">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-235">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0f29a-236">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="0f29a-236">The camel case property naming policy:</span></span>

* <span data-ttu-id="0f29a-237">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-237">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0f29a-238">由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-238">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0f29a-239">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大寫字母的原因。</span><span class="sxs-lookup"><span data-stu-id="0f29a-239">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="0f29a-240">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="0f29a-240">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="0f29a-241">若要使用自訂 JSON 屬性命名原則，請建立一個衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-241">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="0f29a-242">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="0f29a-242">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-243">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-243">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0f29a-244">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="0f29a-244">The JSON property naming policy:</span></span>

* <span data-ttu-id="0f29a-245">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-245">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0f29a-246">由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-246">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0f29a-247">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="0f29a-247">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="0f29a-248">Camel 案例字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="0f29a-248">Camel case dictionary keys</span></span>

<span data-ttu-id="0f29a-249">如果要序列化之物件的屬性是型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="0f29a-249">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="0f29a-250">若要這樣做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-250">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-251">使用名為的字典序列化 `TemperatureRanges` 具有索引鍵/值組的物件 `"ColdMinTemp", 20` ， `"HotMinTemp", 40` 將會產生如下列範例所示的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="0f29a-251">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="0f29a-252">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-252">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="0f29a-253">如果您將字典還原序列化，即使您為指定，金鑰也會與 JSON 檔案相符 `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-253">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="0f29a-254">作為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="0f29a-254">Enums as strings</span></span>

<span data-ttu-id="0f29a-255">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="0f29a-255">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="0f29a-256">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-256">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="0f29a-257">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-257">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="0f29a-258">如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="0f29a-258">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="0f29a-259">下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="0f29a-259">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-260">產生的 JSON 看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-260">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="0f29a-261">您也可以還原序列化列舉字串名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-261">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a><span data-ttu-id="0f29a-262">略過屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-262">Ignore properties</span></span>

<span data-ttu-id="0f29a-263">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-263">By default, all public properties are serialized.</span></span> <span data-ttu-id="0f29a-264">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="0f29a-264">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="0f29a-265">本節說明如何忽略：</span><span class="sxs-lookup"><span data-stu-id="0f29a-265">This section explains how to ignore:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="0f29a-266">個別屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-266">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="0f29a-267">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-267">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="0f29a-268">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-268">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="0f29a-269">所有預設值屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-269">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="0f29a-270">個別屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-270">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="0f29a-271">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-271">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="0f29a-272">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-272">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a><span data-ttu-id="0f29a-273">略過個別屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-273">Ignore individual properties</span></span>

<span data-ttu-id="0f29a-274">若要忽略個別的屬性，請使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-274">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="0f29a-275">以下是序列化和 JSON 輸出的範例類型：</span><span class="sxs-lookup"><span data-stu-id="0f29a-275">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-276">您可以藉由設定 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的屬性來指定條件排除 `Condition` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-276">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="0f29a-277"><xref:System.Text.Json.Serialization.JsonIgnoreCondition>列舉提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="0f29a-277">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="0f29a-278">`Always` -一律會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-278">`Always` - The property is always ignored.</span></span> <span data-ttu-id="0f29a-279">如果未 `Condition` 指定，則會假設為這個選項。</span><span class="sxs-lookup"><span data-stu-id="0f29a-279">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="0f29a-280">`Never` -無論 `DefaultIgnoreCondition` 、 `IgnoreReadOnlyProperties` 和全域設定為何，一律會將屬性序列化和還原序列化 `IgnoreReadOnlyFields` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-280">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="0f29a-281">`WhenWritingDefault` -如果是參考型別或實值型別，則會忽略序列化的屬性 `null` `default` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-281">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null` or a value type `default`.</span></span>
* <span data-ttu-id="0f29a-282">`WhenWritingNull` -如果是參考型別，則會忽略序列化的屬性 `null` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-282">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`.</span></span>

<span data-ttu-id="0f29a-283">下列範例說明如何使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的 `Condition` 屬性：</span><span class="sxs-lookup"><span data-stu-id="0f29a-283">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a><span data-ttu-id="0f29a-284">忽略所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-284">Ignore all read-only properties</span></span>

<span data-ttu-id="0f29a-285">如果屬性包含公用 getter 而非公用 setter，則該屬性為唯讀。</span><span class="sxs-lookup"><span data-stu-id="0f29a-285">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="0f29a-286">若要在序列化時忽略所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-286">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-287">以下是序列化和 JSON 輸出的範例類型：</span><span class="sxs-lookup"><span data-stu-id="0f29a-287">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="0f29a-288">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-288">This option applies only to serialization.</span></span> <span data-ttu-id="0f29a-289">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-289">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-290">此選項只適用于屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-290">This option applies only to properties.</span></span> <span data-ttu-id="0f29a-291">若要在序列化 [欄位](#include-fields)時忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。</span><span class="sxs-lookup"><span data-stu-id="0f29a-291">To ignore read-only fields when [serializing fields](#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

### <a name="ignore-all-null-value-properties"></a><span data-ttu-id="0f29a-292">忽略所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-292">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-293">若要忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-293">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-294">若要在序列化時忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-294">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-295">以下是序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="0f29a-295">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="0f29a-296">屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-296">Property</span></span> |<span data-ttu-id="0f29a-297">值</span><span class="sxs-lookup"><span data-stu-id="0f29a-297">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="0f29a-298">Date</span><span class="sxs-lookup"><span data-stu-id="0f29a-298">Date</span></span>    | <span data-ttu-id="0f29a-299">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="0f29a-299">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="0f29a-300">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="0f29a-300">TemperatureCelsius</span></span>| <span data-ttu-id="0f29a-301">25</span><span class="sxs-lookup"><span data-stu-id="0f29a-301">25</span></span> |
| <span data-ttu-id="0f29a-302">摘要</span><span class="sxs-lookup"><span data-stu-id="0f29a-302">Summary</span></span>| <span data-ttu-id="0f29a-303">null</span><span class="sxs-lookup"><span data-stu-id="0f29a-303">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a><span data-ttu-id="0f29a-304">略過所有預設值屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-304">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-305">若要避免在數值型別屬性中序列化預設值，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-305">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="0f29a-306">這 `WhenWritingDefault` 項設定也會防止 null 值參考型別屬性的序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-306">The `WhenWritingDefault` setting also prevents serialization of null-value reference type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-307">沒有內建的方法可防止序列化 .NET Core 3.1 中具有值型別預設值的屬性 System.Text.Json 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-307">There is no built-in way to prevent serialization of properties with value type defaults in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="customize-character-encoding"></a><span data-ttu-id="0f29a-308">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="0f29a-308">Customize character encoding</span></span>

<span data-ttu-id="0f29a-309">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="0f29a-309">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="0f29a-310">也就是說，它會將它們取代 `\uxxxx` 為 `xxxx` 字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="0f29a-310">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="0f29a-311">例如，如果將 `Summary` 屬性設定為斯拉夫жарко，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-311">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="0f29a-312">將語言字元集序列化</span><span class="sxs-lookup"><span data-stu-id="0f29a-312">Serialize language character sets</span></span>

<span data-ttu-id="0f29a-313">若要將一或多個語言的字元集)  (s，而不進行任何轉義，請在建立實例時指定 [Unicode 範圍 () ](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-313">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="0f29a-314">此程式碼不會將斯拉夫文或希臘文字元換成。</span><span class="sxs-lookup"><span data-stu-id="0f29a-314">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="0f29a-315">如果 `Summary` 屬性設定為斯拉夫жарко，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-315">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="0f29a-316">若要在不經過轉義的情況下序列化所有語言集，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-316">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="0f29a-317">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="0f29a-317">Serialize specific characters</span></span>

<span data-ttu-id="0f29a-318">替代方法是指定您想要允許的個別字元，而不需要經過轉義。</span><span class="sxs-lookup"><span data-stu-id="0f29a-318">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="0f29a-319">下列範例只會將жарко的前兩個字元序列化：</span><span class="sxs-lookup"><span data-stu-id="0f29a-319">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="0f29a-320">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="0f29a-320">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="0f29a-321">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="0f29a-321">Serialize all characters</span></span>

<span data-ttu-id="0f29a-322">若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-322">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="0f29a-323">相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼程式更寬鬆，可讓字元通過非重設密碼：</span><span class="sxs-lookup"><span data-stu-id="0f29a-323">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="0f29a-324">它不會對 HTML 敏感的字元（例如、、和）進行換用 `<` `>` `&` `'` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-324">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="0f29a-325">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深度防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在 *字元集* 上所產生的。</span><span class="sxs-lookup"><span data-stu-id="0f29a-325">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="0f29a-326">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="0f29a-326">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="0f29a-327">例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-327">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="0f29a-328">絕不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="0f29a-328">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="0f29a-329">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-329">Serialize properties of derived classes</span></span>

<span data-ttu-id="0f29a-330">不支援多型類型階層的序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-330">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="0f29a-331">例如，如果屬性定義為介面或抽象類別，則只有在介面或抽象類別上定義的屬性會序列化，即使執行時間型別具有其他屬性也一樣。</span><span class="sxs-lookup"><span data-stu-id="0f29a-331">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="0f29a-332">本節將說明此行為的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-332">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="0f29a-333">例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-333">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="0f29a-334">並假設在編譯時期，方法的型別引數 `Serialize` 是 `WeatherForecast` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-334">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="0f29a-335">在此案例中， `WindSpeed` 即使物件實際上是物件，也不會序列化屬性 `weatherForecast` `WeatherForecastDerived` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-335">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="0f29a-336">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="0f29a-336">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="0f29a-337">這項行為旨在協助防止在衍生的執行時間建立型別中意外曝光資料。</span><span class="sxs-lookup"><span data-stu-id="0f29a-337">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="0f29a-338">若要序列化上述範例中衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="0f29a-338">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="0f29a-339">呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定型別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-339">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="0f29a-340">宣告要序列化為的物件 `object` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-340">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="0f29a-341">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="0f29a-341">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="0f29a-342">這些方法只會針對要序列化的根物件提供多型的序列化，而不是針對該根物件的屬性提供。</span><span class="sxs-lookup"><span data-stu-id="0f29a-342">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="0f29a-343">如果您將物件定義為類型，則可以取得較低層級物件的多型序列化 `object` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-343">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="0f29a-344">例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，該屬性可以定義為類型 `WeatherForecast` 或 `object` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-344">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="0f29a-345">如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-345">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="0f29a-346">序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包括在內** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-346">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="0f29a-347">序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-347">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="0f29a-348">若要序列化 `WeatherForecastWithPreviousAsObject` ，不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能是衍生類型的物件。</span><span class="sxs-lookup"><span data-stu-id="0f29a-348">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="0f29a-349">下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-349">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="0f29a-350">上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-350">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="0f29a-351">將屬性定義為 `object` 與介面搭配使用的相同方法。</span><span class="sxs-lookup"><span data-stu-id="0f29a-351">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="0f29a-352">假設您有下列介面和執行，而且您想要使用包含實實例的屬性來序列化類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-352">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="0f29a-353">當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-353">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="0f29a-354">下列範例顯示上述程式碼所產生的 JSON：</span><span class="sxs-lookup"><span data-stu-id="0f29a-354">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="0f29a-355">如需多型序列化的詳細資訊，以及有關還原 **序列化** 的詳細 **資訊，請** 參閱 [如何從遷移 Newtonsoft.Json System.Text.Json 至](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-355">For more information about polymorphic **serialization** , and for information about **deserialization** , see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="0f29a-356">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="0f29a-356">Allow comments and trailing commas</span></span>

<span data-ttu-id="0f29a-357">根據預設，JSON 中不允許批註和結尾的逗號。</span><span class="sxs-lookup"><span data-stu-id="0f29a-357">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="0f29a-358">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-358">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="0f29a-359">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-359">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="0f29a-360">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="0f29a-360">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="0f29a-361">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="0f29a-361">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="0f29a-362">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="0f29a-362">Case-insensitive property matching</span></span>

<span data-ttu-id="0f29a-363">根據預設，還原序列化會尋找 JSON 與目標物件屬性之間是否有區分大小寫的屬性名稱相符專案。</span><span class="sxs-lookup"><span data-stu-id="0f29a-363">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="0f29a-364">若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-364">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="0f29a-365">以下是使用 camel 大小寫屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="0f29a-365">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="0f29a-366">您可以將它還原序列化為具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="0f29a-366">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="0f29a-367">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="0f29a-367">Handle overflow JSON</span></span>

<span data-ttu-id="0f29a-368">還原序列化時，您可能會收到 JSON 中的資料，而該資料不是由目標型別的屬性所表示。</span><span class="sxs-lookup"><span data-stu-id="0f29a-368">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="0f29a-369">例如，假設您的目標型別是：</span><span class="sxs-lookup"><span data-stu-id="0f29a-369">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="0f29a-370">而且要還原序列化的 JSON 如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-370">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="0f29a-371">如果您將顯示的 JSON 還原序列化為顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="0f29a-371">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="0f29a-372">若要捕獲額外的資料（例如這些屬性），請將 [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 屬性套用至類型或的屬性 `Dictionary<string,object>` `Dictionary<string,JsonElement>` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-372">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="0f29a-373">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-373">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="0f29a-374">屬性</span><span class="sxs-lookup"><span data-stu-id="0f29a-374">Property</span></span> |<span data-ttu-id="0f29a-375">值</span><span class="sxs-lookup"><span data-stu-id="0f29a-375">Value</span></span>  |<span data-ttu-id="0f29a-376">備忘錄</span><span class="sxs-lookup"><span data-stu-id="0f29a-376">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="0f29a-377">Date</span><span class="sxs-lookup"><span data-stu-id="0f29a-377">Date</span></span>    | <span data-ttu-id="0f29a-378">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="0f29a-378">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="0f29a-379">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="0f29a-379">TemperatureCelsius</span></span>| <span data-ttu-id="0f29a-380">0</span><span class="sxs-lookup"><span data-stu-id="0f29a-380">0</span></span> | <span data-ttu-id="0f29a-381">JSON)  (區分大小寫不符 `temperatureCelsius` ，因此未設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-381">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="0f29a-382">摘要</span><span class="sxs-lookup"><span data-stu-id="0f29a-382">Summary</span></span> | <span data-ttu-id="0f29a-383">經常性存取層</span><span class="sxs-lookup"><span data-stu-id="0f29a-383">Hot</span></span> ||
| <span data-ttu-id="0f29a-384">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="0f29a-384">ExtensionData</span></span> | <span data-ttu-id="0f29a-385">temperatureCelsius：25</span><span class="sxs-lookup"><span data-stu-id="0f29a-385">temperatureCelsius: 25</span></span> |<span data-ttu-id="0f29a-386">因為大小寫不相符，所以這個 JSON 屬性是一個額外的，並且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="0f29a-386">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="0f29a-387">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="0f29a-387">DatesAvailable:</span></span><br>  <span data-ttu-id="0f29a-388">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="0f29a-388">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="0f29a-389">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="0f29a-389">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="0f29a-390">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="0f29a-390">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="0f29a-391">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="0f29a-391">SummaryWords:</span></span><br><span data-ttu-id="0f29a-392">非經常性</span><span class="sxs-lookup"><span data-stu-id="0f29a-392">Cool</span></span><br><span data-ttu-id="0f29a-393">風</span><span class="sxs-lookup"><span data-stu-id="0f29a-393">Windy</span></span><br><span data-ttu-id="0f29a-394">潮濕</span><span class="sxs-lookup"><span data-stu-id="0f29a-394">Humid</span></span> |<span data-ttu-id="0f29a-395">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="0f29a-395">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="0f29a-396">序列化目標物件時，擴充功能資料索引鍵值組會變成 JSON 屬性，就像在傳入的 JSON 中一樣：</span><span class="sxs-lookup"><span data-stu-id="0f29a-396">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="0f29a-397">請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="0f29a-397">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="0f29a-398">此行為可讓 JSON 進行往返，而不會遺失任何額外的資料，否則不會還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f29a-398">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="0f29a-399">保留參考並處理迴圈參考</span><span class="sxs-lookup"><span data-stu-id="0f29a-399">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="0f29a-400">若要保留參考並處理迴圈參考，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-400">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="0f29a-401">這項設定會導致下列行為：</span><span class="sxs-lookup"><span data-stu-id="0f29a-401">This setting causes the following behavior:</span></span>

* <span data-ttu-id="0f29a-402">序列化時：</span><span class="sxs-lookup"><span data-stu-id="0f29a-402">On serialize:</span></span>

  <span data-ttu-id="0f29a-403">撰寫複雜型別時，序列化程式也會將中繼資料屬性寫入 (`$id` 、 `$values` 和 `$ref`) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-403">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="0f29a-404">還原序列化時：</span><span class="sxs-lookup"><span data-stu-id="0f29a-404">On deserialize:</span></span>

  <span data-ttu-id="0f29a-405">雖然不是必要的) ，但還原序列化程式會嘗試瞭解中繼資料，但 (的預期。</span><span class="sxs-lookup"><span data-stu-id="0f29a-405">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="0f29a-406">下列程式碼說明如何使用此 `Preserve` 設定。</span><span class="sxs-lookup"><span data-stu-id="0f29a-406">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="0f29a-407">這項功能不能用來保留實數值型別或不可變的類型。</span><span class="sxs-lookup"><span data-stu-id="0f29a-407">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="0f29a-408">在還原序列化時，會在讀取整個裝載之後，建立不可變型別的實例。</span><span class="sxs-lookup"><span data-stu-id="0f29a-408">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="0f29a-409">因此，如果它的參考出現在 JSON 承載內，就不可能還原序列化相同的實例。</span><span class="sxs-lookup"><span data-stu-id="0f29a-409">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="0f29a-410">如果是實值型別、不可變的型別和陣列，則不會序列化任何參考中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0f29a-410">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="0f29a-411">在還原序列化時，如果找到或，則會擲回例外狀況 `$ref` `$id` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-411">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="0f29a-412">不過，實值型別 `$id` 會忽略 (，而 `$values` 在集合的情況下) ，讓您可以還原序列化使用序列化的承載 Newtonsoft.Json 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-412">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="0f29a-413">Newtonsoft.Json 會序列化這類類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0f29a-413">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="0f29a-414">若要判斷物件是否相等， System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> 請使用，它會使用參考相等 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) 而不是 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 在比較兩個物件實例時 (值相等。</span><span class="sxs-lookup"><span data-stu-id="0f29a-414">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="0f29a-415">如需如何序列化和還原序列化參考的詳細資訊，請參閱 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-415">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0f29a-416"><xref:System.Text.Json.Serialization.ReferenceResolver>類別會定義在序列化和還原序列化時保留參考的行為。</span><span class="sxs-lookup"><span data-stu-id="0f29a-416">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="0f29a-417">建立衍生類別以指定自訂行為。</span><span class="sxs-lookup"><span data-stu-id="0f29a-417">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="0f29a-418">如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-418">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-419">System.Text.Json 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-419">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="0f29a-420">以引號允許或寫入數位</span><span class="sxs-lookup"><span data-stu-id="0f29a-420">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="0f29a-421">某些序列化程式會將數位編碼為 JSON 字串， (以引號括住) 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-421">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="0f29a-422">例如： `{"DegreesCelsius":"23"}` 而不是 `{"DegreesCelsius":23}` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-422">For example: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="0f29a-423">若要序列化引號中的數位，或在整個輸入物件圖形中接受以引號括住的數位，請設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-423">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

<span data-ttu-id="0f29a-424">當您 System.Text.Json 透過 ASP.NET Core 間接使用時，當還原序列化時，會允許括住的數位，因為 ASP.NET Core 指定 [web 預設選項](xref:System.Text.Json.JsonSerializerDefaults.Web)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-424">When you use System.Text.Json indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="0f29a-425">若要允許或寫入特定屬性、欄位或類型的引號號碼，請使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-425">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-426">System.Text.Json 在 .NET Core 3.1 中，不支援序列化或還原序列化以引號括住的數位。</span><span class="sxs-lookup"><span data-stu-id="0f29a-426">System.Text.Json in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="0f29a-427">如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)住的數位。</span><span class="sxs-lookup"><span data-stu-id="0f29a-427">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="immutable-types-and-records"></a><span data-ttu-id="0f29a-428">不可變的類型和記錄</span><span class="sxs-lookup"><span data-stu-id="0f29a-428">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-429">System.Text.Json 可以使用參數化的函式，讓您可以還原序列化不可變的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="0f29a-429">System.Text.Json can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="0f29a-430">針對類別，如果唯一的函式是參數化的，則會使用該函數。</span><span class="sxs-lookup"><span data-stu-id="0f29a-430">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="0f29a-431">若為結構或具有多個函式的類別，請套用 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 屬性，以指定要使用的類別。</span><span class="sxs-lookup"><span data-stu-id="0f29a-431">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="0f29a-432">未使用屬性時，一律會使用公用無參數的函式（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="0f29a-432">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="0f29a-433">屬性只能搭配公用的函式使用。</span><span class="sxs-lookup"><span data-stu-id="0f29a-433">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="0f29a-434">下列範例會使用 `[JsonConstructor]` 屬性：</span><span class="sxs-lookup"><span data-stu-id="0f29a-434">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="0f29a-435">也支援 c # 9 中的記錄，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-435">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="0f29a-436">針對不可變的類型，因為其所有屬性 setter 都非公用，請參閱下一節有關 [非公用屬性存取](#non-public-property-accessors)子的資訊。</span><span class="sxs-lookup"><span data-stu-id="0f29a-436">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-437">`JsonConstructorAttribute` 和 c # 9 記錄支援在 .NET Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="0f29a-437">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="0f29a-438">非公用屬性存取子</span><span class="sxs-lookup"><span data-stu-id="0f29a-438">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-439">若要允許使用非公用屬性存取子，請使用 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-439">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-440">.NET Core 3.1 不支援非公用屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="0f29a-440">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="0f29a-441">如需詳細資訊，請參閱「 [從 Newtonsoft.Json 文章遷移](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)」。</span><span class="sxs-lookup"><span data-stu-id="0f29a-441">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="0f29a-442">複製 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="0f29a-442">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-443">有 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerOptions) # A3，可讓您使用與現有實例相同的選項來建立新的實例，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-443">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-444">`JsonSerializerOptions`在 .Net Core 3.1 中無法使用採用現有實例的函式。</span><span class="sxs-lookup"><span data-stu-id="0f29a-444">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="0f29a-445">JsonSerializerOptions 的 Web 預設值</span><span class="sxs-lookup"><span data-stu-id="0f29a-445">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="0f29a-446">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="0f29a-446">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="0f29a-447">有一個 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerDefaults) ？ view = net-5.0&preserve-view = true) 可讓您建立新的實例，其中包含 ASP.NET Core 用於 web 應用程式的預設選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-447">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-448">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="0f29a-448">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="0f29a-449">`JsonSerializerOptions`指定一組預設值的函式在 .Net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="0f29a-449">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="0f29a-450">HttpClient 和 HttpContent 擴充方法</span><span class="sxs-lookup"><span data-stu-id="0f29a-450">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="0f29a-451">從網路序列化和還原序列化 JSON 承載是常見的作業。</span><span class="sxs-lookup"><span data-stu-id="0f29a-451">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="0f29a-452">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions)和[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)上的擴充方法可讓您在一行程式碼中進行這些作業。</span><span class="sxs-lookup"><span data-stu-id="0f29a-452">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="0f29a-453">這些擴充方法會使用 [web 預設值進行 JsonSerializerOptions](#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="0f29a-453">These extension methods use [web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="0f29a-454">下列範例說明如何使用 <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-454">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

<span data-ttu-id="0f29a-455">此外，也有適用 System.Text.Json 于 [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="0f29a-455">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="0f29a-456">和上的擴充方法在 `HttpClient` `HttpContent` System.Text.Json .net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="0f29a-456">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="0f29a-457">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="0f29a-457">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="0f29a-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="0f29a-459">`Utf8JsonReader`是低層級的型別，可用來建立自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="0f29a-459">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="0f29a-460"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonReader` 幕後。</span><span class="sxs-lookup"><span data-stu-id="0f29a-460">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="0f29a-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（如、和）撰寫 UTF-8 編碼的 JSON 文字 `String` `Int32` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="0f29a-462">寫入器是一種低層級的型別，可用來建立自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="0f29a-462">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="0f29a-463"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonWriter` 幕後。</span><span class="sxs-lookup"><span data-stu-id="0f29a-463">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="0f29a-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用建立唯讀檔案物件模型 (DOM) 的功能 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="0f29a-465">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="0f29a-465">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="0f29a-466">撰寫承載的 JSON 專案可以透過型別存取 <xref:System.Text.Json.JsonElement> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-466">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="0f29a-467">此 `JsonElement` 類型提供陣列和物件列舉值以及 api，以將 JSON 文字轉換成常見的 .net 類型。</span><span class="sxs-lookup"><span data-stu-id="0f29a-467">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="0f29a-468">`JsonDocument` 公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-468">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="0f29a-469">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="0f29a-469">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="0f29a-470">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="0f29a-470">Use JsonDocument for access to data</span></span>

<span data-ttu-id="0f29a-471">下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別，隨機存取 JSON 字串中的資料：</span><span class="sxs-lookup"><span data-stu-id="0f29a-471">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="0f29a-472">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="0f29a-472">The preceding code:</span></span>

* <span data-ttu-id="0f29a-473">假設要分析的 JSON 是在名為的字串中 `jsonString` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-473">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="0f29a-474">計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-474">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="0f29a-475">針對沒有等級的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="0f29a-475">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="0f29a-476">依每個反復專案遞增變數來計算學生數目 `count` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-476">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="0f29a-477">替代方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f29a-477">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="0f29a-478">以下是此程式碼處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="0f29a-478">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="0f29a-479">使用 JsonDocument 撰寫 JSON</span><span class="sxs-lookup"><span data-stu-id="0f29a-479">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="0f29a-480">下列範例顯示如何從撰寫 JSON <xref:System.Text.Json.JsonDocument> ：</span><span class="sxs-lookup"><span data-stu-id="0f29a-480">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="0f29a-481">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="0f29a-481">The preceding code:</span></span>

* <span data-ttu-id="0f29a-482">讀取 JSON 檔案、將資料載入中 `JsonDocument` ，然後將格式化 (美觀的) JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="0f29a-482">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="0f29a-483">使用 <xref:System.Text.Json.JsonDocumentOptions> 指定允許但忽略輸入 JSON 中的批註。</span><span class="sxs-lookup"><span data-stu-id="0f29a-483">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="0f29a-484">完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f29a-484">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="0f29a-485">替代方法是讓寫入器在處置時 autoflush。</span><span class="sxs-lookup"><span data-stu-id="0f29a-485">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="0f29a-486">以下是範例程式碼要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="0f29a-486">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="0f29a-487">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="0f29a-487">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="0f29a-488">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="0f29a-488">Use Utf8JsonWriter</span></span>

<span data-ttu-id="0f29a-489">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-489">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="0f29a-490">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="0f29a-490">Use Utf8JsonReader</span></span>

<span data-ttu-id="0f29a-491">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="0f29a-491">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="0f29a-492">上述程式碼假設 `jsonUtf8` 變數是一個位元組陣列，其中包含編碼為 utf-8 的有效 JSON。</span><span class="sxs-lookup"><span data-stu-id="0f29a-492">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="0f29a-493">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="0f29a-493">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="0f29a-494">下列範例示範如何同步讀取檔案，並搜尋值：</span><span class="sxs-lookup"><span data-stu-id="0f29a-494">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="0f29a-495">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="0f29a-495">The preceding code:</span></span>

* <span data-ttu-id="0f29a-496">假設 JSON 包含物件的陣列，而且每個物件都可以包含字串類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f29a-496">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="0f29a-497">計算以 "大學" 結尾的物件和 "name" 屬性值。</span><span class="sxs-lookup"><span data-stu-id="0f29a-497">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="0f29a-498">假設檔案是以 UTF-16 編碼，並將它轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="0f29a-498">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="0f29a-499">您可以 `ReadOnlySpan<byte>` 使用下列程式碼，將編碼為 utf-8 的檔案直接讀入中：</span><span class="sxs-lookup"><span data-stu-id="0f29a-499">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="0f29a-500">如果檔案包含 UTF-8 位元組順序標記 (BOM) ，請先將其移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器預期文字。</span><span class="sxs-lookup"><span data-stu-id="0f29a-500">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="0f29a-501">否則，會將 BOM 視為不正確 JSON，而讀取器會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-501">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="0f29a-502">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="0f29a-502">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="0f29a-503">產生的摘要訊息是「2個以上的名稱的結尾是 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="0f29a-503">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="0f29a-504">使用 Utf8JsonReader 從串流讀取</span><span class="sxs-lookup"><span data-stu-id="0f29a-504">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="0f29a-505">當讀取大型檔案 (gb 或更大的大小時，例如) ，您可能會想要避免必須一次將整個檔案載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="0f29a-505">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="0f29a-506">在此案例中，您可以使用 <xref:System.IO.FileStream> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-506">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="0f29a-507">使用 `Utf8JsonReader` 從資料流程讀取時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="0f29a-507">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="0f29a-508">包含部分 JSON 承載的緩衝區必須至少與它內最大的 JSON 權杖一樣大，讓讀取器可以進行向前的進度。</span><span class="sxs-lookup"><span data-stu-id="0f29a-508">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="0f29a-509">緩衝區至少必須和 JSON 內的最大泛空白字元順序一樣大。</span><span class="sxs-lookup"><span data-stu-id="0f29a-509">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="0f29a-510">讀取器不會追蹤已讀取的資料，直到它完全讀取 JSON 承載中的下一個 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-510">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="0f29a-511">因此，當緩衝區中有剩餘的位元組時，您必須再次將它們傳遞給讀取器。</span><span class="sxs-lookup"><span data-stu-id="0f29a-511">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="0f29a-512">您可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 來判斷剩餘的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f29a-512">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="0f29a-513">下列程式碼說明如何從資料流程讀取。</span><span class="sxs-lookup"><span data-stu-id="0f29a-513">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="0f29a-514">此範例會顯示 <xref:System.IO.MemoryStream> 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-514">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="0f29a-515">類似的程式碼可搭配使用 <xref:System.IO.FileStream> ，但在 `FileStream` 開始時包含 utf-8 BOM 時除外。</span><span class="sxs-lookup"><span data-stu-id="0f29a-515">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="0f29a-516">在這種情況下，您必須先從緩衝區中去除這三個位元組，再將剩餘的位元組傳遞給 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="0f29a-516">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="0f29a-517">否則，讀取器會擲回例外狀況，因為 BOM 不會被視為 JSON 的有效部分。</span><span class="sxs-lookup"><span data-stu-id="0f29a-517">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="0f29a-518">範例程式碼的開頭為 4 KB 的緩衝區，每次發現大小不夠大而無法容納完整的 JSON 權杖時，便會將緩衝區大小加倍，讓讀取器在 JSON 承載上進行向前處理。</span><span class="sxs-lookup"><span data-stu-id="0f29a-518">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="0f29a-519">只有當您設定非常小的初始緩衝區大小（例如10個位元組）時，程式碼片段中提供的 JSON 範例才會觸發緩衝區大小的增加。</span><span class="sxs-lookup"><span data-stu-id="0f29a-519">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="0f29a-520">如果您將初始緩衝區大小設定為10，則 `Console.WriteLine` 語句會說明緩衝區大小增加的原因和影響。</span><span class="sxs-lookup"><span data-stu-id="0f29a-520">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="0f29a-521">在 4 KB 的初始緩衝區大小中，會顯示整個範例 JSON `Console.WriteLine` ，而且永遠不需要增加緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="0f29a-521">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="0f29a-522">先前的範例不會對緩衝區所能成長的大小設定限制。</span><span class="sxs-lookup"><span data-stu-id="0f29a-522">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="0f29a-523">如果權杖大小太大，程式碼可能會失敗併發生 <xref:System.OutOfMemoryException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f29a-523">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="0f29a-524">如果 JSON 包含的權杖大約是 1 GB 或更大的大小，就會發生這種情況，因為 1 GB 的大小加倍會導致大小太大而無法放入 `int32` 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="0f29a-524">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0f29a-525">其他資源</span><span class="sxs-lookup"><span data-stu-id="0f29a-525">Additional resources</span></span>

* [<span data-ttu-id="0f29a-526">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="0f29a-526">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="0f29a-527">如何撰寫自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="0f29a-527">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="0f29a-528">如何遷移 Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="0f29a-528">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="0f29a-529">中的 DateTime 和 DateTimeOffset 支援 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="0f29a-529">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="0f29a-530">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="0f29a-530">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
