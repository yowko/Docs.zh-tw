---
title: "while (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "while_CSharpKeyword"
  - "while"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "while 關鍵字 [C#]"
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# while (C# 參考)
`while` 陳述式會重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。  
  
## 範例  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/csharp/while_1.cs)]  
  
## 範例  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/csharp/while_2.cs)]  
  
## 範例  
 因為 `while` 運算式的測試是在每次執行迴圈前發生，`while` 迴圈可能不會執行，也可能執行一次以上。  這不同於會執行一或多次的 [do](../../../csharp/language-reference/keywords/do.md) 迴圈。  
  
 當 [break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式將控制轉移到迴圈外部時，可以終止 `while` 迴圈。  若要在不結束迴圈的情況下跳至下一個反覆項目，請用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式。  請注意，上述三個範例的輸出差異取決於 `int n` 遞增的地方。  下面的範例將不會產生輸出。  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/csharp/while_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [while 陳述式 \(C\+\+\)](/visual-cpp/cpp/while-statement-cpp)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)