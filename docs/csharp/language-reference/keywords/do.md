---
title: "do (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "do_CSharpKeyword"
  - "do"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "do 關鍵字 [C#]"
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# do (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`do` 陳述式會重複執行一個陳述式或一個陳述式區塊，直到指定運算式計算結果變成 `false` 為止。  迴圈的本體必須括在大括弧 `{}` 內，除非它包含單一陳述式。  在這種情況下，大括弧是可選的。  
  
## 範例  
 在下列範例中，只要變數 `x` 小於 5，就會執行 `do-while` 迴圈陳述式。  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 `do-while` 迴圈 \(Loop\) 會在評估條件運算式之前執行一次，與 [while](../../../csharp/language-reference/keywords/while.md) 陳述式不同。  
  
 您可以在 `do-while` 區塊中的任一位置使用 [break](../../../csharp/language-reference/keywords/break.md) 陳述式中斷此迴圈。  您可以使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式直接跳至 `while` 運算式評估陳述式。  如果 `while` 運算式評估為 true，則會從迴圈中的第一個陳述式繼續執行。  如果運算式評估為 false，則從 `do-while` 迴圈之後的第一個陳述式繼續執行。  
  
 `do-while` 迴圈也可以由 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [do\-while 陳述式 \(C\+\+\)](/visual-cpp/cpp/do-while-statement-cpp)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)