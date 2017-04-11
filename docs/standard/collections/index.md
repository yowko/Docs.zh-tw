---
title: "集合和資料結構"
description: "集合和資料結構"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9e70255a-c02a-4046-86b7-10c84bab2d38
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 30e53c38bd58e15668e01f2af79defb0a0918192
ms.lasthandoff: 04/05/2017

---

# <a name="collections-and-data-structures"></a>集合和資料結構

使用集合進行儲存與管理時，通常可以更有效率地處理類似的資料。 您可以使用 [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array) 類別或者 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)、[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 或 [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中的類別，來新增、移除和修改集合中的個別元素或某個範圍元素。

有兩種主要的集合類型；泛型集合和非泛型集合。 泛型集合在編譯時間具有型別安全。 因此，泛型集合通常會有較佳的效能。 建構泛型集合後，泛型集合可接受類型參數，且當您新增或移除集合中的項目時，不需要轉換成 [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) 類型或從該類型進行轉換。 非泛型集合會將項目儲存為 [Object](https://docs.microsoft.com/dotnet/core/api/System.Object)，而且需要轉型。 您可能會在較舊的程式碼中看到非泛型集合。

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中的集合提供有效率的安全執行緒作業，可從多個執行緒存取集合項目。

## <a name="common-collection-features"></a>常見集合功能

所有集合都提供加入、移除或尋找集合中項目的方法。 此外，直接或間接實作 [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) 介面或 [ICollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1) 介面的所有集合，都可共用這些功能： 

* **列舉集合的能力**

   .NET Framework 集合實作 [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) 或 [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1)，可重複查看集合。 列舉程式可視為集合中任何元素可移動的指標。 `foreach, in` 陳述式 (C#) 使用 `GetEnumerator` 方法所公開的列舉值，並會隱藏管理列舉值的複雜程度。 此外，實作 [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) 的任何集合都會視為可查詢類型，且可使用 LINQ 進行查詢。 LINQ 查詢提供存取資料的常見模式。 且通常比標準 for each 迴圈更簡潔易懂，並提供篩選、排序和分組的功能。 LINQ 查詢也可以提升效能。
    
* **將集合內容複製到陣列的能力**

   所有集合都可使用 `CopyTo` 方法複製到陣列。但新陣列中的元素順序，會根據列舉值傳回元素的順序排列。 產生的陣列一律會是一維陣列，且其下限為零。
    
此外，許多集合類別包含下列功能：

* **容量和計數屬性**

   集合的容量是它可以包含的元素數目。 集合的計數是它實際包含的元素數目。 某些集合會隱藏容量或計數，或同時隱藏兩者。
    
   達到目前的容量時，大多數集合會自動擴大容量。 將會重新配置記憶體，並從舊集合將元素複製到新的集合。 這樣可以減少使用集合所需的程式碼；不過，可能會對集合效能產生負面的影響。 例如，針對 [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)，如果 `Count` 小於 `Capacity`，則新增項目的作業為 O(1)。 如果需要增加容量以容納新的元素，則新增項目的作業會變成 O(n)，其中 n 是 `Count`。 避免多次重新配置造成的效能不佳之最佳方式，是將初始容量設定為集合的預估大小。 
    
   [BitArray](https://docs.microsoft.com/dotnet/core/api/System.Collections.BitArray) 是特殊的情況；它的容量等同於長度，計數也是。
    
*   **一致的下限**

   集合的下限是其第一個元素的索引。 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 命名空間中的所有索引集合下限皆為零，表示它們為 0 索引。 根據預設，[Array](https://docs.microsoft.com/dotnet/core/api/System.Array) 下限為零，但使用 `Array.CreateInstance` 建立 `Array` 類別的執行個體時，可以定義其他下限。

*   **從多個執行緒存取的同步處理** (僅限 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 類別)。

   [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 命名空間中的非泛型集合類型，提供一些同步處理的執行緒安全；通常會透過 `SyncRoot` 和 `IsSynchronized` 成員公開。 這些集合不是預設的安全執行緒。 如果您需要可擴充且有效地以多執行緒存取集合，請使用 [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 命名空間中的其中一個類別，或考慮使用不可變的集合。 如需詳細資訊，請參閱[安全執行緒集合](threadsafe/index.md)。    
    
## <a name="choosing-a-collection"></a>選擇集合 

一般情況下，您應該使用泛型集合。 下表說明一些常見的集合案例，以及您可以為這些案例使用的集合類別。 如果您是泛型集合的新手，此表格可協助您選擇最適合您工作的泛型集合。

我想要… | 泛型集合選項 | 非泛型集合選項
---------- | ---------------------------- | --------------------------------
儲存項目為成對的索引鍵/值，以供依據索引鍵快速查詢 | [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) | [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)
依索引存取項目 | [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) | [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)、[System.Collections.ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList)
先進先出 (FIFO) 地使用項目 | [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) | [System.Collections.Queue](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)
後進先出 (LIFO) 地使用資料 | [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) | [System.Collections.Stack](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)
循序存取項目 | [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) | 不推薦
當集合中有項目移除或加入時，收到通知。 (實作 [INotifyPropertyChanged](https://docs.microsoft.com/dotnet/core/api/System.ComponentModel.INotifyPropertyChanged) 和 [INotifyCollectionChanged](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.INotifyCollectionChanged)) | [System.Collections.ObjectModel.ObservableCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ObservableCollection-1) | 不推薦
使用排序的集合 | [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) | [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList)
管理唯一元素的有效儲存和存取 | [System.Collections.Generic.HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1)、[System.Collections.Generic.SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) | 不推薦

## <a name="related-topics"></a>相關主題

標題 | 說明
----- | -----------
[選取集合類別](selecting-a-collection-class.md) | 說明不同的集合，並協助您選取用於您案例的集合。
[常用的集合類型](commonly-used-collection-types.md) | 描述常用泛形和非泛形集合類型 (例如 [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)、[System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) 和 [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2))。 
[使用泛型集合的時機](when-to-use-generic-collections.md) | 說明泛型集合類型的用法。
[在集合內比較和排序](comparisons-and-sorts-within-collections.md) | 討論在集合中使用相等比較和排序比較。
[排序的集合類型](sorted-collection-types.md) | 描述經過排序之集合的效能與特性。
[Hashtable 和 Dictionary 集合類型](hashtable-and-dictionary-collection-types.md) | 說明泛型和非泛型雜湊字典類型的功能。
[安全執行緒集合](threadsafe/index.md) | 描述 [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) 和 [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) 這類集合類型，這類類型支援從多個執行緒進行安全有效率的並行存取。

## <a name="reference"></a>參考資料

[System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Linq](https://docs.microsoft.com/dotnet/core/api/System.Linq)
  

