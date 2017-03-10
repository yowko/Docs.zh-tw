---
title: "goto (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "goto_CSharpKeyword"
  - "goto"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "goto 關鍵字 [C#]"
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# goto (C# 參考)
`goto` 陳述式將程式控制直接轉移到標記陳述式。  
  
 `goto` 的常見用法是轉移控制至特定的 switch\-case 標記或 `switch` 陳述式中預設的標記。  
  
 `goto` 陳述式對於跳出複雜的巢狀迴圈也很有用。  
  
## 範例  
 下列範例說明在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `goto`。  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/csharp/goto_1.cs)]  
  
## 範例  
 以下的範例說明使用 `goto` 以中斷巢狀迴圈。  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/csharp/goto_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [goto 陳述式](/visual-cpp/cpp/goto-statement-cpp)   
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)