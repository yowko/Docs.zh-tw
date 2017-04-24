---
title: "集合和資料結構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "群組集合中的資料"
  - "物件 [.NET Framework], 在集合中群組"
  - "陣列類別, 群組集合中的資料"
  - "執行緒處理 [.NET Framework], 安全"
  - "集合類別"
  - "集合 [.NET Framework]"
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: 36
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 35
---
# 集合和資料結構
使用集合進行儲存與管理時，通常可以更有效率地處理類似的資料。 您可以使用<xref:System.Array?displayProperty=fullName>類別或類別中的<xref:System.Collections>， <xref:System.Collections.Generic>， <xref:System.Collections.Concurrent>，System.Collections.Immutable 命名空間，以新增、 移除和修改個別元素或在集合中的項目範圍。  
  
 有兩種主要的集合類型；泛型集合和非泛型集合。 泛型集合已加入.NET Framework 2.0 中，且會在編譯階段提供類型安全的集合。 因此，泛型集合通常會有較佳的效能。 建構泛型集合後，泛型集合可接受類型參數，且當您新增或移除集合中的項目時，不需要轉換成 <xref:System.Object> 類型或從該類型進行轉換。  此外，在 [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]應用程式中支援大部分的泛型集合。 非泛型集合中儲存項目，做為<xref:System.Object>，需要進行轉型，並不支援大多數的[!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]應用程式開發。 但您可能會在較舊的程式碼中看到非泛型集合。  
  
 從開始[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，在集合<xref:System.Collections.Concurrent>命名空間提供了有效率的安全執行緒作業，從多個執行緒存取集合項目。 System.Collections.Immutable 命名空間中的不可變的集合類別 ([nuget](https://www.nuget.org/packages/System.Collections.Immutable)) 是原本就是執行緒安全，因為原始集合的複本上執行作業，而且無法修改原始集合。  
  
   
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>常見集合功能  
 所有集合都提供加入、移除或尋找集合中項目的方法。 此外，所有集合直接或間接都實作<xref:System.Collections.ICollection>介面或<xref:System.Collections.Generic.ICollection%601>介面共用這些功能︰  
  
-   **列舉集合的能力**  
  
     .NET framework 集合實作<xref:System.Collections.IEnumerable?displayProperty=fullName>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> ，可重複查看集合。 列舉程式可視為集合中任何元素可移動的指標。 [Foreach 中](../Topic/foreach,%20in%20\(C%23%20Reference\).md)陳述式和[每個...下一個陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)使用所公開的列舉值<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法，並隱藏管理列舉值的複雜度。 此外，任何集合實作<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>會被視為*可查詢型別*且可以使用 LINQ 查詢。 LINQ 查詢提供存取資料的常見模式。 且通常比標準 `foreach` 迴圈更簡潔易懂，並提供篩選、排序和分組的功能。 LINQ 查詢也可以提升效能。 如需詳細資訊，請參閱[LINQ to Objects](../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-objects.md)，[平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)和[LINQ 查詢 (C#) 簡介](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)。  
  
-   **將集合內容複製到陣列的能力**  
  
     所有集合可以都複製到陣列使用**CopyTo**方法; 不過，新陣列中項目的順序根據中列舉值傳回它們的順序。 產生的陣列一律會是一維陣列，且其下限為零。  
  
 此外，許多集合類別包含下列功能：  
  
-   **容量和計數屬性**  
  
     集合的容量是它可以包含的元素數目。 集合的計數是它實際包含的元素數目。 某些集合會隱藏容量或計數，或同時隱藏兩者。  
  
     達到目前的容量時，大多數集合會自動擴大容量。 將會重新配置記憶體，並從舊集合將元素複製到新的集合。 這樣可以減少使用集合所需的程式碼；不過，可能會對集合效能產生負面的影響。 例如，對於<xref:System.Collections.Generic.List%601>，如果<xref:System.Collections.Generic.List%601.Count%2A>是小於<xref:System.Collections.Generic.List%601.Capacity%2A>，加入項目是 o （1） 運算。 如果需要增加，以容納新項目容量，新增項目會變成 o （n） 作業，其中 n 是<xref:System.Collections.Generic.List%601.Count%2A>。 避免多次重新配置造成的效能不佳之最佳方式，是將初始容量設定為集合的預估大小。  
  
     <xref:System.Collections.BitArray> 是特殊的情況；它的容量等同於長度，計數也是。  
  
-   **一致的下限**  
  
     集合的下限是其第一個元素的索引。 <xref:System.Collections> 命名空間中的所有索引集合下限皆為零，表示它們為 0 索引。 <xref:System.Array>下限為零，根據預設，但建立的執行個體時，就可以定義其他下限**陣列**類別使用<xref:System.Array.CreateInstance%2A?displayProperty=fullName>。  
  
-   **從多個執行緒存取的同步處理** (僅限 <xref:System.Collections> 類別)。  
  
     中的非泛型集合類型<xref:System.Collections>命名空間提供一些執行緒安全性同步處理; 通常是透過公開<xref:System.Collections.ICollection.SyncRoot%2A>和<xref:System.Collections.ICollection.IsSynchronized%2A>成員。 這些集合不是預設的安全執行緒。 如果您需要可擴充且有效地以多執行緒存取集合，請使用 <xref:System.Collections.Concurrent> 命名空間中的其中一個類別，或考慮使用不可變的集合。 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>選擇集合  
 一般情況下，您應該使用泛型集合。 下表說明一些常見的集合案例，以及您可以為這些案例使用的集合類別。 如果您是泛型集合的新手，此表格可協助您選擇最適合您工作的泛型集合。  
  
|||||  
|-|-|-|-|  
|我想要…|泛型集合選項|非泛型集合選項|安全執行緒或不可的集合選項|  
|儲存項目為成對的索引鍵/值，以供依據索引鍵快速查詢|<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName></TKey, TValue>|<xref:System.Collections.Hashtable><br /><br /> (成對的索引鍵/值之集合，依據索引鍵的雜湊碼加以組織)。|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> [ImmutableDictionary （Dictionary\<tkey，Tvalue>） 類別](../Topic/ImmutableDictionary\(TKey,%20TValue\)%20Class.md)|  
|依索引存取項目|<xref:System.Collections.Generic.List%601?displayProperty=fullName>|<xref:System.Array?displayProperty=fullName><br /><br /> <xref:System.Collections.ArrayList?displayProperty=fullName>|[ImmutableList(T) 類別](../Topic/ImmutableList\(T\)%20Class.md)<br /><br /> [ImmutableArray 類別](../Topic/ImmutableArray%20Class.md)|  
|先進先出 (FIFO) 地使用項目|<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>|<xref:System.Collections.Queue?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName><br /><br /> [ImmutableQueue(T) 類別](../Topic/ImmutableQueue\(T\)%20Class.md)|  
|後進先出 (LIFO) 地使用資料|<xref:System.Collections.Generic.Stack%601?displayProperty=fullName>|<xref:System.Collections.Stack?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName><br /><br /> [ImmutableStack(T) 類別](../Topic/ImmutableStack\(T\)%20Class.md)|  
|循序存取項目|<xref:System.Collections.Generic.LinkedList%601?displayProperty=fullName>|不推薦|不推薦|  
|當集合中有項目移除或加入時，收到通知。 (實作<xref:System.ComponentModel.INotifyPropertyChanged>和<xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName>)|<xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>|不推薦|不推薦|  
|排序的集合|<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>\</TKey, TValue>|<xref:System.Collections.SortedList?displayProperty=fullName>|[ImmutableSortedDictionary （Dictionary\<tkey，Tvalue>） 類別](../Topic/ImmutableSortedDictionary\(TKey,%20TValue\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) 類別](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
|數學函式的集合|<xref:System.Collections.Generic.HashSet%601?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>|不推薦|[ImmutableHashSet(T) 類別](../Topic/ImmutableHashSet\(T\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) 類別](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[選取集合類別](../../../docs/standard/collections/selecting-a-collection-class.md)|說明不同的集合，並協助您選取用於您案例的集合。|  
|[常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)|說明常用的泛型和非泛型集合型別，例如<xref:System.Array?displayProperty=fullName>， <xref:System.Collections.Generic.List%601?displayProperty=fullName>，和<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>。\</TKey, TValue>|  
|[何時使用泛型集合](../../../docs/standard/collections/when-to-use-generic-collections.md)|說明泛型集合類型的用法。|  
|[在集合內比較和排序](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|討論在集合中使用相等比較和排序比較。|  
|[排序集合類型](../../../docs/standard/collections/sorted-collection-types.md)|說明經過排序之集合的效能與特性|  
|[Hashtable 和 Dictionary 集合類型](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|說明泛型和非泛型雜湊字典類型的功能。|  
|[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)|說明集合類型，例如<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>和<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>支援安全又有效率的並行存取，從多個執行緒。|  
|System.Collections.Immutable|介紹不可變的集合並提供集合類型的連結。|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.Array?displayProperty=fullName>  
  
 <xref:System.Collections?displayProperty=fullName>  
  
 <xref:System.Collections.Concurrent?displayProperty=fullName>  
  
 <xref:System.Collections.Generic?displayProperty=fullName>  
  
 <xref:System.Collections.Specialized?displayProperty=fullName>  
  
 <xref:System.Linq?displayProperty=fullName>  
  
 System.Collections.Immutable