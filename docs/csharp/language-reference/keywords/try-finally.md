---
title: "try-finally (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "finally"
  - "finally_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "finally 關鍵字 [C#]"
  - "try-finally 陳述式 [C#]"
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# try-finally (C# 參考)
透過使用 `finally` 區塊，您可以清除在 [try](../../../csharp/language-reference/keywords/try-catch.md) 區塊中配置的所有資源，即使 `try` 區塊中發生例外狀況，您也可以執行程式碼。  `finally` 區塊的陳述式通常會在控制權離開 `try` 陳述式時執行。  控制權的轉移可能因為正常執行；執行 `break`、`continue`、`goto` 或 `return` 陳述式；或者將例外狀況傳播至 `try` 陳述式範圍之外而發生。  
  
 在已處理的例外狀況中，會保證執行相關聯的 `finally` 區塊。  不過，如果例外狀況是未處理的，`finally` 區塊執行取決於例外狀況回溯作業的觸發方式。  接著，這將取決於您的電腦是如何設定的。  如需詳細資訊，請參閱 [CLR 中未處理之例外狀況的處理機制](http://go.microsoft.com/fwlink/?LinkId=128371)。  
  
 當發生未處理的例外狀況而結束應用程式時，是否執行 `finally` 區塊通常不重要。  不過，如果在 `finally` 區塊中的陳述式即使在那種情況下必須執行，其中一個解決方法是將 `catch` 區塊到 `try`\-`finally` 陳述式。  或者，您可以攔截在呼叫堆疊中較高層 `try`\-`finally` 陳述式的 `try` 區塊可能會擲回的例外狀況。  也就是，您可以在呼叫包含 `try`\-`finally` 陳述式之方法的方法中、在呼叫該方法的方法中，或在呼叫堆疊的任何方法中，攔截例外狀況。  如果未攔截例外狀況，則根據作業系統是否選取觸發例外狀況回溯作業，來決定 `finally` 區塊的執行。  
  
## 範例  
 在下列範例中，無效的轉換陳述式會造成 `System.InvalidCastException` 例外狀況。  例外狀況為未處理。  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 在下列範例中，來自 `TryCast` 方法的例外狀況是在位於呼叫堆疊更上方的方法中攔截到。  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 如需 `finally` 的詳細資訊，請參閱 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)。  
  
 C\# 也包含 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)，以方便語法提供類似的 <xref:System.IDisposable> 物件功能。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [try、throw 和 catch 陳述式 \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [如何：明確擲回例外狀況](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)