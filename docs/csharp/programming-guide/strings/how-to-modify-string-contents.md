---
title: "如何：修改字串內容 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "字串 [C#], 修改"
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：修改字串內容 (C# 程式設計手冊)
因為字串是「*不可變的*」\(Immutable\)，無法 \(在沒有使用 unsafe 程式碼的情況下\) 在建立字串物件之後修改其值，  但有許多方式可以修改字串值，並將結果儲存至新字串物件。  <xref:System.String?displayProperty=fullName> 類別 \(Class\) 提供可根據輸入字串來操作並傳回新字串物件的方法。  在許多情況下，您都可以將新物件指派給存放原始字串的變數。  <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> 類別可提供運作方式都類似的其他方法。  <xref:System.Text.StringBuilder?displayProperty=fullName> 類別提供可讓您「就地」修改的字元緩衝區。 您可以呼叫 <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> 方法，建立含有目前緩衝區內容的新字串物件。  
  
## 範例  
 在下列範例中，會示範不同的方式，取代或移除指定之字串的子字串。  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## 範例  
 若要使用陣列標記法存取字串的個別字元，您可以使用 <xref:System.Text.StringBuilder> 物件，它會多載 `[]` 運算子以提供對其內部字元緩衝區的存取權。  您還可以使用 <xref:System.String.ToCharArray%2A> 方法，將字串轉換為字元陣列。  下列範例會使用 `ToCharArray` 建立陣列，  然後修改這個陣列中的一些元素，  再呼叫把字元陣列視為輸入參數的字串建構函式 \(Constructor\) 來建立新字串。  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## 範例  
 下列範例是在極少數的情況使用，亦即您可能想要藉由以類似於 C\-Style 字元陣列方式，使用 unsafe 程式碼以就地修改字串。  在這個範例中，會示範如何使用 fixed 關鍵字以「就地」存取個別字元，  還會示範對字串執行不安全的作業時，由於 C\# 編譯器會在內部儲存 \(暫存\) 字串，而可能會產生的一個副作用 \(Side Effect\)。  一般而言，除非有絕對的必要，否則不應使用此技巧。  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)