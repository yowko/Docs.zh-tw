---
title: "How to: Calculate Numeric Values (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "operator precedence"
  - "operators [Visual Basic]"
  - "expressions [Visual Basic], numeric"
  - "calculations, numeric expressions"
  - "precedence, of operators"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "numeric expressions"
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Calculate Numeric Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以使用數值運算式來計算數值。  「*數值運算式*」\(Numeric Expression\) 是一種運算式，包含代表數值的常值 \(Literal\)、常數及變數，以及會對這些值執行動作的運算子。  
  
## 計算數值  
  
#### 若要計算數值  
  
-   將一或多個數字常值、常數和變數結合至數值運算式。  下列範例會顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行會顯示常值、常數和變數。  每一行都是由本身構成有效的數值運算式。  最後一行則顯示一個變數與兩個常值的組合。  
  
     請注意，數值運算式本身不會構成完整的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 陳述式。  您必須使用運算式做為完整陳述式的一部分。  
  
#### 若要儲存數值  
  
-   您可以使用指派陳述式 \(Assignment Statement\)，將數值運算式所代表的值指派給變數，如下列範例所示。  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     在上述範例中，等於運算子 \(`=`\) 右側的運算式值已指派給運算子左側的變數 `j`，所以 `j` 會計算為 276。  
  
     如需詳細資訊，請參閱[Statements](../../../../visual-basic/language-reference/statements/index.md)。  
  
## 多個運算子  
 如果數值運算式包含一個以上的運算子，則會按照運算子優先順序 \(Operator Precedence\) 規則 \(Rule\) 來決定評估運算子的順序。  若要覆寫運算子優先順序的規則，您可以用括號將運算式括住，如上面的範例所示。括號內的運算式會先行計算。  
  
#### 若要覆寫一般運算子優先順序  
  
-   使用括號，括住您想要先執行的運算。  下列範例會顯示兩個具有相同運算元和運算子的不同結果。  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     在上述範例中，括住 `(67 + i)` 的括號會覆寫一般優先順序，所以 `j` 的計算會先執行加法運算子 \(`+`\)，因此指派給 `j` 的值為 276 \(4 乘以 69\)。  `k` 的計算會以一般優先順序 \(`*` 優先於 `+`\) 執行運算子，因此指派給 `k` 的值為 270 \(268 加 2\)。  
  
     如需詳細資訊，請參閱 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## 請參閱  
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)