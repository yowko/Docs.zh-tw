---
title: "How to: Force an Argument to Be Passed by Value (Visual Basic) | Microsoft Docs"
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
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], in parentheses"
  - "procedure arguments, in parentheses"
  - "arguments [Visual Basic], changing value"
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Force an Argument to Be Passed by Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

程序宣告可決定傳遞機制。  如果是以 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 方式宣告參數，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會預期以傳址 \(By Reference\) 方式傳遞對應的引數。  這允許程序變更呼叫程式碼中，對應到引數的程式設計項目值。  如果您不想讓對應的項目產生變更，則可使用括號將引數名稱括起來，即能覆寫程序呼叫中的 `ByRef` 傳遞機制。  這些括號不包括在呼叫中用於引數清單的括號。  
  
 呼叫程式碼無法覆寫 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 機制。  
  
### 若要強制以傳值方式傳遞引數  
  
-   如果程序中是以 `ByVal` 宣告對應的參數，則不需採取任何其他步驟。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 也會預期以值來傳遞引數。  
  
-   如果程序中是以 `ByRef` 宣告對應的參數，請在程序呼叫中用括號將引數括起來。  
  
## 範例  
 下列範例會覆寫 `ByRef` 參數宣告。  在強制 `ByVal` 的呼叫中，請注意兩種層次的括號。  
  
 [!code-vb[VbVbcnProcedures#39](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-force-an-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-force-an-argument_2.vb)]  
  
 在將引數清單內的 `str` 以額外括號括起來時，`setNewString` 程序無法變更它在呼叫程式碼中的值，而 `MsgBox` 會顯示「如果以 ByVal 方式傳遞，則無法取代」。  若未以額外的括號將 `str` 括起來，則程序即可變更它，且 `MsgBox` 會顯示「這是新的 inString 引數值」。  
  
## 編譯程式碼  
 當您以傳址方式來傳遞變數時，您必須用 `ByRef` 關鍵字指定這個機制。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的預設值是以值來傳遞引數。  但是，在每一個宣告的參數中包括 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 關鍵字是很好的程式設計方式。  這樣會讓您的程式碼更容易閱讀。  
  
## 穩固程式設計  
 如果程序以 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 宣告參數，則程式碼的正確執行可能會根據是否可在呼叫程式碼中變更對應的項目而定。  如果呼叫程式碼是藉由將引數括在括號中來覆寫這個呼叫機制，或者傳遞的是不可修改的引數，則程序無法變更對應的項目。  這可能會在呼叫程式碼中產生未預期的結果。  
  
## .NET Framework 安全性  
 允許程序在呼叫程式碼中變更引數對應的值，一定會有潛在風險。  請確定您預期會變更這個值，並在使用它之前，準備好檢查它的有效性。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)