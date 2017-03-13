---
title: "如何：使用 String.Split 剖析字串 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "分割字串 [C#]"
  - "Split 方法 [C#]"
  - "字串 [C#], 分割"
  - "剖析字串"
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 如何：使用 String.Split 剖析字串 (C# 程式設計手冊)
下列程式碼範例示範如何使用 <xref:System.String.Split%2A?displayProperty=fullName> 方法剖析字串。 當輸入時，<xref:System.String.Split%2A> 會採用字元陣列以表示用來分隔目標字串之有趣子字串的字元。  該函式會傳回子字串的陣列。  
  
 這個範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。  目標字串句子中的每個文字都會使用字串結果陣列來個別顯示。  
  
## 範例  
 [!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## 範例  
 根據預設，當目標字串中連續出現兩個分隔字元時，String.Split 會傳回空字串。  您可以傳遞選擇性 StringSplitOptions.RemoveEmptyEntries 參數，以排除輸出中的任何空字串。  
  
 String.Split 可採用字串陣列 \(做為分隔符號以剖析目標字串的字元序列，而不是單一字元\)。  
  
```c#  
class TestStringSplit { static void Main() { char[] separatingChars = { "<<", "..." }; string text = "one<<two......three<four"; System.Console.WriteLine("Original text: '{0}'", text); string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries ); System.Console.WriteLine("{0} substrings in text:", words.Length); foreach (string s in words) { System.Console.WriteLine(s); } // Keep the console window open in debug mode. System.Console.WriteLine("Press any key to exit."); System.Console.ReadKey(); } } /* Output: Original text: 'one<<two......three<four' 3 words in text: one two three<four */  
  
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)