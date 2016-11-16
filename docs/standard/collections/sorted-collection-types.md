---
title: "排序集合類型"
description: "排序集合類型"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc9c13e-e56a-433b-a293-c92364f6e9cb
translationtype: Human Translation
ms.sourcegitcommit: 149086110d7470d97e1ab3e5969269626290b523
ms.openlocfilehash: a5f6e2ef7f765dccf1fee0e2de60dea8aec003b9

---

# <a name="sorted-collection-types"></a>排序集合類型  
 
 [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) 類別、[System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別和 [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 泛型類別與 [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 類別和 [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 泛型類別的類似處在於實作 [IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) 介面，但它們會透過索引鍵依排序順序維護其元素，而且沒有雜湊表的 O(1) 插入和擷取特性。 三個類別有數個共用功能︰  

 *   所有三個類別都會實作 [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) 介面。 兩個泛型類別也會實作 [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) 泛型介面。  
 
 *   每個元素都是進行列舉的索引鍵/值組。   
  
> [!NOTE]  
> 雖然兩個泛型類型會傳回 [KeyValuePair&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.KeyValuePair-2) 物件，但是非泛型 [SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) 類別會在列舉時傳回 [DictionaryEntry](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryEntry) 物件。  
   
*   元素的排序根據是 [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) 實作 (適用於非泛型 `SortedList`) 或 [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 實作 (適用於兩個泛型類別)。  
   
 *   每個類別都會提供傳回集合的屬性，而這個集合僅包含索引鍵或僅包含值。  
   
下表列出兩個已排序清單類別與 [SortedDictionary<TKey, TValue>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 類別之間的部分差異。  
   
 `SortedList`泛型類別與 `SortedList<TKey, TValue>` 泛型類別 | `SortedDictionary<TKey, TValue>`泛型類別  
 --------------------------------------------------------------------------------- | ------------------------------  
 對傳回索引鍵和值的屬性進行編製索引，以進行有效率的索引擷取。 | 無索引擷取。  
 擷取是 O(log n)。 | 擷取是 O(log n)。  
 插入和移除一般是 O(n)；不過，對於已處於排序順序的資料，插入是 O(1) ，因此每個元素都會新增至清單的結尾 (這假設不需要調整大小)。 | 插入和移除是 O(log n)。  
 使用的記憶體少於 `SortedDictionary<TKey, TValue>`。 | 使用的記憶體多於 `SortedList` 非泛型類別和 `SortedList<TKey, TValue>` 泛型類別。  
  
 針對必須可以從多個執行緒同時存取的已排序清單或字典，您可以將排序邏輯新增至衍生自 [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) 的類別。  
  
 > [!NOTE]  
 > 針對包含專屬索引鍵的值 (例如，包含員工識別碼的員工記錄)，您可以建立索引鍵集合，而索引鍵集合透過衍生自 [KeyedCollection&lt;TKey, TItem&gt;]() 泛型類別而具有部分清單特性和部分字典特性。  
   
 [SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) 類別會提供自我平衡樹狀目錄，以在插入、刪除和搜尋之後依排序順序維護資料。 這個類別和 [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) 類別會實作 [ISet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ISet-1) 介面。  
   
## <a name="see-also"></a>另請參閱  
  
[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)  
   
[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)  
   
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)  
 
[常用的集合類型](commonly-used-collection-types.md) 



<!--HONumber=Nov16_HO1-->


