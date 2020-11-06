---
title: 從 Newtonsoft.Json .net 遷移 System.Text.Json
description: 瞭解如何從遷移 Newtonsoft.Json 至 System.Text.Json 。 包含範例程式碼。
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 11/05/2020
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cd40b6f6daac267342f54631075e4640f9a77d94
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329764"
---
# <a name="how-to-migrate-from-no-locnewtonsoftjson-to-no-locsystemtextjson"></a>如何從遷移 Newtonsoft.Json 至 System.Text.Json

本文說明如何從遷移 [Newtonsoft.Json](https://www.newtonsoft.com/json) 至 <xref:System.Text.Json> 。

`System.Text.Json`命名空間提供序列化和還原序列化 JavaScript 物件標記法 (JSON) 的功能。 連結 `System.Text.Json` 庫隨附于 [.net Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) 和更新版本的執行時間。 若為其他目標 framework，請安裝 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。 封裝支援：

* .NET Standard 2.0 和更新版本
* .NET Framework 4.7.2 和更新版本
* .NET Core 2.0、2.1 和2。2

`System.Text.Json` 主要著重于效能、安全性和標準合規性。 它在預設行為方面有一些主要的差異，而不是與的功能同位 `Newtonsoft.Json` 。 在某些案例中，沒有 `System.Text.Json` 內建功能，但有建議的因應措施。 在其他情況下，因應措施是不切實際的。 如果您的應用程式相依于遺失的功能，請考慮提出 [問題](https://github.com/dotnet/runtime/issues/new) ，以瞭解是否可以加入您案例的支援。

本文大部分是關於如何使用 <xref:System.Text.Json.JsonSerializer> API，但也包含如何使用 <xref:System.Text.Json.JsonDocument> (（代表檔物件模型或 DOM) 、和類型）的指引 <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> 。

## <a name="table-of-differences-between-no-locnewtonsoftjson-and-no-locsystemtextjson"></a>和之間差異的資料表 Newtonsoft.JsonSystem.Text.Json

下表列出 `Newtonsoft.Json` 功能和 `System.Text.Json` 對應專案。 對等專案屬於下列類別：

* 內建功能的支援。 從取得類似的行為 `System.Text.Json` 可能需要使用屬性或全域選項。
* 不支援，因應措施是可行的。 因應措施是 [自訂轉換器](system-text-json-converters-how-to.md)，可能無法提供與功能完全相同的 `Newtonsoft.Json` 功能。 針對其中一些，範例程式碼會以範例的形式提供。 如果您依賴這些 `Newtonsoft.Json` 功能，則需要修改您的 .net 物件模型或其他程式碼變更。
* 不支援，因應措施並非實際或可能的解決方法。 如果您依賴這些 `Newtonsoft.Json` 功能，則不需要進行重大變更，就不可能進行遷移。

::: zone pivot="dotnet-5-0"
| Newtonsoft.Json 功能                               | System.Text.Json 等效 |
|-------------------------------------------------------|-----------------------------|
| 預設不區分大小寫的還原序列化           | ✔️ [PropertyNameCaseInsensitive global 設定](#case-insensitive-deserialization) |
| Camel 大小寫屬性名稱                             | ✔️ [PropertyNamingPolicy global 設定](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| 減少字元轉義                            | ✔️ [可設定的 Strict 字元轉義](#minimal-character-escaping) |
| `NullValueHandling.Ignore` 全域設定             | ✔️ [DefaultIgnoreCondition global 選項](system-text-json-how-to.md#ignore-all-null-value-properties) |[有條件地忽略屬性](#conditionally-ignore-a-property)
| 允許批註                                        | ✔️ [ReadCommentHandling global 設定](#comments) |
| 允許尾端逗號                                 | ✔️ [AllowTrailingCommas global 設定](#trailing-commas) |
| 自訂轉換器註冊                         | ✔️ [優先順序不同的順序](#converter-registration-precedence) |
| 預設沒有最大深度                           | ✔️ [預設最大深度64（可設定）](#maximum-depth) |
| `PreserveReferencesHandling` 全域設定           | ✔️ [ReferenceHandling global 設定](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling` 全域設定                | ✔️ [ReferenceHandling global 設定](#preserve-object-references-and-handle-loops) |
| 序列化或還原序列化以引號括住的數位            | ✔️ [NumberHandling global 設定，[JsonNumberHandling] 屬性](#allow-or-write-numbers-in-quotes) |
| 還原序列化為不可變的類別和結構          | ✔️ [JsonConstructor，c # 9 記錄](#deserialize-to-immutable-classes-and-structs) |
| 支援欄位                                    | ✔️ [IncludeFields global 設定，[JsonInclude] 屬性](#public-and-non-public-fields) |
| `DefaultValueHandling` 全域設定                 | ✔️ [DefaultIgnoreCondition global 設定](#conditionally-ignore-a-property) |
| `NullValueHandling` 設定開啟 `[JsonProperty]`       | ✔️ [JsonIgnore 屬性](#conditionally-ignore-a-property)  |
| `DefaultValueHandling` 設定開啟 `[JsonProperty]`    | ✔️ [JsonIgnore 屬性](#conditionally-ignore-a-property)  |
| `Dictionary`使用非字串索引鍵還原序列化          | [支援](#dictionary-with-non-string-key)✔️ |
| 支援非公用屬性 setter 和 getter   | ✔️ [JsonInclude 屬性](#non-public-property-setters-and-getters) |
| `[JsonConstructor]` 屬性                         | ✔️ [[JsonConstructor] 屬性](#specify-constructor-to-use-when-deserializing) |
| 支援廣泛的類型範圍                    | ⚠️[某些類型需要自訂轉換器](#types-without-built-in-support) |
| 多型序列化                             | ⚠️[不支援、](#polymorphic-serialization)因應措施、範例 |
| 多型還原序列化                           | ⚠️[不支援、](#polymorphic-deserialization)因應措施、範例 |
| 將推斷的型別還原序列化為 `object` 屬性      | ⚠️[不支援、](#deserialization-of-object-properties)因應措施、範例 |
| 將 JSON `null` 常值還原序列化為不可為 null 的實數值型別 | ⚠️[不支援、](#deserialize-null-to-non-nullable-type)因應措施、範例 |
| `Required`在屬性上設定 `[JsonProperty]`        | ⚠️[不支援、](#required-properties)因應措施、範例 |
| `DefaultContractResolver` 忽略屬性       | ⚠️[不支援、](#conditionally-ignore-a-property)因應措施、範例 |
| `DateTimeZoneHandling`、 `DateFormatString` 設定   | ⚠️[不支援、](#specify-date-format)因應措施、範例 |
| 回撥                                             | ⚠️[不支援、](#callbacks)因應措施、範例 |
| `JsonConvert.PopulateObject` 方法                   | ⚠️[不支援，](#populate-existing-objects)因應措施 |
| `ObjectCreationHandling` 全域設定               | ⚠️[不支援，](#reuse-rather-than-replace-properties)因應措施 |
| 新增至不含 setter 的集合                    | ⚠️[不支援，](#add-to-collections-without-setters)因應措施 |
| 支援 `System.Runtime.Serialization` 屬性 | ❌ [不支援](#systemruntimeserialization-attributes) |
| `MissingMemberHandling` 全域設定                | ❌ [不支援](#missingmemberhandling) |
| 允許沒有引號的屬性名稱                   | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許在字串值前後加上單引號              | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許字串屬性的非字串 JSON 值    | ❌ [不支援](#non-string-values-for-string-properties) |
::: zone-end

::: zone pivot="dotnet-core-3-1"
| Newtonsoft.Json 功能                               | System.Text.Json 等效 |
|-------------------------------------------------------|-----------------------------|
| 預設不區分大小寫的還原序列化           | ✔️ [PropertyNameCaseInsensitive global 設定](#case-insensitive-deserialization) |
| Camel 大小寫屬性名稱                             | ✔️ [PropertyNamingPolicy global 設定](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| 減少字元轉義                            | ✔️ [可設定的 Strict 字元轉義](#minimal-character-escaping) |
| `NullValueHandling.Ignore` 全域設定             | ✔️ [IgnoreNullValues global 選項](system-text-json-how-to.md#ignore-all-null-value-properties) |
| 允許批註                                        | ✔️ [ReadCommentHandling global 設定](#comments) |
| 允許尾端逗號                                 | ✔️ [AllowTrailingCommas global 設定](#trailing-commas) |
| 自訂轉換器註冊                         | ✔️ [優先順序不同的順序](#converter-registration-precedence) |
| 預設沒有最大深度                           | ✔️ [預設最大深度64（可設定）](#maximum-depth) |
| 支援廣泛的類型範圍                    | ⚠️[某些類型需要自訂轉換器](#types-without-built-in-support) |
| 將字串還原序列化為數字                        | ⚠️[不支援、](#allow-or-write-numbers-in-quotes)因應措施、範例 |
| `Dictionary`使用非字串索引鍵還原序列化          | ⚠️[不支援、](#dictionary-with-non-string-key)因應措施、範例 |
| 多型序列化                             | ⚠️[不支援、](#polymorphic-serialization)因應措施、範例 |
| 多型還原序列化                           | ⚠️[不支援、](#polymorphic-deserialization)因應措施、範例 |
| 將推斷的型別還原序列化為 `object` 屬性      | ⚠️[不支援、](#deserialization-of-object-properties)因應措施、範例 |
| 將 JSON `null` 常值還原序列化為不可為 null 的實數值型別 | ⚠️[不支援、](#deserialize-null-to-non-nullable-type)因應措施、範例 |
| 還原序列化為不可變的類別和結構          | ⚠️[不支援、](#deserialize-to-immutable-classes-and-structs)因應措施、範例 |
| `[JsonConstructor]` 屬性                         | ⚠️[不支援、](#specify-constructor-to-use-when-deserializing)因應措施、範例 |
| `Required`在屬性上設定 `[JsonProperty]`        | ⚠️[不支援、](#required-properties)因應措施、範例 |
| `NullValueHandling`在屬性上設定 `[JsonProperty]` | ⚠️[不支援、](#conditionally-ignore-a-property)因應措施、範例  |
| `DefaultValueHandling`在屬性上設定 `[JsonProperty]` | ⚠️[不支援、](#conditionally-ignore-a-property)因應措施、範例  |
| `DefaultValueHandling` 全域設定                 | ⚠️[不支援、](#conditionally-ignore-a-property)因應措施、範例 |
| `DefaultContractResolver` 忽略屬性       | ⚠️[不支援、](#conditionally-ignore-a-property)因應措施、範例 |
| `DateTimeZoneHandling`、 `DateFormatString` 設定   | ⚠️[不支援、](#specify-date-format)因應措施、範例 |
| 回撥                                             | ⚠️[不支援、](#callbacks)因應措施、範例 |
| 支援公用和非公用欄位              | ⚠️[不支援，](#public-and-non-public-fields)因應措施 |
| 支援非公用屬性 setter 和 getter   | ⚠️[不支援，](#non-public-property-setters-and-getters)因應措施 |
| `JsonConvert.PopulateObject` 方法                   | ⚠️[不支援，](#populate-existing-objects)因應措施 |
| `ObjectCreationHandling` 全域設定               | ⚠️[不支援，](#reuse-rather-than-replace-properties)因應措施 |
| 新增至不含 setter 的集合                    | ⚠️[不支援，](#add-to-collections-without-setters)因應措施 |
| `PreserveReferencesHandling` 全域設定           | ❌ [不支援](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling` 全域設定                | ❌ [不支援](#preserve-object-references-and-handle-loops) |
| 支援 `System.Runtime.Serialization` 屬性 | ❌ [不支援](#systemruntimeserialization-attributes) |
| `MissingMemberHandling` 全域設定                | ❌ [不支援](#missingmemberhandling) |
| 允許沒有引號的屬性名稱                   | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許在字串值前後加上單引號              | ❌ [不支援](#json-strings-property-names-and-string-values) |
| 允許字串屬性的非字串 JSON 值    | ❌ [不支援](#non-string-values-for-string-properties) |
::: zone-end

這不是完整的功能清單 `Newtonsoft.Json` 。 此清單包含 [GitHub 問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) 或 [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) 文章中已要求的許多案例。 如果您針對此處所列的其中一個案例執行因應措施，而此案例目前沒有範例程式碼，而且您想要共用方案，請在此頁面底部的 **意見** 反應區段中選取 **此頁面** 。 這會在此檔的 GitHub 存放庫中建立問題，並將其列在此頁面的 **意見** 反應區段中。

## <a name="differences-in-default-jsonserializer-behavior-compared-to-no-locnewtonsoftjson"></a>預設 JsonSerializer 行為與之間的差異 Newtonsoft.Json

<xref:System.Text.Json> 預設為嚴格，並避免呼叫呼叫端的猜測或解讀，強調具決定性的行為。 此程式庫是針對效能和安全性刻意設計的。 `Newtonsoft.Json` 預設為彈性。 這項設計的基本差異在於預設行為的下列許多特定差異背後。

### <a name="case-insensitive-deserialization"></a>不區分大小寫的還原序列化

在還原序列化期間， `Newtonsoft.Json` 預設不區分大小寫的屬性名稱相符。 <xref:System.Text.Json>預設值會區分大小寫，這可提供更佳的效能，因為它會執行完全相符的結果。 如需有關如何進行不區分大小寫比對的詳細資訊，請參閱不區分 [大小寫的屬性](system-text-json-how-to.md#case-insensitive-property-matching)比對。

如果您使用 `System.Text.Json` ASP.NET Core 間接使用，則不需要採取任何動作來取得像這樣的行為 `Newtonsoft.Json` 。 ASP.NET Core 指定符合 [camel 大小寫之屬性名稱](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) 的設定，以及使用時不區分大小寫的比對 `System.Text.Json` 。

::: zone pivot="dotnet-5-0"
ASP.NET Core 預設也啟用還原序列化 [引號的數位](#allow-or-write-numbers-in-quotes) 。
::: zone-end

### <a name="minimal-character-escaping"></a>減少字元轉義

在序列化期間， `Newtonsoft.Json` 相對於讓字元通過，而不將它們進行轉義。 也就是說，它不會將它們取代 `\uxxxx` `xxxx` 為字元的程式碼點。 在它進行 escape 的地方，它會在 (的 `\` 字元之前發出，以 `"` 成為 `\"`) 。 <xref:System.Text.Json> 根據預設，請將更多字元轉義以提供深度防禦的保護，以防範跨網站腳本 (XSS) 或資訊洩漏攻擊，並使用六個字元的序列。 `System.Text.Json` 預設會將所有非 ASCII 字元加入，因此，如果您在中使用，就不需要採取任何動作 `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json` 。 `System.Text.Json` 根據預設，也會將 HTML 機密字元轉義。 如需有關如何覆寫預設行為的詳細資訊 `System.Text.Json` ，請參閱 [自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="comments"></a>註解

在還原序列化期間， `Newtonsoft.Json` 預設會忽略 JSON 中的批註。 <xref:System.Text.Json>預設值是擲回批註的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不包含它們。 如需有關如何允許批註的詳細資訊，請參閱 [允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。

### <a name="trailing-commas"></a>尾端逗號

在還原序列化期間， `Newtonsoft.Json` 預設會忽略結尾的逗號。 它也會忽略多個尾端逗號 (例如 `[{"Color":"Red"},{"Color":"Green"},,]`) 。 <xref:System.Text.Json>預設值是擲回尾端逗號的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。 如需如何接受這些專案的詳細資訊 `System.Text.Json` ，請參閱 [允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。 沒有任何方法可允許多個尾端逗號。

### <a name="converter-registration-precedence"></a>轉換器註冊優先順序

`Newtonsoft.Json`自訂轉換器的註冊優先順序如下所示：

* 屬性上的屬性
* 類型上的屬性
* [轉換器](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) 集合

此順序表示集合中的自訂轉換器 `Converters` 會由在類型層級套用屬性所註冊的轉換器覆寫。 這兩個註冊都會由屬性層級的屬性覆寫。

<xref:System.Text.Json>自訂轉換器的註冊優先順序不同：

* 屬性上的屬性
* <xref:System.Text.Json.JsonSerializerOptions.Converters> 收集
* 類型上的屬性

此處的差異在於集合中的自訂轉換器會 `Converters` 覆寫類型層級的屬性。 這種優先順序背後的目的是要讓執行時間變更覆寫設計階段選項。 沒有任何方法可以變更優先順序。

如需自訂轉換器註冊的詳細資訊，請參閱 [註冊自訂轉換器](system-text-json-converters-how-to.md#register-a-custom-converter)。

### <a name="maximum-depth"></a>最大深度

`Newtonsoft.Json` 預設沒有最大深度限制。 <xref:System.Text.Json>預設限制為64，而且可透過設定來設定 <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType> 。

如果您是 `System.Text.Json` 使用 ASP.NET Core 間接使用，則預設的最大深度限制為32。 預設值與模型系結相同，而且是在 [JsonOptions 類別](https://github.com/dotnet/aspnetcore/blob/1f56888ea03f6a113587a6c4ac4d8b2ded326ffa/src/Mvc/Mvc.Core/src/JsonOptions.cs#L17-L20)中設定。

### <a name="json-strings-property-names-and-string-values"></a> (屬性名稱和字串值的 JSON 字串) 

在還原序列化期間， `Newtonsoft.Json` 接受以雙引號括住的屬性名稱、單引號，或不含引號的屬性名稱。 它接受以雙引號或單引號括住的字串值。 例如， `Newtonsoft.Json` 接受下列 JSON：

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json` 只接受以雙引號括住的屬性名稱和字串值，因為 [RFC 8259](https://tools.ietf.org/html/rfc8259) 規格需要該格式，而且是唯一視為有效 JSON 的格式。

以單引號括住的值會產生包含下列訊息的 [JsonException](xref:System.Text.Json.JsonException) ：

```output
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>字串屬性的非字串值

`Newtonsoft.Json` 接受非字串值，例如數位或常值， `true` 以及用於還原序列化 `false` 為字串類型的屬性。 以下是可成功還原序列化 `Newtonsoft.Json` 為下列類別的 JSON 範例：

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

`System.Text.Json` 不將非字串值還原序列化為字串屬性。 針對字串欄位接收的非字串值會產生包含下列訊息的 [JsonException](xref:System.Text.Json.JsonException) ：

```output
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer"></a>使用 JsonSerializer 的案例

內建功能不支援下列某些案例，但可能的因應措施。 因應措施是 [自訂轉換器](system-text-json-converters-how-to.md)，可能無法提供與功能完全相同的 `Newtonsoft.Json` 功能。 針對其中一些，範例程式碼會以範例的形式提供。 如果您依賴這些 `Newtonsoft.Json` 功能，則需要修改您的 .net 物件模型或其他程式碼變更。

在下列某些案例中，因應措施並非實際或可能的解決方法。 如果您依賴這些 `Newtonsoft.Json` 功能，則不需要進行重大變更，就不可能進行遷移。

### <a name="allow-or-write-numbers-in-quotes"></a>以引號允許或寫入數位

::: zone pivot="dotnet-5-0"
`Newtonsoft.Json` 可以序列化或還原序列化 JSON 字串所表示的數位， (以引號括住) 。 例如，它可以接受： `{"DegreesCelsius":"23"}` 而不是 `{"DegreesCelsius":23}` 。 若要在中啟用該行為 <xref:System.Text.Json> ，請將設 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 為 <xref:System.Text.Json.Serialization.JsonNumberHandling.WriteAsString> 或 <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString> ，或使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。

如果您使用 `System.Text.Json` ASP.NET Core 間接使用，則不需要採取任何動作來取得像這樣的行為 `Newtonsoft.Json` 。 ASP.NET Core 會在使用時指定 [web 預設值](system-text-json-how-to.md#web-defaults-for-jsonserializeroptions) `System.Text.Json` ，而 web 預設值則允許加上引號的數位。

如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-how-to.md#allow-or-write-numbers-in-quotes)住的數位。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`Newtonsoft.Json` 可以序列化或還原序列化 JSON 字串所表示的數位， (以引號括住) 。 例如，它可以接受： `{"DegreesCelsius":"23"}` 而不是 `{"DegreesCelsius":23}` 。 若要在 .NET Core 3.1 中啟用該行為 <xref:System.Text.Json> ，請執行如下列範例所示的自訂轉換子。 轉換器會處理定義為的屬性 `long` ：

* 它會將它們序列化為 JSON 字串。
* 它會在還原序列化時，接受引號內的 JSON 數位和數位。

[!code-csharp[](snippets/system-text-json-how-to/csharp/LongToStringConverter.cs)]

使用個別屬性上的 [屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) ， `long` 或 [將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection) 至集合，以註冊這個自訂轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters> 。
::: zone-end

### <a name="specify-constructor-to-use-when-deserializing"></a>指定還原序列化時要使用的函式

`Newtonsoft.Json` `[JsonConstructor]` 屬性可讓您指定在還原序列化為 POCO 時要呼叫的函式。

::: zone pivot="dotnet-5-0"
`System.Text.Json` 也有 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) 屬性。 如需詳細資訊，請參閱 [不可變的類型和記錄](system-text-json-how-to.md#immutable-types-and-records)。
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> 在 .NET Core 3.1 中，只支援無參數的函式。 因應措施是，您可以在自訂轉換子中呼叫所需的任何一個函數。 請參閱還原序列化 [為不可變的類別和結構](#deserialize-to-immutable-classes-and-structs)的範例。
::: zone-end

### <a name="conditionally-ignore-a-property"></a>有條件地忽略屬性

`Newtonsoft.Json` 有幾種方式可在序列化或還原序列化時有條件地忽略屬性：

* `DefaultContractResolver` 可讓您根據任意準則，選取要包含或忽略的屬性。
* 的 `NullValueHandling` 和 `DefaultValueHandling` 設定 `JsonSerializerSettings` 可讓您指定應忽略所有 null 值或預設值屬性。
* `NullValueHandling` `DefaultValueHandling` 屬性上的和設定 `[JsonProperty]` 可讓您指定當設定為 null 或預設值時應忽略的個別屬性。

::: zone pivot="dotnet-5-0"

<xref:System.Text.Json> 提供下列方法，以在序列化時忽略屬性或欄位：

* 屬性 [（property）上的 [JsonIgnore] 屬性（attribute）](system-text-json-how-to.md#ignore-individual-properties) 會在序列化期間，從 JSON 中省略屬性（property）。
* [IgnoreReadOnlyProperties](system-text-json-how-to.md#ignore-all-read-only-properties) global 選項可讓您忽略所有的唯讀屬性。
* 如果您要 [包含欄位](system-text-json-how-to.md#include-fields)， <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global 選項可讓您忽略所有唯讀欄位。
* `DefaultIgnoreCondition`Global 選項可讓您[忽略所有具有預設值的實值型別屬性](system-text-json-how-to.md#ignore-all-default-value-properties)，或[忽略所有具有 null 值的參考型](system-text-json-how-to.md#ignore-all-null-value-properties)別屬性。

::: zone-end

::: zone pivot="dotnet-core-3-1"

<xref:System.Text.Json> 在 .NET Core 3.1 中，會提供下列方法，在序列化時忽略屬性：

* 屬性 [（property）上的 [JsonIgnore] 屬性（attribute）](system-text-json-how-to.md#ignore-individual-properties) 會在序列化期間，從 JSON 中省略屬性（property）。
* [IgnoreNullValues](system-text-json-how-to.md#ignore-all-null-value-properties) global 選項可讓您忽略所有 null 值屬性。
* [IgnoreReadOnlyProperties](system-text-json-how-to.md#ignore-all-read-only-properties) global 選項可讓您忽略所有的唯讀屬性。
::: zone-end

這些選項 **不** 會讓您：

::: zone pivot="dotnet-5-0"

* 根據在執行時間評估的任意準則，略過選取的屬性。

::: zone-end

::: zone pivot="dotnet-core-3-1"

* 忽略所有具有類型之預設值的屬性。
* 略過具有類型之預設值的選取屬性。
* 如果其值為 null，則忽略選取的屬性。
* 根據在執行時間評估的任意準則，略過選取的屬性。

::: zone-end

針對該功能，您可以撰寫自訂的轉換器。 以下是說明此方法的範例 POCO 和自訂的轉換器：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

`Summary`如果屬性的值為 null、空字串或 "N/A"，轉換器會導致從序列化中省略屬性。

[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection)至集合，以註冊這個自訂轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters> 。

如果有下列情況，這個方法需要額外的邏輯：

* POCO 包含複雜屬性。
* 您需要處理諸如或選項等屬性，例如 `[JsonIgnore]` 自訂編碼器。

### <a name="public-and-non-public-fields"></a>公用和非公用欄位

`Newtonsoft.Json` 可以序列化和還原序列化欄位以及屬性。

::: zone pivot="dotnet-5-0"
在中 <xref:System.Text.Json> ，使用 <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> 全域設定或 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性，在序列化或還原序列化時包含公用欄位。 如需範例，請參閱 [包含欄位](system-text-json-how-to.md#include-fields)。
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> 在 .NET Core 3.1 中，僅適用于公用屬性。 自訂轉換器可以提供這種功能。
::: zone-end

### <a name="preserve-object-references-and-handle-loops"></a>保留物件參考和控制碼迴圈

依預設，會 `Newtonsoft.Json` 依值進行序列化。 例如，如果物件包含兩個屬性，其中包含相同物件的參考，則該 `Person` 物件屬性的值 `Person` 會在 JSON 中重複。

`Newtonsoft.Json` 具有 `PreserveReferencesHandling` 的設定可 `JsonSerializerSettings` 讓您以傳址方式序列化：

* 系統會將識別碼中繼資料加入至為第一個物件建立的 JSON 中 `Person` 。
* 針對第二個物件所建立的 JSON `Person` 包含該識別碼的參考，而不是屬性值的參考。

`Newtonsoft.Json` 也有一個 `ReferenceLoopHandling` 設定，可讓您忽略迴圈參考，而不是擲回例外狀況。

::: zone pivot="dotnet-5-0"
若要保留參考並處理中的迴圈參考 <xref:System.Text.Json> ，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A?displayProperty=nameWithType> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。 此 `ReferenceHandler.Preserve` 設定相當於 `PreserveReferencesHandling`  =  `PreserveReferencesHandling.All` 中的 `Newtonsoft.Json` 。

如同 Newtonsoft.Json [ReferenceResolver](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializer_ReferenceResolver.htm)，此 <xref:System.Text.Json.Serialization.ReferenceResolver?displayProperty=fullName> 類別會定義在序列化和還原序列化時保留參考的行為。 建立衍生類別以指定自訂行為。 如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。

`Newtonsoft.Json`不支援某些相關功能：

* [JsonPropertyAttribute. IsReference](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonPropertyAttribute_IsReference.htm)
* [JsonPropertyAttribute. ReferenceLoopHandling](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonPropertyAttribute_ReferenceLoopHandling.htm)

如需詳細資訊，請參閱 [保留參考和處理迴圈參考](system-text-json-how-to.md#preserve-references-and-handle-circular-references)
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。
::: zone-end

### <a name="dictionary-with-non-string-key"></a>具有非字串索引鍵的字典

::: zone pivot="dotnet-5-0"
`Newtonsoft.Json`和都 `System.Text.Json` 支援型別的集合 `Dictionary<TKey, TValue>` 。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`Newtonsoft.Json` 支援型別的集合 `Dictionary<TKey, TValue>` 。 在 .NET Core 3.1 中內建的字典集合支援 <xref:System.Text.Json> 僅限於 `Dictionary<string, TValue>` 。 也就是說，索引鍵必須是字串。

若要在 .NET Core 3.1 中支援具有整數或其他類型作為索引鍵的字典，請建立類似 [于如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)的轉換器。
::: zone-end

### <a name="types-without-built-in-support"></a>沒有內建支援的類型

<xref:System.Text.Json> 未提供下列類型的內建支援：

* <xref:System.Data.DataTable> 和相關類型
* F # 類型，例如 [區分](../../fsharp/language-reference/discriminated-unions.md)等位、 [記錄類型](../../fsharp/language-reference/records.md)和 [匿名記錄類型](../../fsharp/language-reference/anonymous-records.md)。
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> 及其相關聯的泛型型別

自訂轉換器可以針對沒有內建支援的類型來執行。

### <a name="polymorphic-serialization"></a>多型序列化

`Newtonsoft.Json` 自動執行多型序列化。 如需的有限多型序列化功能的詳細資訊 <xref:System.Text.Json> ，請參閱 [序列化衍生類別的屬性](system-text-json-how-to.md#serialize-properties-of-derived-classes)。

其中所述的因應措施是定義可能包含衍生類別做為類型的屬性 `object` 。 如果無法這麼做，另一個選項是使用整個繼承類型階層的方法來建立轉換器，例如 `Write` [如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)的範例。

### <a name="polymorphic-deserialization"></a>多型還原序列化

`Newtonsoft.Json` 具有在序列化 `TypeNameHandling` 時將類型名稱中繼資料新增至 JSON 的設定。 它會在還原序列化時使用中繼資料，以進行多型還原序列化。 <xref:System.Text.Json> 可以進行有限範圍的多型序列化，但不能進行多型還原 [序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes) 。

若要支援多型還原序列化，請建立類似 [于如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)的轉換器。

### <a name="deserialization-of-object-properties"></a>物件屬性的還原序列化

當還原序列化 `Newtonsoft.Json` 為時 <xref:System.Object> ，會：

* 推斷 JSON 承載 (中的基本數值型別，而非 `null`) 並傳回儲存的 `string` 、 `long` 、 `double` 、 `boolean` 或為已 `DateTime` 封裝的物件。 *基本值* 是單一 json 值，例如 JSON 數位、字串、、 `true` `false` 或 `null` 。
* `JObject` `JArray` 針對 JSON 承載中的複雜值傳回或。 *複雜值* 是以括弧括住的 JSON 索引鍵/值組集合 (`{}`) 或括弧內的值清單 (`[]`) 。 大括弧或括弧內的屬性和值可以有其他屬性或值。
* 當承載具有 JSON 常值時，會傳回 null 參考 `null` 。

<xref:System.Text.Json> 在還原 `JsonElement` 序列化為時，儲存基本和複雜值的已封裝 <xref:System.Object> ，例如：

* `object` 屬性。
* `object`字典值。
* `object`陣列值。
* 根 `object` 。

不過， `System.Text.Json` `null` 會將相同的視為 `Newtonsoft.Json` ，並且在承載中有 JSON 常值時，傳回 null 參考 `null` 。

若要執行屬性的型別推斷 `object` ，請建立類似 [如何撰寫自訂轉換器](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)的轉換器。

### <a name="deserialize-null-to-non-nullable-type"></a>將 null 還原序列化為不可為 null 的型別

`Newtonsoft.Json` 在下列案例中不會擲回例外狀況：

* `NullValueHandling` 設定為 `Ignore` 、和
* 在還原序列化期間，JSON 會針對不可為 null 的實值型別包含 null 值。

在相同的案例中， <xref:System.Text.Json> 會擲回例外狀況。 在中， (對應的 null 處理 `System.Text.Json` 設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>  =  `true` 。 ) 

如果您擁有目標型別，最好的解決方法是讓屬性成為可為 null 的 (例如，變更 `int` 為 `int?`) 。

另一個因應措施是建立類型的轉換器，例如下列範例來處理類型的 null 值 `DateTimeOffset` ：

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetNullHandlingConverter.cs)]

您可以 [使用屬性（attribute）上的屬性（property](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) ）或 [將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection) 至集合，以註冊這個自訂轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters> 。

**注意：** 上述轉換器會 **以不同** 于 `Newtonsoft.Json` 指定預設值的 poco 來處理 null 值。 例如，假設下列程式碼代表您的目標物件：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

假設下列 JSON 是使用上述轉換器還原序列化：

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

還原序列化之後， `Date` 屬性會有 1/1/0001 (`default(DateTimeOffset)`) ，也就是會覆寫在函式中設定的值。 由於具有相同的 POCO 和 JSON，還原序列化 `Newtonsoft.Json` 會在屬性中留下 1/1/2001 `Date` 。

### <a name="deserialize-to-immutable-classes-and-structs"></a>還原序列化為不可變的類別和結構

`Newtonsoft.Json` 可以還原序列化為不可變的類別和結構，因為它可以使用具有參數的函式。

::: zone pivot="dotnet-5-0"
在中 <xref:System.Text.Json> ，使用 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) 屬性來指定參數化函式的使用方式。 C # 9 中的記錄也是不可變的，且支援作為還原序列化目標。 如需詳細資訊，請參閱 [不可變的類型和記錄](system-text-json-how-to.md#immutable-types-and-records)。
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> 在 .NET Core 3.1 中，只支援公用無參數的函式。 因應措施是，您可以使用自訂轉換器中的參數來呼叫函式。

以下是具有多個函式參數的不可變結構：

[!code-csharp[](snippets/system-text-json-how-to/csharp/ImmutablePoint.cs#ImmutablePoint)]

以下是將此結構序列化和還原序列化的轉換器：

[!code-csharp[](snippets/system-text-json-how-to/csharp/ImmutablePointConverter.cs)]

[將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection)至集合，以註冊這個自訂的轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters> 。

如需處理開放式泛型屬性之類似轉換器的範例，請參閱索引 [鍵/值組的內建轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)。
::: zone-end

### <a name="required-properties"></a>必要屬性

在中 `Newtonsoft.Json` ，您可以在屬性上設定來指定屬性為必要項 `Required` `[JsonProperty]` 。 `Newtonsoft.Json` 如果未在 JSON 中針對標示為必要的屬性收到任何值，則會擲回例外狀況。

<xref:System.Text.Json> 如果未收到目標型別其中一個屬性的值，則不會擲回例外狀況。 例如，如果您有一個 `WeatherForecast` 類別：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

下列 JSON 會還原序列化，而不會發生錯誤：

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

若要在 JSON 中沒有任何屬性時將還原序列化失敗 `Date` ，請執行自訂轉換器。 如果未在還原序列化 `Date` 完成之後設定屬性，則下列範例轉換器程式碼會擲回例外狀況：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecastRequiredPropertyConverter.cs)]

[將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection)至集合，以註冊這個自訂的轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 。

以遞迴方式呼叫轉換器的這個模式需要您使用註冊轉換器 <xref:System.Text.Json.JsonSerializerOptions> ，而不是使用屬性。 如果您使用屬性來註冊轉換器，自訂轉換器會以遞迴方式呼叫本身。 結果是在堆疊溢位例外狀況中結束的無限迴圈。

當您使用 options 物件註冊轉換器時，請避免在以遞迴方式呼叫或時傳遞 options 物件，以避免無限 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 迴圈 <xref:System.Text.Json.JsonSerializer.Deserialize%2A> 。 Options 物件包含 <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> 集合。 如果您將它傳入 `Serialize` 或 `Deserialize` ，自訂轉換器會呼叫本身，並產生會導致堆疊溢位例外狀況的無限迴圈。 如果預設選項不可行，請使用您需要的設定來建立新的選項實例。 這種方法會很慢，因為每個新的實例會獨立快取。

另外還有一個可 `JsonConverterAttribute` 在類別上使用註冊來轉換的替代模式。 在這個方法中，轉換器程式碼 `Serialize` `Deserialize` 會在衍生自類別的類別上呼叫或，以進行轉換。 衍生的類別未套用 `JsonConverterAttribute` 至該類別。 在下列替代方案的範例中：

* `WeatherForecastWithRequiredPropertyConverterAttribute` 是要還原序列化的類別，並套用 `JsonConverterAttribute` 至該類別。
* `WeatherForecastWithoutRequiredPropertyConverterAttribute` 是沒有轉換器屬性的衍生類別。
* 轉換器中的程式碼會呼叫 `Serialize` 並 `Deserialize` 開啟， `WeatherForecastWithoutRequiredPropertyConverterAttribute` 以避免發生無限迴圈。 由於額外的物件具現化和屬性值的複製，在序列化時，會有此方法的效能成本。

以下是 `WeatherForecast*` 類型：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithReqPptyConverterAttr)]

以下是轉換器：

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecastRequiredPropertyConverterForAttributeRegistration.cs)]

如果您需要處理屬性（例如 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) ）或不同選項（例如自訂編碼器），則必要的屬性轉換器會需要額外的邏輯。 此外，範例程式碼不會處理在函式中設定預設值的屬性。 這種方法並不區分下列案例：

* JSON 中缺少屬性。
* JSON 中有一個不可為 null 之類型的屬性，但是此值是類型的預設值，例如的零 `int` 。
* JSON 中有可為 null 的實值型別的屬性，但值為 null。

### <a name="specify-date-format"></a>指定日期格式

`Newtonsoft.Json` 提供數種方式來控制和類型的屬性如何 `DateTime` `DateTimeOffset` 序列化和還原序列化：

* `DateTimeZoneHandling`設定可以用來將所有值序列化 `DateTime` 為 UTC 日期。
* `DateFormatString`設定和 `DateTime` 轉換器可以用來自訂日期字串的格式。

在中 <xref:System.Text.Json> ，具有內建支援的唯一格式是 ISO 8601-1:2019，因為它已廣泛採用、明確，並且會精確地進行往返。 若要使用任何其他格式，請建立自訂的轉換器。 如需詳細資訊，請參閱[中 System.Text.Json 的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)。

### <a name="callbacks"></a>回撥

`Newtonsoft.Json` 可讓您在序列化或還原序列化程式中的數個點執行自訂程式碼：

* 開始將物件還原序列化時，OnDeserializing () 
* 完成還原序列化物件時的 OnDeserialized () 
* 開始序列化物件時，OnSerializing () 
* 完成序列化物件的 OnSerialized () 

在中 <xref:System.Text.Json> ，您可以藉由撰寫自訂轉換器來模擬回呼。 下列範例顯示 POCO 的自訂轉換子。 轉換器包含的程式碼會在每個對應至回呼的點上顯示訊息 `Newtonsoft.Json` 。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecastCallbacksConverter.cs)]

[將轉換器新增](system-text-json-converters-how-to.md#registration-sample---converters-collection)至集合，以註冊這個自訂的轉換器 <xref:System.Text.Json.JsonSerializerOptions.Converters> 。

如果您使用的自訂轉換器遵循上述範例：

* 程式 `OnDeserializing` 代碼無法存取新的 POCO 實例。 若要在還原序列化開始時操作新的 POCO 實例，請將該程式碼放入 POCO 函式中。
* 以遞迴方式呼叫或時，在 options 物件中註冊轉換器，而不是傳遞 options 物件，以避免無限迴圈 `Serialize` `Deserialize` 。

如需以遞迴方式呼叫或的自訂轉換器的詳細資訊 `Serialize` `Deserialize` ，請參閱本文稍早的 [必要屬性](#required-properties) 一節。

### <a name="non-public-property-setters-and-getters"></a>非公用屬性 setter 和 getter

`Newtonsoft.Json` 可以透過屬性使用私用和內部屬性 setter 和 getter `JsonProperty` 。

::: zone pivot="dotnet-5-0"
<xref:System.Text.Json> 透過 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性支援私用和內部屬性 setter 和 getter。 如需範例程式碼，請參閱 [非公用屬性存取](system-text-json-how-to.md#non-public-property-accessors)子。
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> 在 .NET Core 3.1 中，只支援公用 setter。 自訂轉換器可以提供這種功能。
::: zone-end

### <a name="populate-existing-objects"></a>填入現有的物件

中的方法會將 `JsonConvert.PopulateObject` `Newtonsoft.Json` JSON 檔案還原序列化為類別的現有實例，而不是建立新的實例。 <xref:System.Text.Json> 一律使用預設公用無參數的函式，建立目標型別的新實例。 自訂轉換器可以還原序列化為現有的實例。

### <a name="reuse-rather-than-replace-properties"></a>重複使用而非取代屬性

此 `Newtonsoft.Json` `ObjectCreationHandling` 設定可讓您指定屬性中的物件應該重複使用，而不是在還原序列化期間取代。 <xref:System.Text.Json> 一律取代屬性中的物件。  自訂轉換器可以提供這種功能。

### <a name="add-to-collections-without-setters"></a>新增至不含 setter 的集合

在還原序列化期間， `Newtonsoft.Json` 即使屬性沒有 setter，也會將物件加入至集合。 <xref:System.Text.Json> 忽略沒有 setter 的屬性。 自訂轉換器可以提供這種功能。

### <a name="systemruntimeserialization-attributes"></a>System.object。序列化屬性

<xref:System.Text.Json> 不支援來自 `System.Runtime.Serialization` 命名空間的屬性，例如 `DataMemberAttribute` 和 `IgnoreDataMemberAttribute` 。

### <a name="octal-numbers"></a>八進位數位

`Newtonsoft.Json` 將前置零的數位視為八進位數位。 <xref:System.Text.Json> 不允許前置零，因為 [RFC 8259](https://tools.ietf.org/html/rfc8259) 規格不允許它們。

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json` 可以設定為在還原序列化期間擲回例外狀況（如果 JSON 包括目標型別中遺漏的屬性）。 <xref:System.Text.Json> 除非您使用 [[JsonExtensionData] 屬性](system-text-json-how-to.md#handle-overflow-json)，否則會忽略 JSON 中的額外屬性。 遺漏的成員功能沒有因應措施。

### <a name="tracewriter"></a>>tracewriter

`Newtonsoft.Json` 可讓您使用 `TraceWriter` 來進行 debug，以查看序列化或還原序列化所產生的記錄。 <xref:System.Text.Json> 不會進行記錄。

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>相較于 JToken (（例如 JObject、JArray) ），JsonDocument 和 JsonElement

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供從現有的 JSON 承載剖析和建立 **唯讀** 檔物件模型 (DOM) 的能力。 DOM 提供 JSON 承載中資料的隨機存取。 撰寫承載的 JSON 專案可以透過型別存取 <xref:System.Text.Json.JsonElement> 。 此 `JsonElement` 類型會提供 api，以將 JSON 文字轉換成常見的 .net 類型。 `JsonDocument` 公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。

### <a name="jsondocument-is-idisposable"></a>JsonDocument 為 IDisposable

`JsonDocument` 將資料的記憶體內部視圖建立到集區緩衝區。 因此，與 `JObject` 或 `JArray` 不同 `Newtonsoft.Json` 的是， `JsonDocument` 型別會執行，而且必須在 `IDisposable` using 區塊內使用。

只有 `JsonDocument` 當您想要將存留期擁有權和處置責任轉移給呼叫者時，才會從您的 API 傳回。 在大部分的情況下，這不是必要的。 如果呼叫端需要使用整個 JSON 檔，請傳回的 <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A> ，也就是 <xref:System.Text.Json.JsonElement> 。 如果呼叫端需要使用 JSON 檔中的特定元素，則傳回 <xref:System.Text.Json.JsonElement.Clone%2A> 該的 <xref:System.Text.Json.JsonElement> 。 如果您 `RootElement` 直接傳回或子項目，但未建立 `Clone` ，則呼叫者將無法在擁有它的之後，存取傳回的 `JsonElement` `JsonDocument` 。

以下是要求您建立的範例 `Clone` ：

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

上述程式碼需要 `JsonElement` 包含 `fileName` 屬性的。 它會開啟 JSON 檔案，並建立 `JsonDocument` 。 方法假設呼叫端想要處理整份檔，因此它會傳回的 `Clone` `RootElement` 。

如果您收到， `JsonElement` 且傳回子項目，則不需要傳回 `Clone` 子項目的。 呼叫端會負責維持 `JsonDocument` 傳入的 `JsonElement` 所屬的。 例如：

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument 是唯讀的

<xref:System.Text.Json>DOM 無法加入、移除或修改 JSON 元素。 它是針對效能所設計，並減少剖析常見 JSON 承載大小的配置， (也就是 < 1 MB) 。 如果您的案例目前使用可修改的 DOM，下列其中一個因應措施可能是可行的：

* 若要 `JsonDocument` 從頭開始建立 (也就是不將現有的 JSON 承載傳遞給 `Parse` 方法) ，請使用來寫入 JSON 文字， `Utf8JsonWriter` 並剖析其輸出，使其成為新的 `JsonDocument` 。
* 若要修改現有的 `JsonDocument` ，請使用它來寫入 JSON 文字、在寫入時進行變更，以及剖析其輸出，以建立新的 `JsonDocument` 。
* 若要合併現有的 JSON 檔（相當於 `JObject.Merge` 或 `JContainer.Merge` 中的 api） `Newtonsoft.Json` ，請參閱 [此 GitHub 問題](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)。

### <a name="jsonelement-is-a-union-struct"></a>JsonElement 是聯集結構

`JsonDocument` 公開 `RootElement` 做為型別的屬性 <xref:System.Text.Json.JsonElement> ，它是包含任何 JSON 專案的 union、struct 型別。 `Newtonsoft.Json` 使用專用的階層型別 `JObject` ，例如、 `JArray` 、 `JToken` 等等。 `JsonElement` 這是您可以搜尋和列舉的專案，您可以使用 `JsonElement` 將 JSON 元素具體化成 .net 類型。

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>如何搜尋子項目的 JsonDocument 和 JsonElement

使用或從搜尋 JSON `JObject` 權杖 `JArray` `Newtonsoft.Json` 通常相對較快，因為它們是在某些字典中進行查閱。 相較之下，搜尋 `JsonElement` 需要連續搜尋屬性，因此相當慢 (例如使用 `TryGetProperty`) 時。 <xref:System.Text.Json> 的設計目的是要將初始剖析時間（而不是查閱時間）降到最低。 因此，在搜尋物件時，請使用下列方法將效能優化 `JsonDocument` ：

* 使用內建的枚舉器 (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> 和 <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) ，而不是執行您自己的索引或迴圈。
* 請勿 `JsonDocument` 使用在每個屬性上進行順序搜尋 `RootElement` 。 相反地，根據 JSON 資料的已知結構來搜尋嵌套的 JSON 物件。 例如，如果您要尋找 `Grade` 物件中的屬性 `Student` ，請在物件之間執行迴圈， `Student` 並 `Grade` 為每個物件取得值，而不是搜尋所有 `JsonElement` 尋找屬性的物件 `Grade` 。 如此一來，就會導致相同資料的不必要傳遞。

如需程式碼範例，請參閱 [使用 JsonDocument 存取資料](system-text-json-how-to.md#use-jsondocument-for-access-to-data)。

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader 相較于 JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從[ReadOnlySpan \<byte> ](xref:System.ReadOnlySpan%601)或[ReadOnlySequence \<byte> ](xref:System.Buffers.ReadOnlySequence%601)讀取。 `Utf8JsonReader`是低層級的型別，可用來建立自訂剖析器和還原序列化程式。

下列各節說明使用的建議程式設計模式 `Utf8JsonReader` 。

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader 是 ref 結構

因為 `Utf8JsonReader` 類型是 *ref 結構* ，所以具有 [某些限制](../../csharp/language-reference/builtin-types/struct.md#ref-struct)。 例如，它無法在 ref 結構以外的類別或結構上儲存為欄位。 為了達到高效能，此型別必須是， `ref struct` 因為它需要快取輸入[ReadOnlySpan \<byte> ](xref:System.ReadOnlySpan%601)，它本身就是 ref 結構。 此外，這種類型是可變動的，因為它會保存狀態。 因此， **以傳址方式傳遞** ，而不是以傳值方式傳遞。 以傳值方式傳遞會導致結構複製，而且呼叫端看不到狀態變更。 這與的不同之處在于， `Newtonsoft.Json` 因為 `Newtonsoft.Json` `JsonTextReader` 是類別。 如需如何使用 ref 結構的詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../csharp/write-safe-efficient-code.md)。

### <a name="read-utf-8-text"></a>讀取 UTF-8 文字

若要在使用時達到最佳效能 `Utf8JsonReader` ，請讀取已編碼為 utf-8 文字而非 utf-16 字串的 JSON 承載。 如需程式碼範例，請參閱 [使用 Utf8JsonReader 來篩選資料](system-text-json-how-to.md#filter-data-using-utf8jsonreader)。

### <a name="read-with-a-stream-or-pipereader"></a>使用資料流程或 PipeReader 讀取

`Utf8JsonReader`支援從 utf-8 編碼的[ReadOnlySpan \<byte> ](xref:System.ReadOnlySpan%601)或[ReadOnlySequence \<byte> ](xref:System.Buffers.ReadOnlySequence%601) (讀取，這是從) 讀取的結果 <xref:System.IO.Pipelines.PipeReader> 。

針對同步讀取，您可以讀取 JSON 承載，直到資料流程的結尾變成位元組陣列並將其傳遞至讀取器。 若要從編碼為 UTF-16)  (字串讀取，請呼叫 <xref:System.Text.Encoding.UTF8> 。<xref:System.Text.Encoding.GetBytes%2A> 首先，將字串轉碼至 UTF-8 編碼的位元組陣列。 然後將其傳遞至 `Utf8JsonReader` 。

因為 `Utf8JsonReader` 會將輸入視為 JSON 文字，所以 (BOM) 的 utf-8 位元組順序標記會被視為不正確 JSON。 呼叫端必須在將資料傳遞給讀取器之前進行篩選。

如需程式碼範例，請參閱 [使用 Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader)。

### <a name="read-with-multi-segment-readonlysequence"></a>使用多區段 ReadOnlySequence 進行讀取

如果您的 JSON 輸入是[ReadOnlySpan \<byte> ](xref:System.ReadOnlySpan%601)， `ValueSpan` 則您可以在執行讀取迴圈時，從讀取器上的屬性存取每個 json 元素。 但是，如果您的輸入是從) 讀取的[ReadOnlySequence \<byte> ](xref:System.Buffers.ReadOnlySequence%601) (<xref:System.IO.Pipelines.PipeReader> ，則某些 JSON 元素可能會跨物件的多個區段 `ReadOnlySequence<byte>` 。 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>在連續記憶體區塊中，無法存取這些元素。 相反地，每當您有多個區段做 `ReadOnlySequence<byte>` 為輸入時，請輪詢 <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> 讀取器上的屬性，以瞭解如何存取目前的 JSON 元素。 以下是建議的模式：

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

請勿使用 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> ，藉由呼叫屬性名稱查閱來執行逐位元組的比較 <xref:System.MemoryExtensions.SequenceEqual%2A> 。 <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>改為呼叫，因為該方法會將任何在 JSON 中進行轉義的字元。 以下範例顯示如何搜尋名為 "name" 的屬性：

[!code-csharp[](snippets/system-text-json-how-to/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>讀取 null 值成為可為 null 的實數值型別

`Newtonsoft.Json` 提供傳回的 Api <xref:System.Nullable%601> ，例如 `ReadAsBoolean` ，藉由傳回來 `Null` `TokenType` 為您處理 `bool?` 。 內建 `System.Text.Json` api 只會傳回不可為 null 的實數值型別。 例如，會傳回 <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> `bool` 。 如果在 JSON 中找到例外狀況，則會擲回例外狀況 `Null` 。 下列範例示範兩種處理 null 的方式，一個方法是傳回可為 null 的實值型別，另一個則傳回預設值：

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

如果您需要繼續使用 `Newtonsoft.Json` 特定的目標架構，您可以多目標且有兩個執行。 不過，這並不簡單，而且需要 `#ifdefs` 進行一些和來源的複製。 有一種方法可以盡可能共用最多的程式碼，以建立與的包裝函式 `ref struct` `Utf8JsonReader` `Newtonsoft.Json` `JsonTextReader` 。 這個包裝函式會統一公用介面區，同時隔離行為差異。 這可讓您將變更主要與型別的結構隔離，以及透過傳址方式傳遞新的型別。 以下是 [DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) 程式庫的模式：

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter 相較于 JsoNtextwriter,

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（如、和）撰寫 UTF-8 編碼的 JSON 文字 `String` `Int32` `DateTime` 。 寫入器是一種低層級的型別，可用來建立自訂序列化程式。

下列各節說明使用的建議程式設計模式 `Utf8JsonWriter` 。

### <a name="write-with-utf-8-text"></a>使用 UTF-8 文字寫入

若要在使用時達到最佳效能 `Utf8JsonWriter` ，請撰寫已編碼為 utf-8 文字而非 utf-16 字串的 JSON 承載。 用 <xref:System.Text.Json.JsonEncodedText> 來快取已知字串屬性名稱和值，並將其預先編碼為靜態，並將其傳遞至寫入器，而不是使用 utf-16 字串常值。 這比快取和使用 UTF-8 位元組陣列更快。

如果您需要進行自訂的轉義，這個方法也適用。 `System.Text.Json` 不讓您在寫入字串時停用轉義。 不過，您可以將自己的自訂 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 作為選項傳遞給寫入器，或是自行建立 `JsonEncodedText` 使用 `JavascriptEncoder` 來進行轉義的，然後寫入， `JsonEncodedText` 而不是字串。 如需詳細資訊，請參閱 [自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="write-raw-values"></a>寫入原始值

`Newtonsoft.Json` `WriteRawValue` 方法會在預期值的位置寫入原始 JSON。 <xref:System.Text.Json> 沒有直接對等專案，但以下是確保只寫入有效 JSON 的因應措施：

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>自訂字元轉義

的 [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) 設定 `JsonTextWriter` 提供選項，以將所有非 ASCII 字元 **或** HTML 字元全部 escape。 依預設，會將 `Utf8JsonWriter` 所有非 ASCII **和** HTML 字元全部加上轉義。 這種轉義是針對深層防禦的安全性原因進行。 若要指定不同的轉義原則，請建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 和設定 <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType> 。 如需詳細資訊，請參閱 [自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。

### <a name="customize-json-format"></a>自訂 JSON 格式

`JsonTextWriter` 包含下列沒有對等專案的設定 `Utf8JsonWriter` ：

* [縮排](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) -指定要縮排的字元數。 `Utf8JsonWriter` 一律會進行2個字元的縮排。
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -指定要用於縮排的字元。  `Utf8JsonWriter` 一律使用空白。
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -指定用來圍繞字串值的字元。  `Utf8JsonWriter` 一律使用雙引號。
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -指定是否以引號括住屬性名稱。  `Utf8JsonWriter` 一律以引號括住。

沒有任何因應措施可讓您以這些方式自訂產生的 JSON `Utf8JsonWriter` 。

### <a name="write-null-values"></a>寫入 null 值

若要使用寫入 null 值 `Utf8JsonWriter` ，請呼叫：

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> 寫入索引鍵/值組，其值為 null。
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> 將 null 寫入為 JSON 陣列的元素。

若為字串屬性，則為，如果字串為 null， <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> 且 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> 相當於 `WriteNull` 和 `WriteNullValue` 。

### <a name="write-timespan-uri-or-char-values"></a>寫入 Timespan、Uri 或 char 值

`JsonTextWriter` 提供 `WriteValue` [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm)、 [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)和 [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) 值的方法。 `Utf8JsonWriter` 沒有對等的方法。 請改為透過呼叫將這些值格式化為字串 (`ToString()` ，例如) 和呼叫 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> 。

### <a name="multi-targeting"></a>多目標

如果您需要繼續使用 `Newtonsoft.Json` 特定的目標架構，您可以多目標且有兩個執行。 不過，這並不簡單，而且需要 `#ifdefs` 進行一些和來源的複製。 有一種方法可以盡可能共用最多的程式碼，以建立與的包裝函式 `Utf8JsonWriter` `Newtonsoft` `JsonTextWriter` 。 這個包裝函式會統一公用介面區，同時隔離行為差異。 這可讓您將變更主要與型別的結構隔離。 [DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) 程式庫如下：

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>其他資源

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Json 概述](system-text-json-overview.md)
* [如何使用 System.Text.Json](system-text-json-how-to.md)
* [如何撰寫自訂轉換器](system-text-json-converters-how-to.md)
* [中的 DateTime 和 DateTimeOffset 支援 System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
