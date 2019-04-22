---
title: 使用者定義常數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813908"
---
# <a name="user-defined-constants-visual-basic"></a>使用者定義常數 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。 您可以使用常數所定義的控制項或元件使用，或建立您自己。 您可以建立自己的常數會被稱為*使用者定義*。  
  
 您可使用宣告常數`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告常數的類型。  
  
## <a name="const-statement-usage"></a>Const 陳述式使用方式  
 A`Const`陳述式可以代表數學或日期/時間數量：  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 它也可以定義`String`常數：  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 等號右邊的運算式 ( `=` ) 通常是數字或常值字串，但它也可以是運算式所產生的數字或字串中 （雖然該運算式無法包含函式的呼叫）。 您甚至可以定義常數，根據先前定義的常數：  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>使用者定義的常數的範圍  
 A`Const`陳述式的範圍是在相同的位置所宣告的變數相同。 您可以使用下列任一方式來指定範圍：  
  
-   若要建立程序內只能存在一個常數，請將它宣告內該程序。  
  
-   若要建立所有的程序，在類別中，但不是屬於該模組外的任何程式碼可以使用的常數，請將它宣告之類別的宣告區段中。  
  
-   若要建立外部的用戶端組件的所有成員的組件，但不是使用的常數，宣告使用`Friend`類別的 「 宣告 」 區段中的關鍵字。  
  
-   若要建立整個應用程式，您可以使用的常數，宣告使用`Public`關鍵字在宣告中的區段的類別。  
  
 如需詳細資訊，請參閱[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免循環參考  
 根據其他常數，就可以定義常數，因為很可能會不小心建立*循環*，或兩個或多個常數之間的循環參考。 當您有兩個或多個公用常數，每一個都以另一個，如下列範例所示定義時，就會發生循環：  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 如果發生循環，Visual Basic 會產生編譯器錯誤。  
  
## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)
- [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常數和列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
