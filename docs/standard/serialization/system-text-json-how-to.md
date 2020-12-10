---
title: '如何使用 c # 序列化和還原序列化 JSON-.NET'
description: 瞭解如何 System.Text.Json 在 .net 中使用命名空間進行序列化，並從 JSON 還原序列化。 包含範例程式碼。
ms.date: 12/02/2020
ms.custom: contperfq2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1ea4ff71b9e21bd7c5b12598581b33e1e96ebb19
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008834"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON

本文說明如何使用 <xref:System.Text.Json?displayProperty=fullName> 命名空間，從 JavaScript 物件標記法 (JSON) 序列化和還原序列化。 如果您要從移植現有的程式碼 `Newtonsoft.Json` ，請參閱[如何 `System.Text.Json` 遷移至](system-text-json-migrate-from-newtonsoft-how-to.md)。

指示和範例程式碼會直接使用程式庫，而不是透過 [ASP.NET Core](/aspnet/core/)的架構。

大部分的序列化程式碼範例會將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為「 `true` 美觀」的 JSON (，以縮排和空白字元來取得可讀性) 。 針對生產用途，您通常會接受此設定的預設值 `false` 。

程式碼範例參考下列類別和它的變異：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a>命名空間

<xref:System.Text.Json>命名空間包含所有進入點和主要類型。 <xref:System.Text.Json.Serialization>命名空間包含適用于進行序列化和還原序列化的 advanced 案例和自訂的屬性和 api。 本文中顯示的程式碼範例需要 `using` 下列其中一個或兩個命名空間的指示詞：

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <xref:System.Runtime.Serialization>不支援命名空間中的屬性 `System.Text.Json` 。

## <a name="how-to-write-net-objects-as-json-serialize"></a>如何將 .NET 物件撰寫為 JSON (序列化) 

若要將 JSON 寫入字串或檔案，請呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。

下列範例會以字串形式建立 JSON：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

下列範例會使用同步程式碼來建立 JSON 檔案：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

下列範例會使用非同步程式碼來建立 JSON 檔案：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

上述範例會針對要序列化的型別使用型別推斷。 的多載 `Serialize()` 會採用泛型型別參數：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a>序列化範例

以下是包含集合類型屬性和使用者定義型別的範例類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> "POCO" 代表 [純舊的 CLR 物件](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。 POCO 是一種 .NET 型別，其不相依于任何架構特定的類型，例如透過繼承或屬性。

序列化上述型別的實例的 JSON 輸出如下列範例所示。 JSON 輸出為縮減 (空白字元、縮排和換行字元預設會) 移除：

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

## <a name="serialize-to-utf-8"></a>序列化為 UTF-8

若要序列化為 UTF-8，請呼叫 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<xref:System.Text.Json.JsonSerializer.Serialize%2A>也可以使用採用的多載 <xref:System.Text.Json.Utf8JsonWriter> 。

使用以字串為基礎的方法，序列化為 UTF-8 的速度大約是5-10%。 差異是因為 (為 UTF-8 的位元組) 不需要轉換成字串 (UTF-16) 。

## <a name="serialization-behavior"></a>序列化行為

::: zone pivot="dotnet-5-0"

* 依預設，所有公用屬性都會進行序列化。 您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。
* 根據預設，JSON 是縮減。 您可以 [整齊列印 JSON](#serialize-to-formatted-json)。
* 根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。 您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。
* 依預設，會偵測到迴圈參考並擲回例外狀況。 您可以 [保留參考並處理迴圈參考](system-text-json-preserve-references.md)。
* 依預設，會忽略 [欄位](../../csharp/programming-guide/classes-and-structs/fields.md) 。 您可以 [包含欄位](#include-fields)。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 依預設，所有公用屬性都會進行序列化。 您可以 [指定要忽略的屬性](system-text-json-ignore-properties.md)。
* [預設編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)會將非 ascii 字元、ASCII 範圍內的 HTML 機密字元，以及必須根據[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259#section-7)進行換用的字元進行轉義。
* 根據預設，JSON 是縮減。 您可以 [整齊列印 JSON](#serialize-to-formatted-json)。
* 根據預設，JSON 名稱的大小寫會與 .NET 名稱相符。 您可以 [自訂 JSON 名稱大小寫](system-text-json-customize-properties.md)。
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

## <a name="how-to-read-json-as-net-objects-deserialize"></a>如何將 JSON 讀取為 .NET 物件 (還原序列化) 

若要從字串或檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。

下列範例會從字串讀取 JSON，並 `WeatherForecastWithPOCOs` 為 [序列化範例](#serialization-example)建立稍早所示類別的實例：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

若要使用同步程式碼從檔案還原序列化，請將檔案讀入字串，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

若要使用非同步程式碼從檔案還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a>從 UTF-8 還原序列化

若要從 UTF-8 還原序列化，請呼叫 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 接受 `ReadOnlySpan<byte>` 或的多載， `Utf8JsonReader` 如下列範例所示。 這些範例假設 JSON 是在名為 jsonUtf8Bytes 的位元組陣列中。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a>還原序列化行為

將 JSON 還原序列化時，會套用下列行為：

::: zone pivot="dotnet-5-0"

* 依預設，屬性名稱比對會區分大小寫。 您可以 [指定不區分大小寫](system-text-json-character-casing.md)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。
* 序列化程式會忽略非公用的函式。
* 支援還原序列化至不可變的物件或唯讀屬性。 請參閱 [不可變的類型和記錄](system-text-json-immutability.md)。
* 依預設，會將列舉支援為數字。 您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。
* 依預設，會忽略欄位。 您可以 [包含欄位](#include-fields)。
* 根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。 您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 依預設，屬性名稱比對會區分大小寫。 您可以 [指定不區分大小寫](system-text-json-character-casing.md)。 ASP.NET Core apps [預設會指定不區分大小寫](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。
* 如果 JSON 包含唯讀屬性的值，則會忽略此值，而且不會擲回例外狀況。
* 無參數的函式（可以是公用、內部或私用）用於還原序列化。
* 不支援還原序列化為不可變的物件或唯讀屬性。
* 依預設，會將列舉支援為數字。 您可以將 [列舉名稱序列化為字串](system-text-json-customize-properties.md#enums-as-strings)。
* 不支援欄位。
* 根據預設，JSON 中的批註或尾端逗號會擲回例外狀況。 您可以 [允許批註和結尾的逗號](system-text-json-invalid-json.md)。
* [預設的最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)為64。

當您 System.Text.Json 在 ASP.NET Core 應用程式中間接使用時，會有一些預設行為不同。 如需詳細資訊，請參閱 [JsonSerializerOptions 的 Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。
::: zone-end

您可以 [執行自訂轉換器](system-text-json-converters-how-to.md) ，以提供內建轉換器不支援的功能。

## <a name="serialize-to-formatted-json"></a>序列化為格式化的 JSON

若要整齊列印 JSON 輸出，請將設定 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 為 `true` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

以下是要序列化的範例型別，以及整齊列印的 JSON 輸出：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

如果您 `JsonSerializerOptions` 重複使用相同的選項，請勿 `JsonSerializerOptions` 在每次使用時建立新的實例。 每次呼叫時重複使用相同的實例。 如需詳細資訊，請參閱 [重複使用 JsonSerializerOptions 實例](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)。

## <a name="include-fields"></a>包含欄位

::: zone pivot="dotnet-5-0"
<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>當序列化或還原序列化時，請使用全域設定或[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)屬性來包含欄位，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

若要忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。
::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json在 .Net Core 3.1 中不支援欄位。 [自訂轉換器](system-text-json-converters-how-to.md) 可以提供這種功能。
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>HttpClient 和 HttpContent 擴充方法

::: zone pivot="dotnet-5-0"

從網路序列化和還原序列化 JSON 承載是常見的作業。 [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions)和[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)上的擴充方法可讓您在一行程式碼中進行這些作業。 這些擴充方法會使用 [web 預設值進行 JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)。

下列範例說明如何使用 <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> ：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

此外，也有適用 System.Text.Json 于 [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)的擴充方法。
::: zone-end

::: zone pivot="dotnet-core-3-1"
和上的擴充方法在 `HttpClient` `HttpContent` System.Text.Json .net Core 3.1 中無法使用。
::: zone-end

## <a name="see-also"></a>請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
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
* [撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
