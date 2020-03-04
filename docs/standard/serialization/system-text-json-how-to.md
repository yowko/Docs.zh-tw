---
title: 如何使用C# -.net 序列化和還原序列化 JSON
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8025f84f2425f5b91e08b28ddb24d105d8c4d1a3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159581"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>如何在 .NET 中序列化和還原序列化（封送處理和 unmarshal） JSON

本文說明如何使用 <xref:System.Text.Json> 命名空間，在 JavaScript 物件標記法（JSON）進行序列化和還原序列化。

指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。

大部分的序列化範例程式碼會將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true` 「美觀」的 JSON （以縮排和空白字元來進行人類可讀性）。 針對生產環境使用，您通常會接受此設定的預設值 `false`。

## <a name="namespaces"></a>命名空間

<xref:System.Text.Json> 命名空間包含所有進入點和主要類型。 <xref:System.Text.Json.Serialization> 命名空間包含用於高階案例的屬性和 Api，以及序列化和還原序列化特有的自訂。 本文中所示的程式碼範例需要其中一個或兩個命名空間的 `using` 指示詞：

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

`System.Text.Json`目前不支援來自 <xref:System.Runtime.Serialization> 命名空間的屬性。

## <a name="how-to-write-net-objects-to-json-serialize"></a>如何將 .NET 物件寫入 JSON （序列化）

若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。

下列範例會將 JSON 建立為字串：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

下列範例會使用同步程式碼來建立 JSON 檔案：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

下列範例會使用非同步程式碼來建立 JSON 檔案：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

上述範例會針對要序列化的型別使用型別推斷。 `Serialize()` 的多載會採用泛型型別參數：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>序列化範例

以下是包含集合和嵌套類別的範例類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

序列化上述型別之實例的 JSON 輸出如下列範例所示。 預設會縮減 JSON 輸出：

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

也可以使用接受 <xref:System.Text.Json.Utf8JsonWriter> 的 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 多載。

序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約5-10%。 差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。

## <a name="serialization-behavior"></a>序列化行為

* 預設會序列化所有公用屬性。 您可以[指定要排除的屬性](#exclude-properties-from-serialization)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行轉義的字元進行轉義。
* 根據預設，JSON 是縮減。 您可以[整齊列印 JSON](#serialize-to-formatted-json)。
* 根據預設，JSON 名稱的大小寫會符合 .NET 名稱。 您可以[自訂 JSON 名稱大小寫](#customize-json-names-and-values)。
* 偵測到迴圈參考，並擲回例外狀況。
* 目前已排除欄位。

支援的類型包括：

* 對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。
* 使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。
* 一維和不規則陣列（`ArrayName[][]`）。
* `Dictionary<string,TValue>`，其中 `TValue` 是 `object`、`JsonElement`或 POCO。
* 下列命名空間中的集合。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

您可以[執行自訂轉換器](system-text-json-converters-how-to.md)來處理其他類型，或提供內建轉換器不支援的功能。

## <a name="how-to-read-json-into-net-objects-deserialize"></a>如何將 JSON 讀入 .NET 物件（還原序列化）

若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。

下列範例會從字串讀取 JSON，並建立先前針對[序列化範例](#serialization-example)所顯示 `WeatherForecast` 類別的實例：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

若要使用同步程式碼從檔案還原序列化，請將檔案讀取到字串中，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>從 UTF-8 還原序列化

若要從 UTF-8 還原序列化，請呼叫採用 `Utf8JsonReader` 或 `ReadOnlySpan<byte>`的 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 多載，如下列範例所示。 這些範例假設 JSON 位於名為 jsonUtf8Bytes 的位元組陣列中。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>還原序列化行為

* 根據預設，屬性名稱比對會區分大小寫。 您可以[指定不區分大小寫](#case-insensitive-property-matching)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。
* 不支援在沒有無參數的函式的情況下還原序列化成參考型別。
* 不支援還原序列化為不可變的物件或唯讀屬性。
* 根據預設，列舉會當做數位來支援。 您可以將[列舉名稱序列化為字串](#enums-as-strings)。
* 欄位不受支援。
* 根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。 您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

您可以[執行自訂轉換器](system-text-json-converters-how-to.md)，以提供內建轉換器不支援的功能。

## <a name="serialize-to-formatted-json"></a>序列化為格式化 JSON

若要以整齊的格式列印 JSON 輸出，請將 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 設定為 `true`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

以下是要序列化的範例型別，以及相當列印的 JSON 輸出：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>自訂 JSON 名稱和值

根據預設，JSON 輸出中的屬性名稱和字典索引鍵是不變的，包括大小寫。 列舉值會以數位表示。 本節說明如何：

* [自訂個別屬性名稱](#customize-individual-property-names)
* [將所有屬性名稱轉換成 camel 大小寫](#use-camel-case-for-all-json-property-names)
* [執行自訂屬性命名原則](#use-a-custom-json-property-naming-policy)
* [將字典索引鍵轉換成 camel 大小寫](#camel-case-dictionary-keys)
* [將列舉轉換為字串和大小寫](#enums-as-strings)

針對需要對 JSON 屬性名稱和值進行特殊處理的其他案例，您可以[執行自訂轉換器](system-text-json-converters-how-to.md)。

### <a name="customize-individual-property-names"></a>自訂個別屬性名稱

若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。

以下是要序列化和產生 JSON 的範例型別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

這個屬性所設定的屬性名稱：

* 雙向套用，用於序列化和還原序列化。
* 優先于屬性命名原則。

### <a name="use-camel-case-for-all-json-property-names"></a>所有 JSON 屬性名稱都使用 camel 大小寫

若要對所有 JSON 屬性名稱使用 camel 大小寫，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

以下是序列化和 JSON 輸出的範例類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* 會由 `[JsonPropertyName]` 屬性來覆寫。 這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大小寫。

### <a name="use-a-custom-json-property-naming-policy"></a>使用自訂 JSON 屬性命名原則

若要使用自訂 JSON 屬性命名原則，請建立衍生自 <xref:System.Text.Json.JsonNamingPolicy> 的類別，並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為您命名原則類別的實例：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

以下是序列化和 JSON 輸出的範例類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* 會由 `[JsonPropertyName]` 屬性來覆寫。 這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不大寫的原因。

### <a name="camel-case-dictionary-keys"></a>Camel 大小寫字典索引鍵

如果要序列化之物件的屬性是 `Dictionary<string,TValue>`類型，則 `string` 索引鍵可以轉換成 camel 大小寫。 若要這麼做，請將 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 設定為 `JsonNamingPolicy.CamelCase`，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

使用名為 `TemperatureRanges` 的字典序列化物件，其中具有 `"ColdMinTemp", 20` 的索引鍵/值組，而 `"HotMinTemp", 40` 會產生如下列範例所示的 JSON 輸出：

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

字典索引鍵的 camel 大小寫命名原則僅適用于序列化。 如果您將字典還原序列化，則即使您指定 `DictionaryKeyPolicy`的 `JsonNamingPolicy.CamelCase`，索引鍵仍會符合 JSON 檔案。

### <a name="enums-as-strings"></a>做為字串的列舉

根據預設，列舉會序列化為數字。 若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter>。

例如，假設您需要序列化具有列舉的下列類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

如果摘要是 `Hot`，則序列化的 JSON 預設值為3：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

產生的 JSON 如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

列舉字串名稱也可以還原序列化，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>排除序列化的屬性

預設會序列化所有公用屬性。 如果您不想讓某些部分出現在 JSON 輸出中，您有數個選項。 本節說明如何排除：

* [個別屬性](#exclude-individual-properties)
* [所有唯讀屬性](#exclude-all-read-only-properties)
* [所有 null 值屬性](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>排除個別屬性

若要忽略個別屬性，請使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。

以下是要序列化和 JSON 輸出的範例型別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>排除所有唯讀屬性

如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。 若要排除所有唯讀屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

以下是要序列化和 JSON 輸出的範例型別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

此選項只適用于序列化。 在還原序列化期間，預設會忽略唯讀屬性。

### <a name="exclude-all-null-value-properties"></a>排除所有 null 值屬性

若要排除所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true`，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

以下是要序列化和 JSON 輸出的範例物件：

|屬性 |值  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureCelsius| 25 |
| 摘要| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

此設定適用于序列化和還原序列化。 如需其對還原序列化之影響的詳細資訊，請參閱[在還原序列化時忽略 null](#ignore-null-when-deserializing)。

## <a name="customize-character-encoding"></a>自訂字元編碼

根據預設，序列化程式會將所有非 ASCII 字元全部轉義。  也就是說，它會以 `\uxxxx` 取代它們，其中 `xxxx` 是字元的 Unicode 代碼。  例如，如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>序列化語言字元集

若要序列化一或多個語言的字元集而不進行轉義，請在建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>的實例時指定[Unicode 範圍](xref:System.Text.Unicode.UnicodeRanges)，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

這段程式碼不會將斯拉夫文或希臘文字元取消換用。 如果 `Summary` 屬性設定為 [斯拉夫жарко]，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

若要序列化所有語言集而不進行任何轉義，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>。

### <a name="serialize-specific-characters"></a>序列化特定字元

另一個替代方式是指定您想要允許通過的個別字元，而不會進行轉義。 下列範例只會序列化жарко的前兩個字元：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

以下是上述程式碼所產生的 JSON 範例：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>序列化所有字元

若要最小化進行的轉義，您可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> 相較于預設編碼器，`UnsafeRelaxedJsonEscaping` 編碼器更寬鬆，可讓字元通過非預設的傳遞：
>
> * 它不會將 HTML 敏感的字元（例如 `<`、`>`、`&`和 `'`）換用。
> * 它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深層防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在*字元集*上。
>
> 只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。 例如，如果伺服器正在傳送回應標頭 `Content-Type: application/json; charset=utf-8`，您可以使用它。 永遠不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。

## <a name="serialize-properties-of-derived-classes"></a>序列化衍生類別的屬性

不支援多型類型階層的序列化。 例如，如果屬性定義為介面或抽象類別，則即使執行時間類型有其他屬性，還是會序列化在介面或抽象類別上定義的屬性。 這一節將說明此行為的例外狀況。

例如，假設您有 `WeatherForecast` 類別和衍生類別 `WeatherForecastDerived`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

而且在編譯時期，假設 `Serialize` 方法的型別引數是 `WeatherForecast`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

在此案例中，即使 `weatherForecast` 物件實際上是 `WeatherForecastDerived` 物件，`WindSpeed` 屬性也不會序列化。 只有基類屬性會序列化：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。

若要在上述範例中序列化衍生型別的屬性，請使用下列其中一種方法：

* 呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 的多載，可讓您在執行時間指定類型：

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* 宣告要序列化為 `object`的物件。

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

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
> 這些方法只會針對要序列化的根物件提供多型序列化，而不是針對該根物件的屬性。

如果您將較低層級的物件定義為 `object`的類型，您就可以取得其多型序列化。 例如，假設您的 `WeatherForecast` 類別具有一個名為 `PreviousForecast` 的屬性，可以定義為 `WeatherForecast` 或 `object`的類型：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

如果 `PreviousForecast` 屬性包含 `WeatherForecastDerived`的實例：

* 序列化 `WeatherForecastWithPrevious` 的 JSON 輸出**不包含**`WindSpeed`。
* 序列化 `WeatherForecastWithPreviousAsObject` 的 JSON 輸出**包含**`WindSpeed`。

若要將 `WeatherForecastWithPreviousAsObject`序列化，則不需要呼叫 `Serialize<object>` 或 `GetType`，因為根物件不是可能屬於衍生類型的物件。 下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

上述程式碼會正確地將 `WeatherForecastWithPreviousAsObject`序列化：

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

將屬性定義為 `object` 與介面搭配使用的相同方法。 假設您有下列介面和實作為，而且您想要使用包含實作為實例的屬性來序列化類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

當您將 `Forecasts`的實例序列化時，只有 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 會定義為 `object`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

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

如需多型**序列化**的詳細資訊，以及還原序列化**的相關資訊**，請參閱[如何從 Newtonsoft 遷移至 system.object](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。

## <a name="allow-comments-and-trailing-commas"></a>允許批註和尾端逗號

根據預設，JSON 中不允許批註和尾端逗號。 若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設為 `JsonCommentHandling.Skip`。
若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設為 `true`。 下列範例顯示如何允許兩者：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

以下是包含批註和尾端逗號的範例 JSON：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>不區分大小寫的屬性比對

根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。 若要變更該行為，請將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 設定為 `true`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

以下是使用 camel 案例屬性名稱的範例 JSON。 它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>處理溢位 JSON

還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。 例如，假設您的目標型別為：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

而要還原序列化的 JSON 則是：

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

如果您將顯示的 JSON 還原序列化為所顯示的類型，`DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。 若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>`類型的屬性：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成 `ExtensionData` 屬性的機碼值組：

|屬性 |值  |注意  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureCelsius| 0 | 區分大小寫不相符（`temperatureCelsius` 在 JSON 中），因此不會設定屬性。 |
| 摘要 | 經常性存取 ||
| ExtensionData | temperatureCelsius：25 |因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。|
| |SummaryWords:<br>非經常性存取<br>風大<br>潮濕 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。|

當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：

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

請注意，`ExtensionData` 屬性名稱不會出現在 JSON 中。 這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。

## <a name="ignore-null-when-deserializing"></a>還原序列化時忽略 null

根據預設，如果 JSON 中的屬性是 null，則目標物件中的對應屬性會設定為 null。 在某些情況下，目標屬性可能會有預設值，而且您不想要 null 值來覆寫預設值。

例如，假設下列程式碼代表您的目標物件：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

假設下列 JSON 已還原序列化：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

還原序列化之後，`WeatherForecastWithDefault` 物件的 `Summary` 屬性為 null。

若要變更此行為，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 設定為 `true`，如下列範例所示：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

使用此選項時，`WeatherForecastWithDefault` 物件的 `Summary` 屬性是還原序列化後的預設值「沒有摘要」。

JSON 中的 Null 值只有在有效時才會被忽略。 不可為 null 的實數值型別的 Null 值會造成例外狀況。

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader、Utf8JsonWriter 和 JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從 `ReadOnlySpan<byte>` 或 `ReadOnlySequence<byte>`讀取。 `Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonReader`。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。 寫入器是可以用來建立自訂序列化程式的低層級類型。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法會使用幕後的 `Utf8JsonWriter`。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用 `Utf8JsonReader`建立唯讀檔案物件模型（DOM）的功能。 DOM 提供 JSON 承載中資料的隨機存取。 組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。 `JsonElement` 類型提供陣列和物件列舉值，以及用來將 JSON 文字轉換成常見 .NET 類型的 Api。 `JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。

下列各節說明如何使用這些工具來讀取和寫入 JSON。

## <a name="use-jsondocument-for-access-to-data"></a>使用 JsonDocument 存取資料

下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別來隨機存取 JSON 字串中的資料：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

上述程式碼：

* 假設要分析的 JSON 是在名為 `jsonString`的字串中。
* 計算 `Students` 陣列中具有 `Grade` 屬性之物件的平均等級。
* 為沒有成績的學生指派預設等級70。
* 藉由遞增 `count` 變數與每個反復專案來計算學生數目。 另一種方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A>，如下列範例所示：

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

以下是此程式碼所處理的 JSON 範例：

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>使用 JsonDocument 寫入 JSON

下列範例顯示如何從 <xref:System.Text.Json.JsonDocument>寫入 JSON：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

上述程式碼：

* 讀取 JSON 檔案、將資料載入 `JsonDocument`，並將格式化（已列印）的 JSON 寫入檔案。
* 會使用 <xref:System.Text.Json.JsonDocumentOptions> 來指定允許輸入 JSON 中的批註，但會忽略它。
* 完成時，會在寫入器上呼叫 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A>。 另一個替代方式是讓寫入器在處置時 autoflush。

以下是範例程式碼所要處理的 JSON 輸入範例：

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

結果會是下列整齊列印的 JSON 輸出：

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>使用 Utf8JsonWriter

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>使用 Utf8JsonReader

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

上述程式碼假設 `jsonUtf8` 變數是包含有效 JSON 的位元組陣列，並以 UTF-8 編碼。

### <a name="filter-data-using-utf8jsonreader"></a>使用 Utf8JsonReader 篩選資料

下列範例示範如何以同步方式讀取檔案，並搜尋值：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

上述程式碼：

* 假設 JSON 包含物件的陣列，而且每個物件都可以包含 string 類型的 "name" 屬性。
* 計算以 "大學" 結尾的物件和「名稱」屬性值。
* 假設檔案是以 UTF-16 編碼，並將其轉碼為 UTF-8。 您可以使用下列程式碼，直接將編碼為 UTF-8 的檔案讀入 `ReadOnlySpan<byte>`中：

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  如果檔案包含 UTF-8 位元組順序標記（BOM），請先將它移除，再將位元組傳遞給 `Utf8JsonReader`，因為讀取器需要文字。 否則，BOM 會被視為不正確 JSON，而讀取器會擲回例外狀況。

以下是上述程式碼可以讀取的 JSON 範例。 產生的摘要訊息為「2個以上的名稱，其結尾為 ' 大學 '」：

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>其他資源

* [System.Text.Json 總覽](system-text-json-overview.md)
* [如何撰寫自訂轉換器](system-text-json-converters-how-to.md)
* [如何從 Newtonsoft.Json 遷移](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.Json 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
