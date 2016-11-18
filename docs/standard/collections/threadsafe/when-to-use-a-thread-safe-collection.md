---
title: "使用安全執行緒集合的時機"
description: "使用安全執行緒集合的時機"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a2a42d44-f6a5-4f16-9000-026221d66349
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 05f692a1a58c0c653e14993cafd61a0711ebf9f8

---

# <a name="when-to-use-a-threadsafe-collection"></a>使用安全執行緒集合的時機

`ConcurrentQueue`、`ConcurrentStack`、`ConcurrentDictionary`、`ConcurrentBag` 和 `BlockingCollection` 集合類型是特別設計來支援多執行緒新增和移除作業。 若要達到執行緒安全，這些新的類型會使用各種有效率的鎖定和無鎖定同步處理機制。 同步處理會增加作業的負荷。 負荷量取決於使用的同步處理類型、執行的作業類型，以及其他因素 (例如，嘗試同時存取集合的執行緒數目)。

在某些情況下，同步處理負荷會顯得微不足道，並且在受到外部鎖定保護時，讓多執行緒類型執行速度大幅加快，而且擴充的狀況遠優於其非安全執行緒對等項目。 在其他情況下，負荷可能會讓安全執行緒類型的執行和擴充速度等於甚於比外部鎖定之非安全執行緒版本的類型還要慢。

下列各節所提供的一般指引是有關何時使用安全執行緒集合，與其具有使用者所提供之讀取和寫入作業鎖定的非安全執行緒對等項目。 因為效能可能會因許多因素而不同，所以本指南不是特定的，也不一定適用於所有情況。 如果效能十分重要，則決定要使用之集合類型的最佳方式是根據代表性電腦組態和負載來測量效能。 本範例使用下列詞彙：

*單純生產者-消費者案例︰*任何指定的執行緒都是新增或移除元素，而非同時執行兩項作業。

*混合生產者-消費者案例︰*任何指定的執行緒都是新增和移除元素。

*加速︰*相對於相同案例中的另一種類型，具有較快速的演算法效能。

*擴充性：*效能會隨著電腦上的核心數目等比例地增加。 在八個核心上進行擴充之演算法的執行速度，比兩個核心還要快。

## <a name="concurrentqueuelttgt-vs-queuelttgt"></a>ConcurrentQueue&lt;T&gt; 與Queue&lt;T&gt;

在每個元素的處理時間都很小 (幾個指示) 的單純生產者-消費者案例中，[System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) 可以透過具有外部鎖定的 [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) 提供適度的效能優點。 在此案例中，如果一個專用執行緒正在置入佇列，而且一個專用執行緒正在移出佇列，則 `ConcurrentQueue<T>` 的執行效果最好。 如果您未強制執行這項規則，則 `Queue<T>` 的執行速度甚至會略高於具有多個核心之電腦上的 `ConcurrentQueue<T>`。 

處理時間約 500 個 FLOPS (浮點作業) 或以上時，雙執行緒規則不適用於 `ConcurrentQueue<T>`，因此具有極佳的擴充性。 在此案例中，`Queue<T>` 不會加以適當調整。

在混合生產者-消費者案例中，處理時間很小時，具有外部鎖定的 `Queue<T>` 所進行的擴充優於 `ConcurrentQueue<T>`。 不過，處理時間大約 500 FLOPS 或以上時，則 `ConcurrentQueue<T>` 會進行較佳的擴充。

## <a name="concurrentstack-vs-stack"></a>ConcurrentStack 與堆疊

在處理時間很小的單純生產者-消費者案例中，[System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) 和具有外部鎖定的 [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) 所執行的作業可能會與使用一個專用推送執行緒和一個專用彈出執行緒相同。 不過，執行緒數目增加時，兩種類型都會因競爭增加而變慢，而且 `Stack<T>` 的執行效果可能會優於 `ConcurrentStack<T>`。 處理時間大約 500 FLOPS 或以上時，兩種類型幾乎會以相同的速率進行擴充。 

在混合生產者-消費者案例中，針對大型和小型工作負載，`ConcurrentStack<T>` 較為快速。

使用 `PushRange` 和 `TryPopRange` 可能會大幅加速存取時間。

## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary 與字典

一般而言，[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) 是用於同時從多個執行緒新增和更新索引鍵或值時。 在經常更新且讀取相對較少的情況下，`ConcurrentDictionary<TKey, TValue>` 一般會提供適度優點。 在進行許多讀取和更新的情況下，`ConcurrentDictionary<TKey, TValue>` 在具有任意數目之核心的電腦上明顯較快。

在需要經常更新的情況下，您可以增加 `ConcurrentDictionary<TKey, TValue>` 中的並行程度，然後測量以查看具有更多核心之電腦的效能是否增加。 如果您變更並行層級，請盡可能避免全域作業。

如果您只是要讀取索引鍵或值，則 [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 的速度會較快，原因是沒有任何執行緒修改字典時就不需要進行同步處理。

## <a name="concurrentbag"></a>ConcurrentBag

在單純生產者-消費者案例中，[System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) 的執行速度可能會比其他並行集合類型還要慢。

在混合生產者-消費者案例中，針對大型和小型工作負載，`ConcurrentBag<T>` 一般都會比任何其他並行集合類型更為快速也更具擴充性。

## <a name="blockingcollection"></a>BlockingCollection

需要界限和封鎖語意時，[System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) 的執行速度可能會比任何自訂實作還要快。 它也支援大量取消、列舉和例外狀況處理。

## <a name="see-also"></a>另請參閱

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[安全執行緒集合](index.md)



<!--HONumber=Nov16_HO3-->


