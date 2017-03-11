---
title: "TypeOf Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "TypeOf"
  - "vb.TypeOf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "types [Visual Basic], compatible"
  - "comparison operators"
  - "TypeOf...Is expression"
  - "data types [Visual Basic], compatible"
  - "TypeOf operator [Visual Basic]"
  - "compatible data types"
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# TypeOf Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

比較物件參考變數與資料類型。  
  
## 語法  
  
```  
  
result = TypeOf objectexpression Is typename  
```  
  
```  
  
result = TypeOf objectexpression IsNot typename  
```  
  
## 組件  
 `result`  
 更有效率。  `Boolean` 值。  
  
 `objectexpression`  
 必要項。  評估為參考類型的任何運算式。  
  
 `typename`  
 必要項。  任何資料類型名稱。  
  
## 備註  
 `TypeOf` 運算子會判定 `objectexpression` 的執行階段類型是否相容 `typename`。  相容性取決 `typename` 的類型分類。  下表顯示如何判斷相容性。  
  
|`typename` 的類型分類|相容性準則|  
|----------------------|-----------|  
|類別|`objectexpression` 屬於類型 `typename` 或繼承自 `typename`|  
|結構|`objectexpression` 屬於類型 `typename`|  
|介面|`objectexpression` 實作 `typename` 或繼承自實作 `typename` 的類別|  
  
 如果 `objectexpression` 的執行階段類別滿足相容性準則，則 `result` 是 `True`。  否則 `result` 是 `False`。  如果 `objectexpression` 為 null，則 `TypeOf`...`Is` 傳回 `False`，`IsNot` 則傳回 `True`。  
  
 `TypeOf` 一律會使用 `Is` 關鍵字來建構 `TypeOf`...`Is` 運算式，或使用 `IsNot` 關鍵字來建構 `TypeOf`...`IsNot` 運算式。  
  
## 範例  
 下列範例會使用 `TypeOf`...`Is` 運算式，測試兩個包含各種資料類型的物件參考變數的類型相容性。  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/typeof-operator_1.vb)]  
  
 變數 `refInteger` 具有執行階段類型 `Integer`。  它相容 `Integer`，但不相容 `Double`。  變數 `refForm` 具有執行階段類型 <xref:System.Windows.Forms.Form>。  它相容 <xref:System.Windows.Forms.Form> \(因為那是其類型\)、相容 <xref:System.Windows.Forms.Control> \(因為 <xref:System.Windows.Forms.Form> 繼承自 <xref:System.Windows.Forms.Control>\)，且具有 <xref:System.ComponentModel.IComponent> \(因為 <xref:System.Windows.Forms.Form> 繼承自 <xref:System.ComponentModel.Component>，它會實作 <xref:System.ComponentModel.IComponent>\)。  不過，`refForm` 不相容 <xref:System.Windows.Forms.Label>。  
  
## 請參閱  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)