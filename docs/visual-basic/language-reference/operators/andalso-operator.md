---
title: "AndAlso Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AndAlso"
  - "AndAlso"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "AndAlso operator"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], conjunction"
  - "short-circuit evaluation"
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# AndAlso Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

對兩個運算式執行最少運算邏輯交集運算。  
  
## 語法  
  
```  
  
result = expression1 AndAlso expression2  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`result`|必要項。  任何 `Boolean` 運算式。  結果是比較兩個運算式的 `Boolean` 結果。|  
|`expression1`|必要項。  任何 `Boolean` 運算式。|  
|`expression2`|必要項。  任何 `Boolean` 運算式。|  
  
## 備註  
 若已編譯的程式碼依其他運算式的結果，能略過運算式的評估，則邏輯運算式就稱為「*最少運算*」\(Short\-Circuiting\)。  若所評估之第一個運算式的結果會決定運算的最終結果，則不需評估第二個運算式，因其無法改變最終結果。  若略過的是複雜或包含程序呼叫的運算式，則最少運算便可以提升效能。  
  
 若將兩個運算式評估為 `True`，則 `result` 為 `True`。  下表說明如何決定 `result`。  
  
||||  
|-|-|-|  
|如果 `expression1` 為|且 `expression2` 是|`result` 的值為|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|\(不評估\)|`False`|  
  
## 資料型別  
 `AndAlso` 運算子只針對 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 定義。  Visual Basic 會在必要時將每個運算元轉換成 `Boolean`，並且完全以 `Boolean` 執行運算。  若將結果指派給數字型別，Visual Basic 就會將它從 `Boolean` 轉換成該型別。  這可能會產生未預期的行為。  例如，轉換成 `Integer` 時，`5 AndAlso 12` 會導致 `–1`。  
  
## 多載化  
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) 和 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以「*多載*」\(Overload\)，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `And` 和 `IsFalse` 運算子會影響 `AndAlso` 運算子的行為。  如果您的程式碼在多載 `And` 和 `IsFalse` 之類別或結構上會使用 `AndAlso`，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `AndAlso` 運算子，對兩個運算式執行邏輯交集。  結果是代表整個交集的運算式是否為 true 的 `Boolean` 值。  如果第一個運算式為 `False`，則不評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/andalso-operator_1.vb)]  
  
 前一個範例分別產生 `True`、`False` 和 `False` 的結果。  計算 `secondCheck` 時，不會評估第二個運算式，因為第一個運算式已經是 `False`。  然而，計算 `thirdCheck` 時會評估第二個運算式。  
  
## 範例  
 下列範例會顯示 `Function` 程序，在陣列元素之間搜尋指定值。  如果陣列是空的，或陣列長度已超過，`While` 陳述式就不能根據搜尋值測試陣列元素。  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/andalso-operator_2.vb)]  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md)   
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)