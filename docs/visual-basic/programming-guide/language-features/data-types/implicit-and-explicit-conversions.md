---
title: 隱含和明確轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008250"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>隱含和明確轉換 (Visual Basic)
*隱含轉換*不需要任何特殊的語法，在原始程式碼中。 在下列範例中，Visual Basic 會隱含地將值轉換`k`為單精確度浮點數值之前將它指派給`q`。  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *明確轉換*使用類型轉換關鍵字。 Visual Basic 提供數個這類關鍵字，會強制轉型為所需的資料類型的括號括住的運算式。 這些關鍵字做為函式，但是編譯器會產生內嵌程式碼，因此執行速度稍微比函式呼叫。  
  
 在以下的上述範例中，擴充`CInt`關鍵字的值轉換`q`回之前將它指派給整數`k`。  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>轉換關鍵字  
 下表顯示可用的轉換關鍵字。  
  
|型別轉換關鍵字|將運算式轉換成資料類型|要轉換之運算式的可允許的資料類型|  
|---|---|---|  
|`CBool`|[Boolean 資料類型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `String`， `Object`|  
|`CByte`|[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任何數值類型 (包括`SByte`以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CChar`|[Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`、 `Object`|  
|`CDate`|[Date 資料類型](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`、 `Object`|  
|`CDbl`|[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CDec`|[Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CInt`|[Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CLng`|[Long 資料類型](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CObj`|[Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任何型別|  
|`CSByte`|[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任何數值類型 (包括`Byte`以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CShort`|[Short 資料類型](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CSng`|[Single 資料類型](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CStr`|[String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `Char`，`Char`陣列， `Date`， `Object`|  
|`CType`|輸入指定下列的逗號 (`,`)|當轉換成*基本資料型別*（包括基礎類型的陣列），相同類型所允許的對應轉換關鍵字<br /><br /> 當轉換成*複合資料型別*，它會實作的介面和它所繼承的類別<br /><br /> 當轉換成類別或結構上您有多載`CType`，該類別或結構|  
|`CUInt`|[UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CULng`|[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
|`CUShort`|[UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任何數值類型 (包括`Byte`， `SByte`，以及列舉型別)， `Boolean`， `String`， `Object`|  
  
## <a name="the-ctype-function"></a>CType 函式  
 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)作兩個引數。 第一個是要轉換的運算式和第二個是目的地資料類型或物件類別。 請注意，第一個引數必須是運算式，不是型別。  
  
 `CType` 已*內嵌函式*，這表示已編譯的程式碼會進行轉換，通常不會產生函式呼叫。 這可改善效能。  
  
 如需的比較`CType`類型轉換關鍵字，請參閱[DirectCast 運算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)並[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
### <a name="elementary-types"></a>基礎類型  
 下列範例示範 `CType` 的用法。  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>複合類型  
 您可以使用`CType`將值轉換為複合資料型別以及基本型別。 您也可以使用要強制轉型的物件類別，其中一個介面，如下列範例所示的型別。  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>陣列類型  
 `CType` 也是可以轉換的陣列資料型別，如下列範例所示。  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 如需詳細資訊和範例，請參閱 <<c0> [ 陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。  
  
### <a name="types-defining-ctype"></a>定義 CType 的類型  
 您可以定義`CType`上類別或您已定義的結構。 這可讓您將從您的類別或結構的型別來回轉換值。 如需詳細資訊和範例，請參閱[How to:定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
> [!NOTE]
>  轉換關鍵字搭配使用的值必須是有效的目的地資料類型，或發生錯誤。 比方說，如果您嘗試轉換`Long`要`Integer`，值`Long`的有效範圍內必須是`Integer`資料型別。  
  
> [!CAUTION]
>  指定`CType`如果來源類型並非衍生自目的型別，從一個類別的型別轉換為另一個在執行階段失敗。 此類錯誤會擲回<xref:System.InvalidCastException>例外狀況。  
  
 不過，如果其中一個型別結構或類別定義，而且您已定義`CType`在該結構或類別中，如果它能滿足的需求，可以成功轉換您`CType`。 請參閱[如何：定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
 執行明確的轉換，也就是*轉型*運算式，以指定的資料型別或物件類別。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
