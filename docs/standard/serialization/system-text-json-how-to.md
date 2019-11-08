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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740428"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="73bfb-102">如何在 .NET 中序列化和還原序列化 JSON</span><span class="sxs-lookup"><span data-stu-id="73bfb-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73bfb-103">JSON 序列化檔集在結構中。</span><span class="sxs-lookup"><span data-stu-id="73bfb-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="73bfb-104">本文並未涵蓋所有案例。</span><span class="sxs-lookup"><span data-stu-id="73bfb-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="73bfb-105">如需詳細資訊，請檢查 GitHub 上 dotnet/corefx 存放庫中的[system.object 問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)，特別是標示為[Json 功能的](https://github.com/dotnet/corefx/labels/json-functionality-doc)檔。</span><span class="sxs-lookup"><span data-stu-id="73bfb-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="73bfb-106">本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="73bfb-107">指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。</span><span class="sxs-lookup"><span data-stu-id="73bfb-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="73bfb-108">命名空間</span><span class="sxs-lookup"><span data-stu-id="73bfb-108">Namespaces</span></span>

<span data-ttu-id="73bfb-109"><xref:System.Text.Json> 命名空間包含所有進入點和主要類型。</span><span class="sxs-lookup"><span data-stu-id="73bfb-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="73bfb-110"><xref:System.Text.Json.Serialization> 命名空間包含用於高階案例的屬性和 Api，以及序列化和還原序列化特有的自訂。</span><span class="sxs-lookup"><span data-stu-id="73bfb-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="73bfb-111">本文中所示的程式碼範例需要其中一個或兩個命名空間的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="73bfb-111">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="73bfb-112">`System.Text.Json`目前不支援來自 <xref:System.Runtime.Serialization> 命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="73bfb-113">如何將 .NET 物件寫入 JSON （序列化）</span><span class="sxs-lookup"><span data-stu-id="73bfb-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="73bfb-114">若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="73bfb-114">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73bfb-115">下列範例會將 JSON 建立為字串：</span><span class="sxs-lookup"><span data-stu-id="73bfb-115">The following example creates JSON as a string:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="73bfb-116">下列範例會使用同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="73bfb-116">The following example uses synchronous code to create a JSON file:</span></span>

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

<span data-ttu-id="73bfb-117">下列範例會使用非同步程式碼來建立 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="73bfb-117">The following example uses asynchronous code to create a JSON file:</span></span>

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

<span data-ttu-id="73bfb-118">上述範例會針對要序列化的型別使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="73bfb-118">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="73bfb-119">`Serialize()` 的多載會採用泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="73bfb-119">An overload of `Serialize()` takes a generic type parameter:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a><span data-ttu-id="73bfb-120">序列化範例</span><span class="sxs-lookup"><span data-stu-id="73bfb-120">Serialization example</span></span>

<span data-ttu-id="73bfb-121">以下是包含集合和嵌套類別的範例型別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-121">Here's an example type that contains collections and nested classes:</span></span>

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

<span data-ttu-id="73bfb-122">序列化上述型別之實例的 JSON 輸出如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="73bfb-122">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="73bfb-123">預設會縮減 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="73bfb-123">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="73bfb-124">下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：</span><span class="sxs-lookup"><span data-stu-id="73bfb-124">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="73bfb-125">序列化為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="73bfb-125">Serialize to UTF-8</span></span>

<span data-ttu-id="73bfb-126">若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="73bfb-126">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="73bfb-127">也可以使用接受 <xref:System.Text.Json.Utf8JsonWriter> 的 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 多載。</span><span class="sxs-lookup"><span data-stu-id="73bfb-127">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="73bfb-128">序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約5-10%。</span><span class="sxs-lookup"><span data-stu-id="73bfb-128">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="73bfb-129">差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。</span><span class="sxs-lookup"><span data-stu-id="73bfb-129">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="73bfb-130">序列化行為</span><span class="sxs-lookup"><span data-stu-id="73bfb-130">Serialization behavior</span></span>

* <span data-ttu-id="73bfb-131">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-131">By default, all public properties are serialized.</span></span> <span data-ttu-id="73bfb-132">您可以[指定要排除的屬性](#exclude-properties-from-serialization)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-132">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="73bfb-133">[預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)來進行轉義的字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="73bfb-133">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="73bfb-134">根據預設，JSON 是縮減。</span><span class="sxs-lookup"><span data-stu-id="73bfb-134">By default, JSON is minified.</span></span> <span data-ttu-id="73bfb-135">您可以[整齊列印 JSON](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-135">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="73bfb-136">根據預設，JSON 名稱的大小寫會符合 .NET 名稱。</span><span class="sxs-lookup"><span data-stu-id="73bfb-136">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="73bfb-137">您可以[自訂 JSON 名稱大小寫](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-137">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="73bfb-138">偵測到迴圈參考，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73bfb-138">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="73bfb-139">如需詳細資訊，請參閱 GitHub 上 dotnet/corefx 存放庫中[迴圈參考的問題](https://github.com/dotnet/corefx/issues/38579)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-139">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="73bfb-140">目前已排除欄位。</span><span class="sxs-lookup"><span data-stu-id="73bfb-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="73bfb-141">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="73bfb-141">Supported types include:</span></span>

* <span data-ttu-id="73bfb-142">對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。</span><span class="sxs-lookup"><span data-stu-id="73bfb-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="73bfb-143">使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="73bfb-144">一維和不規則陣列（`ArrayName[][]`）。</span><span class="sxs-lookup"><span data-stu-id="73bfb-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="73bfb-145">`Dictionary<string,TValue>`，其中 `TValue` 是 `object`、`JsonElement`或 POCO。</span><span class="sxs-lookup"><span data-stu-id="73bfb-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="73bfb-146">下列命名空間中的集合。</span><span class="sxs-lookup"><span data-stu-id="73bfb-146">Collections from the following namespaces.</span></span> <span data-ttu-id="73bfb-147">如需詳細資訊，請參閱 GitHub 上的 dotnet/corefx 存放庫中的[集合支援問題](https://github.com/dotnet/corefx/issues/36643)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-147">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="73bfb-148">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)來處理其他類型，或提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="73bfb-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="73bfb-149">如何將 JSON 讀入 .NET 物件（還原序列化）</span><span class="sxs-lookup"><span data-stu-id="73bfb-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="73bfb-150">若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="73bfb-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73bfb-151">下列範例會從字串讀取 JSON：</span><span class="sxs-lookup"><span data-stu-id="73bfb-151">The following example reads JSON from a string:</span></span>

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="73bfb-152">若要使用同步程式碼從檔案還原序列化，請將檔案讀取到字串中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="73bfb-153">若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="73bfb-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

<span data-ttu-id="73bfb-154">如需範例類型和對應的 JSON，請參閱[序列化範例](#serialization-example)一節。</span><span class="sxs-lookup"><span data-stu-id="73bfb-154">For an example type and corresponding JSON, see the [Serialization example](#serialization-example) section.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="73bfb-155">從 UTF-8 還原序列化</span><span class="sxs-lookup"><span data-stu-id="73bfb-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="73bfb-156">若要從 UTF-8 還原序列化，請呼叫採用 `Utf8JsonReader` 或 `ReadOnlySpan<byte>`的 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 多載，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="73bfb-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="73bfb-157">這些範例假設 JSON 位於名為 jsonUtf8Bytes 的位元組陣列中。</span><span class="sxs-lookup"><span data-stu-id="73bfb-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="73bfb-158">還原序列化行為</span><span class="sxs-lookup"><span data-stu-id="73bfb-158">Deserialization behavior</span></span>

* <span data-ttu-id="73bfb-159">根據預設，屬性名稱比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="73bfb-160">您可以[指定不區分大小寫](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="73bfb-161">如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73bfb-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="73bfb-162">不支援在沒有無參數的函式的情況下還原序列化成參考型別。</span><span class="sxs-lookup"><span data-stu-id="73bfb-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="73bfb-163">不支援還原序列化為不可變的物件或唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="73bfb-164">如需詳細資訊，請參閱 github 上的 dotnet/corefx 存放庫中的[不可變物件支援](https://github.com/dotnet/corefx/issues/38569)和[唯讀屬性支援問題](https://github.com/dotnet/corefx/issues/38163)的問題。</span><span class="sxs-lookup"><span data-stu-id="73bfb-164">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="73bfb-165">根據預設，列舉會當做數位來支援。</span><span class="sxs-lookup"><span data-stu-id="73bfb-165">By default, enums are supported as numbers.</span></span> <span data-ttu-id="73bfb-166">您可以將[列舉名稱序列化為字串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-166">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="73bfb-167">欄位不受支援。</span><span class="sxs-lookup"><span data-stu-id="73bfb-167">Fields aren't supported.</span></span>
* <span data-ttu-id="73bfb-168">根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73bfb-168">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="73bfb-169">您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-169">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="73bfb-170">[預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。</span><span class="sxs-lookup"><span data-stu-id="73bfb-170">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="73bfb-171">您可以[執行自訂轉換器](system-text-json-converters-how-to.md)，以提供內建轉換器不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="73bfb-171">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="73bfb-172">序列化為格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="73bfb-172">Serialize to formatted JSON</span></span>

<span data-ttu-id="73bfb-173">若要以整齊的格式列印 JSON 輸出，請將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="73bfb-173">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-174">以下是要序列化的範例型別，以及相當列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="73bfb-174">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

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

## <a name="customize-json-names-and-values"></a><span data-ttu-id="73bfb-175">自訂 JSON 名稱和值</span><span class="sxs-lookup"><span data-stu-id="73bfb-175">Customize JSON names and values</span></span>

<span data-ttu-id="73bfb-176">根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-176">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="73bfb-177">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="73bfb-177">Enum values are represented as numbers.</span></span> <span data-ttu-id="73bfb-178">本節說明如何：</span><span class="sxs-lookup"><span data-stu-id="73bfb-178">This section explains how to:</span></span>

* <span data-ttu-id="73bfb-179">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="73bfb-179">Customize individual property names</span></span>
* <span data-ttu-id="73bfb-180">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="73bfb-180">Convert all property names to camel case</span></span>
* <span data-ttu-id="73bfb-181">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="73bfb-181">Implement a custom property naming policy</span></span>
* <span data-ttu-id="73bfb-182">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="73bfb-182">Convert dictionary keys to camel case</span></span>
* <span data-ttu-id="73bfb-183">將列舉轉換為字串和大小寫</span><span class="sxs-lookup"><span data-stu-id="73bfb-183">Convert enums to strings and camel case</span></span> 

<span data-ttu-id="73bfb-184">針對需要對 JSON 屬性名稱和值進行特殊處理的其他案例，您可以[執行自訂轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-184">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="73bfb-185">自訂個別屬性名稱</span><span class="sxs-lookup"><span data-stu-id="73bfb-185">Customize individual property names</span></span>

<span data-ttu-id="73bfb-186">若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-186">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="73bfb-187">以下是要序列化和產生 JSON 的範例型別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-187">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="73bfb-188">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="73bfb-188">The property name set by this attribute:</span></span>

* <span data-ttu-id="73bfb-189">雙向套用，用於序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-189">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="73bfb-190">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="73bfb-190">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="73bfb-191">所有 JSON 屬性名稱都使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="73bfb-191">Use camel case for all JSON property names</span></span>

<span data-ttu-id="73bfb-192">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-192">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-193">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-193">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="73bfb-194">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="73bfb-194">The camel case property naming policy:</span></span>

* <span data-ttu-id="73bfb-195">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-195">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="73bfb-196">會由 `[JsonPropertyName]` 屬性來覆寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-196">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="73bfb-197">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-197">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="73bfb-198">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="73bfb-198">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="73bfb-199">若要使用自訂 JSON 屬性命名原則，請建立衍生自 <xref:System.Text.Json.JsonNamingPolicy> 的類別，並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-199">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="73bfb-200">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="73bfb-200">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-201">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-201">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="73bfb-202">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="73bfb-202">The JSON property naming policy:</span></span>

* <span data-ttu-id="73bfb-203">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-203">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="73bfb-204">會由 `[JsonPropertyName]` 屬性來覆寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-204">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="73bfb-205">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="73bfb-205">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="73bfb-206">Camel 大小寫字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="73bfb-206">Camel case dictionary keys</span></span>

<span data-ttu-id="73bfb-207">如果要序列化之物件的屬性是 `Dictionary<string,TValue>`類型，則 `string` 索引鍵可以轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="73bfb-207">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="73bfb-208">若要這麼做，請將 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-208">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-209">使用名為 `TemperatureRanges` 的字典序列化物件，其中具有 `"ColdMinTemp", 20` 的索引鍵/值組，而 `"HotMinTemp", 40` 會產生如下列範例所示的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="73bfb-209">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="73bfb-210">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-210">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="73bfb-211">如果您將字典還原序列化，則即使您指定 `DictionaryKeyPolicy`的 `JsonNamingPolicy.CamelCase`，索引鍵仍會符合 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="73bfb-211">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="73bfb-212">做為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="73bfb-212">Enums as strings</span></span>

<span data-ttu-id="73bfb-213">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="73bfb-213">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="73bfb-214">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter>。</span><span class="sxs-lookup"><span data-stu-id="73bfb-214">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="73bfb-215">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-215">For example, suppose you need to serialize the following class that has an enum:</span></span>

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

<span data-ttu-id="73bfb-216">如果摘要是 `Hot`，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="73bfb-216">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

<span data-ttu-id="73bfb-217">下列範例程式碼會改為序列化列舉名稱，並將它們轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="73bfb-217">The following sample code serializes the enum names instead, and converts them to camel case:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

<span data-ttu-id="73bfb-218">產生的 JSON 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-218">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="73bfb-219">對列舉 as 字串的支援也適用于還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-219">The support for enums as strings applies to deserialization also, as shown in the following example:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="73bfb-220">排除序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-220">Exclude properties from serialization</span></span>

<span data-ttu-id="73bfb-221">預設會序列化所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-221">By default, all public properties are serialized.</span></span> <span data-ttu-id="73bfb-222">如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="73bfb-222">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="73bfb-223">本節說明如何排除：</span><span class="sxs-lookup"><span data-stu-id="73bfb-223">This section explains how to exclude:</span></span>

* <span data-ttu-id="73bfb-224">個別屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-224">Individual properties</span></span>
* <span data-ttu-id="73bfb-225">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-225">All read-only properties</span></span>
* <span data-ttu-id="73bfb-226">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-226">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="73bfb-227">排除個別屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-227">Exclude individual properties</span></span>

<span data-ttu-id="73bfb-228">若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-228">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="73bfb-229">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-229">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="73bfb-230">排除所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-230">Exclude all read-only properties</span></span>

<span data-ttu-id="73bfb-231">如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。</span><span class="sxs-lookup"><span data-stu-id="73bfb-231">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="73bfb-232">若要排除所有唯讀屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-232">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-233">以下是要序列化和 JSON 輸出的範例型別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-233">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="73bfb-234">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-234">This option applies only to serialization.</span></span> <span data-ttu-id="73bfb-235">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-235">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="73bfb-236">排除所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-236">Exclude all null value properties</span></span>

<span data-ttu-id="73bfb-237">若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-237">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-238">以下是要序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="73bfb-238">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="73bfb-239">屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-239">Property</span></span> |<span data-ttu-id="73bfb-240">值</span><span class="sxs-lookup"><span data-stu-id="73bfb-240">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="73bfb-241">日期</span><span class="sxs-lookup"><span data-stu-id="73bfb-241">Date</span></span>    | <span data-ttu-id="73bfb-242">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="73bfb-242">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="73bfb-243">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="73bfb-243">TemperatureC</span></span>| <span data-ttu-id="73bfb-244">25</span><span class="sxs-lookup"><span data-stu-id="73bfb-244">25</span></span> |
| <span data-ttu-id="73bfb-245">總結</span><span class="sxs-lookup"><span data-stu-id="73bfb-245">Summary</span></span>| <span data-ttu-id="73bfb-246">null</span><span class="sxs-lookup"><span data-stu-id="73bfb-246">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="73bfb-247">此設定適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-247">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="73bfb-248">如需其對還原序列化之影響的詳細資訊，請參閱[在還原序列化時忽略 null](#ignore-null-when-deserializing)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-248">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="73bfb-249">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="73bfb-249">Customize character encoding</span></span>

<span data-ttu-id="73bfb-250">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="73bfb-250">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="73bfb-251">也就是說，它會以 `\uxxxx` 取代它們，其中 `xxxxx` 是字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="73bfb-251">That is, it replaces them with `\uxxxx` where `xxxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="73bfb-252">例如，如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-252">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="73bfb-253">序列化語言字元集</span><span class="sxs-lookup"><span data-stu-id="73bfb-253">Serialize language character sets</span></span>

<span data-ttu-id="73bfb-254">若要將一或多個語言的字元集序列化，請在建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>的實例時指定[Unicode 範圍](xref:System.Text.Unicode.UnicodeRanges)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-254">To serialize the character set(s) of one or more languages, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-255">此程式碼會序列化斯拉夫文和希臘文字元。</span><span class="sxs-lookup"><span data-stu-id="73bfb-255">This code serializes Cyrillic and Greek characters.</span></span> <span data-ttu-id="73bfb-256">下列範例顯示的是斯拉夫文字元：</span><span class="sxs-lookup"><span data-stu-id="73bfb-256">Cyrillic characters are shown in the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

<span data-ttu-id="73bfb-257">若要指定所有語言，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="73bfb-257">To specify all languages, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="73bfb-258">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="73bfb-258">Serialize specific characters</span></span>

<span data-ttu-id="73bfb-259">另一個替代方式是指定您想要允許通過的個別字元，而不會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="73bfb-259">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="73bfb-260">下列範例只會序列化жарко的前兩個字元：</span><span class="sxs-lookup"><span data-stu-id="73bfb-260">The following example serializes only the first two characters of жарко:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="73bfb-261">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="73bfb-261">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="73bfb-262">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="73bfb-262">Serialize all characters</span></span>

<span data-ttu-id="73bfb-263">若要最小化進行的轉義，您可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-263">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> <span data-ttu-id="73bfb-264">不同于預設編碼器，`UnsafeRelaxedJsonEscaping` 編碼器：</span><span class="sxs-lookup"><span data-stu-id="73bfb-264">Unlike the default encoder, the `UnsafeRelaxedJsonEscaping` encoder:</span></span>
>
> * <span data-ttu-id="73bfb-265">不會將 HTML 敏感的字元（例如 `<`、`>`、`&`和 `'`）換用。</span><span class="sxs-lookup"><span data-stu-id="73bfb-265">Doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="73bfb-266">不提供任何額外的深層防禦保護，以抵禦 XSS 或資訊洩漏攻擊，例如可能會導致用戶端和伺服器 disagreeing 在*字元集*上。</span><span class="sxs-lookup"><span data-stu-id="73bfb-266">Doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
> * <span data-ttu-id="73bfb-267">比預設編碼器更寬鬆，其允許字元通過非經過轉義。</span><span class="sxs-lookup"><span data-stu-id="73bfb-267">Is more permissive than the default encoder on which characters are allowed to pass through unescaped.</span></span>
>
> <span data-ttu-id="73bfb-268">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="73bfb-268">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="73bfb-269">例如，如果伺服器正在傳送回應標頭 `Content-Type: application/json; charset=utf-8`，您可以使用它。</span><span class="sxs-lookup"><span data-stu-id="73bfb-269">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="73bfb-270">永遠不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="73bfb-270">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="73bfb-271">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-271">Serialize properties of derived classes</span></span>

<span data-ttu-id="73bfb-272">當您在編譯時期指定要序列化的型別時，不支援多型序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-272">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="73bfb-273">例如，假設您有 `WeatherForecast` 類別和衍生類別 `WeatherForecastWithWind`：</span><span class="sxs-lookup"><span data-stu-id="73bfb-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="73bfb-274">而且在編譯時期，假設 `Serialize` 方法的型別引數是 `WeatherForecast`：</span><span class="sxs-lookup"><span data-stu-id="73bfb-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="73bfb-275">在此案例中，即使 `weatherForecast` 物件實際上是 `WeatherForecastWithWind` 物件，`WindSpeed` 屬性也不會序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="73bfb-276">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="73bfb-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="73bfb-277">這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。</span><span class="sxs-lookup"><span data-stu-id="73bfb-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="73bfb-278">若要序列化衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="73bfb-278">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="73bfb-279">呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 的多載，可讓您在執行時間指定類型：</span><span class="sxs-lookup"><span data-stu-id="73bfb-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="73bfb-280">宣告要序列化為 `object`的物件。</span><span class="sxs-lookup"><span data-stu-id="73bfb-280">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="73bfb-281">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="73bfb-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="73bfb-282">如需多型還原序列化的詳細資訊，請參閱[支援](system-text-json-converters-how-to.md#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="73bfb-282">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="73bfb-283">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="73bfb-283">Allow comments and trailing commas</span></span>

<span data-ttu-id="73bfb-284">根據預設，JSON 中不允許批註和尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="73bfb-284">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="73bfb-285">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設為 `JsonCommentHandling.Skip`。</span><span class="sxs-lookup"><span data-stu-id="73bfb-285">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="73bfb-286">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="73bfb-286">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="73bfb-287">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="73bfb-287">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="73bfb-288">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="73bfb-288">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="73bfb-289">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="73bfb-289">Case-insensitive property matching</span></span>

<span data-ttu-id="73bfb-290">根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。</span><span class="sxs-lookup"><span data-stu-id="73bfb-290">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="73bfb-291">若要變更該行為，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="73bfb-291">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="73bfb-292">以下是使用 camel 案例屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="73bfb-292">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="73bfb-293">它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="73bfb-293">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="handle-overflow-json"></a><span data-ttu-id="73bfb-294">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="73bfb-294">Handle overflow JSON</span></span>

<span data-ttu-id="73bfb-295">還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。</span><span class="sxs-lookup"><span data-stu-id="73bfb-295">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="73bfb-296">例如，假設您的目標型別為：</span><span class="sxs-lookup"><span data-stu-id="73bfb-296">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="73bfb-297">而要還原序列化的 JSON 則是：</span><span class="sxs-lookup"><span data-stu-id="73bfb-297">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="73bfb-298">如果您將顯示的 JSON 還原序列化為所顯示的類型，`DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="73bfb-298">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="73bfb-299">若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>`類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="73bfb-299">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="73bfb-300">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成 `ExtensionData` 屬性的機碼值組：</span><span class="sxs-lookup"><span data-stu-id="73bfb-300">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="73bfb-301">屬性</span><span class="sxs-lookup"><span data-stu-id="73bfb-301">Property</span></span> |<span data-ttu-id="73bfb-302">值</span><span class="sxs-lookup"><span data-stu-id="73bfb-302">Value</span></span>  |<span data-ttu-id="73bfb-303">備註</span><span class="sxs-lookup"><span data-stu-id="73bfb-303">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="73bfb-304">日期</span><span class="sxs-lookup"><span data-stu-id="73bfb-304">Date</span></span>    | <span data-ttu-id="73bfb-305">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="73bfb-305">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="73bfb-306">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="73bfb-306">TemperatureC</span></span>| <span data-ttu-id="73bfb-307">0</span><span class="sxs-lookup"><span data-stu-id="73bfb-307">0</span></span> | <span data-ttu-id="73bfb-308">區分大小寫不相符（`temperatureC` 在 JSON 中），因此不會設定屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-308">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="73bfb-309">總結</span><span class="sxs-lookup"><span data-stu-id="73bfb-309">Summary</span></span> | <span data-ttu-id="73bfb-310">熱</span><span class="sxs-lookup"><span data-stu-id="73bfb-310">Hot</span></span> ||
| <span data-ttu-id="73bfb-311">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="73bfb-311">ExtensionData</span></span> | <span data-ttu-id="73bfb-312">temperatureC：25</span><span class="sxs-lookup"><span data-stu-id="73bfb-312">temperatureC: 25</span></span> |<span data-ttu-id="73bfb-313">因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="73bfb-313">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="73bfb-314">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="73bfb-314">DatesAvailable:</span></span><br>  <span data-ttu-id="73bfb-315">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="73bfb-315">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="73bfb-316">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="73bfb-316">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="73bfb-317">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="73bfb-317">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="73bfb-318">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="73bfb-318">SummaryWords:</span></span><br><span data-ttu-id="73bfb-319">酷</span><span class="sxs-lookup"><span data-stu-id="73bfb-319">Cool</span></span><br><span data-ttu-id="73bfb-320">風大</span><span class="sxs-lookup"><span data-stu-id="73bfb-320">Windy</span></span><br><span data-ttu-id="73bfb-321">潮濕</span><span class="sxs-lookup"><span data-stu-id="73bfb-321">Humid</span></span> |<span data-ttu-id="73bfb-322">JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。</span><span class="sxs-lookup"><span data-stu-id="73bfb-322">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="73bfb-323">當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-323">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="73bfb-324">請注意，`ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="73bfb-324">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="73bfb-325">這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="73bfb-325">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="73bfb-326">還原序列化時忽略 null</span><span class="sxs-lookup"><span data-stu-id="73bfb-326">Ignore null when deserializing</span></span>

<span data-ttu-id="73bfb-327">根據預設，如果 JSON 中的屬性是 null，則目標物件中的對應屬性會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="73bfb-327">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="73bfb-328">在某些情況下，目標屬性可能會有預設值，而且您不想要 null 值來覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="73bfb-328">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="73bfb-329">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="73bfb-329">For example, suppose the following code represents your target object:</span></span>

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="73bfb-330">假設下列 JSON 已還原序列化：</span><span class="sxs-lookup"><span data-stu-id="73bfb-330">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

<span data-ttu-id="73bfb-331">還原序列化之後，`WeatherForecastWithDefault` 物件的 `Summary` 屬性為 null。</span><span class="sxs-lookup"><span data-stu-id="73bfb-331">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="73bfb-332">若要變更此行為，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73bfb-332">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

<span data-ttu-id="73bfb-333">使用此選項時，`WeatherForecastWithDefault` 物件的 `Summary` 屬性是還原序列化後的預設值「沒有摘要」。</span><span class="sxs-lookup"><span data-stu-id="73bfb-333">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="73bfb-334">JSON 中的 Null 值只有在有效時才會被忽略。</span><span class="sxs-lookup"><span data-stu-id="73bfb-334">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="73bfb-335">不可為 null 的實數值型別的 Null 值會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73bfb-335">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="73bfb-336">如需詳細資訊，請參閱 GitHub 上 dotnet/corefx 存放庫中[不可為 null 的實數值型別問題](https://github.com/dotnet/corefx/issues/40922)。</span><span class="sxs-lookup"><span data-stu-id="73bfb-336">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="73bfb-337">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="73bfb-337">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="73bfb-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="73bfb-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="73bfb-339">`Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="73bfb-339">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="73bfb-340"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="73bfb-340">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="73bfb-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="73bfb-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="73bfb-342">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="73bfb-342">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="73bfb-343"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonWriter`。</span><span class="sxs-lookup"><span data-stu-id="73bfb-343">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="73bfb-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用 `Utf8JsonReader`建立唯讀檔案物件模型（DOM）的功能。</span><span class="sxs-lookup"><span data-stu-id="73bfb-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="73bfb-345">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="73bfb-345">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="73bfb-346">組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。</span><span class="sxs-lookup"><span data-stu-id="73bfb-346">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="73bfb-347">`JsonElement` 提供陣列和物件列舉值，以及用來將 JSON 文字轉換成常見 .NET 類型的 Api。</span><span class="sxs-lookup"><span data-stu-id="73bfb-347">The `JsonElement` provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="73bfb-348">`JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-348">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="73bfb-349">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="73bfb-349">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="73bfb-350">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="73bfb-350">Use JsonDocument for access to data</span></span>

<span data-ttu-id="73bfb-351">下列範例顯示如何使用 <xref:System.Text.Json.JsonDocument> 類別來隨機存取資料：</span><span class="sxs-lookup"><span data-stu-id="73bfb-351">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data:</span></span>

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

<span data-ttu-id="73bfb-352">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="73bfb-352">The preceding code:</span></span>

* <span data-ttu-id="73bfb-353">假設要分析的 JSON 是在名為 `jsonString`的字串中。</span><span class="sxs-lookup"><span data-stu-id="73bfb-353">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="73bfb-354">計算 `Students` 陣列中具有 `Grade` 屬性之物件的平均等級。</span><span class="sxs-lookup"><span data-stu-id="73bfb-354">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="73bfb-355">為沒有成績的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="73bfb-355">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="73bfb-356">藉由遞增 `count` 變數與每個反復專案來計算學生數目。</span><span class="sxs-lookup"><span data-stu-id="73bfb-356">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="73bfb-357">另一種方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A>：</span><span class="sxs-lookup"><span data-stu-id="73bfb-357">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span></span>

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

<span data-ttu-id="73bfb-358">以下是此程式碼所處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="73bfb-358">Here's an example of the JSON that this code processes:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="73bfb-359">使用 JsonDocument 寫入 JSON</span><span class="sxs-lookup"><span data-stu-id="73bfb-359">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="73bfb-360">下列範例顯示如何從 <xref:System.Text.Json.JsonDocument>寫入 JSON：</span><span class="sxs-lookup"><span data-stu-id="73bfb-360">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

<span data-ttu-id="73bfb-361">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="73bfb-361">The preceding code:</span></span>

* <span data-ttu-id="73bfb-362">讀取 JSON 檔案、將資料載入 `JsonDocument`，並將格式化（已列印）的 JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="73bfb-362">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="73bfb-363">會使用 <xref:System.Text.Json.JsonDocumentOptions> 來指定允許輸入 JSON 中的批註，但會忽略它。</span><span class="sxs-lookup"><span data-stu-id="73bfb-363">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="73bfb-364">完成時，會在寫入器上呼叫 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A>。</span><span class="sxs-lookup"><span data-stu-id="73bfb-364">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="73bfb-365">另一個替代方式是讓寫入器在處置時 autoflush。</span><span class="sxs-lookup"><span data-stu-id="73bfb-365">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="73bfb-366">以下是範例程式碼所要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="73bfb-366">Here's an example of JSON input to be processed by the example code:</span></span>

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

<span data-ttu-id="73bfb-367">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="73bfb-367">The result is the following pretty-printed JSON output:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="73bfb-368">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="73bfb-368">Use Utf8JsonWriter</span></span>

<span data-ttu-id="73bfb-369">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-369">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

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

## <a name="use-utf8jsonreader"></a><span data-ttu-id="73bfb-370">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="73bfb-370">Use Utf8JsonReader</span></span>

<span data-ttu-id="73bfb-371">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="73bfb-371">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

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

<span data-ttu-id="73bfb-372">上述程式碼假設 `jsonUtf8` 變數是包含有效 JSON 的位元組陣列，並以 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="73bfb-372">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="73bfb-373">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="73bfb-373">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="73bfb-374">下列範例示範如何以同步方式讀取檔案，並搜尋值：</span><span class="sxs-lookup"><span data-stu-id="73bfb-374">The following example shows how to read a file synchronously and search for a value:</span></span>

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

<span data-ttu-id="73bfb-375">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="73bfb-375">The preceding code:</span></span>

* <span data-ttu-id="73bfb-376">假設檔案是以 UTF-16 編碼，並將其轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="73bfb-376">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="73bfb-377">您可以使用下列程式碼，直接將編碼為 UTF-8 的檔案讀入 `ReadOnlySpan<byte>`中：</span><span class="sxs-lookup"><span data-stu-id="73bfb-377">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="73bfb-378">假設 JSON 包含物件的陣列，而且每個物件都可以包含 string 類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="73bfb-378">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="73bfb-379">計算物件，並 `name` 以「大學」結尾的屬性值。</span><span class="sxs-lookup"><span data-stu-id="73bfb-379">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="73bfb-380">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="73bfb-380">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="73bfb-381">產生的摘要訊息為「2個以上的名稱，其結尾為 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="73bfb-381">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a><span data-ttu-id="73bfb-382">其他資源</span><span class="sxs-lookup"><span data-stu-id="73bfb-382">Additional resources</span></span>

* [<span data-ttu-id="73bfb-383">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="73bfb-383">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="73bfb-384">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="73bfb-384">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="73bfb-385">撰寫 System.object 的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="73bfb-385">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="73bfb-386">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="73bfb-386">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
