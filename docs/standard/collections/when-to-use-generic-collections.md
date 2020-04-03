---
title: 何時使用泛型集合
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: bbf8ec7f61981332b6984488b369fee62959b92a
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635892"
---
# <a name="when-to-use-generic-collections"></a>何時使用泛型集合

使用泛型集合可自動利用類型安全,而無需從基集合類型派生並實現特定於類型的成員。 當集合元素為值類型時,泛型集合類型通常也比相應的非泛型集合類型(優於從非泛型基集合類型派生的類型更好),因為使用泛型,無需為元素添加框。  
  
 對於目標為 .NET Framework 4 或更新版本的程式，當多個執行緒可能同時在新增或移除集合中的項目時，您應該使用 <xref:System.Collections.Concurrent> 命名空間中的泛型集合類別。  
  
 下列泛型類型對應至現有的集合類型：  
  
- <xref:System.Collections.Generic.List%601> 是對應至 <xref:System.Collections.ArrayList>的泛型類別。  
  
- <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是對應至 <xref:System.Collections.Hashtable>的泛型類別。  
  
- <xref:System.Collections.ObjectModel.Collection%601> 是對應至 <xref:System.Collections.CollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.Collection%601>可用作基類,但與不同<xref:System.Collections.CollectionBase>,它不是抽象的,這使得它更易於使用。  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 是對應至 <xref:System.Collections.ReadOnlyCollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 並非抽象，且具有一個建構函式，能輕鬆地將現有的 <xref:System.Collections.Generic.List%601> 公開為唯讀的集合。  
  
- <xref:System.Collections.Generic.Queue%601>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601>、 <xref:System.Collections.Generic.Stack%601>、 <xref:System.Collections.Concurrent.ConcurrentStack%601>和 <xref:System.Collections.Generic.SortedList%602> 泛型類別對應至同名的個別非泛型類別。  
  
## <a name="additional-types"></a>其他類型  
 數個泛型集合類型沒有非泛型的對應項目。 其中包括：  
  
- <xref:System.Collections.Generic.LinkedList%601> 是提供 O(1) 插入和移除作業的一般用途連結清單。  
  
- <xref:System.Collections.Generic.SortedDictionary%602> 是 O(log `n`) 插入和擷取作業的已排序字典，這讓它成為 <xref:System.Collections.Generic.SortedList%602>相當實用的替代方法。  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602> 是清單與字典之間的混合體，它提供方法來儲存包含自己索引鍵的物件。  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> 會實作具有週框和封鎖功能的集合類別。  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> 提供未排序項目的快速插入和移除。  
  
## <a name="linq-to-objects"></a>LINQ to Objects  
 只要物件類型實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體中的物件。 LINQ 查詢提供了訪問數據的常見模式;通常比標準`foreach`迴圈更簡潔、更可讀;並提供篩選、排序和分組功能。 LINQ 查詢也可以提升效能。 如需詳細資訊，請參閱 [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md)、[LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) 和 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)。  
  
## <a name="additional-functionality"></a>其他功能  
 某些泛型類型具有非泛型集合類型中找不到的功能。 例如， <xref:System.Collections.Generic.List%601> 類別 (對應至非泛型 <xref:System.Collections.ArrayList> 類別) 有許多接受泛型委派的方法，例如 <xref:System.Predicate%601> 委派 (允許您指定方法來搜尋清單)、 <xref:System.Action%601> 委派 (代表對清單每個項目採取動作的方法)，以及 <xref:System.Converter%602> 委派 (可定義類型之間的轉換)。  
  
 <xref:System.Collections.Generic.List%601> 類別可讓您指定自己的 <xref:System.Collections.Generic.IComparer%601> 泛型介面實作，以排序及搜尋清單。 <xref:System.Collections.Generic.SortedDictionary%602> 和 <xref:System.Collections.Generic.SortedList%602> 類別也具有這項功能。 此外，這些類別可讓您在建立集合時，指定比較子。 <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> 類別會以類似的方式，讓您能指定自己的相等比較子。  
  
## <a name="see-also"></a>另請參閱

- [集合和資料結構](../../../docs/standard/collections/index.md)
- [常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)
- [泛型](../../../docs/standard/generics/index.md)
