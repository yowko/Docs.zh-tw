---
title: "如何：在分組作業上執行子查詢 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "分組 LINQ 查詢 [C#]"
  - "群組 [C#], LINQ 查詢運算式"
  - "群組 [C# 中的 LINQ], 子查詢"
  - "查詢 [C# 中的 LINQ], 群組"
  - "查詢 [C# 中的 LINQ], 子查詢"
  - "查詢運算式 [C# 中的 LINQ], 群組"
  - "查詢運算式 [C# 中的 LINQ], 子查詢"
  - "子查詢 [C#]"
ms.assetid: 7b0805cd-53b4-429d-86b6-d37fb08f2c95
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：在分組作業上執行子查詢 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本主題顯示兩個建立查詢的不同方式，將來源資料排序成群組，然後個別對每個群組執行子查詢。  每個範例中的基本技術是使用名為 `newGroup` 的「*接續*」\(Continuation\) 群組來源項目，然後針對 `newGroup` 產生新的子查詢。  此子查詢會針對外部查詢建立的每個新群組執行。  請注意，在此特定範例中最後的輸出不是群組，而是匿名型別的一般序列。  
  
 如需如何群組的詳細資訊，請參閱 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)。  
  
 如需接續的詳細資訊，請參閱 [into](../../../csharp/language-reference/keywords/into.md)。  下列範例使用記憶體中資料結構做為資料來源，但是相同的原則適用任何種類的 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 資料來源。  
  
## 範例  
 [!code-cs[csProgGuideLINQ#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
  
## 編譯程式碼  
 這個範例內含在 [如何：查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) 中的範例應用程式中所定義的物件之參考。  若要編譯和執行這個方法，請將方法貼上至該應用程式中的 `StudentClass` 類別，並加入來自 `Main` 方法的呼叫。  
  
 在配合應用程式調整這個方法時，請注意，LINQ 需要 3.5 版的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，而且專案必須包含 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。  LINQ to SQL、LINQ to XML 和 LINQ to DataSet 型別需要額外的 Using 和參考。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)