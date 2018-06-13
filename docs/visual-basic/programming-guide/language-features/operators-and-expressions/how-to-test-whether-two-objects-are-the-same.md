---
title: 如何：測試兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647601"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>如何：測試兩個物件是否相同 (Visual Basic)
如果您有兩個參考物件的變數，您可以使用`Is`或`IsNot`運算子，或兩者，以判斷它們是否參考相同的執行個體。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>若要測試這兩個物件是否相同  
  
-   使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)與兩個變數做為運算元。  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 您可能想要採取某些動作根據兩個物件是否參考相同的執行個體。 上述範例會比較控制項`c`針對表單上的現用控制項`f`。 如果沒有使用中的控制項，或如果沒有其中一個，但它不是相同的控制項執行個體`c`，然後在`If`陳述式失敗，且此程序傳回而不需進一步處理。  
  
 不論您是使用`Is`或`IsNot`是您的個人起見。 一個可能更方便閱讀比另一個則指定運算式中。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
