---
title: 如何使用自訂屬性名稱和值 System.Text.Json
description: 瞭解如何在使用 .NET 進行序列化時，自訂屬性名稱和值 System.Text.Json 。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c754d41071e886bc1efcc3a30e249bf9e554ab5b
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599586"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a>如何使用自訂屬性名稱和值 System.Text.Json

根據預設，JSON 輸出中的屬性名稱和字典索引鍵不會變更，包括大小寫。 列舉值會以數位表示。 在本文中，您將學會如何：

> [!NOTE]
> [Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)為 [camel 大小寫]。

* [自訂個別的屬性名稱](#customize-individual-property-names)
* [將所有屬性名稱轉換成 camel 大小寫](#use-camel-case-for-all-json-property-names)
* [執行自訂屬性命名原則](#use-a-custom-json-property-naming-policy)
* [將字典索引鍵轉換成 camel 大小寫](#camel-case-dictionary-keys)
* [將列舉轉換為字串和 camel 大小寫](#enums-as-strings)

對於需要特殊處理 JSON 屬性名稱和值的其他情況，您可以 [執行自訂的轉換器](system-text-json-converters-how-to.md)。

## <a name="customize-individual-property-names"></a>自訂個別的屬性名稱

若要設定個別屬性的名稱，請使用 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 屬性。

以下是要序列化並產生 JSON 的範例類型：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="use-camel-case-for-all-json-property-names"></a>針對所有 JSON 屬性名稱使用 camel 大小寫

若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

以下是序列化和 JSON 輸出的範例類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="use-a-custom-json-property-naming-policy"></a>使用自訂 JSON 屬性命名原則

若要使用自訂 JSON 屬性命名原則，請建立一個衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為命名原則類別的實例：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

以下是序列化和 JSON 輸出的範例類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="camel-case-dictionary-keys"></a>Camel 案例字典索引鍵

如果要序列化之物件的屬性是型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。 若要這樣做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

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

## <a name="enums-as-strings"></a>作為字串的列舉

根據預設，列舉會序列化為數字。 若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。

例如，假設您需要序列化具有列舉的下列類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

產生的 JSON 看起來如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

您也可以還原序列化列舉字串名稱，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [Instantiate JsonSerializerOptions](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [忽略屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變型別及非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
