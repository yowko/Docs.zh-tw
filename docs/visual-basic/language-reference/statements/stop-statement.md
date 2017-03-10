---
title: "Stop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Stop"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "breakpoints, Stop statements"
  - "Stop statements, syntax"
  - "Stop statements"
  - "execution, suspending"
  - "processing, interrupting"
  - "processes, interrupting"
  - "execution, stopping"
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Stop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

暫停程式執行。  
  
## 語法  
  
```  
Stop  
```  
  
## 備註  
 可將 `Stop` 陳述式放在程序中的任意位置，以暫停程式的執行。  使用 `Stop` 陳述式類似於在程式碼中設定中斷點。  
  
 `Stop` 陳述式暫停程式執行，但不像 `End`，它並不關閉任何檔案或清除任何變數 \(除非是在編譯過的可執行檔 \(.exe\) 中遇到它\)。  
  
> [!NOTE]
>  如果在整合式開發環境 \(IDE\) 之外執行的程式碼中遇到 `Stop` 陳述式，則會叫用偵錯工具。  不論該程式碼是以 Debug 或 Retail 模式進行編譯，都是如此。  
  
## 範例  
 這個範例使用 `Stop` 陳述式，以在 `For...Next` 迴圈中每次重複時暫停執行。  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/stop-statement_1.vb)]  
  
## 請參閱  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)