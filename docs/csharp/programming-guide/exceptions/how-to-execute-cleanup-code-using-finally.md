---
title: "如何：使用 finally 執行清除程式碼 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外狀況處理 [C#], try/finally 區塊"
  - "例外狀況 [C#], try/finally 區塊"
  - "try/finally 區塊 [C#]"
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 如何：使用 finally 執行清除程式碼 (C# 程式設計手冊)
`finally` 陳述式的用途是確保在必要時會立即清除物件 \(通常是含有外部資源的物件\)，即使擲回例外狀況也一樣。  這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 上的 <xref:System.IO.Stream.Close%2A>，而不等待 Common Language Runtime 進行記憶體回收處理物件，如下所示：  
  
 [!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## 範例  
 為了將前面的程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示：  
  
 [!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 因為在 `OpenWrite()` 呼叫之前，`try` 區塊中隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身就會失敗，所以並不保證在嘗試關閉檔案時它是在開啟狀態。  `finally` 區塊會加入檢查，以確保在呼叫 <xref:System.IO.Stream.Close%2A> 方法之前，<xref:System.IO.FileStream> 物件不會是 `null`。  在沒有 `null` 檢查的情況下，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但是如果可能的話應該避免在 `finally` 區塊中擲回例外狀況。  
  
 在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。  因為允許連接至資料庫伺服器的連接數有時候是有限的，您應該盡快地關閉資料庫連接。  如果在關閉連接之前擲回例外狀況，這就是另一個最好使用 `finally` 區塊等待記憶體回收的案例。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)