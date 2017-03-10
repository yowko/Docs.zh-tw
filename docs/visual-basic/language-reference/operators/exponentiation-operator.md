---
title: "^ Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.^"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising numbers to powers"
  - "^ operator [Visual Basic], exponention"
  - "square operator"
  - "^ operator [Visual Basic]"
  - "exponentiation operator [Visual Basic]"
  - "exponent"
  - "numbers, rasing"
  - "powers"
  - "arithmetic operators, exponentiation"
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# ^ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將一數值對另一數值做乘冪運算。  
  
## 語法  
  
```  
  
number ^ exponent  
```  
  
## 組件  
 `number`  
 必要項。  任何數值運算式。  
  
 `exponent`  
 必要項。  任何數值運算式。  
  
## 結果  
 結果是 `exponent` 對 `number` 做乘冪運算，且必定是 `Double` 值。  
  
## 支援類型  
 `Double`.  任何不同型別的運算元都會轉換成 `Double`。  
  
## 備註  
 Visual Basic 一律會在 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md) 中執行乘冪。  
  
 `exponent` 的值可以是小數、負數或兩者。  
  
 當在單一運算式中執行一個以上乘冪運算時，會按照從左至右的出現順序評估 `^` 運算子。  
  
> [!NOTE]
>  `^` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例使用 `^` 運算子以將數值與其指數做乘冪運算。  結果是第一運算元與第二運算元做乘冪運算。  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/exponentiation-operator_1.vb)]  
  
 前一個範例會產生以下結果：  
  
 `exp1` 設為 4 \(2 的平方\)。  
  
 `exp2` 設為 19683 \(3 的立方，再將該值乘以三次方\)。  
  
 `exp3` 設為 \-125 \(\-5 的立方\)。  
  
 `exp4` 設為 625 \(\-5 的第四次乘冪\)。  
  
 `exp5` 設為 2 \(8 的立方根\)。  
  
 `exp6` 設為 0.5 \(1.0 除以 8 的立方根\)。  
  
 請注意前述範例的運算式中的括號，這一點很重要。  基於「*運算子優先順序*」，Visual Basic 通常會先執行 `^` 運算子再執行其他運算子，即使是一元 `–` 運算子也一樣。  若已計算不含括號的 `exp4` 和 `exp6`，則可能產生下列結果：  
  
 `exp4 = -5 ^ 4`將計算成 – \(5 第四次方\)，從而會導致\-625。  
  
 `exp6 = 8 ^ -1.0 / 3.0` 計算成 \(8 的 –1 乘冪，或 0.125\) 除以 3.0，得到 0.041666666666666666666666666666667。  
  
## 請參閱  
 [^\= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)