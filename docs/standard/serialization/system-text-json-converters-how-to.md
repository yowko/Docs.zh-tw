---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
description: 瞭解如何針對命名空間中提供的 JSON 序列化類別，建立自訂的轉換器 System.Text.Json 。
ms.date: 12/14/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 390438e3dca7a5d40dd9957090f498b495996e05
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513194"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>如何在 .NET 中撰寫 JSON 序列化的自訂轉換器 (封送處理) 

本文說明如何為命名空間中提供的 JSON 序列化類別，建立自訂的轉換器 <xref:System.Text.Json> 。 如需的簡介 `System.Text.Json` ，請參閱 [如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。

*轉換器* 是一種類別，可將物件或值轉換為 JSON。 `System.Text.Json`命名空間具有適用于大部分對應至 JavaScript 基本類型之基本類型的內建轉換器。 您可以撰寫自訂轉換器：

* 覆寫內建轉換器的預設行為。 例如，您可能想要 `DateTime` 以 mm/dd/yyyy 格式表示值。 根據預設，支援 ISO 8601-1:2019，包括 RFC 3339 設定檔。 如需詳細資訊，請參閱[中 System.Text.Json 的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)。
* 支援自訂實值型別。 例如， `PhoneNumber` 結構。

您也可以撰寫自訂轉換器，以自訂或擴充 `System.Text.Json` 未包含在目前版本中的功能。 本文稍後將討論下列案例：

::: zone pivot="dotnet-5-0"

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。
* [支援](#support-polymorphic-deserialization)多型還原序列化。
* [支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。
* [具有非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)。
* [支援](#support-polymorphic-deserialization)多型還原序列化。
* [支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。
::: zone-end

在您為自訂轉換器撰寫的程式碼中，請留意使用新實例的顯著效能損失 <xref:System.Text.Json.JsonSerializerOptions> 。 如需詳細資訊，請參閱 [重複使用 JsonSerializerOptions 實例](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)。

## <a name="custom-converter-patterns"></a>自訂轉換器模式

有兩種模式可建立自訂轉換器：基本模式和 factory 模式。 Factory 模式是用於處理類型 `Enum` 或開放式泛型的轉換器。 基本模式適用于非泛型和封閉式泛型型別。  例如，下列類型的轉換器需要 factory 模式：

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

基本模式可處理的一些類型範例包括：

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

基本模式會建立可以處理一種類型的類別。 Factory 模式會建立一個類別，在執行時間決定需要何種特定類型，並以動態方式建立適當的轉換器。

## <a name="sample-basic-converter"></a>範例基本轉換器

下列範例是覆寫現有資料類型之預設序列化的轉換器。 轉換器使用 mm/dd/yyyy 格式的 `DateTimeOffset` 屬性。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a>範例 factory 模式切換器

下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` 。 因為第一個泛型型別參數為 `Enum` ，第二個是開啟的，所以程式碼會遵循 factory 模式。 `CanConvert`方法 `true` 只 `Dictionary` 會傳回具有兩個泛型參數的，第一個是 `Enum` 型別。 內部轉換器會取得現有的轉換器，以處理執行時間所提供的任何類型 `TValue` 。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

上述程式碼與本文稍後的 [非字串索引鍵的支援字典](#support-dictionary-with-non-string-key) 中所顯示的相同。

## <a name="steps-to-follow-the-basic-pattern"></a>遵循基本模式的步驟

下列步驟說明如何遵循基本模式來建立轉換器：

* 建立衍生自的類別， <xref:System.Text.Json.Serialization.JsonConverter%601> 其中 `T` 是要序列化和還原序列化的型別。
* 覆寫方法以將內送 JSON 還原序列化 `Read` ，並將其轉換為類型 `T` 。 使用 <xref:System.Text.Json.Utf8JsonReader> 傳遞至方法的，以讀取 JSON。 當序列化程式傳遞目前 JSON 範圍的所有資料時，您不需要擔心處理部分資料。 因此，不需要呼叫或，也不需要 <xref:System.Text.Json.Utf8JsonReader.Skip%2A> <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> 驗證傳回的 <xref:System.Text.Json.Utf8JsonReader.Read%2A> `true` 。
* 覆寫 `Write` 方法以序列化類型的傳入物件 `T` 。 使用 <xref:System.Text.Json.Utf8JsonWriter> 傳遞至方法的，以寫入 JSON。
* `CanConvert`只有在必要時才覆寫方法。 `true`當要轉換的類型是型別時，就會傳回預設的實值 `T` 。 因此，只支援類型的轉換器 `T` 不需要覆寫這個方法。 如需需要覆寫這個方法的轉換器範例，請參閱本文稍後的多型還原 [序列化一節](#support-polymorphic-deserialization) 。

您可以參考 [內建的轉換器原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) ，作為撰寫自訂轉換器的參考程式。

## <a name="steps-to-follow-the-factory-pattern"></a>遵循 factory 模式的步驟

下列步驟說明如何遵循 factory 模式來建立轉換器：

* 建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。
* `CanConvert`當要轉換的型別是轉換器可以處理的型別時，請覆寫方法以傳回 true。 例如，如果轉換器適用于 `List<T>` ，它可能只會處理 `List<int>` 、 `List<string>` 和 `List<DateTime>` 。
* 覆寫 `CreateConverter` 方法以傳回轉換器類別的實例，這個實例將會處理在執行時間提供的型別轉換。
* 建立方法具現化的轉換器類別 `CreateConverter` 。

開啟泛型需要 factory 模式，因為將物件與字串相互轉換的程式碼對所有類型而言都不相同。 開放式泛型型別 (的轉換器 `List<T>` ，例如) 必須為封閉式泛型型別 (建立轉換器 `List<DateTime>` ，例如在幕後進行) 。 您必須撰寫程式碼來處理轉換器可以處理的每個封閉式泛型型別。

`Enum`型別類似于開放式泛型型別：的轉換器 `Enum` 必須建立特定 (的轉換器 `Enum` `WeekdaysEnum` ，例如在幕後) 。

## <a name="error-handling"></a>錯誤處理

序列化程式會針對例外狀況類型和提供特殊處理 <xref:System.Text.Json.JsonException> <xref:System.NotSupportedException> 。

### <a name="jsonexception"></a>JsonException

如果您擲回 `JsonException` 沒有訊息的，則序列化程式會建立一個訊息，其中包含造成錯誤之 JSON 部分的路徑。 例如，語句會 `throw new JsonException()` 產生類似下列範例的錯誤訊息：

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

如果您確實提供訊息 (例如， `throw new JsonException("Error occurred")` 序列化程式仍會設定 <xref:System.Text.Json.JsonException.Path> 、 <xref:System.Text.Json.JsonException.LineNumber> 和 <xref:System.Text.Json.JsonException.BytePositionInLine> 屬性。

### <a name="notsupportedexception"></a>NotSupportedException

如果您擲回 `NotSupportedException` ，一律會取得訊息中的路徑資訊。 如果您提供訊息，則會將路徑資訊附加至該訊息。 例如，語句會 `throw new NotSupportedException("Error occurred.")` 產生類似下列範例的錯誤訊息：

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a>何時擲回哪個例外狀況類型

當 JSON 承載包含的權杖對要還原序列化的類型無效時，會擲回 `JsonException` 。

當您想要禁止特定類型時，會擲回 `NotSupportedException` 。 此例外狀況是序列化程式針對不支援的類型自動擲回的例外狀況。 例如，基於 `System.Type` 安全性理由，不支援，因此嘗試將它還原序列化會導致 `NotSupportedException` 。

您可以視需要擲回其他例外狀況，但不會自動包含 JSON 路徑資訊。

## <a name="register-a-custom-converter"></a>註冊自訂轉換器

*註冊* 自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。 選擇下列其中一種方法：

* 將轉換器類別的實例新增至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。
* 將 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 屬性套用至需要自訂轉換器的屬性。
* 將 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 屬性套用至代表自訂實值型別的類別或結構。

## <a name="registration-sample---converters-collection"></a>註冊範例-轉換器集合

以下範例會 <xref:System.ComponentModel.DateTimeOffsetConverter> 為類型的屬性建立預設值 <xref:System.DateTimeOffset> ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

假設您將下列型別的實例序列化：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

以下是顯示已使用自訂轉換器的 JSON 輸出範例：

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

下列程式碼使用自訂轉換器還原序列化的相同方法 `DateTimeOffset` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a>註冊範例-屬性上的 [JsonConverter]

下列程式碼會選取屬性的自訂轉換器 `Date` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

要序列化的程式碼 `WeatherForecastWithConverterAttribute` 不需要使用 `JsonSerializeOptions.Converters` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

還原序列化的程式碼也不需要使用 `Converters` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a>註冊範例-類型上的 [JsonConverter]

以下程式碼會建立結構，並 `[JsonConverter]` 對其套用屬性：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

以下是上述結構的自訂轉換器：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

`[JsonConvert]`結構上的屬性會將自訂轉換器註冊為類型屬性的預設值 `Temperature` 。 當您將轉換器序列化或還原序列化時，會自動在下列類型的屬性上使用轉換器 `TemperatureCelsius` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a>轉換器註冊優先順序

在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序到最低：

* `[JsonConverter]` 套用至屬性。
* 加入至集合的轉換器 `Converters` 。
* `[JsonConverter]` 套用至自訂實數值型別或 POCO。

如果在集合中註冊了某個類型的多個自訂轉換器 `Converters` ，則會使用第一個傳回 true 的轉換器 `CanConvert` 。

只有在沒有註冊適用的自訂轉換器時，才會選擇內建的轉換器。

## <a name="converter-samples-for-common-scenarios"></a>常見案例的轉換器範例

下列各節提供的轉換器範例可解決一些內建功能未處理的常見案例。

::: zone pivot="dotnet-5-0"

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。
* [支援](#support-polymorphic-deserialization)多型還原序列化。
* [支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。
* [具有非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)。
* [支援](#support-polymorphic-deserialization)多型還原序列化。
* [支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a>將推斷的類型還原序列化為物件屬性

當還原序列化為型別的屬性時 `object` ， `JsonElement` 會建立物件。 原因是還原序列化程式不知道要建立什麼 CLR 型別，而且它不會試著猜測。 例如，如果 JSON 屬性有 "true"，則還原序列化程式並不會推斷值為 `Boolean` ，而且如果專案具有 "01/01/2019"，則還原序列化程式並不會推斷它是 a `DateTime` 。

型別推斷可能不正確。 如果還原序列化程式會剖析沒有小數點的 JSON 數位 `long` ，如果值原本是序列化為或，可能會導致超出範圍的問題 `ulong` `BigInteger` 。 如果數位原本是序列化為，則剖析具有小數點的數位 `double` 可能會遺失精確度 `decimal` 。

針對需要型別推斷的案例，下列程式碼會顯示內容的自訂轉換器 `object` 。 程式碼會轉換：

* `true`以及 `false``Boolean`
* 不含小數位數的數位 `long`
* 具有小數點的數位 `double`
* 日期至 `DateTime`
* 字串至 `string`
* 其他專案 `JsonElement`

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

下列程式碼會註冊轉換器：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

以下是包含屬性的範例類型 `object` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime` 、和的值 `long` `string` ：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

如果沒有自訂轉換器，還原序列化會 `JsonElement` 在每個屬性中放置。

命名空間中的 [單元測試資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` 有更多的自訂轉換器範例，可處理屬性的還原序列化 `object` 。

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a>使用非字串索引鍵的支援字典

字典集合的內建支援適用于 `Dictionary<string, TValue>` 。 也就是說，索引鍵必須是字串。 若要支援具有整數或其他類型作為索引鍵的字典，則需要自訂轉換子。

下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

下列程式碼會註冊轉換器：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

轉換器可以序列化和還原序列化 `TemperatureRanges` 下列使用下列類別的屬性 `Enum` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

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

命名空間中的 [單元測試資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) ， `System.Text.Json.Serialization` 有更多的自訂轉換器的範例，可處理非字串金鑰字典。
::: zone-end

### <a name="support-polymorphic-deserialization"></a>支援多型還原序列化

內建功能提供有限範圍的多型 [序列化](system-text-json-polymorphism.md) ，但完全不支援還原序列化。 還原序列化需要自訂的轉換器。

例如，假設您有一個 `Person` 具有 `Employee` 和衍生類別的抽象基類 `Customer` 。 多型還原序列化表示在設計階段，您可以將指定為還原序列化 `Person` 目標，並在 `Customer` `Employee` 執行時間將 JSON 中的物件正確還原序列化。 在還原序列化期間，您必須在 JSON 中尋找識別所需類型的線索。 可用的線索種類會因每個案例而異。 例如，可能會有鑒別子屬性，或您可能必須依賴特定屬性的存在或不存在。 目前的版本 `System.Text.Json` 並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂的轉換器。

下列程式碼顯示基類、兩個衍生類別，以及它們的自訂轉換子。 轉換器會使用鑒別子屬性來進行多型還原序列化。 類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

下列程式碼會註冊轉換器：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

轉換器可以將使用相同轉換器所建立的 JSON 還原序列化，例如：

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

上述範例中的轉換器程式碼會以手動方式讀取和寫入每個屬性。 替代方法是呼叫 `Deserialize` 或 `Serialize` 執行某些工作。 如需範例，請參閱 [這 StackOverflow 文章](https://stackoverflow.com/a/59744873/12509023)。

### <a name="support-round-trip-for-stackt"></a>支援堆疊的來回行程\<T>

如果您將 JSON 字串還原序列化為物件，然後將 <xref:System.Collections.Generic.Stack%601> 該物件序列化，堆疊的內容會以相反的順序排列。 此行為適用于下列型別和介面，以及衍生自這些型別的使用者定義型別：

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

若要支援在堆疊中保留原始順序的序列化和還原序列化，則需要自訂轉換子。

下列程式碼顯示可啟用物件來回往返的自訂轉換器 `Stack<T>` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

下列程式碼會註冊轉換器：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a>處理 Null 值

根據預設，序列化程式會處理 null 值，如下所示：

* 針對參考型別和 <xref:System.Nullable%601> 類型：

  * 它不會 `null` 在序列化時傳遞至自訂轉換器。
  * 它不會在還原序列化 `JsonTokenType.Null` 時傳遞至自訂轉換器。
  * 它會在還原序列化 `null` 時傳回實例。
  * 它會 `null` 直接寫入序列化的寫入器。

* 針對不可為 null 的實數值型別：

  * 它會 `JsonTokenType.Null` 在還原序列化時傳遞至自訂轉換器。  (如果沒有可用的自訂轉換器，則 `JsonException` 類型的內部轉換器會擲回例外狀況。 ) 

這項 null 處理行為主要是藉由略過額外的轉換器呼叫來優化效能。 此外，它可避免 `null` 在每個和方法覆寫的開頭，強制執行可為 null 類型的轉換器 `Read` `Write` 。

::: zone pivot="dotnet-5-0"
若要啟用自訂轉換器來處理 `null` 參考或實數值型別，請覆寫 <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> 以傳回 `true` ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="18":::
::: zone-end

## <a name="other-custom-converter-samples"></a>其他自訂轉換器範例

[從遷移 Newtonsoft.Json 至 System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md)文章包含其他自訂轉換器範例。

原始程式碼中的 [ [單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` 包含其他自訂轉換器範例，例如：

* [在還原序列化時將 null 轉換為0的 Int32 轉換子](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Int32 轉換器，可在還原序列化時同時允許字串和數位值](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [列舉轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [\<T>接受外部資料的清單轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] 轉換器，適用于以逗號分隔的數位清單](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

如果您需要建立可修改現有內建轉換器行為的轉換器，您可以取得 [現有轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) ，以做為自訂的起點。

## <a name="additional-resources"></a>其他資源

* [內建轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [System.Text.Json 概述](system-text-json-overview.md)
* [如何將 JSON 序列化及還原序列化](system-text-json-how-to.md)
* [具現化 JsonSerializerOptions 實例](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [忽略屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留參考](system-text-json-preserve-references.md)
* [不可變型別及非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [從遷移 Newtonsoft.Json 至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [自訂字元編碼](system-text-json-character-encoding.md)
* [撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
