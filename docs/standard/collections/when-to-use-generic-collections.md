---
title: "何時使用泛型集合"
description: "何時使用泛型集合"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 971e08bd-b63f-4832-9e61-9f65cbedd352
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bde317c165981775330e1d0d8261d355e2401bc9
ms.lasthandoff: 03/03/2017

---

# <a name="when-to-use-generic-collections"></a>何時使用泛型集合

通常建議使用泛型集合，因為這樣可以得到類型安全的立即好處，而無須衍生自基底集合類型同時實作類型專屬的成員。 當集合元素為實值類型時，泛型集合類型也通常會優於對應的非泛型集合類型 (且優於衍生自非泛型基底集合類型的類型)，因為有了泛型，就不需要對這些元素進行 box。 

當多個執行緒可能同時在新增或移除集合中的項目時，您應該使用 [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中的泛型集合類別。

下列泛型類型對應至現有的集合類型： 

*   [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 是對應至 [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) 的泛型類別。

*   [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 和 [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) 是對應至 [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 的泛型類別。 

*   [Collection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.Collection-1) 是對應至 [CollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase) 的泛型類別。 `Collection<T>` 可以用做為基底類別，但不同於 `CollectionBase`，它並非抽象。 這可讓您更容易使用。

*   [ReadOnlyCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ReadOnlyCollection-1) 是對應至 [ReadOnlyCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase) 的泛型類別。 `ReadOnlyCollection<T>` 一點也不抽象。其具有一個建構函式，可以輕鬆地將現有的 [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 公開成唯讀的集合。

*   [Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1)、[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1)、[Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1)、[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 和 [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別對應至同名的個別非泛型類別。

## <a name="additional-types"></a>其他類型

數個泛型集合類型沒有非泛型的對應項目。 包括下列各項： 

*   [LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) 是提供 O(1) 插入和移除作業的一般用途連結清單。

*   [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 是 O(log n) 插入和擷取作業的已排序字典，這讓它成為 [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 相當實用的替代方法。 

*   [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 是清單與字典之間的混合體，它提供方法來儲存包含自己索引鍵的物件。

*   [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) 會實作具有界限和封鎖功能的集合類別。

*   [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) 提供未排序元素的快速插入和移除。

## <a name="linq-to-objects"></a>LINQ to Objects

只要物件類型實作 [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) 或 [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) 介面，LINQ to Objects 功能可讓您使用 LINQ 查詢來存取記憶體內的物件。 LINQ 查詢提供一般模式以存取資料，比標準的 `foreach` 迴圈 (Loop) 更精簡、可讀性更高，並提供篩選、排序和群組功能。 LINQ 查詢也可以提升效能。

## <a name="additional-functionality"></a>其他功能

某些泛型類型具有非泛型集合類型中找不到的功能。 例如，[List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 類別 (對應至非泛型 [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) 類別) 有許多接受泛型委派的方法，例如 [Predicate&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Predicate-1) 委派 (允許您指定方法來搜尋清單)，以及 [Action&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Action-1) 委派 (代表對清單之每個元素採取動作的方法)。

[List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 類別可讓您指定自己的 [IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 泛型介面實作，以排序及搜尋清單。 [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 和 [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 類別也具有這項功能。 此外，這些類別可讓您在建立集合時，指定比較子。 [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 和 [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 類別會以類似的方式，讓您能指定自己的相等比較子。

## <a name="see-also"></a>另請參閱

[集合與資料結構](index.md) 

[常用的集合類型](commonly-used-collection-types.md)

