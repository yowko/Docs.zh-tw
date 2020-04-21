---
title: 從Newtonsoft.Json移至System.Text.Json- .NET
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0828a5654171df39230055215903d3a49690155d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739243"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>如何從牛頓軟.Json遷移到系統.Text.Json

本文展示如何從[牛頓軟遷移到](https://www.newtonsoft.com/json)<xref:System.Text.Json>。

命名`System.Text.Json`空間提供了從 JAVAScript 物件表示法 (JSON) 序列化和反序列化的功能。 該`System.Text.Json`庫包含在[.NET Core 3.0](https://aka.ms/netcore3download)共用框架中。 對於其他目標框架,請安裝[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 包。 該包支援:

* .NET 標準 2.0 及更高版本
* .NET 框架 4.7.2 及更高版本
* .NET 核心 2.0、2.1 和 2.2

`System.Text.Json`主要關注性能、安全性和標準合規性。 它在默認行為上有一些關鍵差異,並且並不旨在與`Newtonsoft.Json`具有功能奇偶校驗。 對於某些方案,`System.Text.Json`沒有內置功能,但建議使用解決方法。 對於其他方案,解決方法不切實際。 如果應用程式依賴於缺少的功能,請考慮[提交問題](https://github.com/dotnet/runtime/issues/new),以瞭解是否可以添加對方案的支援。

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

本文的大部分內容是關於如何使用<xref:System.Text.Json.JsonSerializer>API 的,但它也包括有關<xref:System.Text.Json.JsonDocument>如何使用 (表示文檔物件模型<xref:System.Text.Json.Utf8JsonReader>或<xref:System.Text.Json.Utf8JsonWriter>DOM) 和 類型的指南。

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>牛頓軟.Json 和系統之間的差異表.文本.Json

下表列出了`Newtonsoft.Json`功能`System.Text.Json`和 等效項。 等效項分為以下幾類:

* 內置功能支援。 從`System.Text.Json`中獲取類似行為可能需要使用屬性或全域選項。
* 不支援,解決方法是可能的。 解決方法是[自訂轉換器](system-text-json-converters-how-to.md),可能無法提供完整的奇偶校`Newtonsoft.Json`驗功能 。 對於其中一些,示例代碼作為示例提供。 如果依賴於這些`Newtonsoft.Json`功能,遷移將需要修改 .NET 物件模型或其他代碼更改。
* 不支援,解決方法不可行或可能。 如果依賴於這些`Newtonsoft.Json`功能,則如果不進行重大更改,遷移就不可能實現。

| 牛頓軟.Json 功能                               | 系統.文字.Json 等效 |
|-------------------------------------------------------|-----------------------------|
| 預設情況下,不區分大小寫的反序列化           | [✔️ 屬性命名Case敏感全域設定](#case-insensitive-deserialization) |
| 駱駝大小寫屬性名稱                             | ✔️[屬性命名策略全域設定](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| 最小字元轉義                            | ✔️[嚴格字元轉義,可配置](#minimal-character-escaping) |
| `NullValueHandling.Ignore`全域設定             | ✔️[忽略空值全域選項](system-text-json-how-to.md#exclude-all-null-value-properties) |
| 允許註解                                        | ✔️ [ReadComment 處理全域設定](#comments) |
| 允許尾隨逗號                                 | ✔️[允許尾隨全球設定](#trailing-commas) |
| 自訂轉換器註冊                         | ✔️[優先權順序不同](#converter-registration-precedence) |
| 預設情況下沒有最大深度                           | ✔️[預設最大深度 64,可設定](#maximum-depth) |
| 支援多種型態                    | ⚠️[某些類型需要自訂轉換器](#types-without-built-in-support) |
| 將字串反序列化為數字                        | ⚠️[不支援,解決方法,示例](#quoted-numbers) |
| 使用非字串`Dictionary`鍵反序列化          | ⚠️[不支援,解決方法,示例](#dictionary-with-non-string-key) |
| 多態序列化                             | ⚠️[不支援,解決方法,示例](#polymorphic-serialization) |
| 多態反序列化                           | ⚠️[不支援,解決方法,示例](#polymorphic-deserialization) |
| 將推斷型態反序列化`object`為 屬性      | ⚠️[不支援,解決方法,示例](#deserialization-of-object-properties) |
| 將 JSON`null`文字序列化為非空值類型 | ⚠️[不支援,解決方法,示例](#deserialize-null-to-non-nullable-type) |
| 反序列化為不可變類別和結構          | ⚠️[不支援,解決方法,示例](#deserialize-to-immutable-classes-and-structs) |
| `[JsonConstructor]` 屬性                         | ⚠️[不支援,解決方法,示例](#specify-constructor-to-use) |
| `Required`屬性上的`[JsonProperty]`設定        | ⚠️[不支援,解決方法,示例](#required-properties) |
| `NullValueHandling`屬性上的`[JsonProperty]`設定 | ⚠️[不支援,解決方法,示例](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`屬性上的`[JsonProperty]`設定 | ⚠️[不支援,解決方法,示例](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`全域設定                 | ⚠️[不支援,解決方法,示例](#conditionally-ignore-a-property) |
| `DefaultContractResolver`以排除屬性       | ⚠️[不支援,解決方法,示例](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`、`DateFormatString`設定   | ⚠️[不支援,解決方法,示例](#specify-date-format) |
| 回撥                                             | ⚠️[不支援,解決方法,示例](#callbacks) |
| 支援公共和非公共欄位              | ⚠️[不支援,解決方法](#public-and-non-public-fields) |
| 支援內部和私有財產設定者和獲取者 | ⚠️[不支援,解決方法](#internal-and-private-property-setters-and-getters) |
| `JsonConvert.PopulateObject` 方法                   | ⚠️[不支援,解決方法](#populate-existing-objects) |
| `ObjectCreationHandling`全域設定               | ⚠️[不支援,解決方法](#reuse-rather-than-replace-properties) |
| 新增到沒有設定器的集合                    | ⚠️[不支援,解決方法](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`全域設定           | ❌ [不支援](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`全域設定                | ❌ [不支援](#preserve-object-references-and-handle-loops) |
| 支援屬性`System.Runtime.Serialization` | ❌ [不支援](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`全域設定                | ❌ [不支援](#missingmemberhandling) |
| 允許沒有引號的屬性名稱                   | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許字串值周圍的單引號              | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許字串屬性的非字串 JSON 值    | ❌ [不支援](#non-string-values-for-string-properties) |

這不是功能的`Newtonsoft.Json`詳盡清單。 該清單包括[GitHub 問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)或[堆疊溢出](https://stackoverflow.com/questions/tagged/system.text.json)帖子中請求的許多方案。 如果此欄位目前沒有範例代碼的方案之一實現解決方法,並且想要分享解決方案,請在此頁面底部**的「回饋」** 部分中選擇**這個頁面**。 這在本文檔的 GitHub 儲存庫中造成了問題,並在此頁上**的「反饋」** 部分中列出。

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>與牛頓軟相比,預設Json序列器行為的差異

<xref:System.Text.Json>默認情況下嚴格,避免代表呼叫者進行任何猜測或解釋,強調確定性行為。 為了性能和安全性,特意設計了此庫。 `Newtonsoft.Json`默認情況下是靈活的。 這種在設計上的根本差異是以下許多默認行為的具體差異的背後。

### <a name="case-insensitive-deserialization"></a>區分大小寫反序列化

在反序列化期間`Newtonsoft.Json`,預設情況下執行不區分大小寫的屬性名稱匹配。 <xref:System.Text.Json>默認值區分大小寫,由於執行完全匹配,因此性能更好。 有關如何執行不區分大小寫匹配的資訊,請參閱[不區分大小寫的屬性匹配](system-text-json-how-to.md#case-insensitive-property-matching)。

如果您使用ASP.NET酷間接`System.Text.Json`使用,則無需執行任何操作,`Newtonsoft.Json`例如 。 ASP.NET Core 指定[駱駝大小寫屬性名稱](system-text-json-how-to.md#use-camel-case-for-all-json-property-names)的設置`System.Text.Json`,以及使用 時不區分大小寫的匹配。

### <a name="minimal-character-escaping"></a>最小字元轉義

在序列化期間`Newtonsoft.Json`,對於讓字元通過而不逃避字元相對寬鬆。 也就是說,它不會將它們替換為`\uxxxx``xxxx`字元的代碼點。 當它從它們轉義時,它通過在字元之前發出`\`一個(例如,`"`變`\"`為 ) 來這樣做。 <xref:System.Text.Json>默認情況下,可以逃避更多字元,以提供縱深防禦,防止跨網站腳本 (XSS) 或信息洩露攻擊,並使用六個字元序列這樣做。 `System.Text.Json`預設情況下,將轉義所有非 ASCII 字元,因此,`StringEscapeHandling.EscapeNonAscii`如果您在`Newtonsoft.Json`中使用 ,則無需執行任何操作。 `System.Text.Json`預設情況下,也會轉義對 HTML 敏感的字元。 有關如何重寫預設`System.Text.Json`行為的資訊,請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="comments"></a>註解

在反序列化期間`Newtonsoft.Json`,默認情況下忽略 JSON 中的註釋。 默認值<xref:System.Text.Json>是引發註釋異常,因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規範不包括它們。 有關如何允許註釋的資訊,請參閱[允許註解和尾隨逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。

### <a name="trailing-commas"></a>尾隨逗號

在反序列化期間`Newtonsoft.Json`,預設情況下忽略尾隨逗號。 它還忽略多個尾隨逗號(例如, `[{"Color":"Red"},{"Color":"Green"},,]`。 默認值<xref:System.Text.Json>是引發尾隨逗號的異常,因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規範不允許它們。 有關如何接受`System.Text.Json`它們的資訊,請參閱[允許註解和尾隨逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。 無法允許多個尾隨逗號。

### <a name="converter-registration-precedence"></a>轉換器註冊優先權

自訂`Newtonsoft.Json`轉換器的註冊優先順序如下:

* 屬性屬性
* 類型的屬性
* [轉換器](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)集合

此順序表示集合中的`Converters`自定義轉換器由通過在類型級別應用屬性而註冊的轉換器覆蓋。 這兩個註冊都由屬性級別的屬性覆蓋。

自訂<xref:System.Text.Json>轉換器的註冊優先權不同:

* 屬性屬性
* <xref:System.Text.Json.JsonSerializerOptions.Converters>收集
* 類型的屬性

此處的區別是`Converters`集合中的自定義轉換器在類型級別覆蓋屬性。 此優先順序順序背後的意圖是使運行時更改覆蓋設計時選擇。 沒有辦法更改優先順序。

有關自訂轉換器註冊的詳細資訊,請參閱[註冊自訂轉換器](system-text-json-converters-how-to.md#register-a-custom-converter)。

### <a name="maximum-depth"></a>最大深度

`Newtonsoft.Json`默認情況下,沒有最大深度限制。 對於<xref:System.Text.Json>有一個預設限制 64,並且<xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>可以通過設置 來配置。

### <a name="json-strings-property-names-and-string-values"></a>JSON 字串(屬性名稱和字串值)

在反序列化期間`Newtonsoft.Json`,接受由雙引號、單引號或無引弧括起來的屬性名稱。 它接受由雙引號或單引弧括起來的字串值。 例如,`Newtonsoft.Json`接受以下 JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`僅接受雙引號的屬性名稱和字串值,因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規範需要該格式,並且是唯一被視為有效 JSON 的格式。

包含在單個報價中的值會產生[JsonException,](xref:System.Text.Json.JsonException)並顯示以下訊息:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>字串屬性的非字串值

`Newtonsoft.Json`接受非字串值,如數位或文本`true`和`false`,以便對類型字串的屬性進行反序列化。 下面是 JSON 的範例,`Newtonsoft.Json`它成功地反序列化到以下類:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json`不會將非字串值解序列化為字串屬性。 為字串欄位接收的非字串值會導致[JonException,](xref:System.Text.Json.JsonException)並顯示以下訊息:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>使用 Json 序列化器需要解決方法的方案

內置功能不支援以下方案,但可以採用解決方法。 解決方法是[自訂轉換器](system-text-json-converters-how-to.md),可能無法提供完整的奇偶校`Newtonsoft.Json`驗功能 。 對於其中一些,示例代碼作為示例提供。 如果依賴於這些`Newtonsoft.Json`功能,遷移將需要修改 .NET 物件模型或其他代碼更改。

### <a name="types-without-built-in-support"></a>沒有內置支援的類型

<xref:System.Text.Json>不為以下類型提供內置支援:

* <xref:System.Data.DataTable>與相關類型
* F# 類型,例如[區分聯合](../../fsharp/language-reference/discriminated-unions.md),[以及匿名](../../fsharp/language-reference/records.md)[紀錄型態](../../fsharp/language-reference/anonymous-records.md)。
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>及其關聯的泛型型態

可以為沒有內置支援的類型實現自定義轉換器。

### <a name="quoted-numbers"></a>報價數字

`Newtonsoft.Json`可以序列化或去序列化 JSON 字串表示的數位(由引號包圍)。 例如,它可以接受:`{"DegreesCelsius":"23"}`而不是`{"DegreesCelsius":23}`。 要在<xref:System.Text.Json>中 啟用該行為,可以實現自定義轉換器,如下所示。 轉換器處理定義為`long`的屬性:

* 它將它們序列化為 JSON 字串。
* 它在反序列化時接受報價中的JSON數位和數位。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

`long`通過在單個屬性上[使用屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)或[將轉換器添加到](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>集合中來註冊此自定義轉換器。

### <a name="dictionary-with-non-string-key"></a>產生字串鍵的字典

`Newtonsoft.Json`支持類型的`Dictionary<TKey, TValue>`集合。 中<xref:System.Text.Json>對字典集合的內建支援僅限`Dictionary<string, TValue>`於 。 也就是說,鍵必須是字串。

要支援以整數或某種類型的字典作為鍵,請創建一個轉換器,如[「如何編寫自定義轉換器](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)」中的範例。

### <a name="polymorphic-serialization"></a>多態序列化

`Newtonsoft.Json`自動執行多態序列化。 有關的有限多態序列化功能的<xref:System.Text.Json>資訊 ,請參閱[派生類 的序列化屬性](system-text-json-how-to.md#serialize-properties-of-derived-classes)。

描述現有的解決方法是定義可能包含指定的類別的屬性為`object`類型 。 如果這是不可能的,另一個選項是建立一個`Write`轉換器,該方法為整個繼承類型層次結構,如範例在[如何編寫自定義轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)。

### <a name="polymorphic-deserialization"></a>多態反序列化

`Newtonsoft.Json`具有在`TypeNameHandling`序列化時向 JSON 添加類型名稱元數據的設置。 它使用元數據,同時反序列化,以執行多態反序列化。 <xref:System.Text.Json>可以做有限範圍的[多態序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes),但不能進行多態反序列化。

要支援多態反序列化,請建立一個轉換器,如[「如何編寫自定義轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)」中的範例。

### <a name="deserialization-of-object-properties"></a>物件屬性的序列化

當`Newtonsoft.Json`反序列化<xref:System.Object>到 時, 它:

* 推斷 JSON 有效`null`負載 (非)中的原始值的類型,`string`並返回`boolean``DateTime``long``double`存儲 的 、、、、 或作為盒裝物件。 *基元值*是單一 JSON 值,`true`如`false`JSON 編`null`號、字串、或 。
* 返回`JObject``JArray`或用於 JSON 負載中的複雜值。 *複雜值*是大括號 ( )`{}`內的 JSON 鍵值對的`[]`集合, 或括弧內 的值清單 ( 。 大括弧或括弧中的屬性和值可以具有其他屬性或值。
* 當有效負載具有`null`JSON 文本時,傳回 null 引用。

<xref:System.Text.Json>每當序列化<xref:System.Object>到`JsonElement`時,儲存基元值和複雜值的裝箱,例如:

* `object` 屬性。
* `object`字典值。
* `object`陣列值。
* 根`object`。

但是,`System.Text.Json``null`當有效負載`Newtonsoft.Json`中`null`包含 JSON 文本時,請處理和返回空引用的相同。

要實現`object`屬性的類型推理,請建立一個轉換器,如[「如何編寫自定義轉換器](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)」中的範例。

### <a name="deserialize-null-to-non-nullable-type"></a>將空序列化為非空型態

`Newtonsoft.Json`在以下情況下不會引發異常:

* `NullValueHandling`設定為`Ignore`與
* 在反序列化期間,JSON包含非空值類型的空值。

在同一方案中,<xref:System.Text.Json>確實會引發異常。 ( 相關的空處理設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>為 .)

如果您擁有目標類型,則最佳解決方法是使有問題的屬性為空(例如,更改為`int``int?`。

另一種解決方法是為類型建立轉換器,例如處理`DateTimeOffset`類型空值的以下範例:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

[通過使用屬性上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)或[將轉換器添加到](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>集合中來註冊此自定義轉換器。

**註:** 前面的轉換器**處理空值**`Newtonsoft.Json`的方式與 指定預設值的 POCO 不同。 例如,假設以下代碼表示目標物件:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

假設使用上述轉換器對以下 JSON 進行反序列化:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

反序列化後,`Date`屬性具有 1/1/0001`default(DateTimeOffset)`(),即建構函數中設置的值將被覆蓋。 鑒於相同的POCO和JSON,`Newtonsoft.Json`去序列化將`Date`留在 財產中1/1/2001。

### <a name="deserialize-to-immutable-classes-and-structs"></a>反序列化為不可變類別和結構

`Newtonsoft.Json`可以反序列化為不可變類和結構,因為它可以使用具有參數的構造函數。 <xref:System.Text.Json>僅支援公共無參數構造函數。 作為解決方法,您可以調用具有自定義轉換器中參數的構造函數。

下面是具有多個建構函數參數的不可變結構:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

下面是一個轉換器,可序列化並取消序列化此結構:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

通過將<xref:System.Text.Json.JsonSerializerOptions.Converters>[轉換器添加到集合中來](system-text-json-converters-how-to.md#registration-sample---converters-collection)註冊此自定義轉換器。

有關處理開啟泛型屬性的類似轉換器的範例,請參閱鍵[值對的內建轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)。

### <a name="specify-constructor-to-use"></a>指定要使用的建構函式

該`Newtonsoft.Json``[JsonConstructor]`屬性允許您指定在反序列化到 POCO 時調用的建構函數。 <xref:System.Text.Json>僅支援無參數構造函數。 作為解決方法,您可以調用自定義轉換器中所需的任何構造函數。 請參考[反序列化到不可變類別與結構的範例](#deserialize-to-immutable-classes-and-structs)。

### <a name="required-properties"></a>必要屬性

在`Newtonsoft.Json`中,通過`Required``[JsonProperty]`在屬性上設置指定屬性是必需的。 `Newtonsoft.Json`如果 JSON 中未收到標記為所需屬性的值,則引發異常。

<xref:System.Text.Json>如果未收到目標類型之一的屬性的值,則不會引發異常。 例如,如果您有一個`WeatherForecast`類別:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

以下 JSON 已反序列化,沒有錯誤:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

要使反序列化失敗,如果`Date`JSON 中沒有屬性,則實現自定義轉換器。 如果解序列化完成後未設定該屬性,`Date`以下範例轉換器代碼將引發異常:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

[使用 POCO 類上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)或[將轉換器添加到](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>集合中來註冊此自定義轉換器。

如果遵循此模式,則在遞歸調用<xref:System.Text.Json.JsonSerializer.Serialize%2A><xref:System.Text.Json.JsonSerializer.Deserialize%2A>或 時不要傳遞選項物件。 選項物件包含<xref:System.Text.Json.JsonSerializerOptions.Converters%2A>集合。 如果將其傳遞到`Serialize``Deserialize`或 ,則自定義轉換器將調用自身,從而產生無限循環,從而導致堆疊溢出異常。 如果預設選項不可行,請使用所需的設定創建選項的新實例。 由於每個新實例單獨緩存,此方法將很慢。

前面的轉換器代碼是一個簡化的範例。 如果需要處理屬性(如[[JsonIgnore] 或](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)不同的選項(如自定義編碼器),則需要其他邏輯。 此外,範例代碼不處理建構函數中為其設置預設值的屬性。 此方法不區分以下機制:

* JSON 中缺少一個屬性。
* 非空類型的屬性存在於 JSON 中,但值是類型的預設值,`int`例如的零。
* 值類型的屬性存在於 JSON 中,但該值為 null。

### <a name="conditionally-ignore-a-property"></a>有條件地忽略屬性

`Newtonsoft.Json`有幾種方法可以有條件地忽略序列化或反序列化的屬性:

* `DefaultContractResolver`允許您根據任意條件選擇要包括或排除的屬性。
* `NullValueHandling`和`DefaultValueHandling`上的`JsonSerializerSettings`設定允許您指定應忽略所有空值或預設值屬性。
* 屬性`NullValueHandling``DefaultValueHandling``[JsonProperty]`上的和 設定允許您指定在設定為 null 或預設值時應忽略的單個屬性。

<xref:System.Text.Json>提供序列化時省略屬性的以下方法:

* 屬性上的[[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties)屬性會導致在序列化期間從 JSON 中省略該屬性。
* 「[忽略 Nullvalue](system-text-json-how-to.md#exclude-all-null-value-properties)全域」選項允許您排除所有空值屬性。
* [通過"忽略只屬性](system-text-json-how-to.md#exclude-all-read-only-properties)"全域選項,可以排除所有唯讀屬性。

這些選項**不**允許您:

* 忽略具有類型預設值的所有屬性。
* 忽略具有類型預設值的選定屬性。
* 如果所選屬性的值為空,則忽略它們。
* 忽略基於運行時計算的任意條件選擇的屬性。

對於該功能,您可以編寫自定義轉換器。 下面是一個範例 POCO 和一個自訂轉換器,說明了此方法:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

如果`Summary`該屬性的值為空、空字串或"N/A",則轉換器會導致在序列化中省略該屬性。

通過在[類中使用屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)或將[轉換器添加到](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>集合中來註冊此自定義轉換器。

此方法需要額外的邏輯,如果:

* POCO 包含複雜的屬性。
* 您需要處理屬性,如`[JsonIgnore]`或選項,如自定義編碼器。

### <a name="specify-date-format"></a>指定日期格式

`Newtonsoft.Json`提供幾種控制`DateTime`屬性`DateTimeOffset`與類型序列化與非序列化的方法:

* 該`DateTimeZoneHandling`設定可用於將`DateTime`所有 值序列化為 UTC 日期。
* 設定`DateFormatString`和`DateTime`轉換器可用於自訂日期字串的格式。

在<xref:System.Text.Json>中,唯一具有內置支援的格式是 ISO 8601-1:2019,因為它被廣泛採用、明確且精確進行往返。 要使用任何其他格式,請創建自定義轉換器。 有關詳細資訊,請參閱[系統中的日期時間和日期時間偏移支援。](../datetime/system-text-json-support.md)

### <a name="callbacks"></a>回撥

`Newtonsoft.Json`允許您在序列化或反序列化過程的幾個點執行自訂碼:

* 開啟序列化(開始反序列化物件時)
* 開啟序列化(完成物件反序列化時)
* 在序列化時(開始序列化物件時)
* 序列化時(完成序列化物件時)

在<xref:System.Text.Json>中,可以通過編寫自定義轉換器來模擬回調。 下面的範例顯示了 POCO 的自定義轉換器。 轉換器包括代碼,該代碼在每個點顯示對應於`Newtonsoft.Json`回調的消息。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

通過在[類中使用屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)或將[轉換器添加到](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>集合中來註冊此自定義轉換器。

如果使用遵循此範例的自訂轉換器:

* 代碼`OnDeserializing`無法造訪新的 POCO 實體。 要在反序列化開始時操作新的 POCO 實例,請將該代碼放入 POCO 構造函數中。
* 遞迴呼用`Serialize``Deserialize`或 時,不要傳遞選項物件。 選項物件包含`Converters`集合。 如果將其傳遞到`Serialize``Deserialize`或 ,則將使用轉換器,從而產生無限迴圈,從而導致堆疊溢出異常。

### <a name="public-and-non-public-fields"></a>公開和非公共欄位

`Newtonsoft.Json`可以序列化欄位和屬性。 <xref:System.Text.Json>僅適用於公共屬性。 自定義轉換器可以提供此功能。

### <a name="internal-and-private-property-setters-and-getters"></a>內部和私有財產設定者和獲取者

`Newtonsoft.Json`可以使用私有和內部屬性設置器和獲取器通過`JsonProperty`屬性。 <xref:System.Text.Json>僅支援公共設置器。 自定義轉換器可以提供此功能。

### <a name="populate-existing-objects"></a>填滿現有物件

解`JsonConvert.PopulateObject`序列`Newtonsoft.Json`化 的 JSON 文件到類的現有實例,而不是創建新實例。 <xref:System.Text.Json>始終使用預設的公共無參數建構函數創建目標類型的新實例。 自定義轉換器可以反序列化到現有實例。

### <a name="reuse-rather-than-replace-properties"></a>重用而非取代屬性

該`Newtonsoft.Json``ObjectCreationHandling`設置允許您指定屬性中的物件應重複使用,而不是在反序列化期間替換。 <xref:System.Text.Json>始終替換屬性中的物件。  自定義轉換器可以提供此功能。

### <a name="add-to-collections-without-setters"></a>新增到沒有設定器的集合

在反序列化期間`Newtonsoft.Json`,即使屬性沒有 setter,也會將物件添加到集合中。 <xref:System.Text.Json>忽略沒有設置器的屬性。 自定義轉換器可以提供此功能。

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Json 序列化程式目前不支援的機制

對於以下方案,解決方法不可行或不可能。 如果依賴於這些`Newtonsoft.Json`功能,則如果不進行重大更改,遷移就不可能實現。

### <a name="preserve-object-references-and-handle-loops"></a>保留物件參考與句柄迴圈

預設情況下,`Newtonsoft.Json`按值序列化。 例如,如果物件包含兩個屬性,其中包含對同`Person`一物件的引用,則`Person`該 物件的屬性的值將複製在 JSON 中。

`Newtonsoft.Json`具有允許您`PreserveReferencesHandling`按`JsonSerializerSettings`參考 序列化設定:

* 標識符元數據將添加到為第一個`Person`對象創建的 JSON 中。
* 為第二`Person`個對象創建的 JSON 包含對該識別碼的引用,而不是屬性值。

`Newtonsoft.Json`還有一個`ReferenceLoopHandling`設置,允許您忽略迴圈引用,而不是引發異常。

<xref:System.Text.Json>僅支援按值序列化,並為迴圈引用引發異常。

### <a name="systemruntimeserialization-attributes"></a>系統.執行時.序列化屬性

<xref:System.Text.Json>不支援命名空間的屬性`System.Runtime.Serialization`,如`DataMemberAttribute`與`IgnoreDataMemberAttribute`。

### <a name="octal-numbers"></a>八進位數字

`Newtonsoft.Json`將前導零的數位視為八進位數位。 <xref:System.Text.Json>不允許前導零,因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規範不允許它們。

### <a name="missingmemberhandling"></a>缺少成員處理

`Newtonsoft.Json`如果 JSON 包含目標類型中缺少的屬性,則可以配置為在反序列化期間引發異常。 <xref:System.Text.Json>忽略 JSON 中的額外屬性,除非使用[[Json 延伸資料] 屬性](system-text-json-how-to.md#handle-overflow-json)。 缺少的成員功能沒有解決方法。

### <a name="tracewriter"></a>追蹤寫器

`Newtonsoft.Json`允許您使用`TraceWriter`查看 序列化或反序列化生成的日誌來調試。 <xref:System.Text.Json>不進行日誌記錄。

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>與 JToken 相比,JsonDocument 和 JsonElement(如 JObject、JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>提供了從現有 JSON 負載解析和構建**唯讀**文件物件模型 (DOM) 的能力。 DOM 提供對 JSON 負載中數據的隨機訪問。 構成有效負載的 JSON 元素可<xref:System.Text.Json.JsonElement>通過類型 進行訪問。 該`JsonElement`類型提供 API 以將 JSON 文本轉換為常見的 .NET 類型。 `JsonDocument`公開<xref:System.Text.Json.JsonDocument.RootElement>屬性。

### <a name="jsondocument-is-idisposable"></a>JsonDocument 是 I 一次性的

`JsonDocument`將數據的記憶體中視圖構建到池緩衝區中。 因此,與`JObject``JArray`或`Newtonsoft.Json`不同`JsonDocument`,`IDisposable`類型實現和需要在 using 塊內使用。

僅當要將`JsonDocument`存留期所有權轉移並釋放責任給調用方時,才從 API 返回 。 在大多數情況下,這是沒有必要的。 如果呼叫者需要處理整個 JSON 文件,<xref:System.Text.Json.JsonElement.Clone%2A><xref:System.Text.Json.JsonDocument.RootElement%2A><xref:System.Text.Json.JsonElement>則傳回 。 如果調用方需要使用 JSON 文檔中的特定元素,<xref:System.Text.Json.JsonElement.Clone%2A><xref:System.Text.Json.JsonElement>則返回該 元素。 如果在不創建`RootElement`的情況下直接返回 或`Clone`子元素 ,則調用方將`JsonElement``JsonDocument`無法在釋放 擁有的 返回后訪問返回。

下面是一個範例,要求您建立`Clone`:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

前面的代碼需要包含屬性`JsonElement`的`fileName`。 它開啟 JSON 檔`JsonDocument`並建立一個 。 該方法假定呼叫方要處理整個文件,因此傳回`Clone`的`RootElement`。

如果收到`JsonElement`和正在返回子元素,則無需返回子元素的`Clone`a。 調用方負責保持傳入`JsonDocument``JsonElement`所屬的處於活動狀態。 例如：

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument 是唯讀的

DOM<xref:System.Text.Json>無法添加、刪除或修改 JSON 元素。 它以這種方式設計是為了提高性能,並減少了用於分析常見 JSON 有效負載大小(即< 1 MB)的分配。 如果方案目前使用可修改的 DOM,則以下解決方法之一可能是可行的:

* 要從頭`JsonDocument`開始產生一個(即,不將現有的 JSON`Parse`負載 傳遞到方法),請使用`Utf8JsonWriter`編寫 JSON 文本,並`JsonDocument`分析該中的輸出以產生新的 。
* 要修改現有文字`JsonDocument`,請使用它編寫 JSON 文字,在寫入時進行變更,並分析其輸出`JsonDocument`以建立新 。
* 要合併現有的 JSON 文件,`JObject.Merge`等`JContainer.Merge`效`Newtonsoft.Json`於中的或 API,請參閱[此 GitHub 問題](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)。

### <a name="jsonelement-is-a-union-struct"></a>JsonElement 是一個聯合結構

`JsonDocument`公開`RootElement`為類型<xref:System.Text.Json.JsonElement>的 屬性 ,它是包含任何 JSON 元素的聯合結構類型。 `Newtonsoft.Json`使用專用分層類型,`JObject``JArray``JToken`如 、、、等。 `JsonElement`是您可以搜尋和枚舉的內容,您可以使用`JsonElement`將 JSON 元素具體化到 .NET 類型中。

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>如何搜尋 JsonDocument 和 JsonElement 的子元素

使用`JObject``JArray`或`Newtonsoft.Json`從 中搜索 JSON 令牌往往相對較快,因為它們是某些字典中的查找。 相比之下,搜索需要`JsonElement`按順序搜索屬性,因此相對較慢(例如,使用`TryGetProperty`時)。 <xref:System.Text.Json>旨在最小化初始分析時間,而不是查找時間。 因此,在搜尋`JsonDocument`物件時,請使用以下方法來優化性能:

* 使用內建枚舉器(<xref:System.Text.Json.JsonElement.EnumerateArray%2A><xref:System.Text.Json.JsonElement.EnumerateObject%2A>和 ) 而不是執行自己的索引或迴圈。
* 不要使用`RootElement`每個屬性執行順序搜尋`JsonDocument`。 相反,根據 JSON 數據的已知結構搜索嵌套的 JSON 物件。 例如`Grade`,如果要在物件`Student`中 尋找屬性,則迴圈遍`Student`歷 物件並獲取 每個`Grade`物件的值,`JsonElement`而不是搜索`Grade`所有查找 屬性的物件。 執行後者將導致對同一數據進行不必要的傳遞。

有關代碼範例,請參閱[使用 JsonDocument 存取資料](system-text-json-how-to.md#use-jsondocument-for-access-to-data)。

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader 與 JsonTextReader 相比

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>是 UTF-8 編碼 JSON 文本的高性能、低分配、僅轉發讀取器,從[ReadOnlySpan\<位元組>](xref:System.ReadOnlySpan%601)讀取或[\<ReadOnlySequence 位元組>](xref:System.Buffers.ReadOnlySequence%601)。 `Utf8JsonReader`是一種低級類型,可用於構建自定義解析器和反序列化器。

以下各節解釋使用`Utf8JsonReader`的建議程式設計模式。

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JonReader 是一個參考結構

由於`Utf8JsonReader`類型是*ref 結構*,因此具有[某些限制](../../csharp/language-reference/builtin-types/struct.md#ref-struct)。 例如,不能將其存儲為類或結構上的欄位,而不是 ref 結構。 為了實現高性能,此類型必須是 a,`ref struct`因為它需要緩存輸入[ReadOnlySpan\<位元組>](xref:System.ReadOnlySpan%601),這本身就是一個 ref 結構。 此外,此類型是可變的,因為它保持狀態。 因此,透過 ref 而不是按值**傳遞它**。 按值傳遞它將導致結構副本,並且調用方看不到狀態更改。 這與`Newtonsoft.Json``Newtonsoft.Json``JsonTextReader`因為是類不同。 有關如何使用 ref 結構的詳細資訊,請參閱[編寫安全高效的 C# 程式碼](../../csharp/write-safe-efficient-code.md)。

### <a name="read-utf-8-text"></a>閱讀 UTF-8 文字

為了在使用 時獲得最佳性能`Utf8JsonReader`, 請閱讀 JSON 有效負載,該負載已編碼為 UTF-8 文本,而不是 UTF-16 字串。 有關代碼示例,請參閱[使用Utf8JonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader)篩選數據。

### <a name="read-with-a-stream-or-pipereader"></a>使用串流或導管閱讀器進行讀取

支援`Utf8JsonReader`從 UTF-8 編碼的[ReadOnlySpan\<位元組>](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<位元組>(](xref:System.Buffers.ReadOnlySequence%601)這是從 讀取的結果<xref:System.IO.Pipelines.PipeReader>)讀取。

對於同步讀取,您可以讀取 JSON 有效負載,直到流結束進入位元組,並將其傳遞到讀取器中。 對於從字串(編碼為 UTF-16)讀取,呼叫<xref:System.Text.Encoding.UTF8>。<xref:System.Text.Encoding.GetBytes%2A> 首先將字串轉碼到 UTF-8 編碼位元組。 然後傳遞給`Utf8JsonReader`。

由於`Utf8JsonReader`將輸入視為 JSON 文本,因此 UTF-8 位元組訂單標記 (BOM) 被視為無效的 JSON。 調用方在將數據傳遞給讀取器之前需要篩選出來。

有關代碼範例,請參閱[使用 Utf8JonReader](system-text-json-how-to.md#use-utf8jsonreader)。

### <a name="read-with-multi-segment-readonlysequence"></a>使用多段 ReadOnlySequence 進行讀取

如果您的 JSON 輸入是[ReadOnlySpan\<位元組>,](xref:System.ReadOnlySpan%601)則在讀取迴圈時`ValueSpan`,可以從讀取器 的屬性訪問每個 JSON 元素。 但是,如果輸入是[ReadOnlySequence\<位元組>(](xref:System.Buffers.ReadOnlySequence%601)這是<xref:System.IO.Pipelines.PipeReader>從讀取的結果 ),則某些`ReadOnlySequence<byte>`JSON 元素可能跨越 物件的多個段。 這些元素無法從<xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>連續記憶體塊中訪問。 相反,每當將多段`ReadOnlySequence<byte>`作為輸入時,在讀取器上<xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A>輪詢屬性以瞭解如何訪問當前 JSON 元素。 下面是推薦的模式:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>對屬性名稱尋找使用 ValueText 等值

不要使用<xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>通過調<xref:System.MemoryExtensions.SequenceEqual%2A>用 屬性名稱查找來逐位元組比較。 請<xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>改為調用,因為該方法將取消轉義 JSON 中轉義的任何字元。 下面是示範如何搜尋名為「name」的屬性的範例:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>將空值讀取為空值類型

`Newtonsoft.Json`<xref:System.Nullable%601>提供`ReadAsBoolean`傳回的 API,`Null``TokenType`例如, 透過`bool?`傳回來處理 內置`System.Text.Json`API 僅返回不可消除的值類型。 例如,<xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType>傳`bool`回 。 如果在 JSON`Null`中找到,它將引發異常。 以下範例顯示了處理 null 的兩種方法,一種是透過回空值類型,另一種透過回預設值來處理空:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>多目標

如果需要繼續用於`Newtonsoft.Json`某些目標框架,則可以多目標並具有兩個實現。 然而,這不是微不足道的,需要一些`#ifdefs`和來源重複。 `ref struct`共用盡可能多的代碼的一種方法是`Utf8JsonReader`圍繞`Newtonsoft.Json``JsonTextReader`和創建包裝器。 此包裝器將統一公共表面積,同時隔離行為差異。 這樣,您就可以隔離主要對類型構造的更改,以及通過引用傳遞新類型。 這是[Microsoft.擴展.依賴模型](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)庫遵循的模式:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter 與 JsonTextWriter 相比

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>是從常見的 .NET 類型`String`(`Int32`如`DateTime`) 和 寫入 UTF-8 編碼的 JSON 文本的高性能方法。 編寫器是一種低級類型,可用於構建自定義序列化程式。

以下各節解釋使用`Utf8JsonWriter`的建議程式設計模式。

### <a name="write-with-utf-8-text"></a>使用 UTF-8 文書寫

為了在使用 時獲得最佳性能`Utf8JsonWriter`, 請編寫 JSON 有效負載,該負載已編碼為 UTF-8 文本,而不是 UTF-16 字串。 用於<xref:System.Text.Json.JsonEncodedText>將已知的字串屬性名稱和值緩存和預編碼為靜態,並將這些名稱和值傳遞給編寫器,而不是使用 UTF-16 字串文字。 這比緩存和使用 UTF-8 位元組陣組更快。

如果需要執行自定義轉義,此方法也有效。 `System.Text.Json`不要讓您在編寫字串時關閉轉義。 但是,您可以將自己的自定義作為選項傳遞給編寫<xref:System.Text.Encodings.Web.JavaScriptEncoder>器,或者創建自己的自定義`JsonEncodedText`項 ,`JavascriptEncoder`使用執行轉義,然後`JsonEncodedText`編寫 而不是字串。 關於詳細資訊,請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="write-raw-values"></a>寫入原始值

該方法`Newtonsoft.Json``WriteRawValue`在預期值的地方寫入原始 JSON。 <xref:System.Text.Json>沒有直接等效項,但下面是一種確保僅寫入有效 JSON 的解決方法:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>自訂字元轉義

[StringEscape處理](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)`JsonTextWriter`設定 提供了用於轉義所有非 ASCII 字元**或**HTML 字元的選項。 預設情況下,`Utf8JsonWriter`將轉義所有非 ASCII**和**HTML 字元。 此逃生是出於深度安全防禦的原因。 要指定不同的轉義策略,請建立<xref:System.Text.Encodings.Web.JavaScriptEncoder>與<xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>集 。 關於詳細資訊,請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="customize-json-format"></a>自訂 JSON 格式

`JsonTextWriter`包括以下設定,這些`Utf8JsonWriter`設定沒有等效設定:

* [縮排](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm)- 指定縮排的字元數。 `Utf8JsonWriter`總是做兩個字元的縮進。
* [縮排符](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm)- 指定用於縮排的字元。  `Utf8JsonWriter`始終使用空白。
* [報價字元](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm)─ 指定用於環繞字串值的字元。  `Utf8JsonWriter`始終使用雙引號。
* [報價名稱](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm)- 指定是否用引號括括屬性名稱。  `Utf8JsonWriter`總是用引號包圍他們。

沒有解決方法可以允許您自定義`Utf8JsonWriter`以這些方式生成的 JSON。

### <a name="write-null-values"></a>寫入空值

要使用 呼`Utf8JsonWriter`叫 寫入空值:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>編寫一個鍵值對,其中 null 為值。
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>將 null 寫入 JSON 陣列的元素。

對字串屬性,如果<xref:System.Text.Json.Utf8JsonWriter.WriteString%2A>字串為 null,並且<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>等效於`WriteNull`與`WriteNullValue`。

### <a name="write-timespan-uri-or-char-values"></a>寫入時間跨度、Uri 或字元值

`JsonTextWriter`提供了`WriteValue` [TimeSpan、Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm)和[字元](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm)[Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)值的方法。 `Utf8JsonWriter`沒有等效的方法。 相反,將這些值格式化為字串(例如,`ToString()`透過呼叫)和呼叫<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>。

### <a name="multi-targeting"></a>多目標

如果需要繼續用於`Newtonsoft.Json`某些目標框架,則可以多目標並具有兩個實現。 然而,這不是微不足道的,需要一些`#ifdefs`和來源重複。 共用盡可能多的代碼的一種方法是`Utf8JsonWriter`圍繞`Newtonsoft``JsonTextWriter`和創建包裝器。 此包裝器將統一公共表面積,同時隔離行為差異。 這允許您隔離主要對類型的構造的更改。 [Microsoft.擴展.依賴模型](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)庫如下:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>其他資源

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Json概述](system-text-json-overview.md)
* [如何使用System.Text.Json](system-text-json-how-to.md)
* [如何撰寫自訂轉換器](system-text-json-converters-how-to.md)
* [日期時間與日期時間位移支援System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonAPI 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
