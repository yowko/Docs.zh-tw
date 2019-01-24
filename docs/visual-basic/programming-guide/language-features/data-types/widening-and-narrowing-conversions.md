---
title: 擴展和縮小轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: d1b573dbafbead20330a4fd0f62e8f21f27dce81
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610925"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>擴展和縮小轉換 (Visual Basic)
使用類型轉換的重要考量是轉換的結果是否在目的地資料類型的範圍內。  
  
 A*擴展轉換*值變更為可允許任何可能的值，原始資料的資料類型。  擴展轉換保留原始值，但可以變更其表示法。 如果您從整數類資料類型轉換的之所以`Decimal`，或從`Char`至`String`。  
  
 *「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。 比方說，小數的值，則會轉換成整數類資料類型，並轉換成數值類型後便會四捨五入`Boolean`縮減為其中一個`True`或`False`。  
  
## <a name="widening-conversions"></a>擴展轉換  
 下表顯示標準的擴展轉換。  
  
|資料類型|資料類型可擴展<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`、 `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|任何列舉型別 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|其基礎的整數類資料類型和任何類型的擴展基礎的型別。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`、 `String`|  
|`Char` 陣列|`Char` 陣列， `String`|  
|任何型別|[物件](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|任何衍生型別|任何基底的類型衍生自此<sup>3</sup>。|  
|任何型別|它會實作任何介面。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何資料型別或物件型別。|  
  
 <sup>1</sup>根據定義，每個資料類型可擴展為本身。  
  
 <sup>2</sup>從不`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`至`Single`或`Double`可能會導致遺失有效位數，但永遠不會遺失大小。 在這種情況下它們不會造成資訊遺失。  
  
 <sup>3</sup>一定很驚訝從衍生的型別轉換為其基底型別會擴展。 理由是衍生型別包含的基底類型中，所有成員，因此它有資格做為基底類型的執行個體。 朝相反的方向的基底類型不包含任何新的成員所衍生的型別定義。  
  
 擴展轉換時，一律在執行階段成功，而且永遠不會造成資料遺失。 您可以隱含地執行它們是否[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定檢查參數的型別`On`或`Off`。  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 標準的縮小轉換包括下列各項：  
  
-   在上述的擴展轉換的反向資料表 （不同之處在於每個類型可擴展為本身）  
  
-   在任一方向之間的轉換[布林](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)和任何數值類型  
  
-   從任何數值類型轉換為任何列舉型別 (`Enum`)  
  
-   在任一方向之間的轉換[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)任何數值類型，以及`Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   從資料型別或物件型別轉換成從其衍生類型  
  
 縮小轉換執行不一定成功在執行階段，並可能會失敗或者會造成資料遺失。 如果目的地資料類型無法接收轉換的值，就會發生錯誤。 例如，數值轉換可能會導致溢位。 編譯器不允許以隱含方式執行縮小轉換，除非[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定類型檢查參數以`Off`。  
  
> [!NOTE]
>  轉換中的項目隱藏的縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。 如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>何時使用縮小轉換  
 當您知道來源值可以轉換成目的資料型別，而不會錯誤或資料遺失時，您可以使用縮小轉換。 例如，如果您有`String`您知道包含"True"False"，您可以使用`CBool`關鍵字來將它轉換成`Boolean`。  
  
## <a name="exceptions-during-conversion"></a>在轉換期間的例外狀況  
 因為一律擴展轉換成功，則不會擲回例外狀況。 縮小轉換，失敗時，通常會擲回下列例外狀況：  
  
-   <xref:System.InvalidCastException> -如果任何轉換不定義兩個類型之間  
  
-   <xref:System.OverflowException> -（只有整數類型） 如果已轉換的值太大的目標型別  
  
 如果類別或結構定義[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)做為與該類別或結構，轉換運算子，`CType`可能會擲回它認為適當的任何例外狀況。 此外，所`CType`可能會呼叫 Visual Basic 函式或[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]接著可能會擲回例外狀況的各種不同的方法。  
  
## <a name="changes-during-reference-type-conversions"></a>參考型別轉換期間的變更  
 從轉換*參考的型別*複製值的指標。 值本身不會複製或以任何方式變更。 唯一可以變更為指標的變數的資料類型。 在下列範例中，資料類型轉換從衍生類別為其基底類別，但這兩個變數現在指向的物件不會變更。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>另請參閱
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
