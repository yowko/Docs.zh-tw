---
title: 如何使用自訂字元編碼 System.Text.Json
description: 瞭解如何自訂字元編碼，以及如何在 .NET 中從 JSON 序列化和還原序列化。
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 136a75ab73767fd79f99caa1d1387706ab655473
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215975"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="09f6a-103">如何使用自訂字元編碼 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="09f6a-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="09f6a-104">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="09f6a-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="09f6a-105">也就是說，它會將它們取代 `\uxxxx` 為 `xxxx` 字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="09f6a-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="09f6a-106">例如，如果 `Summary` 下列 JSON 中的屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09f6a-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="09f6a-107">將語言字元集序列化</span><span class="sxs-lookup"><span data-stu-id="09f6a-107">Serialize language character sets</span></span>

<span data-ttu-id="09f6a-108">若要將一或多個語言的字元集)  (s，而不進行任何轉義，請在建立實例時指定 [Unicode 範圍 () ](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09f6a-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="09f6a-109">此程式碼不會將斯拉夫文或希臘文字元換成。</span><span class="sxs-lookup"><span data-stu-id="09f6a-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="09f6a-110">如果 `Summary` 屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09f6a-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="09f6a-111">根據預設，編碼器會以 <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> 範圍初始化。</span><span class="sxs-lookup"><span data-stu-id="09f6a-111">By default, the encoder is initialized with the <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> range.</span></span>

<span data-ttu-id="09f6a-112">若要在不經過轉義的情況下序列化所有語言集，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="09f6a-112">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="09f6a-113">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="09f6a-113">Serialize specific characters</span></span>

<span data-ttu-id="09f6a-114">替代方法是指定您想要允許的個別字元，而不需要經過轉義。</span><span class="sxs-lookup"><span data-stu-id="09f6a-114">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="09f6a-115">下列範例只會序列化的前兩個字元 `жарко` ：</span><span class="sxs-lookup"><span data-stu-id="09f6a-115">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="09f6a-116">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="09f6a-116">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a><span data-ttu-id="09f6a-117">封鎖清單</span><span class="sxs-lookup"><span data-stu-id="09f6a-117">Block lists</span></span>

<span data-ttu-id="09f6a-118">上述各節顯示如何指定您不想要加入的程式碼點或範圍的允許清單。</span><span class="sxs-lookup"><span data-stu-id="09f6a-118">The preceding sections show how to specify allow lists of code points or ranges that you don't want to be escaped.</span></span> <span data-ttu-id="09f6a-119">不過，有全域和編碼器專屬的區塊清單，可覆寫您允許清單中的特定程式碼點。</span><span class="sxs-lookup"><span data-stu-id="09f6a-119">However, there are global and encoder-specific block lists that can override certain code points in your allow list.</span></span> <span data-ttu-id="09f6a-120">區塊清單中的程式碼點一律會進行轉義，即使它們包含在您的允許清單中也一樣。</span><span class="sxs-lookup"><span data-stu-id="09f6a-120">Code points in a block list are always escaped, even if they're included in your allow list.</span></span>

### <a name="global-block-list"></a><span data-ttu-id="09f6a-121">全域封鎖清單</span><span class="sxs-lookup"><span data-stu-id="09f6a-121">Global block list</span></span>

<span data-ttu-id="09f6a-122">全域封鎖清單包括私用字元、控制字元、未定義的程式碼點，以及某些 Unicode 類別，例如 [Space_Separator 分類](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)（排除） `U+0020 SPACE` 。</span><span class="sxs-lookup"><span data-stu-id="09f6a-122">The global block list includes things like private-use characters, control characters, undefined code points, and certain Unicode categories, such as the [Space_Separator category](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), excluding `U+0020 SPACE`.</span></span> <span data-ttu-id="09f6a-123">例如， `U+3000 IDEOGRAPHIC SPACE` 即使您指定 Unicode 範圍 [CJK 符號和標點符號 (u +3000-U + 303F) ](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) 做為您的允許清單，也會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="09f6a-123">For example, `U+3000 IDEOGRAPHIC SPACE` is escaped even if you specify Unicode range [CJK Symbols and Punctuation (U+3000-U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) as your allow list.</span></span>

<span data-ttu-id="09f6a-124">全域封鎖清單是每個 .NET Core 和 .NET 5 版本中已變更的實做詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09f6a-124">The global block list is an implementation detail that has changed in every release of .NET Core and in .NET 5.</span></span> <span data-ttu-id="09f6a-125">請勿相依于屬於 (成員或不是) 全域封鎖清單成員的字元。</span><span class="sxs-lookup"><span data-stu-id="09f6a-125">Don't take a dependency on a character being a member of (or not being a member of) the global block list.</span></span>

### <a name="encoder-specific-block-lists"></a><span data-ttu-id="09f6a-126">編碼器特定的區塊清單</span><span class="sxs-lookup"><span data-stu-id="09f6a-126">Encoder-specific block lists</span></span>

<span data-ttu-id="09f6a-127">編碼器特定封鎖的程式碼點範例包括 `'<'` 和 `'&'` 適用于 [HTML 編碼器](xref:System.Text.Encodings.Web.HtmlEncoder)、 `'\'` [JSON 編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder)，以及 `'%'` [URL 編碼器](xref:System.Text.Encodings.Web.UrlEncoder)。</span><span class="sxs-lookup"><span data-stu-id="09f6a-127">Examples of encoder-specific blocked code points include `'<'` and `'&'` for the [HTML encoder](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` for the [JSON encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder), and `'%'` for the [URL encoder](xref:System.Text.Encodings.Web.UrlEncoder).</span></span> <span data-ttu-id="09f6a-128">例如， `'&'` 即使連字號是在範圍內， `BasicLatin` 而且所有編碼器都會依預設初始化，HTML 編碼程式一律會將 & 符號 () `BasicLatin` 。</span><span class="sxs-lookup"><span data-stu-id="09f6a-128">For example, the HTML encoder always escapes ampersands (`'&'`), even though the ampersand is in the `BasicLatin` range and all the encoders are initialized with `BasicLatin` by default.</span></span>

## <a name="serialize-all-characters"></a><span data-ttu-id="09f6a-129">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="09f6a-129">Serialize all characters</span></span>

<span data-ttu-id="09f6a-130">若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09f6a-130">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="09f6a-131">相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼程式更寬鬆，可讓字元通過非重設密碼：</span><span class="sxs-lookup"><span data-stu-id="09f6a-131">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="09f6a-132">它不會對 HTML 敏感的字元（例如、、和）進行換用 `<` `>` `&` `'` 。</span><span class="sxs-lookup"><span data-stu-id="09f6a-132">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="09f6a-133">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深度防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在 *字元集* 上所產生的。</span><span class="sxs-lookup"><span data-stu-id="09f6a-133">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="09f6a-134">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="09f6a-134">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="09f6a-135">例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。</span><span class="sxs-lookup"><span data-stu-id="09f6a-135">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="09f6a-136">絕不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="09f6a-136">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="09f6a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09f6a-137">See also</span></span>

* [<span data-ttu-id="09f6a-138">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="09f6a-138">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="09f6a-139">如何將 JSON 序列化及還原序列化</span><span class="sxs-lookup"><span data-stu-id="09f6a-139">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="09f6a-140">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="09f6a-140">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="09f6a-141">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="09f6a-141">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="09f6a-142">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="09f6a-142">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="09f6a-143">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="09f6a-143">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="09f6a-144">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="09f6a-144">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="09f6a-145">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="09f6a-145">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="09f6a-146">保留參考</span><span class="sxs-lookup"><span data-stu-id="09f6a-146">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="09f6a-147">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="09f6a-147">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="09f6a-148">多型序列化</span><span class="sxs-lookup"><span data-stu-id="09f6a-148">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="09f6a-149">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="09f6a-149">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="09f6a-150">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="09f6a-150">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="09f6a-151">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="09f6a-151">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="09f6a-152">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="09f6a-152">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="09f6a-153">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="09f6a-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="09f6a-154">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="09f6a-154">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
