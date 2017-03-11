---
title: "And Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.And"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic], bitwise"
  - "logical conjunction"
  - "bitwise AND operator [Visual Basic]"
  - "conjunction operator"
  - "And operator [Visual Basic]"
  - "bitwise operators, AND operator"
  - "operators [Visual Basic], conjunction"
  - "bitwise comparison"
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# And Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

對兩個 `Boolean` 運算式執行邏輯上的交集 \(Conjunction\)，或對兩個數值運算式 \(Numeric Expression\) 執行位元的交集。  
  
## 語法  
  
```  
  
result = expression1 And expression2  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 或數值運算式。  對於布林比較而言，`result` 為兩個 `Boolean` 值的邏輯結合。  對於位元運算而言，`result` 則為數值，代表兩個數值位元模式的位元結合。  
  
 `expression1`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
## 備註  
 對於 Boolean 比較而言，只有在 `expression1` 和 `expression2` 都評估為 `True` 時，`result` 才會是 `True`。  下表說明如何決定 `result`。  
  
|如果 `expression1` 為|且 `expression2` 是|`result` 的值為|  
|------------------------|-----------------------|------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在布林比較中，`And` 運算子一律會評估兩個運算式，其中可以包括進行程序呼叫。  [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) 會執行「*最少運算*」\(Short Circuit\)，這表示如果 `expression1` 為 `False`，就不會評估 `expression2`。  
  
 套用至數值時，`And` 運算子會對兩個數值運算式中同位置的位元執行位元比較，並依據下表來設定 `result` 中的對應位元。  
  
|如果 `expression1` 中的位元是|並且 `expression2` 中的位元是|`result` 中的位元是|  
|----------------------------|----------------------------|--------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  由於邏輯和位元運算子的優先順序低於其他算術和關係 \(Relational\) 運算子，所以任何的位元運算都必須加上括號，以確保結果的正確性。  
  
## 資料型別  
 如果運算元是以一個 `Boolean` 運算式和一個數字運算式組成，則 Visual Basic 會將 `Boolean` 運算式轉換成數值 \(\-1 代表 `True` 而 0 代表 `False`\)，並執行位元運算。  
  
 對於 Boolean 比較而言，結果的資料型別是 `Boolean`。  進行位元 \(Bitwise\) 比較時，結果資料型別會是數字型别，適用於 `expression1` 和 `expression2` 的資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關係和位元比較」表。  
  
> [!NOTE]
>  `And` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `And` 運算子，對兩個運算式執行邏輯交集。  結果為 `Boolean` 值，代表兩個運算式是否都是 `True`。  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/and-operator_1.vb)]  
  
 前一個範例會分別產生 `True` 和 `False` 的結果。  
  
## 範例  
 下列範例會使用 `And` 運算子，對兩個數值運算式的個別位元執行邏輯交集。  如果運算元中的對應位元都是設為 1，則會將結果模式中的對應位元設為 1。  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/and-operator_2.vb)]  
  
 前一個範例會分別產生 8、2 和 0 的結果。  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)