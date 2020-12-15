---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: 瞭解如何 System.Text.Json 在 .net 中使用命名空間進行序列化，並從 JSON 還原序列化。 包含範例程式碼。
ms.date: 12/02/2020
ms.custom: contperf-fy21q2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 46203aa1b4daa4281c7c26191f7df947967fa1c0
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513259"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="6b588-104">如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON</span><span class="sxs-lookup"><span data-stu-id="6b588-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="6b588-105">本文說明如何使用 <xref:System.Text.Json?displayProperty=fullName> 命名空間，從 JavaScript 物件標記法 (JSON) 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="6b588-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="6b588-106">如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="6b588-107">指示和範例程式碼會直接使用程式庫，而不是透過 [ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="6b588-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="6b588-108">大部分的序列化程式碼範例會將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為「 `true` 美觀」的 JSON (，以縮排和空白字元來取得可讀性) 。</span><span class="sxs-lookup"><span data-stu-id="6b588-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="6b588-109">針對生產用途，您通常會接受此設定的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6b588-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="6b588-110">程式碼範例參考下列類別和它的變異：</span><span class="sxs-lookup"><span data-stu-id="6b588-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a><span data-ttu-id="6b588-111">命名空間</span><span class="sxs-lookup"><span data-stu-id="6b588-111">Namespaces</span></span>

<span data-ttu-id="6b588-112"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="6b588-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="6b588-113"><xref:System.Text.Json.Serialization>命名空間包含適用于進行序列化和還原序列化的 advanced 案例和自訂的屬性和 api。</span><span class="sxs-lookup"><span data-stu-id="6b588-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="6b588-114">本文中顯示的程式碼範例需要 `using` 下列其中一個或兩個命名空間的指示詞：</span><span class="sxs-lookup"><span data-stu-id="6b588-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="6b588-115"><xref:System.Runtime.Serialization>不支援命名空間中的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="6b588-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="6b588-116">如何將 .NET 物件撰寫為 JSON (序列化) </span><span class="sxs-lookup"><span data-stu-id="6b588-116">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="6b588-117">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b588-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6b588-118">下列範例會以字串形式建立 JSON：</span><span class="sxs-lookup"><span data-stu-id="6b588-118">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="6b588-119">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="6b588-119">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="6b588-120">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="6b588-120">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="6b588-121">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="6b588-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="6b588-122">的多載 `Serialize()` 會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="6b588-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="6b588-123">序列化範例</span><span class="sxs-lookup"><span data-stu-id="6b588-123">Serialization example</span></span>

<span data-ttu-id="6b588-124">以下是包含集合類型屬性和使用者定義型別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="6b588-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="6b588-125">"POCO" 代表 [純舊的 CLR 物件](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="6b588-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="6b588-126">POCO 是一種 .NET 型別，其不相依于任何架構特定的類型，例如透過繼承或屬性。</span><span class="sxs-lookup"><span data-stu-id="6b588-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="6b588-127">序列化上述型別的實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6b588-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="6b588-128">JSON 輸出為縮減 (空白字元、縮排和換行字元預設會) 移除：</span><span class="sxs-lookup"><span data-stu-id="6b588-128">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="6b588-129">下列範例會顯示相同的 JSON，但格式化的 (也就是具有空白字元和縮排) 的整齊列印：</span><span class="sxs-lookup"><span data-stu-id="6b588-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="6b588-130">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="6b588-130">Serialize to UTF-8</span></span>

<span data-ttu-id="6b588-131">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="6b588-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="6b588-132"><xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用採用的多載 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="6b588-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="6b588-133">使用以字串為基礎的方法，序列化為 UTF-8 的速度大約是5-10%。</span><span class="sxs-lookup"><span data-stu-id="6b588-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="6b588-134">差異是因為 (為 UTF-8 的位元組) 不需要轉換成字串 (UTF-16) 。</span><span class="sxs-lookup"><span data-stu-id="6b588-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="6b588-135">序列化行為</span><span class="sxs-lookup"><span data-stu-id="6b588-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6b588-136">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="6b588-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="6b588-137">您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-137">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="6b588-138">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="6b588-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="6b588-139">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="6b588-139">By default, JSON is minified.</span></span> <span data-ttu-id="6b588-140">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="6b588-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="6b588-141">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6b588-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="6b588-142">您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-142">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="6b588-143">依預設，會偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="6b588-144">您可以 [保留參考並處理迴圈參考](system-text-json-preserve-references.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-144">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="6b588-145">依預設，會忽略 [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 。</span><span class="sxs-lookup"><span data-stu-id="6b588-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="6b588-146">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="6b588-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="6b588-147">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="6b588-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6b588-148">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="6b588-148">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6b588-149">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="6b588-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="6b588-150">您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-150">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="6b588-151">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="6b588-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="6b588-152">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="6b588-152">By default, JSON is minified.</span></span> <span data-ttu-id="6b588-153">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="6b588-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="6b588-154">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6b588-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="6b588-155">您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-155">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="6b588-156">偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="6b588-157">[欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6b588-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="6b588-158">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="6b588-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6b588-159">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="6b588-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="6b588-160">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="6b588-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="6b588-161">一維和不規則陣列 (`T[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="6b588-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="6b588-162">下列命名空間中的集合和字典。</span><span class="sxs-lookup"><span data-stu-id="6b588-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6b588-163">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="6b588-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="6b588-164">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="6b588-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="6b588-165">一維和不規則陣列 (`ArrayName[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="6b588-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="6b588-166">`Dictionary<string,TValue>` 其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="6b588-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="6b588-167">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="6b588-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="6b588-168">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) 來處理其他類型，或是提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="6b588-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="6b588-169">如何將 JSON 讀取為 .NET 物件 (還原序列化) </span><span class="sxs-lookup"><span data-stu-id="6b588-169">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="6b588-170">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b588-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6b588-171">下列範例會從字串讀取 JSON，並 `WeatherForecastWithPOCOs` 為 [序列化範例](#serialization-example)建立稍早所示類別的實例：</span><span class="sxs-lookup"><span data-stu-id="6b588-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="6b588-172">若要使用同步程式碼從檔案還原序列化，請將檔案讀入字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6b588-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="6b588-173">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="6b588-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="6b588-174">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="6b588-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="6b588-175">若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `ReadOnlySpan<byte>` 或的多載， `Utf8JsonReader` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6b588-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="6b588-176">這些範例假設 JSON 是在名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="6b588-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="6b588-177">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="6b588-177">Deserialization behavior</span></span>

<span data-ttu-id="6b588-178">將 JSON 還原序列化時，會套用下列行為：</span><span class="sxs-lookup"><span data-stu-id="6b588-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6b588-179">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6b588-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="6b588-180">您可以 [指定不區分大小寫](system-text-json-character-casing.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-180">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="6b588-181">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="6b588-182">序列化程式會忽略非公用的函式。</span><span class="sxs-lookup"><span data-stu-id="6b588-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="6b588-183">支援還原序列化至不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="6b588-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="6b588-184">請參閱 [不可變的類型和記錄](system-text-json-immutability.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-184">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="6b588-185">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="6b588-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="6b588-186">您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="6b588-186">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="6b588-187">依預設，會忽略欄位。</span><span class="sxs-lookup"><span data-stu-id="6b588-187">By default, fields are ignored.</span></span> <span data-ttu-id="6b588-188">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="6b588-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="6b588-189">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="6b588-190">您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-190">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="6b588-191">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="6b588-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="6b588-192">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="6b588-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6b588-193">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="6b588-193">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6b588-194">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6b588-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="6b588-195">您可以 [指定不區分大小寫](system-text-json-character-casing.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-195">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="6b588-196">ASP.NET Core apps [預設會指定不區分大小寫](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="6b588-196">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="6b588-197">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="6b588-198">無參數的函式（可以是公用、內部或私用）用於還原序列化。</span><span class="sxs-lookup"><span data-stu-id="6b588-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="6b588-199">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="6b588-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="6b588-200">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="6b588-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="6b588-201">您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="6b588-201">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="6b588-202">不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="6b588-202">Fields aren't supported.</span></span>
* <span data-ttu-id="6b588-203">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b588-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="6b588-204">您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-204">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="6b588-205">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="6b588-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="6b588-206">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="6b588-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6b588-207">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="6b588-207">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="6b588-208">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) ，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="6b588-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="6b588-209">序列化為格式化的 JSON</span><span class="sxs-lookup"><span data-stu-id="6b588-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="6b588-210">若要整齊列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="6b588-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="6b588-211">以下是要序列化的範例型別，以及整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="6b588-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="6b588-212">如果您 `JsonSerializerOptions` 重複使用相同的選項，請勿 `JsonSerializerOptions` 在每次使用時建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="6b588-212">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="6b588-213">每次呼叫時重複使用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="6b588-213">Reuse the same instance for every call.</span></span> <span data-ttu-id="6b588-214">如需詳細資訊，請參閱 [重複使用 JsonSerializerOptions 實例](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)。</span><span class="sxs-lookup"><span data-stu-id="6b588-214">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="6b588-215">包含欄位</span><span class="sxs-lookup"><span data-stu-id="6b588-215">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6b588-216"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>當序列化或還原序列化時，請使用全域設定或[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)屬性來包含欄位，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6b588-216">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="6b588-217">若要忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。</span><span class="sxs-lookup"><span data-stu-id="6b588-217">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6b588-218">System.Text.Json在 .Net Core 3.1 中不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="6b588-218">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="6b588-219">[自訂轉換器](system-text-json-converters-how-to.md) 可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="6b588-219">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="6b588-220">HttpClient 和 HttpContent 擴充方法</span><span class="sxs-lookup"><span data-stu-id="6b588-220">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="6b588-221">從網路序列化和還原序列化 JSON 承載是常見的作業。</span><span class="sxs-lookup"><span data-stu-id="6b588-221">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="6b588-222">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions)和[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)上的擴充方法可讓您在一行程式碼中進行這些作業。</span><span class="sxs-lookup"><span data-stu-id="6b588-222">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="6b588-223">這些擴充方法會使用 [web 預設值進行 JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="6b588-223">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="6b588-224">下列範例說明如何使用 <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="6b588-224">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="6b588-225">此外，也有適用 System.Text.Json 于 [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6b588-225">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6b588-226">和上的擴充方法在 `HttpClient` `HttpContent` System.Text.Json .net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="6b588-226">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="6b588-227">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b588-227">See also</span></span>

* [<span data-ttu-id="6b588-228">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="6b588-228">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="6b588-229">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="6b588-229">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="6b588-230">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="6b588-230">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="6b588-231">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="6b588-231">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="6b588-232">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="6b588-232">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="6b588-233">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="6b588-233">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="6b588-234">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="6b588-234">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="6b588-235">保留參考</span><span class="sxs-lookup"><span data-stu-id="6b588-235">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="6b588-236">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="6b588-236">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="6b588-237">多型序列化</span><span class="sxs-lookup"><span data-stu-id="6b588-237">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="6b588-238">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="6b588-238">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="6b588-239">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="6b588-239">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="6b588-240">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="6b588-240">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="6b588-241">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="6b588-241">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="6b588-242">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="6b588-242">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="6b588-243">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6b588-243">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="6b588-244">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="6b588-244">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
