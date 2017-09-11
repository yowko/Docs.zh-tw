---
title: "如何：在 ConcurrentDictionary 中加入和移除項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40291d424916c2f87a2070a9a8a6e49243ac083a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="9fb45-102">如何：在 ConcurrentDictionary 中加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="9fb45-102">How to: Add and Remove Items from a ConcurrentDictionary</span></span>
<span data-ttu-id="9fb45-103">這個範例示範如何新增、擷取、更新和移除 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> 中的項目。</span><span class="sxs-lookup"><span data-stu-id="9fb45-103">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>.</span></span> <span data-ttu-id="9fb45-104">這個集合類別是安全執行緒實作。</span><span class="sxs-lookup"><span data-stu-id="9fb45-104">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="9fb45-105">只要多個執行緒可能嘗試同時存取元素，就建議您使用它。</span><span class="sxs-lookup"><span data-stu-id="9fb45-105">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>  
  
 <span data-ttu-id="9fb45-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>供幾種便利的方法，讓程式碼不需要在嘗試新增或移除資料之前，先檢查索引鍵存在與否。</span><span class="sxs-lookup"><span data-stu-id="9fb45-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="9fb45-107">下表列出這些便利方法，並描述其使用時機。</span><span class="sxs-lookup"><span data-stu-id="9fb45-107">The following table lists these convenience methods and describes when to use them.</span></span>  
  
|<span data-ttu-id="9fb45-108">方法</span><span class="sxs-lookup"><span data-stu-id="9fb45-108">Method</span></span>|<span data-ttu-id="9fb45-109">使用時機...</span><span class="sxs-lookup"><span data-stu-id="9fb45-109">Use when…</span></span>|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|<span data-ttu-id="9fb45-110">您想要新增所指定索引鍵的新值，如果已經有索引鍵，則您會想要取代它的值。</span><span class="sxs-lookup"><span data-stu-id="9fb45-110">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span>|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|<span data-ttu-id="9fb45-111">您想要擷取所指定索引鍵的現有值，如果索引鍵不存在，則您會想要指定索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="9fb45-111">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span>|  
|<span data-ttu-id="9fb45-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="9fb45-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span>|<span data-ttu-id="9fb45-113">您想要新增、取得、更新或移除索引鍵/值組，如果已經有索引鍵，或嘗試因任何其他原因而失敗，則您會想要採取一些替代動作。</span><span class="sxs-lookup"><span data-stu-id="9fb45-113">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9fb45-114">範例</span><span class="sxs-lookup"><span data-stu-id="9fb45-114">Example</span></span>  
 <span data-ttu-id="9fb45-115">下列範例使用兩個 <xref:System.Threading.Tasks.Task> 執行個體同時將一些項目新增至 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>，然後輸出所有內容以顯示已成功新增項目。</span><span class="sxs-lookup"><span data-stu-id="9fb45-115">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="9fb45-116">此範例也會示範如何使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 方法，在集合中加入、更新和擷取項目。</span><span class="sxs-lookup"><span data-stu-id="9fb45-116">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve  items from the collection.</span></span>  
  
 <span data-ttu-id="9fb45-117">[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)] [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]</span><span class="sxs-lookup"><span data-stu-id="9fb45-117">[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)] [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]</span></span>  
  
 <span data-ttu-id="9fb45-118"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是針對多執行緒案例所設計。</span><span class="sxs-lookup"><span data-stu-id="9fb45-118"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="9fb45-119">您不需要在程式碼中使用鎖定，即可新增或移除集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="9fb45-119">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="9fb45-120">不過，其中一個執行緒一定要可以擷取一個值，而另一個執行緒要將新的值提供給相同的索引鍵來立即更新集合。</span><span class="sxs-lookup"><span data-stu-id="9fb45-120">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>  
  
 <span data-ttu-id="9fb45-121">此外，雖然 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的所有方法都是安全執行緒，但是並非所有方法都是不可部分完成，尤其是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>。</span><span class="sxs-lookup"><span data-stu-id="9fb45-121">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="9fb45-122">傳遞給這些方法的使用者委派是在字典內部鎖定外部進行叫用</span><span class="sxs-lookup"><span data-stu-id="9fb45-122">The user delegate that is passed to these methods is invoked outside of the dictionary's internal lock.</span></span> <span data-ttu-id="9fb45-123">(完成這項作業是要防止未知程式碼封鎖所有執行緒)。因此，可能會發生這系列的事件︰</span><span class="sxs-lookup"><span data-stu-id="9fb45-123">(This is done to prevent unknown code from blocking all threads.) Therefore it is possible for this sequence of events to occur:</span></span>  
  
 <span data-ttu-id="9fb45-124">1\) threadA 會呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>、找不到項目，並叫用 valueFactory 委派來建立要新增的新項目。</span><span class="sxs-lookup"><span data-stu-id="9fb45-124">1\) threadA calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item and creates a new item to Add by invoking the valueFactory delegate.</span></span>  
  
 <span data-ttu-id="9fb45-125">2\) threadB 同時呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>、叫用其 valueFactory 委派，並且在 threadA 之前到達內部鎖定，因此會將其新的索引鍵/值組新增至字典。</span><span class="sxs-lookup"><span data-stu-id="9fb45-125">2\) threadB calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its valueFactory delegate is invoked and it arrives at the internal lock before threadA, and so its new key-value pair is added to the dictionary.</span></span>  
  
 <span data-ttu-id="9fb45-126">3\) threadA 的使用者委派完成，而且執行緒到達鎖定，但現在會看到這個項目已存在。</span><span class="sxs-lookup"><span data-stu-id="9fb45-126">3\) threadA's user delegate completes, and the thread arrives at the lock, but now sees that the item exists already</span></span>  
  
 <span data-ttu-id="9fb45-127">4\) threadA 執行 "Get"，並傳回 threadB 先前所加入的資料。</span><span class="sxs-lookup"><span data-stu-id="9fb45-127">4\) threadA performs a "Get", and returns the data that was previously added by threadB.</span></span>  
  
 <span data-ttu-id="9fb45-128">因此，不保證 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 所傳回的資料就是執行緒 valueFactory 所建立的相同資料。</span><span class="sxs-lookup"><span data-stu-id="9fb45-128">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's valueFactory.</span></span> <span data-ttu-id="9fb45-129">呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 時，可能會發生一系列類似的事件。</span><span class="sxs-lookup"><span data-stu-id="9fb45-129">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb45-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb45-130">See Also</span></span>  
 <span data-ttu-id="9fb45-131"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9fb45-131"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="9fb45-132">安全執行緒集合</span><span class="sxs-lookup"><span data-stu-id="9fb45-132">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

