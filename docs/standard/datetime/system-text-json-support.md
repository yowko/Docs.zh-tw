---
title: System.Text.Json 中的 DateTime 和 DateTimeOffset 支援
description: 概述 System.Text.Js的程式庫中如何支援 DateTime 和 DateTimeOffset 類型。
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
ms.openlocfilehash: 1c573712f458d3e22cd59112b9e79e85391270c1
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854889"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.Text.Json 中的 DateTime 和 DateTimeOffset 支援

程式庫上的 System.Text.Js會 <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601:-2019 擴充設定檔來剖析和寫入值。
[轉換器](xref:System.Text.Json.Serialization.JsonConverter%601)提供使用進行序列化和還原序列化的自訂支援 <xref:System.Text.Json.JsonSerializer> 。
使用和時，也可以實作為自訂支援 <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> 。

## <a name="support-for-the-iso-8601-12019-format"></a>支援 ISO 8601-1:2019 格式

<xref:System.Text.Json.JsonSerializer>、 <xref:System.Text.Json.Utf8JsonReader> 、 <xref:System.Text.Json.Utf8JsonWriter> 和類型會 <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601-1:2019 格式的延伸設定檔來剖析和寫入和文字標記法，例如 2019-07-26T16：59： 57-05：00。

<xref:System.DateTime>和 <xref:System.DateTimeOffset> 資料可以使用進行序列化 <xref:System.Text.Json.JsonSerializer> ：

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

它們也可以使用還原序列化 <xref:System.Text.Json.JsonSerializer> ：

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

使用預設選項時，輸入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 文字標記法必須符合擴充 ISO 8601-1:2019 設定檔。
嘗試還原序列化不符合設定檔的標記法會導致 <xref:System.Text.Json.JsonSerializer> 擲回 <xref:System.Text.Json.JsonException> ：

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument>提供 JSON 裝載內容的結構化存取，包括 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 標記法。 下列範例顯示如何在指定溫度的集合時，可以計算星期一的平均溫度：

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

嘗試計算出具有不符合規範之承載的平均溫度， <xref:System.DateTime> 會導致 <xref:System.Text.Json.JsonDocument> 擲回 <xref:System.FormatException> ：

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

較低層級的 <xref:System.Text.Json.Utf8JsonWriter> 寫入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader>剖析 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

嘗試使用讀取不相容的格式 <xref:System.Text.Json.Utf8JsonReader> 會導致它擲回 <xref:System.FormatException> ：

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>和的自訂支援 <xref:System.DateTime><xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>使用時<xref:System.Text.Json.JsonSerializer>

如果您想要序列化程式執行自訂剖析或格式設定，您可以實作為[自訂轉換器](xref:System.Text.Json.Serialization.JsonConverter%601)。
以下是一些範例：

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>使用 `DateTime(Offset).Parse` 和`DateTime(Offset).ToString`

如果您無法判斷輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法的格式，您可以 `DateTime(Offset).Parse` 在轉換子中使用方法讀取邏輯。 這可讓您使用。NET 對於剖析各種 <xref:System.DateTime> 和文字格式的廣泛支援 <xref:System.DateTimeOffset> ，包括非 iso 8601 字串和 ISO 8601 格式，但不符合延伸的 iso 8601-1:2019 設定檔。 相較于使用序列化程式的原生執行，此方法的效能大幅降低。

若要進行序列化，您可以 `DateTime(Offset).ToString` 在轉換器寫入邏輯中使用方法。 這可讓您 <xref:System.DateTime> <xref:System.DateTimeOffset> 使用任何[標準日期和時間格式](../base-types/standard-date-and-time-format-strings.md)，以及[自訂日期和時間格式](../base-types/custom-date-and-time-format-strings.md)來撰寫和值。
相較于使用序列化程式的原生執行，這也會大幅降低效能。

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> 在執行時 <xref:System.Text.Json.Serialization.JsonConverter%601> ，如果 `T` 是 <xref:System.DateTime> ，則 `typeToConvert` 參數一律會是 `typeof(DateTime)` 。
參數適用于處理多型案例，以及使用泛型以高效能的方式取得時 `typeof(T)` 。

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>使用 <xref:System.Buffers.Text.Utf8Parser> 和<xref:System.Buffers.Text.Utf8Formatter>

如果您的輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法符合其中一個 "R"、"l"、"O" 或 "G"[標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md)，或者您想要根據其中一種格式來撰寫，則您可以在轉換器邏輯中使用快速以 utf-8 為基礎的剖析和格式化方法。 這比使用和更快 `DateTime(Offset).Parse` `DateTime(Offset).ToString` 。

這個範例會顯示 <xref:System.DateTime> 根據["R" 標準格式](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)序列化和還原序列化值的自訂轉換器：

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" 標準格式的長度一律為29個字元。
>
> "L" (小寫 "L" ) 格式不會與其他[標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md)一起記載，因為只有 `Utf8Parser` 和類型才支援 `Utf8Formatter` 。 格式為小寫 RFC 1123 (小寫版本的 "R" 格式) ，例如： "thu，25七月 2019 06:36:07 gmt"。

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>使用 `DateTime(Offset).Parse` 做為序列化程式的原生剖析

如果您通常會預期輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 資料必須符合擴充 ISO 8601-1:2019 設定檔，您可以使用序列化程式的原生剖析邏輯。 您也可以只在案例中執行回溯機制。
這個範例顯示，在無法 <xref:System.DateTime> 使用剖析文字標記法之後， <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> 轉換器會使用成功地剖析資料 <xref:System.DateTime.Parse(System.String)> 。

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>寫入時<xref:System.Text.Json.Utf8JsonWriter>

如果您想要使用撰寫自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonWriter> ，您可以將自訂表格示格式格式化為 <xref:System.String> 、 `ReadOnlySpan<Byte>` 、 `ReadOnlySpan<Char>` 或 <xref:System.Text.Json.JsonEncodedText> ，然後將它傳遞給對應的 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> 或 <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> 方法。

下列範例顯示如何 <xref:System.DateTime> 使用來建立自訂格式 <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> ，然後使用 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> 方法撰寫：

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>讀取時<xref:System.Text.Json.Utf8JsonReader>

如果您想要使用讀取自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonReader> ，您可以使用來取得目前 JSON token 的值 <xref:System.String> <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用自訂邏輯來剖析該值。

下列範例顯示如何使用來抓取自訂 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用進行剖析 <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> ：

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System.Text.Js中的擴充 ISO 8601-1:2019 設定檔

### <a name="date-and-time-components"></a>日期和時間元件

在中執行的延伸 ISO 8601-1:2019 設定檔會 <xref:System.Text.Json> 定義下列日期和時程表示的元件。 這些元件是用來定義剖析和格式化 <xref:System.DateTime> 和標記法時，所支援的各種資料細微性層級 <xref:System.DateTimeOffset> 。

| 元件       | 格式                      | 描述                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| Month           | "MM"                        | 01-12                                                                           |
| 天             | "dd"                        | 01-28、01-29、01-30、01-31 （以月/年為基礎）                                  |
| 小時            | "HH"                        | 00-23                                                                           |
| Minute          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| 第二個分數 | "FFFFFFF"                   | 最少一個數位，最多16位數                                      |
| 時間位移     | "K"                         | "Z" 或 " ( ' + '/'-' ) HH '： ' mm"                                                |
| 部分時間    | "HH '： ' mm '： ' ss [FFFFFFF]"     | 沒有 UTC 時差的時間資訊                                             |
| 完整日期       | "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"            | 行事曆日期                                                                   |
| 完整時間       | 「部分 time'K」           | 在當地時間與 UTC 之間時間位移的日或本地時間 UTC |
| 日期時間       | 「完整日期 ' 不是 '」完整時間 '」 | 行事曆日期和時間，例如 2019-07-26T16：59： 57-05：00                   |

### <a name="support-for-parsing"></a>支援剖析

下列資料細微性層級是針對剖析而定義：

1. 「完整日期」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"

2. 「完整日期 ' 不是 ' ' 小時 ' '： ' ' 分鐘 '」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM"

3. 「完整日期 ' 不是」 ' 部分時間 '」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可[排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) 
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF

4. 「完整日期 ' t ' ' 時間小時 ' '： ' ' 分鐘 ' ' 時間位移 '」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mmZ"
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm ( ' + '/'-' ) HH '： ' mm"

5. 「日期時間」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"
    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'SS.FFFFFFFZ
    3. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"
    4. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF ( ' + '/'-' ) HH '： ' mm "

如果秒數有小數，則至少必須有一個數位。`2019-07-26T00:00:00.`不允許。
雖然允許最多16個小數位數，但只有前七個會經過剖析。 除了之外的任何專案都會被視為零。
例如，將會剖析 `2019-07-26T00:00:00.1234567890` 為 `2019-07-26T00:00:00.1234567` 。
這是為了與實施保持相容 <xref:System.DateTime> ，這僅限於此解決方案。

不支援閏秒。

### <a name="support-for-formatting"></a>支援格式化

下列資料細微性層級是針對格式而定義的：

1. 「完整日期 ' 不是」 ' 部分時間 '」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可[排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) 

        用來格式化 <xref:System.DateTime> 不含小數秒的，且不含位移資訊。

    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF

        用來格式化 <xref:System.DateTime> ，並以小數秒為單位，但不含位移資訊。

2. 「日期時間」
    1. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"

        用來格式化 <xref:System.DateTime> 不含小數秒的，但使用 UTC 時差。

    2. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'SS.FFFFFFFZ

        用來以 <xref:System.DateTime> 小數秒和 UTC 位移來格式化。

    3. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"

        用來格式化 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 不含小數秒，但具有區域位移。

    4. "yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF ( ' + '/'-' ) HH '： ' mm "

        用來格式化 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> （以小數秒為單位），並使用本機位移。

如果或實例的[來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示 <xref:System.DateTime> <xref:System.DateTimeOffset> 在其小數秒的結尾為零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 會將實例的標記法格式化，而不會有尾端零。
例如，如果 <xref:System.DateTime> 實例的[來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示為，則的 `2019-04-24T14:50:17.1010000Z` 格式會是 `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。

如果或實例的[來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示 <xref:System.DateTime> <xref:System.DateTimeOffset> 在其小數秒中全部為零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 會將實例的標記法格式化，而不含小數秒數。
例如，如果 <xref:System.DateTime> 實例的[來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示為，則的 `2019-04-24T14:50:17.0000000+02:00` 格式會是 `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。

以小數秒數來截斷零會允許最小的輸出，以便在要寫入的來回行程上保留資訊。

最多可寫入7個小數秒數位。 這會與實作為配合 <xref:System.DateTime> ，僅限於此解析度。
