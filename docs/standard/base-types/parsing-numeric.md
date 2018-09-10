---
title: 在 .NET 中剖析數值字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07ad8b278f6a44fce78bccc980acdc0dc93b1a7a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193246"
---
# <a name="parsing-numeric-strings-in-net"></a>在 .NET 中剖析數值字串
所有數值類型皆有兩個靜態剖析方法：`Parse` 和 `TryParse`，可將數字的字串表示轉換成數值類型。 這些方法可讓您剖析使用[標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)和[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)中記錄的格式字串所產生的字串。 根據預設，`Parse` 和 `TryParse` 方法只能將包含十進位數字的字串成功轉換為整數值。 它們可以將包含整數和小數的十進位數字、群組分隔符號，以及小數分隔符號的字串，成功轉換為浮點值。 如果作業失敗，即 `TryParse` 方法傳回 `false`，則 `Parse` 方法會擲回例外狀況。  
  
## <a name="parsing-and-format-providers"></a>剖析和格式提供者  
 數值的字串表示通常會隨文化特性而不同。 數值字串的元素都會因文化特性而有所不同，包括貨幣符號、群組 (或千分位) 分隔符號以及小數分隔符號。 剖析方法會隱含或明確使用能夠辨識這些特定文化特性變化的格式提供者。 如果 `Parse` 或 `TryParse` 方法的呼叫中未指定格式提供者，則會使用與目前執行緒文化特性相關聯的格式提供者 (<xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> 屬性所傳回的 <xref:System.Globalization.NumberFormatInfo> 物件)。  
  
 格式提供者會由 <xref:System.IFormatProvider> 實作來代表。 此介面具有單一成員 (<xref:System.IFormatProvider.GetFormat%2A> 方法)，它的單一參數是表示要格式化之類型的 <xref:System.Type> 物件。 此方法會傳回提供格式設定資訊的物件。 .NET 支援下列兩個可用來剖析數值字串的 <xref:System.IFormatProvider> 實作：  
  
-   <xref:System.Globalization.CultureInfo> 物件，它的 <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> 方法會傳回提供文化特性特定格式資訊的 <xref:System.Globalization.NumberFormatInfo> 物件。  
  
-   <xref:System.Globalization.NumberFormatInfo> 物件，它的 <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> 方法會傳回本身。  
  
 下列範例會嘗試將陣列中的每個字串轉換為 <xref:System.Double> 值。 它會先嘗試使用反映英文 (美國) 文化特性慣例的格式提供者剖析字串。 如果此作業擲回 <xref:System.FormatException>，它就會嘗試使用可反映法文 (法國) 文化特性慣例的格式提供者來剖析字串。  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>剖析和 NumberStyles 值  
 剖析作業可處理的樣式元素 (例如空白字元、群組分隔符號和小數分隔符號)，會由 <xref:System.Globalization.NumberStyles> 列舉值來定義。 根據預設，代表整數值的字串會使用 <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> 值進行剖析，這僅允許數字、前置和後置空白字元，以及前置正負號。 表示浮點值的字串會使用 <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> 和 <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> 值的組合進行剖析，此複合樣式允許十進位數字，以及前置和後置空白字元、前置正負號、小數分隔符號、群組分隔符號和指數。 您可以藉由呼叫包含 <xref:System.Globalization.NumberStyles> 類型參數之 `Parse` 或 `TryParse` 方法的多載，並設定一或多個 <xref:System.Globalization.NumberStyles> 旗標，來控制可在字串中顯示的樣式元素，使剖析作業得以成功進行。  
  
 例如，包含群組分隔符號的字串無法使用 <xref:System.Int32> 方法轉換為 <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> 值。 然而，如果您使用 <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> 旗標，則轉換會成功，如下列範例所示。  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  剖析作業一律使用特定文化特性的格式化慣例。 如果未藉由傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.NumberFormatInfo> 物件來指定文化特性，就會使用與目前執行緒相關聯的文化特性。  
  
 下表列出 <xref:System.Globalization.NumberStyles> 列舉的成員，並說明它們對剖析作業的影響。  
  
|NumberStyles 值|對要剖析字串的影響|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|只允許數字。|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|允許小數分隔符號和小數位。 若為整數值，小數位只允許零。 有效的小數分隔符號會由 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> 屬性來決定。|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|可以使用 "e" 或 "E" 字元表示指數標記法。 如需詳細資訊，請參閱 <xref:System.Globalization.NumberStyles>。|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|可以使用前置空白字元。|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|可以使用後置空白字元。|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|數字前面可以使用正負號。|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|數字後面可以使用正負號。|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|可以使用括號表示負數值。|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|允許群組分隔符號。 群組分隔符號字元會由 <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> 屬性來決定。|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|允許使用貨幣符號。 貨幣符號會由 <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> 屬性來定義。|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|要剖析的字串會解譯為十六進位數字。 它可以包含十六進位數字 0-9、A-F 和 a-f。 這個旗標只能用於剖析整數值。|  
  
 此外，<xref:System.Globalization.NumberStyles> 列舉提供下列複合樣式，其中包括多個 <xref:System.Globalization.NumberStyles> 旗標。  
  
|複合的 NumberStyles 值|包含成員|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> 和 <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> 樣式。 這是用來剖析整數值的預設樣式。|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> 及 <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> 樣式。|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> 及 <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> 樣式。|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> 和 <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> 以外的所有樣式。|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> 以外的所有樣式。|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|包含 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> 和 <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> 樣式。|  
  
## <a name="parsing-and-unicode-digits"></a>剖析和 Unicode 數字  
 Unicode 標準會定義各種書寫系統中數字的字碼指標。 例如，U+0030 到 U+0039 的字碼指標表示基本拉丁文數字 0 到 9，U+09E6 到 U+09EF 字碼指標表示孟加拉文數字 0 到 9，而 U+FF10 到 U+FF19 字碼指數表示全形數字 0 到 9。 不過，剖析方法唯一認識的數字是基本拉丁文數字 0-9 與 U+0030 到 U+0039 字碼指標。 如果將包含任何其他數字的字串傳遞給數值剖析方法，則該方法會擲回 <xref:System.FormatException>。  
  
 下列範例會使用 <xref:System.Int32.Parse%2A?displayProperty=nameWithType> 方法，來剖析以不同書寫系統的數字組成的字串。 如範例的輸出所示，嘗試剖析基本拉丁文數字會成功，而嘗試剖析全型、阿拉伯-印度文和孟加拉文數字則會失敗。  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.NumberStyles>  
- [剖析字串](../../../docs/standard/base-types/parsing-strings.md)  
- [格式化類型](../../../docs/standard/base-types/formatting-types.md)
