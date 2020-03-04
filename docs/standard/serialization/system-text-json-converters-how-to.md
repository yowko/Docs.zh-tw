---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 310967f39c3aa7a46d79087bcbf0cb016f7d7284
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159568"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>如何在 .NET 中撰寫 JSON 序列化（封送處理）的自訂轉換器

本文說明如何為 <xref:[!OP.NO-LOC(System.Text.Json)]> 命名空間中提供的 JSON 序列化類別建立自訂的轉換器。 如需 `[!OP.NO-LOC(System.Text.Json)]`的簡介，請參閱[如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。

*轉換器*是一個類別，可將物件或值轉換成 JSON。 針對對應至 JavaScript 基本類型的大部分基本型別，`[!OP.NO-LOC(System.Text.Json)]` 命名空間具有內建的轉換器。 您可以撰寫自訂轉換器：

* 覆寫內建轉換器的預設行為。 例如，您可能想要以 mm/dd/yyyy 格式來表示 `DateTime` 值，而不是預設的 ISO 8601-1:2019 格式。
* 支援自訂實值型別。 例如，`PhoneNumber` 結構。

您也可以撰寫自訂轉換器，使用目前版本中未包含的功能來自訂或擴充 `[!OP.NO-LOC(System.Text.Json)]`。 本文稍後會涵蓋下列案例：

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>範例 factory 模式切換器

下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器。 程式碼會遵循 factory 模式，因為第一個泛型型別參數是 `Enum`，而第二個是開啟的。 `CanConvert` 方法只會針對具有兩個泛型參數的 `Dictionary` 傳回 `true`，其中第一個是 `Enum` 型別。 內部轉換器會取得現有的轉換器，以處理在執行時間針對 `TValue`所提供的任何類型。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

上述程式碼與本文稍後的「[包含非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)」中所顯示的相同。

## <a name="steps-to-follow-the-basic-pattern"></a>遵循基本模式的步驟

下列步驟說明如何遵循基本模式來建立轉換器：

* 建立衍生自 <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601> 的類別，其中 `T` 是要序列化和還原序列化的類型。
* 覆寫 `Read` 方法，將內送 JSON 還原序列化，並將它轉換成類型 `T`。 使用傳遞至方法的 <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader> 來讀取 JSON。
* 覆寫 `Write` 方法，將 `T`類型的傳入物件序列化。 使用傳遞至方法的 <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> 來寫入 JSON。
* 只有在必要時，才覆寫 `CanConvert` 方法。 當要轉換的型別是 `T`型別時，預設的實值會傳回 `true`。 因此，只支援類型 `T` 的轉換器不需要覆寫此方法。 如需需要覆寫此方法之轉換器的範例，請參閱本文稍後[的多](#support-polymorphic-deserialization)型還原序列化一節。

您可以參考[內建的轉換器原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/)做為參考執行，以撰寫自訂的轉換器。

## <a name="steps-to-follow-the-factory-pattern"></a>遵循 factory 模式的步驟

下列步驟說明如何遵循 factory 模式來建立轉換器：

* 建立衍生自 <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory> 的類別。
* 當要轉換的型別是轉換器可以處理的類型時，覆寫 `CanConvert` 方法，使其傳回 true。 例如，如果轉換器適用于 `List<T>` 它可能只會處理 `List<int>`、`List<string>`和 `List<DateTime>`。
* 覆寫 `CreateConverter` 方法，以傳回將處理在執行時間所提供之類型轉換的轉換器類別實例。
* 建立 `CreateConverter` 方法具現化的轉換器類別。

開放式泛型需要 factory 模式，因為所有類型的物件來回轉換的程式碼都不相同。 舉例來說，開放式泛型型別的轉換器（例如`List<T>`）必須針對封閉式泛型型別（例如，`List<DateTime>`）建立轉換子，以供幕後使用。 必須撰寫程式碼，以處理轉換器可以處理的每個封閉式泛型型別。

`Enum` 類型類似于開放式泛型型別： `Enum` 的轉換器必須針對特定 `Enum` （例如，`WeekdaysEnum`）建立轉換器，以供幕後使用。

## <a name="error-handling"></a>錯誤處理

如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮在沒有訊息的情況下擲回 <xref:[!OP.NO-LOC(System.Text.Json)].JsonException>。 此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。 例如，語句 `throw new JsonException();` 會產生類似下列範例的錯誤訊息：

```
Unhandled exception. [!OP.NO-LOC(System.Text.Json)].JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

如果您提供訊息（例如 `throw new JsonException("Error occurred")`，例外狀況仍然會在 <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path> 屬性中提供路徑。

## <a name="register-a-custom-converter"></a>註冊自訂轉換器

*註冊*自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。 選擇下列其中一種方法：

* 將轉換器類別的實例加入至 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。
* 將[[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute)屬性套用至需要自訂轉換器的屬性。
* 將[[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute)屬性套用至代表自訂實數值型別的類別或結構。

## <a name="registration-sample---converters-collection"></a>註冊範例-轉換器集合

以下範例會讓 <xref:System.ComponentModel.DateTimeOffsetConverter> <xref:System.DateTimeOffset>類型的屬性的預設值：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

假設您將下列類型的實例序列化：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

以下是顯示使用自訂轉換器的 JSON 輸出範例：

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

下列程式碼會使用相同的方法，以使用自訂 `DateTimeOffset` 轉換器進行還原序列化：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>註冊範例-屬性上的 [JsonConverter]

下列程式碼會選取 `Date` 屬性的自訂轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

序列化 `WeatherForecastWithConverterAttribute` 的程式碼不需要使用 `JsonSerializeOptions.Converters`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

要還原序列化的程式碼也不需要使用 `Converters`：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>註冊範例-類型上的 [JsonConverter]

以下程式碼會建立結構，並將 `[JsonConverter]` 屬性套用至它：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

以下是上述結構的自訂轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

結構上的 `[JsonConvert]` 屬性會註冊自訂轉換器，做為 `Temperature`類型屬性的預設值。 當您序列化或還原序列化時，轉換器會自動用於下列類型的 `TemperatureCelsius` 屬性：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>轉換器註冊優先順序

在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序列到最低：

* 套用至屬性的 `[JsonConverter]`。
* 已新增至 `Converters` 集合的轉換器。
* `[JsonConverter]` 套用至自訂實數值型別或 POCO。

如果類型的多個自訂轉換器已在 `Converters` 集合中註冊，則會使用針對 `CanConvert` 傳回 true 的第一個轉換器。

只有在未註冊適用的自訂轉換器時，才會選擇內建的轉換器。

## <a name="converter-samples-for-common-scenarios"></a>常見案例的轉換子範例

下列各節提供的轉換器範例可解決一些內建功能無法處理的常見案例。

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)
* [支援具有非字串索引鍵的字典](#support-dictionary-with-non-string-key)
* [支援多型還原序列化](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a>將推斷的類型還原序列化為物件屬性

當還原序列化為 `object`類型的屬性時，會建立 `JsonElement` 物件。 原因是還原序列化程式不知道要建立什麼 CLR 型別，而且也不會嘗試猜到。 例如，如果 JSON 屬性具有 "true"，則還原序列化程式並不會推斷值為 `Boolean`，如果元素具有 "01/01/2019"，則還原序列化程式不會推斷它是 `DateTime`。

型別推斷可能不正確。 如果還原序列化程式會剖析沒有小數點的 JSON 數位做為 `long`，如果值原本序列化為 `ulong` 或 `BigInteger`，可能會導致超出範圍的問題。 如果數位原本序列化為 `decimal`，則剖析具有小數點做為 `double` 的數位可能會失去精確度。

針對需要型別推斷的案例，下列程式碼會顯示 `object` 屬性的自訂轉換器。 程式碼會轉換：

* `true` 和 `false` 至 `Boolean`
* 不含小數的數位以 `long`
* 包含小數的數位以 `double`
* 要 `DateTime` 的日期
* 要 `string` 的字串
* `JsonElement` 的其他專案

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

下列程式碼會註冊轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

以下是具有 `object` 屬性的範例型別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime`、`long`和 `string`的值：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

如果沒有自訂轉換器，還原序列化會將 `JsonElement` 放入每個屬性中。

`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)，有更多自訂轉換器的範例，可處理還原序列化為 `object` 屬性。

### <a name="support-dictionary-with-non-string-key"></a>支援具有非字串索引鍵的字典

字典集合的內建支援適用于 `Dictionary<string, TValue>`。 也就是，索引鍵必須是字串。 若要支援具有整數或其他類型做為索引鍵的字典，則需要自訂轉換子。

下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

下列程式碼會註冊轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

轉換器可以序列化和還原序列化下列類別中使用下列 `Enum`的 `TemperatureRanges` 屬性：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

序列化的 JSON 輸出如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)，有更多可處理非字串索引鍵字典的自訂轉換器範例。

### <a name="support-polymorphic-deserialization"></a>支援多型還原序列化

內建功能提供有限範圍的多型[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)，但完全不支援還原序列化。 還原序列化需要自訂的轉換器。

例如，假設您有一個 `Person` 的抽象基類，`Employee` 和 `Customer` 衍生的類別。 多型還原序列化表示在設計階段，您可以指定 `Person` 做為還原序列化目標，而且 JSON 中的 `Customer` 和 `Employee` 物件會在執行時間正確地還原序列化。 在還原序列化期間，您必須尋找識別 JSON 中所需類型的線索。 可用的線索種類會因每個案例而異。 例如，鑒別子屬性可能可供使用，或者您可能必須依賴特定屬性的存在與否。 目前的 `System.Text.Json` 版本並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂轉換器。

下列程式碼顯示基類、兩個衍生類別和自訂的轉換器。 轉換器會使用鑒別子屬性來執行多型還原序列化。 類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

下列程式碼會註冊轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

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

前述範例中的轉換器程式碼會以手動方式讀取和寫入每個屬性。 另一種方法是呼叫 `Deserialize` 或 `Serialize` 來執行一些工作。 如需範例，請參閱[這 StackOverflow 文章](https://stackoverflow.com/a/59744873/12509023)。

## <a name="other-custom-converter-samples"></a>其他自訂轉換器範例

[從 Newtonsoft.Json 遷移至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)文章包含自訂轉換器的其他範例。

`System.Text.Json.Serialization` 原始程式碼中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)包含其他自訂轉換器範例，例如：

* [在還原序列化時，將 null 轉換為0的 Int32 轉換子](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Int32 轉換器，可在還原序列化時同時允許字串和數位值](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [列舉轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [列出接受外部資料的\<T > 轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] 轉換器，適用于以逗號分隔的數位清單](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

如果您需要建立可修改現有內建轉換器行為的轉換器，您可以取得[現有轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)，做為自訂的起點。

## <a name="additional-resources"></a>其他資源

* [內建轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [System.Text.Json 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json 總覽](system-text-json-overview.md)
* [如何使用 System.Text.Json](system-text-json-how-to.md)
* [如何從 Newtonsoft.Json 遷移](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json。序列化 API 參考](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
