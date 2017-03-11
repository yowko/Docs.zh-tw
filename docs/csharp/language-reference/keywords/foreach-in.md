---
title: "foreach、in (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "foreach"
  - "foreach_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "foreach 關鍵字 [C#]"
  - "foreach 陳述式 [C#]"
  - "in 關鍵字 [C#]"
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# foreach、in (C# 參考)
對於在陣列或物件集合中實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面的每個項目，`foreach` 陳述式會重複內嵌陳述式群組。  `foreach` 陳述式是用來逐一查看集合，以取得所需的資訊，但是不能用來加入或移除來源集合的項目，以避免無法預期的副作用。  如果您必須加入或移除來源集合的項目，請使用 [for](../../../csharp/language-reference/keywords/for.md) 迴圈。  
  
 內嵌陳述式繼續執行在陣列或集合中的每個項目。  反覆查看項目完成在集合中的所有項目之後，程式控制權會轉移到 `foreach` 區塊之後的下一個陳述式。  
  
 您可以在 `foreach` 區塊內的任一位置使用 [break](../../../csharp/language-reference/keywords/break.md) 關鍵字中斷迴圈，或使用 [continue](../../../csharp/language-reference/keywords/continue.md) 關鍵字跳至迴圈內的下一個反覆運算。  
  
 `foreach` 迴圈也可以由 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束。  
  
 如需 `foreach` 關鍵字及其程式碼範例的詳細資訊，請參閱下列主題：  
  
 [搭配陣列使用 foreach](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [如何：使用 foreach 存取集合類別](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## 範例  
 下列程式碼顯示三個範例：  
  
-   一般的 `foreach` 迴圈，會顯示整數陣列的內容  
  
-   [for](../../../csharp/language-reference/keywords/for.md) 迴圈會執行相同動作  
  
-   `foreach` 迴圈會保持陣列中的項目數  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/csharp/foreach-in_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)