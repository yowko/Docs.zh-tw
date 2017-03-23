---
title: "Exit Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Exit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "files, closing"
  - "programs, quitting"
  - "code, exiting"
  - "Exit statement"
  - "program termination"
  - "execution, stopping"
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Exit Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

退出程序或區塊，並立即將控制傳輸至接在程序呼叫或區塊定義之後的陳述式。  
  
## 語法  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## 陳述式  
 `Exit Do`  
 立即結束它所在的 `Do` 迴圈。  程式碼會繼續執行 `Loop` 陳述式之後的陳述式。  `Exit Do` 只能用在 `Do` 迴圈內。  用於巢狀的 `Do` 迴圈內時，`Exit Do` 會退出最內層的迴圈，並將控制權轉移到巢狀結構中下一個較高的層次。  
  
 `Exit For`  
 立即結束它所在的 `For` 迴圈。  程式碼會繼續執行 `Next` 陳述式之後的陳述式。  `Exit For` 只能用在 `For`...`Next` 或 `For Each`...`Next` 迴圈內。  用於巢狀的 `For` 迴圈內時，`Exit For` 會退出最內層的迴圈，並將控制權轉移到巢狀結構中下一個較高的層次。  
  
 `Exit Function`  
 立即退出所在的 `Function` 程序，  程式碼會繼續執行呼叫 `Function` 程序的陳述式之後的陳述式。  `Exit Function` 只能用在 `Function` 程序內。  
  
 若要指定傳回值，您可以將該值指派給 `Exit Function` 陳述式前面程式行上的函式名稱。  若要以一個陳述式指派傳回值並結束該函式，您可以使用 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Exit Property`  
 立即退出所在的 `Property` 程序，  程式碼會繼續執行呼叫 `Property` 程序的陳述式，也就是繼續執行要求或設定屬性值的陳述式。  `Exit Property`只可以用在屬性的 `Get` 或 `Set` 程序內。  
  
 若要指定 `Get` 程序中的傳回值，您可以將該值指派給 `Exit Property` 陳述式前面程式行上的函式名稱。  若要以一個陳述式指派傳回值並結束 `Get` 程序，您可以使用 `Return` 陳述式。  
  
 在 `Set` 程序中，`Exit Property` 陳述式相當於 `Return` 陳述式。  
  
 `Exit Select`  
 立即退出所在的 `Select Case` 區塊，  程式碼會繼續執行 `End Select` 陳述式之後的陳述式。  `Exit Select` 只能用在 `Select Case` 陳述式內。  
  
 `Exit Sub`  
 立即退出所在的 `Sub` 程序，  程式碼會繼續執行呼叫 `Sub` 程序的陳述式之後的陳述式。  `Exit Sub` 只能用在 `Sub` 程序內。  
  
 在 `Sub` 程序中，`Exit Sub` 陳述式相當於 `Return` 陳述式。  
  
 `Exit Try`  
 立即退出所在的 `Try` 或 `Catch` 區塊，  程式碼會繼續執行 `Finally` 區塊 \(如果有的話\)，或是執行 `End Try` 陳述式之後的陳述式。  `Exit Try` 只可以用在 `Try` 或 `Catch` 區塊內，不可用在 `Finally` 區塊內。  
  
 `Exit While`  
 立即結束它所在的 `While` 迴圈。  程式碼會繼續執行 `End While` 陳述式之後的陳述式。  `Exit While` 只能用在 `While` 迴圈內。  當用於巢狀 `While` 迴圈內時，`Exit While` 會將控制權轉移到比發生 `Exit While` 的迴圈高出一個巢狀層次的迴圈。  
  
## 備註  
 請勿將 `Exit` 陳述式與 `End` 陳述式混淆。  `Exit` 不會定義陳述式的結尾。  
  
## 範例  
 在下列範例中，當 `index` 變數大於 100 時，迴圈條件就會停止迴圈。  但是當索引變數大於 10 時，迴圈中的 `If` 陳述式會導致 `Exit Do` 陳述式停止迴圈。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## 範例  
 下列範例會將傳回值指派給函式名稱 `myFunction`，然後使用 `Exit Function` 從函式返回。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## 範例  
 下列範例使用 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) 指派傳回值並結束函式。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## 請參閱  
 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)   
 [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)