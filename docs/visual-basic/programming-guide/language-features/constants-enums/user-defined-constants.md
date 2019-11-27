---
title: 使用者定義的常數
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354012"
---
# <a name="user-defined-constants-visual-basic"></a>使用者定義常數 (Visual Basic)
常數是有意義的名稱，用來取代不會變更的數位或字串。 如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。 您可以使用您所使用之控制項或元件所定義的常數，也可以自行建立。 您自行建立的常數會描述為*使用者定義*。  
  
 您可以使用 `Const` 語句來宣告常數，方法與建立變數名稱的方針相同。 如果 `On``Option Strict`，則必須明確宣告常數類型。  
  
## <a name="const-statement-usage"></a>Const 語句使用方式  
 `Const` 語句可以代表數學或日期/時間數量：  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 它也可以定義 `String` 常數：  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 等號（`=`）右邊的運算式通常是數位或常值字串，但也可以是產生數位或字串的運算式（雖然該運算式不能包含函數的呼叫）。 您甚至可以根據先前定義的常數來定義常數：  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>使用者定義常數的範圍  
 `Const` 語句的範圍與在相同位置中宣告的變數相同。 您可以用下列任一種方式指定範圍：  
  
- 若要建立只存在於程式中的常數，請在該程式內宣告它。  
  
- 若要建立一個常數供類別內的所有程式使用，但不能用於該模組外的任何程式碼，請在類別的宣告區段中宣告它。  
  
- 若要建立可用於元件的所有成員，但不是元件外部用戶端的常數，請使用類別的宣告區段中的 `Friend` 關鍵字來宣告它。  
  
- 若要在整個應用程式中建立常數，請在類別的宣告區段中使用 `Public` 關鍵字來宣告。  
  
 如需詳細資訊，請參閱 how [to： Declare A 常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免迴圈參考  
 因為常數可以根據其他常數來定義，所以在兩個或多個常數之間，可能會不小心建立*迴圈*或迴圈參考。 當您有兩個或多個公用常數時，就會發生迴圈，其中每一個都是以另一個的角度定義，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 如果發生迴圈，Visual Basic 會產生編譯器錯誤。  
  
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
