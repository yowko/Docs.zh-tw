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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403417"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>如何：測試兩個物件是否相同 (Visual Basic)
如果您有兩個參考物件的變數，您可以使用 `Is` or `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>測試兩個物件是否相同  
  
- 使用[Is 運算子](../../../language-reference/operators/is-operator.md)或[IsNot 運算子](../../../language-reference/operators/isnot-operator.md)，並將兩個變數當做運算元。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 根據兩個物件是否參考相同的實例而定，您可能會想要採取特定動作。 上述範例會 `c` 針對表單上的現用控制項比較控制項 `f` 。 如果沒有作用中的控制項，或有一個，但它與不是相同的控制項實例，則 `c` `If` 語句會失敗，而程式會傳回而不會進一步處理。  
  
 無論您使用 `Is` 或， `IsNot` 都是您個人的便利性。 在指定的運算式中，可能比另一個更容易閱讀。  
  
## <a name="see-also"></a>另請參閱

- [Comparison Operators in Visual Basic](comparison-operators.md)
