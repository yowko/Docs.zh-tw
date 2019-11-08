---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741889"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>如何在 .NET 中撰寫 JSON 序列化的自訂轉換器

本文說明如何為 <xref:System.Text.Json> 命名空間中提供的 JSON 序列化類別建立自訂的轉換器。 如需 `System.Text.Json`的簡介，請參閱[如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。

*轉換器*是一個類別，可將物件或值轉換成 JSON。 針對對應至 JavaScript 基本類型的大部分基本型別，`System.Text.Json` 命名空間具有內建的轉換器。 您可以撰寫自訂轉換器：

* 覆寫內建轉換器的預設行為。 例如，您可能想要以 mm/dd/yyyy 格式來表示 `DateTime` 值，而不是預設的 ISO 8601-1:2019 格式。
* 支援自訂實值型別。 例如，`PhoneNumber` 結構。

您也可以撰寫自訂轉換器，使用目前版本中未包含的功能來擴充 `System.Text.Json`。 本文稍後會涵蓋下列案例：

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。
* [支援具有非字串索引鍵的字典](#support-dictionary-with-non-string-key)。
* [支援](#support-polymorphic-deserialization)多型還原序列化。

## <a name="custom-converter-patterns"></a>自訂轉換器模式

建立自訂轉換器的模式有兩種：基本模式和 factory 模式。 Factory 模式適用于處理類型 `Enum` 或開放式泛型的轉換器。 基本模式適用于非泛型和封閉式泛型型別。  例如，下列類型的轉換器需要 factory 模式：

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

基本模式可以處理的一些類型範例包括：

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

基本模式會建立可處理一種類型的類別。 Factory 模式會建立一個類別，它會在執行時間決定需要哪一個特定型別，並以動態方式建立適當的轉換器。

## <a name="sample-basic-converter"></a>範例基本轉換器

下列範例是覆寫現有資料類型之預設序列化的轉換器。 轉換器會針對 `DateTimeOffset` 屬性使用 mm/dd/yyyy 格式。

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a>範例 factory 模式切換器

下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器。 程式碼會遵循 factory 模式，因為第一個泛型型別參數是 `Enum`，而第二個是開啟的。 `CanConvert` 方法只會針對具有兩個泛型參數的 `Dictionary` 傳回 `true`，其中第一個是 `Enum` 型別。 內部轉換器會取得現有的轉換器，以處理在執行時間針對 `TValue`所提供的任何類型。 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

上述程式碼與本文稍後的「[包含非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)」中所顯示的相同。

## <a name="steps-to-follow-the-basic-pattern"></a>遵循基本模式的步驟

下列步驟說明如何遵循基本模式來建立轉換器：

* 建立衍生自 <xref:System.Text.Json.Serialization.JsonConverter%601> 的類別，其中 `T` 是要序列化和還原序列化的類型。
* 覆寫 `Read` 方法，將內送 JSON 還原序列化，並將它轉換成類型 `T`。 使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonReader> 來讀取 JSON。
* 覆寫 `Write` 方法，將 `T`類型的傳入物件序列化。 使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonWriter> 來寫入 JSON。
* 只有在必要時，才覆寫 `CanConvert` 方法。 當要轉換的型別是 `T`型別時，預設的實值會傳回 `true`。 因此，只支援類型 `T` 的轉換器不需要覆寫此方法。 如需需要覆寫此方法之轉換器的範例，請參閱本文稍後[的多](#support-polymorphic-deserialization)型還原序列化一節。

您可以參考[內建的轉換器原始程式碼](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)做為參考執行，以撰寫自訂的轉換器。

## <a name="steps-to-follow-the-factory-pattern"></a>遵循 factory 模式的步驟

下列步驟說明如何遵循 factory 模式來建立轉換器：

* 建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。
* 當要轉換的型別是轉換器可以處理的類型時，覆寫 `CanConvert` 方法，使其傳回 true。 例如，如果轉換器適用于 `List<T>` 它可能只會處理 `List<int>`、`List<string>`和 `List<DateTime>`。 
* 覆寫 `CreateConverter` 方法，以傳回將處理在執行時間所提供之類型轉換的轉換器類別實例。
* 建立 `CreateConverter` 方法具現化的轉換器類別。 

開放式泛型需要 factory 模式，因為所有類型的物件來回轉換的程式碼都不相同。 舉例來說，開放式泛型型別的轉換器（例如`List<T>`）必須針對封閉式泛型型別（例如，`List<DateTime>`）建立轉換子，以供幕後使用。 必須撰寫程式碼，以處理轉換器可以處理的每個封閉式泛型型別。

`Enum` 類型類似于開放式泛型型別： `Enum` 的轉換器必須針對特定 `Enum` （例如，`WeekdaysEnum`）建立轉換器，以供幕後使用。 

## <a name="error-handling"></a>錯誤處理

如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮在沒有訊息的情況下擲回 <xref:System.Text.Json.JsonException>。 此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。 例如，語句 `throw new JsonException();` 會產生類似下列範例的錯誤訊息：

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

如果您提供訊息（例如 `throw new JsonException("Error occurred)`，例外狀況仍然會在 <xref:System.Text.Json.JsonException.Path> 屬性中提供路徑。

## <a name="register-a-custom-converter"></a>註冊自訂轉換器

*註冊*自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。 選擇下列其中一種方法：

* 將轉換器類別的實例加入至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。
* 將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至需要自訂轉換器的屬性。
* 將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至代表自訂實數值型別的類別或結構。

## <a name="registration-sample---converters-collection"></a>註冊範例-轉換器集合 

以下範例會讓 `ExampleDateTimeOffsetConverter` `DateTimeOffset`類型的屬性的預設值：

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

假設您將下列型別序列化：

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

以下是顯示使用自訂轉換器的 JSON 輸出範例：

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

下列程式碼會使用相同的方法，以使用自訂 `DateTimeOffset` 轉換器進行還原序列化：

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a>註冊範例-屬性上的 [JsonConverter]

下列程式碼會選取 `Date` 屬性的自訂轉換器：

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

序列化和還原序列化 `WeatherForecastWithConverter` 的程式碼不需要使用 `JsonSerializeOptions.Converters`：

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a>註冊範例-類型上的 [JsonConverter]

以下程式碼會建立結構，並將 `[JsonConverter]` 屬性套用至它：

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

以下是上述結構的自訂轉換器：

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

結構上的 `[JsonConvert]` 屬性會註冊自訂轉換器，做為 `Temperature`類型屬性的預設值。 當您序列化或還原序列化時，轉換器會自動用於下列類型的 `TemperatureC` 屬性：

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a>轉換器註冊優先順序

在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序列到最低：

* 套用至屬性的 `[JsonConverter]`。
* 已新增至 `Converters` 集合的轉換器。
* `[JsonConverter]` 套用至自訂實數值型別或 POCO。

如果類型的多個自訂轉換器已在 `Converters` 集合中註冊，則會使用針對 `CanConvert` 傳回 true 的第一個轉換器。

只有在未註冊適用的自訂轉換器時，才會選擇內建的轉換器。

## <a name="converter-samples-for-common-scenarios"></a>常見案例的轉換子範例

下列各節提供的轉換器範例可解決一些內建功能無法處理的常見案例。

### <a name="deserialize-inferred-types-to-object-properties"></a>將推斷的類型還原序列化為物件屬性

當還原序列化為 `Object`類型的屬性時，會建立 `JsonElement` 物件。 原因是還原序列化程式不知道要建立什麼 CLR 型別，而且也不會嘗試猜到。 例如，如果 JSON 屬性具有 "true"，則還原序列化程式並不會推斷值為 `Boolean`，如果元素具有 "01/01/2019"，則還原序列化程式不會推斷它是 `DateTime`。

型別推斷可能不正確。 如果還原序列化程式會剖析沒有小數點的 JSON 數位做為 `long`，如果值原本序列化為 `ulong` 或 `BigInteger`，可能會導致超出範圍的問題。 如果數位原本序列化為 `decimal`，則剖析具有小數點做為 `double` 的數位可能會失去精確度。

針對需要型別推斷的案例，下列程式碼會顯示 `Object` 屬性的自訂轉換器。 程式碼會轉換：

* `true` 和 `false` 至 `Boolean`
* 要 `long` 或 `double` 的數位
* 要 `DateTime` 的日期
* 要 `string` 的字串
* `JsonElement` 的其他專案

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

下列程式碼會註冊轉換器：

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

以下是具有物件屬性的範例型別：

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime`、`long`和 `string`的值：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

如果沒有自訂轉換器，還原序列化會將 `JsonElement` 放入每個屬性中。

`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多範例可處理還原序列化為物件屬性的自訂轉換器。

### <a name="support-dictionary-with-non-string-key"></a>支援具有非字串索引鍵的字典

字典集合的內建支援適用于 `Dictionary<string, TValue>`。 也就是，索引鍵必須是字串。 若要支援具有整數或其他類型做為索引鍵的字典，則需要自訂轉換子。

下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器：

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

下列程式碼會註冊轉換器：

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

轉換器可以序列化和還原序列化下列類別中使用下列 `Enum`的 `TemperatureRanges` 屬性：

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

序列化的 JSON 輸出如下列範例所示：

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多可處理非字串索引鍵字典的自訂轉換器範例。

### <a name="support-polymorphic-deserialization"></a>支援多型還原序列化

多型[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)不需要自訂轉換器，但是還原序列化的確需要自訂轉換器。

例如，假設您有一個 `Person` 的抽象基類，`Employee` 和 `Customer` 衍生的類別。 多型還原序列化表示在設計階段，您可以指定 `Person` 做為還原序列化目標，而且 JSON 中的 `Customer` 和 `Employee` 物件會在執行時間正確地還原序列化。 在還原序列化期間，您必須尋找識別 JSON 中所需類型的線索。 可用的線索種類會因每個案例而異。 例如，鑒別子屬性可能可供使用，或者您可能必須依賴特定屬性的存在與否。 目前的 `System.Text.Json` 版本並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂轉換器。

下列程式碼顯示基類、兩個衍生類別和自訂的轉換器。 轉換器會使用鑒別子屬性來執行多型還原序列化。 類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

下列程式碼會註冊轉換器：

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

轉換器可以還原序列化使用相同的轉換子所建立的 JSON，例如：

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a>其他自訂轉換器範例

`System.Text.Json.Serialization` 原始程式碼中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)包含其他自訂轉換器範例，例如：

* 在還原序列化時，將 null 轉換為0的 `Int32` 轉換器
* 在還原序列化時允許字串和數值的 `Int32` 轉換器
* `Enum` 轉換器
* 接受外部資料的 `List<T>` 轉換器
* 可搭配以逗號分隔的數位清單使用的 `Long[]` 轉換器 

## <a name="additional-resources"></a>其他資源

* [System.web. Text. Json 總覽](system-text-json-overview.md)
* [System.web API 參考](xref:System.Text.Json)
* [如何使用 System.object](system-text-json-how-to.md)
* [內建轉換器的原始程式碼](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* `System.Text.Json` 自訂轉換器的相關 GitHub 問題
  * [36639引進自訂轉換器](https://github.com/dotnet/corefx/issues/36639)
  * [38713關於還原序列化為物件](https://github.com/dotnet/corefx/issues/38713)
  * [40120有關非字串索引鍵的字典](https://github.com/dotnet/corefx/issues/40120)
  * [37787關於多型還原序列化](https://github.com/dotnet/corefx/issues/37787)
