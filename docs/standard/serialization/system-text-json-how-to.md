---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: 瞭解如何 System.Text.Json 在 .net 中使用命名空間進行序列化，並從 JSON 還原序列化。 包含範例程式碼。
ms.date: 11/05/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1e8c46e11d3a82ca0bce29f9cb7bbc749c219198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676721"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON

本文說明如何使用 <xref:System.Text.Json?displayProperty=fullName> 命名空間，從 JavaScript 物件標記法 (JSON) 序列化和還原序列化。 如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。

指示和範例程式碼會直接使用程式庫，而不是透過 [ASP.NET Core](/aspnet/core/)的架構。

大部分的序列化程式碼範例會將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為「 `true` 美觀」的 JSON (，以縮排和空白字元來取得可讀性) 。 針對生產用途，您通常會接受此設定的預設值 `false` 。

程式碼範例參考下列類別和它的變異：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>命名空間

<xref:System.Text.Json>命名空間包含所有進入點和主要類型。 <xref:System.Text.Json.Serialization>命名空間包含適用于進行序列化和還原序列化的 advanced 案例和自訂的屬性和 api。 本文中顯示的程式碼範例需要 `using` 下列其中一個或兩個命名空間的指示詞：

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization>不支援命名空間中的屬性 `System.Text.Json` 。

## <a name="how-to-write-net-objects-to-json-serialize"></a>如何將 .NET 物件寫入 JSON (序列化) 

若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。

下列範例會以字串形式建立 JSON：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

下列範例會使用同步程式碼來建立 JSON 檔案：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

下列範例會使用非同步程式碼來建立 JSON 檔案：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

上述範例會針對要序列化的型別使用型別推斷。 的多載 `Serialize()` 會採用泛型型別參數：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>序列化範例

以下是包含集合類型屬性和使用者定義型別的範例類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> "POCO" 代表 [純舊的 CLR 物件](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。 POCO 是一種 .NET 型別，其不相依于任何架構特定的類型，例如透過繼承或屬性。

序列化上述型別的實例的 JSON 輸出如下列範例所示。 JSON 輸出預設為縮減：

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

下列範例會顯示相同的 JSON，但格式化的 (也就是具有空白字元和縮排) 的整齊列印：

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

### <a name="serialize-to-utf-8"></a>序列化為 UTF-8

若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用採用的多載 <xref:System.Text.Json.Utf8JsonWriter> 。

使用以字串為基礎的方法，序列化為 UTF-8 的速度大約是5-10%。 差異是因為 (為 UTF-8 的位元組) 不需要轉換成字串 (UTF-16) 。

## <a name="serialization-behavior"></a>序列化行為

::: zone pivot="dotnet-5-0"

* 依預設，所有公用屬性都會進行序列化。 您可以 [指定要忽略的屬性](#ignore-properties)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。
* 根據預設，JSON 是縮減。 您可以 [整齊列印 JSON](#serialize-to-formatted-json)。
* 根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。 您可以 [自訂 JSON 名稱大小寫](#customize-json-names-and-values)。
* 依預設，會偵測到迴圈參考並擲回例外狀況。 您可以 [保留參考並處理迴圈參考](#preserve-references-and-handle-circular-references)。
* 依預設，會忽略 [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 。 您可以 [包含欄位](#include-fields)。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 依預設，所有公用屬性都會進行序列化。 您可以 [指定要忽略的屬性](#ignore-properties)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。
* 根據預設，JSON 是縮減。 您可以 [整齊列印 JSON](#serialize-to-formatted-json)。
* 根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。 您可以 [自訂 JSON 名稱大小寫](#customize-json-names-and-values)。
* 偵測到迴圈參考並擲回例外狀況。
* [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 會被忽略。
::: zone-end

支援的類型包括：
::: zone pivot="dotnet-5-0"

* 對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。
* [ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。
* 一維和不規則陣列 (`T[][]`) 。
* 下列命名空間中的集合和字典。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。
* [ (poco) ](https://en.wikipedia.org/wiki/Plain_old_CLR_object)的使用者定義簡單的 CLR 物件。
* 一維和不規則陣列 (`ArrayName[][]`) 。
* `Dictionary<string,TValue>` 其中 `TValue` 是 `object` 、 `JsonElement` 或 POCO。
* 下列命名空間中的集合。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) 來處理其他類型，或是提供內建轉換器不支援的功能。

## <a name="how-to-read-json-into-net-objects-deserialize"></a>如何將 JSON 讀入 .NET 物件 (還原序列化) 

若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。

下列範例會從字串讀取 JSON，並 `WeatherForecastWithPOCOs` 為 [序列化範例](#serialization-example)建立稍早所示類別的實例：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

若要使用同步程式碼從檔案還原序列化，請將檔案讀入字串，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>從 UTF-8 還原序列化

若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `Utf8JsonReader` 或的多載， `ReadOnlySpan<byte>` 如下列範例所示。 這些範例假設 JSON 是在名為 jsonUtf8Bytes 的位元組陣列中。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>還原序列化行為

將 JSON 還原序列化時，會套用下列行為：

::: zone pivot="dotnet-5-0"

* 依預設，屬性名稱比對會區分大小寫。 您可以 [指定不區分大小寫](#case-insensitive-property-matching)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。
* 序列化程式會忽略非公用的函式。
* 支援還原序列化至不可變的物件或唯讀屬性。 請參閱 [不可變的類型和記錄](#immutable-types-and-records)。
* 依預設，會將列舉支援為數字。 您可以將 [列舉名稱序列化為字串](#enums-as-strings)。
* 依預設，會忽略欄位。 您可以 [包含欄位](#include-fields)。
* 根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。 您可以 [允許批註和結尾的逗號](#allow-comments-and-trailing-commas)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 依預設，屬性名稱比對會區分大小寫。 您可以 [指定不區分大小寫](#case-insensitive-property-matching)。 ASP.NET Core apps [預設會指定不區分大小寫](#web-defaults-for-jsonserializeroptions)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。
* 無參數的函式（可以是公用、內部或私用）用於還原序列化。
* 不支援還原序列化為不可變的物件或唯讀屬性。
* 依預設，會將列舉支援為數字。 您可以將 [列舉名稱序列化為字串](#enums-as-strings)。
* 不支援欄位。
* 根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。 您可以 [允許批註和結尾的逗號](#allow-comments-and-trailing-commas)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](#web-defaults-for-jsonserializeroptions)。
::: zone-end

您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) ，以提供內建轉換器不支援的功能。

## <a name="serialize-to-formatted-json"></a>序列化為格式化的 JSON

若要整齊列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

以下是要序列化的範例型別，以及整齊列印的 JSON 輸出：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a>包含欄位

::: zone pivot="dotnet-5-0"
<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>當序列化或還原序列化時，請使用全域設定或[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)屬性來包含欄位，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

若要忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。
::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json在 .Net Core 3.1 中不支援欄位。 [自訂轉換器](system-text-json-converters-how-to.md) 可以提供這種功能。
::: zone-end

## <a name="customize-json-names-and-values"></a>自訂 JSON 名稱和值

根據預設，JSON 輸出中的屬性名稱和字典索引鍵不會變更，包括大小寫。 列舉值會以數位表示。 本節說明如何：

* [自訂個別的屬性名稱](#customize-individual-property-names)
* [將所有屬性名稱轉換成 camel 大小寫](#use-camel-case-for-all-json-property-names)
* [執行自訂屬性命名原則](#use-a-custom-json-property-naming-policy)
* [將字典索引鍵轉換成 camel 大小寫](#camel-case-dictionary-keys)
* [將列舉轉換為字串和 camel 大小寫](#enums-as-strings)

對於需要特殊處理 JSON 屬性名稱和值的其他情況，您可以 [執行自訂的轉換器](system-text-json-converters-how-to.md)。

### <a name="customize-individual-property-names"></a>自訂個別的屬性名稱

若要設定個別屬性的名稱，請使用 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 屬性。

以下是要序列化並產生 JSON 的範例類型：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

這個屬性所設定的屬性名稱：

* 適用于雙向的序列化和還原序列化。
* 優先于屬性命名原則。

### <a name="use-camel-case-for-all-json-property-names"></a>針對所有 JSON 屬性名稱使用 camel 大小寫

若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

以下是序列化和 JSON 輸出的範例類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Camel 案例屬性命名原則：

* 適用于序列化和還原序列化。
* 由屬性覆寫 `[JsonPropertyName]` 。 這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大寫字母的原因。

### <a name="use-a-custom-json-property-naming-policy"></a>使用自訂 JSON 屬性命名原則

若要使用自訂 JSON 屬性命名原則，請建立一個衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為命名原則類別的實例：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

以下是序列化和 JSON 輸出的範例類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

JSON 屬性命名原則：

* 適用于序列化和還原序列化。
* 由屬性覆寫 `[JsonPropertyName]` 。 這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是大寫的原因。

### <a name="camel-case-dictionary-keys"></a>Camel 案例字典索引鍵

如果要序列化之物件的屬性是型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。 若要這樣做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

使用名為的字典序列化 `TemperatureRanges` 具有索引鍵/值組的物件 `"ColdMinTemp", 20` ， `"HotMinTemp", 40` 將會產生如下列範例所示的 JSON 輸出：

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

字典索引鍵的 camel 大小寫命名原則僅適用于序列化。 如果您將字典還原序列化，即使您為指定，金鑰也會與 JSON 檔案相符 `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` 。

### <a name="enums-as-strings"></a>作為字串的列舉

根據預設，列舉會序列化為數字。 若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。

例如，假設您需要序列化具有列舉的下列類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

產生的 JSON 看起來如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

您也可以還原序列化列舉字串名稱，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a>略過屬性

依預設，所有公用屬性都會進行序列化。 如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。 本節說明如何忽略：

::: zone pivot="dotnet-5-0"

* [個別屬性](#ignore-individual-properties)
* [所有唯讀屬性](#ignore-all-read-only-properties)
* [所有 null 值屬性](#ignore-all-null-value-properties)
* [所有預設值屬性](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [個別屬性](#ignore-individual-properties)
* [所有唯讀屬性](#ignore-all-read-only-properties)
* [所有 null 值屬性](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a>略過個別屬性

若要忽略個別的屬性，請使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性。

以下是序列化和 JSON 輸出的範例類型：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
您可以藉由設定 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的屬性來指定條件排除 `Condition` 。 <xref:System.Text.Json.Serialization.JsonIgnoreCondition>列舉提供下列選項：

* `Always` -一律會忽略屬性。 如果未 `Condition` 指定，則會假設為這個選項。
* `Never` -無論 `DefaultIgnoreCondition` 、 `IgnoreReadOnlyProperties` 和全域設定為何，一律會將屬性序列化和還原序列化 `IgnoreReadOnlyFields` 。
* `WhenWritingDefault` -如果是參考型別或實值型別，則會忽略序列化的屬性 `null` `default` 。
* `WhenWritingNull` -如果是參考型別，則會忽略序列化的屬性 `null` 。

下列範例說明如何使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的 `Condition` 屬性：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a>忽略所有唯讀屬性

如果屬性包含公用 getter 而非公用 setter，則該屬性為唯讀。 若要在序列化時忽略所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

以下是序列化和 JSON 輸出的範例類型：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

此選項只適用于序列化。 在還原序列化期間，預設會忽略唯讀屬性。

::: zone pivot="dotnet-5-0"
此選項只適用于屬性。 若要在序列化 [欄位](#include-fields)時忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。
::: zone-end

### <a name="ignore-all-null-value-properties"></a>忽略所有 null 值屬性

::: zone pivot="dotnet-5-0"
若要忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
若要在序列化時忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

以下是序列化和 JSON 輸出的範例物件：

|屬性 |值  |
|---------|---------|
| 日期    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureCelsius| 25 |
| 摘要| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a>略過所有預設值屬性

::: zone pivot="dotnet-5-0"
若要避免在數值型別屬性中序列化預設值，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

這 `WhenWritingDefault` 項設定也會防止 null 值參考型別屬性的序列化。

::: zone pivot="dotnet-core-3-1"
沒有內建的方法可防止序列化 .NET Core 3.1 中具有值型別預設值的屬性 System.Text.Json 。
::: zone-end

## <a name="customize-character-encoding"></a>自訂字元編碼

根據預設，序列化程式會將所有非 ASCII 字元全部轉義。  也就是說，它會將它們取代 `\uxxxx` 為 `xxxx` 字元的 Unicode 代碼。  例如，如果將 `Summary` 屬性設定為斯拉夫жарко，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>將語言字元集序列化

若要將一或多個語言的字元集)  (s，而不進行任何轉義，請在建立實例時指定 [Unicode 範圍 () ](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

此程式碼不會將斯拉夫文或希臘文字元換成。 如果 `Summary` 屬性設定為斯拉夫жарко，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

若要在不經過轉義的情況下序列化所有語言集，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。

### <a name="serialize-specific-characters"></a>序列化特定字元

替代方法是指定您想要允許的個別字元，而不需要經過轉義。 下列範例只會將жарко的前兩個字元序列化：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

以下是上述程式碼所產生的 JSON 範例：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>序列化所有字元

若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> 相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼程式更寬鬆，可讓字元通過非重設密碼：
>
> * 它不會對 HTML 敏感的字元（例如、、和）進行換用 `<` `>` `&` `'` 。
> * 它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深度防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在 *字元集* 上所產生的。
>
> 只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。 例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。 絕不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。

## <a name="serialize-properties-of-derived-classes"></a>序列化衍生類別的屬性

不支援多型類型階層的序列化。 例如，如果屬性定義為介面或抽象類別，則只有在介面或抽象類別上定義的屬性會序列化，即使執行時間型別具有其他屬性也一樣。 本節將說明此行為的例外狀況。

例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

並假設在編譯時期，方法的型別引數 `Serialize` 是 `WeatherForecast` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

在此案例中， `WindSpeed` 即使物件實際上是物件，也不會序列化屬性 `weatherForecast` `WeatherForecastDerived` 。 只有基類屬性會序列化：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

這項行為旨在協助防止在衍生的執行時間建立型別中意外曝光資料。

若要序列化上述範例中衍生類型的屬性，請使用下列其中一種方法：

* 呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定型別：

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* 宣告要序列化為的物件 `object` 。

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> 這些方法只會針對要序列化的根物件提供多型的序列化，而不是針對該根物件的屬性提供。

如果您將物件定義為類型，則可以取得較低層級物件的多型序列化 `object` 。 例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，該屬性可以定義為類型 `WeatherForecast` 或 `object` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：

* 序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包括在內** `WindSpeed` 。
* 序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。

若要序列化 `WeatherForecastWithPreviousAsObject` ，不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能是衍生類型的物件。 下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：

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

將屬性定義為 `object` 與介面搭配使用的相同方法。 假設您有下列介面和執行，而且您想要使用包含實實例的屬性來序列化類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

下列範例顯示上述程式碼所產生的 JSON：

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

如需多型序列化的詳細資訊，以及有關還原 **序列化** 的詳細 **資訊，請** 參閱 [如何從遷移 Newtonsoft.Json System.Text.Json 至](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。

## <a name="allow-comments-and-trailing-commas"></a>允許批註和尾端逗號

根據預設，JSON 中不允許批註和結尾的逗號。 若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。
若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。 下列範例顯示如何允許兩者：

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

以下是包含批註和尾端逗號的範例 JSON：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>不區分大小寫的屬性比對

根據預設，還原序列化會尋找 JSON 與目標物件屬性之間是否有區分大小寫的屬性名稱相符專案。 若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

以下是使用 camel 大小寫屬性名稱的範例 JSON。 您可以將它還原序列化為具有 Pascal 案例屬性名稱的下列型別。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>處理溢位 JSON

還原序列化時，您可能會收到 JSON 中的資料，而該資料不是由目標型別的屬性所表示。 例如，假設您的目標型別是：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

而且要還原序列化的 JSON 如下所示：

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

如果您將顯示的 JSON 還原序列化為顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。 若要捕獲額外的資料（例如這些屬性），請將 [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 屬性套用至類型或的屬性 `Dictionary<string,object>` `Dictionary<string,JsonElement>` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：

|屬性 |值  |注意  |
|---------|---------|---------|
| 日期    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureCelsius| 0 | JSON)  (區分大小寫不符 `temperatureCelsius` ，因此未設定屬性。 |
| 摘要 | 經常性存取層 ||
| ExtensionData | temperatureCelsius：25 |因為大小寫不相符，所以這個 JSON 屬性是一個額外的，並且會成為字典中的索引鍵/值組。|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。|
| |SummaryWords:<br>非經常性<br>風<br>潮濕 |JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。|

序列化目標物件時，擴充功能資料索引鍵值組會變成 JSON 屬性，就像在傳入的 JSON 中一樣：

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

請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。 此行為可讓 JSON 進行往返，而不會遺失任何額外的資料，否則不會還原序列化。

## <a name="preserve-references-and-handle-circular-references"></a>保留參考並處理迴圈參考

::: zone pivot="dotnet-5-0"

若要保留參考並處理迴圈參考，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。 這項設定會導致下列行為：

* 序列化時：

  撰寫複雜型別時，序列化程式也會將中繼資料屬性寫入 (`$id` 、 `$values` 和 `$ref`) 。

* 還原序列化時：

  雖然不是必要的) ，但還原序列化程式會嘗試瞭解中繼資料，但 (的預期。

下列程式碼說明如何使用此 `Preserve` 設定。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

這項功能不能用來保留實數值型別或不可變的類型。 在還原序列化時，會在讀取整個裝載之後，建立不可變型別的實例。 因此，如果它的參考出現在 JSON 承載內，就不可能還原序列化相同的實例。

如果是實值型別、不可變的型別和陣列，則不會序列化任何參考中繼資料。 在還原序列化時，如果找到或，則會擲回例外狀況 `$ref` `$id` 。 不過，實值型別 `$id` 會忽略 (，而 `$values` 在集合的情況下) ，讓您可以還原序列化使用序列化的承載 Newtonsoft.Json 。  Newtonsoft.Json 會序列化這類類型的中繼資料。

若要判斷物件是否相等， System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> 請使用，它會使用參考相等 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) 而不是 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 在比較兩個物件實例時 (值相等。

如需如何序列化和還原序列化參考的詳細資訊，請參閱 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> 。

<xref:System.Text.Json.Serialization.ReferenceResolver>類別會定義在序列化和還原序列化時保留參考的行為。 建立衍生類別以指定自訂行為。 如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a>以引號允許或寫入數位

::: zone pivot="dotnet-5-0"

某些序列化程式會將數位編碼為 JSON 字串， (以引號括住) 。 例如： `{"DegreesCelsius":"23"}` 而不是 `{"DegreesCelsius":23}` 。 若要序列化引號中的數位，或在整個輸入物件圖形中接受以引號括住的數位，請設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

當您 System.Text.Json 透過 ASP.NET Core 間接使用時，當還原序列化時，會允許括住的數位，因為 ASP.NET Core 指定 [web 預設選項](xref:System.Text.Json.JsonSerializerDefaults.Web)。

若要允許或寫入特定屬性、欄位或類型的引號號碼，請使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。
::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json 在 .NET Core 3.1 中，不支援序列化或還原序列化以引號括住的數位。 如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)住的數位。
::: zone-end

## <a name="immutable-types-and-records"></a>不可變的類型和記錄

::: zone pivot="dotnet-5-0"
System.Text.Json 可以使用參數化的函式，讓您可以還原序列化不可變的類別或結構。 針對類別，如果唯一的函式是參數化的，則會使用該函數。 若為結構或具有多個函式的類別，請套用 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 屬性，以指定要使用的類別。 未使用屬性時，一律會使用公用無參數的函式（如果有的話）。 屬性只能搭配公用的函式使用。 下列範例會使用 `[JsonConstructor]` 屬性：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

也支援 c # 9 中的記錄，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

針對不可變的類型，因為其所有屬性 setter 都非公用，請參閱下一節有關 [非公用屬性存取](#non-public-property-accessors)子的資訊。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` 和 c # 9 記錄支援在 .NET Core 3.1 中無法使用。
::: zone-end

## <a name="non-public-property-accessors"></a>非公用屬性存取子

::: zone pivot="dotnet-5-0"
若要允許使用非公用屬性存取子，請使用 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 不支援非公用屬性存取子。 如需詳細資訊，請參閱「 [從 Newtonsoft.Json 文章遷移](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)」。
::: zone-end

## <a name="copy-jsonserializeroptions"></a>複製 JsonSerializerOptions

::: zone pivot="dotnet-5-0"
有 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerOptions) # A3，可讓您使用與現有實例相同的選項來建立新的實例，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonSerializerOptions`在 .Net Core 3.1 中無法使用採用現有實例的函式。
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>JsonSerializerOptions 的 Web 預設值

::: zone pivot="dotnet-5-0"
以下是針對 web 應用程式具有不同預設值的選項：

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

有一個 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerDefaults) ？ view = net-5.0&preserve-view = true) 可讓您建立新的實例，其中包含 ASP.NET Core 用於 web 應用程式的預設選項，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
以下是針對 web 應用程式具有不同預設值的選項：

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

`JsonSerializerOptions`指定一組預設值的函式在 .Net Core 3.1 中無法使用。
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>HttpClient 和 HttpContent 擴充方法

::: zone pivot="dotnet-5-0"

從網路序列化和還原序列化 JSON 承載是常見的作業。 [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions)和[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)上的擴充方法可讓您在一行程式碼中進行這些作業。 這些擴充方法會使用 [web 預設值進行 JsonSerializerOptions](#web-defaults-for-jsonserializeroptions)。

下列範例說明如何使用 <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> ：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

此外，也有適用 System.Text.Json 于 [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)的擴充方法。
::: zone-end

::: zone pivot="dotnet-core-3-1"
和上的擴充方法在 `HttpClient` `HttpContent` System.Text.Json .net Core 3.1 中無法使用。
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader、Utf8JsonWriter 和 JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。 `Utf8JsonReader`是低層級的型別，可用來建立自訂剖析器和還原序列化程式。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonReader` 幕後。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（如、和）撰寫 UTF-8 編碼的 JSON 文字 `String` `Int32` `DateTime` 。 寫入器是一種低層級的型別，可用來建立自訂序列化程式。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonWriter` 幕後。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用建立唯讀檔案物件模型 (DOM) 的功能 `Utf8JsonReader` 。 DOM 提供 JSON 承載中資料的隨機存取。 撰寫承載的 JSON 專案可以透過型別存取 <xref:System.Text.Json.JsonElement> 。 此 `JsonElement` 類型提供陣列和物件列舉值以及 api，以將 JSON 文字轉換成常見的 .net 類型。 `JsonDocument` 公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。

下列各節說明如何使用這些工具來讀取和寫入 JSON。

## <a name="use-jsondocument-for-access-to-data"></a>使用 JsonDocument 存取資料

下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別，隨機存取 JSON 字串中的資料：

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

上述程式碼：

* 假設要分析的 JSON 是在名為的字串中 `jsonString` 。
* 計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。
* 針對沒有等級的學生指派預設等級70。
* 依每個反復專案遞增變數來計算學生數目 `count` 。 替代方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

以下是此程式碼處理的 JSON 範例：

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>使用 JsonDocument 撰寫 JSON

下列範例顯示如何從撰寫 JSON <xref:System.Text.Json.JsonDocument> ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

上述程式碼：

* 讀取 JSON 檔案、將資料載入中 `JsonDocument` ，然後將格式化 (美觀的) JSON 寫入檔案。
* 使用 <xref:System.Text.Json.JsonDocumentOptions> 指定允許但忽略輸入 JSON 中的批註。
* 完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。 替代方法是讓寫入器在處置時 autoflush。

以下是範例程式碼要處理的 JSON 輸入範例：

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

結果會是下列整齊列印的 JSON 輸出：

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>使用 Utf8JsonWriter

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>使用 Utf8JsonReader

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

上述程式碼假設 `jsonUtf8` 變數是一個位元組陣列，其中包含編碼為 utf-8 的有效 JSON。

### <a name="filter-data-using-utf8jsonreader"></a>使用 Utf8JsonReader 篩選資料

下列範例示範如何同步讀取檔案，並搜尋值。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

 ([此範例的非同步版本](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs) 可供使用。 ) 

上述程式碼：

* 假設 JSON 包含物件的陣列，而且每個物件都可以包含字串類型的 "name" 屬性。
* 計算以 "大學" 結尾的物件和 "name" 屬性值。
* 假設檔案是以 UTF-16 編碼，並將它轉碼為 UTF-8。 您可以 `ReadOnlySpan<byte>` 使用下列程式碼，將編碼為 utf-8 的檔案直接讀入中：

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  如果檔案包含 UTF-8 位元組順序標記 (BOM) ，請先將其移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器預期文字。 否則，會將 BOM 視為不正確 JSON，而讀取器會擲回例外狀況。

以下是上述程式碼可以讀取的 JSON 範例。 產生的摘要訊息是「2個以上的名稱的結尾是 ' 大學 '」：

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>使用 Utf8JsonReader 從串流讀取

當讀取大型檔案 (gb 或更大的大小時，例如) ，您可能會想要避免必須一次將整個檔案載入記憶體中。 在此案例中，您可以使用 <xref:System.IO.FileStream> 。

使用 `Utf8JsonReader` 從資料流程讀取時，適用下列規則：

* 包含部分 JSON 承載的緩衝區必須至少與它內最大的 JSON 權杖一樣大，讓讀取器可以進行向前的進度。
* 緩衝區至少必須和 JSON 內的最大泛空白字元順序一樣大。
* 讀取器不會追蹤已讀取的資料，直到它完全讀取 JSON 承載中的下一個 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> 。 因此，當緩衝區中有剩餘的位元組時，您必須再次將它們傳遞給讀取器。 您可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 來判斷剩餘的位元組數目。

下列程式碼說明如何從資料流程讀取。 此範例會顯示 <xref:System.IO.MemoryStream> 。 類似的程式碼可搭配使用 <xref:System.IO.FileStream> ，但在 `FileStream` 開始時包含 utf-8 BOM 時除外。 在這種情況下，您必須先從緩衝區中去除這三個位元組，再將剩餘的位元組傳遞給 `Utf8JsonReader` 。 否則，讀取器會擲回例外狀況，因為 BOM 不會被視為 JSON 的有效部分。

範例程式碼的開頭為 4 KB 的緩衝區，每次發現大小不夠大而無法容納完整的 JSON 權杖時，便會將緩衝區大小加倍，讓讀取器在 JSON 承載上進行向前處理。 只有當您設定非常小的初始緩衝區大小（例如10個位元組）時，程式碼片段中提供的 JSON 範例才會觸發緩衝區大小的增加。 如果您將初始緩衝區大小設定為10，則 `Console.WriteLine` 語句會說明緩衝區大小增加的原因和影響。 在 4 KB 的初始緩衝區大小中，會顯示整個範例 JSON `Console.WriteLine` ，而且永遠不需要增加緩衝區大小。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

先前的範例不會對緩衝區所能成長的大小設定限制。 如果權杖大小太大，程式碼可能會失敗併發生 <xref:System.OutOfMemoryException> 例外狀況。 如果 JSON 包含的權杖大約是 1 GB 或更大的大小，就會發生這種情況，因為 1 GB 的大小加倍會導致大小太大而無法放入 `int32` 緩衝區中。

## <a name="additional-resources"></a>其他資源

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何撰寫自訂轉換器](system-text-json-converters-how-to.md)
* [如何遷移 Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [中的 DateTime 和 DateTimeOffset 支援 System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
