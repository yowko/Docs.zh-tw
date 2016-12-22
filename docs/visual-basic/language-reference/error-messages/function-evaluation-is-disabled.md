---
title: "Function evaluation is disabled because a previous function evaluation timed out | Microsoft Docs"
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
  - "bc30957"
  - "vbc30957"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30957"
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function evaluation is disabled because a previous function evaluation timed out
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

函式評估已停用，因為先前的函式評估逾時。若要重新啟用函式評估，請再次逐步執行或重新啟動偵錯。  
  
 在 Visual Studio 偵錯工具中，運算式會指定程序呼叫，但是另一個評估已逾時。  
  
 程序呼叫逾時的可能原因包括無限迴圈或「*無止盡迴圈*」\(Endless Loop\)。  如需詳細資訊，請參閱[For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。  
  
 無限迴圈的一個特殊情形是「*遞迴*」\(Recursion\)。  如需詳細資訊，請參閱[Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。  
  
 **錯誤 ID：**BC30957  
  
### 若要更正這個錯誤  
  
1.  如果可能，請判斷前一個函式評估為何，以及導致它逾時的原因。  否則，您可能會再次遇到這個錯誤。  
  
2.  再次逐步執行偵錯工具，或結束並重新啟動偵錯。  
  
## 請參閱  
 [Visual Studio 偵錯](/visual-studio/debugger/debugging-in-visual-studio)   
 [使用偵錯工具巡覽程式碼](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [Visual Basic 中的運算式](../Topic/Expressions%20in%20Visual%20Basic.md)