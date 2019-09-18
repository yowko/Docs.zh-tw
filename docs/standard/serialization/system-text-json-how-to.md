---
title: 如何序列化 JSON-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5c499e7a0abcbf141b6fc68f6eb9ec8983c0a7cf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054353"
---
# <a name="how-to-serialize-json-in-net"></a><span data-ttu-id="b8d97-102">如何在 .NET 中序列化 JSON</span><span class="sxs-lookup"><span data-stu-id="b8d97-102">How to serialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8d97-103">JSON 序列化檔集在結構中。</span><span class="sxs-lookup"><span data-stu-id="b8d97-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="b8d97-104">本文並未涵蓋所有案例。</span><span class="sxs-lookup"><span data-stu-id="b8d97-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="b8d97-105">如需詳細資訊，請檢查 GitHub 上 dotnet/corefx 存放庫中的[system.object 問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)，特別是標示為[Json 功能的](https://github.com/dotnet/corefx/labels/json-functionality-doc)檔。</span><span class="sxs-lookup"><span data-stu-id="b8d97-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="b8d97-106">本文說明如何使用命名空間， <xref:System.Text.Json>在 JavaScript 物件標記法（JSON）中進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="b8d97-107">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="b8d97-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="b8d97-108">命名空間</span><span class="sxs-lookup"><span data-stu-id="b8d97-108">Namespaces</span></span>

<span data-ttu-id="b8d97-109"><xref:System.Text.Json>命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="b8d97-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="b8d97-110"><xref:System.Text.Json.Serialization>命名空間包含用於高階案例的屬性和 api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="b8d97-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="b8d97-111">因此，本文中顯示的程式碼範例需要下列`using`其中一個或兩個指示詞：</span><span class="sxs-lookup"><span data-stu-id="b8d97-111">Therefore the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="b8d97-112">目前不支援<xref:System.Runtime.Serialization>命名空間中`System.Text.Json`的屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="b8d97-113">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="b8d97-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="b8d97-114">若要將 JSON 寫入字串，請使用泛型型別參數或泛型型別推斷呼叫[JsonSerializer。序列化](xref:System.Text.Json.JsonSerializer.Serialize*)：</span><span class="sxs-lookup"><span data-stu-id="b8d97-114">To write JSON to a string, call [JsonSerializer.Serialize](xref:System.Text.Json.JsonSerializer.Serialize*), using a generic type parameter or generic type inference:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="b8d97-115">以下是要序列化的範例型別，其中包含集合和嵌套的類別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-115">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

<span data-ttu-id="b8d97-116">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="b8d97-116">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="b8d97-117">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="b8d97-117">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="b8d97-118">的<xref:System.Text.Json.JsonSerializer.Serialize%2A>多載可讓您將<xref:System.IO.Stream>序列化為。</span><span class="sxs-lookup"><span data-stu-id="b8d97-118">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="b8d97-119">可以使用非同步版本`Stream`的多載。</span><span class="sxs-lookup"><span data-stu-id="b8d97-119">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="b8d97-120">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="b8d97-120">Serialize to UTF-8</span></span>

<span data-ttu-id="b8d97-121">呼叫[JsonSerializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*)：</span><span class="sxs-lookup"><span data-stu-id="b8d97-121">Call [JsonSerializer.SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*):</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="b8d97-122">或者， <xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用<xref:System.Text.Json.Utf8JsonWriter>接受的多載。</span><span class="sxs-lookup"><span data-stu-id="b8d97-122">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="b8d97-123">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約 5-10%。</span><span class="sxs-lookup"><span data-stu-id="b8d97-123">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="b8d97-124">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="b8d97-124">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="default-serialization-behavior"></a><span data-ttu-id="b8d97-125">預設序列化行為</span><span class="sxs-lookup"><span data-stu-id="b8d97-125">Default serialization behavior</span></span>

* <span data-ttu-id="b8d97-126">所有公用屬性都會序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-126">All public properties are serialized.</span></span> <span data-ttu-id="b8d97-127">您可以[指定要排除的屬性](#exclude-properties)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-127">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="b8d97-128">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)來進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="b8d97-128">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes  non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="b8d97-129">JSON 為縮減。</span><span class="sxs-lookup"><span data-stu-id="b8d97-129">JSON is minified.</span></span> <span data-ttu-id="b8d97-130">您可以選擇性地[列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-130">You can optionally [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="b8d97-131">JSON 名稱的大小寫符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="b8d97-131">Casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="b8d97-132">您可以[自訂 JSON 名稱大小寫](#customize-json-names)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-132">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="b8d97-133">偵測到[迴圈參考](https://github.com/dotnet/corefx/issues/38579)，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8d97-133">[Circular references](https://github.com/dotnet/corefx/issues/38579) are detected and exceptions thrown.</span></span>
* <span data-ttu-id="b8d97-134">欄位已排除。</span><span class="sxs-lookup"><span data-stu-id="b8d97-134">Fields are excluded.</span></span>

<span data-ttu-id="b8d97-135">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="b8d97-135">Supported types include:</span></span>

* <span data-ttu-id="b8d97-136">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="b8d97-136">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and boolean.</span></span>
* <span data-ttu-id="b8d97-137">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-137">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="b8d97-138">一維和不規則陣列（`ArrayName[][]`）。</span><span class="sxs-lookup"><span data-stu-id="b8d97-138">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="b8d97-139">`Dictionary<string,TValue>`其中`TValue`是`object` 、`JsonElement`或 POCO。</span><span class="sxs-lookup"><span data-stu-id="b8d97-139">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="b8d97-140">下列命名空間中的[集合類型](https://github.com/dotnet/corefx/issues/36643)：</span><span class="sxs-lookup"><span data-stu-id="b8d97-140">[Collection types](https://github.com/dotnet/corefx/issues/36643) from the following namespaces:</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="b8d97-141">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="b8d97-141">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="b8d97-142">若要從字串還原序列化，請呼叫[JsonSerializer。](xref:System.Text.Json.JsonSerializer.Deserialize*)還原序列化：</span><span class="sxs-lookup"><span data-stu-id="b8d97-142">To deserialize from a string, call [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*):</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="b8d97-143">如需範例，請參閱[序列化](#how-to-write-net-objects-to-json-serialize)一節。</span><span class="sxs-lookup"><span data-stu-id="b8d97-143">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="b8d97-144">JSON 和 .NET 物件相同，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="b8d97-144">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="b8d97-145">的<xref:System.Text.Json.JsonSerializer.Deserialize*>多載可讓您`Stream`從還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-145">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="b8d97-146">可以使用非同步版本`Stream`的多載。</span><span class="sxs-lookup"><span data-stu-id="b8d97-146">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="b8d97-147">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="b8d97-147">Deserialize from UTF-8</span></span>

<span data-ttu-id="b8d97-148">呼叫[JsonSerializer](xref:System.Text.Json.JsonSerializer.Deserialize*) `Utf8JsonReader`或使用或的`ReadOnlySpan<byte>`還原序列化多載：</span><span class="sxs-lookup"><span data-stu-id="b8d97-148">Call a [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*) overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`:</span></span>

```csharp
byte[] utf8Json = ... ;

var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json = ... ;

var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="default-deserialization-behavior"></a><span data-ttu-id="b8d97-149">預設還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="b8d97-149">Default deserialization behavior</span></span>

* <span data-ttu-id="b8d97-150">屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8d97-150">Property name matching is case-sensitive.</span></span> <span data-ttu-id="b8d97-151">您可以選擇性地指定不區分[大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-151">You can optionally specify [case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="b8d97-152">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8d97-152">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="b8d97-153">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="b8d97-153">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="b8d97-154">不支援還原序列化為[不可變的物件](https://github.com/dotnet/corefx/issues/38569)或[唯讀屬性](https://github.com/dotnet/corefx/issues/38163)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-154">Deserialization to [immutable objects](https://github.com/dotnet/corefx/issues/38569) or [read-only properties](https://github.com/dotnet/corefx/issues/38163) isn't supported.</span></span>
* <span data-ttu-id="b8d97-155">列舉是以數位的形式支援。</span><span class="sxs-lookup"><span data-stu-id="b8d97-155">Enums are supported as numbers.</span></span>
* <span data-ttu-id="b8d97-156">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="b8d97-156">Fields aren't supported.</span></span>
* <span data-ttu-id="b8d97-157">JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8d97-157">Comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="b8d97-158">您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-158">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="b8d97-159">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="b8d97-159">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="b8d97-160">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="b8d97-160">Serialize to formatted JSON</span></span>

<span data-ttu-id="b8d97-161">設定<xref:System.Text.Json.JsonSerializerOptions.WriteIndented>為 true：</span><span class="sxs-lookup"><span data-stu-id="b8d97-161">Set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-162">以下是要序列化的範例型別和 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="b8d97-162">Here's an example type to be serialized and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="b8d97-163">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="b8d97-163">Allow comments and trailing commas</span></span>

<span data-ttu-id="b8d97-164">將<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling>設定`JsonCommentHandling.Skip`為，並<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas>將設定為 true：</span><span class="sxs-lookup"><span data-stu-id="b8d97-164">Set <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> to `JsonCommentHandling.Skip`, and set <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="b8d97-165">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="b8d97-165">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="b8d97-166">自訂 JSON 名稱</span><span class="sxs-lookup"><span data-stu-id="b8d97-166">Customize JSON names</span></span>

<span data-ttu-id="b8d97-167">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="b8d97-167">This section explains how to:</span></span>

* <span data-ttu-id="b8d97-168">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="b8d97-168">Customize individual property names</span></span>
* <span data-ttu-id="b8d97-169">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="b8d97-169">Convert all property names to camel case</span></span>
* <span data-ttu-id="b8d97-170">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="b8d97-170">Implement a custom property naming policy</span></span>
* <span data-ttu-id="b8d97-171">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="b8d97-171">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="b8d97-172">不支援自動[將列舉轉換為 camel 案例](https://github.com/dotnet/corefx/issues/37725)。</span><span class="sxs-lookup"><span data-stu-id="b8d97-172">There's no support for automatically [converting enums to camel case](https://github.com/dotnet/corefx/issues/37725).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="b8d97-173">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="b8d97-173">Customize individual property names</span></span>

<span data-ttu-id="b8d97-174">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-174">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="b8d97-175">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-175">Here's an example type to serialize and resulting JSON:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="b8d97-176">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="b8d97-176">The property name set by this attribute:</span></span>

* <span data-ttu-id="b8d97-177">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-177">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="b8d97-178">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="b8d97-178">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="b8d97-179">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="b8d97-179">Use camel case for all JSON property names</span></span>

<span data-ttu-id="b8d97-180">設定<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>為`JsonNamingPolicy.CamelCase`：</span><span class="sxs-lookup"><span data-stu-id="b8d97-180">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-181">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-181">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="b8d97-182">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="b8d97-182">The camel case property naming policy:</span></span>

* <span data-ttu-id="b8d97-183">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-183">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="b8d97-184">會由`[JsonPropertyName]`屬性覆寫。</span><span class="sxs-lookup"><span data-stu-id="b8d97-184">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="b8d97-185">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="b8d97-185">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="b8d97-186">衍生自<xref:System.Text.Json.JsonNamingPolicy> ，並<xref:System.Text.Json.JsonNamingPolicy.ConvertName*>覆寫：</span><span class="sxs-lookup"><span data-stu-id="b8d97-186">Derive from <xref:System.Text.Json.JsonNamingPolicy> and override <xref:System.Text.Json.JsonNamingPolicy.ConvertName*>:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="b8d97-187">將<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="b8d97-187">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-188">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-188">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="b8d97-189">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="b8d97-189">The JSON property naming policy:</span></span>

* <span data-ttu-id="b8d97-190">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="b8d97-191">會由`[JsonPropertyName]`屬性覆寫。</span><span class="sxs-lookup"><span data-stu-id="b8d97-191">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="b8d97-192">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="b8d97-192">Camel case dictionary keys</span></span>

<span data-ttu-id="b8d97-193">如果要序列化之物件的屬性屬於型`Dictionary<string,Tvalue>`別，則`string`可以將索引鍵轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8d97-193">If a property of an object to be serialized is of type `Dictionary<string,Tvalue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="b8d97-194">若要這麼做， <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy>請`JsonNamingPolicy.CamelCase`將設定為：</span><span class="sxs-lookup"><span data-stu-id="b8d97-194">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-195">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="b8d97-195">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="b8d97-196">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-196">Property</span></span> |<span data-ttu-id="b8d97-197">值</span><span class="sxs-lookup"><span data-stu-id="b8d97-197">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="b8d97-198">Date</span><span class="sxs-lookup"><span data-stu-id="b8d97-198">Date</span></span>    | <span data-ttu-id="b8d97-199">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="b8d97-199">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="b8d97-200">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="b8d97-200">TemperatureC</span></span>| <span data-ttu-id="b8d97-201">25</span><span class="sxs-lookup"><span data-stu-id="b8d97-201">25</span></span> |
| <span data-ttu-id="b8d97-202">總結</span><span class="sxs-lookup"><span data-stu-id="b8d97-202">Summary</span></span>| <span data-ttu-id="b8d97-203">熱</span><span class="sxs-lookup"><span data-stu-id="b8d97-203">Hot</span></span>|
| <span data-ttu-id="b8d97-204">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="b8d97-204">TemperatureRanges</span></span> | <span data-ttu-id="b8d97-205">冷，20</span><span class="sxs-lookup"><span data-stu-id="b8d97-205">Cold, 20</span></span><br><span data-ttu-id="b8d97-206">熱門、40</span><span class="sxs-lookup"><span data-stu-id="b8d97-206">Hot, 40</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

<span data-ttu-id="b8d97-207">Camel 案例命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-207">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="b8d97-208">排除屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-208">Exclude properties</span></span>

<span data-ttu-id="b8d97-209">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="b8d97-209">This section explains how to exclude:</span></span>

* <span data-ttu-id="b8d97-210">個別屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-210">Individual properties</span></span>
* <span data-ttu-id="b8d97-211">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-211">All read-only properties</span></span>
* <span data-ttu-id="b8d97-212">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-212">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="b8d97-213">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-213">Exclude individual properties</span></span>

<span data-ttu-id="b8d97-214">使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-214">Use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="b8d97-215">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-215">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="b8d97-216">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-216">Exclude all read-only properties</span></span>

<span data-ttu-id="b8d97-217">設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties>為 true：</span><span class="sxs-lookup"><span data-stu-id="b8d97-217">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-218">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="b8d97-218">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="b8d97-219">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-219">This option applies only to serialization.</span></span> <span data-ttu-id="b8d97-220">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-220">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="b8d97-221">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="b8d97-221">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="b8d97-222">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-222">Exclude all null value properties</span></span>

<span data-ttu-id="b8d97-223">設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>為 true：</span><span class="sxs-lookup"><span data-stu-id="b8d97-223">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="b8d97-224">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="b8d97-224">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="b8d97-225">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-225">Property</span></span> |<span data-ttu-id="b8d97-226">值</span><span class="sxs-lookup"><span data-stu-id="b8d97-226">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="b8d97-227">Date</span><span class="sxs-lookup"><span data-stu-id="b8d97-227">Date</span></span>    | <span data-ttu-id="b8d97-228">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="b8d97-228">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="b8d97-229">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="b8d97-229">TemperatureC</span></span>| <span data-ttu-id="b8d97-230">25</span><span class="sxs-lookup"><span data-stu-id="b8d97-230">25</span></span> |
| <span data-ttu-id="b8d97-231">總結</span><span class="sxs-lookup"><span data-stu-id="b8d97-231">Summary</span></span>| <span data-ttu-id="b8d97-232">null</span><span class="sxs-lookup"><span data-stu-id="b8d97-232">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="b8d97-233">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-233">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="b8d97-234">在還原序列化期間，JSON 中的 null 值只有在有效的情況下才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b8d97-234">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="b8d97-235">[不可為 null 的實數值型別的 Null 值會造成例外](https://github.com/dotnet/corefx/issues/40922)狀況。</span><span class="sxs-lookup"><span data-stu-id="b8d97-235">[Null values for non-nullable value types cause exceptions](https://github.com/dotnet/corefx/issues/40922).</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="b8d97-236">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="b8d97-236">Case-insensitive property matching</span></span>

<span data-ttu-id="b8d97-237">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="b8d97-237">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="b8d97-238">若要變更該行為， <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive>請將設定為 true：</span><span class="sxs-lookup"><span data-stu-id="b8d97-238">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="b8d97-239">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="b8d97-239">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="b8d97-240">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="b8d97-240">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="b8d97-241">包含衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-241">Include properties of derived classes</span></span>

<span data-ttu-id="b8d97-242">當您在編譯時期指定要序列化的型別時，不支援多型序列化。</span><span class="sxs-lookup"><span data-stu-id="b8d97-242">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="b8d97-243">例如，假設您有一個`WeatherForecast`類別和一個衍生的類別： `WeatherForecastWithWind`</span><span class="sxs-lookup"><span data-stu-id="b8d97-243">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

<span data-ttu-id="b8d97-244">而且假設在編譯時期傳遞給或推斷`Serialize`的型別為： `WeatherForecast`</span><span class="sxs-lookup"><span data-stu-id="b8d97-244">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="b8d97-245">在此案例中， `WindSpeed`即使`weatherForecast`物件實際上`WeatherForecastWithWind`是物件，也不會序列化屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-245">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="b8d97-246">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="b8d97-246">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="b8d97-247">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="b8d97-247">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="b8d97-248">若要序列化衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="b8d97-248">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="b8d97-249">`Serialize`呼叫的多載，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="b8d97-249">Call an overload of `Serialize` that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="b8d97-250">宣告要序列化為`object`的物件。</span><span class="sxs-lookup"><span data-stu-id="b8d97-250">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="b8d97-251">在上述範例案例中，這兩種方法`WindSpeed`都會使屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="b8d97-251">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="b8d97-252">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="b8d97-252">Handle overflow JSON</span></span>

<span data-ttu-id="b8d97-253">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="b8d97-253">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="b8d97-254">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="b8d97-254">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="b8d97-255">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="b8d97-255">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

<span data-ttu-id="b8d97-256">如果您將顯示的 JSON 還原序列化為所顯示的`DatesAvailable`類型`SummaryWords` ，和屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="b8d97-256">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="b8d97-257">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至類型`Dictionary<string,object>`的`Dictionary<string,JsonElement>`屬性或：</span><span class="sxs-lookup"><span data-stu-id="b8d97-257">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

<span data-ttu-id="b8d97-258">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成`ExtensionData`屬性的索引鍵/值組：</span><span class="sxs-lookup"><span data-stu-id="b8d97-258">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="b8d97-259">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d97-259">Property</span></span> |<span data-ttu-id="b8d97-260">值</span><span class="sxs-lookup"><span data-stu-id="b8d97-260">Value</span></span>  |<span data-ttu-id="b8d97-261">注意</span><span class="sxs-lookup"><span data-stu-id="b8d97-261">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="b8d97-262">Date</span><span class="sxs-lookup"><span data-stu-id="b8d97-262">Date</span></span>    | <span data-ttu-id="b8d97-263">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="b8d97-263">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="b8d97-264">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="b8d97-264">TemperatureC</span></span>| <span data-ttu-id="b8d97-265">0</span><span class="sxs-lookup"><span data-stu-id="b8d97-265">0</span></span> | <span data-ttu-id="b8d97-266">區分大小寫不相符`temperatureC` （在 JSON 中），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d97-266">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="b8d97-267">總結</span><span class="sxs-lookup"><span data-stu-id="b8d97-267">Summary</span></span> | <span data-ttu-id="b8d97-268">熱</span><span class="sxs-lookup"><span data-stu-id="b8d97-268">Hot</span></span> ||
| <span data-ttu-id="b8d97-269">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="b8d97-269">ExtensionData</span></span> | <span data-ttu-id="b8d97-270">temperatureC:25</span><span class="sxs-lookup"><span data-stu-id="b8d97-270">temperatureC: 25</span></span> |<span data-ttu-id="b8d97-271">因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="b8d97-271">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="b8d97-272">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="b8d97-272">DatesAvailable:</span></span><br>  <span data-ttu-id="b8d97-273">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="b8d97-273">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="b8d97-274">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="b8d97-274">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="b8d97-275">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="b8d97-275">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="b8d97-276">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="b8d97-276">SummaryWords:</span></span><br><span data-ttu-id="b8d97-277">酷</span><span class="sxs-lookup"><span data-stu-id="b8d97-277">Cool</span></span><br><span data-ttu-id="b8d97-278">風大</span><span class="sxs-lookup"><span data-stu-id="b8d97-278">Windy</span></span><br><span data-ttu-id="b8d97-279">潮濕</span><span class="sxs-lookup"><span data-stu-id="b8d97-279">Humid</span></span> |<span data-ttu-id="b8d97-280">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="b8d97-280">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="b8d97-281">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="b8d97-281">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

<span data-ttu-id="b8d97-282">請注意， `ExtensionData`屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="b8d97-282">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="b8d97-283">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="b8d97-283">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="b8d97-284">直接使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="b8d97-284">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="b8d97-285">下列範例顯示如何直接使用<xref:System.Text.Json.Utf8JsonWriter>類別。</span><span class="sxs-lookup"><span data-stu-id="b8d97-285">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="b8d97-286">直接使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="b8d97-286">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="b8d97-287">下列範例顯示如何直接使用<xref:System.Text.Json.Utf8JsonReader>類別。</span><span class="sxs-lookup"><span data-stu-id="b8d97-287">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="b8d97-288">此程式`jsonUtf8`代碼假設變數是包含有效 JSON 的位元組陣列，並以 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="b8d97-288">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, isFinalBlock: true, state: default);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

## <a name="additional-resources"></a><span data-ttu-id="b8d97-289">其他資源</span><span class="sxs-lookup"><span data-stu-id="b8d97-289">Additional resources</span></span>

* [<span data-ttu-id="b8d97-290">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="b8d97-290">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="b8d97-291">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="b8d97-291">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="b8d97-292">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="b8d97-292">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
