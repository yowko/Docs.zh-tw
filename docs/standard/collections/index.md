---
title: 集合和資料結構
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
ms.openlocfilehash: 1bc632a7cfdb96967c7fc508e22ca93c1ed9318f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728501"
---
# <a name="collections-and-data-structures"></a>集合和資料結構

使用集合進行儲存與管理時，通常可以更有效率地處理類似的資料。 您可以使用<xref:System.Array?displayProperty=nameWithType> <xref:System.Collections>類別或、、 <xref:System.Collections.Generic> <xref:System.Collections.Concurrent>和<xref:System.Collections.Immutable>命名空間中的類別，來新增、移除和修改集合中的個別專案或某個範圍的元素。

有兩種主要的集合類型；泛型集合和非泛型集合。 泛型集合已加入.NET Framework 2.0 中，且會在編譯階段提供類型安全的集合。 因此，泛型集合通常會有較佳的效能。 建構泛型集合後，泛型集合可接受類型參數，且當您加入或移除集合中的項目時，不需要轉換成 <xref:System.Object> 類型或從該類型進行轉換。  此外，Windows Store 應用程式也支援大部分的泛型集合。 非泛型集合會將專案儲存<xref:System.Object>為、需要轉型，而且大部分都不支援 Windows store 應用程式開發。 但您可能會在較舊的程式碼中看到非泛型集合。

從 .NET Framework 4 開始，<xref:System.Collections.Concurrent> 命名空間中的集合提供了有效率的安全執行緒作業，可從多個執行緒存取集合項目。 <xref:System.Collections.Immutable>命名空間（[NuGet 套件](https://www.nuget.org/packages/System.Collections.Immutable)）中不可變的集合類別原本就是安全線程，因為作業是在原創組合的複本上執行，而且無法修改原創組合。

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>常見集合功能

所有集合都會提供方法來新增、移除或尋找集合中的專案。 此外，直接或間接實作 <xref:System.Collections.ICollection> 介面或 <xref:System.Collections.Generic.ICollection%601> 介面的所有集合，都可共用這些功能：

- **列舉集合的能力**

    .NET Framework 集合實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>，可重複查看集合。 列舉程式可視為集合中任何元素可移動的指標。 [foreach, in](../../csharp/language-reference/keywords/foreach-in.md) 陳述式和 [For Each...Next 陳述式](../../visual-basic/language-reference/statements/for-each-next-statement.md)，會使用 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法所公開的列舉程式，並會隱藏管理列舉程式的複雜程度。 此外，實作 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 的任何集合，會視為「可查詢類型」**，且可使用 LINQ 進行查詢。 LINQ 查詢提供存取資料的常見模式。 且通常比標準 `foreach` 迴圈更簡潔易懂，並提供篩選、排序和分組的功能。 LINQ 查詢也可以提升效能。 如需詳細資訊，請參閱 [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md)、[LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)、[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)、[LINQ 查詢簡介 (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) 及[基本查詢作業 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。

- **將集合內容複製到陣列的能力**

    所有集合都可使用 **CopyTo** 方法複製到陣列。但新陣列中的元素順序，會根據列舉程式傳回元素的順序排列。 產生的陣列一律會是一維陣列，且其下限為零。

此外，許多集合類別包含下列功能：

- **容量和計數屬性**

    集合的容量是它可以包含的元素數目。 集合的計數是它實際包含的元素數目。 某些集合會隱藏容量或計數，或同時隱藏兩者。

    達到目前的容量時，大多數集合會自動擴大容量。 將會重新配置記憶體，並從舊集合將元素複製到新的集合。 這樣可以減少使用集合所需的程式碼；不過，可能會對集合效能產生負面的影響。 例如， <xref:System.Collections.Generic.List%601>如果<xref:System.Collections.Generic.List%601.Count%2A>小於<xref:System.Collections.Generic.List%601.Capacity%2A>，則新增專案為 O （1）運算。 如果需要增加容量以容納新的元素，則新增專案會變成 O （`n`）運算，其中`n`為。 <xref:System.Collections.Generic.List%601.Count%2A> 避免多次重新配置造成的效能不佳之最佳方式，是將初始容量設定為集合的預估大小。

    <xref:System.Collections.BitArray> 是特殊的情況；它的容量等同於長度，計數也是。

- **一致的下限**

    集合的下限是其第一個元素的索引。 <xref:System.Collections> 命名空間中的所有索引集合下限皆為零，表示它們為 0 索引。 <xref:System.Array>預設的下限為零，但使用<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>建立**Array**類別的實例時，可以定義不同的下限。

- **從多個執行緒存取的同步**處理（<xref:System.Collections>僅限類別）。

    <xref:System.Collections> 命名空間中的非泛型集合類型，提供一些同步處理的執行緒安全性；通常會透過 <xref:System.Collections.ICollection.SyncRoot%2A> 和 <xref:System.Collections.ICollection.IsSynchronized%2A> 成員公開。 這些集合不是預設的安全執行緒。 如果您需要可調整且有效地以多執行緒存取集合，請使用 <xref:System.Collections.Concurrent> 命名空間中的其中一個類別，或考慮使用不可變的集合。 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。

<a name="BKMK_Choosingacollection"></a>
## <a name="choose-a-collection"></a>選擇集合

一般情況下，您應該使用泛型集合。 下表說明一些常見的集合案例，以及您可以為這些案例使用的集合類別。 如果您是泛型集合的新手，此表格可協助您選擇最適合您工作的泛型集合。

|我想要…|泛型集合的選項|非泛型集合的選項|安全執行緒或固定集合的選項|
|-|-|-|-|
|儲存項目為成對的索引鍵/值，以供依據索引鍵快速查詢|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (成對的機碼/值之集合，依據機碼的雜湊碼加以組織)。|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|
|依索引存取項目|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|
|先進先出 (FIFO) 地使用項目|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|
|後進先出 (LIFO) 地使用資料|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|
|循序存取項目|<xref:System.Collections.Generic.LinkedList%601>|不推薦|不推薦|
|當集合中有項目移除或加入時，收到通知。 (實作 <xref:System.ComponentModel.INotifyPropertyChanged> 和 <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|不推薦|不推薦|
|排序的集合|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|
|數學函式的集合|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|不推薦|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|

### <a name="algorithmic-complexity-of-collections"></a>集合的演算法複雜度

選擇[集合類別](selecting-a-collection-class.md)時，值得考慮效能的潛在取捨。 使用下表來參考不同的可變動集合類型如何與其對應的不可變對應項比較。 不可變的集合類型通常較不具效能，但會提供不可變性，這通常是有效的比較優點。

| 可變動                   | 分攤  | 最差案例                | 固定                          | 複雜度 |
|---------------------------|------------|---------------------------|------------------------------------|------------|
| `Stack<T>.Push`           | O （1）       | O （`n`）                    | `ImmutableStack<T>.Push`           | O （1）       |
| `Queue<T>.Enqueue`        | O （1）       | O （`n`）                    | `ImmutableQueue<T>.Enqueue`        | O （1）       |
| `List<T>.Add`             | O （1）       | O （`n`）                    | `ImmutableList<T>.Add`             | O （log `n`） |
| `List<T>.Item[Int32]`     | O （1）       | O （1）                      | `ImmutableList<T>.Item[Int32]`     | O （log `n`） |
| `List<T>.Enumerator`      | O （`n`）     | O （`n`）                    | `ImmutableList<T>.Enumerator`      | O （`n`）     |
| `HashSet<T>.Add`，lookup  | O （1）       | O （`n`）                    | `ImmutableHashSet<T>.Add`          | O （log `n`） |
| `SortedSet<T>.Add`        | O （log `n`） | O （`n`）                    | `ImmutableSortedSet<T>.Add`        | O （log `n`） |
| `Dictionary<T>.Add`       | O （1）       | O （`n`）                    | `ImmutableDictionary<T>.Add`       | O （log `n`） |
| `Dictionary<T>`反向    | O （1）       | O （1）-或嚴格的 O`n`（） | `ImmutableDictionary<T>`反向    | O （log `n`） |
| `SortedDictionary<T>.Add` | O （log `n`） | O （`n` log `n`）            | `ImmutableSortedDictionary<T>.Add` | O （log `n`） |

`List<T>`可以使用`for`迴圈或`foreach`迴圈來有效率地列舉。 `ImmutableList<T>`不過，會在`for`迴圈內執行不佳的作業，因為其索引子的 O `n`（log）時間。 `ImmutableList<T>`使用`foreach`迴圈來列舉會很有效率， `ImmutableList<T>`因為會使用二進位樹狀結構來儲存其資料，而不是`List<T>`使用之類的簡單陣列。 陣列可以非常快速地編制索引，而二進位樹狀結構必須向下切入，直到找到具有所需索引的節點為止。

此外， `SortedSet<T>`具有與相同的複雜性`ImmutableSortedSet<T>`。 這是因為它們都使用二進位樹狀結構。 當然，顯著的差異在於`ImmutableSortedSet<T>`使用不可變的二進位樹狀結構。 由於`ImmutableSortedSet<T>`也提供了<xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder?displayProperty=nameWithType>允許變動的類別，因此您可以同時擁有不存在和效能。

<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>[相關主題]

|Title|描述|
|-----------|-----------------|
|[選取集合類別](../../../docs/standard/collections/selecting-a-collection-class.md)|說明不同的集合，並協助您選取用於您案例的集合。|
|[常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)|說明常用的泛型與非泛型集合類型，例如 <xref:System.Array?displayProperty=nameWithType>、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。|
|[使用泛型集合的時機](../../../docs/standard/collections/when-to-use-generic-collections.md)|說明泛型集合類型的用法。|
|[集合內的比較和排序](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|討論在集合中使用相等比較和排序比較。|
|[排序的集合類型](../../../docs/standard/collections/sorted-collection-types.md)|說明經過排序之集合的效能與特性|
|[Hashtable 和 Dictionary 集合類型](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|說明泛型和非泛型雜湊字典類型的功能。|
|[安全線程集合](../../../docs/standard/collections/thread-safe/index.md)|說明如 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 和 <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> 這類集合類型，這類類型支援從多個執行緒進行安全有效率的並行存取。|
|System.Collections.Immutable|介紹不可變的集合並提供集合類型的連結。|

<a name="BKMK_Reference"></a>
## <a name="reference"></a>參考資料
<xref:System.Array?displayProperty=nameWithType>
<xref:System.Collections?displayProperty=nameWithType>
<xref:System.Collections.Concurrent?displayProperty=nameWithType>
<xref:System.Collections.Generic?displayProperty=nameWithType>
<xref:System.Collections.Specialized?displayProperty=nameWithType>
<xref:System.Linq?displayProperty=nameWithType>
<xref:System.Collections.Immutable>
