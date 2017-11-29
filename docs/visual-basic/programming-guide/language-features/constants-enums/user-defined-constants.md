---
title: "使用者定義常數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce839c3e843a52b31e40c13cb765f8eaf9959ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-constants-visual-basic"></a>使用者定義常數 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。 您可以使用常數所定義的控制項或元件，或建立您自己。 常數您自行建立會描述成*使用者定義*。  
  
 您可使用宣告常數`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告的常數類型。  
  
## <a name="const-statement-usage"></a>Const 陳述式使用方式  
 A`Const`陳述式可以代表數學或日期/時間數量：  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 它也可以定義`String`常數：  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 等號右邊的運算式 ( `=` ) 通常是數字或常值字串，但也可以是產生數字或字串 （雖然該運算式無法包含函式的呼叫） 的運算式。 您甚至可以定義常數，根據先前定義的常數：  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>使用者定義常數的範圍  
 A`Const`陳述式的範圍相當於在相同的位置所宣告的變數。 您可以下列方式指定領域：  
  
-   若要建立程序內只能存在一個常數，請將它宣告該程序內。  
  
-   若要建立所有的程序，在類別內，但不是屬於該模組外的任何程式碼可以使用的常數，請將它宣告類別的宣告區段中。  
  
-   若要建立一個常數，代表可用組件的所有成員，但不是屬於組件外部的用戶端，會將它宣告使用`Friend`類別的宣告區段中的關鍵字。  
  
-   若要建立可以在整個應用程式使用的常數，會將它宣告使用`Public`關鍵字宣告中的區段的類別。  
  
 如需詳細資訊，請參閱[如何： 宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免循環參考  
 因為可以根據其他常數定義常數，所以可能會不小心建立*循環*，或兩個或多個常數之間的循環參考。 當您有兩個或多個公用常數，其中每一個都以另一個，如下列範例所示定義時，就會發生循環：  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 如果發生循環，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會產生編譯器錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [常數和列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
