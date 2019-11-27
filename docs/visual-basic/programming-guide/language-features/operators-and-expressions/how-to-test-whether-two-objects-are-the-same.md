---
title: 如何：測試兩個物件是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343624"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>如何：測試兩個物件是否相同 (Visual Basic)
如果您有兩個參考物件的變數，您可以使用 `Is` 或 `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>測試兩個物件是否相同  
  
- 使用[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)或[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)，並將兩個變數當做運算元。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 根據兩個物件是否參考相同的實例而定，您可能會想要採取特定動作。 上述範例會針對表單 `f`上的現用控制項比較控制項 `c`。 如果沒有作用中的控制項，或有一個，但它與 `c`的控制項實例不同，則 `If` 語句會失敗，而程式會傳回而不會進行進一步的處理。  
  
 無論您是使用 `Is` 或 `IsNot`，都是您個人的便利性。 在指定的運算式中，可能比另一個更容易閱讀。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
