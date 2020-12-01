---
title: 如何使用自訂字元編碼 System.Text.Json
description: 瞭解如何自訂字元編碼，以及如何在 .NET 中從 JSON 序列化和還原序列化。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: f6a50a3ca2a5e871294cf7c056cbf197a61cd668
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439938"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="9830e-103">如何使用自訂字元編碼 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="9830e-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="9830e-104">根據預設，序列化程式會將所有非 ASCII 字元全部轉義。</span><span class="sxs-lookup"><span data-stu-id="9830e-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="9830e-105">也就是說，它會將它們取代 `\uxxxx` 為 `xxxx` 字元的 Unicode 代碼。</span><span class="sxs-lookup"><span data-stu-id="9830e-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="9830e-106">例如，如果 `Summary` 下列 JSON 中的屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9830e-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="9830e-107">將語言字元集序列化</span><span class="sxs-lookup"><span data-stu-id="9830e-107">Serialize language character sets</span></span>

<span data-ttu-id="9830e-108">若要將一或多個語言的字元集)  (s，而不進行任何轉義，請在建立實例時指定 [Unicode 範圍 () ](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9830e-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="9830e-109">此程式碼不會將斯拉夫文或希臘文字元換成。</span><span class="sxs-lookup"><span data-stu-id="9830e-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="9830e-110">如果 `Summary` 屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9830e-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="9830e-111">若要在不經過轉義的情況下序列化所有語言集，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9830e-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="9830e-112">序列化特定字元</span><span class="sxs-lookup"><span data-stu-id="9830e-112">Serialize specific characters</span></span>

<span data-ttu-id="9830e-113">替代方法是指定您想要允許的個別字元，而不需要經過轉義。</span><span class="sxs-lookup"><span data-stu-id="9830e-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="9830e-114">下列範例只會序列化的前兩個字元 `жарко` ：</span><span class="sxs-lookup"><span data-stu-id="9830e-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="9830e-115">以下是上述程式碼所產生的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="9830e-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="9830e-116">序列化所有字元</span><span class="sxs-lookup"><span data-stu-id="9830e-116">Serialize all characters</span></span>

<span data-ttu-id="9830e-117">若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9830e-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="9830e-118">相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼程式更寬鬆，可讓字元通過非重設密碼：</span><span class="sxs-lookup"><span data-stu-id="9830e-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="9830e-119">它不會對 HTML 敏感的字元（例如、、和）進行換用 `<` `>` `&` `'` 。</span><span class="sxs-lookup"><span data-stu-id="9830e-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="9830e-120">它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深度防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在 *字元集* 上所產生的。</span><span class="sxs-lookup"><span data-stu-id="9830e-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="9830e-121">只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。</span><span class="sxs-lookup"><span data-stu-id="9830e-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="9830e-122">例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。</span><span class="sxs-lookup"><span data-stu-id="9830e-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="9830e-123">絕不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="9830e-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9830e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9830e-124">See also</span></span>

* [<span data-ttu-id="9830e-125">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="9830e-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9830e-126">如何撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="9830e-126">How to write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="9830e-127">如何撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="9830e-127">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="9830e-128">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9830e-128">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
