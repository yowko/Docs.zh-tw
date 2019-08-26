---
title: 排序集合類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c49b3fcd5b50cc5b48497dcf97862e80b066ab46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957875"
---
# <a name="sorted-collection-types"></a><span data-ttu-id="8fe2c-102">排序集合類型</span><span class="sxs-lookup"><span data-stu-id="8fe2c-102">Sorted Collection Types</span></span>
<span data-ttu-id="8fe2c-103"><xref:System.Collections.SortedList?displayProperty=nameWithType> 類別、<xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> 泛型類別和 <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> 泛型類別，類似於實作 <xref:System.Collections.IDictionary> 介面的 <xref:System.Collections.Hashtable> 類別和 <xref:System.Collections.Generic.Dictionary%602> 泛型類別，但它們會依索引鍵的排序次序維持其項目，沒有 O(1) 插入和雜湊資料表的擷取特性。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-103">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="8fe2c-104">三個類別有數個共用功能︰</span><span class="sxs-lookup"><span data-stu-id="8fe2c-104">The three classes have several features in common:</span></span>  
  
- <span data-ttu-id="8fe2c-105">這三個類別都實作 <xref:System.Collections.IDictionary?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="8fe2c-106">兩個泛型類別還會實作 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>  
  
- <span data-ttu-id="8fe2c-107">每個元素都是進行列舉的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-107">Each element is a key/value pair for enumeration purposes.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8fe2c-108">列舉時，雖然兩個泛型類型傳回 <xref:System.Collections.Generic.KeyValuePair%602> 物件，但非泛型 <xref:System.Collections.SortedList> 類別會傳回 <xref:System.Collections.DictionaryEntry> 物件。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>  
  
- <span data-ttu-id="8fe2c-109">項目會依 <xref:System.Collections.IComparer?displayProperty=nameWithType> 實作排序 (非泛型 <xref:System.Collections.SortedList>) 或依 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 實作排序 (兩個泛型類別)。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>  
  
- <span data-ttu-id="8fe2c-110">每個類別都會提供傳回集合的屬性，而這個集合僅包含索引鍵或僅包含值。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>  
  
 <span data-ttu-id="8fe2c-111">下表列出兩個已排序清單類別與 <xref:System.Collections.Generic.SortedDictionary%602> 類別之間的部分差異。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>  
  
|<span data-ttu-id="8fe2c-112"><xref:System.Collections.SortedList>泛型類別與 <xref:System.Collections.Generic.SortedList%602> 泛型類別</span><span class="sxs-lookup"><span data-stu-id="8fe2c-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span>|<span data-ttu-id="8fe2c-113"><xref:System.Collections.Generic.SortedDictionary%602>泛型類別</span><span class="sxs-lookup"><span data-stu-id="8fe2c-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="8fe2c-114">對傳回索引鍵和值的屬性進行編製索引，以進行有效率的索引擷取。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span>|<span data-ttu-id="8fe2c-115">無索引擷取。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-115">No indexed retrieval.</span></span>|  
|<span data-ttu-id="8fe2c-116">擷取是 O(log `n`)。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-116">Retrieval is O(log `n`).</span></span>|<span data-ttu-id="8fe2c-117">擷取是 O(log `n`)。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-117">Retrieval is O(log `n`).</span></span>|  
|<span data-ttu-id="8fe2c-118">插入和移除一般是 O(`n`)；不過，對於已處於排序次序的資料，插入是 O(log `n`)，因此每個項目都會新增至清單的結尾。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="8fe2c-119">(這假設不需要調整大小)。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-119">(This assumes that a resize is not required.)</span></span>|<span data-ttu-id="8fe2c-120">插入和移除是 O(log `n`)。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-120">Insertion and removal are O(log `n`).</span></span>|  
|<span data-ttu-id="8fe2c-121">使用的記憶體少於 <xref:System.Collections.Generic.SortedDictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span>|<span data-ttu-id="8fe2c-122">使用的記憶體多於 <xref:System.Collections.SortedList> 非泛型類別和 <xref:System.Collections.Generic.SortedList%602> 泛型類別。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span>|  
  
 <span data-ttu-id="8fe2c-123">針對必須可以從多個執行緒同時存取的已排序清單或字典，您可以將排序邏輯新增至衍生自 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的類別。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fe2c-124">針對包含專屬索引鍵的值 (例如，包含員工識別碼的員工記錄)，您可以建立索引鍵集合，而索引鍵集合透過衍生自 <xref:System.Collections.ObjectModel.KeyedCollection%602> 泛型類別而具有部分清單特性和部分字典特性。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-124">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
 <span data-ttu-id="8fe2c-125">自 .NET Framework 4 開始，<xref:System.Collections.Generic.SortedSet%601> 類別會提供自我平衡樹狀目錄，以便在插入、刪除和搜尋之後依排序次序維護資料。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-125">Starting with the .NET Framework 4, the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="8fe2c-126">這個類別和 <xref:System.Collections.Generic.HashSet%601> 類別會實作 <xref:System.Collections.Generic.ISet%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="8fe2c-126">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe2c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fe2c-127">See also</span></span>

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [<span data-ttu-id="8fe2c-128">常用的集合類型</span><span class="sxs-lookup"><span data-stu-id="8fe2c-128">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)
