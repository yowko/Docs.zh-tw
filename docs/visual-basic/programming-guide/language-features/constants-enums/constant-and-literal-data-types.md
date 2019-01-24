---
title: 常數和常值資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: d85ff343587e8689a4859a09c8dc80932374a82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498644"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>常數和常值資料類型 (Visual Basic)
常值是表示為本身，而不是為變數的值或運算式，例如數字 3 或字串"Hello"的結果值。 常數是有意義的名稱，會取代常值，並保留在整個程式，而不是變數，可能會變更其值，這個相同的值。  
  
 當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`並[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告的所有常數，與資料型別。 在下列範例中，資料類型`MyByte`明確宣告資料類型為`Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 當`Option Infer`是`On`或是`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。 編譯器會判斷運算式的類型從常數的類型。 預設會將轉換的數字的整數常值`Integer`資料型別。 預設資料類型是浮點數`Double`，和關鍵字`True`並`False`指定`Boolean`常數。  
  
## <a name="literals-and-type-coercion"></a>常值和類型強制型轉  
 在某些情況下，您可能想要的常值強制為特定的資料類型;例如，當將特別大的整數常值指派給類型的變數`Decimal`。 下列範例會產生錯誤：  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 從常值的表示法會產生錯誤。 `Decimal`資料類型可以保留值，這種大小，但常值隱含地表示為`Long`，哪些不可。  
  
 您可以將兩種方式為特定的資料類型的常值的強制轉型： 將型別字元附加到它，或將其放在封入字元。 類型字元或封入字元必須立即在之前和/或遵循常值，不含空格或任何種類的字元。  
  
 若要讓上述範例運作，您可以將附加`D`型別字元常值，這會導致它表示成`Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 下列範例會示範正確的使用方式的型別字元及封入字元：  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 下表顯示封入字元和 Visual Basic 提供的類型字元。  
  
|資料類型|封入字元|附加的類型字元|  
|---|---|---|  
|`Boolean`|(無)|(無)|  
|`Byte`|(無)|(無)|  
|`Char`|"|C|  
|`Date`|#|(無)|  
|`Decimal`|(無)|D 或使用 @|  
|`Double`|(無)|R 或 #|  
|`Integer`|(無)|I 或 %|  
|`Long`|(無)|L 或 （& s)|  
|`Short`|(無)|S|  
|`Single`|(無)|F 或 ！|  
|`String`|"|(無)|  
  
## <a name="see-also"></a>另請參閱
- [使用者定義的常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit 陳述式](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
