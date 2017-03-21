---
title: "使用者定義常數 (Visual Basic) |Microsoft 文件"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
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
ms.openlocfilehash: e5942d8663a8866b2f9794a86756f2bf25660ba5
ms.lasthandoff: 03/13/2017

---
# <a name="user-defined-constants-visual-basic"></a>使用者定義常數 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 常數用來儲存，正如其名，保持不變的應用程式執行過程中的值。 您可以使用常數所定義的控制項或元件，或建立您自己。 您建立自己的常數之所以被形容為*使用者定義*。  
  
 您可使用宣告常數`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告常數的類型。  
  
## <a name="const-statement-usage"></a>Const 陳述式的使用方式  
 A`Const`陳述式可以代表數學或日期/時間數量︰  
  
 [!code-vb[VbEnumsTask #&10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 它也可以定義`String`常數︰  
  
 [!code-vb[VbEnumsTask #&13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 等號右邊的運算式 ( `=` ) 通常是一個數字或常值字串，但也可以是 （雖然運算式無法包含函式呼叫） 會導致數字或字串的運算式。 您甚至可以定義常數，依據先前定義的常數︰  
  
 [!code-vb[VbEnumsTask #&15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>使用者定義常數的範圍  
 A`Const`陳述式的範圍是在相同的位置所宣告的變數相同。 您可以下列方式指定範圍︰  
  
-   若要建立程序中只存在一個常數，請在該程序內宣告。  
  
-   若要建立所有的程序，在類別中，但不是屬於該模組之外的任何程式碼可以使用的常數，請在類別宣告區段中宣告。  
  
-   若要建立外部用戶端組件的所有成員的組件，但不是使用的常數，宣告使用`Friend`類別的宣告區段中的關鍵字。  
  
-   若要建立整個應用程式可以使用的常數，宣告使用`Public`關鍵字的宣告區段的類別。  
  
 如需詳細資訊，請參閱[如何︰ 宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免循環參考  
 因為可以根據其他常數定義常數，所以有可能會不小心建立*循環*，或兩個或多個常數之間的循環參考。 當您有兩個或多個公用常數，每一個都根據另一個，如下列範例所示定義時，就會發生循環︰  
  
 [!code-vb[VbEnumsTask #&16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask #&17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 如果發生循環，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會產生編譯器錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [常數和列舉型別](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
