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

根據預設，編碼器會以 <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> 範圍初始化。

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

## <a name="block-lists"></a>封鎖清單

上述各節顯示如何指定您不想要加入的程式碼點或範圍的允許清單。 不過，有全域和編碼器專屬的區塊清單，可覆寫您允許清單中的特定程式碼點。 區塊清單中的程式碼點一律會進行轉義，即使它們包含在您的允許清單中也一樣。

### <a name="global-block-list"></a>全域封鎖清單

全域封鎖清單包括私用字元、控制字元、未定義的程式碼點，以及某些 Unicode 類別，例如 [Space_Separator 分類](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)（排除） `U+0020 SPACE` 。 例如， `U+3000 IDEOGRAPHIC SPACE` 即使您指定 Unicode 範圍 [CJK 符號和標點符號 (u +3000-U + 303F) ](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) 做為您的允許清單，也會進行轉義。

全域封鎖清單是每個 .NET Core 和 .NET 5 版本中已變更的實做詳細資料。 請勿相依于屬於 (成員或不是) 全域封鎖清單成員的字元。

### <a name="encoder-specific-block-lists"></a>編碼器特定的區塊清單

編碼器特定封鎖的程式碼點範例包括 `'<'` 和 `'&'` 適用于 [HTML 編碼器](xref:System.Text.Encodings.Web.HtmlEncoder)、 `'\'` [JSON 編碼器](xref:System.Text.Encodings.Web.JavaScriptEncoder)，以及 `'%'` [URL 編碼器](xref:System.Text.Encodings.Web.UrlEncoder)。 例如， `'&'` 即使連字號是在範圍內， `BasicLatin` 而且所有編碼器都會依預設初始化，HTML 編碼程式一律會將 & 符號 () `BasicLatin` 。

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
* [如何將 JSON 序列化及還原序列化](system-text-json-how-to.md)
* [具現化 JsonSerializerOptions 實例](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [忽略屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留參考](system-text-json-preserve-references.md)
* [不可變型別及非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [從遷移 Newtonsoft.Json 至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
