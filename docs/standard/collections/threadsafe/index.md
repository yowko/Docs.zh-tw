---
title: "安全執行緒集合"
description: "安全執行緒集合"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 92d5515d-f5d6-4a09-8bbb-31865d678643
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: 421d46585b5d83f5772fa6596ad581c8c6acbf71

---

# <a name="threadsafe-collections"></a>安全執行緒集合

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)命名空間包含數個具備安全執行緒且可擴充的集合類別。 多個執行緒可以安全且有效率地新增或移除這些集合中的項目，而不需要利用使用者程式碼進行額外同步處理。 當您撰寫新的程式碼時，只要集合同時寫入多個執行緒，就使用並行集合類別。 如果您僅讀取共用集合，則可以使用 [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 命名空間中的類別。 除非您需要將目標設為 .NET Framework 1.1 或舊版本的執行階段，否則建議您不要使用 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 集合類別。

## <a name="finegrained-locking-and-lockfree-mechanisms"></a>更細緻的鎖定和無鎖定機制

有些並行集合類型會使用輕量型同步處理機制 (例如 [SpinLock](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinLock)、[SpinWait](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinWait)、[SemaphoreSlim](https://docs.microsoft.com/dotnet/core/api/System.Threading.SemaphoreSlim) 和 [CountdownEvent](https://docs.microsoft.com/dotnet/core/api/System.Threading.CountdownEvent))。 這些同步處理類型一般會先使用短期間的忙碌旋轉，再讓執行緒進入真正 `Wait` 狀態。 預期等候時間很短時，旋轉的費用遠低於等待，這包含昂貴的核心轉換。 針對使用旋轉的集合類別，這個效率表示多個執行緒可以使用極高的速率來新增和移除項目。

[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) 和 [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 類別根本不會使用鎖定。 相反地，它們依賴連鎖作業來達成執行緒安全。

> [!NOTE]
> 因為並行集合類別支援 [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection)，所以會提供 `IsSynchronized` 和 `SyncRoot` 屬性的實作，即使這些屬性無關也是一樣。 `SyncRoot` 一律會傳回 `IsSynchronized`，而 `false` 一律為 null。

下表列出 [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中的集合類型。

類型 | 說明
---- | -----------
[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) | 提供任何可實作 [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) 之類型的界限和封鎖功能。 如需詳細資訊，請參閱 [BlockingCollection 概觀](blockingcollection-overview.md)。
[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) | 未排序元素集合的安全執行緒實作。
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) | 索引鍵/值組字典的安全執行緒實作。
[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) | FIFO (先進先出) 佇列的安全執行緒實作。
[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) | LIFO (後進先出) 堆疊的安全執行緒實作。
[IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) | 類型必須實作以在 `BlockingCollection` 中使用的介面。

## <a name="thread-synchronization-in-the-net-framework-version-10-and-20-collections"></a>.NET Framework 1.0 和 2.0 版集合中的執行緒同步處理

集合是在 .NET Framework 1.0 版首次引進，並位在 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 命名空間中。 這些包括常用 [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) 和 [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 的集合透過 `Synchronized` 屬性提供某種安全執行緒，而這個屬性會傳回集合的安全執行緒包裝函式。 包裝函式的運作方式是針對每個新增或移除作業鎖定整個集合。 因此，嘗試存取集合的每個執行緒都必須等待，直到輪到它取得一個鎖定。 這無法進行擴充，而且可能會造成大型集合的重大效能下降。 此外，設計未完全保護競爭情形。 

集合類別是在 .NET Framework 2.0 版首次引進，並位在 [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 命名空間中。 這些包含 [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)、[Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 等。 這些類別提供 `System.Collections` 類別的改良類型安全和效能。 不過，`System.Collections.Generic` 集合類別不會提供任何執行緒同步處理；在多個執行緒上同時新增或移除項目時，使用者程式碼必須提供所有同步處理。

建議使用 `System.Collections.Concurrent` 集合類別，原因是它們不僅提供 `System.Collections.Generic` 集合類別的型別安全，而且效率和安全執行緒也會比 `System.Collections` 集合所提供的效率和安全執行緒更高且完整。

## <a name="related-topics"></a>相關主題

標題 | 說明
----- | -----------
[BlockingCollection 概觀](blockingcollection-overview.md) | 描述 `BlockingCollection<T>` 類型所提供的功能。
[使用安全執行緒集合的時機](when-to-use-a-thread-safe-collection.md) | 說明何時適合使用安全執行緒集合。
[如何：在 ConcurrentDictionary 中新增和移除項目](how-to-add-and-remove-items.md) | 描述如何新增和移除 `ConcurrentDictionary<TKey, TValue>` 中的元素。
[如何：從 BlockingCollection 個別新增和擷取項目](how-to-add-and-take-items.md) | 描述在未使用唯讀列舉值的情況下，如何新增和擷取封鎖回收中的項目。
[如何：將界限和封鎖功能新增至集合](how-to-add-bounding-and-blocking.md ) | 描述如何使用任何集合類別作為 `IProducerConsumerCollection<T>;` 集合的基礎儲存機制。
[如何：使用 ForEach 來移除 BlockingCollection 中的項目](how-to-use-foreach-to-remove.md ) | 描述如何使用 `foreach` 來移除封鎖回收中的所有項目。
[如何：在管線中使用封鎖集合的陣列](how-to-use-arrays-of-blockingcollections.md) | 描述如何同時使用多個封鎖回收來實作管線。
[如何：使用 ConcurrentBag 建立物件集區](how-to-create-an-object-pool.md) | 示範在您可以重複使用物件而非持續建立新物件的情況下，如何使用並行資料包改善效能。

## <a name="reference"></a>參考資料

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)






 





<!--HONumber=Nov16_HO1-->


