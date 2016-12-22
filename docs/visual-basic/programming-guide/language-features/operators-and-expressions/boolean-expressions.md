---
title: "Boolean Expressions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "expressions [Visual Basic], Boolean"
  - "expression evaluation, Boolean expressions"
  - "operators [Visual Basic], short-circuiting"
  - "Visual Basic code, operators"
  - "short-circuit evaluation"
  - "logical operators, short-circuiting"
  - "operators [Visual Basic], Boolean"
  - "Visual Basic code, expressions"
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Boolean Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

「*布林運算式*」\(Boolean Expression\) 此運算式評估得出的值為[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)：`True` 或 `False`。  `Boolean` 運算式可以採用數種形式。  最簡單的形式是直接比較 `Boolean` 變數值與 `Boolean` 常值 \(Literal\)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## \= 運算子的兩種意義  
 請注意，指派陳述式 \(Assignment Statement\) `newCustomer = True` 看起來與上述範例中的運算式相同，但是它會執行不同的函式且使用方式不同。  在上述範例中，運算式 `newCustomer = True` 代表布林值，而且 `=` 符號會解譯為比較運算子。  在獨立 \(Stand\-Alone\) 陳述式中，`=` 符號會解譯為指派運算子，並且將右邊的值指派給左邊變數。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 如需詳細資訊，請參閱[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)和[Statements](../../../../visual-basic/language-reference/statements/index.md)。  
  
## 比較運算子  
 比較運算子 \(如 `=`、`<`、`>`、`<>`、`<=` 和 `>=`\) 會產生布林運算式，其做法便是比較左側的運算式與運算子右側的運算式，並將結果評估為 `True` 或 `False`。  下列範例將說明這點。  
  
 `42 < 81`  
  
 因為 42 小於 81，所以上述範例中的布林運算式會評估為 `True`。  如需此種運算式的詳細資訊，請參閱[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)。  
  
### 與邏輯運算子結合的比較運算子  
 比較運算式可以使用邏輯運算子加以結合，以產生更複雜的布林運算式。  下列範例會將比較運算子與邏輯運算子搭配使用。  
  
 `x > y And x < 1000`  
  
 在上述範例中，整個運算式的值取決於位於 `And` 運算子任一邊的運算式值。  如果這兩個運算式都為 `True`，則整體運算式會評估為 `True`。  如果任一個運算式為 `False`，則整個運算式會評估為 `False`。  
  
## 最短路徑運算子  
 邏輯運算子 `AndAlso` 和 `OrElse` 展現的行為稱為「*最少運算*」\(Short\-Circuiting\)。  最少運算的運算子會先評估左邊的運算元。  如果左邊運算元會決定整個運算式的值，則程式執行會繼續進行，但不評估右邊運算式。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 在上述範例中，運算子會評估左邊運算式 `45 < 12`。  因為左邊運算式會評估為 `False`，所以整個邏輯運算式必須評估為 `False`。  因此，程式執行會略過執行 `If` 區塊內的程式碼，而不需要評估右邊的運算式 `testFunction(3)`。  因為左邊運算式竄改整個運算式，所以這個範例不會呼叫 `testFunction()`。  
  
 同樣地，如果使用 `OrElse` 的邏輯運算式中的左邊運算式評估為 `True`，則執行會繼續進行程式碼的下一行，而不會評估右邊運算式，因為左邊運算式已驗證整個運算式。  
  
### 與非最少運算的運算子比較  
 相對地，在使用邏輯運算子 `And` 和 `Or` 時，會評估邏輯運算子的兩側。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 即使左邊運算式評估為 `False`，上述範例也會呼叫 `testFunction()`。  
  
## 括號內的運算式  
 您可以使用括號，控制布林 \(Boolean\) 運算式的評估順序。  會先評估括號所圍住的運算式。  就多層巢狀 \(Nest\) 層次而言，會將優先順序授與給巢狀最深層的運算式。  在括號內，會按照運算子優先順序來進行評估。  如需詳細資訊，請參閱 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## 請參閱  
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)