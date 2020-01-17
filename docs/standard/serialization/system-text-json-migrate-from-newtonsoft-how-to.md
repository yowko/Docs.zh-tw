---
title: 從 Newtonsoft 遷移至 System.object-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 01f94bcfce97da8c71b1b709baa34c2b7509a5e5
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116682"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a><span data-ttu-id="e9f10-102">如何從 Newtonsoft 遷移至 System.web. Json</span><span class="sxs-lookup"><span data-stu-id="e9f10-102">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>

<span data-ttu-id="e9f10-103">本文說明如何從[Newtonsoft](https://www.newtonsoft.com/json)遷移至 <xref:System.Text.Json>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-103">This article shows how to migrate from [Newtonsoft.Json](https://www.newtonsoft.com/json) to <xref:System.Text.Json>.</span></span>

 <span data-ttu-id="e9f10-104">`System.Text.Json` 主要著重于效能、安全性和標準合規性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-104">`System.Text.Json` focuses primarily on performance, security, and standards compliance.</span></span> <span data-ttu-id="e9f10-105">它在預設行為上有一些主要差異，並不是要與 `Newtonsoft.Json`的功能同位。</span><span class="sxs-lookup"><span data-stu-id="e9f10-105">It has some key differences in default behavior and doesn't aim to have feature parity with `Newtonsoft.Json`.</span></span> <span data-ttu-id="e9f10-106">在某些情況下，`System.Text.Json` 沒有內建功能，但有建議的因應措施。</span><span class="sxs-lookup"><span data-stu-id="e9f10-106">For some scenarios, `System.Text.Json` has no built-in functionality, but there are recommended workarounds.</span></span> <span data-ttu-id="e9f10-107">針對其他案例，因應措施並不實用。</span><span class="sxs-lookup"><span data-stu-id="e9f10-107">For other scenarios, workarounds are impractical.</span></span> <span data-ttu-id="e9f10-108">如果您的應用程式相依于遺失的功能，請考慮提出[問題](https://github.com/dotnet/runtime/issues/new)，以瞭解是否可以新增您案例的支援。</span><span class="sxs-lookup"><span data-stu-id="e9f10-108">If your application depends on a missing feature, consider [filing an issue](https://github.com/dotnet/runtime/issues/new) to find out if support for your scenario can be added.</span></span>

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

<span data-ttu-id="e9f10-109">本文大部分是關於如何使用 <xref:System.Text.Json.JsonSerializer> API，但它也包含如何使用 <xref:System.Text.Json.JsonDocument> （代表檔物件模型或 DOM）、<xref:System.Text.Json.Utf8JsonReader>和 <xref:System.Text.Json.Utf8JsonWriter> 類型的指引。</span><span class="sxs-lookup"><span data-stu-id="e9f10-109">Most of this article is about how to use the <xref:System.Text.Json.JsonSerializer> API, but it also includes guidance on how to use the <xref:System.Text.Json.JsonDocument> (which represents the Document Object Model or DOM), <xref:System.Text.Json.Utf8JsonReader>, and <xref:System.Text.Json.Utf8JsonWriter> types.</span></span> <span data-ttu-id="e9f10-110">本文會依照下列順序組織成幾個區段：</span><span class="sxs-lookup"><span data-stu-id="e9f10-110">The article is organized into sections in the following order:</span></span>

* [<span data-ttu-id="e9f10-111">相較于 Newtonsoft，**預設**JsonSerializer 行為的差異</span><span class="sxs-lookup"><span data-stu-id="e9f10-111">Differences in **default** JsonSerializer behavior compared to Newtonsoft.Json</span></span>](#differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson)
* [<span data-ttu-id="e9f10-112">使用需要因應措施之 JsonSerializer 的案例</span><span class="sxs-lookup"><span data-stu-id="e9f10-112">Scenarios using JsonSerializer that require workarounds</span></span>](#scenarios-using-jsonserializer-that-require-workarounds)
* [<span data-ttu-id="e9f10-113">JsonSerializer 目前不支援的案例</span><span class="sxs-lookup"><span data-stu-id="e9f10-113">Scenarios that JsonSerializer currently doesn't support</span></span>](#scenarios-that-jsonserializer-currently-doesnt-support)
* [<span data-ttu-id="e9f10-114">相較于 JToken 的 JsonDocument 和 JsonElement （例如 JObject、JArray）</span><span class="sxs-lookup"><span data-stu-id="e9f10-114">JsonDocument and JsonElement compared to JToken (like JObject, JArray)</span></span>](#jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray)
* [<span data-ttu-id="e9f10-115">Utf8JsonReader 與 JsonTextReader 的比較</span><span class="sxs-lookup"><span data-stu-id="e9f10-115">Utf8JsonReader compared to JsonTextReader</span></span>](#utf8jsonreader-compared-to-jsontextreader)
* [<span data-ttu-id="e9f10-116">Utf8JsonWriter 與 Json.net jsoNtextwriter, 的比較</span><span class="sxs-lookup"><span data-stu-id="e9f10-116">Utf8JsonWriter compared to JsonTextWriter</span></span>](#utf8jsonwriter-compared-to-jsontextwriter)

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a><span data-ttu-id="e9f10-117">相較于 Newtonsoft，預設 JsonSerializer 行為的差異</span><span class="sxs-lookup"><span data-stu-id="e9f10-117">Differences in default JsonSerializer behavior compared to Newtonsoft.Json</span></span>

<span data-ttu-id="e9f10-118"><xref:System.Text.Json> 預設為嚴格，並可避免代表呼叫端的任何猜測或解讀，強調決定性的行為。</span><span class="sxs-lookup"><span data-stu-id="e9f10-118"><xref:System.Text.Json> is strict by default and avoids any guessing or interpretation on the caller's behalf, emphasizing deterministic behavior.</span></span> <span data-ttu-id="e9f10-119">此程式庫是故意以這種方式設計來實現效能和安全性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-119">The library is intentionally designed this way for performance and security.</span></span> <span data-ttu-id="e9f10-120">`Newtonsoft.Json` 預設為彈性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-120">`Newtonsoft.Json` is flexible by default.</span></span> <span data-ttu-id="e9f10-121">這項設計的基本差異在於預設行為的下列許多特定差異背後。</span><span class="sxs-lookup"><span data-stu-id="e9f10-121">This fundamental difference in design is behind many of the following specific differences in default behavior.</span></span>

### <a name="case-insensitive-deserialization"></a><span data-ttu-id="e9f10-122">不區分大小寫的還原序列化</span><span class="sxs-lookup"><span data-stu-id="e9f10-122">Case-insensitive deserialization</span></span> 

<span data-ttu-id="e9f10-123">在還原序列化期間，`Newtonsoft.Json` 預設會執行不區分大小寫的屬性名稱比對。</span><span class="sxs-lookup"><span data-stu-id="e9f10-123">During deserialization, `Newtonsoft.Json` does case-insensitive property name matching by default.</span></span> <span data-ttu-id="e9f10-124"><xref:System.Text.Json> 預設值區分大小寫，這可提供較佳的效能，因為它會執行完全相符的作業。</span><span class="sxs-lookup"><span data-stu-id="e9f10-124">The <xref:System.Text.Json> default is case-sensitive, which gives better performance since it's doing an exact match.</span></span> <span data-ttu-id="e9f10-125">如需如何執行不區分大小寫比對的相關資訊，請參閱不[區分大小寫的屬性](system-text-json-how-to.md#case-insensitive-property-matching)比對。</span><span class="sxs-lookup"><span data-stu-id="e9f10-125">For information about how to do case-insensitive matching, see [Case-insensitive property matching](system-text-json-how-to.md#case-insensitive-property-matching).</span></span>

<span data-ttu-id="e9f10-126">如果您使用 ASP.NET Core 間接使用 `System.Text.Json`，就不需要採取任何動作來取得 `Newtonsoft.Json`之類的行為。</span><span class="sxs-lookup"><span data-stu-id="e9f10-126">If you're using `System.Text.Json` indirectly by using ASP.NET Core, you don't need to do anything to get behavior like `Newtonsoft.Json`.</span></span> <span data-ttu-id="e9f10-127">ASP.NET Core 指定使用 `System.Text.Json`時， [camel 大小寫屬性名稱](system-text-json-how-to.md#use-camel-case-for-all-json-property-names)和不區分大小寫比對的設定。</span><span class="sxs-lookup"><span data-stu-id="e9f10-127">ASP.NET Core specifies the settings for [camel-casing property names](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) and case-insensitive matching when it uses `System.Text.Json`.</span></span>

### <a name="comments"></a><span data-ttu-id="e9f10-128">註解</span><span class="sxs-lookup"><span data-stu-id="e9f10-128">Comments</span></span>

<span data-ttu-id="e9f10-129">在還原序列化期間，`Newtonsoft.Json` 預設會忽略 JSON 中的批註。</span><span class="sxs-lookup"><span data-stu-id="e9f10-129">During deserialization, `Newtonsoft.Json` ignores comments in the JSON by default.</span></span> <span data-ttu-id="e9f10-130"><xref:System.Text.Json> 預設為會擲回批註的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不會包含它們。</span><span class="sxs-lookup"><span data-stu-id="e9f10-130">The <xref:System.Text.Json> default is to throw exceptions for comments because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't include them.</span></span> <span data-ttu-id="e9f10-131">如需如何允許批註的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-131">For information about how to allow comments, see [Allow comments and trailing commas](system-text-json-how-to.md#allow-comments-and-trailing-commas).</span></span>

### <a name="trailing-commas"></a><span data-ttu-id="e9f10-132">尾端逗號</span><span class="sxs-lookup"><span data-stu-id="e9f10-132">Trailing commas</span></span>

<span data-ttu-id="e9f10-133">在還原序列化期間，`Newtonsoft.Json` 預設會忽略尾端的逗號。</span><span class="sxs-lookup"><span data-stu-id="e9f10-133">During deserialization, `Newtonsoft.Json` ignores trailing commas by default.</span></span> <span data-ttu-id="e9f10-134">它也會忽略多個尾端逗號（例如 `[{"Color":"Red"},{"Color":"Green"},,]`）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-134">It also ignores multiple trailing commas (for example, `[{"Color":"Red"},{"Color":"Green"},,]`).</span></span> <span data-ttu-id="e9f10-135"><xref:System.Text.Json> 預設值是擲回尾端逗號的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。</span><span class="sxs-lookup"><span data-stu-id="e9f10-135">The <xref:System.Text.Json> default is to throw exceptions for trailing commas because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't allow them.</span></span> <span data-ttu-id="e9f10-136">如需如何讓 `System.Text.Json` 接受它們的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-136">For information about how to make `System.Text.Json` accept them, see [Allow comments and trailing commas](system-text-json-how-to.md#allow-comments-and-trailing-commas).</span></span> <span data-ttu-id="e9f10-137">沒有任何方法可以允許多個尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="e9f10-137">There's no way to allow multiple trailing commas.</span></span>

### <a name="json-strings-property-names-and-string-values"></a><span data-ttu-id="e9f10-138">JSON 字串（屬性名稱和字串值）</span><span class="sxs-lookup"><span data-stu-id="e9f10-138">JSON strings (property names and string values)</span></span>

<span data-ttu-id="e9f10-139">在還原序列化期間，`Newtonsoft.Json` 接受以雙引號、單引號或不含引號括住的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e9f10-139">During deserialization, `Newtonsoft.Json` accepts property names surrounded by double quotes, single quotes, or without quotes.</span></span> <span data-ttu-id="e9f10-140">它接受以雙引號或單引號括住的字串值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-140">It accepts string values surrounded by double quotes or single quotes.</span></span> <span data-ttu-id="e9f10-141">例如，`Newtonsoft.Json` 接受下列 JSON：</span><span class="sxs-lookup"><span data-stu-id="e9f10-141">For example, `Newtonsoft.Json` accepts the following JSON:</span></span>

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

<span data-ttu-id="e9f10-142">`System.Text.Json` 只接受以雙引號括住的屬性名稱和字串值，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格需要該格式，而且是唯一視為有效 JSON 的格式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-142">`System.Text.Json` only accepts property names and string values in double quotes because that format is required by the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification and is the only format considered valid JSON.</span></span>

<span data-ttu-id="e9f10-143">以單引號括住的值會產生含有下列訊息的[JsonException](xref:System.Text.Json.JsonException) ：</span><span class="sxs-lookup"><span data-stu-id="e9f10-143">A value enclosed in single quotes results in a [JsonException](xref:System.Text.Json.JsonException) with the following message:</span></span>

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a><span data-ttu-id="e9f10-144">字串屬性的非字串值</span><span class="sxs-lookup"><span data-stu-id="e9f10-144">Non-string values for string properties</span></span>

<span data-ttu-id="e9f10-145">`Newtonsoft.Json` 接受非字串值，例如數位或常值 `true` 和 `false`，以還原序列化為 string 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-145">`Newtonsoft.Json` accepts non-string values, such as a number or the literals `true` and `false`, for deserialization to properties of type string.</span></span> <span data-ttu-id="e9f10-146">以下是 `Newtonsoft.Json` 成功還原序列化為下列類別的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="e9f10-146">Here's an example of JSON that `Newtonsoft.Json` successfully deserializes to the following class:</span></span>

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

<span data-ttu-id="e9f10-147">`System.Text.Json` 不會將非字串值還原序列化為字串屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-147">`System.Text.Json` doesn't deserialize non-string values into string properties.</span></span> <span data-ttu-id="e9f10-148">針對字串欄位接收的非字串值會導致[JsonException](xref:System.Text.Json.JsonException) ，並出現下列訊息：</span><span class="sxs-lookup"><span data-stu-id="e9f10-148">A non-string value received for a string field results in a [JsonException](xref:System.Text.Json.JsonException) with the following message:</span></span>

```
The JSON value could not be converted to System.String.
```

### <a name="converter-registration-precedence"></a><span data-ttu-id="e9f10-149">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="e9f10-149">Converter registration precedence</span></span>

<span data-ttu-id="e9f10-150">自訂轉換器的 `Newtonsoft.Json` 註冊優先順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9f10-150">The `Newtonsoft.Json` registration precedence for custom converters is as follows:</span></span>

* <span data-ttu-id="e9f10-151">屬性上的屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-151">Attribute on property</span></span>
* <span data-ttu-id="e9f10-152">類型上的屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-152">Attribute on type</span></span>
* <span data-ttu-id="e9f10-153">[轉換器](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)集合</span><span class="sxs-lookup"><span data-stu-id="e9f10-153">[Converters](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) collection</span></span>

<span data-ttu-id="e9f10-154">此順序表示 `Converters` 集合中的自訂轉換器會由在類型層級套用屬性所註冊的轉換器覆寫。</span><span class="sxs-lookup"><span data-stu-id="e9f10-154">This order means that a custom converter in the `Converters` collection is overridden by a converter that is registered by applying an attribute at the type level.</span></span> <span data-ttu-id="e9f10-155">這兩種註冊都是由屬性層級的屬性所覆寫。</span><span class="sxs-lookup"><span data-stu-id="e9f10-155">Both of those registrations are overridden by an attribute at the property level.</span></span>

<span data-ttu-id="e9f10-156">自訂轉換器的 <xref:System.Text.Json> 註冊優先順序不同：</span><span class="sxs-lookup"><span data-stu-id="e9f10-156">The <xref:System.Text.Json> registration precedence for custom converters is different:</span></span>

* <span data-ttu-id="e9f10-157">屬性上的屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-157">Attribute on property</span></span>
* <span data-ttu-id="e9f10-158"><xref:System.Text.Json.JsonSerializerOptions.Converters> 集合</span><span class="sxs-lookup"><span data-stu-id="e9f10-158"><xref:System.Text.Json.JsonSerializerOptions.Converters> collection</span></span>
* <span data-ttu-id="e9f10-159">類型上的屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-159">Attribute on type</span></span>

<span data-ttu-id="e9f10-160">此處的差異在於，`Converters` 集合中的自訂轉換器會覆寫類型層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-160">The difference here is that a custom converter in the `Converters` collection overrides an attribute at the type level.</span></span> <span data-ttu-id="e9f10-161">此優先順序的目的是要讓執行時間變更覆寫設計階段的選擇。</span><span class="sxs-lookup"><span data-stu-id="e9f10-161">The intention behind this order of precedence is to make run-time changes override design-time choices.</span></span> <span data-ttu-id="e9f10-162">沒有任何方法可以變更優先順序。</span><span class="sxs-lookup"><span data-stu-id="e9f10-162">There's no way to change the precedence.</span></span>

<span data-ttu-id="e9f10-163">如需自訂轉換器註冊的詳細資訊，請參閱[註冊自訂轉換子](system-text-json-converters-how-to.md#register-a-custom-converter)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-163">For more information about custom converter registration, see [Register a custom converter](system-text-json-converters-how-to.md#register-a-custom-converter).</span></span>

### <a name="character-escaping"></a><span data-ttu-id="e9f10-164">字元轉義</span><span class="sxs-lookup"><span data-stu-id="e9f10-164">Character escaping</span></span>

<span data-ttu-id="e9f10-165">在序列化期間，`Newtonsoft.Json` 相對於讓字元通過，而不將它們進行轉義，是相當寬鬆的。</span><span class="sxs-lookup"><span data-stu-id="e9f10-165">During serialization, `Newtonsoft.Json` is relatively permissive about letting characters through without escaping them.</span></span> <span data-ttu-id="e9f10-166">也就是說，它不會將它們取代為 `\uxxxx`，其中 `xxxx` 是字元的程式碼點。</span><span class="sxs-lookup"><span data-stu-id="e9f10-166">That is, it doesn't replace them with `\uxxxx` where `xxxx` is the character's code point.</span></span> <span data-ttu-id="e9f10-167">它會在其中進行 escape，而是在字元之前發出 `\` （例如，`"` 變成 `\"`）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-167">Where it does escape them, it does so by emitting a `\` before the character (for example, `"` becomes `\"`).</span></span> <span data-ttu-id="e9f10-168"><xref:System.Text.Json> 預設會將更多字元加上轉義，以針對跨網站腳本（XSS）或資訊洩漏攻擊提供深度防禦保護，並使用六個字元的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="e9f10-168"><xref:System.Text.Json> escapes more characters by default to provide defense-in-depth protections against cross-site scripting (XSS) or information-disclosure attacks and does so by using the six-character sequence.</span></span> <span data-ttu-id="e9f10-169">`System.Text.Json` 預設會將所有非 ASCII 字元加上轉義，因此如果您在 `Newtonsoft.Json`中使用 `StringEscapeHandling.EscapeNonAscii`，就不需要執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="e9f10-169">`System.Text.Json` escapes all non-ASCII characters by default, so you don't need to do anything if you're using `StringEscapeHandling.EscapeNonAscii` in `Newtonsoft.Json`.</span></span> <span data-ttu-id="e9f10-170">根據預設，`System.Text.Json` 也會對 HTML 敏感字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="e9f10-170">`System.Text.Json` also escapes HTML-sensitive characters, by default.</span></span> <span data-ttu-id="e9f10-171">如需如何覆寫預設 `System.Text.Json` 行為的詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-171">For information about how to override the default `System.Text.Json` behavior, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="deserialization-of-object-properties"></a><span data-ttu-id="e9f10-172">物件屬性的還原序列化</span><span class="sxs-lookup"><span data-stu-id="e9f10-172">Deserialization of object properties</span></span>

<span data-ttu-id="e9f10-173">當 `Newtonsoft.Json` 還原序列化為 Poco 中的 `object` 屬性或類型 `Dictionary<string, object>`的字典中，它會：</span><span class="sxs-lookup"><span data-stu-id="e9f10-173">When `Newtonsoft.Json` deserializes to `object` properties in POCOs or in dictionaries of type `Dictionary<string, object>`, it:</span></span>

* <span data-ttu-id="e9f10-174">推斷 JSON 承載中基本值的類型（不是 `null`），並傳回儲存的 `string`、`long`、`double`、`boolean`或 `DateTime` 做為已封裝的物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-174">Infers the type of primitive values in the JSON payload (other than `null`) and returns the stored `string`, `long`, `double`, `boolean`, or `DateTime` as a boxed object.</span></span> <span data-ttu-id="e9f10-175">*基本值*是單一 json 值，例如 json 數位、字串、`true`、`false`或 `null`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-175">*Primitive values* are single JSON values such as a JSON number, string, `true`, `false`, or `null`.</span></span>
* <span data-ttu-id="e9f10-176">傳回 JSON 承載中複雜值的 `JObject` 或 `JArray`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-176">Returns a `JObject` or `JArray` for complex values in the JSON payload.</span></span> <span data-ttu-id="e9f10-177">*複雜值*是以括弧（`{}`）括住的 JSON 索引鍵/值組集合，或是以方括弧（`[]`）括住的值清單。</span><span class="sxs-lookup"><span data-stu-id="e9f10-177">*Complex values* are collections of JSON key-value pairs within braces (`{}`) or lists of values within brackets (`[]`).</span></span> <span data-ttu-id="e9f10-178">大括弧或括弧內的屬性和值可以有額外的屬性或值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-178">The properties and values within the braces or brackets can have additional properties or values.</span></span>
* <span data-ttu-id="e9f10-179">當裝載具有 `null` 的 JSON 常值時，會傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="e9f10-179">Returns a null reference when the payload has the `null` JSON literal.</span></span>

<span data-ttu-id="e9f10-180"><xref:System.Text.Json> 會在 `System.Object` 屬性或字典值中，儲存基本和複雜值的已裝箱 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-180"><xref:System.Text.Json> stores a boxed `JsonElement` for both primitive and complex values within the `System.Object` property or dictionary value.</span></span> <span data-ttu-id="e9f10-181">不過，它會將 `null` 視為 `Newtonsoft.Json`，並在裝載具有 `null` 的 JSON 常值時傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="e9f10-181">However, it treats `null` the same as `Newtonsoft.Json` and returns a null reference when the payload has the `null` JSON literal in it.</span></span>

<span data-ttu-id="e9f10-182">若要執行 `object` 屬性的型別推斷，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-182">To implement type inference for `object` properties, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).</span></span>

### <a name="maximum-depth"></a><span data-ttu-id="e9f10-183">最大深度</span><span class="sxs-lookup"><span data-stu-id="e9f10-183">Maximum depth</span></span>

<span data-ttu-id="e9f10-184">`Newtonsoft.Json` 預設不具有最大深度限制。</span><span class="sxs-lookup"><span data-stu-id="e9f10-184">`Newtonsoft.Json` doesn't have a maximum depth limit by default.</span></span> <span data-ttu-id="e9f10-185">針對 <xref:System.Text.Json>，預設限制為64，且可透過設定 <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>加以設定。</span><span class="sxs-lookup"><span data-stu-id="e9f10-185">For <xref:System.Text.Json> there's a default limit  of 64, and it's configurable by setting <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.</span></span>

### <a name="omit-null-value-properties"></a><span data-ttu-id="e9f10-186">省略 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-186">Omit null-value properties</span></span>

<span data-ttu-id="e9f10-187">`Newtonsoft.Json` 有一個全域設定，會導致從序列化中排除 null 值屬性： [NullValueHandling。 Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-187">`Newtonsoft.Json` has a global setting that causes null-value properties to be excluded from serialization: [NullValueHandling.Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm).</span></span> <span data-ttu-id="e9f10-188"><xref:System.Text.Json> 中的對應選項是 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-188">The corresponding option in <xref:System.Text.Json> is <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>.</span></span>

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a><span data-ttu-id="e9f10-189">使用需要因應措施之 JsonSerializer 的案例</span><span class="sxs-lookup"><span data-stu-id="e9f10-189">Scenarios using JsonSerializer that require workarounds</span></span>

<span data-ttu-id="e9f10-190">內建功能不支援下列案例，但會針對因應措施提供範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9f10-190">The following scenarios aren't supported by built-in functionality, but sample code is provided for workarounds.</span></span> <span data-ttu-id="e9f10-191">大部分的因應措施需要您執行[自訂的轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-191">Most of the workarounds require that you implement [custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="specify-date-format"></a><span data-ttu-id="e9f10-192">指定日期格式</span><span class="sxs-lookup"><span data-stu-id="e9f10-192">Specify date format</span></span>

<span data-ttu-id="e9f10-193">`Newtonsoft.Json` 提供數種方式來控制 `DateTime` 和 `DateTimeOffset` 類型的屬性如何序列化和還原序列化：</span><span class="sxs-lookup"><span data-stu-id="e9f10-193">`Newtonsoft.Json` provides several ways to control how properties of `DateTime` and `DateTimeOffset` types are serialized and deserialized:</span></span>

* <span data-ttu-id="e9f10-194">`DateTimeZoneHandling` 設定可以用來將所有 `DateTime` 值序列化為 UTC 日期。</span><span class="sxs-lookup"><span data-stu-id="e9f10-194">The `DateTimeZoneHandling` setting can be used to serialize all `DateTime` values as UTC dates.</span></span>
* <span data-ttu-id="e9f10-195">`DateFormatString` 設定和 `DateTime` 轉換器可以用來自訂日期字串的格式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-195">The `DateFormatString` setting and `DateTime` converters can be used to customize the format of date strings.</span></span>

<span data-ttu-id="e9f10-196">在 <xref:System.Text.Json>中，具有內建支援的唯一格式是 ISO 8601-1:2019，因為它廣泛採用、明確，並會精確地進行往返。</span><span class="sxs-lookup"><span data-stu-id="e9f10-196">In <xref:System.Text.Json>, the only format that has built-in support is ISO 8601-1:2019 since it's widely adopted, unambiguous, and makes round trips precisely.</span></span> <span data-ttu-id="e9f10-197">若要使用任何其他格式，請建立自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-197">To use any other format, create a custom converter.</span></span> <span data-ttu-id="e9f10-198">如需詳細資訊，請參閱[system.object 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-198">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>

### <a name="quoted-numbers"></a><span data-ttu-id="e9f10-199">加上引號的數位</span><span class="sxs-lookup"><span data-stu-id="e9f10-199">Quoted numbers</span></span>

<span data-ttu-id="e9f10-200">`Newtonsoft.Json` 可以序列化或還原序列化 JSON 字串所代表的數位（以引號括住）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-200">`Newtonsoft.Json` can serialize or deserialize numbers represented by JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="e9f10-201">例如，它可以接受： `{"DegreesCelsius":"23"}`，而不是 `{"DegreesCelsius":23}`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-201">For example, it can accept: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="e9f10-202">若要在 <xref:System.Text.Json>中啟用該行為，請執行如下列範例所示的自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-202">To enable that behavior in <xref:System.Text.Json>, implement a custom converter like the following example.</span></span> <span data-ttu-id="e9f10-203">轉換器會處理定義為 `long`的屬性：</span><span class="sxs-lookup"><span data-stu-id="e9f10-203">The converter handles properties defined as `long`:</span></span>

* <span data-ttu-id="e9f10-204">它會將它們序列化為 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="e9f10-204">It serializes them as JSON strings.</span></span> 
* <span data-ttu-id="e9f10-205">它會在還原序列化時，接受引號內的 JSON 數位和數位。</span><span class="sxs-lookup"><span data-stu-id="e9f10-205">It accepts JSON numbers and numbers within quotes while deserializing.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

<span data-ttu-id="e9f10-206">使用個別 `long` 屬性上的[屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-206">Register this custom converter by [using an attribute](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) on individual `long` properties or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

### <a name="dictionary-with-non-string-key"></a><span data-ttu-id="e9f10-207">具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="e9f10-207">Dictionary with non-string key</span></span>

<span data-ttu-id="e9f10-208">`Newtonsoft.Json` 支援 `Dictionary<TKey, TValue>`類型的集合。</span><span class="sxs-lookup"><span data-stu-id="e9f10-208">`Newtonsoft.Json` supports collections of type `Dictionary<TKey, TValue>`.</span></span> <span data-ttu-id="e9f10-209"><xref:System.Text.Json> 中的字典集合內建支援僅限於 `Dictionary<string, TValue>`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-209">The built-in support for dictionary collections in <xref:System.Text.Json> is limited to `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="e9f10-210">也就是，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="e9f10-210">That is, the key must be a string.</span></span>

<span data-ttu-id="e9f10-211">若要支援具有整數或其他類型做為索引鍵的字典，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-211">To support a dictionary with an integer or some other type as the key, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).</span></span>

### <a name="polymorphic-serialization"></a><span data-ttu-id="e9f10-212">多型序列化</span><span class="sxs-lookup"><span data-stu-id="e9f10-212">Polymorphic serialization</span></span>

<span data-ttu-id="e9f10-213">`Newtonsoft.Json` 會自動進行多型序列化。</span><span class="sxs-lookup"><span data-stu-id="e9f10-213">`Newtonsoft.Json` automatically does polymorphic serialization.</span></span> <span data-ttu-id="e9f10-214">如需 <xref:System.Text.Json>的有限多型序列化功能的相關資訊，請參閱[序列化衍生類別的屬性](system-text-json-how-to.md#serialize-properties-of-derived-classes)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-214">For information about the limited polymorphic serialization capabilities of <xref:System.Text.Json>, see [Serialize properties of derived classes](system-text-json-how-to.md#serialize-properties-of-derived-classes).</span></span>

<span data-ttu-id="e9f10-215">此處所述的因應措施，是定義可能包含衍生類別的屬性，做為 `object`的型別。</span><span class="sxs-lookup"><span data-stu-id="e9f10-215">The workaround described there is to define properties that may contain derived classes as type `object`.</span></span> <span data-ttu-id="e9f10-216">如果無法這樣做，另一個選項是使用整個繼承類型階層的 `Write` 方法建立轉換器，如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="e9f10-216">If that isn't possible, another option is to create a converter with a `Write` method for the whole inheritance type hierarchy like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

### <a name="polymorphic-deserialization"></a><span data-ttu-id="e9f10-217">多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="e9f10-217">Polymorphic deserialization</span></span>

<span data-ttu-id="e9f10-218">`Newtonsoft.Json` 具有 `TypeNameHandling` 設定，會在序列化時將類型名稱中繼資料新增至 JSON。</span><span class="sxs-lookup"><span data-stu-id="e9f10-218">`Newtonsoft.Json` has a `TypeNameHandling` setting that adds type name metadata to the JSON while serializing.</span></span> <span data-ttu-id="e9f10-219">它會在還原序列化時使用中繼資料來執行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="e9f10-219">It uses the metadata while deserializing to do polymorphic deserialization.</span></span> <span data-ttu-id="e9f10-220"><xref:System.Text.Json> 可以執行有限範圍的多型序列化，但不能進行多型的還原[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-220"><xref:System.Text.Json> can do a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but not polymorphic deserialization.</span></span>

<span data-ttu-id="e9f10-221">若要支援多型還原序列化，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-221">To support polymorphic deserialization, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

### <a name="required-properties"></a><span data-ttu-id="e9f10-222">必要屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-222">Required properties</span></span>

<span data-ttu-id="e9f10-223">在還原序列化期間，如果目標型別的其中一個屬性未在 JSON 中收到任何值，則 <xref:System.Text.Json> 不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-223">During deserialization, <xref:System.Text.Json> doesn't throw an exception if no value is received in the JSON for one of the properties of the target type.</span></span> <span data-ttu-id="e9f10-224">例如，如果您有 `WeatherForecast` 類別：</span><span class="sxs-lookup"><span data-stu-id="e9f10-224">For example, if you have a `WeatherForecast` class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="e9f10-225">下列 JSON 會進行還原序列化，而不會發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="e9f10-225">The following JSON is deserialized without error:</span></span>

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

<span data-ttu-id="e9f10-226">若要讓還原序列化失敗，如果 JSON 中沒有 `Date` 的屬性，請執行自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-226">To make deserialization fail if no `Date` property is in the JSON, implement a custom converter.</span></span> <span data-ttu-id="e9f10-227">如果在還原序列化完成後未設定 `Date` 屬性，下列範例轉換器程式碼會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e9f10-227">The following sample converter code throws an exception if the `Date` property isn't set after deserialization is complete:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

<span data-ttu-id="e9f10-228">藉由[使用 POCO 類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-228">Register this custom converter by [using an attribute on the POCO class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="e9f10-229">如果您遵循此模式，請不要在以遞迴方式呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 或 <xref:System.Text.Json.JsonSerializer.Deserialize%2A>時傳入 options 物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-229">If you follow this pattern, don't pass in the options object when recursively calling <xref:System.Text.Json.JsonSerializer.Serialize%2A> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A>.</span></span> <span data-ttu-id="e9f10-230">Options 物件包含 <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="e9f10-230">The options object contains the <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> collection.</span></span> <span data-ttu-id="e9f10-231">如果您將它傳遞給 `Serialize` 或 `Deserialize`，則自訂轉換器會呼叫自己的，因此會產生無限迴圈，導致堆疊溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-231">If you pass it in to `Serialize` or `Deserialize`, the custom converter calls into itself, making an infinite loop that results in a stack overflow exception.</span></span> <span data-ttu-id="e9f10-232">如果預設選項不可行，請使用您所需的設定來建立選項的新實例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-232">If the default options are not feasible, create a new instance of the options with the settings that you need.</span></span> <span data-ttu-id="e9f10-233">這個方法將會變慢，因為每個新的實例會獨立快取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-233">This approach will be slow since each new instance caches independently.</span></span>

<span data-ttu-id="e9f10-234">上述的轉換器程式碼是簡化的範例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-234">The preceding converter code is a simplified example.</span></span> <span data-ttu-id="e9f10-235">如果您需要處理屬性（例如[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)或不同的選項（例如自訂編碼器），則需要額外的邏輯。</span><span class="sxs-lookup"><span data-stu-id="e9f10-235">Additional logic would be required if you need to handle attributes (such as [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) or different options (such as custom encoders).</span></span> <span data-ttu-id="e9f10-236">此外，範例程式碼不會處理在此函式中設定預設值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-236">Also, the example code doesn't handle properties for which a default value is set in the constructor.</span></span> <span data-ttu-id="e9f10-237">而這種方法不會區分下列案例：</span><span class="sxs-lookup"><span data-stu-id="e9f10-237">And this approach doesn't differentiate between the following scenarios:</span></span>

* <span data-ttu-id="e9f10-238">JSON 中遺漏了屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-238">A property is missing from the JSON.</span></span>
* <span data-ttu-id="e9f10-239">JSON 中有不可為 null 類型的屬性，但此值是類型的預設值，例如零代表 `int`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-239">A property for a non-nullable type is present in the JSON, but the value is the default for the type, such as zero for an `int`.</span></span>
* <span data-ttu-id="e9f10-240">JSON 中有可為 null 類型的屬性，但值為 null。</span><span class="sxs-lookup"><span data-stu-id="e9f10-240">A property for a nullable type is present in the JSON, but the value is null.</span></span>

### <a name="deserialize-null-to-non-nullable-type"></a><span data-ttu-id="e9f10-241">將 null 還原序列化為不可為 null 的類型</span><span class="sxs-lookup"><span data-stu-id="e9f10-241">Deserialize null to non-nullable type</span></span> 

<span data-ttu-id="e9f10-242">`Newtonsoft.Json` 在下列案例中不會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e9f10-242">`Newtonsoft.Json` doesn't throw an exception in the following scenario:</span></span>

* <span data-ttu-id="e9f10-243">`NullValueHandling` 設定為 `Ignore`，而</span><span class="sxs-lookup"><span data-stu-id="e9f10-243">`NullValueHandling` is set to `Ignore`, and</span></span>
* <span data-ttu-id="e9f10-244">在還原序列化期間，JSON 會針對不可為 null 的型別包含 null 值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-244">During deserialization, the JSON contains a null value for a non-nullable type.</span></span>

<span data-ttu-id="e9f10-245">在相同的案例中，<xref:System.Text.Json> 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-245">In the same scenario, <xref:System.Text.Json> does throw an exception.</span></span> <span data-ttu-id="e9f10-246">（對應的 null 處理設定為 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-246">(The corresponding null handling setting is <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)</span></span>

<span data-ttu-id="e9f10-247">如果您擁有目標型別，最佳的解決方法是讓屬性成為可為 null （例如，將 `int` 變更為 `int?`）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-247">If you own the target type, the best workaround is to make the property in question nullable (for example, change `int` to `int?`).</span></span>

<span data-ttu-id="e9f10-248">另一個因應措施是建立類型的轉換器，例如下列範例，其會處理 `DateTimeOffset` 類型的 null 值：</span><span class="sxs-lookup"><span data-stu-id="e9f10-248">Another workaround is to make a converter for the type, such as the following example that handles null values for `DateTimeOffset` types:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

<span data-ttu-id="e9f10-249">藉由[使用屬性上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-249">Register this custom converter by [using an attribute on the property](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="e9f10-250">**注意：** 前面的轉換子**處理 null 值的方式**，與指定預設值的 poco 不同 `Newtonsoft.Json`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-250">**Note:** The preceding converter **handles null values differently** than `Newtonsoft.Json` does for POCOs that specify default values.</span></span> <span data-ttu-id="e9f10-251">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="e9f10-251">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="e9f10-252">而且假設下列 JSON 會使用上述的轉換器還原序列化：</span><span class="sxs-lookup"><span data-stu-id="e9f10-252">And suppose the following JSON is deserialized by using the preceding converter:</span></span>

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="e9f10-253">還原序列化之後，`Date` 屬性具有1/1/0001 （`default(DateTimeOffset)`），也就是會覆寫在此函式中設定的值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-253">After deserialization, the `Date` property has 1/1/0001 (`default(DateTimeOffset)`), that is, the value set in the constructor is overwritten.</span></span> <span data-ttu-id="e9f10-254">假設有相同的 POCO 和 JSON，`Newtonsoft.Json` 還原序列化會在 `Date` 屬性中留下1/1/2001。</span><span class="sxs-lookup"><span data-stu-id="e9f10-254">Given the same POCO and JSON, `Newtonsoft.Json` deserialization would leave 1/1/2001 in the `Date` property.</span></span>

### <a name="deserialize-to-immutable-classes-and-structs"></a><span data-ttu-id="e9f10-255">還原序列化為不可變的類別和結構</span><span class="sxs-lookup"><span data-stu-id="e9f10-255">Deserialize to immutable classes and structs</span></span>

<span data-ttu-id="e9f10-256">`Newtonsoft.Json` 可以還原序列化為不可變的類別和結構，因為它可以使用具有參數的函數。</span><span class="sxs-lookup"><span data-stu-id="e9f10-256">`Newtonsoft.Json` can deserialize to immutable classes and structs because it can use constructors that have parameters.</span></span> <span data-ttu-id="e9f10-257"><xref:System.Text.Json> 僅支援公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-257"><xref:System.Text.Json> supports only public parameterless constructors.</span></span> <span data-ttu-id="e9f10-258">因應措施是，您可以在自訂轉換子中呼叫具有參數的函式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-258">As a workaround, you can call a constructor with parameters in a custom converter.</span></span>

<span data-ttu-id="e9f10-259">以下是具有多個函數參數的不可變結構：</span><span class="sxs-lookup"><span data-stu-id="e9f10-259">Here's an immutable struct with multiple constructor parameters:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

<span data-ttu-id="e9f10-260">以下是將此結構序列化和還原序列化的轉換器：</span><span class="sxs-lookup"><span data-stu-id="e9f10-260">And here's a converter that serializes and deserializes this struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

<span data-ttu-id="e9f10-261">[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-261">Register this custom converter by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="e9f10-262">如需處理開放式泛型屬性之類似轉換器的範例，請參閱索引[鍵/值組的內建轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-262">For an example of a similar converter that handles open generic properties, see the [built-in converter for key-value pairs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).</span></span>

### <a name="specify-constructor-to-use"></a><span data-ttu-id="e9f10-263">指定要使用的構造函式</span><span class="sxs-lookup"><span data-stu-id="e9f10-263">Specify constructor to use</span></span>

<span data-ttu-id="e9f10-264">`Newtonsoft.Json` `[JsonConstructor]` 屬性可讓您指定在還原序列化為 POCO 時要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-264">The `Newtonsoft.Json` `[JsonConstructor]` attribute lets you specify which constructor to call when deserializing to a POCO.</span></span> <span data-ttu-id="e9f10-265"><xref:System.Text.Json> 僅支援無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-265"><xref:System.Text.Json> supports only parameterless constructors.</span></span> <span data-ttu-id="e9f10-266">因應措施是，您可以在自訂轉換器中呼叫所需的任何一個方法。</span><span class="sxs-lookup"><span data-stu-id="e9f10-266">As a workaround, you can call whichever constructor you need in a custom converter.</span></span> <span data-ttu-id="e9f10-267">請參閱還原序列化[為不可變類別和結構](#deserialize-to-immutable-classes-and-structs)的範例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-267">See the example for [Deserialize to immutable classes and structs](#deserialize-to-immutable-classes-and-structs).</span></span>

### <a name="conditionally-ignore-a-property"></a><span data-ttu-id="e9f10-268">有條件地忽略屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-268">Conditionally ignore a property</span></span>

<span data-ttu-id="e9f10-269">`Newtonsoft.Json` 有數種方式可以有條件地忽略序列化或還原序列化上的屬性：</span><span class="sxs-lookup"><span data-stu-id="e9f10-269">`Newtonsoft.Json` has several ways to conditionally ignore a property on serialization or deserialization:</span></span>

* <span data-ttu-id="e9f10-270">`DefaultContractResolver` 可讓您根據任意條件，選取要包含或排除的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-270">`DefaultContractResolver` lets you select properties to include or exclude, based on arbitrary criteria.</span></span> 
* <span data-ttu-id="e9f10-271">`JsonSerializerSettings` 上的 `NullValueHandling` 和 `DefaultValueHandling` 設定，可讓您指定應該忽略所有的 null 值或預設值屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-271">The `NullValueHandling` and `DefaultValueHandling` settings on `JsonSerializerSettings` let you specify that all null-value or default-value properties should be ignored.</span></span>
* <span data-ttu-id="e9f10-272">[`[JsonProperty]`] 屬性上的 [`NullValueHandling`] 和 [`DefaultValueHandling`] 設定可讓您指定在設定為 null 或預設值時，應該忽略的個別屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-272">The `NullValueHandling` and `DefaultValueHandling` settings on the `[JsonProperty]` attribute let you specify individual properties that should be ignored when set to null or the default value.</span></span>

<span data-ttu-id="e9f10-273"><xref:System.Text.Json> 提供下列方法來在序列化時省略屬性：</span><span class="sxs-lookup"><span data-stu-id="e9f10-273"><xref:System.Text.Json> provides the following ways to omit properties while serializing:</span></span>

* <span data-ttu-id="e9f10-274">屬性[（property）上的 [JsonIgnore] 屬性（attribute）](system-text-json-how-to.md#exclude-individual-properties)會在序列化期間，從 JSON 中省略屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-274">The [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) attribute on a property causes the property to be omitted from the JSON during serialization.</span></span>
* <span data-ttu-id="e9f10-275">[IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global 選項可讓您排除所有 null 值屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-275">The [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global option lets you exclude all null-value properties.</span></span>
* <span data-ttu-id="e9f10-276">[IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global 選項可讓您排除所有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-276">The [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global option lets you exclude all read-only properties.</span></span>

<span data-ttu-id="e9f10-277">這些選項**不**會讓您：</span><span class="sxs-lookup"><span data-stu-id="e9f10-277">These options **don't** let you:</span></span>

* <span data-ttu-id="e9f10-278">忽略所有具有類型之預設值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-278">Ignore all properties that have the default value for the type.</span></span>
* <span data-ttu-id="e9f10-279">忽略具有類型之預設值的選取屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-279">Ignore selected properties that have the default value for the type.</span></span>
* <span data-ttu-id="e9f10-280">如果其值為 null，則忽略選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-280">Ignore selected properties if their value is null.</span></span>
* <span data-ttu-id="e9f10-281">根據在執行時間評估的任意準則，忽略選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-281">Ignore selected properties based on arbitrary criteria evaluated at run time.</span></span> 

<span data-ttu-id="e9f10-282">針對該功能，您可以撰寫自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-282">For that functionality, you can write a custom converter.</span></span> <span data-ttu-id="e9f10-283">以下是範例 POCO 和適用于它的自訂轉換器，其說明此方法：</span><span class="sxs-lookup"><span data-stu-id="e9f10-283">Here's a sample POCO and a custom converter for it that illustrates this approach:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

<span data-ttu-id="e9f10-284">如果參數的值為 null、空字串或 "N/A"，則轉換器會從序列化中省略 `Summary` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-284">The converter causes the `Summary` property to be omitted from serialization if its value is null, an empty string, or "N/A".</span></span> 

<span data-ttu-id="e9f10-285">藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-285">Register this custom converter by [using an attribute on the class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="e9f10-286">這種方法需要額外的邏輯，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9f10-286">This approach requires additional logic if:</span></span>

* <span data-ttu-id="e9f10-287">POCO 包含複雜的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-287">The POCO includes complex properties.</span></span>
* <span data-ttu-id="e9f10-288">您需要處理諸如 `[JsonIgnore]` 或選項（例如自訂編碼器）之類的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-288">You need to handle attributes such as `[JsonIgnore]` or options such as custom encoders.</span></span>

### <a name="callbacks"></a><span data-ttu-id="e9f10-289">叫</span><span class="sxs-lookup"><span data-stu-id="e9f10-289">Callbacks</span></span>

<span data-ttu-id="e9f10-290">`Newtonsoft.Json` 可讓您在序列化或還原序列化程式的數個點執行自訂程式碼：</span><span class="sxs-lookup"><span data-stu-id="e9f10-290">`Newtonsoft.Json` lets you execute custom code at several points in the serialization or deserialization process:</span></span>

* <span data-ttu-id="e9f10-291">OnDeserializing （開始還原序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="e9f10-291">OnDeserializing (when beginning to deserialize an object)</span></span>
* <span data-ttu-id="e9f10-292">OnDeserialized （完成還原序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="e9f10-292">OnDeserialized (when finished deserializing an object)</span></span>
* <span data-ttu-id="e9f10-293">OnSerializing （開始序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="e9f10-293">OnSerializing (when beginning to serialize an object)</span></span>
* <span data-ttu-id="e9f10-294">OnSerialized （完成序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="e9f10-294">OnSerialized (when finished serializing an object)</span></span>

<span data-ttu-id="e9f10-295">在 <xref:System.Text.Json>中，您可以藉由撰寫自訂的轉換器來模擬回呼。</span><span class="sxs-lookup"><span data-stu-id="e9f10-295">In <xref:System.Text.Json>, you can simulate callbacks by writing a custom converter.</span></span> <span data-ttu-id="e9f10-296">下列範例顯示 POCO 的自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-296">The following example shows a custom converter for a POCO.</span></span> <span data-ttu-id="e9f10-297">轉換器包含的程式碼會在每個對應至 `Newtonsoft.Json` 回呼的時間點顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="e9f10-297">The converter includes code that displays a message at each point that corresponds to a `Newtonsoft.Json` callback.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

<span data-ttu-id="e9f10-298">藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="e9f10-298">Register this custom converter by [using an attribute on the class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="e9f10-299">如果您使用遵循上述範例的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="e9f10-299">If you use a custom converter that follows the preceding sample:</span></span>

* <span data-ttu-id="e9f10-300">`OnDeserializing` 程式碼沒有新 POCO 實例的存取權。</span><span class="sxs-lookup"><span data-stu-id="e9f10-300">The `OnDeserializing` code doesn't have access to the new POCO instance.</span></span> <span data-ttu-id="e9f10-301">若要在還原序列化開始時操作新的 POCO 實例，請將該程式碼放在 POCO 函式中。</span><span class="sxs-lookup"><span data-stu-id="e9f10-301">To manipulate the new POCO instance at the start of deserialization, put that code in the POCO constructor.</span></span>
* <span data-ttu-id="e9f10-302">當以遞迴方式呼叫 `Serialize` 或 `Deserialize`時，請勿傳入 options 物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-302">Don't pass in the options object when recursively calling `Serialize` or `Deserialize`.</span></span> <span data-ttu-id="e9f10-303">Options 物件包含 `Converters` 集合。</span><span class="sxs-lookup"><span data-stu-id="e9f10-303">The options object contains the `Converters` collection.</span></span> <span data-ttu-id="e9f10-304">如果您將它傳遞給 `Serialize` 或 `Deserialize`，則會使用轉換器，並產生無限迴圈，而導致堆疊溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-304">If you pass it in to `Serialize` or `Deserialize`, the converter will be used, making an infinite loop that results in a stack overflow exception.</span></span>

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a><span data-ttu-id="e9f10-305">JsonSerializer 目前不支援的案例</span><span class="sxs-lookup"><span data-stu-id="e9f10-305">Scenarios that JsonSerializer currently doesn't support</span></span>

<span data-ttu-id="e9f10-306">因應措施適用于下列案例，但其中一些因應措施可能會相對較難實行。</span><span class="sxs-lookup"><span data-stu-id="e9f10-306">Workarounds are possible for the following scenarios, but some of them would be relatively difficult to implement.</span></span> <span data-ttu-id="e9f10-307">本文不會針對這些案例提供因應措施的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-307">This article doesn't provide code samples for workarounds for these scenarios.</span></span>

<span data-ttu-id="e9f10-308">這不是 `System.Text.Json`中沒有對等專案之 `Newtonsoft.Json` 功能的詳盡清單。</span><span class="sxs-lookup"><span data-stu-id="e9f10-308">This is not an exhaustive list of `Newtonsoft.Json` features that have no equivalents in `System.Text.Json`.</span></span> <span data-ttu-id="e9f10-309">此清單包含[GitHub 問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)或[StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json)文章中所要求的許多案例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-309">The list includes many of the scenarios that have been requested in [GitHub issues](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) or [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) posts.</span></span>

<span data-ttu-id="e9f10-310">如果您為上述其中一個案例實行因應措施，而且可以共用程式碼，請選取頁面底部的 [**此頁面**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9f10-310">If you implement a workaround for one of these scenarios and can share the code, select the "**This page**" button at the bottom of the page.</span></span> <span data-ttu-id="e9f10-311">這會建立 GitHub 問題，並將其新增至頁面底部所列的問題。</span><span class="sxs-lookup"><span data-stu-id="e9f10-311">That creates a GitHub issue and adds it to the issues that are listed at the bottom of the page.</span></span>

### <a name="types-without-built-in-support"></a><span data-ttu-id="e9f10-312">沒有內建支援的類型</span><span class="sxs-lookup"><span data-stu-id="e9f10-312">Types without built-in support</span></span>

<span data-ttu-id="e9f10-313"><xref:System.Text.Json> 不會提供下列類型的內建支援：</span><span class="sxs-lookup"><span data-stu-id="e9f10-313"><xref:System.Text.Json> doesn't provide built-in support for the following types:</span></span>

* <span data-ttu-id="e9f10-314"><xref:System.Data.DataTable> 和相關類型</span><span class="sxs-lookup"><span data-stu-id="e9f10-314"><xref:System.Data.DataTable> and related types</span></span>
* <span data-ttu-id="e9f10-315">F#類型，例如[區分](../../fsharp/language-reference/discriminated-unions.md)等位、[記錄類型](../../fsharp/language-reference/records.md)和[匿名記錄類型](../../fsharp/language-reference/anonymous-records.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-315">F# types, such as [discriminated unions](../../fsharp/language-reference/discriminated-unions.md), [record types](../../fsharp/language-reference/records.md), and [anonymous record types](../../fsharp/language-reference/anonymous-records.md).</span></span>
* <span data-ttu-id="e9f10-316"><xref:System.Collections.Specialized> 命名空間中的集合類型</span><span class="sxs-lookup"><span data-stu-id="e9f10-316">Collection types in the <xref:System.Collections.Specialized> namespace</span></span>
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <span data-ttu-id="e9f10-317"><xref:System.ValueTuple> 和其相關聯的泛型型別</span><span class="sxs-lookup"><span data-stu-id="e9f10-317"><xref:System.ValueTuple> and its associated generic types</span></span>

<span data-ttu-id="e9f10-318">針對沒有內建支援的類型，可以實作為自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-318">Custom converters can be implemented for types that don't have built-in support.</span></span>

### <a name="public-and-non-public-fields"></a><span data-ttu-id="e9f10-319">公用和非公用欄位</span><span class="sxs-lookup"><span data-stu-id="e9f10-319">Public and non-public fields</span></span>

<span data-ttu-id="e9f10-320">`Newtonsoft.Json` 可以序列化和還原序列化欄位，以及屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-320">`Newtonsoft.Json` can serialize and deserialize fields as well as properties.</span></span> <span data-ttu-id="e9f10-321"><xref:System.Text.Json> 僅適用于公用屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-321"><xref:System.Text.Json> only works with public properties.</span></span> <span data-ttu-id="e9f10-322">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="e9f10-322">Custom converters can provide this functionality.</span></span>

### <a name="internal-and-private-property-setters-and-getters"></a><span data-ttu-id="e9f10-323">內部和私用屬性 setter 和 getter</span><span class="sxs-lookup"><span data-stu-id="e9f10-323">Internal and private property setters and getters</span></span>

<span data-ttu-id="e9f10-324">`Newtonsoft.Json` 可以透過 `JsonProperty` 屬性來使用私用和內部屬性 setter 和 getter。</span><span class="sxs-lookup"><span data-stu-id="e9f10-324">`Newtonsoft.Json` can use private and internal property setters and getters via the `JsonProperty` attribute.</span></span> <span data-ttu-id="e9f10-325"><xref:System.Text.Json> 僅支援公用 setter。</span><span class="sxs-lookup"><span data-stu-id="e9f10-325"><xref:System.Text.Json> supports only public setters.</span></span> <span data-ttu-id="e9f10-326">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="e9f10-326">Custom converters can provide this functionality.</span></span>

### <a name="preserve-object-references-and-handle-loops"></a><span data-ttu-id="e9f10-327">保留物件參考並處理迴圈</span><span class="sxs-lookup"><span data-stu-id="e9f10-327">Preserve object references and handle loops</span></span>

<span data-ttu-id="e9f10-328">根據預設，`Newtonsoft.Json` 依值序列化。</span><span class="sxs-lookup"><span data-stu-id="e9f10-328">By default, `Newtonsoft.Json` serializes by value.</span></span> <span data-ttu-id="e9f10-329">例如，如果物件包含兩個屬性，其中包含相同 `Person` 物件的參考，則該 `Person` 物件屬性的值會在 JSON 中重複。</span><span class="sxs-lookup"><span data-stu-id="e9f10-329">For example, if an object contains two properties that contain a reference to the same `Person` object, the values of that `Person` object's properties are duplicated in the JSON.</span></span>

<span data-ttu-id="e9f10-330">`Newtonsoft.Json` 在 `JsonSerializerSettings` 上有 `PreserveReferencesHandling` 設定，可讓您以傳址方式序列化：</span><span class="sxs-lookup"><span data-stu-id="e9f10-330">`Newtonsoft.Json` has a `PreserveReferencesHandling` setting on `JsonSerializerSettings` that lets you serialize by reference:</span></span>

* <span data-ttu-id="e9f10-331">識別碼中繼資料會加入至針對第一個 `Person` 物件所建立的 JSON。</span><span class="sxs-lookup"><span data-stu-id="e9f10-331">An identifier metadata is added to the JSON created for the first `Person` object.</span></span>
* <span data-ttu-id="e9f10-332">針對第二個 `Person` 物件所建立的 JSON 包含該識別碼的參考，而不是屬性值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-332">The JSON that is created for the second `Person` object contains a reference to that identifier instead of property values.</span></span>

<span data-ttu-id="e9f10-333">`Newtonsoft.Json` 也有 `ReferenceLoopHandling` 設定，可讓您忽略迴圈參考，而不是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-333">`Newtonsoft.Json` also has a `ReferenceLoopHandling` setting that lets you ignore circular references rather than throw an exception.</span></span>

<span data-ttu-id="e9f10-334"><xref:System.Text.Json> 只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-334"><xref:System.Text.Json> only supports serialization by value and throws an exception for circular references.</span></span>

### <a name="systemruntimeserialization-attributes"></a><span data-ttu-id="e9f10-335">System.object。序列化屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-335">System.Runtime.Serialization attributes</span></span>

<span data-ttu-id="e9f10-336"><xref:System.Text.Json> 不支援來自 `System.Runtime.Serialization` 命名空間的屬性，例如 `DataMemberAttribute` 和 `IgnoreDataMemberAttribute`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-336"><xref:System.Text.Json> doesn't support attributes from the `System.Runtime.Serialization` namespace, such as `DataMemberAttribute` and `IgnoreDataMemberAttribute`.</span></span>

### <a name="octal-numbers"></a><span data-ttu-id="e9f10-337">八進位數位</span><span class="sxs-lookup"><span data-stu-id="e9f10-337">Octal numbers</span></span>

<span data-ttu-id="e9f10-338">`Newtonsoft.Json` 會將前置零的數位視為八進位數位。</span><span class="sxs-lookup"><span data-stu-id="e9f10-338">`Newtonsoft.Json` treats numbers with a leading zero as octal numbers.</span></span> <span data-ttu-id="e9f10-339"><xref:System.Text.Json> 不允許前置零，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。</span><span class="sxs-lookup"><span data-stu-id="e9f10-339"><xref:System.Text.Json> doesn't allow leading zeroes because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't allow them.</span></span>

### <a name="populate-existing-objects"></a><span data-ttu-id="e9f10-340">填入現有的物件</span><span class="sxs-lookup"><span data-stu-id="e9f10-340">Populate existing objects</span></span>

<span data-ttu-id="e9f10-341">中的 `JsonConvert.PopulateObject` 方法 `Newtonsoft.Json` 將 JSON 檔案還原序列化為類別的現有實例，而不是建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-341">The `JsonConvert.PopulateObject` method in `Newtonsoft.Json` deserializes a JSON document to an existing instance of a class, instead of creating a new instance.</span></span> <span data-ttu-id="e9f10-342"><xref:System.Text.Json> 一律會使用預設的公用無參數函式來建立目標型別的新實例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-342"><xref:System.Text.Json> always creates a new instance of the target type by using the default public parameterless constructor.</span></span> <span data-ttu-id="e9f10-343">自訂轉換器可以還原序列化為現有的實例。</span><span class="sxs-lookup"><span data-stu-id="e9f10-343">Custom converters can deserialize to an existing instance.</span></span>

### <a name="reuse-rather-than-replace-properties"></a><span data-ttu-id="e9f10-344">重複使用，而不是取代屬性</span><span class="sxs-lookup"><span data-stu-id="e9f10-344">Reuse rather than replace properties</span></span>

<span data-ttu-id="e9f10-345">[`Newtonsoft.Json` `ObjectCreationHandling`] 設定可讓您指定應該重複使用屬性中的物件，而不是在還原序列化期間加以取代。</span><span class="sxs-lookup"><span data-stu-id="e9f10-345">The `Newtonsoft.Json` `ObjectCreationHandling` setting lets you specify that objects in properties should be reused rather than replaced during deserialization.</span></span> <span data-ttu-id="e9f10-346"><xref:System.Text.Json> 一律會取代屬性中的物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-346"><xref:System.Text.Json> always replaces objects in properties.</span></span>  <span data-ttu-id="e9f10-347">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="e9f10-347">Custom converters can provide this functionality.</span></span>

### <a name="add-to-collections-without-setters"></a><span data-ttu-id="e9f10-348">新增至不含 setter 的集合</span><span class="sxs-lookup"><span data-stu-id="e9f10-348">Add to collections without setters</span></span>

<span data-ttu-id="e9f10-349">在還原序列化期間，即使屬性沒有 setter，`Newtonsoft.Json` 也會將物件加入至集合。</span><span class="sxs-lookup"><span data-stu-id="e9f10-349">During deserialization, `Newtonsoft.Json` adds objects to a collection even if the property has no setter.</span></span> <span data-ttu-id="e9f10-350"><xref:System.Text.Json> 會忽略沒有 setter 的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-350"><xref:System.Text.Json> ignores properties that don't have setters.</span></span> <span data-ttu-id="e9f10-351">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="e9f10-351">Custom converters can provide this functionality.</span></span>

### <a name="missingmemberhandling"></a><span data-ttu-id="e9f10-352">MissingMemberHandling</span><span class="sxs-lookup"><span data-stu-id="e9f10-352">MissingMemberHandling</span></span>

<span data-ttu-id="e9f10-353">`Newtonsoft.Json` 可以設定為在還原序列化期間擲回例外狀況（如果 JSON 包含目標型別中遺漏的屬性）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-353">`Newtonsoft.Json` can be configured to throw exceptions during deserialization if the JSON includes properties that are missing in the target type.</span></span> <span data-ttu-id="e9f10-354"><xref:System.Text.Json> 會忽略 JSON 中的額外屬性，除非您使用[[JsonExtensionData] 屬性](system-text-json-how-to.md#handle-overflow-json)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-354"><xref:System.Text.Json> ignores extra properties in the JSON, except when you use the [[JsonExtensionData] attribute](system-text-json-how-to.md#handle-overflow-json).</span></span> <span data-ttu-id="e9f10-355">缺少的成員功能沒有因應措施。</span><span class="sxs-lookup"><span data-stu-id="e9f10-355">There's no workaround for the missing member feature.</span></span>

### <a name="tracewriter"></a><span data-ttu-id="e9f10-356">TraceWriter</span><span class="sxs-lookup"><span data-stu-id="e9f10-356">TraceWriter</span></span>

<span data-ttu-id="e9f10-357">`Newtonsoft.Json` 可讓您使用 `TraceWriter` 來進行 debug，以查看由序列化或還原序列化所產生的記錄。</span><span class="sxs-lookup"><span data-stu-id="e9f10-357">`Newtonsoft.Json` lets you debug by using a `TraceWriter` to view logs that are generated by serialization or deserialization.</span></span> <span data-ttu-id="e9f10-358"><xref:System.Text.Json> 不會進行記錄。</span><span class="sxs-lookup"><span data-stu-id="e9f10-358"><xref:System.Text.Json> doesn't do logging.</span></span>

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a><span data-ttu-id="e9f10-359">相較于 JToken 的 JsonDocument 和 JsonElement （例如 JObject、JArray）</span><span class="sxs-lookup"><span data-stu-id="e9f10-359">JsonDocument and JsonElement compared to JToken (like JObject, JArray)</span></span>

<span data-ttu-id="e9f10-360"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供從現有 JSON 承載剖析和建立**唯讀**檔物件模型（DOM）的功能。</span><span class="sxs-lookup"><span data-stu-id="e9f10-360"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to parse and build a **read-only** Document Object Model (DOM) from existing JSON payloads.</span></span> <span data-ttu-id="e9f10-361">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-361">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="e9f10-362">組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-362">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="e9f10-363">`JsonElement` 類型會提供 Api，將 JSON 文字轉換成常見的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="e9f10-363">The `JsonElement` type provides APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="e9f10-364">`JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9f10-364">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

### <a name="jsondocument-is-idisposable"></a><span data-ttu-id="e9f10-365">JsonDocument 是 IDisposable</span><span class="sxs-lookup"><span data-stu-id="e9f10-365">JsonDocument is IDisposable</span></span>

<span data-ttu-id="e9f10-366">`JsonDocument` 會將資料的記憶體中視圖建立成集區緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e9f10-366">`JsonDocument` builds an in-memory view of the data into a pooled buffer.</span></span> <span data-ttu-id="e9f10-367">因此，不同于 `Newtonsoft.Json`的 `JObject` 或 `JArray`，`JsonDocument` 型別會執行 `IDisposable`，而且必須在 using 區塊內使用。</span><span class="sxs-lookup"><span data-stu-id="e9f10-367">Therefore, unlike `JObject` or `JArray` from `Newtonsoft.Json`, the `JsonDocument` type implements `IDisposable` and needs to be used inside a using block.</span></span> 

<span data-ttu-id="e9f10-368">如果您想要將存留期擁有權和處置責任轉移給呼叫者，只會從您的 API 傳回 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-368">Only return a `JsonDocument` from your API if you want to transfer lifetime ownership and dispose responsibility to the caller.</span></span> <span data-ttu-id="e9f10-369">在大部分的情況下，這並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="e9f10-369">In most scenarios, that isn't necessary.</span></span> <span data-ttu-id="e9f10-370">如果呼叫端需要使用整個 JSON 檔，則會傳回 <xref:System.Text.Json.JsonDocument.RootElement%2A>的 <xref:System.Text.Json.JsonElement.Clone%2A>，也就是 <xref:System.Text.Json.JsonElement>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-370">If the caller needs to work with the entire JSON document, return the <xref:System.Text.Json.JsonElement.Clone%2A> of the <xref:System.Text.Json.JsonDocument.RootElement%2A>, which is a <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="e9f10-371">如果呼叫端需要使用 JSON 檔中的特定元素，則會傳回該 <xref:System.Text.Json.JsonElement>的 <xref:System.Text.Json.JsonElement.Clone%2A>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-371">If the caller needs to work with a particular element within the JSON document, return the <xref:System.Text.Json.JsonElement.Clone%2A> of that <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="e9f10-372">如果您直接傳回 `RootElement` 或子項目而不進行 `Clone`，則在處置擁有它的 `JsonDocument` 之後，呼叫端將無法存取傳回的 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-372">If you return the `RootElement` or a sub-element directly without making a `Clone`, the caller won't be able to access the returned `JsonElement` after the `JsonDocument` that owns it is disposed.</span></span>

<span data-ttu-id="e9f10-373">以下是要求您進行 `Clone`的範例：</span><span class="sxs-lookup"><span data-stu-id="e9f10-373">Here's an example that requires you to make a `Clone`:</span></span>

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

<span data-ttu-id="e9f10-374">上述程式碼需要包含 `fileName` 屬性的 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-374">The preceding code expects a `JsonElement` that contains a `fileName` property.</span></span> <span data-ttu-id="e9f10-375">它會開啟 JSON 檔案，並建立 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-375">It opens the JSON file and creates a `JsonDocument`.</span></span> <span data-ttu-id="e9f10-376">方法假設呼叫端想要使用整份檔，因此它會傳回 `RootElement`的 `Clone`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-376">The method assumes that the caller wants to work with the entire document, so it returns the `Clone` of the `RootElement`.</span></span> 

<span data-ttu-id="e9f10-377">如果您收到 `JsonElement` 並傳回子項目，則不需要傳回子項目的 `Clone`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-377">If you receive a `JsonElement` and are returning a sub-element, it's not necessary to return a `Clone` of the sub-element.</span></span> <span data-ttu-id="e9f10-378">呼叫端負責保持傳入 `JsonElement` 所屬的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-378">The caller is responsible for keeping alive the `JsonDocument` that the passed-in `JsonElement` belongs to.</span></span> <span data-ttu-id="e9f10-379">例如：</span><span class="sxs-lookup"><span data-stu-id="e9f10-379">For example:</span></span>

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a><span data-ttu-id="e9f10-380">JsonDocument 是唯讀的</span><span class="sxs-lookup"><span data-stu-id="e9f10-380">JsonDocument is read-only</span></span>

<span data-ttu-id="e9f10-381"><xref:System.Text.Json> DOM 無法加入、移除或修改 JSON 元素。</span><span class="sxs-lookup"><span data-stu-id="e9f10-381">The <xref:System.Text.Json> DOM can't add, remove, or modify JSON elements.</span></span> <span data-ttu-id="e9f10-382">其設計是以這種方式來進行效能，並減少剖析一般 JSON 承載大小的配置（也就是 < 1 MB）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-382">It's designed this way for performance and to reduce allocations for parsing common JSON payload sizes (that is, < 1 MB).</span></span> <span data-ttu-id="e9f10-383">如果您的案例目前使用可修改的 DOM，下列其中一個因應措施可能是可行的：</span><span class="sxs-lookup"><span data-stu-id="e9f10-383">If your scenario currently uses a modifiable DOM, one of the following workarounds might be feasible:</span></span>

* <span data-ttu-id="e9f10-384">若要從頭開始建立 `JsonDocument` （也就是不會將現有的 JSON 承載傳遞給 `Parse` 方法），請使用 `Utf8JsonWriter` 寫入 JSON 文字，並剖析該輸出，以建立新的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-384">To build a `JsonDocument` from scratch (that is, without passing in an existing JSON payload to the `Parse` method), write the JSON text by using the `Utf8JsonWriter` and parse the output from that to make a new `JsonDocument`.</span></span>
* <span data-ttu-id="e9f10-385">若要修改現有的 `JsonDocument`，請使用它來寫入 JSON 文字，並在您撰寫時進行變更，並剖析該輸出以建立新的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-385">To modify an existing `JsonDocument`, use it to write JSON text, making changes while you write, and parse the output from that to make a new `JsonDocument`.</span></span>
* <span data-ttu-id="e9f10-386">若要合併現有的 JSON 檔，相當於 `Newtonsoft.Json`的 `JObject.Merge` 或 `JContainer.Merge` Api，請參閱[此 GitHub 問題](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-386">To merge existing JSON documents, equivalent to the `JObject.Merge` or `JContainer.Merge` APIs from `Newtonsoft.Json`, see [this GitHub issue](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).</span></span>

### <a name="jsonelement-is-a-union-struct"></a><span data-ttu-id="e9f10-387">JsonElement 是聯集結構</span><span class="sxs-lookup"><span data-stu-id="e9f10-387">JsonElement is a union struct</span></span>

<span data-ttu-id="e9f10-388">`JsonDocument` 會將 `RootElement` 公開為 <xref:System.Text.Json.JsonElement>類型的屬性，也就是包含任何 JSON 元素的 union、struct 類型。</span><span class="sxs-lookup"><span data-stu-id="e9f10-388">`JsonDocument` exposes the `RootElement` as a property of type <xref:System.Text.Json.JsonElement>, which is a union, struct type that encompasses any JSON element.</span></span> <span data-ttu-id="e9f10-389">`Newtonsoft.Json` 使用專用的階層型別，如 `JObject`、`JArray`、`JToken`等等。</span><span class="sxs-lookup"><span data-stu-id="e9f10-389">`Newtonsoft.Json` uses dedicated hierarchical types like `JObject`,`JArray`, `JToken`, and so forth.</span></span> <span data-ttu-id="e9f10-390">`JsonElement` 是您可以搜尋和列舉的專案，您可以使用 `JsonElement` 將 JSON 元素具體化成 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="e9f10-390">`JsonElement` is what you can search and enumerate over, and you can use `JsonElement` to materialize JSON elements into .NET types.</span></span>

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a><span data-ttu-id="e9f10-391">如何搜尋子項目的 JsonDocument 和 JsonElement</span><span class="sxs-lookup"><span data-stu-id="e9f10-391">How to search a JsonDocument and JsonElement for sub-elements</span></span>

<span data-ttu-id="e9f10-392">使用 `JObject` 或 `JArray` 從 `Newtonsoft.Json` 搜尋 JSON 權杖，通常會相對快速，因為它們是在某個字典中的查閱。</span><span class="sxs-lookup"><span data-stu-id="e9f10-392">Searches for JSON tokens using `JObject` or `JArray` from `Newtonsoft.Json` tend to be relatively fast because they're lookups in some dictionary.</span></span> <span data-ttu-id="e9f10-393">相較之下，搜尋 `JsonElement` 需要依序搜尋屬性，因此速度相當慢（例如使用 `TryGetProperty`時）。</span><span class="sxs-lookup"><span data-stu-id="e9f10-393">By comparison, searches on `JsonElement` require a sequential search of the properties and hence is relatively slow (for example when using `TryGetProperty`).</span></span> <span data-ttu-id="e9f10-394"><xref:System.Text.Json> 的設計目的是要將初始剖析時間減至最少，而不是查閱時間。</span><span class="sxs-lookup"><span data-stu-id="e9f10-394"><xref:System.Text.Json> is designed to minimize initial parse time rather than lookup time.</span></span> <span data-ttu-id="e9f10-395">因此，搜尋 `JsonDocument` 物件時，請使用下列方法來優化效能：</span><span class="sxs-lookup"><span data-stu-id="e9f10-395">Therefore, use the following approaches to optimize performance when searching through a `JsonDocument` object:</span></span>

* <span data-ttu-id="e9f10-396">使用內建的列舉值（<xref:System.Text.Json.JsonElement.EnumerateArray%2A> 和 <xref:System.Text.Json.JsonElement.EnumerateObject%2A>），而不是執行您自己的索引或迴圈。</span><span class="sxs-lookup"><span data-stu-id="e9f10-396">Use the built-in enumerators (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> and <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) rather than doing your own indexing or loops.</span></span>
* <span data-ttu-id="e9f10-397">請不要透過每個屬性，使用 `RootElement`，對整個 `JsonDocument` 進行順序搜尋。</span><span class="sxs-lookup"><span data-stu-id="e9f10-397">Don't do a sequential search on the whole `JsonDocument` through every property by using `RootElement`.</span></span> <span data-ttu-id="e9f10-398">相反地，請根據 JSON 資料的已知結構來搜尋嵌套的 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-398">Instead, search on nested JSON objects based on the known structure of the JSON data.</span></span> <span data-ttu-id="e9f10-399">例如，如果您要尋找 `Student` 物件中的 `Grade` 屬性，請對 `Student` 物件執行迴圈，並取得每一個的 `Grade` 值，而不是搜尋尋找 `JsonElement` 屬性的所有 `Grade` 物件。</span><span class="sxs-lookup"><span data-stu-id="e9f10-399">For example, if you're looking for a `Grade` property in `Student` objects, loop through the `Student` objects and get the value of `Grade` for each, rather than searching through all `JsonElement` objects looking for `Grade` properties.</span></span> <span data-ttu-id="e9f10-400">執行後者會導致相同資料的不必要傳遞。</span><span class="sxs-lookup"><span data-stu-id="e9f10-400">Doing the latter will result in unnecessary passes over the same data.</span></span>

<span data-ttu-id="e9f10-401">如需程式碼範例，請參閱[使用 JsonDocument 來存取資料](system-text-json-how-to.md#use-jsondocument-for-access-to-data)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-401">For a code example, see [Use JsonDocument for access to data](system-text-json-how-to.md#use-jsondocument-for-access-to-data).</span></span>

## <a name="utf8jsonreader-compared-to-jsontextreader"></a><span data-ttu-id="e9f10-402">Utf8JsonReader 與 JsonTextReader 的比較</span><span class="sxs-lookup"><span data-stu-id="e9f10-402">Utf8JsonReader compared to JsonTextReader</span></span>

<span data-ttu-id="e9f10-403"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器、從[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601)讀取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-403"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) or [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601).</span></span> <span data-ttu-id="e9f10-404">`Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="e9f10-404">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span>

<span data-ttu-id="e9f10-405">下列各節說明使用 `Utf8JsonReader`的建議程式設計模式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-405">The following sections explain recommended programming patterns for using `Utf8JsonReader`.</span></span>

### <a name="utf8jsonreader-is-a-ref-struct"></a><span data-ttu-id="e9f10-406">Utf8JsonReader 是 ref 結構</span><span class="sxs-lookup"><span data-stu-id="e9f10-406">Utf8JsonReader is a ref struct</span></span>

<span data-ttu-id="e9f10-407">因為 `Utf8JsonReader` 類型是*ref 結構*，所以有[一些限制](../../csharp/language-reference/keywords/ref.md#ref-struct-types)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-407">Because the `Utf8JsonReader` type is a *ref struct*, it has [certain limitations](../../csharp/language-reference/keywords/ref.md#ref-struct-types).</span></span> <span data-ttu-id="e9f10-408">例如，它無法在 ref 結構以外的類別或結構上儲存為欄位。</span><span class="sxs-lookup"><span data-stu-id="e9f10-408">For example, it can't be stored as a field on a class or struct other than a ref struct.</span></span> <span data-ttu-id="e9f10-409">為了達到高效能，此型別必須是 `ref struct`，因為它需要快取輸入[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)，這本身就是 ref 結構。</span><span class="sxs-lookup"><span data-stu-id="e9f10-409">To achieve high performance, this type must be a `ref struct` since it needs to cache the input [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), which itself is a ref struct.</span></span> <span data-ttu-id="e9f10-410">此外，這種類型是可變動的，因為它會保存狀態。</span><span class="sxs-lookup"><span data-stu-id="e9f10-410">In addition, this type is mutable since it holds state.</span></span> <span data-ttu-id="e9f10-411">因此，請以 ref 而非傳值方式來**傳遞它**。</span><span class="sxs-lookup"><span data-stu-id="e9f10-411">Therefore, **pass it by ref** rather than by value.</span></span> <span data-ttu-id="e9f10-412">以傳值方式傳遞會導致結構複製，而且呼叫端看不到狀態變更。</span><span class="sxs-lookup"><span data-stu-id="e9f10-412">Passing it by value would result in a struct copy and the state changes would not be visible to the caller.</span></span> <span data-ttu-id="e9f10-413">這與 `Newtonsoft.Json` 不同，因為 `Newtonsoft.Json` `JsonTextReader` 是一個類別。</span><span class="sxs-lookup"><span data-stu-id="e9f10-413">This differs from `Newtonsoft.Json` since the `Newtonsoft.Json` `JsonTextReader` is a class.</span></span> <span data-ttu-id="e9f10-414">如需如何使用 ref 結構的詳細資訊，請參閱[撰寫安全且C#有效率](../../csharp/write-safe-efficient-code.md)的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9f10-414">For more information about how to use ref structs, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>

### <a name="read-utf-8-text"></a><span data-ttu-id="e9f10-415">讀取 UTF-8 文字</span><span class="sxs-lookup"><span data-stu-id="e9f10-415">Read UTF-8 text</span></span>

<span data-ttu-id="e9f10-416">若要在使用 `Utf8JsonReader`時達到最佳效能，請閱讀已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。</span><span class="sxs-lookup"><span data-stu-id="e9f10-416">To achieve the best possible performance while using the `Utf8JsonReader`, read JSON payloads already encoded as UTF-8 text rather than as UTF-16 strings.</span></span> <span data-ttu-id="e9f10-417">如需程式碼範例，請參閱[使用 Utf8JsonReader 來篩選資料](system-text-json-how-to.md#filter-data-using-utf8jsonreader)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-417">For a code example, see [Filter data using Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).</span></span>

### <a name="read-with-a-stream-or-pipereader"></a><span data-ttu-id="e9f10-418">讀取資料流程或 PipeReader</span><span class="sxs-lookup"><span data-stu-id="e9f10-418">Read with a Stream or PipeReader</span></span>

<span data-ttu-id="e9f10-419">`Utf8JsonReader` 支援從以 UTF-8 編碼的[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果）讀取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-419">The `Utf8JsonReader` supports reading from a UTF-8 encoded [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) or [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601) (which is the result of reading from a <xref:System.IO.Pipelines.PipeReader>).</span></span>

<span data-ttu-id="e9f10-420">對於同步讀取，您可以讀取 JSON 承載，直到資料流程結尾到位元組陣列，然後將它傳遞到讀取器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-420">For synchronous reading, you could read the JSON payload until the end of the stream into a byte array and pass that into the reader.</span></span> <span data-ttu-id="e9f10-421">若要從字串讀取（編碼為 UTF-16），請呼叫 <xref:System.Text.Encoding.UTF8>。<xref:System.Text.Encoding.GetBytes%2A></span><span class="sxs-lookup"><span data-stu-id="e9f10-421">For reading from a string (which is encoded as UTF-16), call <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A></span></span> <span data-ttu-id="e9f10-422">首先，將字串轉碼為 UTF-8 編碼的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e9f10-422">to first transcode the string to a UTF-8 encoded byte array.</span></span> <span data-ttu-id="e9f10-423">然後將它傳遞給 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-423">Then pass that to the `Utf8JsonReader`.</span></span> 

<span data-ttu-id="e9f10-424">由於 `Utf8JsonReader` 會將輸入視為 JSON 文字，因此會將 UTF-8 位元組順序標記（BOM）視為不正確 JSON。</span><span class="sxs-lookup"><span data-stu-id="e9f10-424">Since the `Utf8JsonReader` considers the input to be JSON text, a UTF-8 byte order mark (BOM) is considered invalid JSON.</span></span> <span data-ttu-id="e9f10-425">呼叫端必須先篩選掉，再將資料傳遞給讀取器。</span><span class="sxs-lookup"><span data-stu-id="e9f10-425">The caller needs to filter that out before passing the data to the reader.</span></span>

<span data-ttu-id="e9f10-426">如需程式碼範例，請參閱[使用 Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-426">For code examples, see [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).</span></span>

### <a name="read-with-multi-segment-readonlysequence"></a><span data-ttu-id="e9f10-427">閱讀多區段 ReadOnlySequence</span><span class="sxs-lookup"><span data-stu-id="e9f10-427">Read with multi-segment ReadOnlySequence</span></span>

<span data-ttu-id="e9f10-428">如果您的 JSON 輸入是[ReadOnlySpan\<位元組 >](xref:System.ReadOnlySpan%601)，則當您執行讀取迴圈時，可以從讀取器上的 `ValueSpan` 屬性存取每個 json 元素。</span><span class="sxs-lookup"><span data-stu-id="e9f10-428">If your JSON input is a [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), each JSON element can be accessed from the `ValueSpan` property on the reader as you go through the read loop.</span></span> <span data-ttu-id="e9f10-429">不過，如果您的輸入是[ReadOnlySequence\<位元組 >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果），某些 JSON 元素可能會跨 `ReadOnlySequence<byte>` 物件的多個區段。</span><span class="sxs-lookup"><span data-stu-id="e9f10-429">However, if your input is a [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601) (which is the result of reading from a <xref:System.IO.Pipelines.PipeReader>), some JSON elements might straddle multiple segments of the `ReadOnlySequence<byte>` object.</span></span> <span data-ttu-id="e9f10-430">這些元素無法從連續記憶體區塊中的 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 存取。</span><span class="sxs-lookup"><span data-stu-id="e9f10-430">These elements would not be accessible from <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> in a contiguous memory block.</span></span> <span data-ttu-id="e9f10-431">相反地，每當您有多個區段 `ReadOnlySequence<byte>` 做為輸入時，請輪詢讀取器上的 <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> 屬性，以瞭解如何存取目前的 JSON 元素。</span><span class="sxs-lookup"><span data-stu-id="e9f10-431">Instead, whenever you have a multi-segment `ReadOnlySequence<byte>` as input, poll the <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> property on the reader to figure out how to access the current JSON element.</span></span> <span data-ttu-id="e9f10-432">以下是建議的模式：</span><span class="sxs-lookup"><span data-stu-id="e9f10-432">Here's a recommended pattern:</span></span>

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

### <a name="use-valuetextequals-for-property-name-lookups"></a><span data-ttu-id="e9f10-433">使用 ValueTextEquals 進行屬性名稱查閱</span><span class="sxs-lookup"><span data-stu-id="e9f10-433">Use ValueTextEquals for property name lookups</span></span>

<span data-ttu-id="e9f10-434">請不要使用 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 透過呼叫屬性名稱查閱的 <xref:System.MemoryExtensions.SequenceEqual%2A> 來進行逐位元組比較。</span><span class="sxs-lookup"><span data-stu-id="e9f10-434">Don't use <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> to do byte-by-byte comparisons by calling <xref:System.MemoryExtensions.SequenceEqual%2A> for property name lookups.</span></span> <span data-ttu-id="e9f10-435">改為呼叫 <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>，因為該方法會將任何在 JSON 中進行轉義的字元。</span><span class="sxs-lookup"><span data-stu-id="e9f10-435">Call <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> instead, because that method unescapes any characters that are escaped in the JSON.</span></span> <span data-ttu-id="e9f10-436">以下範例顯示如何搜尋名為 "name" 的屬性：</span><span class="sxs-lookup"><span data-stu-id="e9f10-436">Here's an example that shows how to search for a property that is named "name":</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a><span data-ttu-id="e9f10-437">將 null 值讀取成可為 null 的實數值型別</span><span class="sxs-lookup"><span data-stu-id="e9f10-437">Read null values into nullable value types</span></span>

<span data-ttu-id="e9f10-438">`Newtonsoft.Json` 所提供的 Api 會傳回 <xref:System.Nullable%601>，例如 `ReadAsBoolean`，藉由傳回 `TokenType` 來處理 `Null` `bool?`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-438">`Newtonsoft.Json` provides APIs that return <xref:System.Nullable%601>, such as `ReadAsBoolean`, which handles a `Null` `TokenType` for you by returning a `bool?`.</span></span> <span data-ttu-id="e9f10-439">內建的 `System.Text.Json` Api 只會傳回不可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="e9f10-439">The built-in `System.Text.Json` APIs return only non-nullable value types.</span></span> <span data-ttu-id="e9f10-440">例如，<xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> 會傳回 `bool`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-440">For example, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> returns a `bool`.</span></span> <span data-ttu-id="e9f10-441">如果在 JSON 中找到 `Null`，它會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f10-441">It throws an exception if it finds `Null` in the JSON.</span></span> <span data-ttu-id="e9f10-442">下列範例示範兩種處理 null 的方式：一個是藉由傳回可為 null 的實值型別，另一個則是傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-442">The following examples show two ways to handle nulls, one by returning a nullable value type and one by returning the default value:</span></span>

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

### <a name="multi-targeting"></a><span data-ttu-id="e9f10-443">多目標</span><span class="sxs-lookup"><span data-stu-id="e9f10-443">Multi-targeting</span></span>

<span data-ttu-id="e9f10-444">如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。</span><span class="sxs-lookup"><span data-stu-id="e9f10-444">If you need to continue to use `Newtonsoft.Json` for certain target frameworks, you can multi-target and have two implementations.</span></span> <span data-ttu-id="e9f10-445">不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。</span><span class="sxs-lookup"><span data-stu-id="e9f10-445">However, this is not trivial and would require some `#ifdefs` and source duplication.</span></span> <span data-ttu-id="e9f10-446">盡可能共用程式碼的方法之一，就是建立 `Utf8JsonReader` 和 `Newtonsoft.Json` `JsonTextReader`的 `ref struct` 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-446">One way to share as much code as possible is to create a `ref struct` wrapper around `Utf8JsonReader` and `Newtonsoft.Json` `JsonTextReader`.</span></span> <span data-ttu-id="e9f10-447">此包裝函式會統一公用介面區，同時隔離行為差異。</span><span class="sxs-lookup"><span data-stu-id="e9f10-447">This wrapper would unify the public surface area while isolating the behavioral differences.</span></span> <span data-ttu-id="e9f10-448">這可讓您隔離主要變更與型別的結構，並以傳址方式傳遞新的型別。</span><span class="sxs-lookup"><span data-stu-id="e9f10-448">This lets you isolate the changes mainly to the construction of the type, along with passing the new type around by reference.</span></span> <span data-ttu-id="e9f10-449">這是[DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫所遵循的模式：</span><span class="sxs-lookup"><span data-stu-id="e9f10-449">This is the pattern that the [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) library follows:</span></span>

* [<span data-ttu-id="e9f10-450">UnifiedJsonReader.JsonTextReader.cs</span><span class="sxs-lookup"><span data-stu-id="e9f10-450">UnifiedJsonReader.JsonTextReader.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [<span data-ttu-id="e9f10-451">UnifiedJsonReader.Utf8JsonReader.cs</span><span class="sxs-lookup"><span data-stu-id="e9f10-451">UnifiedJsonReader.Utf8JsonReader.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a><span data-ttu-id="e9f10-452">Utf8JsonWriter 與 Json.net jsoNtextwriter, 的比較</span><span class="sxs-lookup"><span data-stu-id="e9f10-452">Utf8JsonWriter compared to JsonTextWriter</span></span>

<span data-ttu-id="e9f10-453"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="e9f10-453"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="e9f10-454">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="e9f10-454">The writer is a low-level type that can be used to build custom serializers.</span></span>

<span data-ttu-id="e9f10-455">下列各節說明使用 `Utf8JsonWriter`的建議程式設計模式。</span><span class="sxs-lookup"><span data-stu-id="e9f10-455">The following sections explain recommended programming patterns for using `Utf8JsonWriter`.</span></span>

### <a name="write-with-utf-8-text"></a><span data-ttu-id="e9f10-456">以 UTF-8 文字撰寫</span><span class="sxs-lookup"><span data-stu-id="e9f10-456">Write with UTF-8 text</span></span>

<span data-ttu-id="e9f10-457">若要在使用 `Utf8JsonWriter`時達到最佳效能，請撰寫已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。</span><span class="sxs-lookup"><span data-stu-id="e9f10-457">To achieve the best possible performance while using the `Utf8JsonWriter`, write JSON payloads already encoded as UTF-8 text rather than as UTF-16 strings.</span></span> <span data-ttu-id="e9f10-458">使用 <xref:System.Text.Json.JsonEncodedText> 來快取和預先編碼已知的字串屬性名稱和值，並將其傳遞給寫入器，而不是使用 UTF-16 字串常值。</span><span class="sxs-lookup"><span data-stu-id="e9f10-458">Use <xref:System.Text.Json.JsonEncodedText> to cache and pre-encode known string property names and values as statics, and pass those to the writer, rather than using UTF-16 string literals.</span></span> <span data-ttu-id="e9f10-459">這比快取和使用 UTF-8 位元組陣列更快速。</span><span class="sxs-lookup"><span data-stu-id="e9f10-459">This is faster than caching and using UTF-8 byte arrays.</span></span>

<span data-ttu-id="e9f10-460">如果您需要執行自訂的轉義，此方法也適用。</span><span class="sxs-lookup"><span data-stu-id="e9f10-460">This approach also works if you need to do custom escaping.</span></span> <span data-ttu-id="e9f10-461">`System.Text.Json` 不允許您在寫入字串時停用轉義。</span><span class="sxs-lookup"><span data-stu-id="e9f10-461">`System.Text.Json` doesn't let you disable escaping while writing a string.</span></span> <span data-ttu-id="e9f10-462">不過，您可以將自己的自訂 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 當做寫入器的選項傳入，或建立您自己的 `JsonEncodedText` 以使用您的 `JavascriptEncoder` 來執行轉義，然後撰寫 `JsonEncodedText`，而不是字串。</span><span class="sxs-lookup"><span data-stu-id="e9f10-462">However, you could pass in your own custom <xref:System.Text.Encodings.Web.JavaScriptEncoder> as an option to the writer, or create your own `JsonEncodedText` that uses your `JavascriptEncoder` to do the escaping, and then write the `JsonEncodedText` instead of the string.</span></span> <span data-ttu-id="e9f10-463">如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-463">For more information, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="write-raw-values"></a><span data-ttu-id="e9f10-464">寫入原始值</span><span class="sxs-lookup"><span data-stu-id="e9f10-464">Write raw values</span></span>

<span data-ttu-id="e9f10-465">`Newtonsoft.Json` `WriteRawValue` 方法會寫入需要值的原始 JSON。</span><span class="sxs-lookup"><span data-stu-id="e9f10-465">The `Newtonsoft.Json` `WriteRawValue` method writes raw JSON where a value is expected.</span></span> <span data-ttu-id="e9f10-466"><xref:System.Text.Json> 沒有直接的對等用法，但以下是可確保只會寫入有效 JSON 的因應措施：</span><span class="sxs-lookup"><span data-stu-id="e9f10-466"><xref:System.Text.Json> has no direct equivalent, but here's a workaround that ensures only valid JSON is written:</span></span>

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a><span data-ttu-id="e9f10-467">自訂字元轉義</span><span class="sxs-lookup"><span data-stu-id="e9f10-467">Customize character escaping</span></span>

<span data-ttu-id="e9f10-468">`JsonTextWriter` 的[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)設定會提供選項，以將所有非 ASCII 字元**或**HTML 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="e9f10-468">The [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) setting of `JsonTextWriter` offers options to escape all non-ASCII characters **or** HTML characters.</span></span> <span data-ttu-id="e9f10-469">根據預設，`Utf8JsonWriter` 會將所有非 ASCII**和**HTML 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="e9f10-469">By default, `Utf8JsonWriter` escapes all non-ASCII **and** HTML characters.</span></span> <span data-ttu-id="e9f10-470">這項轉義是針對深層防禦的安全性原因而完成。</span><span class="sxs-lookup"><span data-stu-id="e9f10-470">This escaping is done for defense-in-depth security reasons.</span></span> <span data-ttu-id="e9f10-471">若要指定不同的轉義原則，請建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 並設定 <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-471">To specify a different escaping policy, create a <xref:System.Text.Encodings.Web.JavaScriptEncoder> and set <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9f10-472">如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="e9f10-472">For more information, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="customize-json-format"></a><span data-ttu-id="e9f10-473">自訂 JSON 格式</span><span class="sxs-lookup"><span data-stu-id="e9f10-473">Customize JSON format</span></span>

<span data-ttu-id="e9f10-474">`JsonTextWriter` 包含下列設定，其中 `Utf8JsonWriter` 沒有對等的：</span><span class="sxs-lookup"><span data-stu-id="e9f10-474">`JsonTextWriter` includes the following settings, for which `Utf8JsonWriter` has no equivalent:</span></span>

* <span data-ttu-id="e9f10-475">[縮排](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm)-指定要縮排的字元數。</span><span class="sxs-lookup"><span data-stu-id="e9f10-475">[Indentation](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Specifies how many characters to indent.</span></span> <span data-ttu-id="e9f10-476">`Utf8JsonWriter` 一律會進行2個字元的縮排。</span><span class="sxs-lookup"><span data-stu-id="e9f10-476">`Utf8JsonWriter` always does 2-character indentation.</span></span>
* <span data-ttu-id="e9f10-477">[IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -指定要用於縮排的字元。</span><span class="sxs-lookup"><span data-stu-id="e9f10-477">[IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Specifies the character to use for indentation.</span></span>  <span data-ttu-id="e9f10-478">`Utf8JsonWriter` 一律使用空白字元。</span><span class="sxs-lookup"><span data-stu-id="e9f10-478">`Utf8JsonWriter` always uses whitespace.</span></span>
* <span data-ttu-id="e9f10-479">[QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -指定用來括住字串值的字元。</span><span class="sxs-lookup"><span data-stu-id="e9f10-479">[QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Specifies the character to use to surround string values.</span></span>  <span data-ttu-id="e9f10-480">`Utf8JsonWriter` 一律使用雙引號。</span><span class="sxs-lookup"><span data-stu-id="e9f10-480">`Utf8JsonWriter` always uses double quotes.</span></span>
* <span data-ttu-id="e9f10-481">[QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -指定是否要以引號括住屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e9f10-481">[QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Specifies whether or not to surround property names with quotes.</span></span>  <span data-ttu-id="e9f10-482">`Utf8JsonWriter` 一律以引號括住它們。</span><span class="sxs-lookup"><span data-stu-id="e9f10-482">`Utf8JsonWriter` always surrounds them with quotes.</span></span>

<span data-ttu-id="e9f10-483">沒有任何因應措施可讓您自訂 `Utf8JsonWriter` 以這些方式產生的 JSON。</span><span class="sxs-lookup"><span data-stu-id="e9f10-483">There are no workarounds that would let you customize the JSON produced by `Utf8JsonWriter` in these ways.</span></span>

### <a name="write-null-values"></a><span data-ttu-id="e9f10-484">寫入 null 值</span><span class="sxs-lookup"><span data-stu-id="e9f10-484">Write null values</span></span>

<span data-ttu-id="e9f10-485">若要使用 `Utf8JsonWriter`來寫入 null 值，請呼叫：</span><span class="sxs-lookup"><span data-stu-id="e9f10-485">To write null values by using `Utf8JsonWriter`, call:</span></span>

* <span data-ttu-id="e9f10-486"><xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> 寫入具有 null 值的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="e9f10-486"><xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> to write a key-value pair with null as the value.</span></span>
* <span data-ttu-id="e9f10-487"><xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> 寫入 null 做為 JSON 陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="e9f10-487"><xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> to write null as an element of a JSON array.</span></span>

<span data-ttu-id="e9f10-488">若為字串屬性，如果字串為 null，<xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> 和 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> 就相當於 `WriteNull` 和 `WriteNullValue`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-488">For a string property, if the string is null, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> and <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> are equivalent to `WriteNull` and `WriteNullValue`.</span></span>

### <a name="write-timespan-uri-or-char-values"></a><span data-ttu-id="e9f10-489">寫入 Timespan、Uri 或 char 值</span><span class="sxs-lookup"><span data-stu-id="e9f10-489">Write Timespan, Uri, or char values</span></span>

<span data-ttu-id="e9f10-490">`JsonTextWriter` 提供[TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm)、 [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)和[char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm)值的 `WriteValue` 方法。</span><span class="sxs-lookup"><span data-stu-id="e9f10-490">`JsonTextWriter` provides `WriteValue` methods for [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm), and [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) values.</span></span> <span data-ttu-id="e9f10-491">`Utf8JsonWriter` 沒有對等的方法。</span><span class="sxs-lookup"><span data-stu-id="e9f10-491">`Utf8JsonWriter` doesn't have equivalent methods.</span></span> <span data-ttu-id="e9f10-492">相反地，請將這些值格式化為字串（例如，藉由呼叫 `ToString()`）並呼叫 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="e9f10-492">Instead, format these values as strings (by calling `ToString()`, for example) and call <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.</span></span>

### <a name="multi-targeting"></a><span data-ttu-id="e9f10-493">多目標</span><span class="sxs-lookup"><span data-stu-id="e9f10-493">Multi-targeting</span></span>

<span data-ttu-id="e9f10-494">如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。</span><span class="sxs-lookup"><span data-stu-id="e9f10-494">If you need to continue to use `Newtonsoft.Json` for certain target frameworks, you can multi-target and have two implementations.</span></span> <span data-ttu-id="e9f10-495">不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。</span><span class="sxs-lookup"><span data-stu-id="e9f10-495">However, this is not trivial and would require some `#ifdefs` and source duplication.</span></span> <span data-ttu-id="e9f10-496">盡可能共用程式碼的方法之一，就是建立一個圍繞 `Utf8JsonWriter` 的包裝函式，並 `Newtonsoft` `JsonTextWriter`。</span><span class="sxs-lookup"><span data-stu-id="e9f10-496">One way to share as much code as possible is to create a wrapper around `Utf8JsonWriter` and `Newtonsoft` `JsonTextWriter`.</span></span> <span data-ttu-id="e9f10-497">此包裝函式會統一公用介面區，同時隔離行為差異。</span><span class="sxs-lookup"><span data-stu-id="e9f10-497">This wrapper would unify the public surface area while isolating the behavioral differences.</span></span> <span data-ttu-id="e9f10-498">這可讓您將變更主要隔離到類型的結構。</span><span class="sxs-lookup"><span data-stu-id="e9f10-498">This lets you isolate the changes mainly to the construction of the type.</span></span> <span data-ttu-id="e9f10-499">[DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫如下：</span><span class="sxs-lookup"><span data-stu-id="e9f10-499">[Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) library follows:</span></span>

* [<span data-ttu-id="e9f10-500">UnifiedJsonWriter.JsonTextWriter.cs</span><span class="sxs-lookup"><span data-stu-id="e9f10-500">UnifiedJsonWriter.JsonTextWriter.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [<span data-ttu-id="e9f10-501">UnifiedJsonWriter.Utf8JsonWriter.cs</span><span class="sxs-lookup"><span data-stu-id="e9f10-501">UnifiedJsonWriter.Utf8JsonWriter.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a><span data-ttu-id="e9f10-502">其他資源</span><span class="sxs-lookup"><span data-stu-id="e9f10-502">Additional resources</span></span>

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [<span data-ttu-id="e9f10-503">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="e9f10-503">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e9f10-504">如何使用 System.object</span><span class="sxs-lookup"><span data-stu-id="e9f10-504">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e9f10-505">如何撰寫自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="e9f10-505">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="e9f10-506">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="e9f10-506">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="e9f10-507">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="e9f10-507">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="e9f10-508">System.object。序列化 API 參考</span><span class="sxs-lookup"><span data-stu-id="e9f10-508">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
