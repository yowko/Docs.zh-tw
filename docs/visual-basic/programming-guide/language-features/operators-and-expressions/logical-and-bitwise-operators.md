---
title: "Logical and Bitwise Operators in Visual Basic | Microsoft Docs"
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
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "operators [Visual Basic], logical"
  - "AndAlso operator"
  - "Not operator [Visual Basic], Boolean expressions"
  - "Xor operator [Visual Basic], Boolean expressions"
  - "And operator [Visual Basic], logical operators"
  - "logical operators"
  - "expressions [Visual Basic], Boolean"
  - "Or operator, logical operators"
  - "Visual Basic code, operators"
  - "short-circuiting, logical operators"
  - "logical operators, short-circuiting"
  - "Visual Basic code, expressions"
  - "logical operators, binary"
  - "OrElse operator [Visual Basic]"
  - "logical operators, unary"
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Logical and Bitwise Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

邏輯運算子會比較 `Boolean` 運算式並傳回 `Boolean` 結果。  `And`、`Or`、`AndAlso`、`OrElse` 和 `Xor` 運算子會採用兩個運算元，因此為「*二元*」\(Binary\)，而 `Not` 運算子則採用單一運算元，所以為「*一元*」\(Unary\)。  其中某些運算子也可以對整數值執行位元邏輯運算。  
  
## 一元邏輯運算子  
 [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) 會對 `Boolean` 運算式執行邏輯「*負運算*」\(Negation\)。  它會產生與其運算元相反的邏輯。  如果運算式評估為 `True`，則 `Not` 會傳回 `False`。如果運算式評估為 `False`，則 `Not` 會傳回 `True`。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_1.vb)]  
  
## 二元邏輯運算子  
 [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) 會對兩個 `Boolean` 運算式執行邏輯「*結合*」\(Conjunction\)。  如果兩個運算式都評估為 `True`，則 `And` 會傳回 `True`。  如果至少有一個運算式評估為 `False`，則 `And` 會傳回 `False`。  
  
 [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) 會對兩個 `Boolean` 運算式執行邏輯「*分離*」\(Disjunction\) 或「*包含*」\(Inclusion\)。  如果任一個運算式評估為 `True`，或兩者都評估為 `True`，則 `Or` 會傳回 `True`。  如果兩個運算式都不是評估為 `True`，則 `Or` 會傳回 `False`。  
  
 [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) 會對兩個 `Boolean` 運算式執行邏輯「*互斥*」\(Exclusion\)。  如果恰好一個運算式評估為 `True`，但並非兩者都如此，則 `Xor` 會傳回 `True`。  如果兩個運算式都評估為 `True`，或兩者都評估為 `False`，則 `Xor` 會傳回 `False`。  
  
 下列範例會說明 `And`、`Or` 和 `Xor` 運算子。  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_2.vb)]  
  
## 最少運算的邏輯運算  
 [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md)非常類似於 `And` 運算子，因為前者也會對兩個 `Boolean` 運算式執行邏輯結合。  兩者的主要差異在於 `AndAlso` 會展現「*最少運算*」\(Short\-Circuiting\) 行為。  如果 `AndAlso` 運算式中的第一個運算式評估為 `False`，則不會評估第二個運算式，因為它無法變更最終結果，而且 `AndAlso` 會傳回 `False`。  
  
 同樣地，[OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md)會對兩個 `Boolean` 運算式執行最少運算的邏輯分離。  如果 `OrElse` 運算式中的第一個運算式評估為 `True`，則不會評估第二個運算式，因為它無法變更最終結果，而且 `OrElse` 會傳回 `True`。  
  
### 最少運算的交換  
 最少運算可以透過不評估無法變更邏輯運算結果的運算式來增進效能。  然而，如果該運算式執行額外動作，最少運算則會略過那些動作。  例如，如果運算式包括 `Function` 程序的呼叫，則在運算式為最少運算時便不會呼叫該程序，並且不會執行 `Function` 中內含的任何其他程式碼。  因此，函式只能偶爾執行，無法正常進行測試。  或者，程式邏輯可能相依於 `Function` 中的程式碼。  
  
 下列範例會說明 `And`、`Or` 與其最少運算對應項之間的差異。  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_5.vb)]  
  
 在上述範例中，請注意在呼叫為最少運算時，不會執行 `checkIfValid()` 內的一些重要程式碼。  因為 `And` 不會進行最少運算，所以即使 `12 > 45` 會傳回 `False`，第一個 `If` 陳述式 \(Statement\) 也會呼叫 `checkIfValid()`。  當 `12 > 45` 傳回 `False` 時，`AndAlso` 會對第二個運算式進行最少運算，所以第二個 `If` 陳述式不會呼叫 `checkIfValid()`。  因為 `Or` 不會進行最少運算，所以即使 `12 < 45` 傳回 `True`，第三個 `If` 陳述式也會呼叫 `checkIfValid()`。  當 `12 < 45` 傳回 `True` 時，`OrElse` 會對第二個運算式進行最少運算，所以第四個 `If` 陳述式不會呼叫 `checkIfValid()`。  
  
## 位元運算  
 位元運算會以二進位 \(基底為 2\) 形式評估兩個整數值。  它們會比較位於對應位置的位元，然後根據比較結果來指派值。  下列範例會說明 `And` 運算子。  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/visualbasic/logical-and-bitwise-oper_6.vb)]  
  
 上述範例會將 `x` 的預設值設定為 1。  由於下列理由而發生這種情況：  
  
-   值會被視為二進位：  
  
     3 的二進位形式 \= 011  
  
     5 的二進位形式 \= 101  
  
-   `And` 運算子會比較二進位表示法，一次一個二進位位置 \(位元\)。  如果位於給定位置上的兩個位元都是 1，則會在結果的該位置中置入 1。  如果任一位元是 0，則會在結果的該位置中置入 0。  在上述範例中，結果如下：  
  
     011 \(3 的二進位形式\)  
  
     101 \(5 的二進位形式\)  
  
     001 \(結果，二進位形式\)  
  
-   結果會被視為十進位。  值 001 是 1 的二進位表示法，所以 `x` \= 1。  
  
 位元 `Or` 運算類似，但如果比較位元的任一或兩個位元為 1，則會將 1 指派給結果位元。  如果其中一個 \(而非兩者\) 比較位元為 1，則 `Xor` 會將 1 指派給結果位元。  `Not` 會採用單一運算元並且使所有位元 \(包括正負號位元\) 反轉，然後將該值指派給結果。  這表示對於帶正負號的正數，`Not` 一律會傳回負值，而對於負數，`Not` 則一律會傳回正值或零值。  
  
 `AndAlso` 和 `OrElse` 運算子不支援位元運算。  
  
> [!NOTE]
>  只有整數型別才能執行位元運算。  必須先將浮點值轉換成整數型別，才能執行位元運算。  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)