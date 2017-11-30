---
title: "擴展和縮小轉換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf1f8d956935a9a363211abf94b4f1c2f538074
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>擴展和縮小轉換 (Visual Basic)
類型轉換的重要考量是轉換的結果是否目的地資料類型的範圍內。  
  
 A*擴展轉換*值變更為可允許任何的原始資料的可能值的資料類型。  擴展轉換，保留原始值，但可以變更它的表示。 如果您從整數類資料類型轉換，發生這種的情況`Decimal`，或從`Char`至`String`。  
  
 *「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。 例如，小數的值會四捨五入時將它轉換成整數類型，並轉換成數值類型`Boolean`降低為`True`或`False`。  
  
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
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|任何列舉型別 ([列舉](../../../../visual-basic/language-reference/statements/enum-statement.md))|其基礎的整數類資料類型和任何類型的基礎類型將擴展。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 陣列|`Char`陣列，`String`|  
|任何型別|[物件](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|任何衍生型別|任何基底的類型衍生的來源<sup>3</sup>。|  
|任何型別|它會實作任何介面。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何資料類型或物件類型。|  
  
 <sup>1</sup>根據定義，每個資料類型可擴展為本身。  
  
 <sup>2</sup>從不`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`至`Single`或`Double`可能會產生在遺失有效位數，但永遠不會在遺失的大小。 就這個意義而言它們不會造成資訊遺失。  
  
 <sup>3</sup>看起來令人意外從衍生型別轉換為其基底型別會擴展。 原因是衍生的類型包含基底型別的所有成員，因此它符合基底類型的執行個體。 相反的方向，基底型別不包含任何新的成員所衍生的型別定義。  
  
 擴展轉換，一定要成功執行階段，並永遠不會造成資料遺失。 您可以隱含地執行它們是否[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`On`或`Off`。  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 標準的縮小轉換包括下列各項：  
  
-   在上述的擴展轉換的反向資料表 （不同之處在於擴展至其本身的型別）  
  
-   轉換之間的任一方向[布林](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)和任何數值類型  
  
-   從任何數值類型轉換為任何列舉型別 (`Enum`)  
  
-   轉換之間的任一方向[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)和任何數值類型， `Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   從資料類型或物件型別轉換從它衍生的型別  
  
 縮小轉換執行不一定成功在執行階段，並可能會失敗或者造成資料遺失。 如果目的地資料類型無法接收要轉換的值，就會發生錯誤。 例如，數字轉換導致溢位。 編譯器不允許隱含地執行縮小轉換，除非[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`Off`。  
  
> [!NOTE]
>  縮小轉換錯誤的轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。 如需詳細資訊與範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>何時使用縮小轉換  
 當您知道來源值可以轉換成目的地資料類型，而不會錯誤或資料遺失時，您可以使用縮小轉換。 例如，如果您有`String`您知道包含"True"False"，您可以使用`CBool`關鍵字來將它轉換成`Boolean`。  
  
## <a name="exceptions-during-conversion"></a>轉換期間的例外狀況  
 因為永遠擴展轉換成功，它們不會擲回例外狀況。 縮小轉換，失敗時，通常會擲回下列例外狀況：  
  
-   <xref:System.InvalidCastException>— 如果兩個類型之間不定義任何轉換  
  
-   <xref:System.OverflowException>-（只有整數類型） 如果已轉換的值是目標類型而言太大  
  
 如果類別或結構定義[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)做為轉換運算子或從該類別或結構的`CType`可以擲回任何例外狀況，它認為適當的行動。 此外的`CType`可能呼叫[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]函式或[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]接著可能會擲回例外狀況的各種不同的方法。  
  
## <a name="changes-during-reference-type-conversions"></a>參考型別轉換期間的變更  
 從轉換*參考型別*複製只有指標值。 值本身尚未複製或以任何方式變更。 唯一可以變更會保留指標變數的資料型別。 在下列範例中，資料類型會從衍生類別轉換為其基底類別，但這兩個變數指向的物件不會變更。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [如何： 將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
