---
title: Widening and Narrowing Conversions
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
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058530"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>擴展和縮小轉換 (Visual Basic)

類型轉換的重要考慮是轉換的結果是否在目的地資料類型的範圍內。  
  
 「 *擴展」轉換* 會將值變更為資料類型，以允許任何可能的原始資料值。  擴輾轉換會保留來源值，但可以變更其標記法。 如果您從整數類資料類型轉換為，或從轉換成，就會發生這種情況 `Decimal` `Char` `String` 。  
  
 *「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。 例如，當小數值轉換成整數類資料類型，而且要轉換的數數值型別縮減為或時，會將其四捨五入 `Boolean` `True` `False` 。  
  
## <a name="widening-conversions"></a>擴展轉換  

 下表顯示標準的擴輾轉換。  
  
|資料類型|擴大至資料類型 <sup>1</sup>|  
|---|---|  
|[SByte](../../../language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[位元組](../../../language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[短](../../../language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[整數](../../../language-reference/data-types/integer-data-type.md)|`Integer`、 `Long` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup>|  
|[UInteger](../../../language-reference/data-types/uinteger-data-type.md)|`UInteger`、 `Long` 、 `ULong` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup>|  
|[Long](../../../language-reference/data-types/long-data-type.md)|`Long`、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup>|  
|[ULong](../../../language-reference/data-types/ulong-data-type.md)|`ULong`、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup>|  
|[十進位](../../../language-reference/data-types/decimal-data-type.md)|`Decimal`、 `Single` 、 `Double` <sup>2</sup>|  
|[Single](../../../language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|[列舉 (列舉](../../../language-reference/statements/enum-statement.md)型別) |其基礎整數型別，以及基礎類型擴展的任何型別。|  
|[字元](../../../language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 陣列|`Char` 陣 列 `String`|  
|任何型別|[Object](../../../language-reference/data-types/object-data-type.md)|  
|任何衍生類型|衍生自的任何基底類型 <sup>3</sup>。|  
|任何型別|它所實行的任何介面。|  
|[什麼](../../../language-reference/nothing.md)|任何資料類型或物件類型。|  
  
 <sup>1</sup> 依照定義，每個資料類型都會擴大為本身。  
  
 <sup>2</sup> 從 `Integer` 、 `UInteger` 、 `Long` 、或轉換 `ULong` `Decimal` 成 `Single` 或 `Double` 可能會導致精確度遺失，但不會遺失大小。 在這種情況下，不會導致資訊遺失。  
  
 <sup>3</sup> 看看從衍生型別轉換成其基底類型的其中一個基底類型，可能看起來很奇怪。 理由是衍生型別包含基底類型的所有成員，因此它會限定為基底類型的實例。 相反地，基底類型不包含任何由衍生型別所定義的新成員。  
  
 擴輾轉換一律會在執行時間成功，且不會產生資料遺失。 您一律可以隱含地執行它們，無論 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 是否將型別檢查參數設定為 `On` 或 `Off` 。  
  
## <a name="narrowing-conversions"></a>縮小轉換  

 標準的縮小轉換包含下列各項：  
  
- 上表中擴輾轉換的反向指示 (，但每個類型會擴大為本身)   
  
- 在 [布林值](../../../language-reference/data-types/boolean-data-type.md) 與任何數數值型別之間的雙向轉換  
  
- 從任何數數值型別轉換成任何列舉型別 (`Enum`)   
  
- [字串](../../../language-reference/data-types/string-data-type.md)與任何數數值型別、 `Boolean` 或[日期](../../../language-reference/data-types/date-data-type.md)之間的任何方向轉換  
  
- 從資料類型或物件類型轉換成衍生自它的型別  
  
 縮小轉換在執行時間不一定會成功，而且可能會失敗或導致資料遺失。 如果目的地資料類型無法接收要轉換的值，就會發生錯誤。 例如，數值轉換可能會造成溢位。 編譯器不允許您隱含地執行縮小轉換，除非 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 將類型檢查參數設定為 `Off` 。  
  
> [!NOTE]
> 從集合中的專案轉換 `For Each…Next` 到迴圈控制變數時，會隱藏縮小轉換錯誤。 如需詳細資訊和範例，請參閱 For Each 中的「縮小轉換」一節。 [下一個語句](../../../language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>使用縮小轉換的時機  

 當您知道來源值可以轉換為目的地資料類型，而沒有發生錯誤或資料遺失時，您可以使用縮小轉換。 例如，如果您 `String` 知道您知道包含 "True" 或 "False"，您可以使用 `CBool` 關鍵字將它轉換成 `Boolean` 。  
  
## <a name="exceptions-during-conversion"></a>轉換期間的例外狀況  

 因為擴輾轉換一律會成功，所以不會擲回例外狀況。 縮小轉換失敗時，最常擲回下列例外狀況：  
  
- <xref:System.InvalidCastException> -如果兩個類型之間沒有定義任何轉換  
  
- <xref:System.OverflowException> —只有在轉換的值對目標型別而言太大時，才)  (整數類型  
  
 如果類別或結構定義了 [CType](../../../language-reference/functions/ctype-function.md) 函式做為該類別或結構的轉換運算子，則 `CType` 可能會擲回它認為適當的任何例外狀況。 此外，這 `CType` 可能會呼叫 Visual Basic 函式或 .NET Framework 方法，進而擲回不同的例外狀況。  
  
## <a name="changes-during-reference-type-conversions"></a>參考型別轉換期間的變更  

 從 *參考型* 別進行轉換時，只會複製值的指標。 此值本身不會以任何方式複製或變更。 唯一可變更的內容是包含指標之變數的資料類型。 在下列範例中，資料類型會從衍生類別轉換成其基類，但兩個變數現在指向的物件也不會變更。  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](index.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [隱含和明確轉換](implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](conversions-between-strings-and-other-types.md)
- [如何：在 Visual Basic 中將物件轉換成其他類型](how-to-convert-an-object-to-another-type.md)
- [陣列轉換](array-conversions.md)
- [Data types (資料類型)](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
