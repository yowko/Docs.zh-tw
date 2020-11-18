---
title: 在 ConcurrentDictionary 中新增和移除項目
description: 閱讀如何在 .NET 中新增、取出、更新和移除 ConcurrentDictionary<TKey、Tvalue>> 集合類別中專案的範例。
ms.date: 05/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 17d820aba564d467152c52c7a0352bbc860f548b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823806"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="1a3e7-103">如何新增和移除 ConcurrentDictionary 中的專案</span><span class="sxs-lookup"><span data-stu-id="1a3e7-103">How to add and remove items from a ConcurrentDictionary</span></span>

<span data-ttu-id="1a3e7-104">這個範例示範如何新增、擷取、更新和移除 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> 中的項目。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-104">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a3e7-105">這個集合類別是安全執行緒實作。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-105">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="1a3e7-106">只要多個執行緒可能嘗試同時存取元素，就建議您使用它。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-106">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>

<span data-ttu-id="1a3e7-107"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>供幾種便利的方法，讓程式碼不需要在嘗試新增或移除資料之前，先檢查索引鍵存在與否。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-107"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="1a3e7-108">下表列出這些便利方法，並描述其使用時機。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-108">The following table lists these convenience methods and describes when to use them.</span></span>

| <span data-ttu-id="1a3e7-109">方法</span><span class="sxs-lookup"><span data-stu-id="1a3e7-109">Method</span></span> | <span data-ttu-id="1a3e7-110">使用時機...</span><span class="sxs-lookup"><span data-stu-id="1a3e7-110">Use when…</span></span> |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | <span data-ttu-id="1a3e7-111">您想要新增所指定索引鍵的新值，如果已經有索引鍵，則您會想要取代它的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-111">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span> |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | <span data-ttu-id="1a3e7-112">您想要擷取所指定索引鍵的現有值，如果索引鍵不存在，則您會想要指定索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-112">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span> |
| <span data-ttu-id="1a3e7-113"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="1a3e7-113"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span> | <span data-ttu-id="1a3e7-114">您想要新增、取得、更新或移除索引鍵/值組，如果已經有索引鍵，或嘗試因任何其他原因而失敗，則您會想要採取一些替代動作。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-114">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span> |

## <a name="example"></a><span data-ttu-id="1a3e7-115">範例</span><span class="sxs-lookup"><span data-stu-id="1a3e7-115">Example</span></span>

<span data-ttu-id="1a3e7-116">下列範例使用兩個 <xref:System.Threading.Tasks.Task> 執行個體同時將一些項目新增至 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>，然後輸出所有內容以顯示已成功新增項目。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-116">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="1a3e7-117">此範例也會示範如何使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 、 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 和方法， <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 從集合中加入、更新及取出專案。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-117">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve items from the collection.</span></span>

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<span data-ttu-id="1a3e7-118"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是針對多執行緒案例所設計。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-118"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="1a3e7-119">您不需要在程式碼中使用鎖定，即可新增或移除集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-119">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="1a3e7-120">不過，其中一個執行緒一定要可以擷取一個值，而另一個執行緒要將新的值提供給相同的索引鍵來立即更新集合。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-120">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>

<span data-ttu-id="1a3e7-121">此外，雖然 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的所有方法都是安全執行緒，但是並非所有方法都是不可部分完成，尤其是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-121">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="1a3e7-122">為了避免未知的程式碼封鎖所有線程，傳遞給這些方法的使用者委派是在字典內部鎖定之外叫用。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-122">To prevent unknown code from blocking all threads, the user delegate that's passed to these methods is invoked outside of the dictionary's internal lock.</span></span> <span data-ttu-id="1a3e7-123">因此，可能會發生這一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="1a3e7-123">Therefore, it's possible for this sequence of events to occur:</span></span>

1. <span data-ttu-id="1a3e7-124">_threadA_ 呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 、找不到專案，並藉由叫用委派來建立要加入的新專案 `valueFactory` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-124">_threadA_ calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item, and creates a new item to add by invoking the `valueFactory` delegate.</span></span>

1. <span data-ttu-id="1a3e7-125">_threadB_ <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 會同時呼叫它的 `valueFactory` 委派，並在 _threadA_ 之前到達內部鎖定，因此會將其新的索引鍵/值組加入字典中。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-125">_threadB_ calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its `valueFactory` delegate is invoked and it arrives at the internal lock before _threadA_, and so its new key-value pair is added to the dictionary.</span></span>

1. <span data-ttu-id="1a3e7-126">_threadA 的_ 使用者委派完成，而且執行緒到達鎖定，但是現在會看到該專案已經存在。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-126">_threadA's_ user delegate completes, and the thread arrives at the lock, but now sees that the item exists already.</span></span>

1. <span data-ttu-id="1a3e7-127">_threadA_ 會執行 "Get"，並傳回 _threadB_ 先前新增的資料。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-127">_threadA_ performs a "Get" and returns the data that was previously added by _threadB_.</span></span>

<span data-ttu-id="1a3e7-128">因此，不保證所傳回的資料 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 是執行緒所建立的相同資料 `valueFactory` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-128">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's `valueFactory`.</span></span> <span data-ttu-id="1a3e7-129">呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 時，可能會發生一系列類似的事件。</span><span class="sxs-lookup"><span data-stu-id="1a3e7-129">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a3e7-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a3e7-130">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="1a3e7-131">安全執行緒集合</span><span class="sxs-lookup"><span data-stu-id="1a3e7-131">Thread-Safe Collections</span></span>](index.md)
