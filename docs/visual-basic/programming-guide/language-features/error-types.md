---
title: "Error Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, types"
  - "errors [Visual Basic], types"
  - "errors [Visual Basic], logic"
  - "errors [Visual Basic], syntax"
  - "logic errors, Visual Basic"
  - "run-time errors, types of errors"
  - "syntax errors, Visual Basic"
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中，錯誤 \(亦稱為「*例外狀況*」\(Exception\)\) 可分為三個類別：語法錯誤、執行階段錯誤和邏輯錯誤。  
  
## 語法錯誤  
 「*語法錯誤*」\(Syntax Error\) 會在編寫程式碼時出現。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會在您於 \[**程式碼編輯器**\] 視窗內輸入程式碼時進行檢查，並在有錯誤 \(例如拼字錯誤或語言項目使用不正確\) 時發出警示。  語法錯誤是最常見的錯誤類型。  當錯誤發生時，您可在程式碼環境下直接修正。  
  
> [!NOTE]
>  `Option Explicit` 陳述式是避免語法錯誤的一種方式。  它會強制您事先宣告要用於應用程式的所有變數。  因此，當您在程式碼中使用那些變數時，任何字面上的錯誤可立即發現並修正。  
  
## 執行階段錯誤  
 「*執行階段錯誤*」\(Run\-time Error\) 是在您編譯完成並執行程式碼時才會出現的錯誤。  這些包括沒有語法錯誤，看起來似乎正確但是卻無法執行的程式碼。  例如，假設您正確地撰寫了一行開啟檔案的程式碼。  但如果這個檔案損毀，應用程式就無法執行 `Open` 函式，並且停止執行。  您可以重新撰寫程式碼，然後重新編譯與執行，以修正大部分的執行階段錯誤。  
  
## 邏輯錯誤  
 「*邏輯錯誤*」\(Logic Error\) 是應用程式在使用時出現的錯誤。  這類錯誤最常見的是在回應使用者動作時出現缺點或意外的結果。  例如，輸入錯誤的索引鍵或是其他外界的影響可能會使應用程式在預期的參數中或整個停止運作。  邏輯錯誤通常是最難修復的錯誤類型，因為您不一定瞭解發生原因。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [偵錯工具基礎](/visual-studio/debugger/debugger-basics)