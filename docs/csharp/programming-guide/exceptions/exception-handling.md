---
title: "例外狀況處理 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外狀況處理 [C#], 關於例外狀況處理"
  - "例外狀況 [C#], 處理"
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 例外狀況處理 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 程式設計師使用 [try](../../../csharp/language-reference/keywords/try-catch.md) 區塊分割可能受例外狀況影響的程式碼。  使用相關聯的 [catch](../../../csharp/language-reference/keywords/try-catch.md)區塊處理任何產生的例外狀況。  [finally](../../../csharp/language-reference/keywords/try-finally.md) 區塊包含程式碼，無論是否在 `try` 區塊擲出例外狀況 \(例如釋放在 `try` 區塊中配置的資源\)，都會執行該程式碼。  `try` 區塊需要一或多個相關聯的 `catch` 區塊和\/或`finally`區塊。  
  
 下列範例顯示 `try-catch` 陳述式、`try-finally` 陳述式和 `try-catch-finally` 陳述式。  
  
 [!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 `try` 區塊若沒有`catch`或`finally`，會導致編譯器錯誤。  
  
## Catch 區塊  
 `catch` 區塊可指定要攔截的例外狀況類型。  型別規格稱為「*例外狀況篩選條件*」\(Exception Filter\)。  例外狀況型別必須是從 <xref:System.Exception> 衍生。  一般情況下，除非您知道如何處理可能會在 `try` 區塊中擲回的所有例外狀況，或者您已在 `catch` 區塊的結尾包含 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式，否則請勿將 <xref:System.Exception>指定為例外狀況篩選條件。  
  
 具有不同例外狀況篩選條件的多個 `catch` 區塊可以鏈結在一起。  `catch` 區塊在程式碼中是由上至下進行評估的，但針對每個擲回的例外狀況，只會執行一個 `catch` 區塊。  會執行第一個 `catch` 區塊，這個區塊指定精確的型別或擲回例外狀況的基底類別。  如果沒有任何 `catch` 區塊指定相符的例外狀況篩選器，若陳述式中有篩選器，則 `catch` 中每有選定任何篩選器。  重要的是要先將 `catch` 區塊和最特定的 \(即最具衍生性的\) 例外狀況型別放在一起。  
  
 當下列條件為 true 時，您應攔截例外狀況：  
  
-   您確實了解可能擲回例外狀況的原因，而且可以實作特定復原動作，例如，在攔截 <xref:System.IO.FileNotFoundException> 物件時提示使用者輸入新的檔案名稱。  
  
-   您可以建立並擲回較特定的新例外狀況。  
  
     [!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   您想要在傳遞例外狀況以進行其他處理之前，對該例外狀況進行部分處理。  在下列範例中，`catch` 區塊用來將項目增加至錯誤記錄檔，再重新擲回例外狀況。  
  
     [!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## Finally 區塊  
 `finally` 區塊可讓您清理在 `try` 區塊中執行的動作。  如果有，`finally` 區塊會在 `try` 區塊和任何相符的 `catch` 區塊之後最後執行。  `finally` 區塊永遠都會執行，不管是否擲回例外狀況，或是否找到與例外狀況型別相符的 `catch` 區塊。  
  
 `finally` 區塊可用來釋放資源 \(例如檔案資料流、資料庫連接和圖形控制代碼\)，而不需等候執行階段中的記憶體回收行程完成物件。  如需詳細資訊，請參閱 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)。  
  
 下列範例中，`finally` 區塊用於關閉在 `try` 區塊中開啟的檔案。  請注意，在關閉檔案之前，會先檢查檔案控制代碼的狀態。  如果`try`區塊不能開啟檔案，檔案控制代碼仍然會有 `null` 值，且`finally` 區塊不會嘗試關閉它。  或者，如果成功在 `try`區塊開啟該檔案，`finally` 區塊會關閉開啟的檔案。  
  
 [!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)