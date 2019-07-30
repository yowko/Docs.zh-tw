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
ms.openlocfilehash: 4bcf2d76a2983294f244b72f286842a92fb5e64e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512872"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>隱含和明確轉換 (Visual Basic)

*隱含轉換*在原始程式碼中不需要任何特殊語法。 在下列範例中, Visual Basic 會先將的值`k`隱含轉換為單精確度浮點數, 再將它指派給`q`。

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

*明確轉換*會使用類型轉換關鍵字。 Visual Basic 提供了數個這類關鍵字, 可將括弧中的運算式強制轉型為所需的資料類型。 這些關鍵字的作用就像函式, 但編譯器會產生內嵌程式碼, 因此執行的速度會比函式呼叫稍微快。

在上述範例的下列延伸模組中, `CInt`關鍵字會將的`q`值轉換回整數, 再將它指派給`k`。

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>轉換關鍵字

下表顯示可用的轉換關鍵字。

|類型轉換關鍵字|將運算式轉換為資料類型|允許轉換之運算式的資料類型|
|---|---|---|
|`CBool`|[Boolean 資料類型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `String`、`Object`|
|`CByte`|[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任何數數值型別 (包括`SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CChar`|[Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`、 `Object`|
|`CDate`|[Date 資料類型](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`、 `Object`|
|`CDbl`|[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CDec`|[Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CInt`|[Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CLng`|[Long 資料類型](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CObj`|[Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任何型別|
|`CSByte`|[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任何數數值型別 (包括`Byte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CShort`|[Short 資料類型](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CSng`|[Single 資料類型](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CStr`|[String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `Char`、 `Char` array、 `Date`、`Object`|
|`CType`|在逗號 (`,`) 後面指定的類型|轉換成*基本資料類型*(包括基本類型的陣列) 時, 與對應的轉換關鍵字所允許的類型相同<br /><br /> 轉換成*複合資料型別*時, 它所執行的介面和它所繼承的類別<br /><br /> 轉換成您已`CType`多載的類別或結構時, 該類別或結構|
|`CUInt`|[UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CULng`|[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|
|`CUShort`|[UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任何數數值型別 (包括`Byte`、 `SByte`和列舉類型)、 `Boolean`、 `String`、`Object`|

## <a name="the-ctype-function"></a>CType 函式

[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)會在兩個引數上運作。 第一個是要轉換的運算式, 第二個是目的地資料類型或物件類別。 請注意, 第一個引數必須是運算式, 而不是類型。

`CType`是*內嵌*函式, 這表示已編譯的程式碼會進行轉換, 通常不會產生函式呼叫。 這會改善效能。

如需`CType`與其他類型轉換關鍵字的比較, 請參閱[DirectCast 運算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)。

### <a name="elementary-types"></a>基本類型

下列範例示範 `CType` 的用法。

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>複合類型

您可以使用`CType`將值轉換成複合資料型別以及基本類型。 您也可以使用它將物件類別強制轉型為其中一個介面的類型, 如下列範例所示。

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>陣列類型

`CType`也可以轉換陣列資料類型, 如下列範例所示。

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

如需詳細資訊和範例, 請參閱[陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。

### <a name="types-defining-ctype"></a>定義 CType 的類型

您可以在`CType`已定義的類別或結構上定義。 這可讓您將值轉換為類別或結構的類型。 如需詳細資訊和範例, 請[參閱如何:定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。

> [!NOTE]
> 搭配轉換關鍵字使用的值, 對於目的地資料類型而言必須是有效的, 否則會發生錯誤。 例如, 如果`Long`您嘗試將轉換`Integer`成`Long` , 則的值`Integer`必須在資料類型的有效範圍內。

> [!CAUTION]
> 如果`CType`來源類型不是衍生自目的地類型, 指定要從一個類別類型轉換成另一個類別類型時, 會在執行時間失敗。 這類失敗<xref:System.InvalidCastException>會擲回例外狀況。

不過, 如果其中一種類型是您已定義的結構或類別, 而且如果您已在`CType`該結構或類別上定義, 則轉換可能會在滿足的需求`CType`時成功。 請參閱[How to:定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。

執行明確轉換也稱為將運算式*轉換*成指定的資料類型或物件類別。

## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：在 Visual Basic 中將物件轉換成另一種類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
