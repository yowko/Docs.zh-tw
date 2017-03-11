---
title: "Continue Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.continue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Continue statement [Visual Basic]"
  - "loops, transferring to next iteration"
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Continue Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將控制權立即轉移到迴圈 \(Loop\) 的下一個反覆運算。  
  
## 語法  
  
```  
Continue { Do | For | While }  
```  
  
## 備註  
 您可以從 `Do`、`For` 或 `While` 迴圈內轉移到該迴圈的下一個反覆運算。  控制權會立即移交給迴圈條件測試，這相當於轉移到 `For` 或 `While` 陳述式，或是轉移到包含 `Until` 或 `While` 子句的 `Do` 或 `Loop` 陳述式。  
  
 您可以在迴圈中任何允許轉移的位置使用 `Continue`。  允許控制權轉移的規則與 [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md)相同。  
  
 例如，如果迴圈完全包含在 `Try` 區塊、`Catch` 區塊或 `Finally` 區塊內，您便可以使用 `Continue` 轉移到迴圈之外。  相反地，如果 `Try`...`End Try` 結構包含於迴圈內，您就無法使用 `Continue` 將控制權轉移到 `Finally` 區塊之外，而是只能在要完全轉移到 `Try`...`End Try` 結構外時，用它轉移到 `Try` 或 `Catch` 區塊之外。  
  
 如果您具有相同類型的巢狀迴圈 \(例如，將 `Do` 迴圈置於另一個 `Do` 迴圈內\)，則 `Continue Do` 陳述式會跳到包含該陳述式之最內層 `Do` 迴圈的下一個反覆運算。  您無法使用 `Continue` 跳到相同類型之外層迴圈的下一個反覆運算。  
  
 如果您具有不同類型的巢狀迴圈 \(例如，將 `Do` 迴圈置於 `For` 迴圈內\)，則可以使用 `Continue Do` 或 `Continue For`，跳到這些任一迴圈的下一個反覆運算。  
  
## 範例  
 下列程式碼範例會使用 `Continue While` 陳述式，在除數為零時跳到陣列的下一行。  `Continue While` 會在 `For` 迴圈內。  它會轉移到 `While col < lastcol` 陳述式，這是包含 `For` 迴圈之最內層 `While` 迴圈的下一個反覆運算。  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/continue-statement_1.vb)]  
  
## 請參閱  
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)