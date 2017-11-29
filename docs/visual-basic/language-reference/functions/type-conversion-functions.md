---
title: "類型轉換函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 117cd4ce038a533715bbc86558545f0f223dd149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-functions-visual-basic"></a>類型轉換函式 (Visual Basic)
這些函式是編譯的內嵌，這表示，轉換程式碼程式碼可評估運算式的一部分。 有時候可能沒有任何呼叫程序來完成轉換，進而改善效能。 每個函式會強制特定資料型別運算式。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="part"></a>組件  
 `expression`  
 必要項。 來源資料型別的任何運算式。  
  
## <a name="return-value-data-type"></a>傳回值的資料類型  
 下表所示，函式名稱會決定它所傳回的值的資料類型。  
  
|函式名稱|傳回資料類型|範圍`expression`引數|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何有效`Char`或`String`或數值運算式。|  
|`CByte`|[Byte 資料類型](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 到 255 之間 （不帶正負號）。會捨去小數部分。<sup>1</sup>|  
|`CChar`|[Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)|任何有效`Char`或`String`運算式; 只有第一個字元的`String`轉換; 值可以是 0 到 65535 之間 （不帶正負號）。|  
|`CDate`|[Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)|日期和時間的任何有效表示法。|  
|`CDbl`|[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 到-4.94065645841246544 e-324 負數的值;4.94065645841246544 e-324 到 1.79769313486231570 e + 308 的正值。|  
|`CDec`|[Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+ /-零縮放的數字，也就是沒有小數點的數字 79228162514264337593543950335。 若是 28 位小數的數字，範圍是 + /--7.9228162514264337593543950335。 最小可能的非零值是 0.0000000000000000000000000001 （+ /-1E 28)。|  
|`CInt`|[Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2,147,483,648 到 2,147,483,647。會捨去小數部分。<sup>1</sup>|  
|`CLng`|[Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)|-9223372036854775808 到 9,223,372,036,854,775,807;會捨去小數部分。<sup>1</sup>|  
|`CObj`|[Object 資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)|任何有效的運算式。|  
|`CSByte`|[SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 到 127。會捨去小數部分。<sup>1</sup>|  
|`CShort`|[Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32,768 到 32,767。會捨去小數部分。<sup>1</sup>|  
|`CSng`|[Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 到-1.401298-45 負數的值;1.401298-45 到 3.402823 e + 38 的正數值。|  
|`CStr`|[String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)|傳回`CStr`相依於`expression`引數。 請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。|  
|`CUInt`|[UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 到 4294967295 （不帶正負號）。會捨去小數部分。<sup>1</sup>|  
|`CULng`|[ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 到 18446744073709551615 （不帶正負號）。會捨去小數部分。<sup>1</sup>|  
|`CUShort`|[UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 到 65535 （不帶正負號）。會捨去小數部分。<sup>1</sup>|  
  
 <sup>1</sup>小數部分可能會受到特殊類型的捨入呼叫影響*銀行進位*。 如需詳細資訊，請參閱 < 備註 >。  
  
## <a name="remarks"></a>備註  
 因此，您應該使用 Visual Basic 類型轉換函式，而非.NET Framework 方法例如`ToString()`，在上<xref:System.Convert>類別或個別的類型結構或類別。 Visual Basic 函式專為與 Visual Basic 程式碼，最佳的互動，而且它們也會使原始程式碼短也更容易閱讀。 此外，.NET Framework 轉換方法不一定會產生相同的結果做為 Visual Basic 函式，例如當轉換`Boolean`至`Integer`。 如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="behavior"></a>行為  
  
-   **強制型轉。** 一般情況下，您可以使用資料類型轉換函式強制轉型為特定資料類型，而不是預設的資料型別作業的結果。 例如，使用`CDec`來強制執行在其中單精確度、 雙精確度或整數運算也通常不會發生的情況下的十進位運算。  
  
-   **轉換失敗。** 如果`expression`傳遞至函式超出範圍的資料類型會是轉換， <xref:System.OverflowException> ，就會發生。  
  
-   **小數部分。** 在您將非整數值轉換成整數類資料類型時，整數轉換函式 (`CByte`， `CInt`， `CLng`， `CSByte`， `CShort`， `CUInt`， `CULng`，和`CUShort`) 移除小數部分，四捨五入為最接近的整數值。  
  
     如果小數部分正好 0.5，整數轉換函式捨入至最接近的偶數整數。 例如，0.5 捨入為 0，1.5 和 2.5 都會捨入為 2。 這有時候稱為*銀行進位*，和其目的是要彌補可能會不斷累積時將此類數字相加的偏差。  
  
     `CInt`和`CLng`不同<xref:Microsoft.VisualBasic.Conversion.Int%2A>和<xref:Microsoft.VisualBasic.Conversion.Fix%2A>函式，它們截斷，而不是圓形，數字的小數部分。 此外，`Fix`和`Int`一律傳回相同的資料類型的值，將傳入。  
  
-   **日期/時間轉換。** 使用<xref:Microsoft.VisualBasic.Information.IsDate%2A>函式來判斷值是否可以轉換成日期和時間。 `CDate`可辨識的日期常值和時間常值，但不是數值。 要轉換的 Visual Basic 6.0`Date`值設定為`Date`在 Visual Basic 2005 中的值或更新版本，您可以使用<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>方法。  
  
-   **中性日期/時間值。** [日期資料型別](../../../visual-basic/language-reference/data-types/date-data-type.md)一定會包含日期和時間資訊。 類型轉換的目的而言，Visual Basic 視為 1/1/0001 (1 年的 1 年)*中性值*日期，和 00:00:00 （午夜） 是中性值的時間。 如果您要轉換`Date`值到一個字串，`CStr`中產生的字串不包含中性的值。 例如，如果您要轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"; 隱藏日期資訊。 不過，將日期資訊是仍會出現在原始`Date`值，並可以復原與函式例如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>函式。  
  
-   **區分文化。** 字串的相關的類型轉換函式會執行轉換取決於應用程式的目前文化特性設定。 例如，`CDate`可辨識的日期格式，根據您的系統地區設定。 您必須提供日、 月和年針對您的地區設定正確的順序，或可能不正確解譯日期。 如果它包含的週日期字串，例如 「 星期三 」 無法辨識的完整日期格式。  
  
     如果您需要轉換或從您的地區設定所指定以外的格式的值的字串表示，您無法使用 Visual Basic 的類型轉換函式。 若要這樣做，請使用`ToString(IFormatProvider)`和`Parse(String, IFormatProvider)`該實值類型的方法。 例如，使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>字串轉換成`Double`，並使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`為字串。  
  
## <a name="ctype-function"></a>CType Function  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)採用第二個引數， `typename`，並轉`expression`至`typename`，其中`typename`可以是任何資料類型、 結構、 類別或介面的有有效的轉換。  
  
 如需的比較`CType`與其他類型轉換關鍵字，請參閱[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
## <a name="cbool-example"></a>CBool 範例  
 下列範例會使用`CBool`函式將轉換運算式到`Boolean`值。 如果運算式評估為非零值，`CBool`傳回`True`; 否則它會傳回`False`。  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte 範例  
 下列範例會使用`CByte`函式將轉換運算式，以便`Byte`。  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>CChar 範例  
 下列範例會使用`CChar`函式將轉換的第一個字元`String`運算式`Char`型別。  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 若要輸入的引數`CChar`的資料類型必須是`Char`或`String`。 您無法使用`CChar`轉換成字元的數字，因為`CChar`無法接受的數值資料類型。 下列範例會取得代表的字碼指標 （字元碼） 的數字，並將它轉換成對應的字元。 它會使用<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>函式可取得的數字、 字串`CInt`將輸入字串轉換`Integer`，和`ChrW`轉換要輸入的數字`Char`。  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>CDate 範例  
 下列範例會使用`CDate`函式可將字串轉換為`Date`值。 一般情況下，不建議進行硬式編碼的日期和時間為字串 （如本範例所示）。 使用日期常值和時間常值，例如 #Feb 12，&#1969; 和 # 4:45:23 PM #，改為。  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl 範例  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec 範例  
 下列範例會使用`CDec`函式，將數字值轉換成`Decimal`。  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>CInt 範例  
 下列範例會使用`CInt`函式，將值轉換成`Integer`。  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>CLng 範例  
 下列範例會使用`CLng`函式，將值轉換為`Long`。  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>CObj 範例  
 下列範例會使用`CObj`函式，將數字值轉換成`Object`。 `Object`變數本身僅包含四個位元組指標，指向`Double`指派給它的值。  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>CSByte 範例  
 下列範例會使用`CSByte`函式，將數字值轉換成`SByte`。  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>CShort 範例  
 下列範例會使用`CShort`函式，將數字值轉換成`Short`。  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng 範例  
 下列範例會使用`CSng`函式，將值轉換為`Single`。  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>CStr 範例  
 下列範例會使用`CStr`函式，將數字值轉換成`String`。  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 下列範例會使用`CStr`函式將轉換`Date`值`String`值。  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr`一律會呈現`Date`目前地區設定，例如，標準的簡短格式的值"2003 年 6 月 15 日 4:35:47 PM"。 不過，`CStr`隱藏*中性值*的 1/1/0001 的日期和時間的 00:00:00。  
  
 如需詳細資訊，所傳回的值上`CStr`，請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。  
  
## <a name="cuint-example"></a>CUInt 範例  
 下列範例會使用`CUInt`函式，將數字值轉換成`UInteger`。  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>CULng 範例  
 下列範例會使用`CULng`函式，將數字值轉換成`ULong`。  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>CUShort 範例  
 下列範例會使用`CUShort`函式，將數字值轉換成`UShort`。  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>另請參閱  
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
 [轉換函式](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
