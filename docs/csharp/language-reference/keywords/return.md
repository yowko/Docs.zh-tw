---
title: "return (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "return_CSharpKeyword"
  - "return"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "return 關鍵字 [C#]"
  - "return 陳述式 [C#]"
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# return (C# 參考)
`return` 陳述式終止其所在處之方法的執行，並且轉移程式控制權至呼叫的方法。  它也可以傳回選擇性值。  如果方法屬於 `void` 型別，那麼可以省略 `return` 陳述式。  
  
 如果 return 陳述式位於 `try` 區塊內，則會先執行 `finally` 區塊 \(如果有的話\)，控制權才會回到呼叫的方法。  
  
## 範例  
 在下列範例中，`A()` 方法會將變數 `Area` 當做 [double](../../../csharp/language-reference/keywords/double.md) 值傳回。  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [return 陳述式](/visual-cpp/cpp/return-statement-cpp)   
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)