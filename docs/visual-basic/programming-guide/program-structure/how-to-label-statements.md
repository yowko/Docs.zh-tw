---
title: "如何：標記陳述式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a>如何：標記陳述式 (Visual Basic)
陳述式區塊是由以冒號分隔的程式碼行所組成。 行程式碼前面有識別的字串或整數都稱為*標示為*。 陳述式標籤用來標記資料行的程式碼，以找出它使用陳述式例如`On Error Goto`。  
  
 標籤可能是其中一個有效的 Visual Basic 識別項，例如識別程式設計項目，或整數常值。 標籤必須出現在原始程式碼行開頭，而且必須後面接著冒號，不論是否接下來還陳述式同一行上。  
  
 編譯器會辨識標籤藉由檢查一行的開頭是否符合任何已定義的識別項。 如果不存在，編譯器會假設它是標籤。  
  
 標籤會有自己的宣告空間，並不會干擾其他識別項。 標籤的範圍是方法的主體。 標記宣告會優先使用在任何模稜兩可的情況下。  
  
> [!NOTE]
>  只有在方法內的可執行陳述式上可用的標籤。  
  
### <a name="to-label-a-line-of-code"></a>若要標記的一行程式碼  
  
-   將識別項，後面接著冒號，在原始程式碼行的開頭。  
  
     例如，下列程式碼則標示為`Jump`和`120`分別：  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
