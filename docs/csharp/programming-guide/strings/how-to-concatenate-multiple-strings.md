---
title: "如何：串連多個字串 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "串連字串 [C#]"
  - "聯結字串 [C#]"
  - "字串 [C#], 串連"
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 如何：串連多個字串 (C# 程式設計手冊)
「*串連*」\(Concatenation\) 是將某一個字串附加至另一個字串結尾的程序。  使用 `+` 運算子串連字串常值 \(String Literal\) 或字串常數時，編譯器會建立單一字串。  執行階段不會發生串連作業，  但只有在執行階段才可以串連字串變數。  針對此種案例，您應該要了解各種方式的效能含意。  
  
## 範例  
 在下列範例中，會示範如何將長字串常值分割成較小字串，以增加原始程式碼的易讀性。  在編譯時期，這些分割部分將串連成單一字串。  不管包含多少字串，都不會耗用任何執行階段效能。  
  
 [!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#30)]  
  
## 範例  
 若要串連字串變數，您可以使用 `+` 或 `+=` 運算子，或是 <xref:System.String.Concat%2A?displayProperty=fullName>、<xref:System.String.Format%2A?displayProperty=fullName> 或 <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> 方法。  `+` 運算子很容易使用，有利於程式撰寫人員按照直覺來撰寫程式碼。  即使您在一個陳述式中使用數個 \+ 運算子，字串內容仍只會複製一次。  但如果您多次重複執行這種運算 \(例如在迴圈中\)，則可能會造成效率問題。  例如，請注意下列程式碼：  
  
 [!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#23)]  
  
> [!NOTE]
>  在字串的串連作業中，C\# 編譯器會將 null 字串視為與空字串相同，但不會轉換原始 null 字串的值。  
  
 如果不是串連大量的字串 \(例如在迴圈中\)，執行這個程式碼所耗用的效能可能不值得一提。  對 <xref:System.String.Concat%2A?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName> 方法來說，這同樣是成立的。  
  
 不過，當效能很重要時，一定要使用 <xref:System.Text.StringBuilder> 類別 \(Class\) 來串連字串。  下列程式碼會使用 <xref:System.Text.StringBuilder> 類別的 <xref:System.Text.StringBuilder.Append%2A> 方法來串連字串，並沒有 `+` 運算子的鏈結效果。  
  
 [!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#22)]  
  
## 請參閱  
 <xref:System.String>   
 <xref:System.Text.StringBuilder>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)