---
title: 複合格式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parameter specifiers
- strings [.NET Framework], alignment
- format specifiers, composite formatting
- strings [.NET Framework], composite
- composite formatting
- objects [.NET Framework], formatting multiple objects
ms.assetid: 87b7d528-73f6-43c6-b71a-f23043039a49
caps.latest.revision: 36
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 473669b4aaa0782fec32fb0e2d89875c4ab7a838
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="composite-formatting"></a>複合格式
.NET 複合格式功能會採用物件清單和複合格式字串作為輸入。 複合格式字串是由混合索引替代符號 (Placeholder) 的固定文字所組成 (這些符號稱為對應至清單內物件的格式項目)。 格式作業產生的結果字串是由原始固定文字所組成，這些固定文字混合了清單中代表物件的字串。  
  
 下列方法支援複合格式功能：  
  
-   <xref:System.String.Format%2A?displayProperty=nameWithType>，傳回格式化的結果字串。  
  
-   <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>，將格式化的結果字串附加至 <xref:System.Text.StringBuilder> 物件。  
  
-   <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 方法的部分多載，對主控台顯示格式化的結果字串。  
  
-   <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> 方法的部分多載，將格式化的結果字串寫入至資料流或檔案。 衍生自 <xref:System.IO.TextWriter> 的類別，例如 <xref:System.IO.StreamWriter> 和 <xref:System.Web.UI.HtmlTextWriter>，也會共用這項功能。  
  
-   <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>，將格式化的訊息輸出至追蹤接聽項。  
  
-   <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法，將格式化的訊息輸出至追蹤接聽項。  
  
-   <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法，將告知性方法寫入至追蹤接聽項。  
  
## <a name="composite-format-string"></a>複合格式字串  
 複合格式字串和物件清單會當做支援複合格式功能之方法的引數來使用。 複合格式字串是由零個或更多段與一個或多個格式項目混合的固定文字所組成， 固定文字是您選擇的任何文字，而每個格式項目都會對應到清單內的一個物件或 boxed 結構。 複合格式功能將會傳回新的結果字串，其中每一個格式項目都會由清單內對應物件的字串表示來取代。  
  
 請考量下列 <xref:System.String.Format%2A> 程式碼片段。  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 固定文字是 "`Name =`" 和 "`, hours =`"。 格式項目為 "`{0}`" (其索引為 0，且對應至物件 `name`) 及 "`{1:hh}`" (其索引為 1，且對應至物件 `DateTime.Now`)。  
  
## <a name="format-item-syntax"></a>格式項目語法  
 每個格式項目都會使用下列格式，並由下列元件所組成：  
  
 `{` *index*[`,`*alignment*][`:`*formatString*]`}`  
  
 成對的大括號 ("{" 和 "}") 是必要的。  
  
### <a name="index-component"></a>索引元件  
 強制的 *index* 元件 (也稱為參數規範) 是用以識別物件清單中對應項目的數字 (從 0 開始)。 也就是說，參數規範為 0 的格式項目會格式化清單中的第一個物件，而參數規範為 1 的格式項目會格式化清單中的第二個物件，依此類推。 下列範例包含四個參數規範 (編號為 0 到 3)，以表示小於 10 的質數：  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 多個格式項目可以藉由指定相同參數規範來參考物件清單中的相同項目。 例如，您可以指定複合格式字串 (例如："0x{0:X} {0:E} {0:N}") 來將同一個數值設定成十六進位、科學記號和數字格式，如下列範例所示。  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 每個格式項目皆可參考清單內的任何物件。 例如，如果有三個物件，您可以指定複合格式字串 (如："{1} {0} {2}") 來格式化第二個、第一個和第三個物件。 不是格式項目所參考的物件會被忽略。 如果參數規範指定超出物件清單範圍的項目，則會在執行階段擲回 <xref:System.FormatException>。  
  
### <a name="alignment-component"></a>對齊元件  
 選擇性 *alignment* 元件為帶正負號的整數，表示慣用的格式化欄位寬度。 如果 *alignment* 的值小於格式化字串的長度，則會忽略 *alignment* 並使用格式化字串的長度當做欄位寬度。 如果 *alignment* 為正數，欄位中的格式化資料會靠右對齊；如果 *alignment* 為負數，則會靠左對齊。 如果填補有必要，則會使用泛空白字元 (White Space)。 如果指定了 *alignment*，則需要逗號。  
  
 下列範例會定義兩個陣列，一個包含員工的名稱，另一個包含他們在兩週內的工作時數。 複合格式字串會在 20 個字元的欄位中，將名稱靠左對齊，並且在 5 個字元的欄位中，將其工作時數靠右對齊。 請注意，"N1" 標準格式字串也會用來格式化具有一個小數位數的時數。  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>格式字串元件  
 選擇性 *formatString* 元件是一個格式字串，適用於將格式化的物件類型。 如果對應的物件為數值，指定標準或自訂的數值格式字串；如果對應的物件為 <xref:System.DateTime> 物件，指定標準或自訂的日期和時間格式字串；或者，如果對應的物件為列舉值，指定[列舉格式字串](../../../docs/standard/base-types/enumeration-format-strings.md)。 如果未指定 *formatString*，則會使用數值、日期和時間或列舉類型的一般 ("G") 格式規範。 如果指定 *formatString*，則需要冒號。  
  
 下表列出 .NET Framework 類別庫中支援預先定義之格式字串的類型或類型分類，並提供列出支援之格式字串的主題連結。 請注意，字串格式是一種可延伸機制，可讓為所有現有類型定義新的格式字串，以及定義一組應用程式定義類型所支援的格式字串。 如需詳細資訊，請參閱 <xref:System.IFormattable> 和 <xref:System.ICustomFormatter> 介面主題。  
  
|類型或類型分類|請參閱|  
|---------------------------|---------|  
|日期和時間類型 (<xref:System.DateTime>、<xref:System.DateTimeOffset>)|[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|列舉類型 (衍生自 <xref:System.Enum?displayProperty=nameWithType> 的所有類型)|[Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|數字類型 (<xref:System.Numerics.BigInteger>、<xref:System.Byte>、<xref:System.Decimal>、<xref:System.Double>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.SByte>、<xref:System.Single>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64>)|[Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[標準 TimeSpan 格式字串](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>逸出大括號  
 左右大括號會被解譯成格式項目的開頭與結尾。 因此，您必須使用逸出序列 (Escape Sequence)，才能顯示字面上的左右大括號。 請在固定文字中指定兩個左邊的大括號 ("{{")，以顯示一個左邊的大括號 ("{")，或者指定兩個右邊的大括號 ("}}") 來顯示一個右邊的大括號 ("}")。 格式項目中的括號會以它們出現的順序依序解譯， 但是不支援解譯巢狀大括號。  
  
 解譯逸出括號的方式，可能會造成無法預期的結果。 例如，格式項目 "{{{0:D}}}" 原本是要顯示一個左邊大括號、一個格式化為十進位的數值和一個右邊大括號。 然而，格式項目實際會以下列方式來解譯：  
  
1.  前面兩個左邊大括號 ("{{") 逸出，產生一個左邊大括號。  
  
2.  接下來的三個字元 ("{0:") 會解譯成格式項目的開頭。  
  
3.  再下一個字元 ("D") 可能解譯成十進位 (Decimal) 標準數值格式規範，但後面兩個逸出的右邊大括號 ("}}") 會產生一個大括號。 由於結果字串 ("D}") 並非標準的數值格式規範，因此，結果字串會被解譯成自訂格式字串，表示會顯示成常值字串 "D}"。  
  
4.  最後的大括號 ("}") 會被解譯成格式項目的結尾。  
  
5.  最後顯示的結果會是常值字串 "{D}"， 而要進行格式化的數值則不會顯示出來。  
  
 撰寫程式碼時，能夠避免錯誤解譯逸出大括號和格式項目的方法，就是個別地格式化大括號和格式項目。 也就是說，在第一個格式化作業中顯示常值的左邊大括號，在下一個作業中顯示格式項目的結果，接著在最終作業中顯示常值的右邊大括號。 下列範例將示範這個方法。  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>處理順序  
 如果對複合格式方法的呼叫包含的 <xref:System.IFormatProvider> 引數其值不是 `null`，則執行階段會呼叫其 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 方法要求 <xref:System.ICustomFormatter> 實作。 如果方法能夠傳回 <xref:System.ICustomFormatter> 實作，則會將它快取以供日後使用。  
  
 參數清單中每個對應至格式項目的值都會藉由執行下列步驟轉換為字串。 如果在前三個步驟中有任何條件成立，則會在該步驟傳回值的字串表示，而不會再執行後續步驟。  
  
1.  如果要格式化的值是 `null`，則會傳回空字串 ("")。  
  
2.  如果可以使用 <xref:System.ICustomFormatter> 實作，則執行階段會呼叫其 <xref:System.ICustomFormatter.Format%2A> 方法。 它會將格式項目的 *formatString<xref:System.IFormatProvider> 值 (如果有的話) 傳遞給方法；如果沒有，則會將*  連同 `null` 實作一起傳遞。  
  
3.  如果值實作 <xref:System.IFormattable> 介面，則會呼叫介面的 <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> 方法。 如果格式項目中有 *formatString* 值的話，就會將該值傳遞給方法；如果沒有的話，則會傳遞 `null`。 <xref:System.IFormatProvider> 引數的判斷如下：  
  
    -   對於數值，如果呼叫具有非 null <xref:System.IFormatProvider> 引數的複合格式方法，則執行階段會從其 <xref:System.Globalization.NumberFormatInfo> 方法要求 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 物件。 如果無法提供、如果引數的值為 `null`，或者如果複合格式方法沒有 <xref:System.IFormatProvider> 參數，則會使用目前執行緒文化特性的 <xref:System.Globalization.NumberFormatInfo> 物件。  
  
    -   對於日期和時間值，如果呼叫具有非 null <xref:System.IFormatProvider> 引數的複合格式方法，則執行階段會從其 <xref:System.Globalization.DateTimeFormatInfo> 方法要求 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 物件。 如果無法提供、如果引數的值為 `null`，或者如果複合格式方法沒有 <xref:System.IFormatProvider> 參數，則會使用目前執行緒文化特性的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
    -   對於其他類型的物件，如果呼叫複合格式時包含 <xref:System.IFormatProvider> 引數，它的值會直接傳遞至 <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> 實作。 否則會傳遞 `null` 至 <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> 實作。  
  
4.  呼叫類型的無參數 `ToString` 方法，該方法會覆寫 <xref:System.Object.ToString?displayProperty=nameWithType> 或繼承其基底類別的行為。 在這種情況下，會忽略 *formatString* 元件在格式項目中指定的格式字串 (如果有的話)。  
  
 對齊會在已經執行前面的步驟之後套用。  
  
## <a name="code-examples"></a>程式碼範例  
 下列範例顯示一個使用複合格式建立的字串，以及另一個使用物件的 `ToString` 方法建立的字串。 這兩個類型的格式化產生相等結果。  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 假設目前日期是五月的星期四，前面範例中兩個字串的值在美國英文文化特性中都是 `Thursday May`。  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 會公開與 <xref:System.String.Format%2A?displayProperty=nameWithType> 相同的功能。 這兩種方法唯一的差別在於，<xref:System.String.Format%2A?displayProperty=nameWithType> 會以字串形式傳回結果，而 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 則會將結果寫入至與 <xref:System.Console> 物件關聯的輸出資料流。 下列範例使用 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 方法，將 `MyInt` 的值格式化為貨幣值。  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 下列範例示範多個物件的格式化，其中包括使用兩種不同方式來格式化一個物件。  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 下列範例示範格式設定中的對齊用法。 格式化的引數會放在兩個垂直線 (&#124;) 字元之間以強調所產生的對齊。  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Console.WriteLine%2A>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [字串內插補點 (C#)](../../csharp/language-reference/tokens/interpolated.md)  
 [字串內插補點 (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [標準 TimeSpan 格式字串](../../../docs/standard/base-types/standard-timespan-format-strings.md)  
 [自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md)
