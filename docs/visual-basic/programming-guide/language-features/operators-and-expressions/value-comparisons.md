---
title: 數值比較
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403391"
---
# <a name="value-comparisons-visual-basic"></a>數值比較 (Visual Basic)
比較運算子可以用來建立比較數值變數值的運算式。 這些運算式會根據 `Boolean` 比較是否為 true 或 false 傳回值。 這類運算式的範例如下所示。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 第一個運算式會評估為 `True` ，因為45大於26。 第二個範例會評估為 `False` ，因為26不大於45。  
  
 您也可以用這種方式來比較數值運算式。 您比較的運算式本身可以是複雜的運算式，如下列範例所示。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 前面的複雜運算式包含常值、變數和函式呼叫。 比較運算子兩邊的運算式會進行評估，然後使用比較運算子來比較產生的值 `>=` 。 如果左邊的運算式值大於或等於右邊運算式的值，則整個運算式會評估為， `True` 否則會評估為，否則為 `False` 。  
  
 比較值的運算式最常用於結構中 `If...Then` ，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`正負號是比較運算子，也是指派運算子。 做為比較運算子使用時，它會評估左邊的值是否等於右邊的值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 您也可以在需要值的任何位置使用比較運算式 `Boolean` ，例如 `If` ，在、 `While` 、或語句中，或在 `Loop` `ElseIf` 指派或傳遞值給 `Boolean` 變數時。 在下列範例中，比較運算式所傳回的值會指派給 `Boolean` 變數。  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>另請參閱

- [布林運算式](boolean-expressions.md)
- [運算子和運算式](index.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [如何：計算數值](how-to-calculate-numeric-values.md)
- [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)
