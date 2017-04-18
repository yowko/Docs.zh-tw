---
title: "常用的集合類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "集合 [.NET Framework], 泛型"
  - "集合類別"
  - "泛型集合"
  - "泛型 [.NET Framework], 集合"
  - "群組集合中的資料, 泛型集合類型"
  - "IDictionary 介面, 群組集合中的資料"
  - "IList 介面, 群組集合中的資料"
  - "物件 [.NET Framework], 在集合中群組"
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
caps.latest.revision: 29
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 29
---
# 常用的集合類型
集合類型是資料集合 \(例如雜湊表、佇列、堆疊、封包、字典和清單\) 最常見的一些呈現方式。  
  
 集合取決於 <xref:System.Collections.ICollection> 介面、<xref:System.Collections.IList> 介面、<xref:System.Collections.IDictionary> 介面或其泛型對應項目。  <xref:System.Collections.IList> 介面和 <xref:System.Collections.IDictionary> 介面都衍生自 <xref:System.Collections.ICollection> 介面；因此，所有集合都直接或間接地以 <xref:System.Collections.ICollection> 介面為依據。  在依據 <xref:System.Collections.IList> 介面的集合中 \(例如 <xref:System.Array>、<xref:System.Collections.ArrayList> 或 <xref:System.Collections.Generic.List%601>\) 或直接依據 <xref:System.Collections.ICollection> 介面的集合中 \(例如 <xref:System.Collections.Queue>、<xref:System.Collections.Concurrent.ConcurrentQueue%601>、<xref:System.Collections.Stack>、<xref:System.Collections.Concurrent.ConcurrentStack%601> 或 <xref:System.Collections.Generic.LinkedList%601>\)，每個項目都只包含一個值。  在依據 <xref:System.Collections.IDictionary> 介面的集合中 \(例如 <xref:System.Collections.Hashtable> 和 <xref:System.Collections.SortedList> 類別、<xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Generic.SortedList%602> 泛型類別\)，或 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 類別中，每個項目都包含索引鍵和值。  <xref:System.Collections.ObjectModel.KeyedCollection%602> 類別的獨特之處在於它是將索引鍵內嵌於值的值清單，因此它的行為類似於清單和字典。  
  
 泛型集合是強式類型的最佳解決方案。  不過，如果您的語言不支援泛型，<xref:System.Collections> 命名空間就會包含基底集合，例如 <xref:System.Collections.CollectionBase>、<xref:System.Collections.ReadOnlyCollectionBase> 和 <xref:System.Collections.DictionaryBase>，這些是可以延伸以建立強式類型之集合類別的抽象基底類別。  需要有效率的多執行緒集合存取時，請在 <xref:System.Collections.Concurrent> 命名空間中使用泛型集合。  
  
 集合會視儲存項目、排序項目、執行搜尋以及進行比較等方式，而有所不同。  <xref:System.Collections.Queue> 類別和 <xref:System.Collections.Generic.Queue%601> 泛型類別提供先進先出清單，而 <xref:System.Collections.Stack> 類別和 <xref:System.Collections.Generic.Stack%601> 泛型類別則提供後進先出清單。  <xref:System.Collections.SortedList> 類別和 <xref:System.Collections.Generic.SortedList%602> 泛型類別提供排序版本的 <xref:System.Collections.Hashtable> 類別與 <xref:System.Collections.Generic.Dictionary%602> 泛型類別。  <xref:System.Collections.Hashtable> 或 <xref:System.Collections.Generic.Dictionary%602> 的項目只能依項目的索引鍵加以存取，但 <xref:System.Collections.SortedList> 或 <xref:System.Collections.ObjectModel.KeyedCollection%602> 的項目則可依項目的索引鍵或索引加以存取。  所有集合中的索引都以零起始，<xref:System.Array> 除外，它能允許不是以零起始的陣列。  
  
 只要物件類型實作 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體內的物件。  LINQ 查詢提供一般模式以存取資料，比標準的 `foreach` 迴圈 \(Loop\) 更精簡、可讀性更高，並提供篩選、排序和群組功能。  LINQ 查詢也可以提升效能。  如需詳細資訊，請參閱 [LINQ to Objects](../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-objects.md) 和 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[集合和資料結構](../../../docs/standard/collections/index.md)|討論 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中可用的各種集合類型，包括堆疊、佇列、清單、陣列和字典。|  
|[Hashtable 和 Dictionary 集合類型](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|說明泛型和非泛型雜湊字典類型的功能。|  
|[排序集合類型](../../../docs/standard/collections/sorted-collection-types.md)|說明提供清單和集合之排序功能的類別。|  
|[泛型](../../../docs/standard/generics/index.md)|說明泛型功能，包括 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所提供的泛型集合、委派與介面。  提供 C\#、Visual Basic 和 Visual C\+\+ 功能說明文件的連結，以及支援技術 \(例如反映\) 的連結。|  
  
## 參考資料  
 <xref:System.Collections?displayProperty=fullName>  
  
 <xref:System.Collections.Generic?displayProperty=fullName>  
  
 <xref:System.Collections.ICollection?displayProperty=fullName>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
 <xref:System.Collections.IList?displayProperty=fullName>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
 <xref:System.Collections.IDictionary?displayProperty=fullName>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>