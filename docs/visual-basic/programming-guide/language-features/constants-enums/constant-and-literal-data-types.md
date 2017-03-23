---
title: "常數和常值資料類型 (Visual Basic) |Microsoft 文件"
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 22ad31415ab560b7fd0180a6dadd6d2dcd7ec77a
ms.lasthandoff: 03/13/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a>常數和常值資料類型 (Visual Basic)
常值是其本身，而不是變數的值或運算式，例如數字 3 或字串"Hello"的結果表示的值。 常數是有意義的名稱會採用取代常值，並維持相同的值在整個程式，而不是變數，其值可能會變更。  
  
 當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告的所有常數的資料型別。 在下列範例中，資料類型的`MyByte`明確宣告資料型別為`Byte`:  
  
 [!code-vb[VbVbalrConstants #&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。 編譯器會判斷運算式的型別常數的類型。 預設會將數字的整數常值轉換`Integer`資料型別。 預設資料類型為浮點數`Double`，和關鍵字`True`和`False`指定`Boolean`常數。  
  
## <a name="literals-and-type-coercion"></a>常值和強制型轉  
 在某些情況下，您可能想要的常值強制為特定的資料類型;例如，將特別大的整數常值指派給類型的變數時`Decimal`。 下列範例會產生錯誤︰  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 常值的表示方式會產生錯誤。 `Decimal`資料類型可以保留值，這種大小，但常值會隱含地表示為`Long`，哪些不可。  
  
 您可以強制轉型成特定的資料類型有兩種常值︰ 將型別字元附加到它，或將其放在封入字元。 型別字元或封入字元必須立即之前和/或遵循常值，沒有多餘的空格或任何種類的字元。  
  
 若要使先前的範例工作，您可以附加`D`輸入字元常值，使它表示成`Decimal`:  
  
 [!code-vb[VbVbalrConstants #&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 下列範例示範正確的型別字元和封入字元使用方式︰  
  
 [!code-vb[VbVbalrConstants #&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 下表顯示內含的字元和型別字元用於[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
|資料類型|封入字元|附加的型別字元|  
|---|---|---|  
|`Boolean`|(無)|(無)|  
|`Byte`|(無)|(無)|  
|`Char`|"|C|  
|`Date`|#|(無)|  
|`Decimal`|(無)|D 或 @|  
|`Double`|(無)|R 或 #|  
|`Integer`|(無)|I 或 %|  
|`Long`|(無)|L 或 i|  
|`Short`|(無)|S|  
|`Single`|(無)|F 或 ！|  
|`String`|"|(無)|  
  
## <a name="see-also"></a>另請參閱  
 [使用者定義常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [如何︰ 宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit 陳述式](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
