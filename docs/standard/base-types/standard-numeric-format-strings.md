---
title: 標準數值格式字串
ms.date: 06/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 245492a8a903593dc1532b67ed96224e171aad7e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804727"
---
# <a name="standard-numeric-format-strings"></a>標準數值格式字串

標準數值格式字串會用來格式化一般數字類型。 標準數值格式字串會採用 `Axx` 格式，其中：

- `A` 是稱為「格式規範」  的單一字母字元。 任何包含一個以上字母字元 (包含泛空白字元 (White Space)) 的數值格式字串都會解譯為自訂數值格式字串。 如需詳細資訊，請參閱[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。

- `xx` 是稱為「精確度規範」  的選用性整數。 精確度規範的範圍從 0 到 99，而且會影響結果內的位數。 請注意，精確度規範可控制數字字串表示法中的位數。 它不會捨入數字本身。 若要執行捨入運算，請使用 <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>、<xref:System.Math.Floor%2A?displayProperty=nameWithType> 或 <xref:System.Math.Round%2A?displayProperty=nameWithType> 方法。

  當「有效位數規範」  控制結果字串中小數點後的位數，結果字串會反映已四捨五入為最接近無限精確度之可代表結果的數字。 若有兩個相等的近似可代表結果：
  - **在 .NET Framework 與 .NET Core (最高版本 .NET Core 2.0) 上**，執行階段會選取具有較大之最不顯著位數 (亦即，使用 <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>) 的結果。
  - **在 .NET Core 2.1 與更新版本上**，執行階段會選取具有偶數最不顯著位數 (亦即，使用 <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>) 的結果。

  > [!NOTE]
  > 有效位數規範可判斷結果字串中的位數。 若要使用前置或尾端空格填補結果字串，請使用[複合格式設定](../../../docs/standard/base-types/composite-formatting.md)功能，並在格式項目中定義「對齊元件」  。

標準數值格式字串受到下列各項支援：

- 所有數值類型之 `ToString` 方法的一些多載。 例如，您可以將數值格式字串提供給 <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> 和 <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法。

- .NET 的[複合格式功能](../../../docs/standard/base-types/composite-formatting.md)，此功能會由 <xref:System.Console> 與 <xref:System.IO.StreamWriter> 類別的一些 `Write` 和 `WriteLine` 方法，以及 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法和 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> 方法所使用。 複合格式功能可讓您將多個資料項目的字串表示法包含在單一字串中，以指定欄位寬度，以及對齊欄位中的數字。 如需詳細資訊，請參閱[複合格式設定](../../../docs/standard/base-types/composite-formatting.md)。

- C# 和 Visual Basic 中的[字串插值](../../csharp/language-reference/tokens/interpolated.md)，相較於複合格式字串，其可提供簡化的語法。

> [!TIP]
> 您可以下載 [格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)，這個應用程式可讓您將格式字串套用至數值或日期和時間值，並且顯示結果字串。

<a name="table"></a>下表描述標準數值格式規範，並顯示每個格式範例所產生的範例輸出。 如需使用標準數值格式字串的詳細資訊，請參閱[備註](#NotesStandardFormatting)一節，如需其用法的完整解說，請參閱[範例](#example)一節。

|格式規範|名稱|說明|範例|
|----------------------|----------|-----------------|--------------|
|"C" 或 "c"|貨幣|結果︰貨幣值。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：小數位數。<br /><br /> 預設的有效位數規範：由 <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> 定義。<br /><br /> 詳細資訊：[貨幣 ("C") 格式規範](#CFormatString)。|123.456 ("C", en-US) -> `$123.46`<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> `($123.456)`<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" 或 "d"|Decimal|結果︰帶選擇性負號的整數位數。<br /><br /> 支援下列項目：僅限整數類型。<br /><br /> 有效位數規範：最少位數。<br /><br /> 預設的有效位數規範：必要的最少位數。<br /><br /> 詳細資訊：[十進位 ("D") 格式規範](#DFormatString)。|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|
|"E" 或 "e"|指數 (科學記號)|結果︰指數標記法。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：小數位數。<br /><br /> 預設的有效位數規範：6.<br /><br /> 詳細資訊：[指數 ("E") 格式規範](#EFormatString)。|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|"F" 或 "f"|固定點|結果︰帶選擇性負號的整數和小數位數。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：小數位數。<br /><br /> 預設的有效位數規範：由 <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> 定義。<br /><br /> 詳細資訊：[固定點 ("F") 格式規範](#FFormatString)。|1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|
|"G" 或 "g"|一般|結果︰固定點和科學記號標記法兩者中最精簡的一個。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：有效位數。<br /><br /> 預設的有效位數規範：取決於數值類型。<br /><br /> 詳細資訊：[一般 ("G") 格式規範](#GFormatString)。|-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|
|"N" 或 "n"|Number|結果︰帶選擇性負號的整數和小數位數、群組分隔符號，以及小數分隔符號。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：想要的小數位數。<br /><br /> 預設的有效位數規範：由 <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> 定義。<br /><br /> 詳細資訊：[數值 ("N") 格式規範](#NFormatString)。|1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|
|"P" 或 "p"|百分比|結果︰乘以 100 並加上百分比符號來顯示的數字。<br /><br /> 支援下列項目：所有數值類型。<br /><br /> 有效位數規範：想要的小數位數。<br /><br /> 預設的有效位數規範：由 <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType> 定義。<br /><br /> 詳細資訊：[百分比 ("P") 格式規範](#PFormatString)。|1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|
|"R" 或 "r"|來回|結果︰可以來回轉換為相同數字的字串。<br /><br /> 支援的類型：<xref:System.Single>、<xref:System.Double> 和 <xref:System.Numerics.BigInteger>。<br /><br /> 注意：建議僅用於 <xref:System.Numerics.BigInteger> 類型。 針對 <xref:System.Double> 類型，使用 "G17"；針對 <xref:System.Single> 類型，使用 "G9"。 <br> 有效位數規範：忽略。<br /><br /> 詳細資訊：[來回 ("R") 格式規範](#RFormatString)。|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|
|"X" 或 "x"|十六進位|結果︰十六進位字串。<br /><br /> 支援下列項目：僅限整數類型。<br /><br /> 有效位數規範：結果字串中的位數。<br /><br /> 詳細資訊：[十六進位 ("X") 格式規範](#XFormatString)。|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|任何其他單一字元|未知的規範|結果︰在執行階段擲回 <xref:System.FormatException>。||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>使用標準數值格式字串

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

使用標準數值格式字串來定義數值的格式有兩種方式：

- 您可以將它傳遞至具有 `ToString` 參數之 `format` 方法的多載。 下列範例會以目前的文化特定 (在此範例中是 en-US 文化特性) 來將數值格式化為貨幣字串。

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- 您可以在搭配 <xref:System.String.Format%2A?displayProperty=nameWithType>、<xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> 等方法一起使用的格式項目中，提供它作為 `formatString` 引數。 如需詳細資訊，請參閱[複合格式設定](../../../docs/standard/base-types/composite-formatting.md)。 下列範例會使用格式項目，在字串中插入貨幣值。

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  您可以選擇性地提供 `alignment` 引數，來指定數值欄位的寬度，以及其值為靠右或靠左對齊。 下列範例在 28 個字元的欄位中將貨幣值靠左對齊，並在 14 個字元的欄位中將貨幣值靠右對齊。

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- 它可以提供作為字串內插補點的插補運算式項目中的 `formatString` 引數。 如需詳細資訊，請參閱 C# 參考中的[字串內插補點](../../csharp/language-reference/tokens/interpolated.md)主題，或 Visual Basic 參考中的[字串內插補點](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)主題。

下列各節提供每個標準數值格式字串的詳細資訊。

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>貨幣 ("C") 格式規範

"C" (表示貨幣) 格式規範會將數字轉換為表示貨幣金額的字串。 精確度規範表示在結果字串中所需要的小數位數。 如果省略精確度規範，則預設有效位數會由 <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> 屬性定義。

如果要格式化的值擁有的小數位數超過指定或預設的小數位數，則分數值會在結果字串中四捨五入。 如果指定的小數位數右邊的值為 5 或更大值，則結果字串中的最後一位數會遠離零四捨五入。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出 <xref:System.Globalization.NumberFormatInfo> 屬性，這些屬性控制傳回之字串的格式設定。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|定義正值的貨幣符號位置。|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|定義負值的貨幣符號位置，並指定負號是以括號還是 <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> 屬性來表示。|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義在 <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> 表示不使用括號時所使用的負號。|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|定義貨幣符號。|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|定義貨幣值中的預設小數位數。 您可以使用有效位數規範來覆寫這個值。|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|定義分隔整數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|定義分隔整數群組的字串。|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|定義整數部分的每個群組中出現的整數位數。|

下列範例會使用貨幣格式規範格式化 <xref:System.Double> 值。

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp-interactive[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[回到表格](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>十進位 ("D") 格式規範

"D" (表示十進位) 格式規範會將數字轉換為十進位數 (0-9) 的字串，如果數字為負數，則在前面加上負號。 只有整數類資料類型 (Integral Type) 才支援這個格式。

精確度規範指示產生的字串中所需要的最少位數。 如果有必要，數值以零填補其左邊，產生精確度規範所指定的位數。 如果未指定精確度規範，則預設值為在不填補前置零的情況下，表示整數所需的最小值。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 如下表所示，只有一個屬性會影響結果字串的格式設定。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|

下列範例會使用十進位格式規範來格式化 <xref:System.Int32> 值。

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[回到表格](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>指數 ("E") 格式規範

指數 ("E") 格式規範會將數字轉換為 "-d.ddd…E+ddd" 或 "-d.ddd…e+ddd" 形式的字串，其中 "d" 表示數字 (0-9)。 字串以負號開始，如果數值為負數的話。 在小數點前面永遠會有確切一個位數。

精確度規範指示小數點之後需要的位數。 如果省略精確度規範，則使用小數點之後有六位數的預設值。

格式規範的大小寫表示要在指數之前加上 "E" 還是 "e"。 指數永遠由正號或負號和最少三位數所組成。 必要時，指數將以零填補來符合指定的最少位數。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出 <xref:System.Globalization.NumberFormatInfo> 屬性，這些屬性控制傳回之字串的格式設定。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字在係數和指數部分都是負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|定義將係數中的整數位數與小數位數分隔的字串。|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|定義表示指數為正數的字串。|

下列範例會使用指數格式規範來格式化 <xref:System.Double> 值。

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp-interactive[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[回到表格](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>固定點 ("F") 格式規範

固定點 ("F") 格式規範，會將數字轉換為 "-ddd.ddd…" 形式的字串，其中的每個 "d" 代表一個數字 (0-9)。 字串以負號開始，如果數值為負數的話。

精確度規範指示所需要的小數位數。 如果省略精確度規範，則會由目前 <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> 屬性提供數值有效位數。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出 <xref:System.Globalization.NumberFormatInfo> 物件的屬性，這些屬性控制結果字串的格式設定。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|定義分隔整數位數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|定義小數位數的預設數目。 您可以使用有效位數規範來覆寫這個值。|

下列範例會使用定點格式規範格式化 <xref:System.Double> 和 <xref:System.Int32> 值。

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp-interactive[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[回到表格](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>一般 ("G") 格式規範

一般 ("G") 格式規範會將數字轉換為固定點和科學標記法兩者中較精簡的一個，視數字的類型以及精確度規範是否存在而定。 精確度規範定義結果字串中最多可顯示的有效位數。 如果精確度規範已省略或為零，則由數字的類型決定預設有效位數，如下表所示。

|數字類型|預設有效位數|
|------------------|-----------------------|
|<xref:System.Byte> 或 <xref:System.SByte>|3 位數|
|<xref:System.Int16> 或 <xref:System.UInt16>|5 位數|
|<xref:System.Int32> 或 <xref:System.UInt32>|10 位數|
|<xref:System.Int64>|19 位數|
|<xref:System.UInt64>|20 位數|
|<xref:System.Numerics.BigInteger>|無限制 (如同 ["R"](#RFormatString))|
|<xref:System.Single>|7 位數|
|<xref:System.Double>|15 位數|
|<xref:System.Decimal>|29 位數|

如果以科學標記法來表示數字所產生的指數大於 -5 而且小於精確度規範，則會使用固定點標記法，否則使用科學標記法。 必要時，結果會包含小數點並省略小數點後最後幾個零。 如果精確度規範存在，且結果中的有效位數超過指定的有效位數，則會四捨五入來移除超出的尾端位數。

不過，如果數字是 <xref:System.Decimal>，而且省略精確度規範，則一律會使用固定點標記法，並且保留尾端的零。

使用科學標記法時，結果中的指數前面會加上 "E" (如果格式規範為 "G") 或 "e" (如果格式規範為 "g")。 指數至少包含兩位數。 這不同於指數格式規範所產生的科學標記法格式，此格式會在指數中包含至少三位數。

請注意，搭配 <xref:System.Double> 值使用時，"G17" 格式規範會確保原始的 <xref:System.Double> 值可成功地反覆存取。 這是因為 <xref:System.Double> 是符合 IEEE 754-2008 規範的雙精確度 (`binary64`) 浮點數，可提供最多 17 個有效位數的精確度。 建議您使用它，而不是 ["R" 格式規範](#RFormatString)，因為在某些情況下，"R" 無法成功地反覆存取雙精確度浮點值。 下列範例將說明一個這類案例。

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

搭配 <xref:System.Single> 值使用時，"G9" 格式規範會確保原始的 <xref:System.Single> 值可成功地反覆存取。 這是因為 <xref:System.Single> 是符合 IEEE 754-2008 規範的單精確度 (`binary32`) 浮點數，可提供最多九個有效位數的精確度。 基於效能考量，我們建議使用它，而不要使用 ["R" 格式規範](#RFormatString)。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 <xref:System.Globalization.NumberFormatInfo> 屬性。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|定義分隔整數位數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|定義表示指數為正數的字串。|

下列範例會使用一般格式規範來格式化各種浮點數值。

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp-interactive[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[回到表格](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>數值 ("N") 格式規範

數字 ("N") 格式規範會將數字轉換為 "-d,ddd,ddd.ddd…" 形式的字串，其中 "-" 表示負數符號 (如有需要)、"d" 表示數字 (0-9)、"," 表示群組分隔符號，而 "." 表示小數點符號。 精確度規範指示小數點之後需要的位數。 如果省略精確度規範，則小數位數會由目前的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> 屬性定義。

結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 <xref:System.Globalization.NumberFormatInfo> 屬性。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|定義負值的格式，並指定負號是以括號還是 <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> 屬性來表示。|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|定義在群組分隔符號之間出現的整數位數。|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|定義分隔整數群組的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|定義分隔整數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|定義小數位數的預設數目。 您可以使用精確度規範來覆寫這個值。|

下列範例會使用數字格式規範來格式化各種浮點數值。

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp-interactive[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[回到表格](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>百分比 ("P") 格式規範

百分比 ("P") 格式規範會將數字乘以 100，然後轉換為表示百分比的字串。 精確度規範指示所需要的小數位數。 如果省略精確度規範，則會使用目前 <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> 屬性所提供的預設數值有效位數。

下表列出 <xref:System.Globalization.NumberFormatInfo> 屬性，這些屬性控制傳回之字串的格式設定。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|定義正值的百分比符號位置。|
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|定義負值的百分比符號位置和負號位置。|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|定義百分比符號。|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|定義百分比值中的預設小數位數。 您可以使用有效位數規範來覆寫這個值。|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|定義分隔整數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|定義分隔整數群組的字串。|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|定義整數部分的每個群組中出現的整數位數。|

下列範例會使用百分比格式規範來格式化浮點數值。

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp-interactive[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[回到表格](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>來回 ("R") 格式規範

反覆存取 ("R") 格式規範會嘗試確保可將轉換為字串的數值剖析回相同的數值。 只有 <xref:System.Single>、<xref:System.Double> 和 <xref:System.Numerics.BigInteger> 類型才支援這個格式。

針對 <xref:System.Double> 值，"R" 格式規範在某些情況下無法成功地反覆存取原始值。 針對 <xref:System.Double> 和 <xref:System.Single> 值，它也提供相當差的效能。 我們建議您針對 <xref:System.Double> 值改用 ["G17"](#GFormatString) 格式規範以及 ["G9"](#GFormatString) 格式規範，以便成功地反覆存取 <xref:System.Single> 值。

使用這個規範來格式化 <xref:System.Numerics.BigInteger> 值時，這個值的字串表示會包含 <xref:System.Numerics.BigInteger> 值中的所有有效位數。

雖然您可以包含精確度規範，但該規範會被忽略。 使用來回規範時，這個規範優先於精確度規範。
結果字串會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 <xref:System.Globalization.NumberFormatInfo> 屬性。

|NumberFormatInfo 屬性|說明|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|定義表示數字為負數的字串。|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|定義分隔整數位數與小數位數的字串。|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|定義表示指數為正數的字串。|

下列範例會使用反覆存取格式規範來將 <xref:System.Numerics.BigInteger> 值格式化。

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> 在某些情況下，使用 "R" 標準數值格式字串格式化的 <xref:System.Double> 值，如果使用 `/platform:x64` 或 `/platform:anycpu` 參數編譯並在 64 位元系統上執行，則不會成功地反覆存取。 如需詳細資訊，請參閱下一段內容。

若要解決以 "R" 標準數值格式字串格式化的 <xref:System.Double> 值，在使用 `/platform:x64` 或 `/platform:anycpu` 參數編譯並於 64 位元系統上執行時，不會成功地反覆存取的問題，您可以使用 "G17" 標準數值格式字串格式化 <xref:System.Double> 值。 下列範例使用 "R" 格式字串，搭配不會成功反覆存取的 <xref:System.Double> 值，並且也會使用 "G17" 格式字串來成功反覆存取原始值。

[!code-csharp-interactive[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[回到表格](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>十六進位 ("X") 格式規範

十六進位 ("X") 格式規範會將數字轉換為十六進位數字的字串。 格式規範的大小寫表示對於大於 9 的十六進位數字，要使用大寫還是小寫字元。 例如，使用 "X" 會產生 "ABCDEF"，使用 "x" 則會產生 "abcdef"。 只有整數類資料類型 (Integral Type) 才支援這個格式。

精確度規範指示產生的字串中所需要的最少位數。 如果有必要，數值以零填補其左邊，產生精確度規範所指定的位數。

結果字串不受目前 <xref:System.Globalization.NumberFormatInfo> 物件的格式設定資訊所影響。

下列範例會使用十六進位格式規範格式化 <xref:System.Int32> 值。

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[回到表格](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>注意

### <a name="control-panel-settings"></a>控制台設定值

[控制台] 中 [ **地區及語言選項]** 項目的設定會影響格式化作業所產生的結果字串。 這些設定是用來初始化與目前執行緒文化特性相關的 <xref:System.Globalization.NumberFormatInfo> 物件，該物件會提供用來管理格式的值。 使用不同設定的電腦會產生不同的結果字串。

此外，如果使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> 建構函式來將新的 <xref:System.Globalization.CultureInfo> 物件具現化，而此物件代表的文化特性與目前系統文化特性相同，則 [控制台] 中的 [地區及語言選項]  項目所建立的任何自訂都會套用至新的 <xref:System.Globalization.CultureInfo> 物件。 您可以使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來建立不反映系統自訂的 <xref:System.Globalization.CultureInfo> 物件。

### <a name="numberformatinfo-properties"></a>NumberFormatInfo 屬性

格式會受到目前 <xref:System.Globalization.NumberFormatInfo> 物件屬性的影響，而此物件是由目前執行緒文化特性隱含提供或由叫用格式之方法的 <xref:System.IFormatProvider> 參數明確提供。 為該參數指定 <xref:System.Globalization.NumberFormatInfo> 或 <xref:System.Globalization.CultureInfo> 物件。

> [!NOTE]
> 如需有關自訂格式化數值所使用之模式或字串的詳細資訊，請參閱 <xref:System.Globalization.NumberFormatInfo> 類別主題。

### <a name="integral-and-floating-point-numeric-types"></a>整數類資料類型和浮點數值類型

標準數值格式規範的某些描述會參考整數類資料類型或浮點數值類型。 整數數字類型為 <xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64> 和 <xref:System.Numerics.BigInteger>。 浮點數值類型有 <xref:System.Decimal>、<xref:System.Single> 和 <xref:System.Double>。

### <a name="floating-point-infinities-and-nan"></a>無限浮點數和 NaN

不論格式字串為何，如果 <xref:System.Single> 或 <xref:System.Double> 浮點類型的值為正無限大、負無限大或不是數字 (NaN)，則格式化後的字串會分別是 <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>、<xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A> 或 <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> 屬性的值 (這些屬性由目前適用的 <xref:System.Globalization.NumberFormatInfo> 物件所指定)。

## <a name="example"></a>範例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

下列範例會使用 en-US 文化特性和所有標準數值格式規範來格式化整數和浮點數值。 這個範例使用兩個特定的數字類型 (<xref:System.Double> 和 <xref:System.Int32>)，但用於其他任何數字基底類型 (<xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64>、<xref:System.Numerics.BigInteger>、<xref:System.Decimal> 和 <xref:System.Single>) 也會產生類似的結果。

[!code-csharp-interactive[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.NumberFormatInfo>
- [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [格式化類型](../../../docs/standard/base-types/formatting-types.md)
- [操作說明：以前置字元零來填補數字](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [範例：.NET Framework 4 格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
- [複合格式](../../../docs/standard/base-types/composite-formatting.md)
