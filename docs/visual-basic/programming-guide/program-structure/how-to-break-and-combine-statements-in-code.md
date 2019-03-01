---
title: HOW TO：中斷和合併陳述式中的程式碼 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: a43d09be53eb5a04d154e482f9388e2ca480118a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967174"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>HOW TO：中斷和合併陳述式中的程式碼 (Visual Basic)
當撰寫程式碼，您有時可能會建立冗長的陳述式也許水平捲軸在程式碼編輯器。 雖然這不會影響的方式執行程式碼，它很難對您或其他人讀取的程式碼，此監視器上顯示的方式。 在此情況下，您應該考慮單一長的陳述式分成數行。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>若要在單一陳述式分成多行  
  
-   使用行接續字元是底線 (`_`)，您想要中斷的列之處。 底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 (歸位字元)。  
  
    > [!NOTE]
    >  在某些情況下，如果您省略行接續字元中，Visual Basic 編譯器會隱含地繼續陳述式在下一行程式碼。 可以略過行接續字元的語法項目清單，請參閱 「 隱含行接續符號 」，在[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
     在下列範例中，陳述式會分成四行程式碼，以終止所有的行接續字元，但最後一行。  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     使用此順序可讓您的程式碼更方便閱讀，列印線上和時。  
  
     行接續字元必須是該行的最後一個字元。 您不可以跟隨它與其他任何位於同一行上。  
  
     對於您可以在其中使用行接續字元中，有部分限制例如，您無法使用它的引數名稱的中間。 您可能會中斷以行接續字元的引數清單，但個別的名稱，引數必須保持不變。  
  
     您無法繼續註解使用行接續字元。 編譯器不會檢查特殊意義的註解中的字元。 多行註解中，重複的註解符號 (`'`) 在每一行。  
  
 雖然每個陳述式置於不同行的建議的方法，Visual Basic 也可讓您將多個陳述式放在同一行。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>若要將多個陳述式放在同一行  
  
-   將陳述式以冒號分隔 (`:`)，如下列範例所示。  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>另請參閱
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
