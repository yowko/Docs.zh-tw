---
title: 邏輯運算子和位元運算子
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 55a246c0d56501a409ebbc7d0d0aa39ae9fa1770
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343599"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic 中的邏輯運算子和位元運算子
邏輯運算子會比較 `Boolean` 運算式，並傳回 `Boolean` 的結果。 `And`、`Or`、`AndAlso`、`OrElse`和 `Xor` 運算子都是*二進位*，因為它們接受兩個運算元，而 `Not` 運算子是*一元*，因為它採用單一運算元。 其中有些運算子也可以在整數值上執行位邏輯運算。  
  
## <a name="unary-logical-operator"></a>一元邏輯運算子  
 [Not 運算子會](../../../../visual-basic/language-reference/operators/not-operator.md)在 `Boolean` 運算式上執行邏輯*否定*。 它會產生與其運算元相反的邏輯。 如果運算式評估為 `True`，則 `Not` 會傳回 `False`;如果運算式評估為 `False`，則 `Not` 會傳回 `True`。 說明如下例。  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>二元邏輯運算子  
 [And 運算子](../../../../visual-basic/language-reference/operators/and-operator.md)會在兩個 `Boolean` 運算式上執行邏輯*結合*。 如果兩個運算式都評估為 `True`，則 `And` 會傳回 `True`。 如果至少有一個運算式評估為 `False`，則 `And` 會傳回 `False`。  
  
 [Or 運算子](../../../../visual-basic/language-reference/operators/or-operator.md)會在兩個 `Boolean` 運算式上*執行邏輯分離*或*包含*。 如果任一運算式評估為 `True`，或兩者都評估為 `True`，則 `Or` 會傳回 `True`。 如果兩個運算式都不是評估為 `True`，`Or` 會傳回 `False`。  
  
 [Xor 運算子](../../../../visual-basic/language-reference/operators/xor-operator.md)會在兩個 `Boolean` 運算式上執行邏輯*排除*。 如果只有一個運算式評估為 `True`，但不是兩者都計算為，`Xor` 會傳回 `True`。 如果兩個運算式都評估為 `True` 或兩者都評估為 `False`，`Xor` 會傳回 `False`。  
  
 下列範例說明 `And`、`Or`和 `Xor` 運算子。  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>最小運算邏輯作業  
 [AndAlso 運算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)與 `And` 運算子非常類似，因為它也會在兩個 `Boolean` 運算式上執行邏輯結合。 兩者的主要差異在於，`AndAlso` 展現最少*運算的行為*。 如果 `AndAlso` 運算式中的第一個運算式評估為 `False`，則不會評估第二個運算式，因為它無法改變最終結果，而且 `AndAlso` 會傳回 `False`。  
  
 同樣地， [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)會在兩個 `Boolean` 運算式上執行最少運算邏輯分離。 如果 `OrElse` 運算式中的第一個運算式評估為 `True`，則不會評估第二個運算式，因為它無法改變最終結果，而且 `OrElse` 會傳回 `True`。  
  
### <a name="short-circuiting-trade-offs"></a>短路取捨  
 「最少運算」可以藉由不評估無法改變邏輯作業結果的運算式來改善效能。 不過，如果該運算式執行其他動作，則最少運算會略過這些動作。 例如，如果運算式包含對 `Function` 程式的呼叫，則不會在縮短運算式時呼叫該程式，而且包含在 `Function` 中的任何其他程式碼都不會執行。 因此，函式可能只會偶爾執行，而且可能無法正確地進行測試。 或程式邏輯可能相依于 `Function`中的程式碼。  
  
 下列範例說明 `And`、`Or`和其最小運算對應項之間的差異。  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 在上述範例中，請注意，`checkIfValid()` 中的某些重要程式碼不會在呼叫縮短時執行。 即使 `12 > 45` 傳回 `False`，第一個 `If` 語句還是會呼叫 `checkIfValid()`，因為 `And` 不是最短的運算。 第二個 `If` 語句不會呼叫 `checkIfValid()`，因為當 `12 > 45` 傳回 `False`時，`AndAlso` 會將第二個運算式短路。 第三個 `If` 語句會呼叫 `checkIfValid()`，即使 `12 < 45` 會傳回 `True`，因為 `Or` 不會執行最少運算。 第四個 `If` 語句不會呼叫 `checkIfValid()`，因為當 `12 < 45` 傳回 `True`時，`OrElse` 會將第二個運算式短路。  
  
## <a name="bitwise-operations"></a>位運算  
 位運算會以二進位（基底2）形式評估兩個整數值。 它們會比較對應位置的位，然後根據比較來指派值。 下列範例說明 `And` 運算子。  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 上述範例會將 `x` 的值設定為1。 這會因下列原因而發生：  
  
- 這些值會被視為二進位：  
  
     3（二進位格式 = 011）  
  
     5二進位格式 = 101  
  
- `And` 運算子會比較二進位標記法，一次一個二進位位置（位）。 如果指定位置的兩個位都是1，則會將1放在結果中的該位置。 如果任一個位為0，則會將0放在結果中的該位置。 在上述範例中，這種方式如下所示：  
  
     011（二進位格式為3）  
  
     101（二進位格式的5）  
  
     001（以二進位形式呈現的結果）  
  
- 結果會被視為 decimal。 001值是1的二進位表示，因此 `x` = 1。  
  
 位 `Or` 運算相似，不同之處在于如果其中一個或兩個比較的位為1，則會將1指派給結果位。 如果只有一個比較的位（不是兩個）是1，`Xor` 會將1指派給結果位。 `Not` 會採用單一運算元並反轉所有位（包括符號位），並將該值指派給結果。 這表示對於帶正負號的正數，`Not` 一律會傳回負值，而對於負數，`Not` 一律會傳回正值或零值。  
  
 `AndAlso` 和 `OrElse` 運算子不支援位運算。  
  
> [!NOTE]
> 位運算只能在整數類型上執行。 必須先將浮點值轉換成整數類型，才能繼續進行位運算。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子（Visual Basic）](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
