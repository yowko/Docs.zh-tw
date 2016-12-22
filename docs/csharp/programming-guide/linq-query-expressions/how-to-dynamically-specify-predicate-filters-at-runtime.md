---
title: "如何：在執行階段動態指定述詞篩選條件 (C# 程式設計手冊) | Microsoft Docs"
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
  - "動態查詢 [C# 中的 LINQ]"
  - "述詞篩選條件 [C#]"
  - "述詞 [C#]"
  - "查詢 [C# 中的 LINQ], 述詞篩選條件"
  - "查詢運算式 [C# 中的 LINQ], 述詞篩選條件"
ms.assetid: 52f2dc7a-8353-4c6e-98d3-eec99a907a5f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：在執行階段動態指定述詞篩選條件 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在某些情況下，在執行階段之前您不知道必須將多少述詞套用至 `where` 子句中的來源項目。  動態指定多個述詞篩選條件的一個方法是使用 <xref:System.Linq.Enumerable.Contains%2A> 方法，如下列範例所示。  本範例是以兩種方式建構：  首先，藉由篩選程式中提供的值來執行專案。  接著，使用在執行階段提供的輸入再次執行專案。  
  
### 若要使用 Contains 方法進行篩選  
  
1.  在 Visual Studio 中開啟新的主控台應用程式。  將它命名為 `PredicateFilters`。  
  
2.  複製 [如何：查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)中的 `StudentClass` 類別並將它複製到 `Program` 類別之下的 `PredicateFilters` 命名空間中。  `StudentClass` 會提供 `Student` 物件清單。  
  
3.  將 `StudentClass` 中的 `Main` 方法標記為註解。  
  
4.  將 `Program` 類別替換成下列程式碼。  
  
     [!code-cs[csProgGuideLINQ#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  在 `ids` 的宣告之下，將下列程式碼行加入至 `DynamicPredicates` 類別中的 `Main` 方法。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
6.  按 F5 執行專案。  
  
7.  下列輸出會顯示在 \[命令提示字元\] 視窗中：  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  下一個步驟是再次執行專案，這一次請藉由使用在執行階段提供的輸入而非 `ids` 陣列。  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**PredicateFilters**\]，然後按一下 \[**屬性**\]。  
  
9. 按一下 \[**偵錯**\] 索引標籤。  
  
10. 在 \[**命令列引數**\] 視窗中，輸入 122、117、120 和 115 並以空白字元分隔：`122 117 120 115`。  執行專案時，這些值會變成 `args` 的項目、`Main` 方法的參數。  
  
11. 在 `Main` 方法中，將 `QueryByID(ids)` 變更為 `QueryByID(args)`。  
  
12. 按 F5 執行專案。  
  
13. 下列輸出會顯示在 \[命令提示字元\] 視窗中：  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
### 若要使用 switch 陳述式進行篩選  
  
1.  您可以使用 `switch` 陳述式，在預先決定的替代查詢中進行選取。  在下列範例中，根據在執行階段指定的年級，`studentQuery` 會使用不同的 `where` 子句。  
  
2.  複製下列方法並將它貼入至 `DynamicPredicates` 類別中。  
  
     [!code-cs[csProgGuideLINQ#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  在 \[**命令列引數**\] 視窗中，使用介於 1 和 4 之間的整數值取代上一個程序中的 ID 編號。  
  
4.  在 `Main` 方法中，使用下列呼叫取代對 `QueryByID` 的呼叫，以傳送 `args` 陣列中的第一個項目做為其引數：`QueryByYear(args[0])`。  
  
5.  按 F5 執行專案。  
  
### 若要在自己的應用程式中使用這個方法  
  
-   在配合自己的應用程式調整這個方法時，請記得 LINQ 需要 3.5 或 4 版的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，而且專案必須包含 System.Core.dll 的參考以及 `System.Linq` 的 `using` 指示詞。  LINQ to SQL、LINQ to XML 和 LINQ to DataSet 型別都需要額外的 `using` 指示詞和參考。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)