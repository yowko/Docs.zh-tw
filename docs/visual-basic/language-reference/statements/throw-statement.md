---
title: "Throw Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Throw"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structured exception handling, throw statements"
  - "try-catch exception handling, throw statements"
  - "throw statement, about throw statements"
  - "throwing exceptions, throw statement"
  - "exception handling, throw statement"
  - "On Error statement, throwing exceptions"
  - "throwing exceptions"
  - "exception handling, unstructured"
  - "throw statement"
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Throw Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在程序內擲回例外狀況。  
  
## 語法  
  
```  
Throw [ expression ]  
```  
  
## 組件  
 `expression`  
 提供要擲回的例外狀況的資訊。  位於 `Catch` 陳述式中時為選擇項，否則為必要項。  
  
## 備註  
 `Throw` 陳述式會擲回可以使用結構化例外處理程式碼 \(`Try`...`Catch`...`Finally`\) 或非結構化例外處理程式碼 \(`On Error GoTo`\) 處理的例外狀況。  您可以使用 `Throw` 陳述式截取程式碼內的錯誤，因為 Visual Basic 會將呼叫堆疊上移，直到它找到正確的例外狀況處理程式碼為止。  
  
 不含運算式的 `Throw` 陳述式僅能用於 `Catch` 陳述式內，在這個情況下，陳述式會重新擲回目前正由 `Catch` 陳述式處理的例外狀況。  
  
 `Throw` 陳述式會為 `expression` 例外狀況重設呼叫堆疊。  如果未提供 `expression`，呼叫堆疊會保持不變。  您可以透過 <xref:System.Exception.StackTrace%2A> 屬性存取例外狀況的呼叫堆疊。  
  
## 範例  
 下列程式碼使用 `Throw` 陳述式擲回例外狀況：  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## 需求  
 **命名空間**：[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組**︰`Interaction`  
  
 **組件**：Visual Basic 執行階段程式庫 \(在 Microsoft.VisualBasic.dll 中\)  
  
## 請參閱  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)