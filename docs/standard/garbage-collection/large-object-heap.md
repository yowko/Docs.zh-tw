---
title: Windows 系統上的大型物件堆積
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff25d2cef52a8c690f895222d69591bc53b3765e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677162"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="dd6ee-102">Windows 系統上的大型物件堆積</span><span class="sxs-lookup"><span data-stu-id="dd6ee-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="dd6ee-103">.NET 記憶體回收行程 (GC) 會將物件區分成小型和大型的物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="dd6ee-104">當物件是大型時，它的一些屬性就會變得比物件是小型時更加重要。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="dd6ee-105">例如，要壓縮大型物件 (亦即，將記憶體中的大型物件複製到堆積上的其他地方) 時需要耗費大量資源。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="dd6ee-106">因為這個緣故，.NET 記憶體回收行程會將大型物件放在大型物件堆積 (LOH) 中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="dd6ee-107">在本主題中，我們將深入探討大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="dd6ee-108">我們將討論什麼條件才能將物件區分為大型物件，如何回收這些大型物件，以及大型物件對效能有何種影響。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd6ee-109">本主題只討論 Windows 系統上執行之 .NET Framework 和 .NET Core 的大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="dd6ee-110">它並未涵蓋在其他平台的 .NET 實作上執行的 LOH。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="dd6ee-111">物件最後如何送入大型物件堆積以及 GC 如何處理它們</span><span class="sxs-lookup"><span data-stu-id="dd6ee-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="dd6ee-112">如果物件大於或等於 85,000 個位元組，就會視為大型物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="dd6ee-113">這個數目取決於效能微調。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="dd6ee-114">當物件配置要求是針對 85,000 個以上的位元組時，執行階段會將它配置在大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="dd6ee-115">若要了解這表示什麼意思，請務必查看有關 .NET GC 的某些基本概念。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="dd6ee-116">.NET 記憶體回收行程是層代式的回收行程。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="dd6ee-117">它有三個層代：層代 0、層代 1 和層代 2。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="dd6ee-118">具有 3 個層代的原因是，在精密微調的應用程式中，大部分的物件都會在 gen0 中結束。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="dd6ee-119">例如，在伺服器應用程式中，與每個要求相關聯的配置應該在要求完成之後結束。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="dd6ee-120">執行中的配置要求則會進入 gen1，並且在該處結束。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="dd6ee-121">基本上，gen1 是扮演年輕物件區域與長期存留物件區域之間的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="dd6ee-122">小物件一律會配置在層代 0 中，並根據其存留期，可能會提升至層代 1 或層代 2。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="dd6ee-123">大型物件則一律配置在層代 2 中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="dd6ee-124">大型物件屬於層代 2，因為只有在層代 2 回收期間才會回收它們。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="dd6ee-125">回收層代時，也會回收其所有較年輕的層代。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="dd6ee-126">舉例來說，發生層代 1 GC 時，會同時回收層代 1 和 0。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="dd6ee-127">而發生層代 2 GC 時，就會回收整個堆積。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="dd6ee-128">基於這個理由，層代 2 GC 也稱為「完整 GC」。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="dd6ee-129">此文章引用層代 2 GC，而不是完整 GC，但這些詞彙可以互換。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="dd6ee-130">層代提供 GC 堆積的邏輯檢視。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="dd6ee-131">實際上，物件是存留在受控堆積區段中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="dd6ee-132">「受控堆積區段」是記憶體的區塊，由 GC 代替受控程式碼向 OS (透過呼叫 [VirtualAlloc 函式](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)) 要求保留。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="dd6ee-133">載入 CLR 時，GC 會配置兩個初始堆積區段：一個針對小型物件 (小型物件堆積或 SOH)，另一個針對大型物件 (大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="dd6ee-134">藉由將受控物件置於這些受控堆積區段中，就可以滿足配置的要求了。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="dd6ee-135">如果物件小於 85,000 個位元組，它會置於 SOH 的區段上；否則，它會置於 LOH 區段。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="dd6ee-136">隨著愈來愈多的物件配置在區段之上，這些區段就會被認可 (以較小的區塊)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="dd6ee-137">對於 SOH，在 GC 之後存留下來的物件會提升至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="dd6ee-138">層代 0 回收之後存留下來的物件目前被視為層代 1 物件，依此類推。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="dd6ee-139">然而，通過最老層代存留的物件仍可視為屬於最老的層代。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="dd6ee-140">換句話說，來自層代 2 的存留者就是層代 2 物件；來自 LOH 的存留者就是 LOH 的物件 (用 gen2 來回收)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="dd6ee-141">使用者的程式碼只能配置在層代 0 (小型物件) 或 LOH (大型物件) 中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="dd6ee-142">唯有 GC 才能「配置」物件於層代 1 (藉由提升來自層代 0 的存留者) 與層代 2 (藉由提升來自層代 1 和 2 的存留者) 中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="dd6ee-143">觸發記憶體回收時，GC 會追蹤所有作用中的物件，並且加以壓縮。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="dd6ee-144">但因為壓縮要耗費大量資源，所以 GC 會「掃除」LOH；這可將無作用物件建立成一份可用清單，稍後再用此清單來滿足大型物件配置的要求。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="dd6ee-145">鄰近的無作用物件會結合成為一個可用物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="dd6ee-146">.NET Core 和 .NET Framework (從 .NET Framework 4.5.1 開始) 包含 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> 屬性，可讓使用者指定 LOH 應該在下一個完整封鎖 GC 期間進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="dd6ee-147">而且在未來，.NET 可能會決定自動壓縮 LOH。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="dd6ee-148">這表示如果您配置了大型物件，並且想要確定它們不會更動，那麼您仍然應該將其固定。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="dd6ee-149">圖 1 說明的案例，是 GC 在第一個層代 0 GC 之後形成了層代 1，其中 `Obj1` 和 `Obj3` 已無作用；以及 GC 在第一個層代 1 GC 之後形成了層代 2，其中 `Obj2` 和 `Obj5` 已無作用。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="dd6ee-150">請注意，此圖和下圖僅供說明之用；它們包含一些物件，可更清楚顯示堆積上發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="dd6ee-151">事實上，GC 中通常涉及更多的物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-151">In reality, many more objects are typically involved in a GC.</span></span>

![圖 1：層代 0 GC 和層代 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="dd6ee-153">圖 1：層代 0 和層代 1 GC。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="dd6ee-154">圖 2 顯示在發現 `Obj1` 和 `Obj2` 無作用的層代 2 GC 之後，GC 會使用 `Obj1` 和 `Obj2` 曾經佔用的記憶體形成連續的可用空間，這之後將用來滿足 `Obj4` 的配置要求。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="dd6ee-155">在最後的物件 `Obj3` 之後，一直到區段結尾的空間，仍然可以用來滿足更多的配置要求。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![圖 2：在層代 2 GC 之後](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="dd6ee-157">圖 2：在層代 2 GC 之後</span><span class="sxs-lookup"><span data-stu-id="dd6ee-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="dd6ee-158">如果沒有足夠的可用空間來處理大型物件配置的要求，GC 會先嘗試從 OS 取得更多區段。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="dd6ee-159">如果該作業失敗，它就會觸發層代 2 GC，以期釋放一些空間。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="dd6ee-160">在層代 1 或層代 2 GC 期間，記憶體回收行程將沒有作用中物件的區段釋放歸還給 OS (藉由呼叫 [VirtualFree 函式](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree))。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="dd6ee-161">從最後的作用中物件到區段結尾的空間會取消認可。(gen0/gen1 存留的暫時區段除外，記憶體回收行程確實會保持部分已認可，因為您的應用程式將立即開始在其中配置)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="dd6ee-162">可用空間雖然重設過，但仍然是經認可的，這表示 OS 並不必將其中的資料寫回磁碟中。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="dd6ee-163">由於在層代 2 GC 期間只會收集 LOH，因此只能在這類 GC 期間釋放 LOH 區段。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="dd6ee-164">圖 3 說明的案例，是記憶體回收行程將一個區段 (區段 2) 釋放釋放歸還 OS，並在其餘區段上取消認可更多空間的情況。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="dd6ee-165">如果它必須使用位於區段結尾的已取消認可空間，來滿足大型物件配置要求，就會再次認可記憶體。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="dd6ee-166">(如需認可/取消認可的說明，請參閱 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 的文件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![圖 3：層代 2 GC 之後的 LOH](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="dd6ee-168">圖 3：層代 2 GC 之後的 LOH</span><span class="sxs-lookup"><span data-stu-id="dd6ee-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="dd6ee-169">何時收集大型物件？</span><span class="sxs-lookup"><span data-stu-id="dd6ee-169">When is a large object collected?</span></span>

<span data-ttu-id="dd6ee-170">一般情況下，發生下列 3 種情況其中之一時，就會發生 GC：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="dd6ee-171">配置超過層代 0 或大型物件的臨界值。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="dd6ee-172">臨界值是層代的屬性。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="dd6ee-173">當記憶體回收行程將物件配置到層代中時，就會設定層代的臨界值。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="dd6ee-174">若超過臨界值，則會在該層代上觸發 GC。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="dd6ee-175">當您配置小型或大型物件時，會分別取用層代 0 和 LOH 的臨界值。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="dd6ee-176">如果記憶體回收行程配置到層代 1 和 2，就會取用其臨界值。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="dd6ee-177">這些臨界值會隨著程式的執行而動態地調整。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="dd6ee-178">這是一般的情況；大部分 GC 的發生原因是由於受控堆積上的配置。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="dd6ee-179">已呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="dd6ee-180">如果呼叫無參數的 <xref:System.GC.Collect?displayProperty=nameWithType> 方法或另一個多載傳遞 <xref:System.GC.MaxGeneration?displayProperty=nameWithType> 作為引數，LOH 會連同受控堆積的其餘部分一起回收。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="dd6ee-181">系統處於記憶體不足的狀況。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="dd6ee-182">當記憶體回收行程從 OS 收到高記憶體通知時，會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="dd6ee-183">如果記憶體回收行程認為執行層代 2 GC 會提高生產力，則會觸發層代 2 GC。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="dd6ee-184">LOH 效能的影響</span><span class="sxs-lookup"><span data-stu-id="dd6ee-184">LOH Performance Implications</span></span>

<span data-ttu-id="dd6ee-185">大型物件堆積上的配置會以下列方式影響效能。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="dd6ee-186">配置成本。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-186">Allocation cost.</span></span>

  <span data-ttu-id="dd6ee-187">CLR 會保證它送出的每個新物件都已清除。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="dd6ee-188">這表示大型物件的配置成本，是完全由記憶體清除來掌控的 (除非它觸發 GC)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="dd6ee-189">如果要花 2 個週期的時間才能清除一個位元組，就表示要花 170,000 個週期才能清除最小的大型物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="dd6ee-190">在 2GHz 電腦上清除 16MB 物件的記憶體大約需要 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="dd6ee-191">這是相當大的成本。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-191">That's a rather large cost.</span></span>

- <span data-ttu-id="dd6ee-192">回收成本。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-192">Collection cost.</span></span>

  <span data-ttu-id="dd6ee-193">因為 LOH 和層代 2 會一起回收，如果超過其中一個的臨界值時，就會觸發層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="dd6ee-194">如果因為 LOH 而觸發了層代 2 回收，那麼在 GC 之後，層代 2 不一定會變得更小。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="dd6ee-195">如果在層代 2 上沒有太多資料，其影響極小。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="dd6ee-196">但是如果層代 2 很大，一旦觸發許多層代 2 GC，就可能會造成效能問題。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="dd6ee-197">如果暫時配置了許多大型物件，而且您的 SOH 很大，則執行 GC 可能會花費太多時間。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="dd6ee-198">此外，如果您繼續配置並釋放相當大的物件，配置的成本就會暴增。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="dd6ee-199">含有參考類型的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-199">Array elements with reference types.</span></span>

  <span data-ttu-id="dd6ee-200">LOH 上的非常大型物件通常都是陣列 (非常大的執行個體物件極為罕見)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="dd6ee-201">如果陣列中的元素有許多參考，則會帶來元素中沒有許多參考時不會具有的成本。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="dd6ee-202">如果元素未包含任何參考，記憶體回收行程根本不需要處理整個陣列。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="dd6ee-203">例如，如果您使用陣列來儲存二元樹狀結構中的節點，實作它的方法之一，就是根據所有實際節點，逐一參考節點的右邊和左邊節點：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="dd6ee-204">如果 `num_nodes` 很大，記憶體回收行程需要每個元素至少處理兩個參考。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="dd6ee-205">另一個方法是儲存右邊與左邊節點的索引：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="dd6ee-206">請不要將左邊節點的資料參考為 `left.d`，應將它參考為 `binary_tr[left_index].d`。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="dd6ee-207">而記憶體回收行程不需要查看左邊和右邊節點的任何參考。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="dd6ee-208">在這三個因素中，前兩個通常比第三個更加重要。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="dd6ee-209">因此，建議您配置可複使用的大型物件集區，而不是配置暫存大型物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="dd6ee-210">收集 LOH 的效能資料</span><span class="sxs-lookup"><span data-stu-id="dd6ee-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="dd6ee-211">收集特定區域的效能資料之前，您應該已經完成下列作業：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="dd6ee-212">已找到您應該查看此區域的證據。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="dd6ee-213">已排除您所知未找到任何項目能夠說明所看到效能問題的其他區域。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="dd6ee-214">如需記憶體和 CPU 基本概念的詳細資訊，請參閱部落格 [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) (了解問題，再嘗試找出解決方案)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="dd6ee-215">您可以使用下列工具來收集 LOH 效能的相關資料：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="dd6ee-216">.NET CLR 記憶體效能計數器</span><span class="sxs-lookup"><span data-stu-id="dd6ee-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="dd6ee-217">ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dd6ee-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="dd6ee-218">偵錯工具</span><span class="sxs-lookup"><span data-stu-id="dd6ee-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="dd6ee-219">.NET CLR 記憶體效能計數器</span><span class="sxs-lookup"><span data-stu-id="dd6ee-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="dd6ee-220">在調查效能問題時，這些效能計數器通常是很好的起點 (即使我們建議您使用 [ETW 事件](#etw-events))。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="dd6ee-221">您可以新增所需的計數器來設定效能監視器，如圖 4 所示。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="dd6ee-222">與 LOH 相關的是：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="dd6ee-223">**層代 2 回收**</span><span class="sxs-lookup"><span data-stu-id="dd6ee-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="dd6ee-224">顯示自處理序啟動後發生層代 2 GC 的次數。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="dd6ee-225">此計數器會在層代 2 回收 (也稱為完整記憶體回收) 的結尾處遞增。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="dd6ee-226">此計數器會顯示最後觀察到的值。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="dd6ee-227">**Large Object Heap size**</span><span class="sxs-lookup"><span data-stu-id="dd6ee-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="dd6ee-228">顯示 LOH 的目前大小 (以位元組為單位)，包括可用空間。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="dd6ee-229">這個計數器於記憶體回收的結尾更新，而非每次配置時更新。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="dd6ee-230">查看效能計數器的常用方式，就是利用效能監視器 (perfmon.exe)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="dd6ee-231">請使用 [新增計數器]，為您關心的處理序新增有意義的計數器。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="dd6ee-232">您可以將效能計數器資料儲存到記錄檔中，如圖 4 所示。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![圖 4：新增效能計數器。](media/loh/perfcounter.png)\
<span data-ttu-id="dd6ee-234">圖 4：層代 2 GC 之後的 LOH</span><span class="sxs-lookup"><span data-stu-id="dd6ee-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="dd6ee-235">效能計數器也可以用程式設計的方式來查詢。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="dd6ee-236">許多人都會使用這種方式在日常測試程序中收集相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="dd6ee-237">當他們發覺到計數器有不正常的數值時，就可以使用其他方式取得詳細資料，來協助進行調查。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="dd6ee-238">建議您使用 ETW 事件而不是效能計數器，因為 ETW 提供更豐富的資訊。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="dd6ee-239">ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dd6ee-239">ETW events</span></span>

<span data-ttu-id="dd6ee-240">記憶體回收行程提供一組豐富的 ETW 事件，可協助您了解堆積正在執行的作業和原因。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="dd6ee-241">下列部落格文章顯示如何收集和了解使用 ETW 的 GC 事件：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- <span data-ttu-id="dd6ee-242">[GC ETW Events - 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/) (GC ETW 事件 - 1)</span><span class="sxs-lookup"><span data-stu-id="dd6ee-242">[GC ETW Events - 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)</span></span>

- <span data-ttu-id="dd6ee-243">[GC ETW Events - 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/) (GC ETW 事件 - 2)</span><span class="sxs-lookup"><span data-stu-id="dd6ee-243">[GC ETW Events - 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)</span></span>

- <span data-ttu-id="dd6ee-244">[GC ETW Events - 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/) (GC ETW 事件 - 3)</span><span class="sxs-lookup"><span data-stu-id="dd6ee-244">[GC ETW Events - 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)</span></span>

- <span data-ttu-id="dd6ee-245">[GC ETW Events - 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/) (GC ETW 事件 - 4)</span><span class="sxs-lookup"><span data-stu-id="dd6ee-245">[GC ETW Events - 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)</span></span>

<span data-ttu-id="dd6ee-246">若要識別暫存 LOH 配置所造成的過多層代 2 GC，請查看 GC 的 [Trigger Reason] \(觸發原因\) 資料行。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="dd6ee-247">對於只配置暫存大型物件的簡單測試，您可以使用下列 [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) 命令列收集 ETW 事件的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="dd6ee-248">結果看起來如下：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-248">The result is something like this:</span></span>

<span data-ttu-id="dd6ee-249">![圖 5：使用 PerfView 檢查 ETW 事件](media/loh/perfview.png) 圖 5：使用 PerfView 顯示的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dd6ee-249">![Figure 5: Examining ETW events using PerfView](media/loh/perfview.png) Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="dd6ee-250">如您所見，所有的 GC 都是層代 2 GC，而且它們都是由 AllocLarge 所觸發，這表示配置大型物件時觸發了此 GC。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-250">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="dd6ee-251">我們知道這些配置是暫時的，因為 [LOH Survival Rate %] \(LOH 未回收率 %\) 資料行顯示 1%。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-251">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="dd6ee-252">您可以收集其他 ETW 事件，讓您知道何者配置了這些大型物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-252">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="dd6ee-253">下列命令列：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-253">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="dd6ee-254">會收集 AllocationTick 事件，大約每隔 100K 的配置就會引發該事件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-254">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="dd6ee-255">換句話說，每次配置大型物件時，就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-255">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="dd6ee-256">接著，您可以查看其中一個 GC 堆積配置檢視，這些檢視可向您顯示已配置大型物件的呼叫堆疊：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-256">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

![圖 6：GC 堆積配置檢視](media/loh/perfview2.png)\
<span data-ttu-id="dd6ee-258">圖 6：GC 堆積配置檢視</span><span class="sxs-lookup"><span data-stu-id="dd6ee-258">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="dd6ee-259">如您所見，這是非常簡單的測試，只會從其 `Main` 方法配置大型物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-259">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="dd6ee-260">偵錯工具</span><span class="sxs-lookup"><span data-stu-id="dd6ee-260">A debugger</span></span>

<span data-ttu-id="dd6ee-261">如果您只具有記憶體傾印，而且需要查看哪些物件實際在 LOH 上，您可以使用 .NET 所提供的 [SoS 偵錯工具延伸模組](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-261">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="dd6ee-262">本節中提及的偵錯命令適用於 [Windows 偵錯工具](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-262">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="dd6ee-263">下圖顯示分析 LOH 的範例輸出：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-263">The following shows sample output from analyzing the LOH:</span></span>

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="dd6ee-264">LOH 堆積的大小是 (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 個位元組。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-264">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="dd6ee-265">在位址 023e1000 和 033db630 之間，<xref:System.Object?displayProperty=nameWithType> 物件的陣列佔用了 8,008,736 個位元組、<xref:System.Byte?displayProperty=nameWithType> 物件的陣列佔用了 6,663,696 個位元組，而可用空間佔用了 2,081,792 個位元組。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-265">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="dd6ee-266">有時候，偵錯工具會顯示 LOH 大小總計是小於 85,000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-266">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="dd6ee-267">這是因為執行階段本身會使用 LOH 來配置一些比大型物件小的物件。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-267">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="dd6ee-268">因為 LOH 並未壓縮，所以有時候 LOH 會被認為是造成片段的來源。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-268">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="dd6ee-269">片段意指：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-269">Fragmentation means:</span></span>

- <span data-ttu-id="dd6ee-270">受控堆積的片段，以受管理物件之間的可用空間數量表示。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-270">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="dd6ee-271">在 SoS 中，`!dumpheap –type Free` 命令會顯示受控物件之間的可用空間數量。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-271">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="dd6ee-272">虛擬記憶體 (VM) 位址空間的片段，這是標示為 `MEM_FREE` 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-272">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="dd6ee-273">您可以在 windbg 中使用各種偵錯工具命令來取得它。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-273">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="dd6ee-274">下列範例會顯示 VM 空間中的片段：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-274">The following example shows fragmentation in the VM space:</span></span>

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="dd6ee-275">經常可以看到 VM 片段，這是由需要經常進行記憶體回收的暫存大型物件所造成的，因為這樣才能從 OS 取得新的受控堆積區段，並將空的區段釋放歸還給 OS。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-275">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="dd6ee-276">若要驗證 LOH 是否會造成 VM 片段，您可以在 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 和 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) 上設定中斷點，以查看何者會呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-276">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="dd6ee-277">例如，若要查看何者會嘗試從 OS 配置大於 8MB 的虛擬記憶體區塊，您可以設定中斷點如下：</span><span class="sxs-lookup"><span data-stu-id="dd6ee-277">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="dd6ee-278">此命令會中斷並進入偵錯工具，並且只有在配置大小大於 8MB (0x800000) 的情況下呼叫 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 時，才會顯示呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-278">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="dd6ee-279">CLR 2.0 中新增了稱為 *VM Hoarding* 的功能，對於經常取得再釋放區段 (包括在大型與小型物件堆積上) 的案例，此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-279">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="dd6ee-280">若要指定 VM Hoarding，您可以透過裝載 API 指定稱為 `STARTUP_HOARD_GC_VM` 的啟動旗標。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-280">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="dd6ee-281">CLR 會取消認可這些區段上的記憶體並將其放置於待命清單上，而不會將空的區段釋放歸還給 OS。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-281">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="dd6ee-282">(請注意，CLR 不會對太大的區段執行此操作)。CLR 稍後會使用這些區段來滿足新的區段要求。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-282">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="dd6ee-283">下次您的應用程式需要新的區段時，CLR 如果能夠找到夠大的區段，就會使用此待命清單中的區段。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-283">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="dd6ee-284">對於想要保存已取得區段以避免發生記憶體不足例外狀況的應用程式 (例如本身是系統上所執行之主控項應用程式的某些伺服器應用程式) 來說，VM hoarding 也很有用。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-284">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="dd6ee-285">強烈建議您在使用此功能時仔細測試應用程式，以確保應用程式的記憶體使用情形相當穩定。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-285">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
