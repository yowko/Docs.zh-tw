---
title: 如何使用C# -.net 序列化和還原序列化 JSON
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 22c2fd5fc5eaf7a5dc9b71a7335b0b844fa92b51
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291611"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="fa4d4-102">如何在 .NET 中序列化和還原序列化 JSON</span><span class="sxs-lookup"><span data-stu-id="fa4d4-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa4d4-103">JSON 序列化檔集在結構中。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="fa4d4-104">本文並未涵蓋所有案例。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="fa4d4-105">如需詳細資訊，請檢查 GitHub 上 dotnet/corefx 存放庫中的[system.object 問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)，特別是標示為[Json 功能的](https://github.com/dotnet/corefx/labels/json-functionality-doc)檔。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="fa4d4-106">本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="fa4d4-107">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="fa4d4-108">命名空間</span><span class="sxs-lookup"><span data-stu-id="fa4d4-108">Namespaces</span></span>

<span data-ttu-id="fa4d4-109">@No__t-0 命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="fa4d4-110">@No__t-0 命名空間包含用於高階案例的屬性和 Api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="fa4d4-111">因此，本文中顯示的程式碼範例需要下列其中一個或兩個 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="fa4d4-112">@No__t-1 中目前不支援來自 <xref:System.Runtime.Serialization> 命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="fa4d4-113">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="fa4d4-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="fa4d4-114">若要將 JSON 寫入字串，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fa4d4-115">下列範例會使用具有泛型型別參數的多載：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="fa4d4-116">您可以省略泛型型別參數，並改為使用泛型型別推斷：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="fa4d4-117">以下是要序列化的範例型別，其中包含集合和嵌套的類別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="fa4d4-118">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="fa4d4-119">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="fa4d4-120">@No__t-0 的多載可讓您序列化為 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="fa4d4-121">@No__t 0 多載的非同步版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="fa4d4-122">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="fa4d4-122">Serialize to UTF-8</span></span>

<span data-ttu-id="fa4d4-123">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="fa4d4-124">或者，可以使用 <xref:System.Text.Json.Utf8JsonWriter> 的 @no__t 0 多載。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="fa4d4-125">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約 5-10%。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="fa4d4-126">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="fa4d4-127">序列化行為</span><span class="sxs-lookup"><span data-stu-id="fa4d4-127">Serialization behavior</span></span>

* <span data-ttu-id="fa4d4-128">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="fa4d4-129">您可以[指定要排除的屬性](#exclude-properties)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="fa4d4-130">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)來進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="fa4d4-131">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-131">By default, JSON is minified.</span></span> <span data-ttu-id="fa4d4-132">您可以[整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="fa4d4-133">根據預設，JSON 名稱的大小寫會符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="fa4d4-134">您可以[自訂 JSON 名稱大小寫](#customize-json-names)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="fa4d4-135">偵測到迴圈參考，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="fa4d4-136">如需詳細資訊，請參閱 GitHub 上 dotnet/corefx 存放庫中[迴圈參考的問題](https://github.com/dotnet/corefx/issues/38579)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="fa4d4-137">目前已排除欄位。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="fa4d4-138">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-138">Supported types include:</span></span>

* <span data-ttu-id="fa4d4-139">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="fa4d4-140">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="fa4d4-141">一維和不規則陣列（`ArrayName[][]`）。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="fa4d4-142">`Dictionary<string,TValue>`，其中 `TValue` 是 `object`、`JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="fa4d4-143">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-143">Collections from the following namespaces.</span></span> <span data-ttu-id="fa4d4-144">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的[集合支援問題](https://github.com/dotnet/corefx/issues/36643)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="fa4d4-145">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="fa4d4-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="fa4d4-146">若要從字串還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="fa4d4-147">如需範例，請參閱[序列化](#how-to-write-net-objects-to-json-serialize)一節。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="fa4d4-148">JSON 和 .NET 物件相同，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="fa4d4-149">@No__t-0 的多載可讓您從 `Stream` 進行還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="fa4d4-150">@No__t 0 多載的非同步版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="fa4d4-151">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="fa4d4-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="fa4d4-152">若要從 UTF-8 還原序列化，請呼叫採用 `Utf8JsonReader` 或 `ReadOnlySpan<byte>` 的 @no__t 0 多載，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="fa4d4-153">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="fa4d4-153">Deserialization behavior</span></span>

* <span data-ttu-id="fa4d4-154">根據預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="fa4d4-155">您可以[指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="fa4d4-156">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="fa4d4-157">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="fa4d4-158">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="fa4d4-159">如需詳細資訊，請參閱 github 上的 dotnet/corefx 存放庫中的[不可變物件支援](https://github.com/dotnet/corefx/issues/38569)和[唯讀屬性支援問題](https://github.com/dotnet/corefx/issues/38163)的問題。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="fa4d4-160">根據預設，列舉會當做數位來支援。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="fa4d4-161">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-161">Fields aren't supported.</span></span>
* <span data-ttu-id="fa4d4-162">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="fa4d4-163">如有需要，您可以[允許留言和尾端逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="fa4d4-164">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="fa4d4-165">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="fa4d4-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="fa4d4-166">若要以整齊的格式列印 JSON 輸出，請將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-167">以下是要序列化的範例型別和 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-167">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="fa4d4-168">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="fa4d4-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="fa4d4-169">根據預設，在 JSON 中不允許批註和尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="fa4d4-170">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip`。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="fa4d4-171">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="fa4d4-172">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

<span data-ttu-id="fa4d4-173">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="fa4d4-174">自訂 JSON 名稱</span><span class="sxs-lookup"><span data-stu-id="fa4d4-174">Customize JSON names</span></span>

<span data-ttu-id="fa4d4-175">根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="fa4d4-176">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-176">This section explains how to:</span></span>

* <span data-ttu-id="fa4d4-177">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="fa4d4-177">Customize individual property names</span></span>
* <span data-ttu-id="fa4d4-178">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="fa4d4-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="fa4d4-179">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="fa4d4-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="fa4d4-180">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="fa4d4-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="fa4d4-181">目前不支援自動將列舉轉換為 camel 案例。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="fa4d4-182">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的[列舉 camel 案例支援問題](https://github.com/dotnet/corefx/issues/37725)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="fa4d4-183">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="fa4d4-183">Customize individual property names</span></span>

<span data-ttu-id="fa4d4-184">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="fa4d4-185">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-185">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="fa4d4-186">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="fa4d4-187">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="fa4d4-188">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="fa4d4-189">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="fa4d4-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="fa4d4-190">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-191">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-191">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="fa4d4-192">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="fa4d4-193">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="fa4d4-194">會由 `[JsonPropertyName]` 屬性覆寫。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="fa4d4-195">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="fa4d4-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="fa4d4-196">若要使用自訂 JSON 屬性命名原則，請建立衍生自 <xref:System.Text.Json.JsonNamingPolicy> 的類別，並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="fa4d4-197">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-198">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-198">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="fa4d4-199">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="fa4d4-200">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="fa4d4-201">會由 `[JsonPropertyName]` 屬性覆寫。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="fa4d4-202">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="fa4d4-202">Camel case dictionary keys</span></span>

<span data-ttu-id="fa4d4-203">如果要序列化之物件的屬性為 `Dictionary<string,TValue>` 的類型，則 @no__t 1 鍵可以轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="fa4d4-204">若要這麼做，請將 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-205">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="fa4d4-206">屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-206">Property</span></span> |<span data-ttu-id="fa4d4-207">值</span><span class="sxs-lookup"><span data-stu-id="fa4d4-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="fa4d4-208">Date</span><span class="sxs-lookup"><span data-stu-id="fa4d4-208">Date</span></span>    | <span data-ttu-id="fa4d4-209">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="fa4d4-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="fa4d4-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="fa4d4-210">TemperatureC</span></span>| <span data-ttu-id="fa4d4-211">25</span><span class="sxs-lookup"><span data-stu-id="fa4d4-211">25</span></span> |
| <span data-ttu-id="fa4d4-212">總結</span><span class="sxs-lookup"><span data-stu-id="fa4d4-212">Summary</span></span>| <span data-ttu-id="fa4d4-213">熱</span><span class="sxs-lookup"><span data-stu-id="fa4d4-213">Hot</span></span>|
| <span data-ttu-id="fa4d4-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="fa4d4-214">TemperatureRanges</span></span> | <span data-ttu-id="fa4d4-215">冷，20</span><span class="sxs-lookup"><span data-stu-id="fa4d4-215">Cold, 20</span></span><br><span data-ttu-id="fa4d4-216">熱門、40</span><span class="sxs-lookup"><span data-stu-id="fa4d4-216">Hot, 40</span></span>|

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

<span data-ttu-id="fa4d4-217">Camel 案例命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="fa4d4-218">排除屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-218">Exclude properties</span></span>

<span data-ttu-id="fa4d4-219">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="fa4d4-220">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="fa4d4-221">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="fa4d4-222">個別屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-222">Individual properties</span></span>
* <span data-ttu-id="fa4d4-223">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-223">All read-only properties</span></span>
* <span data-ttu-id="fa4d4-224">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="fa4d4-225">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-225">Exclude individual properties</span></span>

<span data-ttu-id="fa4d4-226">若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="fa4d4-227">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-227">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="fa4d4-228">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-228">Exclude all read-only properties</span></span>

<span data-ttu-id="fa4d4-229">若要排除所有唯讀屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-230">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-230">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="fa4d4-231">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-231">This option applies only to serialization.</span></span> <span data-ttu-id="fa4d4-232">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="fa4d4-233">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="fa4d4-234">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-234">Exclude all null value properties</span></span>

<span data-ttu-id="fa4d4-235">若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="fa4d4-236">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="fa4d4-237">屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-237">Property</span></span> |<span data-ttu-id="fa4d4-238">值</span><span class="sxs-lookup"><span data-stu-id="fa4d4-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="fa4d4-239">Date</span><span class="sxs-lookup"><span data-stu-id="fa4d4-239">Date</span></span>    | <span data-ttu-id="fa4d4-240">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="fa4d4-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="fa4d4-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="fa4d4-241">TemperatureC</span></span>| <span data-ttu-id="fa4d4-242">25</span><span class="sxs-lookup"><span data-stu-id="fa4d4-242">25</span></span> |
| <span data-ttu-id="fa4d4-243">總結</span><span class="sxs-lookup"><span data-stu-id="fa4d4-243">Summary</span></span>| <span data-ttu-id="fa4d4-244">null</span><span class="sxs-lookup"><span data-stu-id="fa4d4-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="fa4d4-245">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="fa4d4-246">在還原序列化期間，JSON 中的 null 值只有在有效的情況下才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="fa4d4-247">不可為 null 的實數值型別的 Null 值會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="fa4d4-248">如需詳細資訊，請參閱 GitHub 上 dotnet/corefx 存放庫中[不可為 null 的實數值型別問題](https://github.com/dotnet/corefx/issues/40922)。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="fa4d4-249">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="fa4d4-249">Case-insensitive property matching</span></span>

<span data-ttu-id="fa4d4-250">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="fa4d4-251">若要變更此行為，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="fa4d4-252">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="fa4d4-253">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="fa4d4-254">包含衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-254">Include properties of derived classes</span></span>

<span data-ttu-id="fa4d4-255">當您在編譯時期指定要序列化的型別時，不支援多型序列化。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="fa4d4-256">例如，假設您有 `WeatherForecast` 類別，而衍生類別 `WeatherForecastWithWind`：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="fa4d4-257">而且假設在編譯時期傳遞給或 @no__t 推斷的型別是 `WeatherForecast`：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="fa4d4-258">在此案例中，即使 `weatherForecast` 物件實際上是 @no__t 2 物件，也不會序列化 `WindSpeed` 屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="fa4d4-259">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="fa4d4-260">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="fa4d4-261">若要序列化衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="fa4d4-262">呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 的多載，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="fa4d4-263">宣告要序列化為 `object` 的物件。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="fa4d4-264">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="fa4d4-265">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="fa4d4-265">Handle overflow JSON</span></span>

<span data-ttu-id="fa4d4-266">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="fa4d4-267">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="fa4d4-268">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-268">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="fa4d4-269">如果您將顯示的 JSON 還原序列化為顯示的類型，`DatesAvailable` 和 @no__t 1 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="fa4d4-270">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>` 類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="fa4d4-271">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成 `ExtensionData` 屬性的機碼值組：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="fa4d4-272">屬性</span><span class="sxs-lookup"><span data-stu-id="fa4d4-272">Property</span></span> |<span data-ttu-id="fa4d4-273">值</span><span class="sxs-lookup"><span data-stu-id="fa4d4-273">Value</span></span>  |<span data-ttu-id="fa4d4-274">注意</span><span class="sxs-lookup"><span data-stu-id="fa4d4-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="fa4d4-275">Date</span><span class="sxs-lookup"><span data-stu-id="fa4d4-275">Date</span></span>    | <span data-ttu-id="fa4d4-276">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="fa4d4-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="fa4d4-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="fa4d4-277">TemperatureC</span></span>| <span data-ttu-id="fa4d4-278">0</span><span class="sxs-lookup"><span data-stu-id="fa4d4-278">0</span></span> | <span data-ttu-id="fa4d4-279">區分大小寫不相符（在 JSON 中為 `temperatureC`），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="fa4d4-280">總結</span><span class="sxs-lookup"><span data-stu-id="fa4d4-280">Summary</span></span> | <span data-ttu-id="fa4d4-281">熱</span><span class="sxs-lookup"><span data-stu-id="fa4d4-281">Hot</span></span> ||
| <span data-ttu-id="fa4d4-282">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="fa4d4-282">ExtensionData</span></span> | <span data-ttu-id="fa4d4-283">temperatureC:25</span><span class="sxs-lookup"><span data-stu-id="fa4d4-283">temperatureC: 25</span></span> |<span data-ttu-id="fa4d4-284">因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="fa4d4-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="fa4d4-285">DatesAvailable:</span></span><br>  <span data-ttu-id="fa4d4-286">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="fa4d4-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="fa4d4-287">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="fa4d4-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="fa4d4-288">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="fa4d4-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="fa4d4-289">SummaryWords:</span></span><br><span data-ttu-id="fa4d4-290">酷</span><span class="sxs-lookup"><span data-stu-id="fa4d4-290">Cool</span></span><br><span data-ttu-id="fa4d4-291">風大</span><span class="sxs-lookup"><span data-stu-id="fa4d4-291">Windy</span></span><br><span data-ttu-id="fa4d4-292">潮濕</span><span class="sxs-lookup"><span data-stu-id="fa4d4-292">Humid</span></span> |<span data-ttu-id="fa4d4-293">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="fa4d4-294">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="fa4d4-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="fa4d4-295">請注意，`ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="fa4d4-296">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="fa4d4-297">直接使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="fa4d4-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="fa4d4-298">下列範例顯示如何直接使用 <xref:System.Text.Json.Utf8JsonWriter> 類別。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="fa4d4-299">直接使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="fa4d4-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="fa4d4-300">下列範例顯示如何直接使用 <xref:System.Text.Json.Utf8JsonReader> 類別。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="fa4d4-301">此程式碼假設 @no__t 0 變數是包含有效 JSON 的位元組陣列，並以 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="fa4d4-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

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

## <a name="additional-resources"></a><span data-ttu-id="fa4d4-302">其他資源</span><span class="sxs-lookup"><span data-stu-id="fa4d4-302">Additional resources</span></span>

* [<span data-ttu-id="fa4d4-303">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="fa4d4-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="fa4d4-304">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="fa4d4-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="fa4d4-305">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="fa4d4-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
