---
title: HOW TO：標籤陳述式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 00a08bd3bd1f866cec883b6591b03ebd9d858b90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552253"
---
# <a name="how-to-label-statements-visual-basic"></a>HOW TO：標籤陳述式 (Visual Basic)
陳述式區塊所組成的以分號分隔的程式碼行。 據說是幾行程式碼，加上識別的字串或整數*標示為*。 陳述式標籤用來標記行程式碼來加以識別，以便使用陳述式這類`On Error Goto`。  
  
 標籤可能是其中一個有效的 Visual Basic 識別項，例如識別程式設計項目，或整數常值。 標籤必須出現在原始程式碼行開頭，而且必須後面接著冒號，不論是否它後面的陳述式同一行上。  
  
 編譯器會藉由檢查一行的開頭是否符合任何已定義的識別項識別標籤。 如果不存在，編譯器會假設它是一個標籤。  
  
 標籤會有自己的宣告空間，而且不會干擾其他識別項。 標籤的範圍是方法的主體。 標籤宣告的任何模稜兩可的情況下，會優先。  
  
> [!NOTE]
>  只能在方法內的可執行陳述式上可用的標籤。  
  
### <a name="to-label-a-line-of-code"></a>若要標記一行程式碼  
  
-   將後面接著冒號，在原始程式碼行開頭的識別碼。  
  
     例如，下列程式碼會加上`Jump`和`120`分別：  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
