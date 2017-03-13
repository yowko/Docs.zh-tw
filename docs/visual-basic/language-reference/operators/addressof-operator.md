---
title: "AddressOf Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "AddressOf"
  - "vb.AddressOf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddressOf operator"
  - "addresses, passing to API procedures"
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# AddressOf Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

建立參考特定程序的程序委派執行個體。  
  
## 語法  
  
```  
  
AddressOf procedurename  
```  
  
## 組件  
 `procedurename`  
 必要項。  指定最近建立之程序委派所參考的程序。  
  
## 備註  
 `AddressOf` 運算子會建立指向 `procedurename` 所指定之函式的函式委派。  當指定的程序是執行個體方法 \(Instance Method\) 時，函式委派會同時參考執行個體和方法。  然後，叫用 \(Invoke\) 該函式委派時，會呼叫所指定執行個體的指定方法。  
  
 `AddressOf` 運算子可用來做為委派建構函式的運算元，或是在可由編譯器 \(Compiler\) 決定型別的內容中使用此運算子。  
  
## 範例  
 這個範例會使用 `AddressOf` 運算子，來指定要處理按鈕之 `Click` 事件的委派。  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## 範例  
 下列範例會使用 `AddressOf` 運算子，來指定執行緒 \(Thread\) 的啟動函式。  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## 請參閱  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)