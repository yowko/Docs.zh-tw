---
title: "IsNot Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.isnot"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsNot operator"
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# IsNot Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

比較兩個物件參考變數。  
  
## 語法  
  
```  
  
result = object1 IsNot object2  
```  
  
## 組件  
 `result`  
 必要項。  `Boolean` 值。  
  
 `object1`  
 必要項。  任何 `Object` 變數或運算式。  
  
 `object2`  
 必要項。  任何 `Object` 變數或運算式。  
  
## 備註  
 `IsNot` 運算子會判斷兩個物件參考是否會參考不同的物件。  但是，它不會執行值比較。  如果 `object1` 和 `object2` 都會參考完全相同的物件執行個體，則 `result` 為 `False`，如果不是，則 `result` 為 `True`。  
  
 `IsNot` 是 `Is` 運算子的相反。  `IsNot` 的優點是可避免含有 `Not` 和 `Is` 之難操作的語法，這種語法十分難閱讀。  
  
 您可以使用 `Is` 和 `IsNot` 運算子，來測試早期繫結 \(Early Bound\) 和晚期繫結 \(Late Bound\) 物件。  
  
> [!NOTE]
>  `IsNot` 運算子不能用來比較從 `TypeOf` 運算子傳回的運算式。  您必須改用 `Not` 和 `Is` 運算子。  
  
## 範例  
 下列程式碼範例會使用 `Is` 運算子和 `IsNot` 運算子，來完成相同的比較。  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/isnot-operator_1.vb)]  
  
## 請參閱  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [How to: Test Whether Two Objects Are the Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)