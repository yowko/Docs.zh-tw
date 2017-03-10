---
title: "如何：使用 try/catch 處理例外狀況 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外狀況處理 [C#], try/catch 區塊"
  - "例外狀況 [C#], try/catch 區塊"
  - "try/catch 區塊 [C#]"
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 如何：使用 try/catch 處理例外狀況 (C# 程式設計手冊)
[try\-catch](../../../csharp/language-reference/keywords/try-catch.md) 區塊的用途，是攔截和處理工作碼所產生的例外狀況。  某些例外狀況可在 `catch` 區塊中處理，並且可以解決問題而不會重新擲回例外狀況，不過，通常您只能用於確保會擲回適當的例外狀況。  
  
## 範例  
 在此範例中，<xref:System.IndexOutOfRangeException> 不是最適當的例外狀況：<xref:System.ArgumentOutOfRangeException> 更適用於此方法，因為錯誤是由呼叫端傳入的 `index` 引數所導致。  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/csharp/how-to-handle-an-excepti_1.cs)]  
  
## 註解  
 造成例外狀況的程式碼位於 `try` 區塊中。  後面立即加入 `catch` 陳述式以處理 `IndexOutOfRangeException` \(如果發生的話\)。  `catch` 區塊會處理 `IndexOutOfRangeException`，然後改為擲回更適當的 `ArgumentOutOfRangeException` 例外狀況。  為了盡可能為呼叫端提供更多資訊，請考慮將原始的例外狀況指定為新例外狀況的 <xref:System.Exception.InnerException%2A>。  因為 <xref:System.Exception.InnerException%2A> 屬性為 [readonly](../../../csharp/language-reference/keywords/readonly.md)，所以您必須在新例外狀況的建構函式 \(Constructor\) 內指派它。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)