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
ms.openlocfilehash: 8b3ffc885691264548a19f694d159ce07aba7550
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904681"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a><span data-ttu-id="9a068-102">如何從 Newtonsoft 遷移至 System.web. Json</span><span class="sxs-lookup"><span data-stu-id="9a068-102">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>

<span data-ttu-id="9a068-103">本文說明如何從[Newtonsoft](https://www.newtonsoft.com/json)遷移至 <xref:System.Text.Json>。</span><span class="sxs-lookup"><span data-stu-id="9a068-103">This article shows how to migrate from [Newtonsoft.Json](https://www.newtonsoft.com/json) to <xref:System.Text.Json>.</span></span>

 <span data-ttu-id="9a068-104">`System.Text.Json` 主要著重于效能、安全性和標準合規性。</span><span class="sxs-lookup"><span data-stu-id="9a068-104">`System.Text.Json` focuses primarily on performance, security, and standards compliance.</span></span> <span data-ttu-id="9a068-105">它在預設行為上有一些主要差異，並不是要與 `Newtonsoft.Json`的功能同位。</span><span class="sxs-lookup"><span data-stu-id="9a068-105">It has some key differences in default behavior and doesn't aim to have feature parity with `Newtonsoft.Json`.</span></span> <span data-ttu-id="9a068-106">在某些情況下，`System.Text.Json` 沒有內建功能，但有建議的因應措施。</span><span class="sxs-lookup"><span data-stu-id="9a068-106">For some scenarios, `System.Text.Json` has no built-in functionality, but there are recommended workarounds.</span></span> <span data-ttu-id="9a068-107">針對其他案例，因應措施並不實用。</span><span class="sxs-lookup"><span data-stu-id="9a068-107">For other scenarios, workarounds are impractical.</span></span> <span data-ttu-id="9a068-108">如果您的應用程式相依于遺失的功能，請考慮提出[問題](https://github.com/dotnet/runtime/issues/new)，以瞭解是否可以新增您案例的支援。</span><span class="sxs-lookup"><span data-stu-id="9a068-108">If your application depends on a missing feature, consider [filing an issue](https://github.com/dotnet/runtime/issues/new) to find out if support for your scenario can be added.</span></span>

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

<span data-ttu-id="9a068-109">本文大部分是關於如何使用 <xref:System.Text.Json.JsonSerializer> API，但它也包含如何使用 <xref:System.Text.Json.JsonDocument> （代表檔物件模型或 DOM）、<xref:System.Text.Json.Utf8JsonReader>和 <xref:System.Text.Json.Utf8JsonWriter> 類型的指引。</span><span class="sxs-lookup"><span data-stu-id="9a068-109">Most of this article is about how to use the <xref:System.Text.Json.JsonSerializer> API, but it also includes guidance on how to use the <xref:System.Text.Json.JsonDocument> (which represents the Document Object Model or DOM), <xref:System.Text.Json.Utf8JsonReader>, and <xref:System.Text.Json.Utf8JsonWriter> types.</span></span> <span data-ttu-id="9a068-110">本文會依照下列順序組織成幾個區段：</span><span class="sxs-lookup"><span data-stu-id="9a068-110">The article is organized into sections in the following order:</span></span>

* [<span data-ttu-id="9a068-111">相較于 Newtonsoft，**預設**JsonSerializer 行為的差異</span><span class="sxs-lookup"><span data-stu-id="9a068-111">Differences in **default** JsonSerializer behavior compared to Newtonsoft.Json</span></span>](#differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson)
* [<span data-ttu-id="9a068-112">使用需要因應措施之 JsonSerializer 的案例</span><span class="sxs-lookup"><span data-stu-id="9a068-112">Scenarios using JsonSerializer that require workarounds</span></span>](#scenarios-using-jsonserializer-that-require-workarounds)
* [<span data-ttu-id="9a068-113">JsonSerializer 目前不支援的案例</span><span class="sxs-lookup"><span data-stu-id="9a068-113">Scenarios that JsonSerializer currently doesn't support</span></span>](#scenarios-that-jsonserializer-currently-doesnt-support)
* [<span data-ttu-id="9a068-114">相較于 JToken 的 JsonDocument 和 JsonElement （例如 JObject、JArray）</span><span class="sxs-lookup"><span data-stu-id="9a068-114">JsonDocument and JsonElement compared to JToken (like JObject, JArray)</span></span>](#jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray)
* [<span data-ttu-id="9a068-115">Utf8JsonReader 與 JsonTextReader 的比較</span><span class="sxs-lookup"><span data-stu-id="9a068-115">Utf8JsonReader compared to JsonTextReader</span></span>](#utf8jsonreader-compared-to-jsontextreader)
* [<span data-ttu-id="9a068-116">Utf8JsonWriter 與 Json.net jsoNtextwriter, 的比較</span><span class="sxs-lookup"><span data-stu-id="9a068-116">Utf8JsonWriter compared to JsonTextWriter</span></span>](#utf8jsonwriter-compared-to-jsontextwriter)

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a><span data-ttu-id="9a068-117">相較于 Newtonsoft，預設 JsonSerializer 行為的差異</span><span class="sxs-lookup"><span data-stu-id="9a068-117">Differences in default JsonSerializer behavior compared to Newtonsoft.Json</span></span>

<span data-ttu-id="9a068-118"><xref:System.Text.Json> 預設為嚴格，並可避免代表呼叫端的任何猜測或解讀，強調決定性的行為。</span><span class="sxs-lookup"><span data-stu-id="9a068-118"><xref:System.Text.Json> is strict by default and avoids any guessing or interpretation on the caller's behalf, emphasizing deterministic behavior.</span></span> <span data-ttu-id="9a068-119">此程式庫是故意以這種方式設計來實現效能和安全性。</span><span class="sxs-lookup"><span data-stu-id="9a068-119">The library is intentionally designed this way for performance and security.</span></span> <span data-ttu-id="9a068-120">`Newtonsoft.Json` 預設為彈性。</span><span class="sxs-lookup"><span data-stu-id="9a068-120">`Newtonsoft.Json` is flexible by default.</span></span> <span data-ttu-id="9a068-121">這項設計的基本差異在於預設行為的下列許多特定差異背後。</span><span class="sxs-lookup"><span data-stu-id="9a068-121">This fundamental difference in design is behind many of the following specific differences in default behavior.</span></span>

### <a name="case-insensitive-deserialization"></a><span data-ttu-id="9a068-122">不區分大小寫的還原序列化</span><span class="sxs-lookup"><span data-stu-id="9a068-122">Case-insensitive deserialization</span></span> 

<span data-ttu-id="9a068-123">在還原序列化期間，`Newtonsoft.Json` 預設會執行不區分大小寫的屬性名稱比對。</span><span class="sxs-lookup"><span data-stu-id="9a068-123">During deserialization, `Newtonsoft.Json` does case-insensitive property name matching by default.</span></span> <span data-ttu-id="9a068-124"><xref:System.Text.Json> 預設值區分大小寫，這可提供較佳的效能，因為它會執行完全相符的作業。</span><span class="sxs-lookup"><span data-stu-id="9a068-124">The <xref:System.Text.Json> default is case-sensitive, which gives better performance since it's doing an exact match.</span></span> <span data-ttu-id="9a068-125">如需如何執行不區分大小寫比對的相關資訊，請參閱不[區分大小寫的屬性](system-text-json-how-to.md#case-insensitive-property-matching)比對。</span><span class="sxs-lookup"><span data-stu-id="9a068-125">For information about how to do case-insensitive matching, see [Case-insensitive property matching](system-text-json-how-to.md#case-insensitive-property-matching).</span></span>

<span data-ttu-id="9a068-126">如果您使用 ASP.NET Core 間接使用 `System.Text.Json`，就不需要採取任何動作來取得 `Newtonsoft.Json`之類的行為。</span><span class="sxs-lookup"><span data-stu-id="9a068-126">If you're using `System.Text.Json` indirectly by using ASP.NET Core, you don't need to do anything to get behavior like `Newtonsoft.Json`.</span></span> <span data-ttu-id="9a068-127">ASP.NET Core 指定使用 `System.Text.Json`時， [camel 大小寫屬性名稱](system-text-json-how-to.md#use-camel-case-for-all-json-property-names)和不區分大小寫比對的設定。</span><span class="sxs-lookup"><span data-stu-id="9a068-127">ASP.NET Core specifies the settings for [camel-casing property names](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) and case-insensitive matching when it uses `System.Text.Json`.</span></span>

### <a name="comments"></a><span data-ttu-id="9a068-128">註解</span><span class="sxs-lookup"><span data-stu-id="9a068-128">Comments</span></span>

<span data-ttu-id="9a068-129">在還原序列化期間，`Newtonsoft.Json` 預設會忽略 JSON 中的批註。</span><span class="sxs-lookup"><span data-stu-id="9a068-129">During deserialization, `Newtonsoft.Json` ignores comments in the JSON by default.</span></span> <span data-ttu-id="9a068-130"><xref:System.Text.Json> 預設為會擲回批註的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不會包含它們。</span><span class="sxs-lookup"><span data-stu-id="9a068-130">The <xref:System.Text.Json> default is to throw exceptions for comments because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't include them.</span></span> <span data-ttu-id="9a068-131">如需如何允許批註的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="9a068-131">For information about how to allow comments, see [Allow comments and trailing commas](system-text-json-how-to.md#allow-comments-and-trailing-commas).</span></span>

### <a name="trailing-commas"></a><span data-ttu-id="9a068-132">尾端逗號</span><span class="sxs-lookup"><span data-stu-id="9a068-132">Trailing commas</span></span>

<span data-ttu-id="9a068-133">在還原序列化期間，`Newtonsoft.Json` 預設會忽略尾端的逗號。</span><span class="sxs-lookup"><span data-stu-id="9a068-133">During deserialization, `Newtonsoft.Json` ignores trailing commas by default.</span></span> <span data-ttu-id="9a068-134">它也會忽略多個尾端逗號（例如 `[{"Color":"Red"},{"Color":"Green"},,]`）。</span><span class="sxs-lookup"><span data-stu-id="9a068-134">It also ignores multiple trailing commas (for example, `[{"Color":"Red"},{"Color":"Green"},,]`).</span></span> <span data-ttu-id="9a068-135"><xref:System.Text.Json> 預設值是擲回尾端逗號的例外狀況，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。</span><span class="sxs-lookup"><span data-stu-id="9a068-135">The <xref:System.Text.Json> default is to throw exceptions for trailing commas because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't allow them.</span></span> <span data-ttu-id="9a068-136">如需如何讓 `System.Text.Json` 接受它們的相關資訊，請參閱[允許批註和尾端逗號](system-text-json-how-to.md#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="9a068-136">For information about how to make `System.Text.Json` accept them, see [Allow comments and trailing commas](system-text-json-how-to.md#allow-comments-and-trailing-commas).</span></span> <span data-ttu-id="9a068-137">沒有任何方法可以允許多個尾端逗號。</span><span class="sxs-lookup"><span data-stu-id="9a068-137">There's no way to allow multiple trailing commas.</span></span>

### <a name="json-strings-property-names-and-string-values"></a><span data-ttu-id="9a068-138">JSON 字串（屬性名稱和字串值）</span><span class="sxs-lookup"><span data-stu-id="9a068-138">JSON strings (property names and string values)</span></span>

<span data-ttu-id="9a068-139">在還原序列化期間，`Newtonsoft.Json` 接受以雙引號、單引號或不含引號括住的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9a068-139">During deserialization, `Newtonsoft.Json` accepts property names surrounded by double quotes, single quotes, or without quotes.</span></span> <span data-ttu-id="9a068-140">它接受以雙引號或單引號括住的字串值。</span><span class="sxs-lookup"><span data-stu-id="9a068-140">It accepts string values surrounded by double quotes or single quotes.</span></span> <span data-ttu-id="9a068-141">例如，`Newtonsoft.Json` 接受下列 JSON：</span><span class="sxs-lookup"><span data-stu-id="9a068-141">For example, `Newtonsoft.Json` accepts the following JSON:</span></span>

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

<span data-ttu-id="9a068-142">`System.Text.Json` 只接受以雙引號括住的屬性名稱和字串值，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格需要該格式，而且是唯一視為有效 JSON 的格式。</span><span class="sxs-lookup"><span data-stu-id="9a068-142">`System.Text.Json` only accepts property names and string values in double quotes because that format is required by the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification and is the only format considered valid JSON.</span></span>

<span data-ttu-id="9a068-143">以單引號括住的值會產生含有下列訊息的[JsonException](xref:System.Text.Json.JsonException) ：</span><span class="sxs-lookup"><span data-stu-id="9a068-143">A value enclosed in single quotes results in a [JsonException](xref:System.Text.Json.JsonException) with the following message:</span></span>

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a><span data-ttu-id="9a068-144">字串屬性的非字串值</span><span class="sxs-lookup"><span data-stu-id="9a068-144">Non-string values for string properties</span></span>

<span data-ttu-id="9a068-145">`Newtonsoft.Json` 接受非字串值，例如數位或常值 `true` 和 `false`，以還原序列化為 string 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-145">`Newtonsoft.Json` accepts non-string values, such as a number or the literals `true` and `false`, for deserialization to properties of type string.</span></span> <span data-ttu-id="9a068-146">以下是 `Newtonsoft.Json` 成功還原序列化為下列類別的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="9a068-146">Here's an example of JSON that `Newtonsoft.Json` successfully deserializes to the following class:</span></span>

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

<span data-ttu-id="9a068-147">`System.Text.Json` 不會將非字串值還原序列化為字串屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-147">`System.Text.Json` doesn't deserialize non-string values into string properties.</span></span> <span data-ttu-id="9a068-148">針對字串欄位接收的非字串值會導致[JsonException](xref:System.Text.Json.JsonException) ，並出現下列訊息：</span><span class="sxs-lookup"><span data-stu-id="9a068-148">A non-string value received for a string field results in a [JsonException](xref:System.Text.Json.JsonException) with the following message:</span></span>

```
The JSON value could not be converted to System.String.
```

### <a name="converter-registration-precedence"></a><span data-ttu-id="9a068-149">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="9a068-149">Converter registration precedence</span></span>

<span data-ttu-id="9a068-150">自訂轉換器的 `Newtonsoft.Json` 註冊優先順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a068-150">The `Newtonsoft.Json` registration precedence for custom converters is as follows:</span></span>

* <span data-ttu-id="9a068-151">屬性上的屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-151">Attribute on property</span></span>
* <span data-ttu-id="9a068-152">類型上的屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-152">Attribute on type</span></span>
* <span data-ttu-id="9a068-153">[轉換器](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)集合</span><span class="sxs-lookup"><span data-stu-id="9a068-153">[Converters](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) collection</span></span>

<span data-ttu-id="9a068-154">此順序表示 `Converters` 集合中的自訂轉換器會由在類型層級套用屬性所註冊的轉換器覆寫。</span><span class="sxs-lookup"><span data-stu-id="9a068-154">This order means that a custom converter in the `Converters` collection is overridden by a converter that is registered by applying an attribute at the type level.</span></span> <span data-ttu-id="9a068-155">這兩種註冊都是由屬性層級的屬性所覆寫。</span><span class="sxs-lookup"><span data-stu-id="9a068-155">Both of those registrations are overridden by an attribute at the property level.</span></span>

<span data-ttu-id="9a068-156">自訂轉換器的 <xref:System.Text.Json> 註冊優先順序不同：</span><span class="sxs-lookup"><span data-stu-id="9a068-156">The <xref:System.Text.Json> registration precedence for custom converters is different:</span></span>

* <span data-ttu-id="9a068-157">屬性上的屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-157">Attribute on property</span></span>
* <span data-ttu-id="9a068-158"><xref:System.Text.Json.JsonSerializerOptions.Converters> 集合</span><span class="sxs-lookup"><span data-stu-id="9a068-158"><xref:System.Text.Json.JsonSerializerOptions.Converters> collection</span></span>
* <span data-ttu-id="9a068-159">類型上的屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-159">Attribute on type</span></span>

<span data-ttu-id="9a068-160">此處的差異在於，`Converters` 集合中的自訂轉換器會覆寫類型層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-160">The difference here is that a custom converter in the `Converters` collection overrides an attribute at the type level.</span></span> <span data-ttu-id="9a068-161">此優先順序的目的是要讓執行時間變更覆寫設計階段的選擇。</span><span class="sxs-lookup"><span data-stu-id="9a068-161">The intention behind this order of precedence is to make run-time changes override design-time choices.</span></span> <span data-ttu-id="9a068-162">沒有任何方法可以變更優先順序。</span><span class="sxs-lookup"><span data-stu-id="9a068-162">There's no way to change the precedence.</span></span>

<span data-ttu-id="9a068-163">如需自訂轉換器註冊的詳細資訊，請參閱[註冊自訂轉換子](system-text-json-converters-how-to.md#register-a-custom-converter)。</span><span class="sxs-lookup"><span data-stu-id="9a068-163">For more information about custom converter registration, see [Register a custom converter](system-text-json-converters-how-to.md#register-a-custom-converter).</span></span>

### <a name="character-escaping"></a><span data-ttu-id="9a068-164">字元轉義</span><span class="sxs-lookup"><span data-stu-id="9a068-164">Character escaping</span></span>

<span data-ttu-id="9a068-165">在序列化期間，`Newtonsoft.Json` 相對於讓字元通過，而不將它們進行轉義，是相當寬鬆的。</span><span class="sxs-lookup"><span data-stu-id="9a068-165">During serialization, `Newtonsoft.Json` is relatively permissive about letting characters through without escaping them.</span></span> <span data-ttu-id="9a068-166">也就是說，它不會將它們取代為 `\uxxxx`，其中 `xxxx` 是字元的程式碼點。</span><span class="sxs-lookup"><span data-stu-id="9a068-166">That is, it doesn't replace them with `\uxxxx` where `xxxx` is the character's code point.</span></span> <span data-ttu-id="9a068-167">它會在其中進行 escape，而是在字元之前發出 `\` （例如，`"` 變成 `\"`）。</span><span class="sxs-lookup"><span data-stu-id="9a068-167">Where it does escape them, it does so by emitting a `\` before the character (for example, `"` becomes `\"`).</span></span> <span data-ttu-id="9a068-168"><xref:System.Text.Json> 預設會將更多字元加上轉義，以針對跨網站腳本（XSS）或資訊洩漏攻擊提供深度防禦保護，並使用六個字元的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="9a068-168"><xref:System.Text.Json> escapes more characters by default to provide defense-in-depth protections against cross-site scripting (XSS) or information-disclosure attacks and does so by using the six-character sequence.</span></span> <span data-ttu-id="9a068-169">`System.Text.Json` 預設會將所有非 ASCII 字元加上轉義，因此如果您在 `Newtonsoft.Json`中使用 `StringEscapeHandling.EscapeNonAscii`，就不需要執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="9a068-169">`System.Text.Json` escapes all non-ASCII characters by default, so you don't need to do anything if you're using `StringEscapeHandling.EscapeNonAscii` in `Newtonsoft.Json`.</span></span> <span data-ttu-id="9a068-170">根據預設，`System.Text.Json` 也會對 HTML 敏感字元進行轉義。</span><span class="sxs-lookup"><span data-stu-id="9a068-170">`System.Text.Json` also escapes HTML-sensitive characters, by default.</span></span> <span data-ttu-id="9a068-171">如需如何覆寫預設 `System.Text.Json` 行為的詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="9a068-171">For information about how to override the default `System.Text.Json` behavior, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="deserialization-of-object-properties"></a><span data-ttu-id="9a068-172">物件屬性的還原序列化</span><span class="sxs-lookup"><span data-stu-id="9a068-172">Deserialization of object properties</span></span>

<span data-ttu-id="9a068-173">當 `Newtonsoft.Json` 還原序列化為 Poco 中的 `object` 屬性或類型 `Dictionary<string, object>`的字典中，它會：</span><span class="sxs-lookup"><span data-stu-id="9a068-173">When `Newtonsoft.Json` deserializes to `object` properties in POCOs or in dictionaries of type `Dictionary<string, object>`, it:</span></span>

* <span data-ttu-id="9a068-174">推斷 JSON 承載中基本值的類型（不是 `null`），並傳回儲存的 `string`、`long`、`double`、`boolean`或 `DateTime` 做為已封裝的物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-174">Infers the type of primitive values in the JSON payload (other than `null`) and returns the stored `string`, `long`, `double`, `boolean`, or `DateTime` as a boxed object.</span></span> <span data-ttu-id="9a068-175">*基本值*是單一 json 值，例如 json 數位、字串、`true`、`false`或 `null`。</span><span class="sxs-lookup"><span data-stu-id="9a068-175">*Primitive values* are single JSON values such as a JSON number, string, `true`, `false`, or `null`.</span></span>
* <span data-ttu-id="9a068-176">傳回 JSON 承載中複雜值的 `JObject` 或 `JArray`。</span><span class="sxs-lookup"><span data-stu-id="9a068-176">Returns a `JObject` or `JArray` for complex values in the JSON payload.</span></span> <span data-ttu-id="9a068-177">*複雜值*是以括弧（`{}`）括住的 JSON 索引鍵/值組集合，或是以方括弧（`[]`）括住的值清單。</span><span class="sxs-lookup"><span data-stu-id="9a068-177">*Complex values* are collections of JSON key-value pairs within braces (`{}`) or lists of values within brackets (`[]`).</span></span> <span data-ttu-id="9a068-178">大括弧或括弧內的屬性和值可以有額外的屬性或值。</span><span class="sxs-lookup"><span data-stu-id="9a068-178">The properties and values within the braces or brackets can have additional properties or values.</span></span>
* <span data-ttu-id="9a068-179">當裝載具有 `null` 的 JSON 常值時，會傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="9a068-179">Returns a null reference when the payload has the `null` JSON literal.</span></span>

<span data-ttu-id="9a068-180"><xref:System.Text.Json> 會在 `System.Object` 屬性或字典值中，儲存基本和複雜值的已裝箱 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="9a068-180"><xref:System.Text.Json> stores a boxed `JsonElement` for both primitive and complex values within the `System.Object` property or dictionary value.</span></span> <span data-ttu-id="9a068-181">不過，它會將 `null` 視為 `Newtonsoft.Json`，並在裝載具有 `null` 的 JSON 常值時傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="9a068-181">However, it treats `null` the same as `Newtonsoft.Json` and returns a null reference when the payload has the `null` JSON literal in it.</span></span>

<span data-ttu-id="9a068-182">若要執行 `object` 屬性的型別推斷，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-182">To implement type inference for `object` properties, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).</span></span>

### <a name="maximum-depth"></a><span data-ttu-id="9a068-183">最大深度</span><span class="sxs-lookup"><span data-stu-id="9a068-183">Maximum depth</span></span>

<span data-ttu-id="9a068-184">`Newtonsoft.Json` 預設不具有最大深度限制。</span><span class="sxs-lookup"><span data-stu-id="9a068-184">`Newtonsoft.Json` doesn't have a maximum depth limit by default.</span></span> <span data-ttu-id="9a068-185">針對 <xref:System.Text.Json>，預設限制為64，且可透過設定 <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>加以設定。</span><span class="sxs-lookup"><span data-stu-id="9a068-185">For <xref:System.Text.Json> there's a default limit  of 64, and it's configurable by setting <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.</span></span>

### <a name="stack-type-handling"></a><span data-ttu-id="9a068-186">堆疊類型處理</span><span class="sxs-lookup"><span data-stu-id="9a068-186">Stack type handling</span></span>

<span data-ttu-id="9a068-187">在 <xref:System.Text.Json>中，堆疊內容序列化時，它的順序會反轉。</span><span class="sxs-lookup"><span data-stu-id="9a068-187">In <xref:System.Text.Json>, the order of a stack's contents is reversed when it's serialized.</span></span> <span data-ttu-id="9a068-188">這個行為適用于下列類型和介面，以及從它們衍生的使用者定義類型：</span><span class="sxs-lookup"><span data-stu-id="9a068-188">This behavior applies to the following types and interface and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="9a068-189">您可以實作為自訂轉換器，以相同的順序保留堆疊內容。</span><span class="sxs-lookup"><span data-stu-id="9a068-189">A custom converter could be implemented to keep stack contents in the same order.</span></span>

### <a name="omit-null-value-properties"></a><span data-ttu-id="9a068-190">省略 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-190">Omit null-value properties</span></span>

<span data-ttu-id="9a068-191">`Newtonsoft.Json` 有一個全域設定，會導致從序列化中排除 null 值屬性： [NullValueHandling。 Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm)。</span><span class="sxs-lookup"><span data-stu-id="9a068-191">`Newtonsoft.Json` has a global setting that causes null-value properties to be excluded from serialization: [NullValueHandling.Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm).</span></span> <span data-ttu-id="9a068-192"><xref:System.Text.Json> 中的對應選項是 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>。</span><span class="sxs-lookup"><span data-stu-id="9a068-192">The corresponding option in <xref:System.Text.Json> is <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>.</span></span>

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a><span data-ttu-id="9a068-193">使用需要因應措施之 JsonSerializer 的案例</span><span class="sxs-lookup"><span data-stu-id="9a068-193">Scenarios using JsonSerializer that require workarounds</span></span>

<span data-ttu-id="9a068-194">內建功能不支援下列案例，但會針對因應措施提供範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="9a068-194">The following scenarios aren't supported by built-in functionality, but sample code is provided for workarounds.</span></span> <span data-ttu-id="9a068-195">大部分的因應措施需要您執行[自訂的轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="9a068-195">Most of the workarounds require that you implement [custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="specify-date-format"></a><span data-ttu-id="9a068-196">指定日期格式</span><span class="sxs-lookup"><span data-stu-id="9a068-196">Specify date format</span></span>

<span data-ttu-id="9a068-197">`Newtonsoft.Json` 提供數種方式來控制 `DateTime` 和 `DateTimeOffset` 類型的屬性如何序列化和還原序列化：</span><span class="sxs-lookup"><span data-stu-id="9a068-197">`Newtonsoft.Json` provides several ways to control how properties of `DateTime` and `DateTimeOffset` types are serialized and deserialized:</span></span>

* <span data-ttu-id="9a068-198">`DateTimeZoneHandling` 設定可以用來將所有 `DateTime` 值序列化為 UTC 日期。</span><span class="sxs-lookup"><span data-stu-id="9a068-198">The `DateTimeZoneHandling` setting can be used to serialize all `DateTime` values as UTC dates.</span></span>
* <span data-ttu-id="9a068-199">`DateFormatString` 設定和 `DateTime` 轉換器可以用來自訂日期字串的格式。</span><span class="sxs-lookup"><span data-stu-id="9a068-199">The `DateFormatString` setting and `DateTime` converters can be used to customize the format of date strings.</span></span>

<span data-ttu-id="9a068-200">在 <xref:System.Text.Json>中，具有內建支援的唯一格式是 ISO 8601-1:2019，因為它廣泛採用、明確，並會精確地進行往返。</span><span class="sxs-lookup"><span data-stu-id="9a068-200">In <xref:System.Text.Json>, the only format that has built-in support is ISO 8601-1:2019 since it's widely adopted, unambiguous, and makes round trips precisely.</span></span> <span data-ttu-id="9a068-201">若要使用任何其他格式，請建立自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-201">To use any other format, create a custom converter.</span></span> <span data-ttu-id="9a068-202">如需詳細資訊，請參閱[system.object 中的 DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)。</span><span class="sxs-lookup"><span data-stu-id="9a068-202">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>

### <a name="quoted-numbers"></a><span data-ttu-id="9a068-203">加上引號的數位</span><span class="sxs-lookup"><span data-stu-id="9a068-203">Quoted numbers</span></span>

<span data-ttu-id="9a068-204">`Newtonsoft.Json` 可以序列化或還原序列化 JSON 字串所代表的數位（以引號括住）。</span><span class="sxs-lookup"><span data-stu-id="9a068-204">`Newtonsoft.Json` can serialize or deserialize numbers represented by JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="9a068-205">例如，它可以接受： `{"DegreesCelsius":"23"}`，而不是 `{"DegreesCelsius":23}`。</span><span class="sxs-lookup"><span data-stu-id="9a068-205">For example, it can accept: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="9a068-206">若要在 <xref:System.Text.Json>中啟用該行為，請執行如下列範例所示的自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-206">To enable that behavior in <xref:System.Text.Json>, implement a custom converter like the following example.</span></span> <span data-ttu-id="9a068-207">轉換器會處理定義為 `long`的屬性：</span><span class="sxs-lookup"><span data-stu-id="9a068-207">The converter handles properties defined as `long`:</span></span>

* <span data-ttu-id="9a068-208">它會將它們序列化為 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="9a068-208">It serializes them as JSON strings.</span></span> 
* <span data-ttu-id="9a068-209">它會在還原序列化時，接受引號內的 JSON 數位和數位。</span><span class="sxs-lookup"><span data-stu-id="9a068-209">It accepts JSON numbers and numbers within quotes while deserializing.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

<span data-ttu-id="9a068-210">使用個別 `long` 屬性上的[屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-210">Register this custom converter by [using an attribute](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) on individual `long` properties or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

### <a name="dictionary-with-non-string-key"></a><span data-ttu-id="9a068-211">具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="9a068-211">Dictionary with non-string key</span></span>

<span data-ttu-id="9a068-212">`Newtonsoft.Json` 支援 `Dictionary<TKey, TValue>`類型的集合。</span><span class="sxs-lookup"><span data-stu-id="9a068-212">`Newtonsoft.Json` supports collections of type `Dictionary<TKey, TValue>`.</span></span> <span data-ttu-id="9a068-213"><xref:System.Text.Json> 中的字典集合內建支援僅限於 `Dictionary<string, TValue>`。</span><span class="sxs-lookup"><span data-stu-id="9a068-213">The built-in support for dictionary collections in <xref:System.Text.Json> is limited to `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="9a068-214">也就是，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="9a068-214">That is, the key must be a string.</span></span>

<span data-ttu-id="9a068-215">若要支援具有整數或其他類型做為索引鍵的字典，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-215">To support a dictionary with an integer or some other type as the key, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).</span></span>

### <a name="polymorphic-serialization"></a><span data-ttu-id="9a068-216">多型序列化</span><span class="sxs-lookup"><span data-stu-id="9a068-216">Polymorphic serialization</span></span>

<span data-ttu-id="9a068-217">`Newtonsoft.Json` 會自動進行多型序列化。</span><span class="sxs-lookup"><span data-stu-id="9a068-217">`Newtonsoft.Json` automatically does polymorphic serialization.</span></span> <span data-ttu-id="9a068-218">如需 <xref:System.Text.Json>的有限多型序列化功能的相關資訊，請參閱[序列化衍生類別的屬性](system-text-json-how-to.md#serialize-properties-of-derived-classes)。</span><span class="sxs-lookup"><span data-stu-id="9a068-218">For information about the limited polymorphic serialization capabilities of <xref:System.Text.Json>, see [Serialize properties of derived classes](system-text-json-how-to.md#serialize-properties-of-derived-classes).</span></span>

<span data-ttu-id="9a068-219">此處所述的因應措施，是定義可能包含衍生類別的屬性，做為 `object`的型別。</span><span class="sxs-lookup"><span data-stu-id="9a068-219">The workaround described there is to define properties that may contain derived classes as type `object`.</span></span> <span data-ttu-id="9a068-220">如果無法這樣做，另一個選項是使用整個繼承類型階層的 `Write` 方法建立轉換器，如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="9a068-220">If that isn't possible, another option is to create a converter with a `Write` method for the whole inheritance type hierarchy like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

### <a name="polymorphic-deserialization"></a><span data-ttu-id="9a068-221">多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="9a068-221">Polymorphic deserialization</span></span>

<span data-ttu-id="9a068-222">`Newtonsoft.Json` 具有 `TypeNameHandling` 設定，會在序列化時將類型名稱中繼資料新增至 JSON。</span><span class="sxs-lookup"><span data-stu-id="9a068-222">`Newtonsoft.Json` has a `TypeNameHandling` setting that adds type name metadata to the JSON while serializing.</span></span> <span data-ttu-id="9a068-223">它會在還原序列化時使用中繼資料來執行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9a068-223">It uses the metadata while deserializing to do polymorphic deserialization.</span></span> <span data-ttu-id="9a068-224"><xref:System.Text.Json> 可以執行有限範圍的多型序列化，但不能進行多型的還原[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)。</span><span class="sxs-lookup"><span data-stu-id="9a068-224"><xref:System.Text.Json> can do a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but not polymorphic deserialization.</span></span>

<span data-ttu-id="9a068-225">若要支援多型還原序列化，請建立如[如何撰寫自訂轉換器](system-text-json-converters-how-to.md#support-polymorphic-deserialization)中的範例所示的轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-225">To support polymorphic deserialization, create a converter like the example in [How to write custom converters](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

### <a name="required-properties"></a><span data-ttu-id="9a068-226">必要屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-226">Required properties</span></span>

<span data-ttu-id="9a068-227">在還原序列化期間，如果目標型別的其中一個屬性未在 JSON 中收到任何值，則 <xref:System.Text.Json> 不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-227">During deserialization, <xref:System.Text.Json> doesn't throw an exception if no value is received in the JSON for one of the properties of the target type.</span></span> <span data-ttu-id="9a068-228">例如，如果您有 `WeatherForecast` 類別：</span><span class="sxs-lookup"><span data-stu-id="9a068-228">For example, if you have a `WeatherForecast` class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="9a068-229">下列 JSON 會進行還原序列化，而不會發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="9a068-229">The following JSON is deserialized without error:</span></span>

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

<span data-ttu-id="9a068-230">若要讓還原序列化失敗，如果 JSON 中沒有 `Date` 的屬性，請執行自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-230">To make deserialization fail if no `Date` property is in the JSON, implement a custom converter.</span></span> <span data-ttu-id="9a068-231">如果在還原序列化完成後未設定 `Date` 屬性，下列範例轉換器程式碼會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="9a068-231">The following sample converter code throws an exception if the `Date` property isn't set after deserialization is complete:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

<span data-ttu-id="9a068-232">藉由[使用 POCO 類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-232">Register this custom converter by [using an attribute on the POCO class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="9a068-233">如果您遵循此模式，請不要在以遞迴方式呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 或 <xref:System.Text.Json.JsonSerializer.Deserialize%2A>時傳入 options 物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-233">If you follow this pattern, don't pass in the options object when recursively calling <xref:System.Text.Json.JsonSerializer.Serialize%2A> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A>.</span></span> <span data-ttu-id="9a068-234">Options 物件包含 <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="9a068-234">The options object contains the <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> collection.</span></span> <span data-ttu-id="9a068-235">如果您將它傳遞給 `Serialize` 或 `Deserialize`，則自訂轉換器會呼叫自己的，因此會產生無限迴圈，導致堆疊溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-235">If you pass it in to `Serialize` or `Deserialize`, the custom converter calls into itself, making an infinite loop that results in a stack overflow exception.</span></span> <span data-ttu-id="9a068-236">如果預設選項不可行，請使用您所需的設定來建立選項的新實例。</span><span class="sxs-lookup"><span data-stu-id="9a068-236">If the default options are not feasible, create a new instance of the options with the settings that you need.</span></span> <span data-ttu-id="9a068-237">這個方法將會變慢，因為每個新的實例會獨立快取。</span><span class="sxs-lookup"><span data-stu-id="9a068-237">This approach will be slow since each new instance caches independently.</span></span>

<span data-ttu-id="9a068-238">上述的轉換器程式碼是簡化的範例。</span><span class="sxs-lookup"><span data-stu-id="9a068-238">The preceding converter code is a simplified example.</span></span> <span data-ttu-id="9a068-239">如果您需要處理屬性（例如[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)或不同的選項（例如自訂編碼器），則需要額外的邏輯。</span><span class="sxs-lookup"><span data-stu-id="9a068-239">Additional logic would be required if you need to handle attributes (such as [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) or different options (such as custom encoders).</span></span> <span data-ttu-id="9a068-240">此外，範例程式碼不會處理在此函式中設定預設值的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-240">Also, the example code doesn't handle properties for which a default value is set in the constructor.</span></span> <span data-ttu-id="9a068-241">而這種方法不會區分下列案例：</span><span class="sxs-lookup"><span data-stu-id="9a068-241">And this approach doesn't differentiate between the following scenarios:</span></span>

* <span data-ttu-id="9a068-242">JSON 中遺漏了屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-242">A property is missing from the JSON.</span></span>
* <span data-ttu-id="9a068-243">JSON 中有不可為 null 類型的屬性，但此值是類型的預設值，例如零代表 `int`。</span><span class="sxs-lookup"><span data-stu-id="9a068-243">A property for a non-nullable type is present in the JSON, but the value is the default for the type, such as zero for an `int`.</span></span>
* <span data-ttu-id="9a068-244">JSON 中有可為 null 類型的屬性，但值為 null。</span><span class="sxs-lookup"><span data-stu-id="9a068-244">A property for a nullable type is present in the JSON, but the value is null.</span></span>

### <a name="deserialize-null-to-non-nullable-type"></a><span data-ttu-id="9a068-245">將 null 還原序列化為不可為 null 的類型</span><span class="sxs-lookup"><span data-stu-id="9a068-245">Deserialize null to non-nullable type</span></span> 

<span data-ttu-id="9a068-246">`Newtonsoft.Json` 在下列案例中不會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="9a068-246">`Newtonsoft.Json` doesn't throw an exception in the following scenario:</span></span>

* <span data-ttu-id="9a068-247">`NullValueHandling` 設定為 `Ignore`，而</span><span class="sxs-lookup"><span data-stu-id="9a068-247">`NullValueHandling` is set to `Ignore`, and</span></span>
* <span data-ttu-id="9a068-248">在還原序列化期間，JSON 會針對不可為 null 的型別包含 null 值。</span><span class="sxs-lookup"><span data-stu-id="9a068-248">During deserialization, the JSON contains a null value for a non-nullable type.</span></span>

<span data-ttu-id="9a068-249">在相同的案例中，<xref:System.Text.Json> 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-249">In the same scenario, <xref:System.Text.Json> does throw an exception.</span></span> <span data-ttu-id="9a068-250">（對應的 null 處理設定為 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="9a068-250">(The corresponding null handling setting is <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)</span></span>

<span data-ttu-id="9a068-251">如果您擁有目標型別，最佳的解決方法是讓屬性成為可為 null （例如，將 `int` 變更為 `int?`）。</span><span class="sxs-lookup"><span data-stu-id="9a068-251">If you own the target type, the best workaround is to make the property in question nullable (for example, change `int` to `int?`).</span></span>

<span data-ttu-id="9a068-252">另一個因應措施是建立類型的轉換器，例如下列範例，其會處理 `DateTimeOffset` 類型的 null 值：</span><span class="sxs-lookup"><span data-stu-id="9a068-252">Another workaround is to make a converter for the type, such as the following example that handles null values for `DateTimeOffset` types:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

<span data-ttu-id="9a068-253">藉由[使用屬性上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-253">Register this custom converter by [using an attribute on the property](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="9a068-254">**注意：** 前面的轉換子**處理 null 值的方式**，與指定預設值的 poco 不同 `Newtonsoft.Json`。</span><span class="sxs-lookup"><span data-stu-id="9a068-254">**Note:** The preceding converter **handles null values differently** than `Newtonsoft.Json` does for POCOs that specify default values.</span></span> <span data-ttu-id="9a068-255">例如，假設下列程式碼代表您的目標物件：</span><span class="sxs-lookup"><span data-stu-id="9a068-255">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="9a068-256">而且假設下列 JSON 會使用上述的轉換器還原序列化：</span><span class="sxs-lookup"><span data-stu-id="9a068-256">And suppose the following JSON is deserialized by using the preceding converter:</span></span>

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="9a068-257">還原序列化之後，`Date` 屬性具有1/1/0001 （`default(DateTimeOffset)`），也就是會覆寫在此函式中設定的值。</span><span class="sxs-lookup"><span data-stu-id="9a068-257">After deserialization, the `Date` property has 1/1/0001 (`default(DateTimeOffset)`), that is, the value set in the constructor is overwritten.</span></span> <span data-ttu-id="9a068-258">假設有相同的 POCO 和 JSON，`Newtonsoft.Json` 還原序列化會在 `Date` 屬性中留下1/1/2001。</span><span class="sxs-lookup"><span data-stu-id="9a068-258">Given the same POCO and JSON, `Newtonsoft.Json` deserialization would leave 1/1/2001 in the `Date` property.</span></span>

### <a name="deserialize-to-immutable-classes-and-structs"></a><span data-ttu-id="9a068-259">還原序列化為不可變的類別和結構</span><span class="sxs-lookup"><span data-stu-id="9a068-259">Deserialize to immutable classes and structs</span></span>

<span data-ttu-id="9a068-260">`Newtonsoft.Json` 可以還原序列化為不可變的類別和結構，因為它可以使用具有參數的函數。</span><span class="sxs-lookup"><span data-stu-id="9a068-260">`Newtonsoft.Json` can deserialize to immutable classes and structs because it can use constructors that have parameters.</span></span> <span data-ttu-id="9a068-261"><xref:System.Text.Json> 僅支援公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="9a068-261"><xref:System.Text.Json> supports only public parameterless constructors.</span></span> <span data-ttu-id="9a068-262">因應措施是，您可以在自訂轉換子中呼叫具有參數的函式。</span><span class="sxs-lookup"><span data-stu-id="9a068-262">As a workaround, you can call a constructor with parameters in a custom converter.</span></span>

<span data-ttu-id="9a068-263">以下是具有多個函數參數的不可變結構：</span><span class="sxs-lookup"><span data-stu-id="9a068-263">Here's an immutable struct with multiple constructor parameters:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

<span data-ttu-id="9a068-264">以下是將此結構序列化和還原序列化的轉換器：</span><span class="sxs-lookup"><span data-stu-id="9a068-264">And here's a converter that serializes and deserializes this struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

<span data-ttu-id="9a068-265">[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，以註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-265">Register this custom converter by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="9a068-266">如需處理開放式泛型屬性之類似轉換器的範例，請參閱索引[鍵/值組的內建轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)。</span><span class="sxs-lookup"><span data-stu-id="9a068-266">For an example of a similar converter that handles open generic properties, see the [built-in converter for key-value pairs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).</span></span>

### <a name="specify-constructor-to-use"></a><span data-ttu-id="9a068-267">指定要使用的構造函式</span><span class="sxs-lookup"><span data-stu-id="9a068-267">Specify constructor to use</span></span>

<span data-ttu-id="9a068-268">`Newtonsoft.Json` `[JsonConstructor]` 屬性可讓您指定在還原序列化為 POCO 時要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="9a068-268">The `Newtonsoft.Json` `[JsonConstructor]` attribute lets you specify which constructor to call when deserializing to a POCO.</span></span> <span data-ttu-id="9a068-269"><xref:System.Text.Json> 僅支援無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="9a068-269"><xref:System.Text.Json> supports only parameterless constructors.</span></span> <span data-ttu-id="9a068-270">因應措施是，您可以在自訂轉換器中呼叫所需的任何一個方法。</span><span class="sxs-lookup"><span data-stu-id="9a068-270">As a workaround, you can call whichever constructor you need in a custom converter.</span></span> <span data-ttu-id="9a068-271">請參閱還原序列化[為不可變類別和結構](#deserialize-to-immutable-classes-and-structs)的範例。</span><span class="sxs-lookup"><span data-stu-id="9a068-271">See the example for [Deserialize to immutable classes and structs](#deserialize-to-immutable-classes-and-structs).</span></span>

### <a name="conditionally-ignore-a-property"></a><span data-ttu-id="9a068-272">有條件地忽略屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-272">Conditionally ignore a property</span></span>

<span data-ttu-id="9a068-273">`Newtonsoft.Json` 有數種方式可以有條件地忽略序列化或還原序列化上的屬性：</span><span class="sxs-lookup"><span data-stu-id="9a068-273">`Newtonsoft.Json` has several ways to conditionally ignore a property on serialization or deserialization:</span></span>

* <span data-ttu-id="9a068-274">`DefaultContractResolver` 可讓您根據任意條件，選取要包含或排除的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-274">`DefaultContractResolver` lets you select properties to include or exclude, based on arbitrary criteria.</span></span> 
* <span data-ttu-id="9a068-275">`JsonSerializerSettings` 上的 `NullValueHandling` 和 `DefaultValueHandling` 設定，可讓您指定應該忽略所有的 null 值或預設值屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-275">The `NullValueHandling` and `DefaultValueHandling` settings on `JsonSerializerSettings` let you specify that all null-value or default-value properties should be ignored.</span></span>
* <span data-ttu-id="9a068-276">[`[JsonProperty]`] 屬性上的 [`NullValueHandling`] 和 [`DefaultValueHandling`] 設定可讓您指定在設定為 null 或預設值時，應該忽略的個別屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-276">The `NullValueHandling` and `DefaultValueHandling` settings on the `[JsonProperty]` attribute let you specify individual properties that should be ignored when set to null or the default value.</span></span>

<span data-ttu-id="9a068-277"><xref:System.Text.Json> 提供下列方法來在序列化時省略屬性：</span><span class="sxs-lookup"><span data-stu-id="9a068-277"><xref:System.Text.Json> provides the following ways to omit properties while serializing:</span></span>

* <span data-ttu-id="9a068-278">屬性[（property）上的 [JsonIgnore] 屬性（attribute）](system-text-json-how-to.md#exclude-individual-properties)會在序列化期間，從 JSON 中省略屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="9a068-278">The [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) attribute on a property causes the property to be omitted from the JSON during serialization.</span></span>
* <span data-ttu-id="9a068-279">[IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global 選項可讓您排除所有 null 值屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-279">The [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global option lets you exclude all null-value properties.</span></span>
* <span data-ttu-id="9a068-280">[IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global 選項可讓您排除所有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-280">The [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global option lets you exclude all read-only properties.</span></span>

<span data-ttu-id="9a068-281">這些選項**不**會讓您：</span><span class="sxs-lookup"><span data-stu-id="9a068-281">These options **don't** let you:</span></span>

* <span data-ttu-id="9a068-282">忽略所有具有類型之預設值的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-282">Ignore all properties that have the default value for the type.</span></span>
* <span data-ttu-id="9a068-283">忽略具有類型之預設值的選取屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-283">Ignore selected properties that have the default value for the type.</span></span>
* <span data-ttu-id="9a068-284">如果其值為 null，則忽略選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-284">Ignore selected properties if their value is null.</span></span>
* <span data-ttu-id="9a068-285">根據在執行時間評估的任意準則，忽略選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-285">Ignore selected properties based on arbitrary criteria evaluated at run time.</span></span> 

<span data-ttu-id="9a068-286">針對該功能，您可以撰寫自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-286">For that functionality, you can write a custom converter.</span></span> <span data-ttu-id="9a068-287">以下是範例 POCO 和適用于它的自訂轉換器，其說明此方法：</span><span class="sxs-lookup"><span data-stu-id="9a068-287">Here's a sample POCO and a custom converter for it that illustrates this approach:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

<span data-ttu-id="9a068-288">如果參數的值為 null、空字串或 "N/A"，則轉換器會從序列化中省略 `Summary` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-288">The converter causes the `Summary` property to be omitted from serialization if its value is null, an empty string, or "N/A".</span></span> 

<span data-ttu-id="9a068-289">藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-289">Register this custom converter by [using an attribute on the class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="9a068-290">這種方法需要額外的邏輯，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a068-290">This approach requires additional logic if:</span></span>

* <span data-ttu-id="9a068-291">POCO 包含複雜的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-291">The POCO includes complex properties.</span></span>
* <span data-ttu-id="9a068-292">您需要處理諸如 `[JsonIgnore]` 或選項（例如自訂編碼器）之類的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-292">You need to handle attributes such as `[JsonIgnore]` or options such as custom encoders.</span></span>

### <a name="callbacks"></a><span data-ttu-id="9a068-293">叫</span><span class="sxs-lookup"><span data-stu-id="9a068-293">Callbacks</span></span>

<span data-ttu-id="9a068-294">`Newtonsoft.Json` 可讓您在序列化或還原序列化程式的數個點執行自訂程式碼：</span><span class="sxs-lookup"><span data-stu-id="9a068-294">`Newtonsoft.Json` lets you execute custom code at several points in the serialization or deserialization process:</span></span>

* <span data-ttu-id="9a068-295">OnDeserializing （開始還原序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="9a068-295">OnDeserializing (when beginning to deserialize an object)</span></span>
* <span data-ttu-id="9a068-296">OnDeserialized （完成還原序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="9a068-296">OnDeserialized (when finished deserializing an object)</span></span>
* <span data-ttu-id="9a068-297">OnSerializing （開始序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="9a068-297">OnSerializing (when beginning to serialize an object)</span></span>
* <span data-ttu-id="9a068-298">OnSerialized （完成序列化物件時）</span><span class="sxs-lookup"><span data-stu-id="9a068-298">OnSerialized (when finished serializing an object)</span></span>

<span data-ttu-id="9a068-299">在 <xref:System.Text.Json>中，您可以藉由撰寫自訂的轉換器來模擬回呼。</span><span class="sxs-lookup"><span data-stu-id="9a068-299">In <xref:System.Text.Json>, you can simulate callbacks by writing a custom converter.</span></span> <span data-ttu-id="9a068-300">下列範例顯示 POCO 的自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-300">The following example shows a custom converter for a POCO.</span></span> <span data-ttu-id="9a068-301">轉換器包含的程式碼會在每個對應至 `Newtonsoft.Json` 回呼的時間點顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="9a068-301">The converter includes code that displays a message at each point that corresponds to a `Newtonsoft.Json` callback.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

<span data-ttu-id="9a068-302">藉由[使用類別上的屬性](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)，或[將轉換器加入](system-text-json-converters-how-to.md#registration-sample---converters-collection)至 <xref:System.Text.Json.JsonSerializerOptions.Converters> 集合，來註冊此自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="9a068-302">Register this custom converter by [using an attribute on the class](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) or by [adding the converter](system-text-json-converters-how-to.md#registration-sample---converters-collection) to the <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.</span></span>

<span data-ttu-id="9a068-303">如果您使用遵循上述範例的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="9a068-303">If you use a custom converter that follows the preceding sample:</span></span>

* <span data-ttu-id="9a068-304">`OnDeserializing` 程式碼沒有新 POCO 實例的存取權。</span><span class="sxs-lookup"><span data-stu-id="9a068-304">The `OnDeserializing` code doesn't have access to the new POCO instance.</span></span> <span data-ttu-id="9a068-305">若要在還原序列化開始時操作新的 POCO 實例，請將該程式碼放在 POCO 函式中。</span><span class="sxs-lookup"><span data-stu-id="9a068-305">To manipulate the new POCO instance at the start of deserialization, put that code in the POCO constructor.</span></span>
* <span data-ttu-id="9a068-306">當以遞迴方式呼叫 `Serialize` 或 `Deserialize`時，請勿傳入 options 物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-306">Don't pass in the options object when recursively calling `Serialize` or `Deserialize`.</span></span> <span data-ttu-id="9a068-307">Options 物件包含 `Converters` 集合。</span><span class="sxs-lookup"><span data-stu-id="9a068-307">The options object contains the `Converters` collection.</span></span> <span data-ttu-id="9a068-308">如果您將它傳遞給 `Serialize` 或 `Deserialize`，則會使用轉換器，並產生無限迴圈，而導致堆疊溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-308">If you pass it in to `Serialize` or `Deserialize`, the converter will be used, making an infinite loop that results in a stack overflow exception.</span></span>

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a><span data-ttu-id="9a068-309">JsonSerializer 目前不支援的案例</span><span class="sxs-lookup"><span data-stu-id="9a068-309">Scenarios that JsonSerializer currently doesn't support</span></span>

<span data-ttu-id="9a068-310">因應措施適用于下列案例，但其中一些因應措施可能會相對較難實行。</span><span class="sxs-lookup"><span data-stu-id="9a068-310">Workarounds are possible for the following scenarios, but some of them would be relatively difficult to implement.</span></span> <span data-ttu-id="9a068-311">本文不會針對這些案例提供因應措施的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="9a068-311">This article doesn't provide code samples for workarounds for these scenarios.</span></span>

<span data-ttu-id="9a068-312">這不是 `System.Text.Json`中沒有對等專案之 `Newtonsoft.Json` 功能的詳盡清單。</span><span class="sxs-lookup"><span data-stu-id="9a068-312">This is not an exhaustive list of `Newtonsoft.Json` features that have no equivalents in `System.Text.Json`.</span></span> <span data-ttu-id="9a068-313">此清單包含[GitHub 問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)或[StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json)文章中所要求的許多案例。</span><span class="sxs-lookup"><span data-stu-id="9a068-313">The list includes many of the scenarios that have been requested in [GitHub issues](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) or [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) posts.</span></span>

<span data-ttu-id="9a068-314">如果您為上述其中一個案例實行因應措施，而且可以共用程式碼，請選取頁面底部的 [**此頁面**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a068-314">If you implement a workaround for one of these scenarios and can share the code, select the "**This page**" button at the bottom of the page.</span></span> <span data-ttu-id="9a068-315">這會建立 GitHub 問題，並將其新增至頁面底部所列的問題。</span><span class="sxs-lookup"><span data-stu-id="9a068-315">That creates a GitHub issue and adds it to the issues that are listed at the bottom of the page.</span></span>

### <a name="types-without-built-in-support"></a><span data-ttu-id="9a068-316">沒有內建支援的類型</span><span class="sxs-lookup"><span data-stu-id="9a068-316">Types without built-in support</span></span>

<span data-ttu-id="9a068-317"><xref:System.Text.Json> 不會提供下列類型的內建支援：</span><span class="sxs-lookup"><span data-stu-id="9a068-317"><xref:System.Text.Json> doesn't provide built-in support for the following types:</span></span>

* <span data-ttu-id="9a068-318"><xref:System.Data.DataTable> 和相關類型</span><span class="sxs-lookup"><span data-stu-id="9a068-318"><xref:System.Data.DataTable> and related types</span></span>
* <span data-ttu-id="9a068-319">F#類型，例如[區分](../../fsharp/language-reference/discriminated-unions.md)等位、[記錄類型](../../fsharp/language-reference/records.md)和[匿名記錄類型](../../fsharp/language-reference/anonymous-records.md)。</span><span class="sxs-lookup"><span data-stu-id="9a068-319">F# types, such as [discriminated unions](../../fsharp/language-reference/discriminated-unions.md), [record types](../../fsharp/language-reference/records.md), and [anonymous record types](../../fsharp/language-reference/anonymous-records.md).</span></span>
* <span data-ttu-id="9a068-320"><xref:System.Collections.Specialized> 命名空間中的集合類型</span><span class="sxs-lookup"><span data-stu-id="9a068-320">Collection types in the <xref:System.Collections.Specialized> namespace</span></span>
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <span data-ttu-id="9a068-321"><xref:System.ValueTuple> 和其相關聯的泛型型別</span><span class="sxs-lookup"><span data-stu-id="9a068-321"><xref:System.ValueTuple> and its associated generic types</span></span>

<span data-ttu-id="9a068-322">針對沒有內建支援的類型，可以實作為自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="9a068-322">Custom converters can be implemented for types that don't have built-in support.</span></span>

### <a name="public-and-non-public-fields"></a><span data-ttu-id="9a068-323">公用和非公用欄位</span><span class="sxs-lookup"><span data-stu-id="9a068-323">Public and non-public fields</span></span>

<span data-ttu-id="9a068-324">`Newtonsoft.Json` 可以序列化和還原序列化欄位，以及屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-324">`Newtonsoft.Json` can serialize and deserialize fields as well as properties.</span></span> <span data-ttu-id="9a068-325"><xref:System.Text.Json> 僅適用于公用屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-325"><xref:System.Text.Json> only works with public properties.</span></span> <span data-ttu-id="9a068-326">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="9a068-326">Custom converters can provide this functionality.</span></span>

### <a name="internal-and-private-property-setters-and-getters"></a><span data-ttu-id="9a068-327">內部和私用屬性 setter 和 getter</span><span class="sxs-lookup"><span data-stu-id="9a068-327">Internal and private property setters and getters</span></span>

<span data-ttu-id="9a068-328">`Newtonsoft.Json` 可以透過 `JsonProperty` 屬性來使用私用和內部屬性 setter 和 getter。</span><span class="sxs-lookup"><span data-stu-id="9a068-328">`Newtonsoft.Json` can use private and internal property setters and getters via the `JsonProperty` attribute.</span></span> <span data-ttu-id="9a068-329"><xref:System.Text.Json> 僅支援公用 setter。</span><span class="sxs-lookup"><span data-stu-id="9a068-329"><xref:System.Text.Json> supports only public setters.</span></span> <span data-ttu-id="9a068-330">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="9a068-330">Custom converters can provide this functionality.</span></span>

### <a name="preserve-object-references-and-handle-loops"></a><span data-ttu-id="9a068-331">保留物件參考並處理迴圈</span><span class="sxs-lookup"><span data-stu-id="9a068-331">Preserve object references and handle loops</span></span>

<span data-ttu-id="9a068-332">根據預設，`Newtonsoft.Json` 依值序列化。</span><span class="sxs-lookup"><span data-stu-id="9a068-332">By default, `Newtonsoft.Json` serializes by value.</span></span> <span data-ttu-id="9a068-333">例如，如果物件包含兩個屬性，其中包含相同 `Person` 物件的參考，則該 `Person` 物件屬性的值會在 JSON 中重複。</span><span class="sxs-lookup"><span data-stu-id="9a068-333">For example, if an object contains two properties that contain a reference to the same `Person` object, the values of that `Person` object's properties are duplicated in the JSON.</span></span>

<span data-ttu-id="9a068-334">`Newtonsoft.Json` 在 `JsonSerializerSettings` 上有 `PreserveReferencesHandling` 設定，可讓您以傳址方式序列化：</span><span class="sxs-lookup"><span data-stu-id="9a068-334">`Newtonsoft.Json` has a `PreserveReferencesHandling` setting on `JsonSerializerSettings` that lets you serialize by reference:</span></span>

* <span data-ttu-id="9a068-335">識別碼中繼資料會加入至針對第一個 `Person` 物件所建立的 JSON。</span><span class="sxs-lookup"><span data-stu-id="9a068-335">An identifier metadata is added to the JSON created for the first `Person` object.</span></span>
* <span data-ttu-id="9a068-336">針對第二個 `Person` 物件所建立的 JSON 包含該識別碼的參考，而不是屬性值。</span><span class="sxs-lookup"><span data-stu-id="9a068-336">The JSON that is created for the second `Person` object contains a reference to that identifier instead of property values.</span></span>

<span data-ttu-id="9a068-337">`Newtonsoft.Json` 也有 `ReferenceLoopHandling` 設定，可讓您忽略迴圈參考，而不是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-337">`Newtonsoft.Json` also has a `ReferenceLoopHandling` setting that lets you ignore circular references rather than throw an exception.</span></span>

<span data-ttu-id="9a068-338"><xref:System.Text.Json> 只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-338"><xref:System.Text.Json> only supports serialization by value and throws an exception for circular references.</span></span>

### <a name="systemruntimeserialization-attributes"></a><span data-ttu-id="9a068-339">System.object。序列化屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-339">System.Runtime.Serialization attributes</span></span>

<span data-ttu-id="9a068-340"><xref:System.Text.Json> 不支援來自 `System.Runtime.Serialization` 命名空間的屬性，例如 `DataMemberAttribute` 和 `IgnoreDataMemberAttribute`。</span><span class="sxs-lookup"><span data-stu-id="9a068-340"><xref:System.Text.Json> doesn't support attributes from the `System.Runtime.Serialization` namespace, such as `DataMemberAttribute` and `IgnoreDataMemberAttribute`.</span></span>

### <a name="octal-numbers"></a><span data-ttu-id="9a068-341">八進位數位</span><span class="sxs-lookup"><span data-stu-id="9a068-341">Octal numbers</span></span>

<span data-ttu-id="9a068-342">`Newtonsoft.Json` 會將前置零的數位視為八進位數位。</span><span class="sxs-lookup"><span data-stu-id="9a068-342">`Newtonsoft.Json` treats numbers with a leading zero as octal numbers.</span></span> <span data-ttu-id="9a068-343"><xref:System.Text.Json> 不允許前置零，因為[RFC 8259](https://tools.ietf.org/html/rfc8259)規格不允許它們。</span><span class="sxs-lookup"><span data-stu-id="9a068-343"><xref:System.Text.Json> doesn't allow leading zeroes because the [RFC 8259](https://tools.ietf.org/html/rfc8259) specification doesn't allow them.</span></span>

### <a name="populate-existing-objects"></a><span data-ttu-id="9a068-344">填入現有的物件</span><span class="sxs-lookup"><span data-stu-id="9a068-344">Populate existing objects</span></span>

<span data-ttu-id="9a068-345">中的 `JsonConvert.PopulateObject` 方法 `Newtonsoft.Json` 將 JSON 檔案還原序列化為類別的現有實例，而不是建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="9a068-345">The `JsonConvert.PopulateObject` method in `Newtonsoft.Json` deserializes a JSON document to an existing instance of a class, instead of creating a new instance.</span></span> <span data-ttu-id="9a068-346"><xref:System.Text.Json> 一律會使用預設的公用無參數函式來建立目標型別的新實例。</span><span class="sxs-lookup"><span data-stu-id="9a068-346"><xref:System.Text.Json> always creates a new instance of the target type by using the default public parameterless constructor.</span></span> <span data-ttu-id="9a068-347">自訂轉換器可以還原序列化為現有的實例。</span><span class="sxs-lookup"><span data-stu-id="9a068-347">Custom converters can deserialize to an existing instance.</span></span>

### <a name="reuse-rather-than-replace-properties"></a><span data-ttu-id="9a068-348">重複使用，而不是取代屬性</span><span class="sxs-lookup"><span data-stu-id="9a068-348">Reuse rather than replace properties</span></span>

<span data-ttu-id="9a068-349">[`Newtonsoft.Json` `ObjectCreationHandling`] 設定可讓您指定應該重複使用屬性中的物件，而不是在還原序列化期間加以取代。</span><span class="sxs-lookup"><span data-stu-id="9a068-349">The `Newtonsoft.Json` `ObjectCreationHandling` setting lets you specify that objects in properties should be reused rather than replaced during deserialization.</span></span> <span data-ttu-id="9a068-350"><xref:System.Text.Json> 一律會取代屬性中的物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-350"><xref:System.Text.Json> always replaces objects in properties.</span></span>  <span data-ttu-id="9a068-351">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="9a068-351">Custom converters can provide this functionality.</span></span>

### <a name="add-to-collections-without-setters"></a><span data-ttu-id="9a068-352">新增至不含 setter 的集合</span><span class="sxs-lookup"><span data-stu-id="9a068-352">Add to collections without setters</span></span>

<span data-ttu-id="9a068-353">在還原序列化期間，即使屬性沒有 setter，`Newtonsoft.Json` 也會將物件加入至集合。</span><span class="sxs-lookup"><span data-stu-id="9a068-353">During deserialization, `Newtonsoft.Json` adds objects to a collection even if the property has no setter.</span></span> <span data-ttu-id="9a068-354"><xref:System.Text.Json> 會忽略沒有 setter 的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-354"><xref:System.Text.Json> ignores properties that don't have setters.</span></span> <span data-ttu-id="9a068-355">自訂轉換器可以提供這種功能。</span><span class="sxs-lookup"><span data-stu-id="9a068-355">Custom converters can provide this functionality.</span></span>

### <a name="missingmemberhandling"></a><span data-ttu-id="9a068-356">MissingMemberHandling</span><span class="sxs-lookup"><span data-stu-id="9a068-356">MissingMemberHandling</span></span>

<span data-ttu-id="9a068-357">`Newtonsoft.Json` 可以設定為在還原序列化期間擲回例外狀況（如果 JSON 包含目標型別中遺漏的屬性）。</span><span class="sxs-lookup"><span data-stu-id="9a068-357">`Newtonsoft.Json` can be configured to throw exceptions during deserialization if the JSON includes properties that are missing in the target type.</span></span> <span data-ttu-id="9a068-358"><xref:System.Text.Json> 會忽略 JSON 中的額外屬性，除非您使用[[JsonExtensionData] 屬性](system-text-json-how-to.md#handle-overflow-json)。</span><span class="sxs-lookup"><span data-stu-id="9a068-358"><xref:System.Text.Json> ignores extra properties in the JSON, except when you use the [[JsonExtensionData] attribute](system-text-json-how-to.md#handle-overflow-json).</span></span> <span data-ttu-id="9a068-359">缺少的成員功能沒有因應措施。</span><span class="sxs-lookup"><span data-stu-id="9a068-359">There's no workaround for the missing member feature.</span></span>

### <a name="tracewriter"></a><span data-ttu-id="9a068-360">TraceWriter</span><span class="sxs-lookup"><span data-stu-id="9a068-360">TraceWriter</span></span>

<span data-ttu-id="9a068-361">`Newtonsoft.Json` 可讓您使用 `TraceWriter` 來進行 debug，以查看由序列化或還原序列化所產生的記錄。</span><span class="sxs-lookup"><span data-stu-id="9a068-361">`Newtonsoft.Json` lets you debug by using a `TraceWriter` to view logs that are generated by serialization or deserialization.</span></span> <span data-ttu-id="9a068-362"><xref:System.Text.Json> 不會進行記錄。</span><span class="sxs-lookup"><span data-stu-id="9a068-362"><xref:System.Text.Json> doesn't do logging.</span></span>

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a><span data-ttu-id="9a068-363">相較于 JToken 的 JsonDocument 和 JsonElement （例如 JObject、JArray）</span><span class="sxs-lookup"><span data-stu-id="9a068-363">JsonDocument and JsonElement compared to JToken (like JObject, JArray)</span></span>

<span data-ttu-id="9a068-364"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供從現有 JSON 承載剖析和建立**唯讀**檔物件模型（DOM）的功能。</span><span class="sxs-lookup"><span data-stu-id="9a068-364"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to parse and build a **read-only** Document Object Model (DOM) from existing JSON payloads.</span></span> <span data-ttu-id="9a068-365">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="9a068-365">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="9a068-366">組成裝載的 JSON 元素可以透過 <xref:System.Text.Json.JsonElement> 類型來存取。</span><span class="sxs-lookup"><span data-stu-id="9a068-366">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="9a068-367">`JsonElement` 類型會提供 Api，將 JSON 文字轉換成常見的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9a068-367">The `JsonElement` type provides APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="9a068-368">`JsonDocument` 會公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9a068-368">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

### <a name="jsondocument-is-idisposable"></a><span data-ttu-id="9a068-369">JsonDocument 是 IDisposable</span><span class="sxs-lookup"><span data-stu-id="9a068-369">JsonDocument is IDisposable</span></span>

<span data-ttu-id="9a068-370">`JsonDocument` 會將資料的記憶體中視圖建立成集區緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9a068-370">`JsonDocument` builds an in-memory view of the data into a pooled buffer.</span></span> <span data-ttu-id="9a068-371">因此，不同于 `Newtonsoft.Json`的 `JObject` 或 `JArray`，`JsonDocument` 型別會執行 `IDisposable`，而且必須在 using 區塊內使用。</span><span class="sxs-lookup"><span data-stu-id="9a068-371">Therefore, unlike `JObject` or `JArray` from `Newtonsoft.Json`, the `JsonDocument` type implements `IDisposable` and needs to be used inside a using block.</span></span> 

<span data-ttu-id="9a068-372">如果您想要將存留期擁有權和處置責任轉移給呼叫者，只會從您的 API 傳回 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="9a068-372">Only return a `JsonDocument` from your API if you want to transfer lifetime ownership and dispose responsibility to the caller.</span></span> <span data-ttu-id="9a068-373">在大部分的情況下，這並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="9a068-373">In most scenarios, that isn't necessary.</span></span> <span data-ttu-id="9a068-374">如果呼叫端需要使用整個 JSON 檔，則會傳回 <xref:System.Text.Json.JsonDocument.RootElement%2A>的 <xref:System.Text.Json.JsonElement.Clone%2A>，也就是 <xref:System.Text.Json.JsonElement>。</span><span class="sxs-lookup"><span data-stu-id="9a068-374">If the caller needs to work with the entire JSON document, return the <xref:System.Text.Json.JsonElement.Clone%2A> of the <xref:System.Text.Json.JsonDocument.RootElement%2A>, which is a <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="9a068-375">如果呼叫端需要使用 JSON 檔中的特定元素，則會傳回該 <xref:System.Text.Json.JsonElement>的 <xref:System.Text.Json.JsonElement.Clone%2A>。</span><span class="sxs-lookup"><span data-stu-id="9a068-375">If the caller needs to work with a particular element within the JSON document, return the <xref:System.Text.Json.JsonElement.Clone%2A> of that <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="9a068-376">如果您直接傳回 `RootElement` 或子項目而不進行 `Clone`，則在處置擁有它的 `JsonDocument` 之後，呼叫端將無法存取傳回的 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="9a068-376">If you return the `RootElement` or a sub-element directly without making a `Clone`, the caller won't be able to access the returned `JsonElement` after the `JsonDocument` that owns it is disposed.</span></span>

<span data-ttu-id="9a068-377">以下是要求您進行 `Clone`的範例：</span><span class="sxs-lookup"><span data-stu-id="9a068-377">Here's an example that requires you to make a `Clone`:</span></span>

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

<span data-ttu-id="9a068-378">上述程式碼需要包含 `fileName` 屬性的 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="9a068-378">The preceding code expects a `JsonElement` that contains a `fileName` property.</span></span> <span data-ttu-id="9a068-379">它會開啟 JSON 檔案，並建立 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="9a068-379">It opens the JSON file and creates a `JsonDocument`.</span></span> <span data-ttu-id="9a068-380">方法假設呼叫端想要使用整份檔，因此它會傳回 `RootElement`的 `Clone`。</span><span class="sxs-lookup"><span data-stu-id="9a068-380">The method assumes that the caller wants to work with the entire document, so it returns the `Clone` of the `RootElement`.</span></span> 

<span data-ttu-id="9a068-381">如果您收到 `JsonElement` 並傳回子項目，則不需要傳回子項目的 `Clone`。</span><span class="sxs-lookup"><span data-stu-id="9a068-381">If you receive a `JsonElement` and are returning a sub-element, it's not necessary to return a `Clone` of the sub-element.</span></span> <span data-ttu-id="9a068-382">呼叫端負責保持傳入 `JsonElement` 所屬的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="9a068-382">The caller is responsible for keeping alive the `JsonDocument` that the passed-in `JsonElement` belongs to.</span></span> <span data-ttu-id="9a068-383">例如：</span><span class="sxs-lookup"><span data-stu-id="9a068-383">For example:</span></span>

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a><span data-ttu-id="9a068-384">JsonDocument 是唯讀的</span><span class="sxs-lookup"><span data-stu-id="9a068-384">JsonDocument is read-only</span></span>

<span data-ttu-id="9a068-385"><xref:System.Text.Json> DOM 無法加入、移除或修改 JSON 元素。</span><span class="sxs-lookup"><span data-stu-id="9a068-385">The <xref:System.Text.Json> DOM can't add, remove, or modify JSON elements.</span></span> <span data-ttu-id="9a068-386">其設計是以這種方式來進行效能，並減少剖析一般 JSON 承載大小的配置（也就是 < 1 MB）。</span><span class="sxs-lookup"><span data-stu-id="9a068-386">It's designed this way for performance and to reduce allocations for parsing common JSON payload sizes (that is, < 1 MB).</span></span> <span data-ttu-id="9a068-387">如果您的案例目前使用可修改的 DOM，下列其中一個因應措施可能是可行的：</span><span class="sxs-lookup"><span data-stu-id="9a068-387">If your scenario currently uses a modifiable DOM, one of the following workarounds might be feasible:</span></span>

* <span data-ttu-id="9a068-388">若要從頭開始建立 `JsonDocument` （也就是不會將現有的 JSON 承載傳遞給 `Parse` 方法），請使用 `Utf8JsonWriter` 寫入 JSON 文字，並剖析該輸出，以建立新的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="9a068-388">To build a `JsonDocument` from scratch (that is, without passing in an existing JSON payload to the `Parse` method), write the JSON text by using the `Utf8JsonWriter` and parse the output from that to make a new `JsonDocument`.</span></span>
* <span data-ttu-id="9a068-389">若要修改現有的 `JsonDocument`，請使用它來寫入 JSON 文字，並在您撰寫時進行變更，並剖析該輸出以建立新的 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="9a068-389">To modify an existing `JsonDocument`, use it to write JSON text, making changes while you write, and parse the output from that to make a new `JsonDocument`.</span></span>
* <span data-ttu-id="9a068-390">若要合併現有的 JSON 檔，相當於 `Newtonsoft.Json`的 `JObject.Merge` 或 `JContainer.Merge` Api，請參閱[此 GitHub 問題](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)。</span><span class="sxs-lookup"><span data-stu-id="9a068-390">To merge existing JSON documents, equivalent to the `JObject.Merge` or `JContainer.Merge` APIs from `Newtonsoft.Json`, see [this GitHub issue](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).</span></span>

### <a name="jsonelement-is-a-union-struct"></a><span data-ttu-id="9a068-391">JsonElement 是聯集結構</span><span class="sxs-lookup"><span data-stu-id="9a068-391">JsonElement is a union struct</span></span>

<span data-ttu-id="9a068-392">`JsonDocument` 會將 `RootElement` 公開為 <xref:System.Text.Json.JsonElement>類型的屬性，也就是包含任何 JSON 元素的 union、struct 類型。</span><span class="sxs-lookup"><span data-stu-id="9a068-392">`JsonDocument` exposes the `RootElement` as a property of type <xref:System.Text.Json.JsonElement>, which is a union, struct type that encompasses any JSON element.</span></span> <span data-ttu-id="9a068-393">`Newtonsoft.Json` 使用專用的階層型別，如 `JObject`、`JArray`、`JToken`等等。</span><span class="sxs-lookup"><span data-stu-id="9a068-393">`Newtonsoft.Json` uses dedicated hierarchical types like `JObject`,`JArray`, `JToken`, and so forth.</span></span> <span data-ttu-id="9a068-394">`JsonElement` 是您可以搜尋和列舉的專案，您可以使用 `JsonElement` 將 JSON 元素具體化成 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9a068-394">`JsonElement` is what you can search and enumerate over, and you can use `JsonElement` to materialize JSON elements into .NET types.</span></span>

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a><span data-ttu-id="9a068-395">如何搜尋子項目的 JsonDocument 和 JsonElement</span><span class="sxs-lookup"><span data-stu-id="9a068-395">How to search a JsonDocument and JsonElement for sub-elements</span></span>

<span data-ttu-id="9a068-396">使用 `JObject` 或 `JArray` 從 `Newtonsoft.Json` 搜尋 JSON 權杖，通常會相對快速，因為它們是在某個字典中的查閱。</span><span class="sxs-lookup"><span data-stu-id="9a068-396">Searches for JSON tokens using `JObject` or `JArray` from `Newtonsoft.Json` tend to be relatively fast because they're lookups in some dictionary.</span></span> <span data-ttu-id="9a068-397">相較之下，搜尋 `JsonElement` 需要依序搜尋屬性，因此速度相當慢（例如使用 `TryGetProperty`時）。</span><span class="sxs-lookup"><span data-stu-id="9a068-397">By comparison, searches on `JsonElement` require a sequential search of the properties and hence is relatively slow (for example when using `TryGetProperty`).</span></span> <span data-ttu-id="9a068-398"><xref:System.Text.Json> 的設計目的是要將初始剖析時間減至最少，而不是查閱時間。</span><span class="sxs-lookup"><span data-stu-id="9a068-398"><xref:System.Text.Json> is designed to minimize initial parse time rather than lookup time.</span></span> <span data-ttu-id="9a068-399">因此，搜尋 `JsonDocument` 物件時，請使用下列方法來優化效能：</span><span class="sxs-lookup"><span data-stu-id="9a068-399">Therefore, use the following approaches to optimize performance when searching through a `JsonDocument` object:</span></span>

* <span data-ttu-id="9a068-400">使用內建的列舉值（<xref:System.Text.Json.JsonElement.EnumerateArray%2A> 和 <xref:System.Text.Json.JsonElement.EnumerateObject%2A>），而不是執行您自己的索引或迴圈。</span><span class="sxs-lookup"><span data-stu-id="9a068-400">Use the built-in enumerators (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> and <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) rather than doing your own indexing or loops.</span></span>
* <span data-ttu-id="9a068-401">請不要透過每個屬性，使用 `RootElement`，對整個 `JsonDocument` 進行順序搜尋。</span><span class="sxs-lookup"><span data-stu-id="9a068-401">Don't do a sequential search on the whole `JsonDocument` through every property by using `RootElement`.</span></span> <span data-ttu-id="9a068-402">相反地，請根據 JSON 資料的已知結構來搜尋嵌套的 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-402">Instead, search on nested JSON objects based on the known structure of the JSON data.</span></span> <span data-ttu-id="9a068-403">例如，如果您要尋找 `Student` 物件中的 `Grade` 屬性，請對 `Student` 物件執行迴圈，並取得每一個的 `Grade` 值，而不是搜尋尋找 `JsonElement` 屬性的所有 `Grade` 物件。</span><span class="sxs-lookup"><span data-stu-id="9a068-403">For example, if you're looking for a `Grade` property in `Student` objects, loop through the `Student` objects and get the value of `Grade` for each, rather than searching through all `JsonElement` objects looking for `Grade` properties.</span></span> <span data-ttu-id="9a068-404">執行後者會導致相同資料的不必要傳遞。</span><span class="sxs-lookup"><span data-stu-id="9a068-404">Doing the latter will result in unnecessary passes over the same data.</span></span>

<span data-ttu-id="9a068-405">如需程式碼範例，請參閱[使用 JsonDocument 來存取資料](system-text-json-how-to.md#use-jsondocument-for-access-to-data)。</span><span class="sxs-lookup"><span data-stu-id="9a068-405">For a code example, see [Use JsonDocument for access to data](system-text-json-how-to.md#use-jsondocument-for-access-to-data).</span></span>

## <a name="utf8jsonreader-compared-to-jsontextreader"></a><span data-ttu-id="9a068-406">Utf8JsonReader 與 JsonTextReader 的比較</span><span class="sxs-lookup"><span data-stu-id="9a068-406">Utf8JsonReader compared to JsonTextReader</span></span>

<span data-ttu-id="9a068-407"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器、從[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601)讀取。</span><span class="sxs-lookup"><span data-stu-id="9a068-407"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) or [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601).</span></span> <span data-ttu-id="9a068-408">`Utf8JsonReader` 是可以用來建立自訂剖析器和還原序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="9a068-408">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span>

<span data-ttu-id="9a068-409">下列各節說明使用 `Utf8JsonReader`的建議程式設計模式。</span><span class="sxs-lookup"><span data-stu-id="9a068-409">The following sections explain recommended programming patterns for using `Utf8JsonReader`.</span></span>

### <a name="utf8jsonreader-is-a-ref-struct"></a><span data-ttu-id="9a068-410">Utf8JsonReader 是 ref 結構</span><span class="sxs-lookup"><span data-stu-id="9a068-410">Utf8JsonReader is a ref struct</span></span>

<span data-ttu-id="9a068-411">因為 `Utf8JsonReader` 類型是*ref 結構*，所以有[一些限制](../../csharp/language-reference/keywords/ref.md#ref-struct-types)。</span><span class="sxs-lookup"><span data-stu-id="9a068-411">Because the `Utf8JsonReader` type is a *ref struct*, it has [certain limitations](../../csharp/language-reference/keywords/ref.md#ref-struct-types).</span></span> <span data-ttu-id="9a068-412">例如，它無法在 ref 結構以外的類別或結構上儲存為欄位。</span><span class="sxs-lookup"><span data-stu-id="9a068-412">For example, it can't be stored as a field on a class or struct other than a ref struct.</span></span> <span data-ttu-id="9a068-413">為了達到高效能，此型別必須是 `ref struct`，因為它需要快取輸入[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)，這本身就是 ref 結構。</span><span class="sxs-lookup"><span data-stu-id="9a068-413">To achieve high performance, this type must be a `ref struct` since it needs to cache the input [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), which itself is a ref struct.</span></span> <span data-ttu-id="9a068-414">此外，這種類型是可變動的，因為它會保存狀態。</span><span class="sxs-lookup"><span data-stu-id="9a068-414">In addition, this type is mutable since it holds state.</span></span> <span data-ttu-id="9a068-415">因此，請以 ref 而非傳值方式來**傳遞它**。</span><span class="sxs-lookup"><span data-stu-id="9a068-415">Therefore, **pass it by ref** rather than by value.</span></span> <span data-ttu-id="9a068-416">以傳值方式傳遞會導致結構複製，而且呼叫端看不到狀態變更。</span><span class="sxs-lookup"><span data-stu-id="9a068-416">Passing it by value would result in a struct copy and the state changes would not be visible to the caller.</span></span> <span data-ttu-id="9a068-417">這與 `Newtonsoft.Json` 不同，因為 `Newtonsoft.Json` `JsonTextReader` 是一個類別。</span><span class="sxs-lookup"><span data-stu-id="9a068-417">This differs from `Newtonsoft.Json` since the `Newtonsoft.Json` `JsonTextReader` is a class.</span></span> <span data-ttu-id="9a068-418">如需如何使用 ref 結構的詳細資訊，請參閱[撰寫安全且C#有效率](../../csharp/write-safe-efficient-code.md)的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9a068-418">For more information about how to use ref structs, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>

### <a name="read-utf-8-text"></a><span data-ttu-id="9a068-419">讀取 UTF-8 文字</span><span class="sxs-lookup"><span data-stu-id="9a068-419">Read UTF-8 text</span></span>

<span data-ttu-id="9a068-420">若要在使用 `Utf8JsonReader`時達到最佳效能，請閱讀已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。</span><span class="sxs-lookup"><span data-stu-id="9a068-420">To achieve the best possible performance while using the `Utf8JsonReader`, read JSON payloads already encoded as UTF-8 text rather than as UTF-16 strings.</span></span> <span data-ttu-id="9a068-421">如需程式碼範例，請參閱[使用 Utf8JsonReader 來篩選資料](system-text-json-how-to.md#filter-data-using-utf8jsonreader)。</span><span class="sxs-lookup"><span data-stu-id="9a068-421">For a code example, see [Filter data using Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).</span></span>

### <a name="read-with-a-stream-or-pipereader"></a><span data-ttu-id="9a068-422">讀取資料流程或 PipeReader</span><span class="sxs-lookup"><span data-stu-id="9a068-422">Read with a Stream or PipeReader</span></span>

<span data-ttu-id="9a068-423">`Utf8JsonReader` 支援從以 UTF-8 編碼的[ReadOnlySpan\<byte >](xref:System.ReadOnlySpan%601)或[ReadOnlySequence\<byte >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果）讀取。</span><span class="sxs-lookup"><span data-stu-id="9a068-423">The `Utf8JsonReader` supports reading from a UTF-8 encoded [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) or [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601) (which is the result of reading from a <xref:System.IO.Pipelines.PipeReader>).</span></span>

<span data-ttu-id="9a068-424">對於同步讀取，您可以讀取 JSON 承載，直到資料流程結尾到位元組陣列，然後將它傳遞到讀取器。</span><span class="sxs-lookup"><span data-stu-id="9a068-424">For synchronous reading, you could read the JSON payload until the end of the stream into a byte array and pass that into the reader.</span></span> <span data-ttu-id="9a068-425">若要從字串讀取（編碼為 UTF-16），請呼叫 <xref:System.Text.Encoding.UTF8>。<xref:System.Text.Encoding.GetBytes%2A></span><span class="sxs-lookup"><span data-stu-id="9a068-425">For reading from a string (which is encoded as UTF-16), call <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A></span></span> <span data-ttu-id="9a068-426">首先，將字串轉碼為 UTF-8 編碼的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="9a068-426">to first transcode the string to a UTF-8 encoded byte array.</span></span> <span data-ttu-id="9a068-427">然後將它傳遞給 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="9a068-427">Then pass that to the `Utf8JsonReader`.</span></span> 

<span data-ttu-id="9a068-428">由於 `Utf8JsonReader` 會將輸入視為 JSON 文字，因此會將 UTF-8 位元組順序標記（BOM）視為不正確 JSON。</span><span class="sxs-lookup"><span data-stu-id="9a068-428">Since the `Utf8JsonReader` considers the input to be JSON text, a UTF-8 byte order mark (BOM) is considered invalid JSON.</span></span> <span data-ttu-id="9a068-429">呼叫端必須先篩選掉，再將資料傳遞給讀取器。</span><span class="sxs-lookup"><span data-stu-id="9a068-429">The caller needs to filter that out before passing the data to the reader.</span></span>

<span data-ttu-id="9a068-430">如需程式碼範例，請參閱[使用 Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader)。</span><span class="sxs-lookup"><span data-stu-id="9a068-430">For code examples, see [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).</span></span>

### <a name="read-with-multi-segment-readonlysequence"></a><span data-ttu-id="9a068-431">閱讀多區段 ReadOnlySequence</span><span class="sxs-lookup"><span data-stu-id="9a068-431">Read with multi-segment ReadOnlySequence</span></span>

<span data-ttu-id="9a068-432">如果您的 JSON 輸入是[ReadOnlySpan\<位元組 >](xref:System.ReadOnlySpan%601)，則當您執行讀取迴圈時，可以從讀取器上的 `ValueSpan` 屬性存取每個 json 元素。</span><span class="sxs-lookup"><span data-stu-id="9a068-432">If your JSON input is a [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), each JSON element can be accessed from the `ValueSpan` property on the reader as you go through the read loop.</span></span> <span data-ttu-id="9a068-433">不過，如果您的輸入是[ReadOnlySequence\<位元組 >](xref:System.Buffers.ReadOnlySequence%601) （這是從 <xref:System.IO.Pipelines.PipeReader>讀取的結果），某些 JSON 元素可能會跨 `ReadOnlySequence<byte>` 物件的多個區段。</span><span class="sxs-lookup"><span data-stu-id="9a068-433">However, if your input is a [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601) (which is the result of reading from a <xref:System.IO.Pipelines.PipeReader>), some JSON elements might straddle multiple segments of the `ReadOnlySequence<byte>` object.</span></span> <span data-ttu-id="9a068-434">這些元素無法從連續記憶體區塊中的 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 存取。</span><span class="sxs-lookup"><span data-stu-id="9a068-434">These elements would not be accessible from <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> in a contiguous memory block.</span></span> <span data-ttu-id="9a068-435">相反地，每當您有多個區段 `ReadOnlySequence<byte>` 做為輸入時，請輪詢讀取器上的 <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> 屬性，以瞭解如何存取目前的 JSON 元素。</span><span class="sxs-lookup"><span data-stu-id="9a068-435">Instead, whenever you have a multi-segment `ReadOnlySequence<byte>` as input, poll the <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> property on the reader to figure out how to access the current JSON element.</span></span> <span data-ttu-id="9a068-436">以下是建議的模式：</span><span class="sxs-lookup"><span data-stu-id="9a068-436">Here's a recommended pattern:</span></span>

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

### <a name="use-valuetextequals-for-property-name-lookups"></a><span data-ttu-id="9a068-437">使用 ValueTextEquals 進行屬性名稱查閱</span><span class="sxs-lookup"><span data-stu-id="9a068-437">Use ValueTextEquals for property name lookups</span></span>

<span data-ttu-id="9a068-438">請不要使用 <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> 透過呼叫屬性名稱查閱的 <xref:System.MemoryExtensions.SequenceEqual%2A> 來進行逐位元組比較。</span><span class="sxs-lookup"><span data-stu-id="9a068-438">Don't use <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> to do byte-by-byte comparisons by calling <xref:System.MemoryExtensions.SequenceEqual%2A> for property name lookups.</span></span> <span data-ttu-id="9a068-439">改為呼叫 <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>，因為該方法會將任何在 JSON 中進行轉義的字元。</span><span class="sxs-lookup"><span data-stu-id="9a068-439">Call <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> instead, because that method unescapes any characters that are escaped in the JSON.</span></span> <span data-ttu-id="9a068-440">以下範例顯示如何搜尋名為 "name" 的屬性：</span><span class="sxs-lookup"><span data-stu-id="9a068-440">Here's an example that shows how to search for a property that is named "name":</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a><span data-ttu-id="9a068-441">將 null 值讀取成可為 null 的實數值型別</span><span class="sxs-lookup"><span data-stu-id="9a068-441">Read null values into nullable value types</span></span>

<span data-ttu-id="9a068-442">`Newtonsoft.Json` 所提供的 Api 會傳回 <xref:System.Nullable%601>，例如 `ReadAsBoolean`，藉由傳回 `TokenType` 來處理 `Null` `bool?`。</span><span class="sxs-lookup"><span data-stu-id="9a068-442">`Newtonsoft.Json` provides APIs that return <xref:System.Nullable%601>, such as `ReadAsBoolean`, which handles a `Null` `TokenType` for you by returning a `bool?`.</span></span> <span data-ttu-id="9a068-443">內建的 `System.Text.Json` Api 只會傳回不可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="9a068-443">The built-in `System.Text.Json` APIs return only non-nullable value types.</span></span> <span data-ttu-id="9a068-444">例如，<xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> 會傳回 `bool`。</span><span class="sxs-lookup"><span data-stu-id="9a068-444">For example, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> returns a `bool`.</span></span> <span data-ttu-id="9a068-445">如果在 JSON 中找到 `Null`，它會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a068-445">It throws an exception if it finds `Null` in the JSON.</span></span> <span data-ttu-id="9a068-446">下列範例示範兩種處理 null 的方式：一個是藉由傳回可為 null 的實值型別，另一個則是傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="9a068-446">The following examples show two ways to handle nulls, one by returning a nullable value type and one by returning the default value:</span></span>

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

### <a name="multi-targeting"></a><span data-ttu-id="9a068-447">多目標</span><span class="sxs-lookup"><span data-stu-id="9a068-447">Multi-targeting</span></span>

<span data-ttu-id="9a068-448">如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。</span><span class="sxs-lookup"><span data-stu-id="9a068-448">If you need to continue to use `Newtonsoft.Json` for certain target frameworks, you can multi-target and have two implementations.</span></span> <span data-ttu-id="9a068-449">不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。</span><span class="sxs-lookup"><span data-stu-id="9a068-449">However, this is not trivial and would require some `#ifdefs` and source duplication.</span></span> <span data-ttu-id="9a068-450">盡可能共用程式碼的方法之一，就是建立 `Utf8JsonReader` 和 `Newtonsoft.Json` `JsonTextReader`的 `ref struct` 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="9a068-450">One way to share as much code as possible is to create a `ref struct` wrapper around `Utf8JsonReader` and `Newtonsoft.Json` `JsonTextReader`.</span></span> <span data-ttu-id="9a068-451">此包裝函式會統一公用介面區，同時隔離行為差異。</span><span class="sxs-lookup"><span data-stu-id="9a068-451">This wrapper would unify the public surface area while isolating the behavioral differences.</span></span> <span data-ttu-id="9a068-452">這可讓您隔離主要變更與型別的結構，並以傳址方式傳遞新的型別。</span><span class="sxs-lookup"><span data-stu-id="9a068-452">This lets you isolate the changes mainly to the construction of the type, along with passing the new type around by reference.</span></span> <span data-ttu-id="9a068-453">這是[DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫所遵循的模式：</span><span class="sxs-lookup"><span data-stu-id="9a068-453">This is the pattern that the [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) library follows:</span></span>

* [<span data-ttu-id="9a068-454">UnifiedJsonReader.JsonTextReader.cs</span><span class="sxs-lookup"><span data-stu-id="9a068-454">UnifiedJsonReader.JsonTextReader.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [<span data-ttu-id="9a068-455">UnifiedJsonReader.Utf8JsonReader.cs</span><span class="sxs-lookup"><span data-stu-id="9a068-455">UnifiedJsonReader.Utf8JsonReader.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a><span data-ttu-id="9a068-456">Utf8JsonWriter 與 Json.net jsoNtextwriter, 的比較</span><span class="sxs-lookup"><span data-stu-id="9a068-456">Utf8JsonWriter compared to JsonTextWriter</span></span>

<span data-ttu-id="9a068-457"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（例如 `String`、`Int32`和 `DateTime`）撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="9a068-457"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="9a068-458">寫入器是可以用來建立自訂序列化程式的低層級類型。</span><span class="sxs-lookup"><span data-stu-id="9a068-458">The writer is a low-level type that can be used to build custom serializers.</span></span>

<span data-ttu-id="9a068-459">下列各節說明使用 `Utf8JsonWriter`的建議程式設計模式。</span><span class="sxs-lookup"><span data-stu-id="9a068-459">The following sections explain recommended programming patterns for using `Utf8JsonWriter`.</span></span>

### <a name="write-with-utf-8-text"></a><span data-ttu-id="9a068-460">以 UTF-8 文字撰寫</span><span class="sxs-lookup"><span data-stu-id="9a068-460">Write with UTF-8 text</span></span>

<span data-ttu-id="9a068-461">若要在使用 `Utf8JsonWriter`時達到最佳效能，請撰寫已編碼為 UTF-8 文字，而不是 UTF-16 字串的 JSON 承載。</span><span class="sxs-lookup"><span data-stu-id="9a068-461">To achieve the best possible performance while using the `Utf8JsonWriter`, write JSON payloads already encoded as UTF-8 text rather than as UTF-16 strings.</span></span> <span data-ttu-id="9a068-462">使用 <xref:System.Text.Json.JsonEncodedText> 來快取和預先編碼已知的字串屬性名稱和值，並將其傳遞給寫入器，而不是使用 UTF-16 字串常值。</span><span class="sxs-lookup"><span data-stu-id="9a068-462">Use <xref:System.Text.Json.JsonEncodedText> to cache and pre-encode known string property names and values as statics, and pass those to the writer, rather than using UTF-16 string literals.</span></span> <span data-ttu-id="9a068-463">這比快取和使用 UTF-8 位元組陣列更快速。</span><span class="sxs-lookup"><span data-stu-id="9a068-463">This is faster than caching and using UTF-8 byte arrays.</span></span>

<span data-ttu-id="9a068-464">如果您需要執行自訂的轉義，此方法也適用。</span><span class="sxs-lookup"><span data-stu-id="9a068-464">This approach also works if you need to do custom escaping.</span></span> <span data-ttu-id="9a068-465">`System.Text.Json` 不允許您在寫入字串時停用轉義。</span><span class="sxs-lookup"><span data-stu-id="9a068-465">`System.Text.Json` doesn't let you disable escaping while writing a string.</span></span> <span data-ttu-id="9a068-466">不過，您可以將自己的自訂 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 當做寫入器的選項傳入，或建立您自己的 `JsonEncodedText` 以使用您的 `JavascriptEncoder` 來執行轉義，然後撰寫 `JsonEncodedText`，而不是字串。</span><span class="sxs-lookup"><span data-stu-id="9a068-466">However, you could pass in your own custom <xref:System.Text.Encodings.Web.JavaScriptEncoder> as an option to the writer, or create your own `JsonEncodedText` that uses your `JavascriptEncoder` to do the escaping, and then write the `JsonEncodedText` instead of the string.</span></span> <span data-ttu-id="9a068-467">如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="9a068-467">For more information, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="write-raw-values"></a><span data-ttu-id="9a068-468">寫入原始值</span><span class="sxs-lookup"><span data-stu-id="9a068-468">Write raw values</span></span>

<span data-ttu-id="9a068-469">`Newtonsoft.Json` `WriteRawValue` 方法會寫入需要值的原始 JSON。</span><span class="sxs-lookup"><span data-stu-id="9a068-469">The `Newtonsoft.Json` `WriteRawValue` method writes raw JSON where a value is expected.</span></span> <span data-ttu-id="9a068-470"><xref:System.Text.Json> 沒有直接的對等用法，但以下是可確保只會寫入有效 JSON 的因應措施：</span><span class="sxs-lookup"><span data-stu-id="9a068-470"><xref:System.Text.Json> has no direct equivalent, but here's a workaround that ensures only valid JSON is written:</span></span>

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a><span data-ttu-id="9a068-471">自訂字元轉義</span><span class="sxs-lookup"><span data-stu-id="9a068-471">Customize character escaping</span></span>

<span data-ttu-id="9a068-472">`JsonTextWriter` 的[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)設定會提供選項，以將所有非 ASCII 字元**或**HTML 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="9a068-472">The [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) setting of `JsonTextWriter` offers options to escape all non-ASCII characters **or** HTML characters.</span></span> <span data-ttu-id="9a068-473">根據預設，`Utf8JsonWriter` 會將所有非 ASCII**和**HTML 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="9a068-473">By default, `Utf8JsonWriter` escapes all non-ASCII **and** HTML characters.</span></span> <span data-ttu-id="9a068-474">這項轉義是針對深層防禦的安全性原因而完成。</span><span class="sxs-lookup"><span data-stu-id="9a068-474">This escaping is done for defense-in-depth security reasons.</span></span> <span data-ttu-id="9a068-475">若要指定不同的轉義原則，請建立 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 並設定 <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9a068-475">To specify a different escaping policy, create a <xref:System.Text.Encodings.Web.JavaScriptEncoder> and set <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a068-476">如需詳細資訊，請參閱[自訂字元編碼](system-text-json-how-to.md#customize-character-encoding)。</span><span class="sxs-lookup"><span data-stu-id="9a068-476">For more information, see [Customize character encoding](system-text-json-how-to.md#customize-character-encoding).</span></span>

### <a name="customize-json-format"></a><span data-ttu-id="9a068-477">自訂 JSON 格式</span><span class="sxs-lookup"><span data-stu-id="9a068-477">Customize JSON format</span></span>

<span data-ttu-id="9a068-478">`JsonTextWriter` 包含下列設定，其中 `Utf8JsonWriter` 沒有對等的：</span><span class="sxs-lookup"><span data-stu-id="9a068-478">`JsonTextWriter` includes the following settings, for which `Utf8JsonWriter` has no equivalent:</span></span>

* <span data-ttu-id="9a068-479">[縮排](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm)-指定要縮排的字元數。</span><span class="sxs-lookup"><span data-stu-id="9a068-479">[Indentation](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Specifies how many characters to indent.</span></span> <span data-ttu-id="9a068-480">`Utf8JsonWriter` 一律會進行2個字元的縮排。</span><span class="sxs-lookup"><span data-stu-id="9a068-480">`Utf8JsonWriter` always does 2-character indentation.</span></span>
* <span data-ttu-id="9a068-481">[IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -指定要用於縮排的字元。</span><span class="sxs-lookup"><span data-stu-id="9a068-481">[IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Specifies the character to use for indentation.</span></span>  <span data-ttu-id="9a068-482">`Utf8JsonWriter` 一律使用空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a068-482">`Utf8JsonWriter` always uses whitespace.</span></span>
* <span data-ttu-id="9a068-483">[QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -指定用來括住字串值的字元。</span><span class="sxs-lookup"><span data-stu-id="9a068-483">[QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Specifies the character to use to surround string values.</span></span>  <span data-ttu-id="9a068-484">`Utf8JsonWriter` 一律使用雙引號。</span><span class="sxs-lookup"><span data-stu-id="9a068-484">`Utf8JsonWriter` always uses double quotes.</span></span>
* <span data-ttu-id="9a068-485">[QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -指定是否要以引號括住屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9a068-485">[QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Specifies whether or not to surround property names with quotes.</span></span>  <span data-ttu-id="9a068-486">`Utf8JsonWriter` 一律以引號括住它們。</span><span class="sxs-lookup"><span data-stu-id="9a068-486">`Utf8JsonWriter` always surrounds them with quotes.</span></span>

<span data-ttu-id="9a068-487">沒有任何因應措施可讓您自訂 `Utf8JsonWriter` 以這些方式產生的 JSON。</span><span class="sxs-lookup"><span data-stu-id="9a068-487">There are no workarounds that would let you customize the JSON produced by `Utf8JsonWriter` in these ways.</span></span>

### <a name="write-null-values"></a><span data-ttu-id="9a068-488">寫入 null 值</span><span class="sxs-lookup"><span data-stu-id="9a068-488">Write null values</span></span>

<span data-ttu-id="9a068-489">若要使用 `Utf8JsonWriter`來寫入 null 值，請呼叫：</span><span class="sxs-lookup"><span data-stu-id="9a068-489">To write null values by using `Utf8JsonWriter`, call:</span></span>

* <span data-ttu-id="9a068-490"><xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> 寫入具有 null 值的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="9a068-490"><xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> to write a key-value pair with null as the value.</span></span>
* <span data-ttu-id="9a068-491"><xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> 寫入 null 做為 JSON 陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="9a068-491"><xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> to write null as an element of a JSON array.</span></span>

<span data-ttu-id="9a068-492">若為字串屬性，如果字串為 null，<xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> 和 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> 就相當於 `WriteNull` 和 `WriteNullValue`。</span><span class="sxs-lookup"><span data-stu-id="9a068-492">For a string property, if the string is null, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> and <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> are equivalent to `WriteNull` and `WriteNullValue`.</span></span>

### <a name="write-timespan-uri-or-char-values"></a><span data-ttu-id="9a068-493">寫入 Timespan、Uri 或 char 值</span><span class="sxs-lookup"><span data-stu-id="9a068-493">Write Timespan, Uri, or char values</span></span>

<span data-ttu-id="9a068-494">`JsonTextWriter` 提供[TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm)、 [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)和[char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm)值的 `WriteValue` 方法。</span><span class="sxs-lookup"><span data-stu-id="9a068-494">`JsonTextWriter` provides `WriteValue` methods for [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm), and [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) values.</span></span> <span data-ttu-id="9a068-495">`Utf8JsonWriter` 沒有對等的方法。</span><span class="sxs-lookup"><span data-stu-id="9a068-495">`Utf8JsonWriter` doesn't have equivalent methods.</span></span> <span data-ttu-id="9a068-496">相反地，請將這些值格式化為字串（例如，藉由呼叫 `ToString()`）並呼叫 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="9a068-496">Instead, format these values as strings (by calling `ToString()`, for example) and call <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.</span></span>

### <a name="multi-targeting"></a><span data-ttu-id="9a068-497">多目標</span><span class="sxs-lookup"><span data-stu-id="9a068-497">Multi-targeting</span></span>

<span data-ttu-id="9a068-498">如果您需要繼續針對特定目標 framework 使用 `Newtonsoft.Json`，您可以多個目標，而且有兩個執行。</span><span class="sxs-lookup"><span data-stu-id="9a068-498">If you need to continue to use `Newtonsoft.Json` for certain target frameworks, you can multi-target and have two implementations.</span></span> <span data-ttu-id="9a068-499">不過，這並不簡單，而且需要一些 `#ifdefs` 和來源重複。</span><span class="sxs-lookup"><span data-stu-id="9a068-499">However, this is not trivial and would require some `#ifdefs` and source duplication.</span></span> <span data-ttu-id="9a068-500">盡可能共用程式碼的方法之一，就是建立一個圍繞 `Utf8JsonWriter` 的包裝函式，並 `Newtonsoft` `JsonTextWriter`。</span><span class="sxs-lookup"><span data-stu-id="9a068-500">One way to share as much code as possible is to create a wrapper around `Utf8JsonWriter` and `Newtonsoft` `JsonTextWriter`.</span></span> <span data-ttu-id="9a068-501">此包裝函式會統一公用介面區，同時隔離行為差異。</span><span class="sxs-lookup"><span data-stu-id="9a068-501">This wrapper would unify the public surface area while isolating the behavioral differences.</span></span> <span data-ttu-id="9a068-502">這可讓您將變更主要隔離到類型的結構。</span><span class="sxs-lookup"><span data-stu-id="9a068-502">This lets you isolate the changes mainly to the construction of the type.</span></span> <span data-ttu-id="9a068-503">[DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)程式庫如下：</span><span class="sxs-lookup"><span data-stu-id="9a068-503">[Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) library follows:</span></span>

* [<span data-ttu-id="9a068-504">UnifiedJsonWriter.JsonTextWriter.cs</span><span class="sxs-lookup"><span data-stu-id="9a068-504">UnifiedJsonWriter.JsonTextWriter.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [<span data-ttu-id="9a068-505">UnifiedJsonWriter.Utf8JsonWriter.cs</span><span class="sxs-lookup"><span data-stu-id="9a068-505">UnifiedJsonWriter.Utf8JsonWriter.cs</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a><span data-ttu-id="9a068-506">其他資源</span><span class="sxs-lookup"><span data-stu-id="9a068-506">Additional resources</span></span>

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [<span data-ttu-id="9a068-507">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="9a068-507">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9a068-508">如何使用 System.object</span><span class="sxs-lookup"><span data-stu-id="9a068-508">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="9a068-509">如何撰寫自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="9a068-509">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="9a068-510">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="9a068-510">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="9a068-511">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="9a068-511">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="9a068-512">System.object。序列化 API 參考</span><span class="sxs-lookup"><span data-stu-id="9a068-512">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
