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
ms.openlocfilehash: d29d1b0026b3f62d47859cd5b4b7a601532e27b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071686"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>如何：測試兩個物件是否相同 (Visual Basic)

如果您有兩個參考物件的變數，您可以使用 `Is` or `IsNot` 運算子（或兩者）來判斷它們是否參考相同的實例。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>測試兩個物件是否相同  
  
- 使用 as [運算子](../../../language-reference/operators/is-operator.md) 或 [IsNot 運算子](../../../language-reference/operators/isnot-operator.md) ，並將兩個變數做為運算元。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 您可能會想要根據兩個物件是否參考相同的實例，採取特定動作。 上述範例會將控制項 `c` 與表單上的作用中控制項進行比較 `f` 。 如果沒有作用中的控制項，或者有一個控制項不是相同的控制項實例 `c` ，則 `If` 語句會失敗，而且程式會傳回而不會進一步處理。  
  
 無論您 `Is` 是使用或， `IsNot` 都能為您提供個人的便利性。 在給定的運算式中，可能比另一個更容易讀取。  
  
## <a name="see-also"></a>另請參閱

- [Comparison Operators in Visual Basic](comparison-operators.md)
