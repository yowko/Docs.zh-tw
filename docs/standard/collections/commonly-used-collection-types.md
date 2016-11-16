---
title: "常用的集合類型"
description: "常用的集合類型"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 55861611-1e40-4cc2-9ec5-0b2df4ba6c0c
translationtype: Human Translation
ms.sourcegitcommit: d4e7ef84480aa9f735fb8d1ff03c9e8a61127c83
ms.openlocfilehash: 063e43b156771ba0db7c6b8ef5823330a4405c2c

---

# <a name="commonly-used-collection-types"></a>常用的集合類型

集合類型是資料集合 (例如雜湊表、佇列、堆疊、封包、字典和清單) 最常見的一些呈現方式。

集合取決於 [`ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) 介面、[`IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList) 介面、[`IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) 介面或其泛型對應項目。 `IList` 介面和 `IDictionary` 介面都衍生自 `ICollection` 介面；因此，所有集合都直接或間接地以 `ICollection` 介面為依據。 在依據 `IList` 介面的集合中 (例如 [`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array)、[`ArrayList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) 或 [`List<T>)`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)) 或直接依據 `ICollection` 介面的集合中 (例如 [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)、[`ConcurrentQueue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1)、[`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)、[`ConcurrentStack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 或 [`LinkedList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1))，每個元素都只包含一個值。 在依據 `IDictionary` 介面的集合中 (例如 [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 和 [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) 類別、[`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 和 [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別)，或 [`ConcurrentDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) 類別中，每個元素都包含索引鍵和值。 [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 類別的獨特之處在於它是將索引鍵內嵌於值的值清單，因此它的行為類似於清單和字典。

泛型集合是強式類型的最佳解決方案。 不過，如果您的語言不支援泛型，[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections) 命名空間就會包含基底集合，例如 [`CollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase)、[`ReadOnlyCollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase) 和 [`DictionaryBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryBase)，這些是可以延伸以建立強式類型之集合類別的抽象基底類別。 需要有效率的多執行緒集合存取時，請在 [`System.Collections.Concurrent`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中使用泛型集合。

集合會視儲存項目、排序項目、執行搜尋以及進行比較等方式，而有所不同。 [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue) 類別和 [`Queue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) 泛型類別提供先進先出清單，而 [`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack) 類別和 [`Stack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) 泛型類別則提供後進先出清單。 [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) 類別和 [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別提供排序版本的 [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 類別與 [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 泛型類別。 `Hashtable` 或 `Dictionary<TKey, TValue>` 的元素只能依元素的索引鍵加以存取，但 `SortedList` 或 [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 的元素則可依元素的索引鍵或索引加以存取。 所有集合中的索引都以零起始，[`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array) 除外，它能允許不是以零起始的陣列。

只要物件類型實作 [`IEnumerable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) 或 [`IEnumerable<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體內的物件。 LINQ 查詢提供一般模式以存取資料，比標準的 foreach 迴圈更精簡、可讀性更高，並提供篩選、排序和群組功能。 LINQ 查詢也可以提升效能。

## <a name="related-topics"></a>相關主題

標題 | 描述
----- | -----------
[`Collections and Data Structures`](index.md) | 討論 .NET Framework 中可用的各種集合類型，包括堆疊、佇列、清單、陣列和字典。
[`Hashtable and Dictionary Collection Types`](hashtable-and-dictionary-collection-types.md) | 說明泛型和非泛型雜湊字典類型的功能。
[`Sorted Collection Types`](sorted-collection-types.md) | 描述經過排序之集合的效能與特性。

## <a name="reference"></a>參考資料

[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[`System.Collections.Generic`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[`System.Collections.ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection)

[`System.Collections.Generic.ICollection<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1)

[`System.Collections.IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)

[`System.Collections.Generic.IList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1)

[`System.Collections.IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[`System.Collections.Generic.IDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[`System.Linq`](https://docs.microsoft.com/dotnet/core/api/System.Linq)



<!--HONumber=Nov16_HO1-->


