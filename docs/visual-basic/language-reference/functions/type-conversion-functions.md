---
title: 類型轉換函式 (Visual Basic)
ms.date: 10/24/2018
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
ms.openlocfilehash: 3321a9a290e6ba49be289848e4d16907ad9edbda
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662584"
---
# <a name="type-conversion-functions-visual-basic"></a>類型轉換函式 (Visual Basic)
這些函式是編譯的內嵌，這表示，轉換程式碼評估運算式的程式碼的一部分。 有時是沒有呼叫程序來完成轉換，進而改善效能。 每個函式強制轉型為特定的資料類型的運算式。  
  
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
|`CByte`|[Byte 資料類型](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) 透過<xref:System.Byte.MaxValue?displayProperty=nameWithType>(255) （不帶正負號），會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與位元組轉換成浮點數`CByte`函式; 請參閱[備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CChar`|[Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)|任何有效`Char`或是`String`運算式; 只有第一個字元`String`轉換; 值可以是 0 到 65535 （不帶正負號）。|  
|`CDate`|[Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)|日期和時間的任何有效表示法。|  
|`CDbl`|[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 到-4.94065645841246544-324 (負值）4.94065645841246544-324 到 1.79769313486231570 e + 308 的正值。|  
|`CDec`|[Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+ /-零擴充的數字，也就是任何小數位數的數字 79228162514264337593543950335。 如 28 位小數的數字，範圍是 + /--7.9228162514264337593543950335。 最小可能的非零值是 0.0000000000000000000000000001 （+ /-1E-28)。|  
|`CInt`|[Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) 到<xref:System.Int32.MaxValue?displayProperty=nameWithType>(2147483647)，會捨去小數部分。<sup>1</sup> <br/><br/>從 Visual Basic 15.8 開始，Visual Basic 最佳化與整數轉換成浮點數的效能`CInt`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。 |  
|`CLng`|[Long 資料類型](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) 到<xref:System.Int64.MaxValue?displayProperty=nameWithType>(9223372036854775807)，會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化浮點，以使用 64 位元的整數轉換`CLng`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CObj`|[Object 資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)|任何有效的運算式。|  
|`CSByte`|[SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) 透過<xref:System.SByte.MaxValue?displayProperty=nameWithType>(127)，會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與帶正負號的位元組轉換成浮點數`CSByte`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CShort`|[Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) 到<xref:System.Int16.MaxValue?displayProperty=nameWithType>(32,767)，會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與 16 位元的整數轉換成浮點數`CShort`函式; 請參閱[備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CSng`|[Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 到-1.401298E-45 (負值）從 1.401298E-45 到 3.402823 e + 38 的正數值。|  
|`CStr`|[String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)|會傳回`CStr`取決於`expression`引數。 請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。|  
|`CUInt`|[UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) 透過<xref:System.UInt32.MaxValue?displayProperty=nameWithType>(4,294,967,295) （不帶正負號），會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的整數轉換成浮點數`CUInt`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CULng`|[ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) 透過<xref:System.UInt64.MaxValue?displayProperty=nameWithType>(18446744073709551615) （不帶正負號），會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的長整數轉換成浮點數`CULng`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
|`CUShort`|[UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) 透過<xref:System.UInt16.MaxValue?displayProperty=nameWithType>(65,535) （不帶正負號），會捨去小數部分。<sup>1</sup><br/><br/>從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的 16 位元整數轉換成浮點數`CUShort`函式; 請參閱[備註](#remarks)節的詳細資訊。 請參閱[CInt 範例](#cint-example)一節中的範例。|  
  
 <sup>1</sup>小數部分可能會受到特殊類型的捨入呼叫影響*銀行進位*。 如需詳細資訊，請參閱 < 備註 >。  
  
## <a name="remarks"></a>備註  
 因此，您應該使用 Visual Basic 型別轉換函式，而非.NET Framework 方法，例如`ToString()`，在<xref:System.Convert>類別或個別類型結構或類別。 Visual Basic 函式專為 Visual Basic 程式碼，最佳的互動，它們也可讓您的程式碼更簡短、 更方便閱讀。 此外，.NET Framework 轉換方法不一定會產生與 Visual Basic 函式，例如，轉換時相同的結果`Boolean`至`Integer`。 如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  

從 Visual Basic 15.8，浮點-點對點-整數的轉換的效能最佳化傳遞時<xref:System.Single>或是<xref:System.Double>遵循以下方法傳回整數的轉換函式的其中一個值 (`CByte`， `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

此最佳化可讓執行整數轉換為以兩倍速度執行的一大堆程式碼。 下列範例會說明這些最佳化浮點-點對點對整數的轉換：

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>行為  
  
- **強制型轉。** 一般情況下，您可以使用資料類型轉換函式，以強制轉型作業特定的資料類型，而不是預設的資料類型的結果。 例如，使用`CDec`來強制執行在其中單精確度、 雙精確度或整數算術會通常會發生的情況下的十進位運算。  
  
- **轉換失敗。** 如果`expression`傳遞至函式超出範圍的資料型別，它就是轉換， <xref:System.OverflowException> ，就會發生。  
  
- **小數部分。** 當您將非整數值轉換成整數類型，整數的轉換函式 (`CByte`， `CInt`， `CLng`， `CSByte`， `CShort`， `CUInt`， `CULng`，以及`CUShort`) 移除小數部分，並捨入為最接近的整數值。  
  
     如果小數部分正好 0.5，整數的轉換函式將它四捨五入到最接近的偶數整數。 比方說，0.5 捨入為 0，1.5 和 2.5 都會捨入為 2。 這有時候稱為*銀行進位*，其用途是為了彌補可能會不斷累積時將許多這類的數字相加的偏差。  
  
     `CInt` 並`CLng`有所不同<xref:Microsoft.VisualBasic.Conversion.Int%2A>和<xref:Microsoft.VisualBasic.Conversion.Fix%2A>函式，其截斷，而不是四捨五入，數字的小數部分。 此外，`Fix`和`Int`一律傳回相同的資料類型的值，因為您傳入。  
  
- **日期/時間轉換。** 使用<xref:Microsoft.VisualBasic.Information.IsDate%2A>函式來判斷值是否可轉換成日期和時間。 `CDate` 可辨識的日期常值和時間常值，但不是數值。 若要轉換 Visual Basic 6.0`Date`值加入`Date`Visual Basic 2005 中的值或更新版本，您可以使用<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>方法。  
  
- **中性日期/時間值。** [日期資料型別](../../../visual-basic/language-reference/data-types/date-data-type.md)一定會包含日期和時間資訊。 基於型別轉換的詳細資訊，Visual Basic，請考慮為的 1/1/0001 (1 年的 1 年)*中性值*是中性的值時間的日期和 00:00:00 （午夜）。 如果您將轉換`Date`值為字串，`CStr`不產生的字串中包含中性的值。 例如，如果您將轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"，隱藏的日期資訊。 不過，日期資訊是仍會出現在原始`Date`值，而且可以使用函式這類復原<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>函式。  
  
- **區分文化。** 字串類型轉換函式會執行目前的文化特性設定，應用程式為基礎的轉換。 比方說，`CDate`會辨識您的系統地區設定的日期格式。 您必須提供一天、 月和年在您的地區設定，以正確的順序，或可能不正確地解譯日期。 如果它包含的週日期字串，例如"Wednesday"無法辨識的長日期格式。  
  
     如果您需要將轉換成或從您的地區設定所指定以外格式的值的字串表示，您無法使用 Visual Basic 型別轉換函式。 若要這樣做，請使用`ToString(IFormatProvider)`和`Parse(String, IFormatProvider)`該實值型別的方法。 比方說，使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>若要將字串轉換成`Double`，並使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`為字串。  
  
## <a name="ctype-function"></a>CType Function  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)採用第二個引數`typename`，會強制轉型`expression`來`typename`，其中`typename`可以是任何資料類型、 結構、 類別或介面要有有效的轉換。  
  
 如需的比較`CType`類型轉換關鍵字，請參閱[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)並[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
## <a name="cbool-example"></a>CBool 範例  
 下列範例會使用`CBool`函式將轉換運算式到`Boolean`值。 如果運算式評估為非零值，`CBool`會傳回`True`; 否則它會傳回`False`。  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>CByte 範例  
 下列範例會使用`CByte`函式將轉換運算式，以`Byte`。  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>CChar 範例  
 下列範例會使用`CChar`要轉換的第一個字元的函式`String`運算式`Char`型別。  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 若要輸入的引數`CChar`必須是資料型別`Char`或`String`。 您無法使用`CChar`轉換成字元，數字，因為`CChar`無法接受的數值資料類型。 下列範例會取得代表的字碼指標 （字元碼） 的數字，並將它轉換成對應的字元。 它會使用<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>函式來取得的數字、 字串`CInt`若要將字串轉換為類型`Integer`，和`ChrW`轉換要輸入的數字`Char`。  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>CDate 範例  
 下列範例會使用`CDate`函式來將字串轉換為`Date`值。 一般情況下，不建議硬式編碼的日期和時間字串 （如本範例所示）。 使用日期常值和時間常值，例如 #Feb 12，1969 # 和 # 4:45:23 PM #，改為。  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>CDbl 範例  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>CDec 範例  
 下列範例會使用`CDec`函數來轉換數值`Decimal`。  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>CInt 範例  
 下列範例會使用`CInt`函式，將值轉換成`Integer`。  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>CLng 範例
 下列範例會使用`CLng`函式來將值轉換成`Long`。  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>CObj 範例  
 下列範例會使用`CObj`函數來轉換數值`Object`。 `Object`變數本身包含只有四位元組指標，指向`Double`指派給它的值。  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>CSByte 範例  
 下列範例會使用`CSByte`函數來轉換數值`SByte`。  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>CShort 範例  
 下列範例會使用`CShort`函數來轉換數值`Short`。  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>CSng 範例  
 下列範例會使用`CSng`函式來將值轉換成`Single`。  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>CStr 範例  
 下列範例會使用`CStr`函數來轉換數值`String`。  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 下列範例會使用`CStr`要轉換的函式`Date`值來`String`值。  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` 一律會呈現`Date`目前地區設定，例如，標準的簡短格式的值 」 時間 2003 年 6 月 15 日下午 4:35:47"。 不過，`CStr`抑制*中性值*的 1/1/0001 的日期和時間為 00:00:00。  
  
 如需詳細資訊，所傳回的值`CStr`，請參閱 < [CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。  
  
## <a name="cuint-example"></a>CUInt 範例  
 下列範例會使用`CUInt`函數來轉換數值`UInteger`。  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>CULng 範例  
 下列範例會使用`CULng`函數來轉換數值`ULong`。  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>CUShort 範例  
 下列範例會使用`CUShort`函數來轉換數值`UShort`。  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [轉換函式](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [在 Visual Basic 中的類型轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
