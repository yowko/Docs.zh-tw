---
title: 決策結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f8b653b941c5959036256cde097a41f8c6251c7a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601233"
---
# <a name="decision-structures-visual-basic"></a>決策結構 (Visual Basic)
Visual Basic 可讓您測試條件，並執行不同的作業，視該測試的結果而定。 您可以測試條件為 true 或 false，針對各種不同值的運算式，或當您執行一系列的陳述式時，產生的各種例外狀況。  
  
 下圖顯示測試條件為 true，並採用不同的動作，取決於它是否為 true 或 false 的決策結構。  
  
 ![如果流量圖表...Then...其他建構。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...其他建構  
 `If...Then...Else` 建構可讓您測試一或多個條件，並執行一或多個陳述式，根據每個條件。 您可以測試條件，並以下列方式來採取動作：  
  
- 如果條件為，執行一或多個陳述式 `True`  
  
- 如果條件為，執行一或多個陳述式 `False`  
  
- 執行某些陳述式，如果條件為`True`和其他人是否 `False`  
  
- 測試其他狀況，如果先前的條件 `False`  
  
 提供所有這些可能性的控制結構是[如果...Then...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。 如果您有一個測試和執行一個陳述式，您可以使用單行的版本。 如果您有一組更複雜的條件和動作，您可以使用多行版本。  
  
## <a name="selectcase-construction"></a>選取此項目...案例的建構  
 `Select...Case`建構可讓您評估運算式一次，並執行不同的陳述式，根據不同的可能值。 如需詳細資訊，請參閱[選取...Case 陳述式](../../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="trycatchfinally-construction"></a>再試...Catch...最後的建構  
 `Try...Catch...Finally` 建構可讓您執行一組保留控制項，如果陳述式的任何一個造成例外狀況環境下的陳述式。 您可以採取不同的例外狀況的不同動作。 您可以選擇性地指定前結束的整個執行的程式碼區塊`Try...Catch...Finally`建構，不論發生的動作。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  許多控制項結構，當您按一下關鍵字的所有關鍵字在結構中反白顯示。 比方說，當您按一下 `If`中`If...Then...Else`建構、 所有執行個體`If`， `Then`， `ElseIf`， `Else`，和`End If`建構中會反白顯示。 若要移到下一個或上一個反白顯示關鍵字，請按 CTRL + SHIFT + 向下鍵或 CTRL + SHIFT + 向上鍵。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [巢狀控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If 運算子](../../../../visual-basic/language-reference/operators/if-operator.md)
