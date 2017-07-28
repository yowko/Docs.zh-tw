---
title: "何時使用泛型集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 465939bca9e0300300efef9842f312800817a5cc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="when-to-use-generic-collections"></a>何時使用泛型集合
通常建議使用泛型集合，因為這樣可以得到類型安全的立即好處，而無須衍生自基底集合類型同時實作類型專屬的成員。 當集合元素為實值類型時，泛型集合類型也通常會優於對應的非泛型集合類型 (且優於衍生自非泛型基底集合類型的類型)，因為有了泛型，就不需要對這些元素進行 box。  
  
 對於目標為 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 或更新版本的程式，當多個執行緒可能同時在新增或移除集合中的項目時，您應該使用 <xref:System.Collections.Concurrent> 命名空間中的泛型集合類別。  
  
 下列泛型類型對應至現有的集合類型：  
  
-   <xref:System.Collections.Generic.List%601> 是對應至 <xref:System.Collections.ArrayList>的泛型類別。  
  
-   <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是對應至 <xref:System.Collections.Hashtable>的泛型類別。  
  
-   <xref:System.Collections.ObjectModel.Collection%601> 是對應至 <xref:System.Collections.CollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.Collection%601> 可以用做為基底類別，但不同於 <xref:System.Collections.CollectionBase>，它並非抽象。 這可讓您更容易使用。  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 是對應至 <xref:System.Collections.ReadOnlyCollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 並非抽象，且具有一個建構函式，能輕鬆地將現有的 <xref:System.Collections.Generic.List%601> 公開為唯讀的集合。  
  
-   <xref:System.Collections.Generic.Queue%601>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601>、 <xref:System.Collections.Generic.Stack%601>、 <xref:System.Collections.Concurrent.ConcurrentStack%601>和 <xref:System.Collections.Generic.SortedList%602> 泛型類別對應至同名的個別非泛型類別。  
  
## <a name="additional-types"></a>其他類型  
 數個泛型集合類型沒有非泛型的對應項目。 包括下列各項：  
  
-   <xref:System.Collections.Generic.LinkedList%601> 是提供 O(1) 插入和移除作業的一般用途連結清單。  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> 是 O(log `n`) 插入和擷取作業的已排序字典，這讓它成為 <xref:System.Collections.Generic.SortedList%602>相當實用的替代方法。  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> 是清單與字典之間的混合體，它提供方法來儲存包含自己索引鍵的物件。  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> 會實作具有週框和封鎖功能的集合類別。  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> 提供未排序項目的快速插入和移除。  
  
## <a name="linq-to-objects"></a>LINQ to Objects  
 只要物件類型實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體中的物件。 LINQ 查詢提供一般模式以存取資料，比標準的 `foreach` 迴圈 (Loop) 更精簡、可讀性更高，並提供篩選、排序和群組功能。 LINQ 查詢也可以提升效能。 如需詳細資訊，請參閱 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) 與 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## <a name="additional-functionality"></a>其他功能  
 某些泛型類型具有非泛型集合類型中找不到的功能。 例如， <xref:System.Collections.Generic.List%601> 類別 (對應至非泛型 <xref:System.Collections.ArrayList> 類別) 有許多接受泛型委派的方法，例如 <xref:System.Predicate%601> 委派 (允許您指定方法來搜尋清單)、 <xref:System.Action%601> 委派 (代表對清單每個項目採取動作的方法)，以及 <xref:System.Converter%602> 委派 (可定義類型之間的轉換)。  
  
 <xref:System.Collections.Generic.List%601> 類別可讓您指定自己的 <xref:System.Collections.Generic.IComparer%601> 泛型介面實作，以排序及搜尋清單。 <xref:System.Collections.Generic.SortedDictionary%602> 和 <xref:System.Collections.Generic.SortedList%602> 類別也具有這項功能。 此外，這些類別可讓您在建立集合時，指定比較子。 <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> 類別會以類似的方式，讓您能指定自己的相等比較子。  
  
## <a name="see-also"></a>另請參閱  
 [集合和資料結構](../../../docs/standard/collections/index.md)   
 [常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)   
 [泛型](../../../docs/standard/generics/index.md)

