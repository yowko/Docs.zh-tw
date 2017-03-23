---
title: "into (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "into_CSharpKeyword"
  - "into"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "into 關鍵字 [C#]"
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# into (C# 參考)
`into` 內容關鍵字可以用於建立暫時識別項，將 [group](../../../csharp/language-reference/keywords/group-clause.md)、[join](../../../csharp/language-reference/keywords/join-clause.md) 或 [select](../../../csharp/language-reference/keywords/select-clause.md) 子句的結果儲存至新的識別項。  此識別項本身可以是額外查詢命令的產生器。  在 `group` 或 `select` 子句中使用時，使用新識別項有時會視為「*接續*」\(Continuation\)。  
  
## 範例  
 下列範例顯示使用 `into` 關鍵字啟用暫時識別項 `fruitGroup`，其具有推斷型別 `IGrouping`。  使用識別項時，您就可以在每個群組上叫用 <xref:System.Linq.Enumerable.Count%2A> 方法，並且只選取包含兩個或多個文字的群組。  
  
 [!code-cs[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 只有當您要在每個群組上執行額外查詢作業時，才需要在 `group` 子句中使用 `into`。  如需詳細資訊，請參閱 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)。  
  
 如需在 `join` 子句中使用`into` 的範例，請參閱 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)。  
  
## 請參閱  
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)