---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: 瞭解如何 System.Text.Json 在 .net 中使用命名空間進行序列化，並從 JSON 還原序列化。 包含範例程式碼。
ms.date: 01/04/2021
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
ms.openlocfilehash: bd257cf8d79ea2afa209fe71ad7eff969a62d6b2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938711"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="ebd12-104">如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON</span><span class="sxs-lookup"><span data-stu-id="ebd12-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="ebd12-105">本文說明如何使用 <xref:System.Text.Json?displayProperty=fullName> 命名空間，從 JavaScript 物件標記法 (JSON) 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ebd12-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ebd12-106">如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="ebd12-107">指示和範例程式碼會直接使用程式庫，而不是透過 [ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="ebd12-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="ebd12-108">大部分的序列化程式碼範例會將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為「 `true` 美觀」的 JSON (，以縮排和空白字元來取得可讀性) 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="ebd12-109">針對生產用途，您通常會接受此設定的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="ebd12-110">程式碼範例參考下列類別和它的變異：</span><span class="sxs-lookup"><span data-stu-id="ebd12-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

> [!NOTE]
> <span data-ttu-id="ebd12-111">System.Text.Json 使用 Visual Basic 不支援的 [ref 結構](../../csharp/language-reference/builtin-types/struct.md#ref-struct)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-111">System.Text.Json uses [ref structs](../../csharp/language-reference/builtin-types/struct.md#ref-struct), which are not supported by Visual Basic.</span></span> <span data-ttu-id="ebd12-112">如果您嘗試搭配 System.Text.Json Visual Basic 使用 api，您會收到 BC40000 的編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebd12-112">If you try to use System.Text.Json APIs with Visual Basic, you get BC40000 compile errors.</span></span> <span data-ttu-id="ebd12-113">此錯誤訊息表示問題是已淘汰的 API，但實際的問題在於 `ref struct` 編譯器中缺乏支援。</span><span class="sxs-lookup"><span data-stu-id="ebd12-113">The error message indicates that the problem is an obsolete API, but the actual issue is lack of `ref struct` support in the compiler.</span></span>

## <a name="namespaces"></a><span data-ttu-id="ebd12-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="ebd12-114">Namespaces</span></span>

<span data-ttu-id="ebd12-115"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="ebd12-115">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="ebd12-116"><xref:System.Text.Json.Serialization>命名空間包含適用于進行序列化和還原序列化的 advanced 案例和自訂的屬性和 api。</span><span class="sxs-lookup"><span data-stu-id="ebd12-116">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="ebd12-117">本文中顯示的程式碼範例需要 `using` 下列其中一個或兩個命名空間的指示詞：</span><span class="sxs-lookup"><span data-stu-id="ebd12-117">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="ebd12-118"><xref:System.Runtime.Serialization>不支援命名空間中的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-118">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="ebd12-119">如何將 .NET 物件撰寫為 JSON (序列化) </span><span class="sxs-lookup"><span data-stu-id="ebd12-119">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="ebd12-120">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ebd12-120">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ebd12-121">下列範例會以字串形式建立 JSON：</span><span class="sxs-lookup"><span data-stu-id="ebd12-121">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="ebd12-122">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="ebd12-122">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="ebd12-123">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="ebd12-123">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="ebd12-124">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ebd12-124">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="ebd12-125">的多載 `Serialize()` 會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="ebd12-125">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="ebd12-126">序列化範例</span><span class="sxs-lookup"><span data-stu-id="ebd12-126">Serialization example</span></span>

<span data-ttu-id="ebd12-127">以下是包含集合類型屬性和使用者定義型別的範例類別：</span><span class="sxs-lookup"><span data-stu-id="ebd12-127">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="ebd12-128">"POCO" 代表 [純舊的 CLR 物件](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-128">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="ebd12-129">POCO 是一種 .NET 型別，其不相依于任何架構特定的類型，例如透過繼承或屬性。</span><span class="sxs-lookup"><span data-stu-id="ebd12-129">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="ebd12-130">序列化上述型別的實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ebd12-130">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="ebd12-131">JSON 輸出為縮減 (空白字元、縮排和換行字元預設會) 移除：</span><span class="sxs-lookup"><span data-stu-id="ebd12-131">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="ebd12-132">下列範例會顯示相同的 JSON，但格式化的 (也就是具有空白字元和縮排) 的整齊列印：</span><span class="sxs-lookup"><span data-stu-id="ebd12-132">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="ebd12-133">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="ebd12-133">Serialize to UTF-8</span></span>

<span data-ttu-id="ebd12-134">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="ebd12-134">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="ebd12-135"><xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用採用的多載 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-135">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="ebd12-136">使用以字串為基礎的方法，序列化為 UTF-8 的速度大約是5-10%。</span><span class="sxs-lookup"><span data-stu-id="ebd12-136">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="ebd12-137">差異是因為 (為 UTF-8 的位元組) 不需要轉換成字串 (UTF-16) 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-137">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="ebd12-138">序列化行為</span><span class="sxs-lookup"><span data-stu-id="ebd12-138">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ebd12-139">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ebd12-139">By default, all public properties are serialized.</span></span> <span data-ttu-id="ebd12-140">您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-140">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="ebd12-141">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="ebd12-141">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ebd12-142">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="ebd12-142">By default, JSON is minified.</span></span> <span data-ttu-id="ebd12-143">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-143">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ebd12-144">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ebd12-144">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ebd12-145">您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-145">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="ebd12-146">依預設，會偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-146">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="ebd12-147">您可以 [保留參考並處理迴圈參考](system-text-json-preserve-references.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-147">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="ebd12-148">依預設，會忽略 [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-148">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="ebd12-149">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-149">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="ebd12-150">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="ebd12-150">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ebd12-151">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-151">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ebd12-152">依預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ebd12-152">By default, all public properties are serialized.</span></span> <span data-ttu-id="ebd12-153">您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-153">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="ebd12-154">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="ebd12-154">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ebd12-155">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="ebd12-155">By default, JSON is minified.</span></span> <span data-ttu-id="ebd12-156">您可以 [整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-156">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ebd12-157">根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ebd12-157">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ebd12-158">您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-158">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="ebd12-159">偵測到迴圈參考並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-159">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="ebd12-160">[欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ebd12-160">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="ebd12-161">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="ebd12-161">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ebd12-162">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="ebd12-162">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="ebd12-163">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="ebd12-163">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="ebd12-164">一維和不規則陣列 (`T[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-164">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="ebd12-165">下列命名空間中的集合和字典。</span><span class="sxs-lookup"><span data-stu-id="ebd12-165">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ebd12-166">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="ebd12-166">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="ebd12-167">[ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="ebd12-167">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="ebd12-168">一維和不規則陣列 (`ArrayName[][]`) 。</span><span class="sxs-lookup"><span data-stu-id="ebd12-168">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="ebd12-169">`Dictionary<string,TValue>` 其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="ebd12-169">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="ebd12-170">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="ebd12-170">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="ebd12-171">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) 來處理其他類型，或是提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="ebd12-171">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="ebd12-172">如何將 JSON 讀取為 .NET 物件 (還原序列化) </span><span class="sxs-lookup"><span data-stu-id="ebd12-172">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="ebd12-173">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ebd12-173">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ebd12-174">下列範例會從字串讀取 JSON，並 `WeatherForecastWithPOCOs` 為 [序列化範例](#serialization-example)建立稍早所示類別的實例：</span><span class="sxs-lookup"><span data-stu-id="ebd12-174">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="ebd12-175">若要使用同步程式碼從檔案還原序列化，請將檔案讀入字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ebd12-175">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="ebd12-176">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="ebd12-176">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

> [!TIP]
> <span data-ttu-id="ebd12-177">如果您有想要還原序列化的 JSON，而且沒有將它還原序列化的類別，Visual Studio 2019 會自動產生您需要的類別：</span><span class="sxs-lookup"><span data-stu-id="ebd12-177">If you have JSON that you want to deserialize, and you don't have the class to deserialize it into, Visual Studio 2019 can automatically generate the class you need:</span></span>
>
> 1. <span data-ttu-id="ebd12-178">複製您需要還原序列化的 JSON。</span><span class="sxs-lookup"><span data-stu-id="ebd12-178">Copy the JSON that you need to deserialize.</span></span>
> 1. <span data-ttu-id="ebd12-179">建立類別檔案並刪除範本程式碼。</span><span class="sxs-lookup"><span data-stu-id="ebd12-179">Create a class file and delete the template code.</span></span>
> 1. <span data-ttu-id="ebd12-180">選擇 [**編輯** 貼上]  >  **特殊**  >  **貼上 JSON 做為類別**。</span><span class="sxs-lookup"><span data-stu-id="ebd12-180">Choose **Edit** > **Paste Special** > **Paste JSON as Classes**.</span></span>
>
> <span data-ttu-id="ebd12-181">結果是可用於還原序列化目標的類別。</span><span class="sxs-lookup"><span data-stu-id="ebd12-181">The result is a class that you can use for your deserialization target.</span></span>

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="ebd12-182">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="ebd12-182">Deserialize from UTF-8</span></span>

<span data-ttu-id="ebd12-183">若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `ReadOnlySpan<byte>` 或的多載， `Utf8JsonReader` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ebd12-183">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="ebd12-184">這些範例假設 JSON 是在名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="ebd12-184">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="ebd12-185">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="ebd12-185">Deserialization behavior</span></span>

<span data-ttu-id="ebd12-186">將 JSON 還原序列化時，會套用下列行為：</span><span class="sxs-lookup"><span data-stu-id="ebd12-186">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ebd12-187">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ebd12-187">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="ebd12-188">您可以 [指定不區分大小寫](system-text-json-character-casing.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-188">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="ebd12-189">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-189">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ebd12-190">序列化程式會忽略非公用的函式。</span><span class="sxs-lookup"><span data-stu-id="ebd12-190">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="ebd12-191">支援還原序列化至不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="ebd12-191">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="ebd12-192">請參閱 [不可變的類型和記錄](system-text-json-immutability.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-192">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="ebd12-193">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="ebd12-193">By default, enums are supported as numbers.</span></span> <span data-ttu-id="ebd12-194">您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-194">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="ebd12-195">依預設，會忽略欄位。</span><span class="sxs-lookup"><span data-stu-id="ebd12-195">By default, fields are ignored.</span></span> <span data-ttu-id="ebd12-196">您可以 [包含欄位](#include-fields)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-196">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="ebd12-197">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-197">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ebd12-198">您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-198">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="ebd12-199">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="ebd12-199">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="ebd12-200">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="ebd12-200">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ebd12-201">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-201">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ebd12-202">依預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ebd12-202">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="ebd12-203">您可以 [指定不區分大小寫](system-text-json-character-casing.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-203">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="ebd12-204">ASP.NET Core apps [預設會指定不區分大小寫](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-204">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="ebd12-205">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-205">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ebd12-206">無參數的函式（可以是公用、內部或私用）用於還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ebd12-206">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="ebd12-207">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="ebd12-207">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="ebd12-208">依預設，會將列舉支援為數字。</span><span class="sxs-lookup"><span data-stu-id="ebd12-208">By default, enums are supported as numbers.</span></span> <span data-ttu-id="ebd12-209">您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-209">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="ebd12-210">不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="ebd12-210">Fields aren't supported.</span></span>
* <span data-ttu-id="ebd12-211">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebd12-211">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ebd12-212">您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-212">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="ebd12-213">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="ebd12-213">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="ebd12-214">當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。</span><span class="sxs-lookup"><span data-stu-id="ebd12-214">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ebd12-215">如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-215">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="ebd12-216">您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) ，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="ebd12-216">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="ebd12-217">序列化為格式化的 JSON</span><span class="sxs-lookup"><span data-stu-id="ebd12-217">Serialize to formatted JSON</span></span>

<span data-ttu-id="ebd12-218">若要整齊列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="ebd12-218">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="ebd12-219">以下是要序列化的範例型別，以及整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="ebd12-219">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="ebd12-220">如果您 `JsonSerializerOptions` 重複使用相同的選項，請勿 `JsonSerializerOptions` 在每次使用時建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="ebd12-220">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="ebd12-221">每次呼叫時重複使用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="ebd12-221">Reuse the same instance for every call.</span></span> <span data-ttu-id="ebd12-222">如需詳細資訊，請參閱 [重複使用 JsonSerializerOptions 實例](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-222">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="ebd12-223">包含欄位</span><span class="sxs-lookup"><span data-stu-id="ebd12-223">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="ebd12-224"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>當序列化或還原序列化時，請使用全域設定或[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)屬性來包含欄位，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ebd12-224">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="ebd12-225">若要忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。</span><span class="sxs-lookup"><span data-stu-id="ebd12-225">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="ebd12-226">System.Text.Json在 .Net Core 3.1 中不支援欄位。</span><span class="sxs-lookup"><span data-stu-id="ebd12-226">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="ebd12-227">[自訂轉換器](system-text-json-converters-how-to.md) 可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="ebd12-227">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="ebd12-228">HttpClient 和 HttpContent 擴充方法</span><span class="sxs-lookup"><span data-stu-id="ebd12-228">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="ebd12-229">從網路序列化和還原序列化 JSON 承載是常見的作業。</span><span class="sxs-lookup"><span data-stu-id="ebd12-229">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="ebd12-230">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions)和[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)上的擴充方法可讓您在一行程式碼中進行這些作業。</span><span class="sxs-lookup"><span data-stu-id="ebd12-230">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="ebd12-231">這些擴充方法會使用 [web 預設值進行 JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。</span><span class="sxs-lookup"><span data-stu-id="ebd12-231">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="ebd12-232">下列範例說明如何使用 <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="ebd12-232">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="ebd12-233">此外，也有適用 System.Text.Json 于 [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="ebd12-233">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="ebd12-234">和上的擴充方法在 `HttpClient` `HttpContent` System.Text.Json .net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="ebd12-234">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="ebd12-235">請參閱</span><span class="sxs-lookup"><span data-stu-id="ebd12-235">See also</span></span>

* [<span data-ttu-id="ebd12-236">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="ebd12-236">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ebd12-237">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="ebd12-237">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ebd12-238">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="ebd12-238">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ebd12-239">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="ebd12-239">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="ebd12-240">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="ebd12-240">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ebd12-241">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="ebd12-241">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ebd12-242">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="ebd12-242">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="ebd12-243">保留參考</span><span class="sxs-lookup"><span data-stu-id="ebd12-243">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ebd12-244">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="ebd12-244">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="ebd12-245">多型序列化</span><span class="sxs-lookup"><span data-stu-id="ebd12-245">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="ebd12-246">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ebd12-246">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="ebd12-247">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="ebd12-247">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="ebd12-248">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="ebd12-248">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="ebd12-249">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="ebd12-249">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="ebd12-250">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="ebd12-250">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="ebd12-251">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ebd12-251">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="ebd12-252">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="ebd12-252">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
