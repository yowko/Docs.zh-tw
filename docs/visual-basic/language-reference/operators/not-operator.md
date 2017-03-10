---
title: "Not Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Not"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean expressions, negating"
  - "operators [Visual Basic], bitwise"
  - "negation operator"
  - "inverse bit values in variables"
  - "bitwise operators, NOT operator"
  - "bitwise comparison"
  - "Not operator [Visual Basic]"
  - "logical negation"
  - "operators [Visual Basic], negation"
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Not Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

對 `Boolean` 運算式執行邏輯否定，或對數值運算式執行位元否定。  
  
## 語法  
  
```  
  
result = Not expression  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
 `expression`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
## 備註  
 就 `Boolean` 運算式而論，下表說明了如何判斷 `result`。  
  
|如果 `expression` 為|`result` 的值為|  
|-----------------------|------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 就數值運算式而論，`Not` 運算子會將任何數值運算式的位元值反轉，並依據下表來設定 `result` 中的對應位元。  
  
|如果 `expression` 中的位元是|`result` 中的位元是|  
|---------------------------|--------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  由於邏輯和位元運算子的優先順序低於其他算術和關係運算子，所以任何位元運算都必須加上括號，以確保執行結果的正確性。  
  
## 資料型別  
 若為布林 \(Boolean\) 否定，則結果的資料型別為 `Boolean`。  若為位元 \(Bitwise\) 運算，則結果資料型別會與 `expression` 的資料型別相同。  不過，如果運算式是 `Decimal`，則結果為 `Long`。  
  
## 多載化  
 `Not` 運算子可以「*多載*」\(Overloaded\)，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `Not` 運算子，對 `Boolean` 運算式執行邏輯否定。  結果為 `Boolean` 值，表示運算式的相反值。  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/not-operator_1.vb)]  
  
 前述範例分別會產生 `False` 和 `True` 的結果。  
  
## 範例  
 下列範例會使用 `Not` 運算子，對數值運算式的個別位元執行邏輯否定。  會將結果模式中的對應位元設為運算元模式中對應位元的反向，包括正負號位元。  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/not-operator_2.vb)]  
  
 前一個範例分別產生 \-11、\-9 和 \-7 的結果。  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)