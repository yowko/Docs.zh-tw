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
# <a name="how-to-serialize-json-in-net"></a>如何在 .NET 中序列化 JSON

> [!IMPORTANT]
> JSON 序列化檔集在結構中。 本文並未涵蓋所有案例。 如需詳細資訊，請檢查 GitHub 上 dotnet/corefx 存放庫中的[system.object 問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)，特別是標示為[Json 功能的](https://github.com/dotnet/corefx/labels/json-functionality-doc)檔。

本文說明如何使用命名空間， <xref:System.Text.Json>在 JavaScript 物件標記法（JSON）中進行序列化和還原序列化。 指示和範例程式碼會直接使用程式庫，而不是透過如[ASP.NET Core](/aspnet/core/)的架構。

## <a name="namespaces"></a>命名空間

<xref:System.Text.Json>命名空間包含所有進入點和主要類型。 <xref:System.Text.Json.Serialization>命名空間包含用於高階案例的屬性和 api，以及序列化和還原序列化特有的自訂。 因此，本文中顯示的程式碼範例需要下列`using`其中一個或兩個指示詞：

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

目前不支援<xref:System.Runtime.Serialization>命名空間中`System.Text.Json`的屬性。

## <a name="how-to-write-net-objects-to-json-serialize"></a>如何將 .NET 物件寫入 JSON （序列化）

若要將 JSON 寫入字串，請使用泛型型別參數或泛型型別推斷呼叫[JsonSerializer。序列化](xref:System.Text.Json.JsonSerializer.Serialize*)：

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

以下是要序列化的範例型別，其中包含集合和嵌套的類別：

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

預設會縮減 JSON 輸出： 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

下列範例顯示相同的 JSON （也就是使用空白字元和縮排進行整齊列印）：

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

的<xref:System.Text.Json.JsonSerializer.Serialize%2A>多載可讓您將<xref:System.IO.Stream>序列化為。 可以使用非同步版本`Stream`的多載。

### <a name="serialize-to-utf-8"></a>序列化為 UTF-8

呼叫[JsonSerializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*)：

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

或者， <xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用<xref:System.Text.Json.Utf8JsonWriter>接受的多載。

序列化為 UTF-8 的速度比使用以字串為基礎的方法快大約 5-10%。 差別在於，位元組（UTF-8）不需要轉換成字串（UTF-16）。

## <a name="default-serialization-behavior"></a>預設序列化行為

* 所有公用屬性都會序列化。 您可以[指定要排除的屬性](#exclude-properties)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 敏感字元，以及必須根據[JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)來進行轉義的字元進行轉義。
* JSON 為縮減。 您可以選擇性地[列印 JSON](#serialize-to-formatted-json)。
* JSON 名稱的大小寫符合 .NET 名稱。 您可以[自訂 JSON 名稱大小寫](#customize-json-names)。
* 偵測到[迴圈參考](https://github.com/dotnet/corefx/issues/38579)，並擲回例外狀況。
* 欄位已排除。

支援的類型包括：

* 對應至 JavaScript 基本專案的 .NET 基本專案，例如數數值型別、字串和布林值。
* 使用者定義的[簡單 CLR 物件（poco）](https://stackoverflow.com/questions/250001/poco-definition)。
* 一維和不規則陣列（`ArrayName[][]`）。
* `Dictionary<string,TValue>`其中`TValue`是`object` 、`JsonElement`或 POCO。
* 下列命名空間中的[集合類型](https://github.com/dotnet/corefx/issues/36643)：
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>如何將 JSON 讀入 .NET 物件（還原序列化）

若要從字串還原序列化，請呼叫[JsonSerializer。](xref:System.Text.Json.JsonSerializer.Deserialize*)還原序列化：

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

如需範例，請參閱[序列化](#how-to-write-net-objects-to-json-serialize)一節。 JSON 和 .NET 物件相同，但方向相反。

的<xref:System.Text.Json.JsonSerializer.Deserialize*>多載可讓您`Stream`從還原序列化。  可以使用非同步版本`Stream`的多載。

### <a name="deserialize-from-utf-8"></a>從 UTF-8 還原序列化

呼叫[JsonSerializer](xref:System.Text.Json.JsonSerializer.Deserialize*) `Utf8JsonReader`或使用或的`ReadOnlySpan<byte>`還原序列化多載：

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

## <a name="default-deserialization-behavior"></a>預設還原序列化行為

* 屬性名稱比對會區分大小寫。 您可以選擇性地指定不區分[大小寫](#case-insensitive-property-matching)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回任何例外狀況。
* 不支援在沒有無參數的函式的情況下還原序列化成參考型別。
* 不支援還原序列化為[不可變的物件](https://github.com/dotnet/corefx/issues/38569)或[唯讀屬性](https://github.com/dotnet/corefx/issues/38163)。
* 列舉是以數位的形式支援。
* 欄位不受支援。
* JSON 中的批註或尾端逗號會擲回例外狀況。 您可以[允許批註和尾端的逗號](#allow-comments-and-trailing-commas)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

## <a name="serialize-to-formatted-json"></a>序列化為格式化 JSON

設定<xref:System.Text.Json.JsonSerializerOptions.WriteIndented>為 true：

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是要序列化的範例型別和 JSON 輸出：

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

## <a name="allow-comments-and-trailing-commas"></a>允許批註和尾端逗號

將<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling>設定`JsonCommentHandling.Skip`為，並<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas>將設定為 true：

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

以下是包含批註和尾端逗號的範例 JSON：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a>自訂 JSON 名稱

本節說明如何：

* 自訂個別屬性名稱
* 將所有屬性名稱轉換成 camel 大小寫
* 執行自訂屬性命名原則
* 將字典索引鍵轉換成 camel 大小寫

不支援自動[將列舉轉換為 camel 案例](https://github.com/dotnet/corefx/issues/37725)。

### <a name="customize-individual-property-names"></a>自訂個別屬性名稱

若要設定個別屬性的名稱，請使用[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)屬性。

以下是要序列化和產生 JSON 的範例型別：

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

這個屬性所設定的屬性名稱：

* 雙向套用，用於序列化和還原序列化。
* 優先于屬性命名原則。

### <a name="use-camel-case-for-all-json-property-names"></a>所有 JSON 屬性名稱都使用 camel 大小寫

設定<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>為`JsonNamingPolicy.CamelCase`：

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是序列化和 JSON 輸出的範例類別：

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

Camel 案例屬性命名原則：

* 適用于序列化和還原序列化。
* 會由`[JsonPropertyName]`屬性覆寫。

### <a name="use-a-custom-json-property-naming-policy"></a>使用自訂 JSON 屬性命名原則

衍生自<xref:System.Text.Json.JsonNamingPolicy> ，並<xref:System.Text.Json.JsonNamingPolicy.ConvertName*>覆寫：

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

將<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>設定為您命名原則類別的實例：

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是序列化和 JSON 輸出的範例類別：

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

JSON 屬性命名原則：

* 適用于序列化和還原序列化。
* 會由`[JsonPropertyName]`屬性覆寫。

### <a name="camel-case-dictionary-keys"></a>Camel 大小寫字典索引鍵

如果要序列化之物件的屬性屬於型`Dictionary<string,Tvalue>`別，則`string`可以將索引鍵轉換成 camel 大小寫。 若要這麼做， <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy>請`JsonNamingPolicy.CamelCase`將設定為：

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是要序列化和 JSON 輸出的範例物件：

|屬性 |值  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| 總結| 熱|
| TemperatureRanges | 冷，20<br>熱門、40|

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

Camel 案例命名原則僅適用于序列化。

## <a name="exclude-properties"></a>排除屬性

本節說明如何排除：

* 個別屬性
* 所有唯讀屬性
* 所有 null 值屬性 

### <a name="exclude-individual-properties"></a>排除個別屬性

使用[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)屬性。

以下是要序列化和 JSON 輸出的範例型別：

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

### <a name="exclude-all-read-only-properties"></a>排除所有唯讀屬性

設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties>為 true：

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是要序列化和 JSON 輸出的範例型別：

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

此選項只適用于序列化。 在還原序列化期間，預設會忽略唯讀屬性。 如果屬性包含公用 getter，而不是公用 setter，則其為唯讀。

### <a name="exclude-all-null-value-properties"></a>排除所有 null 值屬性

設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>為 true：

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

以下是要序列化和 JSON 輸出的範例物件：

|屬性 |值  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| 總結| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

此設定適用于序列化和還原序列化。 在還原序列化期間，JSON 中的 null 值只有在有效的情況下才會被忽略。 [不可為 null 的實數值型別的 Null 值會造成例外](https://github.com/dotnet/corefx/issues/40922)狀況。

## <a name="case-insensitive-property-matching"></a>不區分大小寫的屬性比對

根據預設，還原序列化會在 JSON 與目標物件屬性之間尋找區分大小寫的屬性名稱是否相符。 若要變更該行為， <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive>請將設定為 true：

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

以下是使用 camel 案例屬性名稱的範例 JSON。 它可以還原序列化成具有 Pascal 案例屬性名稱的下列型別。

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

## <a name="include-properties-of-derived-classes"></a>包含衍生類別的屬性

當您在編譯時期指定要序列化的型別時，不支援多型序列化。 例如，假設您有一個`WeatherForecast`類別和一個衍生的類別： `WeatherForecastWithWind`

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

而且假設在編譯時期傳遞給或推斷`Serialize`的型別為： `WeatherForecast`

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

在此案例中， `WindSpeed`即使`weatherForecast`物件實際上`WeatherForecastWithWind`是物件，也不會序列化屬性。 只有基類屬性會序列化：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

這個行為的目的是協助防止在衍生的執行時間建立的類型中意外公開資料。

若要序列化衍生類型的屬性，請使用下列其中一種方法：

* `Serialize`呼叫的多載，可讓您在執行時間指定類型：

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* 宣告要序列化為`object`的物件。

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

在上述範例案例中，這兩種方法`WindSpeed`都會使屬性包含在 JSON 輸出中：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a>處理溢位 JSON

還原序列化時，您可能會收到 JSON 中不是由目標型別的屬性所表示的資料。 例如，假設您的目標型別為：

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

而要還原序列化的 JSON 則是：

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

如果您將顯示的 JSON 還原序列化為所顯示的`DatesAvailable`類型`SummaryWords` ，和屬性就不會有任何地方，而且會遺失。 若要捕捉額外的資料，例如這些屬性，請將[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)屬性套用至類型`Dictionary<string,object>`的`Dictionary<string,JsonElement>`屬性或：

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

當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成`ExtensionData`屬性的索引鍵/值組：

|屬性 |值  |注意  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureC| 0 | 區分大小寫不相符`temperatureC` （在 JSON 中），因此不會設定屬性。 |
| 總結 | 熱 ||
| ExtensionData | temperatureC:25 |因為大小寫不相符，所以這個 JSON 屬性會是額外的，而且會成為字典中的索引鍵/值組。|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。|
| |SummaryWords:<br>酷<br>風大<br>潮濕 |JSON 中的額外屬性會變成索引鍵/值組，並以陣列做為值物件。|

當目標物件序列化時，延伸模組資料索引鍵值組會變成 JSON 屬性，就像是傳入 JSON 中所示：

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

請注意， `ExtensionData`屬性名稱不會出現在 JSON 中。 這種行為可讓 JSON 進行來回行程，而不會遺失任何其他不會還原序列化的資料。

## <a name="use-utf8jsonwriter-directly"></a>直接使用 Utf8JsonWriter

下列範例顯示如何直接使用<xref:System.Text.Json.Utf8JsonWriter>類別。

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

## <a name="use-utf8jsonreader-directly"></a>直接使用 Utf8JsonReader

下列範例顯示如何直接使用<xref:System.Text.Json.Utf8JsonReader>類別。 此程式`jsonUtf8`代碼假設變數是包含有效 JSON 的位元組陣列，並以 utf-8 編碼。

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

## <a name="additional-resources"></a>其他資源

* [System.web. Text. Json 總覽](system-text-json-overview.md)
* [System.web API 參考](xref:System.Text.Json)
* [System.web 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
