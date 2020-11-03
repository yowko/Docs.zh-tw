---
title: System.Text.Json 中的 DateTime 和 DateTimeOffset 支援
description: 程式庫 System.Text.Js中支援 DateTime 和 DateTimeOffset 類型的總覽。
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 020e6903069da2c5d8761c86e890c4e9575a3fae
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188753"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.Text.Json 中的 DateTime 和 DateTimeOffset 支援

程式庫上的 System.Text.Js會 <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601:-2019 擴充設定檔來剖析和寫入和值。
[轉換器](xref:System.Text.Json.Serialization.JsonConverter%601) 提供序列化和還原序列化的自訂支援 <xref:System.Text.Json.JsonSerializer> 。
使用和時，也可以實作為自訂支援 <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> 。

## <a name="support-for-the-iso-8601-12019-format"></a>支援 ISO 8601-1:2019 格式

<xref:System.Text.Json.JsonSerializer>、 <xref:System.Text.Json.Utf8JsonReader> 、 <xref:System.Text.Json.Utf8JsonWriter> 和類型會 <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601-1:2019 格式的擴充設定檔來剖析和寫入和文字標記法，例如 2019-07-26T16：59： 57-05：00。

<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料可以使用下列方式進行序列化 <xref:System.Text.Json.JsonSerializer> ：

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

也可以使用下列方式還原序列化 <xref:System.Text.Json.JsonSerializer> ：

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

使用預設選項時，輸入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 文字表示必須符合延伸的 ISO 8601-1:2019 設定檔。
嘗試還原序列化不符合設定檔的標記法會導致 <xref:System.Text.Json.JsonSerializer> 擲回 <xref:System.Text.Json.JsonException> ：

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument>提供 JSON 承載內容的結構化存取，包括 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 標記法。 下列範例顯示如何在指定溫度集合時，計算星期一的平均溫度：

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

嘗試計算指定具有不符合規範之承載的平均溫度時 <xref:System.DateTime> ，會導致 <xref:System.Text.Json.JsonDocument> 擲回 <xref:System.FormatException> ：

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

較低層級的 <xref:System.Text.Json.Utf8JsonWriter> 寫入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> 剖析 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

嘗試讀取不符合規範的格式 <xref:System.Text.Json.Utf8JsonReader> 將會導致它擲回 <xref:System.FormatException> ：

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>和的自訂支援 <xref:System.DateTime><xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>使用時 <xref:System.Text.Json.JsonSerializer>

如果您想要序列化程式執行自訂剖析或格式設定，您可以執行 [自訂的轉換器](xref:System.Text.Json.Serialization.JsonConverter%601)。
以下是一些範例：

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>使用 `DateTime(Offset).Parse` 和 `DateTime(Offset).ToString`

如果您無法判斷輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法的格式，則可以使用 `DateTime(Offset).Parse` 轉換器讀取邏輯中的方法。 這可讓您使用。NET 對剖析各種 <xref:System.DateTime> 和文字格式的廣泛支援 <xref:System.DateTimeOffset> ，包括不符合延伸 iso 8601-1:2019 設定檔的非 iso 8601 字串和 ISO 8601 格式。 相較于使用序列化程式的原生執行，這個方法的效能會大幅降低。

針對序列化，您可以 `DateTime(Offset).ToString` 在轉換器寫入邏輯中使用方法。 這可讓您 <xref:System.DateTime> <xref:System.DateTimeOffset> 使用任何 [標準日期和時間格式](../base-types/standard-date-and-time-format-strings.md)，以及 [自訂日期和時間格式](../base-types/custom-date-and-time-format-strings.md)來撰寫和值。
這種效能也比使用序列化程式的原生實作為低。

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> 在執行時， <xref:System.Text.Json.Serialization.JsonConverter%601> `T` <xref:System.DateTime> `typeToConvert` 參數一律為 `typeof(DateTime)` 。
參數適合用來處理多型案例，以及使用泛型以高效能的方式取得時 `typeof(T)` 。

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>使用 <xref:System.Buffers.Text.Utf8Parser> 和 <xref:System.Buffers.Text.Utf8Formatter>

如果您的輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法符合其中一個 "R"、"l"、"O" 或 "G" [標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md)，或者您想要根據這些格式的其中一種來撰寫，您可以在轉換器邏輯中使用快速 utf-8 型剖析和格式化方法。 這比使用和更快 `DateTime(Offset).Parse` `DateTime(Offset).ToString` 。

這個範例會示範 <xref:System.DateTime> 根據 ["R" 標準格式](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)序列化和還原序列化值的自訂轉換器：

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" 標準格式的長度一律會是29個字元。
>
> "L" (小寫 "L" ) 格式未記錄其他 [標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md) ，因為它只有 `Utf8Parser` 和類型才支援 `Utf8Formatter` 。 格式為小寫 RFC 1123 (小寫版本的 "R" 格式) ，例如： "星期四，25七月 2019 06:36:07 gmt"。

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>使用 `DateTime(Offset).Parse` 作為序列化程式原生剖析的回溯

如果您通常預期輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 資料符合延伸的 ISO 8601-1:2019 設定檔，您可以使用序列化程式的原生剖析邏輯。 您也可以在案例中執行回溯機制。
這個範例顯示，在無法 <xref:System.DateTime> 使用剖析文字標記法之後， <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> 轉換器會使用成功剖析資料 <xref:System.DateTime.Parse(System.String)> 。

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>撰寫時 <xref:System.Text.Json.Utf8JsonWriter>

如果您想要使用撰寫自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonWriter> ，您可以將自訂表格示格式設定為 <xref:System.String> 、 `ReadOnlySpan<Byte>` 、 `ReadOnlySpan<Char>` 或 <xref:System.Text.Json.JsonEncodedText> ，然後將它傳遞給對應的 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> 或 <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> 方法。

下列範例顯示如何 <xref:System.DateTime> 使用建立自訂格式 <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> ，然後使用方法來撰寫 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> ：

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>讀取時 <xref:System.Text.Json.Utf8JsonReader>

如果您想要使用讀取自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonReader> ，您可以使用來取得目前 JSON 權杖的值 <xref:System.String> <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用自訂邏輯來剖析該值。

下列範例示範如何使用來抓取自訂 <xref:System.DateTimeOffset> 文字標記法 <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用進行剖析 <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> ：

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System.Text.Js中的擴充 ISO 8601-1:2019 設定檔

### <a name="date-and-time-components"></a>日期和時間元件

在中實的擴充 ISO 8601-1:2019 設定檔會 <xref:System.Text.Json> 定義下列日期和時程表示的元件。 這些元件是用來定義剖析和格式化 <xref:System.DateTime> 和標記法時，所支援的各種資料細微性層級 <xref:System.DateTimeOffset> 。

| 元件       | 格式                      | 描述                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| 月           | "MM"                        | 01-12                                                                           |
| 天             | "dd"                        | 01-28、01-29、01-30、01-31 （依據月份/年）                                  |
| 小時            | "HH"                        | 00-23                                                                           |
| Minute          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| 第二個分數 | "FFFFFFF"                   | 最少一個位數，最多16位數                                      |
| 時間位移     | "K"                         | 可能是 "Z" 或 " ( ' + '/'-' ) HH '： ' mm"                                                |
| 部分時間    | "HH '： ' mm '： ' ss [FFFFFFF]"     | 沒有 UTC 時差資訊的時間                                             |
| 完整日期       | "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"            | 行事曆日期                                                                   |
| 完整時間       | 「部分 time'K」           | 當地時間與 UTC 之間的時差，以天或本地時間為 UTC |
| 日期時間       | "' Full date ' t ' ' Full time '" | 行事曆日期和當日時間，例如 2019-07-26T16：59： 57-05：00                   |

### <a name="support-for-parsing"></a>支援剖析

以下是針對剖析而定義的資料細微性層級：

1. 「完整日期」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"

2. "' Full date ' t ' ' Hour ' '： ' ' Minute '"
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM"

3. "' Full date ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可 [排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) 
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。FFFFFFF

4. "' Full date ' t ' ' Time hour ' '： ' ' Minute ' ' 時間位移 '"
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mmZ"
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm ( ' + '/'-' ) HH '： ' mm"

5. [日期時間]
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。SS.FFFFFFFZ
    3. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"
    4. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。FFFFFFF ( ' + '/'-' ) HH '： ' mm "

    這一層級的資料細微性符合 [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)，這是一種廣泛採用的 ISO 8601 設定檔，用於交換日期和時間資訊。 不過，在執行 System.Text.Js中有幾項限制。

    - RFC 3339 不會指定小數秒數的最大數目，但會指定至少一個數位必須在句點之後，如果有小數秒區段存在的話。 System.Text.Js中的實，最多可支援16位數 (以支援與其他程式設計語言和架構) 的交互操作，但只剖析前七個。 <xref:System.Text.Json.JsonException>如果讀取和實例時有超過16個小數秒位數，則會擲回 `DateTime` `DateTimeOffset` 。
    - RFC 3339 允許將 "T" 和 "Z" 字元分別設為 "t" 或 "z"，但可讓應用程式將支援限制為僅限大寫變異。 System.Text.Js中的實要求必須是 "T" 和 "Z"。 <xref:System.Text.Json.JsonException>如果輸入裝載在讀取和實例時包含 "t" 或 "z"，將會擲回 `DateTime` `DateTimeOffset` 。
    - RFC 3339 指定日期和時間區段會以 "T" 分隔，但可讓應用程式以空格 ( "" ) 來分隔它們。 System.Text.Json 需要以 "T" 分隔日期和時間區段。 <xref:System.Text.Json.JsonException>如果輸入裝載在讀取和實例時包含空格 ( "" ) ，將會擲回 `DateTime` `DateTimeOffset` 。

如果秒有小數小數，則至少必須有一個位數; `2019-07-26T00:00:00.` 不允許。
雖然允許的小數位數最多可達16個，但只有前七個會經過剖析。 超出此值的任何值都會被視為零。
例如，將會剖析 `2019-07-26T00:00:00.1234567890` 為，如下所示 `2019-07-26T00:00:00.1234567` 。
這是為了保持與執行的相容性，這僅 <xref:System.DateTime> 限於此解決方案。

不支援閏秒數。

### <a name="support-for-formatting"></a>支援格式化

以下是針對格式定義的資料細微性層級：

1. "' Full date ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可 [排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) 

        用來格式化 <xref:System.DateTime> 不含小數秒且不含位移資訊的。

    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。FFFFFFF

        用來 <xref:System.DateTime> 利用小數秒來格式化，但不含位移資訊。

2. [日期時間]
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"

        用來格式化 <xref:System.DateTime> 不含小數秒數的，但使用 UTC 位移。

    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。SS.FFFFFFFZ

        用來以 <xref:System.DateTime> 小數秒和 UTC 位移來格式化。

    3. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"

        用來格式化 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 不含小數秒數，但使用區域位移。

    4. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。FFFFFFF ( ' + '/'-' ) HH '： ' mm "

        用來將 <xref:System.DateTime> 或以 <xref:System.DateTimeOffset> 小數秒和區域位移格式化。

    這一層級的資料細微性符合 [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)的規範。

如果或實例的 [來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表示 <xref:System.DateTime> <xref:System.DateTimeOffset> 在其小數秒中有尾端零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 將會格式化實例的標記法，而不會有尾端的零。
例如， <xref:System.DateTime> 其 [來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表示的實例 `2019-04-24T14:50:17.1010000Z` 將會格式化為 `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。

如果或實例的 [來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 標記法 <xref:System.DateTime> 的 <xref:System.DateTimeOffset> 小數秒數全部為零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 將會格式化實例的標記法，而不含小數秒數。
例如， <xref:System.DateTime> 其 [來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表示的實例 `2019-04-24T14:50:17.0000000+02:00` 將會格式化為 `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。

以小數秒數來截斷零，可讓您在寫入的來回行程中保留資訊時所需的最小輸出。

最多會寫入7個小數秒位數。 這 <xref:System.DateTime> 會與實作為此解決方案的限制。
