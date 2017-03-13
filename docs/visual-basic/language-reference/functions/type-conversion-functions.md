---
title: "Type Conversion Functions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.CUShort"
  - "vb.csng"
  - "vb.CDate"
  - "CByte"
  - "CSng"
  - "vb.CDec"
  - "CBool"
  - "CStr"
  - "vb.CULng"
  - "CDec"
  - "CVErr"
  - "CDbl"
  - "CShort"
  - "vb.CObj"
  - "vb.CVErr"
  - "CULng"
  - "vb.cdbl"
  - "vb.cbool"
  - "CObj"
  - "CDate"
  - "CLng"
  - "vb.cstr"
  - "vb.cbyte"
  - "vb.clng"
  - "vb.CChar"
  - "CUShort"
  - "vb.CUInt"
  - "vb.cint"
  - "vb.CShort"
  - "CInt"
  - "CUInt"
  - "CChar"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDate function"
  - "CByte function"
  - "Integer data type, converting"
  - "string conversion, conversion functions"
  - "fractions"
  - "data types [Visual Basic], converting"
  - "text, converting"
  - "CDec function"
  - "Char data type, converting"
  - "type conversion, functions for"
  - "Single data type, converting"
  - "numbers, rounding"
  - "rounding numbers, type conversion"
  - "CUShort function"
  - "Long data type, converting"
  - "return values, data types"
  - "single-precision numbers, converting"
  - "data type conversion, functions for"
  - "CStr function"
  - "times, converting"
  - "CSng function"
  - "conversions, type conversion functions"
  - "CBool function"
  - "CDbl function"
  - "CUInt function"
  - "Currency data type, conversion functions"
  - "numbers, converting"
  - "Double data type, converting"
  - "CLng function"
  - "CSByte function"
  - "double-precision numbers"
  - "Decimal data type, converting"
  - "Boolean data type, converting"
  - "integers, type conversion functions"
  - "dates, converting"
  - "CULng function"
  - "CInt function"
  - "Date data type, converting"
  - "Byte data type, converting"
  - "String data type, converting"
  - "CChar function"
  - "banker's rounding"
  - "Short data type, converting"
  - "rounding numbers, banker's rounding"
  - "type conversion, Visual Basic vs. .NET Framework"
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Type Conversion Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

這些函式是以內嵌方式編譯的，也就是說，轉換程式碼為運算式的部分程式碼。  有時並不需要呼叫程序就能完成轉換，因此能改善效能。  每個函式都可以強制讓運算式成為特定的資料型別。  
  
## 語法  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## 組件  
 `expression`  
 必要項。  來源資料型別的運算式。  
  
## 傳回數值資料型別  
 函數名稱可決定其傳回值的資料型別，如下表所示。  
  
|函式名稱|傳回資料型別|`expression` 引數的範圍|  
|----------|------------|------------------------|  
|`CBool`|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何有效的 `Char` 或 `String` 或數值運算式。|  
|`CByte`|[Byte Data Type](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 至 255 \(不帶正負號\)；小數部分會四捨五入。<sup>1</sup>|  
|`CChar`|[Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)|任何有效的 `Char` 或 `String` 運算式，只會轉換 `String` 的第一個字元，值可從 0 到 65535 \(不帶正負號\)。|  
|`CDate`|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|日期和時間的任何有效表示|  
|`CDbl`|[Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)|負值為 \-1.79769313486231570E\+308 至  \-4.94065645841246544E\-324，正值為 4.94065645841246544E\-324 至 1.79769313486231570E\+308。|  
|`CDec`|[Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|零個小數的數字為 \+\/\-79,228,162,514,264,337,593,543,950,335，也就是沒有小數位數的數字。  具有 28 個小數位數的數字範圍為 \+\/\-7.9228162514264337593543950335。  最小的可能非零值為 0.0000000000000000000000000001 \(\+\/\-1E\-28\)。|  
|`CInt`|[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)|\-2,147,483,648 至 2,147,483,647；小數部分會捨入。<sup>1</sup>|  
|`CLng`|[Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)|\-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807；小數部分會捨入。<sup>1</sup>|  
|`CObj`|[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)|任何有效的運算式。|  
|`CSByte`|[SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|\-128 至 127；小數部分會捨入。<sup>1</sup>|  
|`CShort`|[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)|\-32,768 至 32,767；小數部分會捨入。<sup>1</sup>|  
|`CSng`|[Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)|負值為 \-3.402823E\+38 至 \-1.401298E\-45；正值為 1.401298E\-45 至 3.402823E\+38。|  
|`CStr`|[String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)|`CStr` 的傳回值取決於 `expression` 引數。  請參閱 [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。|  
|`CUInt`|[UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 至 4,294,967,295 \(不帶正負號\)；小數部分會四捨五入。<sup>1</sup>|  
|`CULng`|[ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 至 18,446,744,073,709,551,615 \(不帶正負號\)；小數部分會四捨五入。<sup>1</sup>|  
|`CUShort`|[UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 至 65,535 \(不帶正負號\)；小數部分會四捨五入。<sup>1</sup>|  
  
 <sup>1</sup> 可以用特殊的捨去類型來處理小數部分，稱為「*四捨六入五成雙*」\(Banker's Rounding\)。  如需詳細資訊，請參閱備註。  
  
## 備註  
 因此，您應該在 <xref:System.Convert> 類別或個別的型別結構或類別上，利用慣用的 .NET Framework 方法 \(例如 `ToString()`\) 來使用 Visual Basic 型別轉換函式。  Visual Basic 函式的設計目的是為了與 Visual Basic 程式碼進行最佳的互動，也能讓您的原始程式碼更精簡且更容易閱讀。  此外，.NET Framework 轉換方法不一定會與 Visual Basic 函式產生相同的結果，例如將 `Boolean` 轉換成 `Integer` 時。  如需詳細資訊，請參閱[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## 行為  
  
-   **強制型轉** \(Coercion\)：一般來說，您可使用資料型別轉換函式來將某運算結果強制轉換為特定資料型別，而不是轉換為預設的資料型別。  例如，您可以在一般會發生單精度、雙精度或整數運算情況時，使用 `CDec` 來強制執行十進位運算。  
  
-   **轉換失敗** ：如果傳遞給函式的 `expression` 在其轉換的資料型別範圍之外，就會發生 <xref:System.OverflowException>。  
  
-   **小數部分** ：當您將非整數值轉換成整數型別時，整數轉換函式 \(`CByte`、`CInt`、`CLng`、`CSByte`、`CShort`、`CUInt`、`CULng` 和 `CUShort`\) 會移除小數部分並將值捨入成最接近的整數。  
  
     當小數部分正好為 0.5 時，整數轉換函式會將該數字捨入至最接近的偶數整數。  例如，0.5 會捨入至 0，1.5 和 2.5 皆會捨入至 2。  這個動作有時稱為「*四捨六入五成雙*」\(Banker's Rounding\)，其目的是補償當您一起加總此類數字時會累積的偏差。  
  
     `CInt` 和 `CLng` 與 <xref:Microsoft.VisualBasic.Conversion.Int%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Fix%2A> 函式不同，它會截斷 \(而非捨入\) 數字的小數部分。  同樣地，`Fix` 和 `Int` 也總是會將傳入的相同資料型別數值傳回。  
  
-   **日期\/時間轉換** 使用 <xref:Microsoft.VisualBasic.Information.IsDate%2A> 函式來判斷值是否可以轉換成日期和時間。  `CDate` 會辨識日期常值和時間常值，但不會辨識數值。  若要將 Visual Basic 6.0 的 `Date` 值轉換成 Visual Basic 2005 \(含\) 以後版本的 `Date` 值，可使用 <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> 方法。  
  
-   **中性日期\/時間值** ：[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) 永遠同時包含日期和時間資訊。  為了方便進行型別轉換，Visual Basic 將 1\/1\/0001 \(1 年 1 月 1 日\) 視為日期的「*中性值*」\(Neutral Value\)，將 00:00:00 \(午夜\) 視為時間的中性值。  如果您將 `Date` 值轉換為字串，`CStr` 不會在產生的字串中包含中性值。  例如，如果您將 `#January 1, 0001 9:30:00#` 轉換為字串，結果會是 "9:30:00 AM"；日期資訊會隱藏。  但是，日期資訊仍然存在於原始的 `Date` 值中，而且可以使用類似 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 函式的函式來加以復原。  
  
-   **區分文化特性** ：型別轉換函式包含字串，該字串可根據應用程式的目前文化特性設定來執行轉換。  例如，`CDate` 依據您系統上的地區設定 \(Locale\) 來辨認日期的格式。  您必須依照地區設定的正確順序提供日期、月份和年份，否則可能無法正確解譯日期。  如果完整日期格式包含星期幾的字串，例如 "Wednesday"，則會無法辨識它。  
  
     如果您需要在值的字串表示法之間轉換，且使用的格式不是您地區設定所指定的格式，則無法使用 Visual Basic 型別轉換函式。  若要這麼做，請使用該實值型別的 `ToString(IFormatProvider)` 和 `Parse(String, IFormatProvider)` 方法。  例如，將字串轉換成 `Double` 時使用 <xref:System.Double.Parse%2A?displayProperty=fullName>，將型別 `Double` 的值轉換成字串時則使用 <xref:System.Double.ToString%2A?displayProperty=fullName>。  
  
## CType 函式  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)會利用第二個引數 `typename`，將 `expression` 強制型轉為 `typename`，其中的 `typename` 可為任何資料型別、結構、類別，或可有效轉換的介面。  
  
 如需 `CType` 與其他型別轉換關鍵字的比較，請參閱 [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) 和 [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
## CBool 範例  
 下列範例使用 `CBool` 函式來將運算式轉換為 `Boolean` 值。  如果運算式判定為非零值 \(Nonzero\)，`CBool` 會傳回 `True`，否則傳回 `False`。  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## CByte 範例  
 下列範例使用 `CByte` 函式來將運算式轉換為 `Byte`。  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## CChar 範例  
 下列範例使用 `CChar` 函式來將 `String` 運算式的第一個字元轉換為 `Char` 型別。  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 `CChar` 的輸入引數必須是 `Char` 或 `String` 資料型別。  您不能使用 `CChar` 來將數字轉換為字元，因為 `CChar` 不接受數字資料型別。  下列範例會取得表示字碼指標 \(字元碼\) 的數字並將它轉換為對應的字元。  它使用 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 函式來取得數字字串，`CInt` 將字串轉換為 `Integer` 型別，而 `ChrW` 將數字轉換為 `Char` 型別。  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## CDate 範例  
 下列範例使用 `CDate` 函式來將字串轉換為 `Date` 值。  通常不建議將日期和時間硬式編碼為字串 \(如下列範例所示\)。  請改用日期常值和時間常值，例如 \#Feb 12, 1969\# 和 \#4:45:23 PM\#。  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## CDbl 範例  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## CDec 範例  
 下列範例使用 `CDec` 函式將數值轉換為 `Decimal`。  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## CInt 範例  
 下列範例使用 `CInt` 函式來將值轉換為 `Integer`。  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## CLng 範例  
 下列範例使用 `CLng` 函式來將值轉換為 `Long`。  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## CObj 範例  
 下列範例使用 `CObj` 函式將數值轉換為 `Object`。  `Object` 變數本身只包含一個 4 位元組的指標，它會指向指派給它的 `Double` 值。  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## CSByte 範例  
 下列範例使用 `CSByte` 函式將數值轉換為 `SByte`。  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## CShort 範例  
 下列範例使用 `CShort` 函式將數值轉換為 `Short`。  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## CSng 範例  
 下列範例使用 `CSng` 函式來將值轉換為 `Single`。  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## CStr 範例  
 下列範例使用 `CStr` 函式將數值轉換為 `String`。  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 下列範例使用 `CStr` 函式來將 `Date` 值轉換為 `String` 值。  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` 一定會將 `Date` 值，呈現為目前地區設定的標準簡短格式，例如「6\/15\/2003 4:35:47 PM」。  然而，`CStr` 會隱藏日期和時間的「*中性值*」：1\/1\/0001 和 00:00:00。  
  
 如需 `CStr` 傳回值的詳細資訊，請參閱 [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。  
  
## CUInt 範例  
 下列範例使用 `CUInt` 函式將數值轉換為 `UInteger`。  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## CULng 範例  
 下列範例使用 `CULng` 函式將數值轉換為 `ULong`。  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## CUShort 範例  
 下列範例使用 `CUShort` 函式將數值轉換為 `UShort`。  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 <xref:Microsoft.VisualBasic.Strings.Format%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)