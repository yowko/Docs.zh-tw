---
title: "Is Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.is"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparison operators"
  - "equivalent objects"
  - "TypeOf...Is expression"
  - "Is operator [Visual Basic]"
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Is Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

比較兩個物件參考變數。  
  
## 語法  
  
```  
  
result = object1 Is object2  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 值。  
  
 `object1`  
 必要項。  任何 `Object` 名稱。  
  
 `object2`  
 必要項。  任何 `Object` 名稱。  
  
## 備註  
 `Is` 運算子會判斷兩個物件參考是否代表同一物件。  但是，它不會執行值比較。  如果 `object1` 和 `object2` 都會參考完全相同的物件執行個體，則 `result` 為 `True`，如果不是，則 `result` 為 `False`。  
  
 `Is` 也可與 `TypeOf` 關鍵字搭配使用，以組成 `TypeOf`...`Is` 運算式，用以測試物件變數是否會與資料型別相容。  
  
> [!NOTE]
>  `Is` 關鍵字可以用於 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## 範例  
 下列範例會使用 `Is` 運算子，來比較物件參考的配對。  結果是指派給代表兩個物件是否完全一樣的 `Boolean` 值。  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 如以上範例所示範，可使用 `Is` 運算子來測試早期繫結 \(Early Bound\) 和晚期繫結 \(Late Bound\) 物件。  
  
## 請參閱  
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)