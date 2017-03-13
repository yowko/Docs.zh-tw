---
title: "Resume Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Resume"
  - "vb.ResumeNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Next statement, Resume"
  - "Resume Next statement"
  - "execution, resuming"
  - "run-time errors, resuming after"
  - "Resume statement, syntax"
  - "errors [Visual Basic], resuming after"
  - "Error statement, and Resume statement"
  - "execution"
  - "Resume statement"
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Resume Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在完成錯誤處理常式之後繼續執行。  
  
 我們建議您使用結構化的例外處理，可能的話，程式碼中，而不是使用非結構化的例外處理和`On Error`和`Resume`陳述式。  如需詳細資訊，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## 語法  
  
```  
Resume [ Next | line ]  
```  
  
## 組件  
 `Resume`  
 必要項。  如果錯誤發生在與錯誤處理常式相同的程序中，則繼續執行導致錯誤的陳述式。  如果錯誤發生在呼叫的程序中，則從包含錯誤處理常式的程序中最後呼叫的陳述式繼續執行。  
  
 `Next`  
 選擇項。  如果錯誤發生在與錯誤處理常式相同的程序中，則繼續執行導致錯誤發生的陳述式後面的陳述式。  如果錯誤發生在呼叫的程序中，則從包含錯誤處理常式 \(或 `On Error Resume Next` 陳述式\) 的程序中最後呼叫的陳述式後面的陳述式繼續執行。  
  
 `line`  
 選擇項。  從必要的 `line` 引數中所指定的那一行繼續執行。  `line` 引數就是行標籤或行號，且必須位在與錯誤處理常式相同的程序中。  
  
## 備註  
  
> [!NOTE]
>  我們建議您使用結構化的例外處理，可能的話，程式碼中，而不是使用非結構化的例外處理和`On Error`和`Resume`陳述式。  如需詳細資訊，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 如果您在錯誤處理常式以外的位置使用 `Resume` 陳述式，將會發生錯誤。  
  
 `Resume` 陳述式無法在含有 `Try...Catch...Finally` 陳述式的任何程序中使用。  
  
## 範例  
 這個範例會使用 `Resume` 陳述式結束程序中的錯誤處理，然後繼續執行造成錯誤的陳述式。  產生錯誤代碼 55，說明如何使用 `Resume` 陳述式。  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## 需求  
 **命名空間**：[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件**：Visual Basic 執行階段程式庫 \(在 Microsoft.VisualBasic.dll 中\)  
  
## 請參閱  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)