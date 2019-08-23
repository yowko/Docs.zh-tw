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
ms.openlocfilehash: 858b2b2e154b659470fa61b21f25ab61eabda012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965660"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>擴展和縮小轉換 (Visual Basic)
類型轉換的重要考慮是轉換的結果是否在目的地資料類型的範圍內。  
  
 *擴輾轉換*會將值變更為資料類型, 以允許原始資料的任何可能值。  擴輾轉換會保留來源值, 但可以變更其表示。 如果您從整數類資料類型轉換為`Decimal`, 或`String`從`Char`轉換為, 就會發生此情況。  
  
 *「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。 例如, 當小數值轉換成整數類資料類型, 而且轉換成`Boolean`的數數值型別縮小`True`為或`False`時, 就會將其四捨五入。  
  
## <a name="widening-conversions"></a>擴展轉換  
 下表顯示標準的擴輾轉換。  
  
|資料類型|擴大至資料類型<sup>1</sup>|  
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
|任何列舉型別 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|其基礎整數類型, 以及基礎類型所擴展的任何類型。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`、 `String`|  
|`Char` 陣列|`Char`數列`String`|  
|任何型別|[物件](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|任何衍生類型|衍生它的任何基底類型<sup>3</sup>。|  
|任何型別|它所實行的任何介面。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何資料類型或物件類型。|  
  
 <sup>1</sup>根據定義, 每個資料類型會擴展到其本身。  
  
 <sup>2</sup> `Integer`從、 、、`Single`或轉換為或`Double`可能會導致精確度遺失, 但不會遺失大小。 `Decimal` `Long` `UInteger` `ULong` 就這一點而言, 它們不會造成資訊遺失。  
  
 <sup>3</sup>在從衍生型別轉換成其中一個基底類型時, 它看起來可能會很令人驚訝。 理由是, 衍生的型別包含基底型別的所有成員, 因此它會限定為基底型別的實例。 相反地, 基底類型不會包含衍生類型所定義的任何新成員。  
  
 擴輾轉換一律會在執行時間成功, 而且永遠不會產生資料遺失。 無論[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是否將類型檢查參數設定為`On`或`Off`, 您都可以隱含地執行它們。  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 標準的縮小轉換包括下列各項:  
  
- 上表中擴輾轉換的反向指示 (不同的是, 每個類型會擴展為其本身)  
  
- [布林值](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)與任何數數值型別之間任一方向的轉換  
  
- 從任何數數值型別轉換成任何列舉類型 (`Enum`)  
  
- [字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)與任何數數值型別、 `Boolean`或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)之間任一方向的轉換  
  
- 從資料類型或物件類型轉換成衍生自它的類型  
  
 縮小轉換在執行時間不一定會成功, 而且可能會失敗或產生資料遺失。 如果目的地資料類型無法接收要轉換的值, 就會發生錯誤。 例如, 數值轉換可能會造成溢位。 除非[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)將類型檢查參數設定為`Off`, 否則編譯器不允許您隱含執行縮小轉換。  
  
> [!NOTE]
> 將`For Each…Next`集合中的專案轉換為迴圈控制變數時, 會抑制縮小轉換錯誤。 如需詳細資訊和範例, 請參閱 For Each ... 中的「縮小轉換」一節。 [下一個語句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>使用縮小轉換的時機  
 當您知道來源值可以轉換成目的地資料類型, 而不會發生錯誤或資料遺失時, 您會使用縮小轉換。 例如, 如果您知道有`String`包含 "True" 或 "False" 的, 您可以`CBool`使用關鍵字將它轉換成`Boolean`。  
  
## <a name="exceptions-during-conversion"></a>轉換期間的例外狀況  
 由於擴輾轉換一律會成功, 因此不會擲回例外狀況。 縮小轉換時, 當它們失敗時, 最常擲回下列例外狀況:  
  
- <xref:System.InvalidCastException>-如果兩個類型之間沒有定義轉換  
  
- <xref:System.OverflowException>-(僅限整數類型), 如果轉換過的值對目標型別而言太大  
  
 如果類別或結構定義了[CType](../../../../visual-basic/language-reference/functions/ctype-function.md)函式, 以做為與該類別或結構之間的轉換運算子, `CType`則可能會擲回其認為適當的任何例外狀況。 此外, 這`CType`可能會呼叫 Visual Basic 函式或 .NET Framework 方法, 進而擲回各種例外狀況。  
  
## <a name="changes-during-reference-type-conversions"></a>參考型別轉換期間的變更  
 從*參考型*別進行的轉換只會將指標複製到值。 值本身不會以任何方式複製也不會變更。 唯一可以變更的東西是包含指標之變數的資料類型。 在下列範例中, 資料類型會從衍生類別轉換為其基類, 但目前這兩個變數所指向的物件不會變更。  
  
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
- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：在 Visual Basic 中將物件轉換成另一種類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
