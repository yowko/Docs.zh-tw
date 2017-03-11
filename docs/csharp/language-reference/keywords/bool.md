---
title: "bool (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "bool_CSharpKeyword"
  - "bool"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "bool 關鍵字 [C#]"
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# bool (C# 參考)
`bool` 關鍵字是 <xref:System.Boolean?displayProperty=fullName> 的別名。  它是用來宣告儲存布林值 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的變數。  
  
> [!NOTE]
>  如果您需要可以同時具有 `null` 值的布林值變數，請使用 `bool?`。  如需詳細資訊，請參閱 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)。  
  
## 常值  
 您可以將布林值指派給 `bool` 變數。  您也可以將評估為 `bool` 的運算式指派給 `bool` 變數。  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/csharp/bool_1.cs)]  
  
 `bool` 變數的預設值是 `false`。  `bool?` 變數的預設值是 `null`。  
  
## 轉換  
 在 C\+\+ 中，`bool` 型別的值可以轉換成 `int` 型別的值；換句話說，`false` 等於零，而 `true` 則等於非零值。  在 C\# 中，`bool` 型別和其他型別之間不能轉換。  例如，在 C\# 中，下列 `if` 陳述式是無效的：  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/csharp/bool_2.cs)]  
  
 若要測試 `int` 型別的變數，您必須將該變數與另一個值 \(例如零\) 明確地做比較，如下所示：  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/csharp/bool_3.cs)]  
  
## 範例  
 在這個範例中，由鍵盤輸入一個字元後，程式會檢查輸入的字元是否為字母。  如果是字母，將檢查是大寫或小寫。  這些檢查是使用 <xref:System.Char.IsLetter%2A> 和 <xref:System.Char.IsLower%2A> 來執行，這兩者都會傳回 `bool` 型別：  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/csharp/bool_4.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)