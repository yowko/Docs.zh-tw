---
title: "BlockingCollection 概觀"
description: "BlockingCollection 概觀"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1a867de-53c2-49ca-9a1a-e5770a942724
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 8a770fb7143a547031daf231d1a0863322c3cfaa
ms.lasthandoff: 03/02/2017

---

# <a name="blockingcollection-overview"></a>BlockingCollection 概觀

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) 是提供下列功能的安全執行緒集合類別︰

*   生產者-消費者模式的實作。

*   集合中項目的安全執行緒新增和移除。

*   最佳最大容量。

*   集合是空的或已滿時封鎖的插入和移除作業。

*   不會封鎖或最多封鎖一段指定時間的插入和移除 "try" 作業。

*   封裝任何可實作 [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) 的集合類別。

*   具有取消語彙基元的取消作業。

*   `foreach` 的列舉有兩種： 

    1. 唯讀列舉。
    
    2. 移除所列舉項目的列舉。
    
## <a name="bounding-and-blocking-support"></a>界限和封鎖支援 

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) 支援界限和封鎖。 界限表示您可以設定集合的最大容量。 界限在某些情況下十分重要，原因是它可讓您控制記憶體中集合的大小上限，並且防止產生執行緒移到使用執行緒的太前面。

多個執行緒或工作可以同時將項目新增至集合，如果集合達到其指定的最大容量，則會在移除項目之前封鎖產生執行緒。 多位消費者可以同時移除項目，如果集合變成空的，則會在生產者新增項目之前封鎖使用執行緒。 產生執行緒可以呼叫 `CompleteAdding`，表示無法再新增項目。 消費者會監視 `IsCompleted` 屬性，以得知集合何時變成空的，以及何時無法再新增項目。 下列範例示範界限容量為 100 的簡單 `BlockingCollection`。 只要符合某個外部條件，生產者工作就會將項目新增至集合，然後呼叫 `CompleteAdding`。 在 `IsCompleted` 屬性為 true 之前，消費者工作會擷取項目。

```csharp
// A bounded collection. It can hold no more 
// than 100 items at once.
BlockingCollection<Data> dataItems = new BlockingCollection<Data>(100);


// A simple blocking consumer with no cancellation.
Task.Run(() => 
{
    while (!dataItems.IsCompleted)
    {

        Data data = null;
        // Blocks if number.Count == 0
        // IOE means that Take() was called on a completed collection.
        // Some other thread can call CompleteAdding after we pass the
        // IsCompleted check but before we call Take. 
        // In this example, we can simply catch the exception since the 
        // loop will break on the next iteration.
        try
        {
            data = dataItems.Take();
        }
        catch (InvalidOperationException) { }

        if (data != null)
        {
            Process(data);
        }
    }
    Console.WriteLine("\r\nNo more items to take.");
});

// A simple blocking producer with no cancellation.
Task.Run(() =>
{
    while (moreItemsToAdd)
    {
        Data data = GetData();
        // Blocks if numbers.Count == dataItems.BoundedCapacity
        dataItems.Add(data);
    }
    // Let consumer know we are done.
    dataItems.CompleteAdding();
});
```

如需完整範例，請參閱[如何：從 BlockingCollection 個別新增和擷取項目](how-to-add-and-take-items.md)。

## <a name="timed-blocking-operations"></a>計時封鎖作業

在界限集合的計時封鎖 `TryAdd` 和 `TryTake` 作業上，方法會嘗試新增或擷取項目。 如果項目可用，則會將它置入依傳址所傳遞的變數，而且方法會傳回 `true`。 如果在指定的逾時期間之後未擷取任何項目，則方法會傳回 `false`。 執行緒接著可以先執行一些其他有用工作，再重新嘗試存取集合。 如需計時封鎖存取的範例，請參閱[如何：從 BlockingCollection 個別新增和擷取項目](how-to-add-and-take-items.md)中的第二個範例。

## <a name="cancelling-add-and-take-operations"></a>取消新增和擷取作業

新增和擷取作業一般會透過迴圈形式執行。 您可以將 `CancellationToken` 傳入 `TryAdd` 或 `TryTake` 方法來取消迴圈，然後檢查每個反覆項目上語彙基元之 `IsCancellationRequested` 屬性的值。 如果值為 `true`，則是由您決定透過清除任何資源並結束迴圈來回應取消要求。 下列範例示範採用取消語彙基元之 `TryAdd` 的多載，以及使用它的程式碼︰

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="specifying-the-collection-type"></a>指定集合類型

在您建立 `BlockingCollection<T>;` 時，不僅可以指定界限容量，還可以指定要使用的集合類型。 例如，您可以針對先進先出 (FIFO) 行為指定 [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) 物件，或針對後進先出 (LIFO) 行為指定 [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 物件。 您可以使用任何可實作 [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) 介面的集合類別。 `BlockingCollection<T>` 的預設集合類型為 `ConcurrentQueue<T>`。 下列程式碼範例示範如何建立容量為 1000 並使用 [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) 之字串的 `BlockingCollection<T>`：

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="ienumerable-support"></a>IEnumerable 支援

`BlockingCollection<T>` 提供 `GetConsumingEnumerable` 方法讓消費者可以使用 `foreach` 陳述式移除項目，直到收集完成為止；這表示集合會是空的，而且不會再新增任何項目。 如需詳細資訊，請參閱[如何：使用 ForEach 來移除 BlockingCollection 中的項目](how-to-use-foreach-to-remove.md)。

## <a name="using-many-blockingcollections-as-one"></a>將多個 BlockingCollection 當成一個使用

如果消費者需要同時從多個集合擷取項目，您可以建立 `BlockingCollection<T>` 陣列，並使用將新增至或擷取自陣列中任何集合的靜態方法 (例如 `TakeFromAny` 和 `AddToAny`)。 如果封鎖其中一個集合，則方法會立即嘗試另一個集合，直到找到可執行作業的集合為止。 如需詳細資訊，請參閱[如何：在管線中使用封鎖回收的陣列](how-to-use-arrays-of-blockingcollections.md)。

## <a name="see-also"></a>另請參閱

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[集合與資料結構](../index.md)

[安全執行緒集合](index.md)


