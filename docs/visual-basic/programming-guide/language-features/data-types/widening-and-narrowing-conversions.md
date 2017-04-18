---
title: "擴展和縮小轉換 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- widening conversions
- narrowing conversions
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions, exceptions during conversion
- type conversion, exceptions during conversion
- conversions, data type
- conversions, narrowing
- type conversion, narrowing
- data type conversion, widening
- data type conversion, narrowing
- changing data types
- type conversion, widening
- data type conversion, exceptions during conversion
- conversions, widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 88c5db6e7e82a88ae8015b581e5a795ec389d003
ms.lasthandoff: 03/13/2017

---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>擴展和縮小轉換 (Visual Basic)
型別轉換的重要考量是目的地資料類型的範圍內是否已轉換的結果。  
  
 A*擴展轉換*值變更為資料型別，它可以提供原始資料的任何可能的值。  擴展轉換會保留原始值，但是可以變更它的表示。 如果您從整數類資料類型轉換會發生此`Decimal`，或從`Char`到`String`。  
  
 *「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。 例如，分數的值會捨入轉換成整數型別，而要轉換成數值類型則`Boolean`降低為`True`或`False`。  
  
## <a name="widening-conversions"></a>擴展轉換  
 下表顯示標準的擴展轉換。  
  
|資料類型|擴展資料型別為<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[簡短](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[整數](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[長](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|任何列舉型別 ([列舉](../../../../visual-basic/language-reference/statements/enum-statement.md))|其基礎整數型別和任何類型的擴展基礎的型別。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 陣列|`Char`陣列，`String`|  
|任何型別|[物件](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|任何衍生型別|任何基底型別衍生自此<sup>3</sup>。|  
|任何型別|它會實作任何介面。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何資料型別或物件型別。|  
  
 <sup>1</sup>根據定義，擴展至本身的資料型別。  
  
 <sup>2</sup>從不`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`至`Single`或`Double`可能會導致失去精確度，但永遠不會遺失的大小。 在這種情況下它們不會造成資訊遺失。  
  
 <sup>3</sup>一定很驚訝從衍生型別轉換為其基底型別會擴展。 原因是衍生型別包含基底型別的所有成員，因此它可視為基底型別的執行個體。 換言之，基底型別不包含任何衍生型別所定義的新成員。  
  
 擴展轉換永遠成功執行階段，而且永遠不會造成資料遺失。 您可以隱含地執行它們是否[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`On`或`Off`。  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 標準的縮小轉換包括︰  
  
-   在上述的擴展轉換的反向資料表 （不包括任何擴展至本身的型別）  
  
-   之間轉換[布林](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)及任何數字類型  
  
-   從任何數字類型轉換為任何列舉型別 (`Enum`)  
  
-   之間轉換[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)及任何數字類型， `Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   從資料型別或物件型別轉換從它衍生的型別  
  
 縮小轉換執行不一定成功在執行階段，並可能會失敗或者造成資料遺失。 如果目的地資料類型無法接收轉換的值，就會發生錯誤。 例如，數字轉換導致溢位。 編譯器不允許隱含地執行縮小轉換，除非[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`Off`。  
  
> [!NOTE]
>  轉換中的項目會隱藏縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。 如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>何時使用縮小轉換  
 當您知道來源值可以轉換為目的資料型別，而不會錯誤或資料遺失時，您可以使用縮小轉換。 例如，如果您有`String`，您知道包含"True"False"，您可以使用`CBool`關鍵字，將它轉換為`Boolean`。  
  
## <a name="exceptions-during-conversion"></a>在轉換期間的例外狀況  
 因為擴展轉換一定成功，它們不會擲回例外狀況。 縮小轉換，失敗時，通常會擲回下列例外狀況︰  
  
-   <xref:System.InvalidCastException>— 如果兩個類型之間有不定義任何轉換</xref:System.InvalidCastException>  
  
-   <xref:System.OverflowException>-（只有整數類型） 如果轉換的值是目標類型而言太大</xref:System.OverflowException>  
  
 如果類別或結構定義[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)做為該類別或結構，來回轉換運算子，`CType`可以擲回任何例外狀況，其認為適當的行動。 此外，，`CType`可能會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式或[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]接著可能會擲回例外狀況的各種不同的方法。  
  
## <a name="changes-during-reference-type-conversions"></a>參考型別轉換期間的變更  
 從轉換*參考型別*複製只有指標值。 值本身是既不會複製或以任何方式變更。 唯一可以變更是存放指標變數的資料型別。 在下列範例中，資料型別會從衍生類別轉換為其基底類別，但是這兩個變數現在指向的物件不變。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [字串和其他類型之間轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [如何︰ 將物件轉換成 Visual Basic 中的另一個型別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
