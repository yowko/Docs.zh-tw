---
title: 在 .NET 中將類型格式化
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3273b8babe44a48d6952620e4331cba4f22b6e9
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026038"
---
# <a name="formatting-types-in-net"></a>在 .NET 中將類型格式化

格式化是將類別、結構或列舉值的執行個體轉換成字串表示的過程，通常是為了將結果字串展示予使用者，或是為了將字串藉還原序列化方式還原成原始的資料類型。 這種轉換可能面臨幾項挑戰：

- 值的內部儲存方式不見得反映出使用者想要的檢視方式。 例如，電話號碼可能以 8009999999 的格式儲存，但這並不太符合使用者的閱讀習慣。 應該改以顯示成 800-999-9999。 如需以此方式格式化數字的範例，請參閱 [自訂格式字串](#customStrings) 一節。

- 物件轉換後的字串表示有時候並不符合直覺。 例如，Temperature 物件或 Person 物件的字串表示應該為何種格式，就不是那麼清楚。 如需以各種方式將 Temperature 物件格式化的範例，請參閱 [標準格式字串](#standardStrings) 一節。

- 值的格式通常需要符合文化特性。 例如，如果應用程式需要使用數字來表達貨幣值，則數值字串應該包含目前文化特性的貨幣符號、群組分隔符號 (即大部分文化特性中的千位分隔符號) 和小數點符號。 如需範例，請參閱 [以格式提供者和 IFormatProvider 介面進行符合文化特性的格式化](#FormatProviders) 一節。

- 應用程式可能需要以不同的方式來顯示相同的值。 例如，應用程式在表示列舉成員時，在做法上可能是顯示其名稱的字串表示，或顯示其基礎值。 如需以不同方式格式化 <xref:System.DayOfWeek> 列舉成員的範例，請參閱 [標準格式字串](#standardStrings) 一節。

> [!NOTE]
> 格式化會將某種類型的值轉換為字串表示。 剖析是格式化的反向操作。 剖析作業會從資料類型的字串表示來建立資料類型的執行個體。 如需將字串轉換為其他資料類型的相關資訊，請參閱 [Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)。

.NET 提供豐富的格式化支援，可滿足開發人員的這些需求。

本概觀包含下列各節：

- [.NET 中的格式化​​](#NetFormatting)

- [使用 ToString 方法的預設格式](#DefaultToString)

- [覆寫 ToString 方法](#OverrideToString)

- [ToString 方法和格式字串](#FormatStrings)

  - [標準格式字串](#standardStrings)

  - [自訂格式字串](#customStrings)

  - [格式字串和 .NET 類別庫類型](#stringRef)

- [以格式提供者和 IFormatProvider 介面進行符合文化特性的格式化](#FormatProviders)

  - [符合文化特性的數值格式](#numericCulture)

  - [符合文化特性的日期和時間值格式](#dateCulture)

- [IFormattable 介面](#IFormattable)

- [複合格式](#CompositeFormatting)

- [使用 ICustomFormatter 的自訂格式](#Custom)

- [相關主題](#RelatedTopics)

- [參考資料](#Reference)

<a name="NetFormatting"></a>

## <a name="formatting-in-net"></a>.NET 中的格式化​​

格式化機制的基礎在於 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 方法的預設實作，這將於本主題稍後的[使用 ToString 方法的預設格式](#DefaultToString)一節中討論。 不過，.NET 提供幾種方式來修改和擴充其預設格式化支援。 這些需求包括下列各項：

- 覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 方法來自訂物件值的字串表示。 如需詳細資訊，請參閱本主題稍後的 [覆寫 ToString 方法](#OverrideToString) 一節。

- 定義格式規範，格式規範讓物件值的字串表示可以採用多種形式。 例如，下列陳述式中的 "X" 格式規範會將整數轉換為十六進位值的字串表示。

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     如需格式規範的詳細資訊，請參閱 [ToString 方法和格式字串](#FormatStrings) 一節。

- 透過格式提供者來採用特定文化特性的格式化慣例。 例如，下列陳述式會使用 en-US 文化特性的格式化慣例來顯示貨幣值。

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     如需以格式提供者進行格式化的詳細資訊，請參閱 [格式提供者和 IFormatProvider 介面](#FormatProviders) 一節。

- 實作 <xref:System.IFormattable> 介面，以同時支援使用 <xref:System.Convert> 類別和複合格式來轉換字串。 如需詳細資訊，請參閱 [IFormattable 介面](#IFormattable) 一節。

- 使用複合格式將值的字串表示嵌入更大的字串中。 如需詳細資訊，請參閱 [複合格式](#CompositeFormatting) 一節。

- 實作 <xref:System.ICustomFormatter> 和 <xref:System.IFormatProvider> 來提供完整的自訂格式解決方案。 如需詳細資訊，請參閱 [使用 ICustomFormatter 的自訂格式](#Custom) 一節。

下列各節會討論這些將物件轉換為其字串表示的方法。

<a name="DefaultToString"></a>

## <a name="default-formatting-using-the-tostring-method"></a>使用 ToString 方法的預設格式

每個衍生自 <xref:System.Object?displayProperty=nameWithType> 的類型都會自動繼承無參數的 `ToString` 方法，這個方法預設會傳回類型的名稱。 下列範例示範預設的 `ToString` 方法。 範例中會定義一個不具任何實作的 `Automobile` 類別。 當具現化這個類別並呼叫其 `ToString` 方法時，會顯示這個類別的類型名稱。 請注意，在範例中不會明確呼叫 `ToString` 方法。 <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> 方法會隱含呼叫本身所收到做為引數傳遞之物件的 `ToString` 方法。

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> 自 [!INCLUDE[win81](../../../includes/win81-md.md)] 起，Windows 執行階段即包含了 <xref:Windows.Foundation.IStringable> 介面。此介面只有一個方法 [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A)，可提供預設的格式化支援。 不過，不建議 Managed 類型實作 `IStringable` 介面。 如需詳細資訊，請參閱 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 參考頁面中的＜Windows 執行階段與 `IStringable` 介面>＞一節。

因為除介面以外的所有其他類型都會衍生自 <xref:System.Object>，所以您的自訂類別或結構會自動被賦予此功能。 不過，預設 `ToString` 方法所提供的功能會受到限制：雖然其可以識別類型，但無法提供類型之執行個體的任何資訊。 若要提供物件的字串表示來表達該物件的相關資訊，您必須覆寫 `ToString` 方法。

> [!NOTE]
> 結構會繼承自 <xref:System.ValueType>，而後者又會衍生自 <xref:System.Object>。 雖然 <xref:System.ValueType> 會覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType>，但實作方法是相同的。

<a name="OverrideToString"></a>

## <a name="overriding-the-tostring-method"></a>覆寫 ToString 方法

顯示類型的名稱通常用途不大，亦無法讓您類型的使用者藉以區分不同的執行個體。 不過，您可以覆寫 `ToString` 方法，以更實用的方式表示物件的值。 下列範例定義 `Temperature` 物件，並覆寫其 `ToString` 方法來顯示攝氏溫度。

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

在 .NET 中，已覆寫每個基本實值類型的 `ToString` 方法來顯示物件的值，而非物件的名稱。 下表顯示各基本類型如何覆寫 ToString 方法。 請注意，大部分經過覆寫的方法都會呼叫 `ToString` 方法的另一個多載，並且將 "G" 格式規範 (此規範定義此類型的一般格式) 和 <xref:System.IFormatProvider> 物件 (此物件表示目前文化特性) 傳遞至這個多載。

|類型|ToString 覆寫|
|----------|-----------------------|
|<xref:System.Boolean>|傳回 <xref:System.Boolean.TrueString?displayProperty=nameWithType> 或 <xref:System.Boolean.FalseString?displayProperty=nameWithType>。|
|<xref:System.Byte>|呼叫 `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Byte> 值。|
|<xref:System.Char>|以字串形式傳回字元。|
|<xref:System.DateTime>|呼叫 `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` ，以根據對目前的文化特性來格式化日期和時間值。|
|<xref:System.Decimal>|呼叫 `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Decimal> 值。|
|<xref:System.Double>|呼叫 `Double.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Double> 值。|
|<xref:System.Int16>|呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Int16> 值。|
|<xref:System.Int32>|呼叫 `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Int32> 值。|
|<xref:System.Int64>|呼叫 `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Int64> 值。|
|<xref:System.SByte>|呼叫 `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.SByte> 值。|
|<xref:System.Single>|呼叫 `Single.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.Single> 值。|
|<xref:System.UInt16>|呼叫 `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.UInt16> 值。|
|<xref:System.UInt32>|呼叫 `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.UInt32> 值。|
|<xref:System.UInt64>|呼叫 `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` ，以根據目前的文化特性來格式化 <xref:System.UInt64> 值。|

<a name="FormatStrings"></a>

## <a name="the-tostring-method-and-format-strings"></a>ToString 方法和格式字串

當物件只有單一字串表示時，使用預設 `ToString` 方法或覆寫 `ToString` 都沒有問題。 不過，物件的值通常有多種表示。 例如，溫度可以用華氏、攝氏或開氏溫度表示。 同樣地，整數值 10 可以用許多方式表示，包括 10、10.0、1.0e01 或 $10.00。

為了讓單一值可以具有多種字串表示，.NET 使用格式字串。 格式字串是包含一個或多個預先定義之格式規範的字串，這個字串是單一字元或一組字元，用於定義 `ToString` 方法應採用的輸出格式。 然後，格式字串會當做參數傳遞至物件的 `ToString` 方法，以決定如何呈現該物件的值的字串表示。

.NET 中所有的數值類型、日期和時間類型，以及列舉類型，都支援一組預先定義的格式規範。 您也可以利用格式字串定義多種字串表示給您應用程式中定義的資料類型。

<a name="standardStrings"></a>

### <a name="standard-format-strings"></a>標準格式字串

標準格式字串包含單一格式規範 (一個字母字元，定義套用此規範之物件的字串表示) 和選擇性的精確度規範 (這個規範影響結果字串中顯示的位數)。 如果省略或不支援精確度規範，則標準格式規範與標準格式字串無異。

.NET 定義一組適用於所有數值類型、所有日期和時間類型，以及所有列舉類型的標準格式規範。 例如，這些分類每個都支援 "G" 標準格式規範 (這個規範定義該類型之值的一般字串表示)。

列舉類型的標準格式字串直接控制了值的字串表示。 傳遞給列舉值的 `ToString` 方法的格式字串決定了該值是以其字串名稱 ("G" 和 "F" 格式規範)、基礎整數值 ("D" 格式規範)，還是十六進位值 ("X" 格式規範) 來顯示。 下列範例示範如何使用標準格式字串來格式化 <xref:System.DayOfWeek> 列舉值。

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

如需列舉格式字串的相關資訊，請參閱 [Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md)。

數值類型的標準格式字串定義出的結果字串之確切外觀通常是由一個或多個屬性值所控制。 例如，"C" 格式規範會將數字格式化為貨幣值。 當您將 "C" 格式規範做為唯一參數來呼叫 `ToString` 方法時，會使用目前文化特性之 <xref:System.Globalization.NumberFormatInfo> 物件中的下列屬性值來定義數值的字串表示：

- <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> 屬性，指定目前文化特性的貨幣符號。

- <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> 或 <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> 屬性，這個屬性傳回的整數會決定：

  - 貨幣符號的位置。

  - 負值是以開頭負號、結尾負號還是括號來表示。

  - 數值和貨幣符號之間是否顯示一個空格。

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> 屬性，定義結果字串中的小數位數。

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> 屬性，定義結果字串中的十進位分隔符號。

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> 屬性，定義群組分隔符號。

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> 屬性，定義小數點左邊每個群組的位數。

- <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> 屬性，決定當不使用括號來表示負數時，要在結果字串中使用的負數值表示符號。

此外，數值格式字串也可以包含精確度規範。 這個規範的意義視搭配使用的格式字串而定，但通常是表示結果字串中應該顯示的總位數或小數位數。 例如，下列範例會使用 "X4" 標準數值字串和精確度規範，建立具有四個十六進位數字的字串值。

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

如需標準數值格式字串的詳細資訊，請參閱 [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)。

日期和時間值的標準格式字串是特定 <xref:System.Globalization.DateTimeFormatInfo> 屬性所儲存之自訂格式字串的別名。 例如，以 "D" 格式規範來呼叫日期和時間值的 `ToString` 方法，將會使用目前文化特性之 <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> 屬性中所儲存的自訂格式字串來顯示日期和時間 (如需自訂格式字串的詳細資訊，請參閱[下一節](#customStrings))。下列範例示範這種關聯性。

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

如需標準日期和時間格式字串的詳細資訊，請參閱 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)。

對於應用程式定義的物件，您也可以使用標準格式字串來定義由該物件的 `ToString(String)` 方法所產生的字串表示。 您可以定義您的物件所支援的特定標準格式規範，並且決定這項規範是否區分大小寫。 您對 `ToString(String)` 方法的實作應該要能支援：

- "G" 格式規範，表示物件的慣用或通用格式。 您物件的 `ToString` 方法的無參數多載應該要呼叫這個方法的 `ToString(String)` 多載，並且將 "G" 標準格式字串傳遞給這個方法。

- 支援等於 null 參考 (在 Visual Basic 中為`Nothing` ) 的格式規範。 等於 null 參考的格式規範應該要視為相當於 "G" 格式規範。

例如， `Temperature` 類別可以在內部以攝氏儲存溫度，並透過格式規範以攝氏、華氏和開氏溫度來表示 `Temperature` 物件的值。 下列範例提供一個實例。

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

<a name="customStrings"></a>

### <a name="custom-format-strings"></a>自訂格式字串

除了標準格式字串，.NET 也為數值以及日期和時間值定義了自訂格式字串。 自訂格式字串由一個或多個自訂格式規範組成，這些規範定義了值的字串表示。 例如，自訂日期和時間格式字串 "yyyy/mm/dd hh:mm:ss.ffff t zzz" 會將日期轉換為其字串表示，以 en-US 文化特性而言為 "2008/11/15 07:45:00.0000 P -08:00" 形式。 同樣地，自訂格式字串 "0000" 會將整數值 12 轉換為 "0012"。 如需完整的自訂格式字串清單，請參閱 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) 和 [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)。

如果格式字串由單一自訂格式規範組成，則應該在格式規範前面加上百分比 (%) 符號，以避免與標準格式規範產生混淆。 下列範例會使用 "M" 自訂格式規範來顯示特定日期的一位數或兩位數月份。

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

日期和時間值的許多標準格式字串都是自訂格式字串 (這些自訂格式字串由 <xref:System.Globalization.DateTimeFormatInfo> 物件的屬性所定義) 的別名。 自訂格式字串也提供極大的彈性，來提供應用程式定義的數值或日期和時間值格式。 您可以將多個自訂格式規範結合成單一自訂格式字串，以自訂您的數值及日期和時間值結果字串。 下列範例定義的自訂格式字串，會在月份名稱、日期和年後面顯示加上括號的星期。

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

下列範例會定義自訂格式字串，該字串會將 <xref:System.Int64> 值顯示為標準的七位數美國電話號碼且包含其區碼。

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

雖然標準格式字串通常能夠為應用程式定義的類型解決大部分的格式需求，但您也可以定義自訂格式規範來格式化您的類型。

<a name="stringRef"></a>

### <a name="format-strings-and-net-types"></a>格式字串和 .NET 類型

所有數字類型 (也就是 <xref:System.Byte>、<xref:System.Decimal>、<xref:System.Double>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.SByte>、<xref:System.Single>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64> 和 <xref:System.Numerics.BigInteger> 類型)，以及 <xref:System.DateTime>、<xref:System.DateTimeOffset>、<xref:System.TimeSpan>、<xref:System.Guid> 和所有列舉類型，都支援以格式字串進行格式化。 如需每個類型所支援特定格式字串的資訊，請參閱下列主題：

|標題|定義|
|-----------|----------------|
|[Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)|說明建立數值常用之字串表示的標準格式字串。|
|[Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)|說明建立應用程式專屬數值格式的自訂格式字串。|
|[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|說明建立 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值之常用字串表示的標準格式字串。|
|[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|說明建立應用程式專屬 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值格式的自訂格式字串。|
|[標準 TimeSpan 格式字串](../../../docs/standard/base-types/standard-timespan-format-strings.md)|說明建立時間間隔之常用字串表示的標準格式字串。|
|[自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)|說明建立應用程式專屬數值格式的自訂格式字串。|
|[Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md)|說明用來建立列舉值之字串表示的標準格式字串。|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|描述 <xref:System.Guid> 值的標準格式字串。|

<a name="FormatProviders"></a>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>以格式提供者和 IFormatProvider 介面進行符合文化特性的格式化

雖然格式規範可讓您自訂物件的格式，但如果要為物件產生有意義的字串表示，您通常還需要其他格式設定資訊。 例如，如果要使用 "C" 標準格式字串或自訂格式字串 (例如 "$ #,#.00") 將數字格式化為貨幣值，您至少還需要有正確的貨幣符號、群組分隔符號和小數分隔符號的相關資訊。 在 .NET 中，這項額外的格式資訊是透過 <xref:System.IFormatProvider> 介面取得，而這個介面會當做傳遞至數字類型以及日期和時間類型的 `ToString` 方法之一個或多個多載的參數來提供。 <xref:System.IFormatProvider> 實作會在 .NET 中用來支援文化特性特定的格式。 下列範例將示範以代表不同文化特性的三個 <xref:System.IFormatProvider> 物件進行格式化時，物件的字串表示會有什麼樣的變化。

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

<xref:System.IFormatProvider> 介面包含一個 <xref:System.IFormatProvider.GetFormat%28System.Type%29>方法，這個方法具有單一參數來指定可提供格式設定資訊之物件的類型。 如果這個方法可以提供該類型的物件，則會傳回該物件。 否則會傳回 null 參考 (在 Visual Basic 中為`Nothing` )。

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 是一種回呼方法。 當您呼叫包含 `ToString` 參數的 <xref:System.IFormatProvider> 方法多載時，這個多載會呼叫該 <xref:System.IFormatProvider.GetFormat%2A> 物件的 <xref:System.IFormatProvider> 方法。 <xref:System.IFormatProvider.GetFormat%2A> 方法負責將提供必要格式設定資訊的物件 (由其 `formatType` 參數指定)，傳回給 `ToString` 方法。

有幾個格式化或字串轉換方法都包含 <xref:System.IFormatProvider>類型的參數，但通常呼叫方法時，會忽略這個參數的值。 下表列出一些使用這個參數的格式化方法，以及這些方法傳遞至 <xref:System.Type> 方法的 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 物件的類型。

|方法|`formatType` 參數的類型|
|------------|------------------------------------|
|數字類型的`ToString` 方法|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|日期和時間類型的`ToString` 方法|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> 數字類型及日期和時間類型的 `ToString` 方法都含有多載，而其中只有某些多載會包含 <xref:System.IFormatProvider> 參數。 如果方法沒有 <xref:System.IFormatProvider>類型的參數，則會改以傳遞 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性所傳回的物件。 例如，呼叫預設的 <xref:System.Int32.ToString?displayProperty=nameWithType> 方法最終會產生如下的方法呼叫： `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`。

.NET 提供三個實作 <xref:System.IFormatProvider> 的類別：

- <xref:System.Globalization.DateTimeFormatInfo>，這個類別提供特定文化特性之日期和時間值的格式設定資訊。 它的 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 實作會傳回它自己的執行個體。

- <xref:System.Globalization.NumberFormatInfo>，這個類別提供特定文化特性的數值格式設定資訊。 它的 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 實作會傳回它自己的執行個體。

- <xref:System.Globalization.CultureInfo> 它的 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 實作可以傳回 <xref:System.Globalization.NumberFormatInfo> 物件來提供數值格式設定資訊，或傳回 <xref:System.Globalization.DateTimeFormatInfo> 物件來提供日期和時間值的格式設定資訊。

您也可以實作自己的格式提供者來取代上述任何一個類別。 不過，您實作的 <xref:System.IFormatProvider.GetFormat%2A> 方法如果必須提供格式設定資訊給 `ToString` 方法，則必須傳回上表所列之類型的物件。

<a name="numericCulture"></a>

### <a name="culture-sensitive-formatting-of-numeric-values"></a>符合文化特性的數值格式

根據預設，數值格式會區分文化特性。 如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。 下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> 方法。 在各案例中，結果字串都會反映目前文化特性的格式設定慣例。 這是因為 `ToString` 和 `ToString(String)` 方法會包裝對每個數值類型之 `ToString(String, IFormatProvider)` 方法的呼叫。

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

您也可以呼叫具有 `ToString` 參數的 `provider` 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的數值：

- <xref:System.Globalization.CultureInfo> 物件，表示要使用其格式設定慣例的文化特性。 它的 <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> 方法會傳回 <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> 屬性的值，也就是為數值提供文化特性特有格式資訊的 <xref:System.Globalization.NumberFormatInfo> 物件。

- <xref:System.Globalization.NumberFormatInfo> 物件，該物件會定義要使用的文化特性特有格式設定慣例。 它的 <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> 方法會傳回本身的執行個體。

下列範例將使用 <xref:System.Globalization.NumberFormatInfo> 物件，該物件表示用於格式化浮點數的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

<a name="dateCulture"></a>

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>符合文化特性的日期和時間值格式

根據預設，日期和時間值的格式區分文化特性。 如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。 下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 方法。 在各案例中，結果字串都會反映目前文化特性的格式設定慣例。 這是因為 <xref:System.DateTime.ToString?displayProperty=nameWithType>、 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>、 <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>和 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> 方法會包裝 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法的呼叫。

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

您也可以呼叫具有 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 參數的 <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> 或 `provider` 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的日期和時間值：

- <xref:System.Globalization.CultureInfo> 物件，表示要使用其格式設定慣例的文化特性。 它的 <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> 方法會傳回 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性的值，也就是為日期和時間值提供文化特性特有格式資訊的 <xref:System.Globalization.DateTimeFormatInfo> 物件。

- <xref:System.Globalization.DateTimeFormatInfo> 物件，該物件會定義要使用的文化特性特有格式設定慣例。 它的 <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> 方法會傳回本身的執行個體。

下列範例將使用 <xref:System.Globalization.DateTimeFormatInfo> 物件，該物件表示用於格式化日期的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

<a name="IFormattable"></a>

## <a name="the-iformattable-interface"></a>IFormattable 介面

以格式字串和 `ToString` 參數來多載 <xref:System.IFormatProvider> 方法的類型，通常也會實作 <xref:System.IFormattable> 介面。 這個介面具有單一成員 <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>，這個成員同時包含格式字串和格式提供者做為參數。

針對您的應用程式定義的類別來實作 <xref:System.IFormattable> 介面有兩項好處：

- 支援透過 <xref:System.Convert> 類別來轉換字串。 呼叫 <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> 和 <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法時，會自動呼叫您的 <xref:System.IFormattable> 實作。

- 支援複合格式。 如果使用包含格式字串的格式項目來格式化您的自訂類型，則 Common Language Runtime 會自動呼叫您的 <xref:System.IFormattable> 實作並將格式字串傳遞給這個實作。 如需透過 <xref:System.String.Format%2A?displayProperty=nameWithType> 或 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>等方法執行複合格式的詳細資訊，請參閱 [複合格式](#CompositeFormatting) 一節。

下列範例定義一個實作 `Temperature` 介面的 <xref:System.IFormattable> 類別。 這個類別支援 "C" 或 "G" 格式規範來顯示攝氏溫度、支援 "F" 格式規範來顯示華氏溫度，也支援 "K" 格式規範來顯示絕對溫度。

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

下列範例會執行個體化 `Temperature` 物件。 然後呼叫 <xref:System.Convert.ToString%2A> 方法，並使用數個複合格式字串來取得 `Temperature` 物件的不同字串表示。 其中每個方法又呼叫 <xref:System.IFormattable> 類別的 `Temperature` 實作。

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

<a name="CompositeFormatting"></a>

## <a name="composite-formatting"></a>複合格式

某些方法 (例如 <xref:System.String.Format%2A?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>) 支援複合格式。 複合格式字串是一種範本，可傳回由零個、一個或更多物件的字串表示所組成的單一字串。 複合格式字串中的每個物件都以有索引的格式項目來表示。 格式項目的索引對應至其所表示的物件在方法的參數清單中的位置。 索引以零為起始。 例如，在下列對 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法的呼叫中，第一個格式項目 `{0:D}` 由 `thatDate` 的字串表示所取代、第二個格式項目 `{1}` 由 `item1` 的字串表示所取代，而第三個格式項目 `{2:C2}` 由 `item1.Value` 的字串表示所取代。

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

除了取代具有對應物件字串表示格式的項目，格式項目也可讓您控制下列幾項：

- 當物件實作 <xref:System.IFormattable> 介面，並支援格式字串時，物件表示為字串的特定方式。 您可將格式項目索引後面接上 `:` (冒號) ，後面再接有效的格式字串，以執行此作業。 前一個範例採用的方法是用 "d" (簡短日期模式) 格式字串來格式化日期值 (例如 `{0:d}`) 以及用 "C2" 格式字串 (例如 `{2:C2}` ) 來格式化數值，以表示具有兩個小數位數的十進位數字之貨幣值。

- 包含物件字串表示法及在該欄位中對齊方式的字串表示法之欄位寬度。 您可將格式項目索引後面接上 `,` (逗號) ，後面再接欄位寬度，以執行此作業。 如果欄位寬度是正值，則此欄位中的字串為靠右對齊；如果欄位寬度是負值，則為靠左對齊。 下列範例在長 20 個字元的欄位中將日期值靠左對齊，並在長 11 個字元的欄位中將具有一位小數位數的十進位值靠右對齊。

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     請注意如果對齊字串元件和格式字串元件都存在，則前者優先於後者 (例如， `{0,-20:g}`)。

如需複合格式的詳細資訊，請參閱 [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md)。

<a name="Custom"></a>

## <a name="custom-formatting-with-icustomformatter"></a>使用 ICustomFormatter 的自訂格式

<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>這兩個複合格式方法包含支援自訂格式的格式提供者參數。 呼叫這兩種格式化方法的任一種時，會將表示 <xref:System.Type> 介面的 <xref:System.ICustomFormatter> 物件傳遞至格式提供者的 <xref:System.IFormatProvider.GetFormat%2A> 方法。 然後， <xref:System.IFormatProvider.GetFormat%2A> 方法負責傳回 <xref:System.ICustomFormatter> 實作，這個實作提供自訂格式。

<xref:System.ICustomFormatter> 介面具有單一方法 <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>，複合格式化方法會自動針對複合格式字串中的每個格式項目，各呼叫一次這個方法。 <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> 方法具有三個參數：格式字串 (表示格式項目中的 `formatString` 引數)、要格式化的物件，以及提供格式化服務的 <xref:System.IFormatProvider> 物件。 實作 <xref:System.ICustomFormatter> 的物件通常也會實作 <xref:System.IFormatProvider>，所以這最後一個參數是對自訂格式化類別的參考。 方法會傳回要格式化之物件的自訂格式化字串表示。 如果方法無法格式化物件，則應該傳回 null 參考 (在 Visual Basic 中為`Nothing` )。

下列範例提供一個名為 <xref:System.ICustomFormatter> 的 `ByteByByteFormatter` 實作，這個實作會將整數值顯示為一連串由兩位數十六進位值再加上一個空格所組成的數列。

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

下列範例會使用 `ByteByByteFormatter` 類別來格式化整數值。 請注意，在範例中不會明確呼叫 <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> 方法在第二個 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法呼叫中被呼叫不只一次，且第三個方法呼叫中使用預設 <xref:System.Globalization.NumberFormatInfo> 提供者，因為`ByteByByteFormatter.Format` 方法無法辨認 "N0" 格式字串而傳回 null 參考 (在 Visual Basic 中為`Nothing` ) 的格式規範。

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

<a name="RelatedTopics"></a>

## <a name="related-topics"></a>相關主題

|標題|定義|
|-----------|----------------|
|[Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)|說明建立數值常用之字串表示的標準格式字串。|
|[Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)|說明建立應用程式專屬數值格式的自訂格式字串。|
|[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|說明建立 <xref:System.DateTime> 值之常用字串表示的標準格式字串。|
|[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|說明建立應用程式專屬 <xref:System.DateTime> 值格式的自訂格式字串。|
|[標準 TimeSpan 格式字串](../../../docs/standard/base-types/standard-timespan-format-strings.md)|說明建立時間間隔之常用字串表示的標準格式字串。|
|[自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)|說明建立應用程式專屬數值格式的自訂格式字串。|
|[Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md)|說明用來建立列舉值之字串表示的標準格式字串。|
|[複合格式](../../../docs/standard/base-types/composite-formatting.md)|描述如何將一個或更多的格式化值嵌入字串。 字串可以隨後顯示在主控台 (Console) 或寫入資料流。|
|[執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)|列出各主題，提供執行特定格式設定作業的逐步指示。|
|[Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)|說明如何將物件初始化為這些物件的字串表示所描述的值。 剖析是格式化的反向作業。|

<a name="Reference"></a>

## <a name="reference"></a>參考資料

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
