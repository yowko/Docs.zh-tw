---
title: HOW TO：測試兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: dbb268175d197e7b931af45a98f3a273c593e5a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819105"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>HOW TO：測試兩個物件是否相同 (Visual Basic)
如果您有兩個參考物件的變數，您可以使用`Is`或`IsNot`運算子，或兩者，以判斷它們是否參考相同的執行個體。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>若要測試兩個物件是否相同  
  
-   使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)搭配兩個變數，做為運算元。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 您可以採取特定動作取決於兩個物件是否參考相同的執行個體。 上述範例會比較控制項`c`針對表單上的現用控制項`f`。 如果沒有任何作用中的控制項，或如果有一個，但它不是相同的控制項執行個體`c`，則`If`陳述式失敗，且程序傳回不會進一步處理。  
  
 您是否使用`Is`或`IsNot`是您的個人比較方便。 一個可能比其他指定的運算式中讀取的工作變得更容易。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
