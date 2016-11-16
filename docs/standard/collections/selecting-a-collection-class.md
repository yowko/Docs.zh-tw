---
title: "選取集合類別"
description: "選取集合類別"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0a60fca7-e082-48d4-9dda-30b0d3e67ec7
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: f00fedb70bddc184e5c6ea71213b2beb78594792

---

# <a name="selecting-a-collection-class"></a>選取集合類別

請務必謹慎選擇您的集合類別。 使用錯誤的類型可能會限制您使用集合。 由於泛型和並行版本的集合類型較安全，並且提供其他增強功能，因此會優先使用這些版本。 一般而言，除非您特別以 .NET Framework 1.1 版為目標，否則請避免使用 System.Collections 命名空間中的類型。 

請考慮下列問題：

* 您是否需要循序清單，其中的項目通常會在擷取其值之後捨棄？ 

    * 如果是，並且需要先進先出 (FIFO) 行為，請考慮使用 [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) 泛型類別。 如果需要後進先出 (LIFO) 行為，請考慮使用 [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) 泛型類別。 若要從多個執行緒進行安全存取，請使用並行版本 [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) 和 [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1)。
    
    * 如果否，請考慮使用其他集合。
    
* 您是否需要以特定順序 (例如 FIFO、LIFO 或隨機) 存取項目？

    * [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) 或 [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) 泛型類別提供 FIFO 存取。 如需詳細資訊，請參閱[使用安全執行緒集合的時機](threadsafe/when-to-use-a-thread-safe-collection.md)。
    
    * [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) 或 [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 泛型類別提供 LIFO 存取。 如需詳細資訊，請參閱[使用安全執行緒集合的時機](threadsafe/when-to-use-a-thread-safe-collection.md)。
    
    * [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) 泛型類別允許從頭到尾或從尾到頭進行循序存取。
    
* 您是否需要依索引存取每個項目？ 

    * [System.Collections.Specialized.StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) 類別和 [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 泛型類別可以透過元素之以零為起始的索引來存取元素。 
    
    * [System.Collections.Specialized.ListDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.ListDictionary) 和 [System.Collections.Specialized.StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) 類別以及 [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 和 [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 泛型類別可以透過元素的索引鍵來存取元素。
    
    * [System.Collections.Specialized.NameObjectCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameObjectCollectionBase) 和 [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection) 類別以及 [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 和 [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別可以透過元素之以零為起始的索引或索引鍵來存取元素。
    
* 每個項目會包含一個值、一個索引鍵和一個值的組合，還是一個索引鍵和多個值的組合？ 

    * 一個值：根據 [System.Collections.Generic.IList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1) 泛型介面來使用任何集合。
    
    * 一個索引鍵和一個值：根據 [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) 泛型介面來使用任何集合。
    
    * 一個具有內嵌索引鍵的值：使用 [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) 泛型類別。
    
    * 一個索引鍵和多個值：使用 [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection) 類別。
    
* 您是否需要使用與輸入項目不同的順序來排序項目？ 

    * [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 類別會依其雜湊碼來排序其元素。
    
    * [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) 和 [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) 泛型類別會根據 [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) 介面和 [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 泛型介面的實作以透過索引鍵來排序其元素。
    
    * [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 泛型類別，會提供 `Sort` 方法，這個方法接受 `IComparer<T>` 泛型介面的實作作為參數。
    
* 您是否需要只接受字串的集合？ 

    * [StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) (根據 [System.Collections.IList](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)) 和 [StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) (根據 [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)) 位於 [System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized) 命名空間中。 
    
    * 此外，您可以使用 [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 命名空間中的任何泛型集合類別做為強類型字串集合，方法是指定其泛型型別引數的 `String` 類別。
    
## <a name="linq-to-objects"></a>LINQ to Objects

只要物件類型實作 [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) 或 [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1)，LINQ to Objects 就可讓開發人員使用 LINQ 查詢以存取記憶體內的物件。 LINQ 查詢提供一般模式以存取資料，比標準的 foreach 迴圈更精簡、可讀性更高，並提供篩選、排序和群組功能。 如需詳細資訊，請參閱 [Language Integrated Query (LINQ)](../../csharp/linq.md)。

## <a name="see-also"></a>另請參閱

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[安全執行緒集合](threadsafe/index.md)



<!--HONumber=Nov16_HO1-->


