---
title: "throw (C# 參考) | Microsoft Docs"
ms.date: "2015-03-02"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "throw"
  - "throw_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "throw 陳述式 [C#]"
  - "throw 陳述式 [C#]"
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
caps.handback.revision: 22
---
# throw (C# 參考)
`throw` 陳述式用來表示在程式執行期間發生異常情況 \(例外狀況\)。  
  
## 備註  
 擲回的例外狀況是一個物件，其類別衍生自 <xref:System.Exception?displayProperty=fullName>，如下列範例所示。  
  
```  
class MyException : System.Exception {}  
// ...  
throw new MyException();  
```  
  
 `throw` 陳述式通常會與 `try-catch` 或 `try-finally` 陳述式一起使用。[throw](../../../csharp/language-reference/keywords/throw.md) 陳述式可以在 `catch` 區塊中用來重新擲回 `catch` 區塊攔截到的例外狀況。在這種情況下，[throw](../../../csharp/language-reference/keywords/throw.md) 陳述式不接受例外狀況運算元。如需詳細資訊與範例，請參閱 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)與 [如何：明確擲回例外狀況](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)。  
  
## 範例  
 這個範例將示範如何使用 `throw` 陳述式擲回例外狀況。  
  
 [!code-cs[csrefKeywordsExceptions#5](../../../csharp/language-reference/keywords/codesnippet/csharp/throw_1.cs)]  
  
## 程式碼範例  
 請參閱 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) 和 [如何：明確擲回例外狀況](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)中的範例。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [C\+\+ 中的 try、catch 和 throw 陳述式](../../../csharp/language-reference/keywords/try-catch.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [如何：明確擲回例外狀況](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)