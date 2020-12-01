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
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a>如何使用自訂字元編碼 System.Text.Json

根據預設，序列化程式會將所有非 ASCII 字元全部轉義。 也就是說，它會將它們取代 `\uxxxx` 為 `xxxx` 字元的 Unicode 代碼。 例如，如果 `Summary` 下列 JSON 中的屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a>將語言字元集序列化

若要將一或多個語言的字元集)  (s，而不進行任何轉義，請在建立實例時指定 [Unicode 範圍 () ](xref:System.Text.Unicode.UnicodeRanges) <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

此程式碼不會將斯拉夫文或希臘文字元換成。 如果 `Summary` 屬性設定為斯拉夫 `жарко` ，則 `WeatherForecast` 物件會序列化，如下列範例所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

若要在不經過轉義的情況下序列化所有語言集，請使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> 。

## <a name="serialize-specific-characters"></a>序列化特定字元

替代方法是指定您想要允許的個別字元，而不需要經過轉義。 下列範例只會序列化的前兩個字元 `жарко` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

以下是上述程式碼所產生的 JSON 範例：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a>序列化所有字元

若要最小化可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> 的轉義，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> 相較于預設編碼器， `UnsafeRelaxedJsonEscaping` 編碼程式更寬鬆，可讓字元通過非重設密碼：
>
> * 它不會對 HTML 敏感的字元（例如、、和）進行換用 `<` `>` `&` `'` 。
> * 它不會針對 XSS 或資訊洩漏攻擊提供任何額外的深度防禦保護，例如，可能是因為用戶端和伺服器 disagreeing 在 *字元集* 上所產生的。
>
> 只有在已知用戶端會將產生的承載解讀為 UTF-8 編碼的 JSON 時，才使用 unsafe 編碼器。 例如，如果伺服器正在傳送回應標頭，您可以使用它 `Content-Type: application/json; charset=utf-8` 。 絕不允許將原始 `UnsafeRelaxedJsonEscaping` 輸出發出至 HTML 網頁或 `<script>` 元素。

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [如何撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
