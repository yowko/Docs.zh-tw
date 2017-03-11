---
title: "Operators and Expressions in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic], operands"
  - "operators [Visual Basic]"
  - "operands, definition"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "operands"
  - "expressions [Visual Basic]"
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Operators and Expressions in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*運算子*」\(Operator\) 是一種程式碼項目，會在保留值的一個或多個程式碼項目上執行運算。  值項目包括變數、常數、常值 \(Literal\)、屬性、來自 `Function` 和 `Operator` 程序的傳回值，以及運算式。  
  
 「*運算式*」\(Expression\) 是一系列與運算子結合的值項目，它會產生新值。  運算子會經由執行計算、比較或其他作業，對值項目執行動作。  
  
## 運算子的型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供下列型別的運算子：  
  
-   [算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)會在數值上執行類似的計算，包括將它們的位元模式移位。  
  
-   [比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)會比較兩個運算式，並傳回代表比較結果的 `Boolean` 值。  
  
-   [串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)會將多個字串聯結 \(Join\) 成單一字串。  
  
-   [Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)會結合 `Boolean` 或數值，並傳回與值相同資料型別的結果。  
  
 與運算子結合的值項目稱為該運算子的「*運算元*」\(Operand\)。  與值項目結合的運算子會成形運算式，但指派運算子除外，因為它會形成「*陳述式*」\(Statement\)。  如需詳細資訊，請參閱 [Statements](../../../../visual-basic/programming-guide/language-features/statements.md)。  
  
## 計算運算式  
 運算式的最終結果代表一個值，通常具有熟悉的資料型別，如 `Boolean`、`String` 或數字型別 \(Numeric Type\)。  
  
 以下是運算式的範例。  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 數個運算子可以在單一運算式或陳述式中執行動作，如下列範例所述。  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/index_1.vb)]  
  
 在上述範例中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在指派運算子 \(`=`\) 右側的運算式中執行運算，然後將結果值指派給左側的變數 `x`。  可以結合為運算式的運算子數目並沒有實際的限制，但是必須了解 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)，以確定您會取得預期的結果。  
  
 如需詳細資訊和範例，請參閱 [Visual Basic 2005 中的運算子多載](http://go.microsoft.com/fwlink/?LinkId=101703) \(英文\)。  
  
## 請參閱  
 [Operators](../../../../visual-basic/language-reference/operators/index.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)