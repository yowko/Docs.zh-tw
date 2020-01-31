---
title: 從 Newtonsoft.Json 遷移至 System.Text.Json-.NET
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
ms.openlocfilehash: 588a36c70d31883f79a4449d69cb4ba3b4239b9f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741560"
---
# <a name="how-to-migrate-from-opno-locnewtonsoftjson-to-opno-locsystemtextjson"></a>如何從 [!OP.NO-LOC(Newtonsoft.Json)] 遷移至 [!OP.NO-LOC(System.Text.Json)]

本文說明如何從[[!OP.NO-LOC(Newtonsoft.Json)]](https://www.newtonsoft.com/json)遷移至 <xref:[!OP.NO-LOC(System.Text.Json)]>。

`[!OP.NO-LOC(System.Text.Json)]` 主要著重于效能、安全性和標準合規性。 它在預設行為上有一些主要差異，並不是要與 `[!OP.NO-LOC(Newtonsoft.Json)]`的功能同位。 在某些情況下，`[!OP.NO-LOC(System.Text.Json)]` 沒有內建功能，但有建議的因應措施。 針對其他案例，因應措施並不實用。 如果您的應用程式相依于遺失的功能，請考慮提出[問題](https://github.com/dotnet/runtime/issues/new)，以瞭解是否可以新增您案例的支援。

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/roadmap/README.md). [Restore this when the roadmap is updated.]-->

本文大部分是關於如何使用 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializer> API，但它也包含如何使用 <xref:[!OP.NO-LOC(System.Text.Json)].JsonDocument> （代表檔物件模型或 DOM）、<xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader>和 <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> 類型的指引。

## <a name="table-of-differences-between-opno-locnewtonsoftjson-and-opno-locsystemtextjson"></a>[!OP.NO-LOC(Newtonsoft.Json)] 和 [!OP.NO-LOC(System.Text.Json)] 之間的差異資料表

下表列出 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能和 `[!OP.NO-LOC(System.Text.Json)]` 對應項。 對等專案屬於下列類別：

* 受到內建功能的支援。 從 `[!OP.NO-LOC(System.Text.Json)]` 取得類似的行為，可能需要使用屬性或全域選項。
* 不支援，可能的解決方法。 因應措施是[自訂轉換器](system-text-json-converters-how-to.md)，可能不會提供與 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能完全同位檢查。 其中一些範例程式碼會以範例的形式提供。 如果您依賴這些 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能，則必須修改您的 .NET 物件模型或其他程式碼變更，才能進行遷移。
* 不支援，因應措施不可行或無法解決。 如果您依賴這些 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能，則不會有重大變更，因此無法進行遷移。

| [!OP.NO-LOC(Newtonsoft.Json)] 功能                               | [!OP.NO-LOC(System.Text.Json)] 對等 |
|-------------------------------------------------------|-----------------------------|
| 預設不區分大小寫的還原序列化           | ✔️ [PropertyNameCaseInsensitive 全域設定](#case-insensitive-deserialization) |
| Camel 大小寫屬性名稱                             | ✔️ [PropertyNamingPolicy 全域設定](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| 最少字元的轉義                            | ✔️[嚴格的字元轉義，可](#minimal-character-escaping)設定 |
| `NullValueHandling.Ignore` 的全域設定             | ✔️ [IgnoreNullValues global 選項](system-text-json-how-to.md#exclude-all-null-value-properties) |
| 允許批註                                        | ✔️ [ReadCommentHandling 全域設定](#comments) |
| 允許尾端逗號                                 | ✔️ [AllowTrailingCommas 全域設定](#trailing-commas) |
| 自訂轉換器註冊                         | ✔️[優先順序的順序不同](#converter-registration-precedence) |
| 預設無最大深度                           | ✔️[預設的最大深度64，可](#maximum-depth)設定 |
| 支援廣泛的類型                    | ⚠️[某些類型需要自訂轉換器](#types-without-built-in-support) |
| 將字串還原序列化為數字                        | ⚠️[不受支援、](#quoted-numbers)因應措施、範例 |
| 使用非字串索引鍵還原序列化 `Dictionary`          | ⚠️[不受支援、](#dictionary-with-non-string-key)因應措施、範例 |
| 多型序列化                             | ⚠️[不受支援、](#polymorphic-serialization)因應措施、範例 |
| 多型還原序列化                           | ⚠️[不受支援、](#polymorphic-deserialization)因應措施、範例 |
| 將推斷的類型還原序列化為 `object` 屬性      | ⚠️[不受支援、](#deserialization-of-object-properties)因應措施、範例 |
| 將 JSON `null` 常值還原序列化為不可為 null 的類型 | ⚠️[不受支援、](#deserialize-null-to-non-nullable-type)因應措施、範例 |
| 還原序列化為不可變的類別和結構          | ⚠️[不受支援、](#deserialize-to-immutable-classes-and-structs)因應措施、範例 |
| `[JsonConstructor]` 屬性                         | ⚠️[不受支援、](#specify-constructor-to-use)因應措施、範例 |
| `[JsonProperty]` 屬性上的 `Required` 設定        | ⚠️[不受支援、](#required-properties)因應措施、範例 |
| `[JsonProperty]` 屬性上的 `NullValueHandling` 設定 | ⚠️[不受支援、](#conditionally-ignore-a-property)因應措施、範例  |
| `[JsonProperty]` 屬性上的 `DefaultValueHandling` 設定 | ⚠️[不受支援、](#conditionally-ignore-a-property)因應措施、範例  |
| `DefaultValueHandling` 的全域設定                 | ⚠️[不受支援、](#conditionally-ignore-a-property)因應措施、範例 |
| 排除屬性的 `DefaultContractResolver`       | ⚠️[不受支援、](#conditionally-ignore-a-property)因應措施、範例 |
| `DateTimeZoneHandling`，`DateFormatString` 設定   | ⚠️[不受支援、](#specify-date-format)因應措施、範例 |
| 叫                                             | ⚠️[不受支援、](#callbacks)因應措施、範例 |
| 支援公用和非公用欄位              | ⚠️[不受支援，](#public-and-non-public-fields)因應措施 |
| 支援內部和私用屬性 setter 和 getter | ⚠️[不受支援，](#internal-and-private-property-setters-and-getters)因應措施 |
| `JsonConvert.PopulateObject` 方法                   | ⚠️[不受支援，](#populate-existing-objects)因應措施 |
| `ObjectCreationHandling` 的全域設定               | ⚠️[不受支援，](#reuse-rather-than-replace-properties)因應措施 |
| 新增至不含 setter 的集合                    | ⚠️[不受支援，](#add-to-collections-without-setters)因應措施 |
| `PreserveReferencesHandling` 的全域設定           | [不支援](#preserve-object-references-and-handle-loops)❌ |
| `ReferenceLoopHandling` 的全域設定                | [不支援](#preserve-object-references-and-handle-loops)❌ |
| 支援 `System.Runtime.Serialization` 屬性 | [不支援](#systemruntimeserialization-attributes)❌ |
| `MissingMemberHandling` 的全域設定                | [不支援](#missingmemberhandling)❌ |
| 允許沒有引號的屬性名稱                   | [不支援](#json-strings-property-names-and-string-values)❌ |
| 允許字串值前後加上單引號              | [不支援](#json-strings-property-names-and-string-values)❌ |
| 允許字串屬性的非字串 JSON 值    | [不支援](#non-string-values-for-string-properties)❌ |

這不是 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能的詳盡清單。 此清單包含[GitHub 問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-[!OP.NO-LOC(System.Text.Json)])或[StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json)文章中所要求的許多案例。 如果您針對此處所列的其中一個案例執行因應措施，但目前沒有範例程式碼，而且您想要共用您的方案，請在此頁面的 [意見反應][區段](/dotnet/standard/serialization/system-text-json-migrate-from-newtonsoft-how-to#feedback)中選取**此頁面**。 這會建立 GitHub 問題，並將其列在此頁面底部。

## <a name="differences-in-default-jsonserializer-behavior-compared-to-opno-locnewtonsoftjson"></a>相較于 [!OP.NO-LOC(Newtonsoft.Json)]，預設 JsonSerializer 行為的差異

<xref:[!OP.NO-LOC(System.Text.Json)]> 預設為嚴格，並可避免代表呼叫端的任何猜測或解讀，強調決定性的行為。 此程式庫是故意以這種方式設計來實現效能和安全性。 `[!OP.NO-LOC(Newtonsoft.Json)]` 預設為彈性。 這項設計的基本差異在於預設行為的下列許多特定差異背後。

### <a name="case-insensitive-deserialization"></a>不區分大小寫的還原序列化 

在還原序列化期間，`[!OP.NO-LOC(Newtonsoft.Json)]` 預設會執行不區分大小寫的屬性名稱比對。 <xref:[!OP.NO-LOC(System.Text.Json)]> 預設值區分大小寫，這可提供較佳的效能，因為它會執行完全相符的作業。 如需如何執行不區分大小寫比對的相關資訊，請參閱不[區分大小寫的屬性](system-text-json-how-to.md#case-insensitive-property-matching)比對。

如果您使用 ASP.NET Core 間接使用 `[!OP.NO-LOC(System.Text.Json)]`，就不需要採取任何動作來取得 `[!OP.NO-LOC(Newtonsoft.Json)]`之類的行為。 ASP.NET Core 指定使用 `[!OP.NO-LOC(System.Text.Json)]`時， [camel 大小寫屬性名稱](system-text-json-how-to.md#use-camel-case-for-all-json-property-names)和不區分大小寫比對的設定。

### <a name="minimal-character-escaping"></a>最少字元的轉義

在序列化期間，`[!OP.NO-LOC(Newtonsoft.Json)]` 相對於讓字元通過，而不將它們進行轉義，是相當寬鬆的。 也就是說，它不會將它們取代為 `\uxxxx`，其中 `xxxx` 是字元的程式碼點。 它會在其中進行 escape，而是在字元之前發出 `\` （例如，`"` 變成 `\"`）。 <xref:[!OP.NO-LOC(System.Text.Json)]> 預設會將更多字元加上轉義，以針對跨網站腳本（XSS）或資訊洩漏攻擊提供深度防禦保護，並使用六個字元的順序來執行。 `[!OP.NO-LOC(System.Text.Json)]` 預設會將所有非 ASCII 字元加上轉義，因此如果您在 `[!OP.NO-LOC(Newtonsoft.Json)]`中使用 `StringEscapeHandling.EscapeNonAscii`，就不需要執行任何動作。 根據預設，`[!OP.NO-LOC(System.Text.Json)]` 也會對 HTML 敏感字元進行轉義。 如需如何覆寫預設 `[!OP.NO-LOC(System.Text.Json)]` 行為的詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="comments"></a>註解

在還原序列化期間，`[!OP.NO-LOC(Newtonsoft.Json)]` 預設會忽略 JSON 中的批註。 <xref:[!OP.NO-LOC(System.Text.Json)]> 預設為會擲回批註的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不會包含它們。 如需如何允許批註的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。

### <a name="trailing-commas"></a>尾端逗號

在還原序列化期間，`[!OP.NO-LOC(Newtonsoft.Json)]` 預設會忽略尾端的逗號。 它也會忽略多個尾端逗號（例如 `[{"Color":"Red"},{"Color":"Green"},,]`）。 <xref:[!OP.NO-LOC(System.Text.Json)]> 預設值是擲回尾端逗號的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。 如需如何讓 `[!OP.NO-LOC(System.Text.Json)]` 接受它們的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。 沒有任何方法可以允許多個尾端逗號。

### <a name="converter-registration-precedence"></a>轉換器註冊優先順序

自訂轉換器的 `[!OP.NO-LOC(Newtonsoft.Json)]` 註冊優先順序如下所示：

* 屬性上的屬性
* 類型上的屬性
* [轉換器](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)集合

此順序表示 `Converters` 集合中的自訂轉換器會由在類型層級套用屬性所註冊的轉換器覆寫。 這兩種註冊都是由屬性層級的屬性所覆寫。

自訂轉換器的 <xref:[!OP.NO-LOC(System.Text.Json)]> 註冊優先順序不同：

* 屬性上的屬性
* <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合
* 類型上的屬性

此處的差異在於，`Converters` 集合中的自訂轉換器會覆寫類型層級的屬性。 此優先順序的目的是要讓執行時間變更覆寫設計階段的選擇。 沒有任何方法可以變更優先順序。

如需自訂轉換器註冊的詳細資訊，請參閱[註冊自訂轉換子](system-text-json-converters-how-to.md#register-a-custom-converter)。

### <a name="maximum-depth"></a>最大深度

`[!OP.NO-LOC(Newtonsoft.Json)]` 預設不具有最大深度限制。 針對 <xref:[!OP.NO-LOC(System.Text.Json)]>，預設限制為64，且可透過設定 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>加以設定。

### <a name="json-strings-property-names-and-string-values"></a>JSON 字串（屬性名稱和字串值）

在還原序列化期間，`[!OP.NO-LOC(Newtonsoft.Json)]` 接受以雙引號、單引號或不含引號括住的屬性名稱。 它接受以雙引號或單引號括住的字串值。 例如，`[!OP.NO-LOC(Newtonsoft.Json)]` 接受下列 JSON：

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`[!OP.NO-LOC(System.Text.Json)]` 只接受以雙引號括住的屬性名稱和字串值，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格需要該格式，而且是唯一視為有效 JSON 的格式。

以單引號括住的值會產生含有下列訊息的[JsonException](xref:[!OP.NO-LOC(System.Text.Json)].JsonException) ：

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>字串屬性的非字串值

`[!OP.NO-LOC(Newtonsoft.Json)]` 接受非字串值，例如數位或常值 `true` 和 `false`，以還原序列化為 string 類型的屬性。 以下是 `[!OP.NO-LOC(Newtonsoft.Json)]` 成功還原序列化為下列類別的 JSON 範例：

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

`[!OP.NO-LOC(System.Text.Json)]` 不會將非字串值還原序列化為字串屬性。 針對字串欄位接收的非字串值會導致[JsonException](xref:[!OP.NO-LOC(System.Text.Json)].JsonException) ，並出現下列訊息：

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>使用需要因應措施之 JsonSerializer 的案例

內建功能不支援下列案例，但可能的因應措施。 因應措施是[自訂轉換器](system-text-json-converters-how-to.md)，可能不會提供與 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能完全同位檢查。 其中一些範例程式碼會以範例的形式提供。 如果您依賴這些 `[!OP.NO-LOC(Newtonsoft.Json)]` 功能，則必須修改您的 .NET 物件模型或其他程式碼變更，才能進行遷移。

### <a name="types-without-built-in-support"></a>沒有內建支援的類型

<xref:[!OP.NO-LOC(System.Text.Json)]> 不會提供下列類型的內建支援：

* <xref:System.Data.DataTable> 和相關類型
* F#類型，例如[區分](../../fsharp/language-reference/discriminated-unions.md)等位、[記錄類型](../../fsharp/language-reference/records.md)和[匿名記錄類型](../../fsharp/language-reference/anonymous-records.md)。
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> 和其相關聯的泛型型別

針對沒有內建支援的類型，可以實作為自訂轉換器。

### <a name="quoted-numbers"></a>加上引號的數位

`[!OP.NO-LOC(Newtonsoft.Json)]` 可以序列化或還原序列化 JSON 字串所代表的數位（以引號括住）。 例如，它可以接受： `{"DegreesCelsius":"23"}`，而不是 `{"DegreesCelsius":23}`。 若要在 <xref:[!OP.NO-LOC(System.Text.Json)]>中啟用該行為，請執行如下列範例所示的自訂轉換子。 轉換器會處理定義為 `long`的屬性：

* 它會將它們序列化為 JSON 字串。 
* 它會在還原序列化時，接受引號內的 JSON 數位和數位。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

使用個別 `long` 屬性上的[屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換器。

### <a name="dictionary-with-non-string-key"></a>具有非字串索引鍵的字典

`[!OP.NO-LOC(Newtonsoft.Json)]` 支援 `Dictionary<TKey, TValue>`類型的集合。 <xref:[!OP.NO-LOC(System.Text.Json)]> 中的字典集合內建支援僅限於 `Dictionary<string, TValue>`。 也就是，索引鍵必須是字串。

若要支援具有整數或其他類型做為索引鍵的字典，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)中的範例所示的轉換器。

### <a name="polymorphic-serialization"></a>多型序列化

`[!OP.NO-LOC(Newtonsoft.Json)]` 會自動進行多型序列化。 如需 <xref:[!OP.NO-LOC(System.Text.Json)]>的有限多型序列化功能的相關資訊，請參閱[序列化衍生類別的屬性](system-text-json-how-to.md#serialize-properties-of-derived-classes)。

此處所述的因應措施，是定義可能包含衍生類別的屬性，做為 `object`的型別。 如果無法這樣做，另一個選項是使用整個繼承類型階層的 `Write` 方法建立轉換器，如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示。

### <a name="polymorphic-deserialization"></a>多型還原序列化

`[!OP.NO-LOC(Newtonsoft.Json)]` 具有 `TypeNameHandling` 設定，會在序列化時將類型名稱中繼資料新增至 JSON。 它會在還原序列化時使用中繼資料來執行多型還原序列化。 <xref:[!OP.NO-LOC(System.Text.Json)]> 可以執行有限範圍的多型序列化，但不能進行多型的還原[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)。

若要支援多型還原序列化，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示的轉換器。

### <a name="deserialization-of-object-properties"></a>物件屬性的還原序列化

當 `[!OP.NO-LOC(Newtonsoft.Json)]` 還原序列化為 Poco 中的 `object` 屬性或類型 `Dictionary<string, object>`的字典中，它會：

* 推斷 JSON 承載中基本值的類型（不是 `null`），並傳回儲存的 `string`、`long`、`double`、`boolean`或 `DateTime` 做為已封裝的物件。 *基本值*是單一 json 值，例如 json 數位、字串、`true`、`false`或 `null`。
* 傳回 JSON 承載中複雜值的 `JObject` 或 `JArray`。 *複雜值*是以括弧（`{}`）括住的 JSON 索引鍵/值組集合，或是以方括弧（`[]`）括住的值清單。 大括弧或括弧內的屬性和值可以有額外的屬性或值。
* 當裝載具有 `null` 的 JSON 常值時，會傳回 null 參考。

<xref:[!OP.NO-LOC(System.Text.Json)]> 會在 `System.Object` 屬性或字典值中，儲存基本和複雜值的已裝箱 `JsonElement`。 不過，它會將 `null` 視為 `[!OP.NO-LOC(Newtonsoft.Json)]`，並在裝載具有 `null` 的 JSON 常值時傳回 null 參考。

若要執行 `object` 屬性的型別推斷，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)中的範例所示的轉換器。

### <a name="deserialize-null-to-non-nullable-type"></a>將 null 還原序列化為不可為 null 的類型 

`[!OP.NO-LOC(Newtonsoft.Json)]` 在下列案例中不會擲回例外狀況：

* `NullValueHandling` 設定為 `Ignore`，而
* 在還原序列化期間，JSON 會針對不可為 null 的型別包含 null 值。

在相同的案例中，<xref:[!OP.NO-LOC(System.Text.Json)]> 會擲回例外狀況。 （對應的 null 處理設定為 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>）。

如果您擁有目標型別，最佳的解決方法是讓屬性成為可為 null （例如，將 `int` 變更為 `int?`）。

另一個因應措施是建立類型的轉換器，例如下列範例，其會處理 `DateTimeOffset` 類型的 null 值：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

藉由[使用屬性上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。

**注意：** 前面的轉換子**處理 null 值的方式**，與指定預設值的 poco 不同 `[!OP.NO-LOC(Newtonsoft.Json)]`。 例如，假設下列程式碼代表您的目標物件：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

而且假設下列 JSON 會使用上述的轉換器還原序列化：

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

還原序列化之後，`Date` 屬性具有1/1/0001 （`default(DateTimeOffset)`），也就是會覆寫在此函式中設定的值。 假設有相同的 POCO 和 JSON，`[!OP.NO-LOC(Newtonsoft.Json)]` 還原序列化會在 `Date` 屬性中留下1/1/2001。

### <a name="deserialize-to-immutable-classes-and-structs"></a>還原序列化為不可變的類別和結構

`[!OP.NO-LOC(Newtonsoft.Json)]` 可以還原序列化為不可變的類別和結構，因為它可以使用具有參數的函數。 <xref:[!OP.NO-LOC(System.Text.Json)]> 僅支援公用無參數的函式。 因應措施是，您可以在自訂轉換子中呼叫具有參數的函式。

以下是具有多個函數參數的不可變結構：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

以下是將此結構序列化和還原序列化的轉換器：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換子。

如需處理開放式泛型屬性之類似轉換器的範例，請參閱索引[鍵/值組的內建轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/JsonValueConverterKeyValuePair.cs)。

### <a name="specify-constructor-to-use"></a>指定要使用的構造函式

`[!OP.NO-LOC(Newtonsoft.Json)]` `[JsonConstructor]` 屬性可讓您指定在還原序列化為 POCO 時要呼叫的函式。 <xref:[!OP.NO-LOC(System.Text.Json)]> 僅支援無參數的函式。 因應措施是，您可以在自訂轉換器中呼叫所需的任何一個方法。 請參閱還原序列化[為不可變類別和結構](#deserialize-to-immutable-classes-and-structs)的範例。

### <a name="required-properties"></a>必要屬性

在 `[!OP.NO-LOC(Newtonsoft.Json)]`中，您可以在 `[JsonProperty]` 屬性上設定 `Required`，以指定需要屬性。 如果針對標示為必要的屬性，JSON 中未收到任何值，`[!OP.NO-LOC(Newtonsoft.Json)]` 會擲回例外狀況。

如果目標型別的其中一個屬性未收到任何值，<xref:[!OP.NO-LOC(System.Text.Json)]> 不會擲回例外狀況。 例如，如果您有 `WeatherForecast` 類別：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

下列 JSON 會進行還原序列化，而不會發生錯誤：

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

若要讓還原序列化失敗，如果 JSON 中沒有 `Date` 的屬性，請執行自訂的轉換器。 如果在還原序列化完成後未設定 `Date` 屬性，下列範例轉換器程式碼會擲回例外狀況：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

藉由[使用 POCO 類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。

如果您遵循此模式，請不要在以遞迴方式呼叫 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializer.Serialize%2A> 或 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializer.Deserialize%2A>時傳入 options 物件。 Options 物件包含 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters%2A> 集合。 如果您將它傳遞給 `Serialize` 或 `Deserialize`，則自訂轉換器會呼叫自己的，因此會產生無限迴圈，導致堆疊溢位例外狀況。 如果預設選項不可行，請使用您所需的設定來建立選項的新實例。 這個方法將會變慢，因為每個新的實例會獨立快取。

上述的轉換器程式碼是簡化的範例。 如果您需要處理屬性（例如[[JsonIgnore]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonIgnoreAttribute)或不同的選項（例如自訂編碼器），則需要額外的邏輯。 此外，範例程式碼不會處理在此函式中設定預設值的屬性。 而這種方法不會區分下列案例：

* JSON 中遺漏了屬性。
* JSON 中有不可為 null 類型的屬性，但此值是類型的預設值，例如零代表 `int`。
* JSON 中有可為 null 類型的屬性，但值為 null。

### <a name="conditionally-ignore-a-property"></a>有條件地忽略屬性

`[!OP.NO-LOC(Newtonsoft.Json)]` 有數種方式可以有條件地忽略序列化或還原序列化上的屬性：

* `DefaultContractResolver` 可讓您根據任意條件，選取要包含或排除的屬性。 
* `JsonSerializerSettings` 上的 `NullValueHandling` 和 `DefaultValueHandling` 設定，可讓您指定應該忽略所有的 null 值或預設值屬性。
* [`[JsonProperty]`] 屬性上的 [`NullValueHandling`] 和 [`DefaultValueHandling`] 設定可讓您指定在設定為 null 或預設值時，應該忽略的個別屬性。

<xref:[!OP.NO-LOC(System.Text.Json)]> 提供下列方法來在序列化時省略屬性：

* 屬性[（property）上的 [JsonIgnore] 屬性（attribute）](system-text-json-how-to.md#exclude-individual-properties)會在序列化期間，從 JSON 中省略屬性（property）。
* [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global 選項可讓您排除所有 null 值屬性。
* [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global 選項可讓您排除所有唯讀屬性。

這些選項**不**會讓您：

* 忽略所有具有類型之預設值的屬性。
* 忽略具有類型之預設值的選取屬性。
* 如果其值為 null，則忽略選取的屬性。
* 根據在執行時間評估的任意準則，忽略選取的屬性。 

針對該功能，您可以撰寫自訂的轉換器。 以下是範例 POCO 和適用于它的自訂轉換器，其說明此方法：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

如果參數的值為 null、空字串或 "N/A"，則轉換器會從序列化中省略 `Summary` 屬性。 

藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。

這種方法需要額外的邏輯，如下所示：

* POCO 包含複雜的屬性。
* 您需要處理諸如 `[JsonIgnore]` 或選項（例如自訂編碼器）之類的屬性。

### <a name="specify-date-format"></a>指定日期格式

`[!OP.NO-LOC(Newtonsoft.Json)]` 提供數種方式來控制 `DateTime` 和 `DateTimeOffset` 類型的屬性如何序列化和還原序列化：

* `DateTimeZoneHandling` 設定可以用來將所有 `DateTime` 值序列化為 UTC 日期。
* `DateFormatString` 設定和 `DateTime` 轉換器可以用來自訂日期字串的格式。

在 <xref:[!OP.NO-LOC(System.Text.Json)]>中，具有內建支援的唯一格式是 ISO 8601-1:2019，因為它廣泛採用、明確，並會精確地進行往返。 若要使用任何其他格式，請建立自訂轉換器。 如需詳細資訊，請參閱[[!OP.NO-LOC(System.Text.Json)]中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)。

### <a name="callbacks"></a>叫

`[!OP.NO-LOC(Newtonsoft.Json)]` 可讓您在序列化或還原序列化程式的數個點執行自訂程式碼：

* OnDeserializing （開始還原序列化物件時）
* OnDeserialized （完成還原序列化物件時）
* OnSerializing （開始序列化物件時）
* OnSerialized （完成序列化物件時）

在 <xref:[!OP.NO-LOC(System.Text.Json)]>中，您可以藉由撰寫自訂的轉換器來模擬回呼。 下列範例顯示 POCO 的自訂轉換子。 轉換器包含的程式碼會在每個對應至 `[!OP.NO-LOC(Newtonsoft.Json)]` 回呼的時間點顯示訊息。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。

如果您使用遵循上述範例的自訂轉換器：

* `OnDeserializing` 程式碼沒有新 POCO 實例的存取權。 若要在還原序列化開始時操作新的 POCO 實例，請將該程式碼放在 POCO 函式中。
* 當以遞迴方式呼叫 `Serialize` 或 `Deserialize`時，請勿傳入 options 物件。 Options 物件包含 `Converters` 集合。 如果您將它傳遞給 `Serialize` 或 `Deserialize`，則會使用轉換器，並產生無限迴圈，而導致堆疊溢位例外狀況。

### <a name="public-and-non-public-fields"></a>公用和非公用欄位

`Newtonsoft.Json` 可以序列化和還原序列化欄位，以及屬性。 <xref:System.Text.Json> 僅適用于公用屬性。 自訂轉換器可以提供這種功能。

### <a name="internal-and-private-property-setters-and-getters"></a>內部和私用屬性 setter 和 getter

`Newtonsoft.Json` 可以透過 `JsonProperty` 屬性來使用私用和內部屬性 setter 和 getter。 <xref:System.Text.Json> 僅支援公用 setter。 自訂轉換器可以提供這種功能。

### <a name="populate-existing-objects"></a>填入現有的物件

中的 `JsonConvert.PopulateObject` 方法 `Newtonsoft.Json` 將 JSON 檔案還原序列化為類別的現有實例，而不是建立新的實例。 <xref:System.Text.Json> 一律會使用預設的公用無參數函式來建立目標型別的新實例。 自訂轉換器可以還原序列化為現有的實例。

### <a name="reuse-rather-than-replace-properties"></a>重複使用，而不是取代屬性

[`Newtonsoft.Json` `ObjectCreationHandling`] 設定可讓您指定應該重複使用屬性中的物件，而不是在還原序列化期間加以取代。 <xref:System.Text.Json> 一律會取代屬性中的物件。  自訂轉換器可以提供這種功能。

### <a name="add-to-collections-without-setters"></a>新增至不含 setter 的集合

在還原序列化期間，即使屬性沒有 setter，`Newtonsoft.Json` 也會將物件加入至集合。 <xref:System.Text.Json> 會忽略沒有 setter 的屬性。 自訂轉換器可以提供這種功能。

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>JsonSerializer 目前不支援的案例

在下列案例中，因應措施不可行或無法解決。 如果您依賴這些 `Newtonsoft.Json` 功能，則不會有重大變更，因此無法進行遷移。

### <a name="preserve-object-references-and-handle-loops"></a>保留物件參考並處理迴圈

根據預設，`Newtonsoft.Json` 依值序列化。 例如，如果物件包含兩個屬性，其中包含相同 `Person` 物件的參考，則該 `Person` 物件屬性的值會在 JSON 中重複。

`Newtonsoft.Json` 在 `JsonSerializerSettings` 上有 `PreserveReferencesHandling` 設定，可讓您以傳址方式序列化：

* 識別碼中繼資料會加入至針對第一個 `Person` 物件所建立的 JSON。
* 針對第二個 `Person` 物件所建立的 JSON 包含該識別碼的參考，而不是屬性值。

`Newtonsoft.Json` 也有 `ReferenceLoopHandling` 設定，可讓您忽略迴圈參考，而不是擲回例外狀況。

<xref:System.Text.Json> 只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。

### <a name="systemruntimeserialization-attributes"></a>System.object。序列化屬性

<xref:System.Text.Json> 不支援來自 `System.Runtime.Serialization` 命名空間的屬性，例如 `DataMemberAttribute` 和 `IgnoreDataMemberAttribute`。

### <a name="octal-numbers"></a>八進位數位

`Newtonsoft.Json` 會將前置零的數位視為八進位數位。 <xref:System.Text.Json> 不允許前置零，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json` 可以設定為在還原序列化期間擲回例外狀況（如果 JSON 包含目標型別中遺漏的屬性）。 <xref:System.Text.Json> 會忽略 JSON 中的額外屬性，除非您使用[[JsonExtensionData] 屬性](system-text-json-how-to.md#handle-overflow-json)。 缺少的成員功能沒有因應措施。

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json` 可讓您使用 `TraceWriter` 來進行 debug，以查看由序列化或還原序列化所產生的記錄。 <xref:System.Text.Json> 不會進行記錄。

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>相較于 JToken 的 JsonDocument 和 JsonElement （例如 JObject、JArray）

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供從現有 JSON 承載剖析和建立**唯讀**檔物件模型（DOM）的功能。 DOM 提供 JSON 承載中資料的隨機存取。 組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。 `JsonElement` 類型會提供 Api，將 JSON 文字轉換成常見的 .NET 類型。 `JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。

### <a name="jsondocument-is-idisposable"></a>JsonDocument 是 IDisposable

`JsonDocument` 會將資料的記憶體中視圖建立成集區緩衝區。 因此，不同于 `Newtonsoft.Json`的 `JObject` 或 `JArray`，`JsonDocument` 型別會執行 `IDisposable`，而且必須在 using 區塊內使用。 

如果您想要將存留期擁有權和處置責任轉移給呼叫者，只會從您的 API 傳回 `JsonDocument`。 在大部分的情況下，這並不是必要的。 如果呼叫端需要使用整個 JSON 檔，則會傳回 <xref:System.Text.Json.JsonDocument.RootElement%2A>的 <xref:System.Text.Json.JsonElement.Clone%2A>，也就是 <xref:System.Text.Json.JsonElement>。 如果呼叫端需要使用 JSON 檔中的特定元素，則會傳回該 <xref:System.Text.Json.JsonElement>的 <xref:System.Text.Json.JsonElement.Clone%2A>。 如果您直接傳回 `RootElement` 或子項目而不進行 `Clone`，則在處置擁有它的 `JsonDocument` 之後，呼叫端將無法存取傳回的 `JsonElement`。

以下是要求您進行 `Clone`的範例：

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

上述程式碼需要包含 `fileName` 屬性的 `JsonElement`。 它會開啟 JSON 檔案，並建立 `JsonDocument`。 方法假設呼叫端想要使用整份檔，因此它會傳回 `RootElement`的 `Clone`。 

如果您收到 `JsonElement` 並傳回子項目，則不需要傳回子項目的 `Clone`。 呼叫端負責保持傳入 `JsonElement` 所屬的 `JsonDocument`。 例如：

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument 是唯讀的

<xref:System.Text.Json> DOM 無法加入、移除或修改 JSON 元素。 其設計是以這種方式來進行效能，並減少剖析一般 JSON 承載大小的配置（也就是 < 1 MB）。 如果您的案例目前使用可修改的 DOM，下列其中一個因應措施可能是可行的：

* 若要從頭開始建立 `JsonDocument` （也就是不會將現有的 JSON 承載傳遞給 `Parse` 方法），請使用 `Utf8JsonWriter` 寫入 JSON 文字，並剖析該輸出，以建立新的 `JsonDocument`。
* 若要修改現有的 `JsonDocument`，請使用它來寫入 JSON 文字，並在您撰寫時進行變更，並剖析該輸出以建立新的 `JsonDocument`。
* 若要合併現有的 JSON 檔，相當於 `Newtonsoft.Json`的 `JObject.Merge` 或 `JContainer.Merge` Api，請參閱[此 GitHub 問題](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)。

### <a name="jsonelement-is-a-union-struct"></a>JsonElement 是聯集結構

`JsonDocument` 會將 `RootElement` 公開為 <xref:System.Text.Json.JsonElement>類型的屬性，也就是包含任何 JSON 元素的 union、struct 類型。 `Newtonsoft.Json` 使用專用的階層型別，如 `JObject`、`JArray`、`JToken`等等。 `JsonElement` 是您可以搜尋和列舉的專案，您可以使用 `JsonElement` 將 JSON 元素具體化成 .NET 類型。

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>如何搜尋子項目的 JsonDocument 和 JsonElement

使用 `JObject` 或 `JArray` 從 `Newtonsoft.Json` 搜尋 JSON 權杖，通常會相對快速，因為它們是在某個字典中的查閱。 相較之下，搜尋 `JsonElement` 需要依序搜尋屬性，因此速度相當慢（例如使用 `TryGetProperty`時）。 <xref:System.Text.Json> 的設計目的是要將初始剖析時間減至最少，而不是查閱時間。 因此，搜尋 `JsonDocument` 物件時，請使用下列方法來優化效能：

* 使用內建的列舉值（<xref:System.Text.Json.JsonElement.EnumerateArray%2A> 和 <xref:System.Text.Json.JsonElement.EnumerateObject%2A>），而不是執行您自己的索引或迴圈。
* 請不要透過每個屬性，使用 `RootElement`，對整個 `JsonDocument` 進行順序搜尋。 相反地，請根據 JSON 資料的已知結構來搜尋嵌套的 JSON 物件。 例如，如果您要尋找 `Student` 物件中的 `Grade` 屬性，請對 `Student` 物件執行迴圈，並取得每一個的 `Grade` 值，而不是搜尋尋找 `JsonElement` 屬性的所有 `Grade` 物件。 執行後者會導致相同資料的不必要傳遞。

如需程式碼範例，請參閱[使用 JsonDocument 來存取資料](system-text-json-how-to.md#use-jsondocument-for-access-to-data)。

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader 與 JsonTextReader 的比較

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器、從[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601)讀取。 `Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。

下列各節說明使用 `Utf8JsonReader`的建議程式設計模式。

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader 是 ref 結構

因為 `Utf8JsonReader` 類型是*ref 結構*，所以有[一些限制](../../csharp/language-reference/keywords/ref.md#ref-struct-types)。 例如，它無法在 ref 結構以外的類別或結構上儲存為欄位。 為了達到高效能，此型別必須是 `ref struct`，因為它需要快取輸入[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)，這本身就是 ref 結構。 此外，這種類型是可變動的，因為它會保存狀態。 因此，請以 ref 而非傳值方式來**傳遞它**。 以傳值方式傳遞會導致結構複製，而且呼叫端看不到狀態變更。 這與 `Newtonsoft.Json` 不同，因為 `Newtonsoft.Json` `JsonTextReader` 是一個類別。 如需如何使用 ref 結構的詳細資訊，請參閱[撰寫安全且C#有效率](../../csharp/write-safe-efficient-code.md)的程式碼。

### <a name="read-utf-8-text"></a>讀取 UTF-8 文字

若要在使用 `Utf8JsonReader`時達到最佳效能，請閱讀已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。 如需程式碼範例，請參閱[使用 Utf8JsonReader 來篩選資料](system-text-json-how-to.md#filter-data-using-utf8jsonreader)。

### <a name="read-with-a-stream-or-pipereader"></a>讀取資料流程或 PipeReader

`Utf8JsonReader` 支援從以 UTF-8 編碼的[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果）讀取。

對於同步讀取，您可以讀取 JSON 承載，直到資料流程結尾到位元組陣列，然後將它傳遞到讀取器。 若要從字串讀取（編碼為 UTF-16），請呼叫 <xref:System.Text.Encoding.UTF8>。<xref:System.Text.Encoding.GetBytes%2A> 首先，將字串轉碼為 UTF-8 編碼的位元組陣列。 然後將它傳遞給 `Utf8JsonReader`。 

由於 `Utf8JsonReader` 會將輸入視為 JSON 文字，因此會將 UTF-8 位元組順序標記（BOM）視為不正確 JSON。 呼叫端必須先篩選掉，再將資料傳遞給讀取器。

如需程式碼範例，請參閱[使用 Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader)。

### <a name="read-with-multi-segment-readonlysequence"></a>閱讀多區段 ReadOnlySequence

如果您的 JSON 輸入是[ReadOnlySpan\<位元組 >](xref:System.ReadOnlySpan%601)，則當您執行讀取迴圈時，可以從讀取器上的 `ValueSpan` 屬性存取每個 json 元素。 不過，如果您的輸入是[ReadOnlySequence\<位元組 >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果），某些 JSON 元素可能會跨 `ReadOnlySequence<byte>` 物件的多個區段。 這些元素無法從連續記憶體區塊中的 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 存取。 相反地，每當您有多個區段 `ReadOnlySequence<byte>` 做為輸入時，請輪詢讀取器上的 <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> 屬性，以瞭解如何存取目前的 JSON 元素。 以下是建議的模式：

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

### <a name="use-valuetextequals-for-property-name-lookups"></a>使用 ValueTextEquals 進行屬性名稱查閱

請不要使用 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 透過呼叫屬性名稱查閱的 <xref:System.MemoryExtensions.SequenceEqual%2A> 來進行逐位元組比較。 改為呼叫 <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>，因為該方法會將任何在 JSON 中進行轉義的字元。 以下範例顯示如何搜尋名為 "name" 的屬性：

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>將 null 值讀取成可為 null 的實數值型別

`Newtonsoft.Json` 所提供的 Api 會傳回 <xref:System.Nullable%601>，例如 `ReadAsBoolean`，藉由傳回 `TokenType` 來處理 `Null` `bool?`。 內建的 `System.Text.Json` Api 只會傳回不可為 null 的實數值型別。 例如，<xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> 會傳回 `bool`。 如果在 JSON 中找到 `Null`，它會擲回例外狀況。 下列範例示範兩種處理 null 的方式：一個是藉由傳回可為 null 的實值型別，另一個則是傳回預設值。

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

如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。 不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。 盡可能共用程式碼的方法之一，就是建立 `Utf8JsonReader` 和 `Newtonsoft.Json` `JsonTextReader`的 `ref struct` 包裝函式。 此包裝函式會統一公用介面區，同時隔離行為差異。 這可讓您隔離主要變更與型別的結構，並以傳址方式傳遞新的型別。 這是[DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫所遵循的模式：

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter 與 Json.net jsoNtextwriter, 的比較

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。 寫入器是可以用來建立自訂序列化程式的低層級類型。

下列各節說明使用 `Utf8JsonWriter`的建議程式設計模式。

### <a name="write-with-utf-8-text"></a>以 UTF-8 文字撰寫

若要在使用 `Utf8JsonWriter`時達到最佳效能，請撰寫已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。 使用 <xref:System.Text.Json.JsonEncodedText> 來快取和預先編碼已知的字串屬性名稱和值，並將其傳遞給寫入器，而不是使用 UTF-16 字串常值。 這比快取和使用 UTF-8 位元組陣列更快速。

如果您需要執行自訂的轉義，此方法也適用。 `System.Text.Json` 不允許您在寫入字串時停用轉義。 不過，您可以將自己的自訂 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 當做寫入器的選項傳入，或建立您自己的 `JsonEncodedText` 以使用您的 `JavascriptEncoder` 來執行轉義，然後撰寫 `JsonEncodedText`，而不是字串。 如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="write-raw-values"></a>寫入原始值

`Newtonsoft.Json` `WriteRawValue` 方法會寫入需要值的原始 JSON。 <xref:System.Text.Json> 沒有直接的對等用法，但以下是可確保只會寫入有效 JSON 的因應措施：

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>自訂字元轉義

`JsonTextWriter` 的[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)設定會提供選項，以將所有非 ASCII 字元**或**HTML 字元全部轉義。 根據預設，`Utf8JsonWriter` 會將所有非 ASCII**和**HTML 字元全部轉義。 這項轉義是針對深層防禦的安全性原因而完成。 若要指定不同的轉義原則，請建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 並設定 <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>。 如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="customize-json-format"></a>自訂 JSON 格式

`JsonTextWriter` 包含下列設定，其中 `Utf8JsonWriter` 沒有對等的：

* [縮排](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm)-指定要縮排的字元數。 `Utf8JsonWriter` 一律會進行2個字元的縮排。
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -指定要用於縮排的字元。  `Utf8JsonWriter` 一律使用空白字元。
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -指定用來括住字串值的字元。  `Utf8JsonWriter` 一律使用雙引號。
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -指定是否要以引號括住屬性名稱。  `Utf8JsonWriter` 一律以引號括住它們。

沒有任何因應措施可讓您自訂 `Utf8JsonWriter` 以這些方式產生的 JSON。

### <a name="write-null-values"></a>寫入 null 值

若要使用 `Utf8JsonWriter`來寫入 null 值，請呼叫：

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> 寫入具有 null 值的索引鍵/值組。
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> 寫入 null 做為 JSON 陣列的元素。

若為字串屬性，如果字串為 null，<xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> 和 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> 就相當於 `WriteNull` 和 `WriteNullValue`。

### <a name="write-timespan-uri-or-char-values"></a>寫入 Timespan、Uri 或 char 值

`JsonTextWriter` 提供[TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm)、 [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)和[char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm)值的 `WriteValue` 方法。 `Utf8JsonWriter` 沒有對等的方法。 相反地，請將這些值格式化為字串（例如，藉由呼叫 `ToString()`）並呼叫 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>。

### <a name="multi-targeting"></a>多目標

如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。 不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。 盡可能共用程式碼的方法之一，就是建立一個圍繞 `Utf8JsonWriter` 的包裝函式，並 `Newtonsoft` `JsonTextWriter`。 此包裝函式會統一公用介面區，同時隔離行為差異。 這可讓您將變更主要隔離到類型的結構。 [DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫如下：

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>其他資源

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Json 總覽](system-text-json-overview.md)
* [如何使用 System.Text.Json](system-text-json-how-to.md)
* [如何撰寫自訂轉換器](system-text-json-converters-how-to.md)
* [System.Text.Json 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json。序列化 API 參考](xref:System.Text.Json.Serialization)
