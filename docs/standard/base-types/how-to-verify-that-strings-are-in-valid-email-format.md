---
title: 如何確認字串是否為有效的電子郵件格式
description: 閱讀如何在 .NET 中使用正則運算式來驗證字串是否為有效電子郵件格式的範例。
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 07b8e31e4a0203b87492eb01ab686a1c56f5565d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889071"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>如何確認字串是否為有效的電子郵件格式

下列範例會使用規則運算式來確認字串是否為有效的電子郵件格式。

這個正則運算式相當簡單，可作為電子郵件的實際用途。 使用正則運算式來驗證電子郵件有助於確保電子郵件的結構正確無誤，但它並不是確認電子郵件實際存在的替代方法。

✔️使用小型的正則運算式來檢查電子郵件的有效結構。

✔️會將測試電子郵件傳送至應用程式使用者所提供的位址。

❌ 請勿使用正則運算式作為驗證電子郵件的唯一方式。

如果您嘗試建立 _完美_ 的正則運算式來驗證電子郵件的結構是否正確，則運算式會變得很複雜，因此很難進行 debug 錯或改進。 正則運算式無法驗證電子郵件是否存在，即使它的結構正確。 驗證電子郵件的最佳方式是將測試電子郵件傳送至位址。

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>範例

此範例會定義 `IsValidEmail` 方法， `true` 如果字串包含有效的電子郵件地址，則會傳回; `false` 如果沒有，則不會採取其他任何動作。

為了驗證電子郵件地址是否有效， `IsValidEmail` 方法會以 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 規則運算式模式呼叫 `(@)(.+)$` 方法，從電子郵件地址分離出網域名稱。 第三個參數是 <xref:System.Text.RegularExpressions.MatchEvaluator> 委派，用於表示處理並取代相符文字的方法。 規則運算式模式解譯如下。

| 模式 | 描述                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | 比對 @ 字元。 這個部分是第一個捕獲群組。                           |
| `(.+)`  | 比對出現一次或多次的任何字元。 這部分是第二個捕獲群組。 |
| `$`     | 在字串的結尾結束比對。                                             |

網域名稱會連同 @ 字元一併傳遞至 `DomainMapper` 方法，該方法會使用 <xref:System.Globalization.IdnMapping> 類別將 US-ASCII 字元範圍以外的 Unicode 字元轉譯為 Punycode。 如果 `invalid` 方法在網域名稱中偵測到任何無效字元，則方法也會將 `True` 旗標設定為 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。 方法會將前面加上 @ 符號的 Punycode 網域名稱傳回至 `IsValidEmail` 方法。

> [!TIP]
> 建議您使用簡單的 `(@)(.+)$` 正則運算式模式來正規化網域，然後傳回值，指出它已通過或失敗。 不過，本文中的範例會說明如何進一步使用正則運算式來驗證電子郵件。 無論您如何驗證電子郵件，都應該一律將測試電子郵件傳送至該位址，以確保其存在。

接著 `IsValidEmail` 方法會呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法，確認位址符合規則運算式模式。

`IsValidEmail`方法只會判斷電子郵件地址是否有效，而不會驗證電子郵件是否存在。 此外，此 `IsValidEmail` 方法不會驗證最上層功能變數名稱是否為 [IANA 根區域資料庫](https://www.iana.org/domains/root/db)所列的有效功能變數名稱，這需要查閱作業。

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

在這個範例中，規則運算式模式 `^[^@\s]+@[^@\s]+\.[^@\s]+$` 會依下表所示的方式解譯。 使用旗標來編譯正則運算式 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 。

| 模式   | 描述                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | 在字串開頭開始比對。                                              |
| `[^@\s]+` | 比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。 |
| `@`       | 比對 @ 字元。                                                                   |
| `[^@\s]+` | 比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。 |
| `\.`      | 符合單一句號字元。                                                         |
| `[^@\s]+` | 比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。 |
| `$`       | 在字串的結尾結束比對。                                                  |

> [!IMPORTANT]
> 此正則運算式並非用來涵蓋有效電子郵件地址的每個層面。 它是一個範例，可讓您視需要擴充。

## <a name="see-also"></a>請參閱

- [.NET 規則運算式](regular-expressions.md)
- [一個電子郵件地址驗證的距離為何？](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
