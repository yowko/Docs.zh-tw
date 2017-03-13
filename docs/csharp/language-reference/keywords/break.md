---
title: "break (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "break"
  - "break_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "break 關鍵字 [C#]"
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# break (C# 參考)
`break` 陳述式會終止它所在之最靠近的封閉式迴圈或 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。  程式控制權轉移到終止陳述式之後的陳述式 \(如果有的話\)。  
  
## 範例  
 此範例中的條件陳述式含有一個計數器，原本應該是從 1 數到 100，不過 `break` 陳述式在數到 4 的時候就會將迴圈終止。  
  
 [!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## 範例  
 在這個範例中，`break` 陳述式會用於中斷內層巢狀迴圈，並且將控制項傳回外層迴圈。  
  
 [!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## 範例  
 本範例說明如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `break`。  
  
 [!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 如果您輸入 `4`，輸出結果就會是：  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [switch](../../../csharp/language-reference/keywords/switch.md)   
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)