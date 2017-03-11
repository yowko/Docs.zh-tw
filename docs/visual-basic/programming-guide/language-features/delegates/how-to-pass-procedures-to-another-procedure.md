---
title: "How to: Pass Procedures to Another Procedure in Visual Basic | Microsoft Docs"
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
  - "AddressOf operator"
  - "delegates [Visual Basic], passing procedures"
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Pass Procedures to Another Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

此範例顯示如何使用委派 \(Delegate\) 將程序傳遞至其他程序。  
  
 委派是可像 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中所有其他型別一樣使用的型別。  `AddressOf` 運算子會在套用至程序名稱時傳回委派物件。  
  
 此範例具有程序，該程序有委派參數且可參考以 `AddressOf` 運算子所取得的其他程序。  
  
### 建立委派和相對應的程序  
  
1.  建立名為 `MathOperator` 的委派。  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-pass-procedures-t_1.vb)]  
  
2.  建立名為 `AddNumbers` 並具有參數和傳回值的程序，且這些參數和傳回值符合 `MathOperator` 的參數和傳回值，這樣簽章會相符。  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-pass-procedures-t_2.vb)]  
  
3.  建立名為 `SubtractNumbers` 且具有和 `MathOperator` 相符的簽章程序。  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-pass-procedures-t_3.vb)]  
  
4.  建立名為 `DelegateTest` 且將委派視為參數的程序。  
  
     此程序可接受 \(Accept\) `AddNumbers` 或 `SubtractNumbers` 的參考，因為它們的簽章符合 `MathOperator` 簽章。  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-pass-procedures-t_4.vb)]  
  
5.  建立名為 `Test` 且呼叫一次 `DelegateTest` 的程序，這個程序將 `AddNumbers` 的委派做為參數，然後重新將 `SubtractNumbers` 的委派做為參數。  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-pass-procedures-t_5.vb)]  
  
     呼叫 `Test` 時，會先顯示 `5` 和 `3` 的 `AddNumbers` 結果 \(為 8\)。  然後會顯示 `9` 和 `3` 的 `SubtractNumbers` 結果 \(為 6\)。  
  
## 請參閱  
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)