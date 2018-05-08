---
title: Visual Basic 中的邏輯運算子和位元運算子
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
ms.openlocfilehash: 371d28629b39fb2808ca018ea69da3306a31f50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic 中的邏輯運算子和位元運算子
邏輯運算子會比較`Boolean`運算式並傳回`Boolean`結果。 `And`， `Or`， `AndAlso`， `OrElse`，和`Xor`運算子是*二進位*由於它們會採用兩個運算元，而`Not`運算子是*一元*因為它會採用單一運算元。 其中某些運算子也可以執行位元整數值上的邏輯作業。  
  
## <a name="unary-logical-operator"></a>一元邏輯運算子  
 [Not 運算子](../../../../visual-basic/language-reference/operators/not-operator.md)執行邏輯*否定*上`Boolean`運算式。 它會產生其運算元的相反邏輯。 如果運算式評估為`True`，然後`Not`傳回`False`; 如果運算式評估為`False`，然後`Not`傳回`True`。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>二元邏輯運算子  
 [與運算子](../../../../visual-basic/language-reference/operators/and-operator.md)執行邏輯*搭配*在兩個`Boolean`運算式。 如果這兩個運算式評估為`True`，然後`And`傳回`True`。 如果至少一個運算式評估為`False`，然後`And`傳回`False`。  
  
 [或運算子](../../../../visual-basic/language-reference/operators/or-operator.md)執行邏輯*分離*或*包含*在兩個`Boolean`運算式。 如果任一個運算式評估為`True`，或兩者都評估為`True`，然後`Or`傳回`True`。 如果兩個運算式判斷值為`True`，`Or`傳回`False`。  
  
 [Xor 運算子](../../../../visual-basic/language-reference/operators/xor-operator.md)執行邏輯*排除*在兩個`Boolean`運算式。 如果只有一個運算式評估為`True`，但非兩者`Xor`傳回`True`。 如果這兩個運算式評估為`True`或兩者都評估為`False`，`Xor`傳回`False`。  
  
 下列範例說明`And`， `Or`，和`Xor`運算子。  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>最少運算邏輯作業  
 [AndAlso 運算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)非常類似於`And`運算子，它也會在兩個執行邏輯結合`Boolean`運算式。 兩者之間的主要差異在於`AndAlso`表現*最少運算*行為。 如果中的第一個運算式`AndAlso`運算式評估為`False`，則它無法改變的最終結果，因為不會評估第二個運算式和`AndAlso`傳回`False`。  
  
 同樣地， [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)執行最少運算邏輯分離，在兩個`Boolean`運算式。 如果中的第一個運算式`OrElse`運算式評估為`True`，則它無法改變的最終結果，因為不會評估第二個運算式和`OrElse`傳回`True`。  
  
### <a name="short-circuiting-trade-offs"></a>最少運算的取捨  
 最少運算可以改善效能，不會評估運算式，無法變更邏輯作業的結果。 不過，如果該運算式會執行其他動作，最少運算會略過這些動作。 例如，如果運算式包括呼叫`Function`程序中，如果運算式是最少運算，和任何額外的程式碼包含在程序不會呼叫`Function`不會執行。 因此，函式可能會偶爾才會執行，而且可能不正確地測試。 程式邏輯可能會相依於中的程式碼或`Function`。  
  
 下列範例說明之間的差異`And`， `Or`，及其最少運算的對應。  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 在上述範例中，請注意，某些重要的程式碼內`checkIfValid()`呼叫最少運算時不會執行。 第一個`If`陳述式會呼叫`checkIfValid()`即使`12 > 45`傳回`False`，因為`And`不最短路徑。 第二個`If`陳述式不會呼叫`checkIfValid()`，因為當`12 > 45`傳回`False`， `AndAlso` short-circuits 第二個運算式。 第三個`If`陳述式會呼叫`checkIfValid()`即使`12 < 45`傳回`True`，因為`Or`不最短路徑。 第四個`If`陳述式不會呼叫`checkIfValid()`，因為當`12 < 45`傳回`True`， `OrElse` short-circuits 第二個運算式。  
  
## <a name="bitwise-operations"></a>位元運算  
 位元運算的評估結果 (基底 2) 的二進位格式的兩個整數值。 這些比較對應位置的位元，並接著指派根據比較結果的值。 下列範例說明`And`運算子。  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 上述範例中設定的值`x`設為 1。 發生這種情況，原因如下：  
  
-   值會被視為二進位：  
  
     以二進位形式的 3 = 011  
  
     以二進位形式的 5 = 101  
  
-   `And`運算子比較的二進位表示法，一次一個二進位位置 （位元）。 如果指定的位置兩個位元都是 1，1 會在結果中的那個位置中。 如果其中一個位元為 0，0 會在結果中的那個位置中。 在上述範例中可以這麼做，如下所示：  
  
     011 (3 二進位格式)  
  
     101 (5 二進位格式)  
  
     001 （結果，以二進位格式）  
  
-   結果會被視為十進位。 001 的值是 1 的二進位表示法因此`x`= 1。  
  
 位元`Or`作業很類似，不同之處在於如果一個或兩個比較的位元為 1 1 指派給結果位元。 `Xor` 如果只有其中一個比較 （非兩者） 位元為 1，將 1 指派的結果位元。 `Not` 使用單一運算元反轉所有位元，包括正負號位元，並將該值指派給結果。 這表示針對簽署正數，`Not`一律會傳回一個負數值，並為負數，`Not`一律會傳回正或零值。  
  
 `AndAlso`和`OrElse`運算子不支援位元運算。  
  
> [!NOTE]
>  只有整數類資料型別，可以執行位元運算。 浮點值必須轉換成整數類資料類型，然後才可以繼續執行位元運算。  
  
## <a name="see-also"></a>另請參閱  
 [邏輯/位元運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
