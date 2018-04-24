---
title: 何時使用泛型集合
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dcf8dbf3c937fbd2c8a599b60792f15d47f5fe25
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-use-generic-collections"></a><span data-ttu-id="2a02d-102">何時使用泛型集合</span><span class="sxs-lookup"><span data-stu-id="2a02d-102">When to Use Generic Collections</span></span>
<span data-ttu-id="2a02d-103">通常建議使用泛型集合，因為這樣可以得到類型安全的立即好處，而無須衍生自基底集合類型同時實作類型專屬的成員。</span><span class="sxs-lookup"><span data-stu-id="2a02d-103">Using generic collections is generally recommended, because you gain the immediate benefit of type safety without having to derive from a base collection type and implement type-specific members.</span></span> <span data-ttu-id="2a02d-104">當集合元素為實值類型時，泛型集合類型也通常會優於對應的非泛型集合類型 (且優於衍生自非泛型基底集合類型的類型)，因為有了泛型，就不需要對這些元素進行 box。</span><span class="sxs-lookup"><span data-stu-id="2a02d-104">Generic collection types also generally perform better than the corresponding nongeneric collection types (and better than types that are derived from nongeneric base collection types) when the collection elements are value types, because with generics there is no need to box the elements.</span></span>  
  
 <span data-ttu-id="2a02d-105">對於目標為 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 或更新版本的程式，當多個執行緒可能同時在新增或移除集合中的項目時，您應該使用 <xref:System.Collections.Concurrent> 命名空間中的泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-105">For programs that target the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later, you should use the generic collection classes in the <xref:System.Collections.Concurrent> namespace when multiple threads might be adding or removing items from the collection concurrently.</span></span>  
  
 <span data-ttu-id="2a02d-106">下列泛型類型對應至現有的集合類型：</span><span class="sxs-lookup"><span data-stu-id="2a02d-106">The following generic types correspond to existing collection types:</span></span>  
  
-   <span data-ttu-id="2a02d-107"><xref:System.Collections.Generic.List%601> 是對應至 <xref:System.Collections.ArrayList>的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-107"><xref:System.Collections.Generic.List%601> is the generic class that corresponds to <xref:System.Collections.ArrayList>.</span></span>  
  
-   <span data-ttu-id="2a02d-108"><xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是對應至 <xref:System.Collections.Hashtable>的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-108"><xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are the generic classes that correspond to <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="2a02d-109"><xref:System.Collections.ObjectModel.Collection%601> 是對應至 <xref:System.Collections.CollectionBase>的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-109"><xref:System.Collections.ObjectModel.Collection%601> is the generic class that corresponds to <xref:System.Collections.CollectionBase>.</span></span> <span data-ttu-id="2a02d-110"><xref:System.Collections.ObjectModel.Collection%601> 可以用做為基底類別，但不同於 <xref:System.Collections.CollectionBase>，它並非抽象。</span><span class="sxs-lookup"><span data-stu-id="2a02d-110"><xref:System.Collections.ObjectModel.Collection%601> can be used as a base class, but unlike <xref:System.Collections.CollectionBase>, it is not abstract.</span></span> <span data-ttu-id="2a02d-111">這可讓您更容易使用。</span><span class="sxs-lookup"><span data-stu-id="2a02d-111">This makes it much easier to use.</span></span>  
  
-   <span data-ttu-id="2a02d-112"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 是對應至 <xref:System.Collections.ReadOnlyCollectionBase>的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-112"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> is the generic class that corresponds to <xref:System.Collections.ReadOnlyCollectionBase>.</span></span> <span data-ttu-id="2a02d-113"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 並非抽象，且具有一個建構函式，能輕鬆地將現有的 <xref:System.Collections.Generic.List%601> 公開為唯讀的集合。</span><span class="sxs-lookup"><span data-stu-id="2a02d-113"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> is not abstract, and has a constructor that makes it easy to expose an existing <xref:System.Collections.Generic.List%601> as a read-only collection.</span></span>  
  
-   <span data-ttu-id="2a02d-114"><xref:System.Collections.Generic.Queue%601>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601>、 <xref:System.Collections.Generic.Stack%601>、 <xref:System.Collections.Concurrent.ConcurrentStack%601>和 <xref:System.Collections.Generic.SortedList%602> 泛型類別對應至同名的個別非泛型類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-114">The <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, and <xref:System.Collections.Generic.SortedList%602> generic classes correspond to the respective nongeneric classes with the same names.</span></span>  
  
## <a name="additional-types"></a><span data-ttu-id="2a02d-115">其他類型</span><span class="sxs-lookup"><span data-stu-id="2a02d-115">Additional Types</span></span>  
 <span data-ttu-id="2a02d-116">數個泛型集合類型沒有非泛型的對應項目。</span><span class="sxs-lookup"><span data-stu-id="2a02d-116">Several generic collection types do not have nongeneric counterparts.</span></span> <span data-ttu-id="2a02d-117">包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="2a02d-117">They include the following:</span></span>  
  
-   <span data-ttu-id="2a02d-118"><xref:System.Collections.Generic.LinkedList%601> 是提供 O(1) 插入和移除作業的一般用途連結清單。</span><span class="sxs-lookup"><span data-stu-id="2a02d-118"><xref:System.Collections.Generic.LinkedList%601> is a general-purpose linked list that provides O(1) insertion and removal operations.</span></span>  
  
-   <span data-ttu-id="2a02d-119"><xref:System.Collections.Generic.SortedDictionary%602> 是 O(log `n`) 插入和擷取作業的已排序字典，這讓它成為 <xref:System.Collections.Generic.SortedList%602>相當實用的替代方法。</span><span class="sxs-lookup"><span data-stu-id="2a02d-119"><xref:System.Collections.Generic.SortedDictionary%602> is a sorted dictionary with O(log `n`) insertion and retrieval operations, which makes it a useful alternative to <xref:System.Collections.Generic.SortedList%602>.</span></span>  
  
-   <span data-ttu-id="2a02d-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> 是清單與字典之間的混合體，它提供方法來儲存包含自己索引鍵的物件。</span><span class="sxs-lookup"><span data-stu-id="2a02d-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> is a hybrid between a list and a dictionary, which provides a way to store objects that contain their own keys.</span></span>  
  
-   <span data-ttu-id="2a02d-121"><xref:System.Collections.Concurrent.BlockingCollection%601> 會實作具有週框和封鎖功能的集合類別。</span><span class="sxs-lookup"><span data-stu-id="2a02d-121"><xref:System.Collections.Concurrent.BlockingCollection%601> implements a collection class with bounding and blocking functionality.</span></span>  
  
-   <span data-ttu-id="2a02d-122"><xref:System.Collections.Concurrent.ConcurrentBag%601> 提供未排序項目的快速插入和移除。</span><span class="sxs-lookup"><span data-stu-id="2a02d-122"><xref:System.Collections.Concurrent.ConcurrentBag%601> provides fast insertion and removal of unordered elements.</span></span>  
  
## <a name="linq-to-objects"></a><span data-ttu-id="2a02d-123">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="2a02d-123">LINQ to Objects</span></span>  
 <span data-ttu-id="2a02d-124">只要物件類型實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體中的物件。</span><span class="sxs-lookup"><span data-stu-id="2a02d-124">The LINQ to Objects feature enables you to use LINQ queries to access in-memory objects as long as the object type implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="2a02d-125">LINQ 查詢提供一般模式以存取資料，比標準的 `foreach` 迴圈 (Loop) 更精簡、可讀性更高，並提供篩選、排序和群組功能。</span><span class="sxs-lookup"><span data-stu-id="2a02d-125">LINQ queries provide a common pattern for accessing data; are typically more concise and readable than standard `foreach` loops; and provide filtering, ordering and grouping capabilities.</span></span> <span data-ttu-id="2a02d-126">LINQ 查詢也可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="2a02d-126">LINQ queries can also improve performance.</span></span> <span data-ttu-id="2a02d-127">如需詳細資訊，請參閱 [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) 與 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="2a02d-127">For more information, see [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) and [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="additional-functionality"></a><span data-ttu-id="2a02d-128">其他功能</span><span class="sxs-lookup"><span data-stu-id="2a02d-128">Additional Functionality</span></span>  
 <span data-ttu-id="2a02d-129">某些泛型類型具有非泛型集合類型中找不到的功能。</span><span class="sxs-lookup"><span data-stu-id="2a02d-129">Some of the generic types have functionality that is not found in the nongeneric collection types.</span></span> <span data-ttu-id="2a02d-130">例如， <xref:System.Collections.Generic.List%601> 類別 (對應至非泛型 <xref:System.Collections.ArrayList> 類別) 有許多接受泛型委派的方法，例如 <xref:System.Predicate%601> 委派 (允許您指定方法來搜尋清單)、 <xref:System.Action%601> 委派 (代表對清單每個項目採取動作的方法)，以及 <xref:System.Converter%602> 委派 (可定義類型之間的轉換)。</span><span class="sxs-lookup"><span data-stu-id="2a02d-130">For example, the <xref:System.Collections.Generic.List%601> class, which corresponds to the nongeneric <xref:System.Collections.ArrayList> class, has a number of methods that accept generic delegates, such as the <xref:System.Predicate%601> delegate that allows you to specify methods for searching the list, the <xref:System.Action%601> delegate that represents methods that act on each element of the list, and the <xref:System.Converter%602> delegate that lets you define conversions between types.</span></span>  
  
 <span data-ttu-id="2a02d-131"><xref:System.Collections.Generic.List%601> 類別可讓您指定自己的 <xref:System.Collections.Generic.IComparer%601> 泛型介面實作，以排序及搜尋清單。</span><span class="sxs-lookup"><span data-stu-id="2a02d-131">The <xref:System.Collections.Generic.List%601> class allows you to specify your own <xref:System.Collections.Generic.IComparer%601> generic interface implementations for sorting and searching the list.</span></span> <span data-ttu-id="2a02d-132"><xref:System.Collections.Generic.SortedDictionary%602> 和 <xref:System.Collections.Generic.SortedList%602> 類別也具有這項功能。</span><span class="sxs-lookup"><span data-stu-id="2a02d-132">The <xref:System.Collections.Generic.SortedDictionary%602> and <xref:System.Collections.Generic.SortedList%602> classes also have this capability.</span></span> <span data-ttu-id="2a02d-133">此外，這些類別可讓您在建立集合時，指定比較子。</span><span class="sxs-lookup"><span data-stu-id="2a02d-133">In addition, these classes let you specify comparers when the collection is created.</span></span> <span data-ttu-id="2a02d-134"><xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> 類別會以類似的方式，讓您能指定自己的相等比較子。</span><span class="sxs-lookup"><span data-stu-id="2a02d-134">In similar fashion, the <xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.ObjectModel.KeyedCollection%602> classes let you specify your own equality comparers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a02d-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a02d-135">See Also</span></span>  
 [<span data-ttu-id="2a02d-136">集合和資料結構</span><span class="sxs-lookup"><span data-stu-id="2a02d-136">Collections and Data Structures</span></span>](../../../docs/standard/collections/index.md)  
 [<span data-ttu-id="2a02d-137">常用的集合類型</span><span class="sxs-lookup"><span data-stu-id="2a02d-137">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)  
 [<span data-ttu-id="2a02d-138">泛型</span><span class="sxs-lookup"><span data-stu-id="2a02d-138">Generics</span></span>](../../../docs/standard/generics/index.md)
