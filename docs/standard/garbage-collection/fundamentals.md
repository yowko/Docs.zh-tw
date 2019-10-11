---
title: 記憶體回收的基本概念
description: 了解記憶體回收行程如何運作，以及如何為它設定最佳效能。
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0fa0e2c59856beda65ec5804b8896352db98b3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180186"
---
# <a name="fundamentals-of-garbage-collection"></a><span data-ttu-id="01c91-103">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="01c91-103">Fundamentals of garbage collection</span></span>

<a name="top"></a> <span data-ttu-id="01c91-104">在 Common Language Runtime (CLR) 中，記憶體回收行程會當做自動記憶體管理員。</span><span class="sxs-lookup"><span data-stu-id="01c91-104">In the common language runtime (CLR), the garbage collector serves as an automatic memory manager.</span></span> <span data-ttu-id="01c91-105">它提供了下列優點：</span><span class="sxs-lookup"><span data-stu-id="01c91-105">It provides the following benefits:</span></span>

- <span data-ttu-id="01c91-106">可讓您開發應用程式，而不需要為您建立的物件手動釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-106">Enables you to develop your application without having to manually free memory for objects you create.</span></span>

- <span data-ttu-id="01c91-107">有效率地在 Managed 堆積上配置物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-107">Allocates objects on the managed heap efficiently.</span></span>

- <span data-ttu-id="01c91-108">回收不再使用的物件、清除其記憶體，並且讓記憶體可供未來的配置使用。</span><span class="sxs-lookup"><span data-stu-id="01c91-108">Reclaims objects that are no longer being used, clears their memory, and keeps the memory available for future allocations.</span></span> <span data-ttu-id="01c91-109">Managed 物件在開始時會自動取得乾淨的內容，因此其建構函式不需要初始化每個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="01c91-109">Managed objects automatically get clean content to start with, so their constructors do not have to initialize every data field.</span></span>

- <span data-ttu-id="01c91-110">確保某個物件無法使用另一個物件的內容，藉以提供記憶體安全性。</span><span class="sxs-lookup"><span data-stu-id="01c91-110">Provides memory safety by making sure that an object cannot use the content of another object.</span></span>

 <span data-ttu-id="01c91-111">本主題描述記憶體回收的核心概念。</span><span class="sxs-lookup"><span data-stu-id="01c91-111">This topic describes the core concepts of garbage collection.</span></span>

<a name="fundamentals_of_memory"></a>

## <a name="fundamentals-of-memory"></a><span data-ttu-id="01c91-112">記憶體的基本概念</span><span class="sxs-lookup"><span data-stu-id="01c91-112">Fundamentals of memory</span></span>

<span data-ttu-id="01c91-113">下列清單摘要說明重要的 CLR 記憶體概念。</span><span class="sxs-lookup"><span data-stu-id="01c91-113">The following list summarizes important CLR memory concepts.</span></span>

- <span data-ttu-id="01c91-114">每個處理序都有各自獨立的虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="01c91-114">Each process has its own, separate virtual address space.</span></span> <span data-ttu-id="01c91-115">同一部電腦上的所有處理序會共用相同的實體記憶體，並且共用分頁檔 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="01c91-115">All processes on the same computer share the same physical memory, and share the page file if there is one.</span></span>

- <span data-ttu-id="01c91-116">根據預設，在 32 位元電腦上，每個處理序都有 2 GB 使用者模式虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="01c91-116">By default, on 32-bit computers, each process has a 2-GB user-mode virtual address space.</span></span>

- <span data-ttu-id="01c91-117">身為應用程式開發人員，您只會處理虛擬位址空間，絕不會直接操作實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-117">As an application developer, you work only with virtual address space and never manipulate physical memory directly.</span></span> <span data-ttu-id="01c91-118">記憶體回收行程會在 Managed 堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-118">The garbage collector allocates and frees virtual memory for you on the managed heap.</span></span>

  <span data-ttu-id="01c91-119">如果您要撰寫原生程式碼，可使用 Win32 函式來處理虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="01c91-119">If you are writing native code, you use Win32 functions to work with the virtual address space.</span></span> <span data-ttu-id="01c91-120">這些函式會在原生堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-120">These functions allocate and free virtual memory for you on native heaps.</span></span>

- <span data-ttu-id="01c91-121">虛擬記憶體可以有三種狀態：</span><span class="sxs-lookup"><span data-stu-id="01c91-121">Virtual memory can be in three states:</span></span>

  - <span data-ttu-id="01c91-122">可用。</span><span class="sxs-lookup"><span data-stu-id="01c91-122">Free.</span></span> <span data-ttu-id="01c91-123">記憶體區塊沒有任何參考，可進行配置。</span><span class="sxs-lookup"><span data-stu-id="01c91-123">The block of memory has no references to it and is available for allocation.</span></span>

  - <span data-ttu-id="01c91-124">保留的。</span><span class="sxs-lookup"><span data-stu-id="01c91-124">Reserved.</span></span> <span data-ttu-id="01c91-125">記憶體區塊可供您使用，但是無法用於任何其他配置要求。</span><span class="sxs-lookup"><span data-stu-id="01c91-125">The block of memory is available for your use and cannot be used for any other allocation request.</span></span> <span data-ttu-id="01c91-126">不過，在此記憶體區塊認可之前，您無法將資料儲存到其中。</span><span class="sxs-lookup"><span data-stu-id="01c91-126">However, you cannot store data to this memory block until it is committed.</span></span>

  - <span data-ttu-id="01c91-127">已認可。</span><span class="sxs-lookup"><span data-stu-id="01c91-127">Committed.</span></span> <span data-ttu-id="01c91-128">記憶體區塊會指派給實體儲存區。</span><span class="sxs-lookup"><span data-stu-id="01c91-128">The block of memory is assigned to physical storage.</span></span>

- <span data-ttu-id="01c91-129">虛擬位址空間可能會分成片段。</span><span class="sxs-lookup"><span data-stu-id="01c91-129">Virtual address space can get fragmented.</span></span> <span data-ttu-id="01c91-130">這表示，位址空間中有可用的區塊，也稱為可用的洞 (Hole)。</span><span class="sxs-lookup"><span data-stu-id="01c91-130">This means that there are free blocks, also known as holes, in the address space.</span></span> <span data-ttu-id="01c91-131">要求虛擬記憶體配置時，虛擬記憶體管理程式必須找到大小可滿足配置要求的單一可用區塊。</span><span class="sxs-lookup"><span data-stu-id="01c91-131">When a virtual memory allocation is requested, the virtual memory manager has to find a single free block that is large enough to satisfy that allocation request.</span></span> <span data-ttu-id="01c91-132">即使您擁有 2GB 可用空間，要求 2GB 的配置仍然不會成功，除非該可用空間全都在單一位址區塊中。</span><span class="sxs-lookup"><span data-stu-id="01c91-132">Even if you have 2 GB of free space, the allocation that requires 2 GB will be unsuccessful unless all of that free space is in a single address block.</span></span>

- <span data-ttu-id="01c91-133">如果您用盡保留用的虛擬位址空間或認可用的實體空間，則可能會用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-133">You can run out of memory if you run out of virtual address space to reserve or physical space to commit.</span></span>

<span data-ttu-id="01c91-134">即使實體記憶體壓力 (也就是實體記憶體的需求) 不高，仍會使用您的分頁檔。</span><span class="sxs-lookup"><span data-stu-id="01c91-134">Your page file is used even if physical memory pressure (that is, demand for physical memory) is low.</span></span> <span data-ttu-id="01c91-135">您的實體記憶體第一次面臨壓力高的情況時，作業系統必須釋出實體記憶體的空間來儲存資料，而且它會將實體記憶體中的部分資料備份到分頁檔。</span><span class="sxs-lookup"><span data-stu-id="01c91-135">The first time your physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file.</span></span> <span data-ttu-id="01c91-136">該資料只會在需要時進行分頁，因此可能在實體記憶體壓力相當低的情況下發生分頁。</span><span class="sxs-lookup"><span data-stu-id="01c91-136">That data is not paged until it is needed, so it is possible to encounter paging in situations where the physical memory pressure is very low.</span></span>

[<span data-ttu-id="01c91-137">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-137">Back to top</span></span>](#top)

<a name="conditions_for_a_garbage_collection"></a>

## <a name="conditions-for-a-garbage-collection"></a><span data-ttu-id="01c91-138">記憶體回收的條件</span><span class="sxs-lookup"><span data-stu-id="01c91-138">Conditions for a garbage collection</span></span>

<span data-ttu-id="01c91-139">當下列其中一個條件成立時，就會進行記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="01c91-139">Garbage collection occurs when one of the following conditions is true:</span></span>

- <span data-ttu-id="01c91-140">系統的實體記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="01c91-140">The system has low physical memory.</span></span> <span data-ttu-id="01c91-141">這是透過來自 OS 的低記憶體通知或由主機指出的低記憶體來偵測。</span><span class="sxs-lookup"><span data-stu-id="01c91-141">This is detected by either the low memory notification from the OS or low memory indicated by the host.</span></span>

- <span data-ttu-id="01c91-142">由 Managed 堆積上之已配置物件所使用的記憶體超過可接受的臨界值。</span><span class="sxs-lookup"><span data-stu-id="01c91-142">The memory that is used by allocated objects on the managed heap surpasses an acceptable threshold.</span></span> <span data-ttu-id="01c91-143">這個臨界值會在處理序執行時持續調整。</span><span class="sxs-lookup"><span data-stu-id="01c91-143">This threshold is continuously adjusted as the process runs.</span></span>

- <span data-ttu-id="01c91-144">已呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="01c91-144">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="01c91-145">在大多數的情況下，您不需要呼叫這個方法，因為記憶體回收行程會持續執行。</span><span class="sxs-lookup"><span data-stu-id="01c91-145">In almost all cases, you do not have to call this method, because the garbage collector runs continuously.</span></span> <span data-ttu-id="01c91-146">這個方法主要用於獨特的情況和測試。</span><span class="sxs-lookup"><span data-stu-id="01c91-146">This method is primarily used for unique situations and testing.</span></span>

[<span data-ttu-id="01c91-147">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-147">Back to top</span></span>](#top)

<a name="the_managed_heap"></a>

## <a name="the-managed-heap"></a><span data-ttu-id="01c91-148">Managed 堆積</span><span class="sxs-lookup"><span data-stu-id="01c91-148">The managed heap</span></span>

<span data-ttu-id="01c91-149">CLR 初始化記憶體回收行程之後，記憶體回收行程就會配置用來儲存和管理物件的記憶體區段。</span><span class="sxs-lookup"><span data-stu-id="01c91-149">After the garbage collector is initialized by the CLR, it allocates a segment of memory to store and manage objects.</span></span> <span data-ttu-id="01c91-150">這個記憶體稱為 Managed 堆積，與作業系統中的原生堆積相反。</span><span class="sxs-lookup"><span data-stu-id="01c91-150">This memory is called the managed heap, as opposed to a native heap in the operating system.</span></span>

<span data-ttu-id="01c91-151">每個 Managed 處理序都有一個 Managed 堆積。</span><span class="sxs-lookup"><span data-stu-id="01c91-151">There is a managed heap for each managed process.</span></span> <span data-ttu-id="01c91-152">處理序中的所有執行緒都會對相同堆積上的物件配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-152">All threads in the process allocate memory for objects on the same heap.</span></span>

<span data-ttu-id="01c91-153">為節省記憶體，記憶體回收行程會呼叫 Win32 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 函式，並且針對 Managed 應用程式一次保留一個記憶體區段。</span><span class="sxs-lookup"><span data-stu-id="01c91-153">To reserve memory, the garbage collector calls the Win32 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function, and reserves one segment of memory at a time for managed applications.</span></span> <span data-ttu-id="01c91-154">記憶體回收行程也會視需要保留區段，並且透過呼叫 Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) 函式，將區段釋放回作業系統 (在清除任何物件的區段之後)。</span><span class="sxs-lookup"><span data-stu-id="01c91-154">The garbage collector also reserves segments as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01c91-155">記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="01c91-155">The size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="01c91-156">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="01c91-156">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

<span data-ttu-id="01c91-157">配置在堆積上的物件越少，記憶體回收行程必須進行的工作就越少。</span><span class="sxs-lookup"><span data-stu-id="01c91-157">The fewer objects allocated on the heap, the less work the garbage collector has to do.</span></span> <span data-ttu-id="01c91-158">當您配置物件時，請勿使用超出需求的進位值，例如，當您只需要 15 個位元組時，卻配置 32 個位元組的陣列。</span><span class="sxs-lookup"><span data-stu-id="01c91-158">When you allocate objects, do not use rounded-up values that exceed your needs, such as allocating an array of 32 bytes when you need only 15 bytes.</span></span>

<span data-ttu-id="01c91-159">觸發記憶體回收時，記憶體回收行程就會回收無作用物件所佔據的記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-159">When a garbage collection is triggered, the garbage collector reclaims the memory that is occupied by dead objects.</span></span> <span data-ttu-id="01c91-160">回收處理序會壓縮使用中物件，讓它們集合在一起，並且移除無作用物件，因而讓堆積更小。</span><span class="sxs-lookup"><span data-stu-id="01c91-160">The reclaiming process compacts live objects so that they are moved together, and the dead space is removed, thereby making the heap smaller.</span></span> <span data-ttu-id="01c91-161">這樣可確保一起配置的物件會在 Managed 堆積上集中，以便保持其區域性。</span><span class="sxs-lookup"><span data-stu-id="01c91-161">This ensures that objects that are allocated together stay together on the managed heap, to preserve their locality.</span></span>

<span data-ttu-id="01c91-162">記憶體回收的干擾程度 (頻率和持續期間) 是 Managed 堆積上之配置量和未被回收記憶體數量的結果。</span><span class="sxs-lookup"><span data-stu-id="01c91-162">The intrusiveness (frequency and duration) of garbage collections is the result of the volume of allocations and the amount of survived memory on the managed heap.</span></span>

<span data-ttu-id="01c91-163">您可以將此堆積視為兩個堆積的累積：[大型物件堆積](large-object-heap.md)和小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="01c91-163">The heap can be considered as the accumulation of two heaps: the [large object heap](large-object-heap.md) and the small object heap.</span></span>

<span data-ttu-id="01c91-164">[大型物件堆積](large-object-heap.md)包含 85,000 個位元組以上的超大型物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-164">The [large object heap](large-object-heap.md) contains very large objects that are 85,000 bytes and larger.</span></span> <span data-ttu-id="01c91-165">大型物件堆積上的物件通常是陣列。</span><span class="sxs-lookup"><span data-stu-id="01c91-165">The objects on the large object heap are usually arrays.</span></span> <span data-ttu-id="01c91-166">超大型的執行個體物件非常罕見。</span><span class="sxs-lookup"><span data-stu-id="01c91-166">It is rare for an instance object to be extremely large.</span></span>

[<span data-ttu-id="01c91-167">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-167">Back to top</span></span>](#top)

<a name="generations"></a>

## <a name="generations"></a><span data-ttu-id="01c91-168">層代</span><span class="sxs-lookup"><span data-stu-id="01c91-168">Generations</span></span>

<span data-ttu-id="01c91-169">堆積會組織成層代，因此它可以處理存留較久和存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-169">The heap is organized into generations so it can handle long-lived and short-lived objects.</span></span> <span data-ttu-id="01c91-170">記憶體回收主要與存留較短物件的回收一起進行，而這些物件通常只佔據堆積的一小部分。</span><span class="sxs-lookup"><span data-stu-id="01c91-170">Garbage collection primarily occurs with the reclamation of short-lived objects that typically occupy only a small part of the heap.</span></span> <span data-ttu-id="01c91-171">堆積上的物件有三個層代：</span><span class="sxs-lookup"><span data-stu-id="01c91-171">There are three generations of objects on the heap:</span></span>

- <span data-ttu-id="01c91-172">**層代 0**。</span><span class="sxs-lookup"><span data-stu-id="01c91-172">**Generation 0**.</span></span> <span data-ttu-id="01c91-173">這是最新的層代而且包含存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-173">This is the youngest generation and contains short-lived objects.</span></span> <span data-ttu-id="01c91-174">存留較短的物件範例是暫存變數。</span><span class="sxs-lookup"><span data-stu-id="01c91-174">An example of a short-lived object is a temporary variable.</span></span> <span data-ttu-id="01c91-175">記憶體回收最常在這個層代中進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-175">Garbage collection occurs most frequently in this generation.</span></span>

  <span data-ttu-id="01c91-176">新配置的物件會構成新的物件層代而且隱含成為層代 0 回收，但如果它們是大型物件，就會移至層代 2 回收中的大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="01c91-176">Newly allocated objects form a new generation of objects and are implicitly generation 0 collections, unless they are large objects, in which case they go on the large object heap in a generation 2 collection.</span></span>

  <span data-ttu-id="01c91-177">大部分物件都會在層代 0 的記憶體回收中回收，而且不會存留至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="01c91-177">Most objects are reclaimed for garbage collection in generation 0 and do not survive to the next generation.</span></span>

- <span data-ttu-id="01c91-178">**層代 1**。</span><span class="sxs-lookup"><span data-stu-id="01c91-178">**Generation 1**.</span></span> <span data-ttu-id="01c91-179">這個層代包含存留較短的物件，而且當做存留較短物件與存留較長物件之間的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="01c91-179">This generation contains short-lived objects and serves as a buffer between short-lived objects and long-lived objects.</span></span>

- <span data-ttu-id="01c91-180">**層代 2**。</span><span class="sxs-lookup"><span data-stu-id="01c91-180">**Generation 2**.</span></span> <span data-ttu-id="01c91-181">這個層代包含存留較長的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-181">This generation contains long-lived objects.</span></span> <span data-ttu-id="01c91-182">存留較長的物件範例是伺服器應用程式中包含處理序持續期間存留之靜態資料的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-182">An example of a long-lived object is an object in a server application that contains static data that is live for the duration of the process.</span></span>

<span data-ttu-id="01c91-183">當條件許可時，記憶體回收會針對特定層代進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-183">Garbage collections occur on specific generations as conditions warrant.</span></span> <span data-ttu-id="01c91-184">回收層代是指回收該層代中的物件及其所有較新的層代。</span><span class="sxs-lookup"><span data-stu-id="01c91-184">Collecting a generation means collecting objects in that generation and all its younger generations.</span></span> <span data-ttu-id="01c91-185">層代 2 記憶體回收也稱為完整記憶體回收，因為它會回收所有層代中的所有物件 (亦即，Managed 堆積中的所有物件)。</span><span class="sxs-lookup"><span data-stu-id="01c91-185">A generation 2 garbage collection is also known as a full garbage collection, because it reclaims all objects in all generations (that is, all objects in the managed heap).</span></span>

### <a name="survival-and-promotions"></a><span data-ttu-id="01c91-186">未回收和提升</span><span class="sxs-lookup"><span data-stu-id="01c91-186">Survival and promotions</span></span>

<span data-ttu-id="01c91-187">沒有在記憶體回收中回收的物件稱為未回收物件，而且會提升至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="01c91-187">Objects that are not reclaimed in a garbage collection are known as survivors, and are promoted to the next generation.</span></span> <span data-ttu-id="01c91-188">在層代 0 記憶體回收中未被回收的物件會提升至層代 1、在層代 1 記憶體回收中未被回收的物件會提升至層代 2，而在層代 2 記憶體回收中未被回收的物件則保留在層代 2 中。</span><span class="sxs-lookup"><span data-stu-id="01c91-188">Objects that survive a generation 0 garbage collection are promoted to generation 1; objects that survive a generation 1 garbage collection are promoted to generation 2; and objects that survive a generation 2 garbage collection remain in generation 2.</span></span>

<span data-ttu-id="01c91-189">當記憶體回收行程偵測出某個層代的未回收率很高時，它就會增加該層代的配置臨界值，因此下一次回收就會取得大量的回收記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-189">When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation, so the next collection gets a substantial size of reclaimed memory.</span></span> <span data-ttu-id="01c91-190">CLR 會持續在兩個優先權之間取得平衡：不讓應用程式的工作集變得太大，而且不讓記憶體回收花費太多時間。</span><span class="sxs-lookup"><span data-stu-id="01c91-190">The CLR continually balances two priorities: not letting an application's working set get too big and not letting the garbage collection take too much time.</span></span>

### <a name="ephemeral-generations-and-segments"></a><span data-ttu-id="01c91-191">暫時層代和區段</span><span class="sxs-lookup"><span data-stu-id="01c91-191">Ephemeral generations and segments</span></span>

<span data-ttu-id="01c91-192">因為層代 0 和 1 中的物件存留較短，所以這些層代稱為暫時層代。</span><span class="sxs-lookup"><span data-stu-id="01c91-192">Because objects in generations 0 and 1 are short-lived, these generations are known as the ephemeral generations.</span></span>

<span data-ttu-id="01c91-193">暫時層代必須配置於稱為暫時區段的記憶體區段中。</span><span class="sxs-lookup"><span data-stu-id="01c91-193">Ephemeral generations must be allocated in the memory segment that is known as the ephemeral segment.</span></span> <span data-ttu-id="01c91-194">記憶體回收行程所取得的每個新區段都會成為新的暫時區段，而且包含在層代 0 記憶體回收中未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-194">Each new segment acquired by the garbage collector becomes the new ephemeral segment and contains the objects that survived a generation 0 garbage collection.</span></span> <span data-ttu-id="01c91-195">舊的暫時區段會成為新的層代 2 區段。</span><span class="sxs-lookup"><span data-stu-id="01c91-195">The old ephemeral segment becomes the new generation 2 segment.</span></span>

<span data-ttu-id="01c91-196">暫時區段的大小會根據系統是 32 位元或 64 位元，以及根據系統所執行的記憶體回收行程類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="01c91-196">The size of the ephemeral segment varies depending on whether a system is 32- or 64-bit, and on the type of garbage collector it is running.</span></span> <span data-ttu-id="01c91-197">下表顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="01c91-197">Default values are shown in the following table.</span></span>

||<span data-ttu-id="01c91-198">32 位元</span><span class="sxs-lookup"><span data-stu-id="01c91-198">32-bit</span></span>|<span data-ttu-id="01c91-199">64 位元</span><span class="sxs-lookup"><span data-stu-id="01c91-199">64-bit</span></span>|
|-|-------------|-------------|
|<span data-ttu-id="01c91-200">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="01c91-200">Workstation GC</span></span>|<span data-ttu-id="01c91-201">16 MB</span><span class="sxs-lookup"><span data-stu-id="01c91-201">16 MB</span></span>|<span data-ttu-id="01c91-202">256 MB</span><span class="sxs-lookup"><span data-stu-id="01c91-202">256 MB</span></span>|
|<span data-ttu-id="01c91-203">伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="01c91-203">Server GC</span></span>|<span data-ttu-id="01c91-204">64 MB</span><span class="sxs-lookup"><span data-stu-id="01c91-204">64 MB</span></span>|<span data-ttu-id="01c91-205">4 GB</span><span class="sxs-lookup"><span data-stu-id="01c91-205">4 GB</span></span>|
|<span data-ttu-id="01c91-206">具有多於 4 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="01c91-206">Server GC with > 4 logical CPUs</span></span>|<span data-ttu-id="01c91-207">32 MB</span><span class="sxs-lookup"><span data-stu-id="01c91-207">32 MB</span></span>|<span data-ttu-id="01c91-208">2 GB</span><span class="sxs-lookup"><span data-stu-id="01c91-208">2 GB</span></span>|
|<span data-ttu-id="01c91-209">具有 > 8 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="01c91-209">Server GC with > 8 logical CPUs</span></span>|<span data-ttu-id="01c91-210">16 MB</span><span class="sxs-lookup"><span data-stu-id="01c91-210">16 MB</span></span>|<span data-ttu-id="01c91-211">1 GB</span><span class="sxs-lookup"><span data-stu-id="01c91-211">1 GB</span></span>|

<span data-ttu-id="01c91-212">暫時區段可能會包括層代 2 物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-212">The ephemeral segment can include generation 2 objects.</span></span> <span data-ttu-id="01c91-213">層代 2 物件可以使用多個區段 (取決於處理序所需而且記憶體允許的數目)。</span><span class="sxs-lookup"><span data-stu-id="01c91-213">Generation 2 objects can use multiple segments (as many as your process requires and memory allows for).</span></span>

<span data-ttu-id="01c91-214">暫時記憶體回收中釋放記憶體的數量會限制為暫時區段的大小。</span><span class="sxs-lookup"><span data-stu-id="01c91-214">The amount of freed memory from an ephemeral garbage collection is limited to the size of the ephemeral segment.</span></span> <span data-ttu-id="01c91-215">所釋放的記憶體數量會與無作用物件所佔據的空間成正比。</span><span class="sxs-lookup"><span data-stu-id="01c91-215">The amount of memory that is freed is proportional to the space that was occupied by the dead objects.</span></span>

[<span data-ttu-id="01c91-216">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-216">Back to top</span></span>](#top)

<a name="what_happens_during_a_garbage_collection"></a>

## <a name="what-happens-during-a-garbage-collection"></a><span data-ttu-id="01c91-217">記憶體回收期間進行的作業</span><span class="sxs-lookup"><span data-stu-id="01c91-217">What happens during a garbage collection</span></span>

<span data-ttu-id="01c91-218">記憶體回收具有下列階段：</span><span class="sxs-lookup"><span data-stu-id="01c91-218">A garbage collection has the following phases:</span></span>

- <span data-ttu-id="01c91-219">標記階段：尋找和建立所有使用中物件的清單。</span><span class="sxs-lookup"><span data-stu-id="01c91-219">A marking phase that finds and creates a list of all live objects.</span></span>

- <span data-ttu-id="01c91-220">重新配置階段：更新即將壓縮之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="01c91-220">A relocating phase that updates the references to the objects that will be compacted.</span></span>

- <span data-ttu-id="01c91-221">壓縮階段：回收無作用物件所佔據的空間並壓縮未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-221">A compacting phase that reclaims the space occupied by the dead objects and compacts the surviving objects.</span></span> <span data-ttu-id="01c91-222">壓縮階段會將記憶體回收中未被回收的物件移至區段的較舊端。</span><span class="sxs-lookup"><span data-stu-id="01c91-222">The compacting phase moves objects that have survived a garbage collection toward the older end of the segment.</span></span>

  <span data-ttu-id="01c91-223">因為層代 2 回收可能會佔據多個區段，所以提升至層代 2 的物件可能會移至較舊區段。</span><span class="sxs-lookup"><span data-stu-id="01c91-223">Because generation 2 collections can occupy multiple segments, objects that are promoted into generation 2 can be moved into an older segment.</span></span> <span data-ttu-id="01c91-224">層代 1 和層代 2 的未回收物件都可能會移至不同的區段，因為它們都會被提升至層代 2。</span><span class="sxs-lookup"><span data-stu-id="01c91-224">Both generation 1 and generation 2 survivors can be moved to a different segment, because they are promoted to generation 2.</span></span>

  <span data-ttu-id="01c91-225">正常情況下，大型物件堆積不會壓縮，因為複製大型物件會帶來效能損失。</span><span class="sxs-lookup"><span data-stu-id="01c91-225">Ordinarily, the large object heap is not compacted, because copying large objects imposes a performance penalty.</span></span> <span data-ttu-id="01c91-226">不過，從 .NET Framework 4.5.1 開始，您可以視需要使用 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> 屬性壓縮大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="01c91-226">However, starting with the .NET Framework 4.5.1, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand.</span></span>

<span data-ttu-id="01c91-227">記憶體回收行程會使用下列資訊來判斷物件是否使用中：</span><span class="sxs-lookup"><span data-stu-id="01c91-227">The garbage collector uses the following information to determine whether objects are live:</span></span>

- <span data-ttu-id="01c91-228">**堆疊根目錄**。</span><span class="sxs-lookup"><span data-stu-id="01c91-228">**Stack roots**.</span></span> <span data-ttu-id="01c91-229">Just-in-Time (JIT) 編譯器和堆疊查核器所提供的堆疊變數。</span><span class="sxs-lookup"><span data-stu-id="01c91-229">Stack variables provided by the just-in-time (JIT) compiler and stack walker.</span></span> <span data-ttu-id="01c91-230">請注意，JIT 最佳化可以延長或縮短程式碼區域，其中堆疊變數會向記憶體回收行程回報。</span><span class="sxs-lookup"><span data-stu-id="01c91-230">Note that JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.</span></span>

- <span data-ttu-id="01c91-231">**記憶體回收控制代碼**。</span><span class="sxs-lookup"><span data-stu-id="01c91-231">**Garbage collection handles**.</span></span> <span data-ttu-id="01c91-232">會指向 Managed 物件，而且可由使用者程式碼或 Common Language Runtime 配置的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="01c91-232">Handles that point to managed objects and that can be allocated by user code or by the common language runtime.</span></span>

- <span data-ttu-id="01c91-233">**靜態資料**。</span><span class="sxs-lookup"><span data-stu-id="01c91-233">**Static data**.</span></span> <span data-ttu-id="01c91-234">應用程式定義域中可能參考其他物件的靜態物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-234">Static objects in application domains that could be referencing other objects.</span></span> <span data-ttu-id="01c91-235">每個應用程式定義域都會追蹤其靜態物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-235">Each application domain keeps track of its static objects.</span></span>

<span data-ttu-id="01c91-236">記憶體回收開始之前，所有 Managed 執行緒都會暫停，但觸發記憶體回收的執行緒除外。</span><span class="sxs-lookup"><span data-stu-id="01c91-236">Before a garbage collection starts, all managed threads are suspended except for the thread that triggered the garbage collection.</span></span>

<span data-ttu-id="01c91-237">下圖顯示觸發記憶體回收且造成其他執行緒暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="01c91-237">The following illustration shows a thread that triggers a garbage collection and causes the other threads to be suspended.</span></span>

<span data-ttu-id="01c91-238">當執行緒(../../../docs/standard/garbage-collection/media/gc-triggered.png "觸發垃圾收集時") ![，執行緒觸發垃圾收集]時</span><span class="sxs-lookup"><span data-stu-id="01c91-238">![When a thread triggers a Garbage Collection](../../../docs/standard/garbage-collection/media/gc-triggered.png "When a thread triggers a Garbage Collection")</span></span>

[<span data-ttu-id="01c91-239">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-239">Back to top</span></span>](#top)

<a name="manipulating_unmanaged_resources"></a>

## <a name="manipulating-unmanaged-resources"></a><span data-ttu-id="01c91-240">管理 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="01c91-240">Manipulating unmanaged resources</span></span>

<span data-ttu-id="01c91-241">如果您的 Managed 物件使用其原生檔案控制代碼參考 Unmanaged 物件，則您必須明確釋放這些 Unmanaged 物件，因為記憶體回收行程只會追蹤 Managed 堆積上的記憶體。</span><span class="sxs-lookup"><span data-stu-id="01c91-241">If your managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector tracks memory only on the managed heap.</span></span>

<span data-ttu-id="01c91-242">Managed 物件的使用者無法處置此物件所使用的原生資源。</span><span class="sxs-lookup"><span data-stu-id="01c91-242">Users of your managed object may not dispose the native resources used by the object.</span></span> <span data-ttu-id="01c91-243">若要執行清除，您可以讓 Managed 物件變成可最終處理物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-243">To perform the cleanup, you can make your managed object finalizable.</span></span> <span data-ttu-id="01c91-244">最終處理是由您在物件不再使用時所執行的清除動作組成。</span><span class="sxs-lookup"><span data-stu-id="01c91-244">Finalization consists of cleanup actions that you execute when the object is no longer in use.</span></span> <span data-ttu-id="01c91-245">當您的 Managed 物件無作用時，它就會執行其完成項方法中指定的清除動作。</span><span class="sxs-lookup"><span data-stu-id="01c91-245">When your managed object dies, it performs cleanup actions that are specified in its finalizer method.</span></span>

<span data-ttu-id="01c91-246">當系統發現某個可最終處理物件無作用時，該物件的完成項就會放入佇列中，以便執行其清除動作，但是物件本身會提升至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="01c91-246">When a finalizable object is discovered to be dead, its finalizer is put in a queue so that its cleanup actions are executed, but the object itself is promoted to the next generation.</span></span> <span data-ttu-id="01c91-247">因此，您必須等候直到在該層代上進行的下一次記憶體回收 (不一定是下一次記憶體回收)，以便判斷此物件是否已經回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-247">Therefore, you have to wait until the next garbage collection that occurs on that generation (which is not necessarily the next garbage collection) to determine whether the object has been reclaimed.</span></span>

[<span data-ttu-id="01c91-248">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-248">Back to top</span></span>](#top)

<a name="workstation_and_server_garbage_collection"></a>

## <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="01c91-249">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-249">Workstation and server garbage collection</span></span>

<span data-ttu-id="01c91-250">記憶體回收行程會自行調整而且可在各種案例中運作。</span><span class="sxs-lookup"><span data-stu-id="01c91-250">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="01c91-251">您可以使用組態檔設定，根據工作負載的特性來設定記憶體回收的類型。</span><span class="sxs-lookup"><span data-stu-id="01c91-251">You can use a configuration file setting to set the type of garbage collection based on the characteristics of the workload.</span></span> <span data-ttu-id="01c91-252">CLR 會提供下列記憶體回收類型：</span><span class="sxs-lookup"><span data-stu-id="01c91-252">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="01c91-253">工作站記憶體回收，適用於所有用戶端工作站和獨立電腦。</span><span class="sxs-lookup"><span data-stu-id="01c91-253">Workstation garbage collection, which is for all client workstations and stand-alone PCs.</span></span> <span data-ttu-id="01c91-254">在執行階段組態結構描述中，這是 [\<gcServer> 項目](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)的預設設定。</span><span class="sxs-lookup"><span data-stu-id="01c91-254">This is the default setting for the [\<gcServer> element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) in the runtime configuration schema.</span></span>

  <span data-ttu-id="01c91-255">工作站記憶體回收可能是並行或非並行的。</span><span class="sxs-lookup"><span data-stu-id="01c91-255">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="01c91-256">並行記憶體回收可讓 Managed 執行緒在記憶體回收期間繼續運作。</span><span class="sxs-lookup"><span data-stu-id="01c91-256">Concurrent garbage collection enables managed threads to continue operations during a garbage collection.</span></span>

  <span data-ttu-id="01c91-257">從 .NET Framework 4 開始，背景記憶體回收取代了並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-257">Starting with the .NET Framework 4, background garbage collection replaces concurrent garbage collection.</span></span>

- <span data-ttu-id="01c91-258">伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="01c91-258">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span> <span data-ttu-id="01c91-259">伺服器記憶體回收可以是非並行或背景。</span><span class="sxs-lookup"><span data-stu-id="01c91-259">Server garbage collection can be non-concurrent or background.</span></span>

<span data-ttu-id="01c91-260">下圖顯示在伺服器上執行記憶體回收的專屬執行緒。</span><span class="sxs-lookup"><span data-stu-id="01c91-260">The following illustration shows the dedicated threads that perform the garbage collection on a server.</span></span>

<span data-ttu-id="01c91-261">![伺服器垃圾收集執行緒](../../../docs/standard/garbage-collection/media/gc-server.png "伺服器垃圾收集執行緒")</span><span class="sxs-lookup"><span data-stu-id="01c91-261">![Server Garbage Collection Threads](../../../docs/standard/garbage-collection/media/gc-server.png "Server Garbage Collection Threads")</span></span>

### <a name="configuring-garbage-collection"></a><span data-ttu-id="01c91-262">設定記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-262">Configuring garbage collection</span></span>

<span data-ttu-id="01c91-263">您可以使用執行階段組態結構描述的 [\<gcServer> 項目](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)來指定您想讓 CLR 執行的記憶體回收類型。</span><span class="sxs-lookup"><span data-stu-id="01c91-263">You can use the [\<gcServer> element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) of the runtime configuration schema to specify the type of garbage collection you want the CLR to perform.</span></span> <span data-ttu-id="01c91-264">當此項目的 `enabled` 屬性設定為 `false` (預設值) 時，CLR 就會執行工作站記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-264">When this element's `enabled` attribute is set to `false` (the default), the CLR performs workstation garbage collection.</span></span> <span data-ttu-id="01c91-265">當您將 `enabled` 屬性設定為 `true`時，CLR 就會執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-265">When you set the `enabled` attribute to `true`, the CLR performs server garbage collection.</span></span>

<span data-ttu-id="01c91-266">並行記憶體回收是使用執行階段組態結構描述的 [\<gcConcurrent> 項目](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)來指定。</span><span class="sxs-lookup"><span data-stu-id="01c91-266">Concurrent garbage collection is specified with the [\<gcConcurrent> element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) of the runtime configuration schema.</span></span> <span data-ttu-id="01c91-267">預設的設定值是 `enabled`。</span><span class="sxs-lookup"><span data-stu-id="01c91-267">The default setting is `enabled`.</span></span> <span data-ttu-id="01c91-268">這項設定可控制並行和背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-268">This setting controls both concurrent and background garbage collection.</span></span>

<span data-ttu-id="01c91-269">您也可以使用 Unmanaged 裝載介面來指定伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-269">You can also specify server garbage collection with unmanaged hosting interfaces.</span></span> <span data-ttu-id="01c91-270">請注意，ASP.NET 和 SQL Server 會自動啟用伺服器記憶體回收 (如果您的應用程式裝載在其中一個環境內部的話)。</span><span class="sxs-lookup"><span data-stu-id="01c91-270">Note that ASP.NET and SQL Server enable server garbage collection automatically if your application is hosted inside one of these environments.</span></span>

### <a name="comparing-workstation-and-server-garbage-collection"></a><span data-ttu-id="01c91-271">比較工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-271">Comparing workstation and server garbage collection</span></span>

<span data-ttu-id="01c91-272">以下是工作站記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="01c91-272">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="01c91-273">此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="01c91-273">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="01c91-274">因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="01c91-274">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span>

  <span data-ttu-id="01c91-275">執行機器碼的執行緒不會暫停。</span><span class="sxs-lookup"><span data-stu-id="01c91-275">Threads that are running native code are not suspended.</span></span>

- <span data-ttu-id="01c91-276">工作站記憶體回收一律使用於只有單一處理器的電腦上，不論 [\<gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) 設定為何。</span><span class="sxs-lookup"><span data-stu-id="01c91-276">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [\<gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) setting.</span></span> <span data-ttu-id="01c91-277">如果您指定了伺服器記憶體回收，CLR 就會使用工作站記憶體回收並停用並行。</span><span class="sxs-lookup"><span data-stu-id="01c91-277">If you specify server garbage collection, the CLR uses workstation garbage collection with concurrency disabled.</span></span>

<span data-ttu-id="01c91-278">以下是伺服器記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="01c91-278">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="01c91-279">此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-279">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="01c91-280">執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-280">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="01c91-281">每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="01c91-281">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="01c91-282">不同堆積上的物件可以彼此參考。</span><span class="sxs-lookup"><span data-stu-id="01c91-282">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="01c91-283">因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。</span><span class="sxs-lookup"><span data-stu-id="01c91-283">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="01c91-284">伺服器記憶體回收通常具有較大的區段。</span><span class="sxs-lookup"><span data-stu-id="01c91-284">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="01c91-285">不過請注意，這只是概括而言：區段大小為實作特定，並可能隨時變更。</span><span class="sxs-lookup"><span data-stu-id="01c91-285">Note, however, that this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="01c91-286">當您微調應用程式時，不應該對記憶體回收行程所配置的區段大小做出假設。</span><span class="sxs-lookup"><span data-stu-id="01c91-286">You should make no assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="01c91-287">伺服器記憶體回收可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="01c91-287">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="01c91-288">例如，如果您在具有 4 個處理器的電腦上執行 12 個處理序，就會存在 48 個專屬記憶體回收執行緒 (如果它們都使用伺服器記憶體回收的話)。</span><span class="sxs-lookup"><span data-stu-id="01c91-288">For example, if you have 12 processes running on a computer that has 4 processors, there will be 48 dedicated garbage collection threads if they are all using server garbage collection.</span></span> <span data-ttu-id="01c91-289">在記憶體負載很高的情況下，如果所有處理序開始進行記憶體回收，記憶體回收行程就必須排程 48 個執行緒。</span><span class="sxs-lookup"><span data-stu-id="01c91-289">In a high memory load situation, if all the processes start doing garbage collection, the garbage collector will have 48 threads to schedule.</span></span>

<span data-ttu-id="01c91-290">如果您正在執行數百個應用程式執行個體，請考慮使用工作站記憶體回收並停用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-290">If you are running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="01c91-291">這樣會產生較少的內容切換，因此可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="01c91-291">This will result in less context switching, which can improve performance.</span></span>

[<span data-ttu-id="01c91-292">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-292">Back to top</span></span>](#top)

<a name="concurrent_garbage_collection"></a>

## <a name="concurrent-garbage-collection"></a><span data-ttu-id="01c91-293">並行的記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-293">Concurrent garbage collection</span></span>

<span data-ttu-id="01c91-294">在工作站或伺服器記憶體回收中，您可以啟用並行記憶體回收，以便在大部分回收期間，讓執行緒以並行方式與執行記憶體回收的專屬執行緒一起執行。</span><span class="sxs-lookup"><span data-stu-id="01c91-294">In workstation or server garbage collection, you can enable concurrent garbage collection, which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection.</span></span> <span data-ttu-id="01c91-295">這個選項只會影響層代 2 中的記憶體回收。層代 0 和 1 一律為非並行，因為它們的完成速度非常快。</span><span class="sxs-lookup"><span data-stu-id="01c91-295">This option affects only garbage collections in generation 2; generations 0 and 1 are always non-concurrent because they finish very fast.</span></span>

<span data-ttu-id="01c91-296">並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。</span><span class="sxs-lookup"><span data-stu-id="01c91-296">Concurrent garbage collection enables interactive applications to be more responsive by minimizing pauses for a collection.</span></span> <span data-ttu-id="01c91-297">當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="01c91-297">Managed threads can continue to run most of the time while the concurrent garbage collection thread is running.</span></span> <span data-ttu-id="01c91-298">這會在記憶體回收進行時縮短暫停時間。</span><span class="sxs-lookup"><span data-stu-id="01c91-298">This results in shorter pauses while a garbage collection is occurring.</span></span>

<span data-ttu-id="01c91-299">若要在許多處理序正在執行時改善效能，請停用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-299">To improve performance when several processes are running, disable concurrent garbage collection.</span></span> <span data-ttu-id="01c91-300">您可以藉由將 [\<gcConcurrent> 項目](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)加入應用程式的組態檔，並將其 `enabled` 屬性的值設為 `"false"`，來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="01c91-300">You can do this by adding a [\<gcConcurrent> element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to the app's configuration file and setting the value of its `enabled` attribute to `"false"`.</span></span>

<span data-ttu-id="01c91-301">並行記憶體回收會針對專屬執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="01c91-301">Concurrent garbage collection is performed on a dedicated thread.</span></span> <span data-ttu-id="01c91-302">根據預設，CLR 會執行工作站記憶體回收並啟用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-302">By default, the CLR runs workstation garbage collection with concurrent garbage collection enabled.</span></span> <span data-ttu-id="01c91-303">這種回收適用於單一處理器和多處理器電腦。</span><span class="sxs-lookup"><span data-stu-id="01c91-303">This is true for single-processor and multi-processor computers.</span></span>

<span data-ttu-id="01c91-304">並行記憶體回收期間，您在堆積上配置小型物件的能力會受限於並行記憶體回收開始時保留在暫時區段上的物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-304">Your ability to allocate small objects on the heap during a concurrent garbage collection is limited by the objects left on the ephemeral segment when a concurrent garbage collection starts.</span></span> <span data-ttu-id="01c91-305">一旦您到達區段的結尾時，就必須等候並行記憶體回收完成，而必須進行小型物件配置的 Managed 執行緒會暫停。</span><span class="sxs-lookup"><span data-stu-id="01c91-305">As soon as you reach the end of the segment, you will have to wait for the concurrent garbage collection to finish while managed threads that have to make small object allocations are suspended.</span></span>

<span data-ttu-id="01c91-306">並行記憶體回收具有稍微較大的工作集 (與非並行記憶體回收相較之下)，因為您可以在並行回收期間配置物件。</span><span class="sxs-lookup"><span data-stu-id="01c91-306">Concurrent garbage collection has a slightly bigger working set (compared with non-concurrent garbage collection), because you can allocate objects during concurrent collection.</span></span> <span data-ttu-id="01c91-307">不過，這可能會影響效能，因為您所配置的物件會成為工作集的一部分。</span><span class="sxs-lookup"><span data-stu-id="01c91-307">However, this can affect performance, because the objects that you allocate become part of your working set.</span></span> <span data-ttu-id="01c91-308">基本上，並行記憶體回收會犧牲一些 CPU 和記憶體以換取縮短的暫停時間。</span><span class="sxs-lookup"><span data-stu-id="01c91-308">Essentially, concurrent garbage collection trades some CPU and memory for shorter pauses.</span></span>

<span data-ttu-id="01c91-309">下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-309">The following illustration shows concurrent garbage collection performed on a separate dedicated thread.</span></span>

<span data-ttu-id="01c91-310">![並行垃圾收集執行緒](../../../docs/standard/garbage-collection/media/gc-concurrent.png "並行垃圾收集執行緒")</span><span class="sxs-lookup"><span data-stu-id="01c91-310">![Concurrent Garbage Collection Threads](../../../docs/standard/garbage-collection/media/gc-concurrent.png "Concurrent Garbage Collection Threads")</span></span>

[<span data-ttu-id="01c91-311">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-311">Back to top</span></span>](#top)

<a name="background_garbage_collection"></a>

## <a name="background-workstation-garbage-collection"></a><span data-ttu-id="01c91-312">背景工作站記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-312">Background workstation garbage collection</span></span>

<span data-ttu-id="01c91-313">背景垃圾收集會取代從 .NET Framework 4 開始的並行工作站垃圾收集，它會取代從 .NET Framework 4.5 開始的並行伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="01c91-313">Background garbage collection replaces concurrent workstation garbage collection starting with the .NET Framework 4, and it replaces concurrent server garbage collection starting with the .NET Framework 4.5.</span></span>  <span data-ttu-id="01c91-314">在背景記憶體回收中，當層代 2 的回收正在進行時，會視需要回收暫時層代 (0 和 1)。</span><span class="sxs-lookup"><span data-stu-id="01c91-314">In background garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress.</span></span> <span data-ttu-id="01c91-315">它是在專用的執行緒上執行，而且只適用于層代2回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-315">It is performed on a dedicated thread and is applicable only to generation 2 collections.</span></span> <span data-ttu-id="01c91-316">背景垃圾收集預設會自動啟用，而且可以使用 .NET Framework 應用程式中的[@no__t 1gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)設定 設定來啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="01c91-316">Background garbage collection is automatically enabled by default, and can be enabled or disabled with the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework applications.</span></span> 

> [!NOTE]
> <span data-ttu-id="01c91-317">只有 .NET Framework 4 和更新版本才能使用背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-317">Background garbage collection is available only in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="01c91-318">而 .NET Framework 4 只支援將上述功能用於工作站記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-318">In the .NET Framework 4, it is supported only for workstation garbage collection.</span></span> <span data-ttu-id="01c91-319">從 .NET Framework 4.5 開始，背景記憶體回收可供工作站和伺服器記憶體回收使用。</span><span class="sxs-lookup"><span data-stu-id="01c91-319">Starting with the .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.</span></span>

<span data-ttu-id="01c91-320">背景記憶體回收期間，暫時層代的回收稱為前景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-320">A collection on ephemeral generations during background garbage collection is known as foreground garbage collection.</span></span> <span data-ttu-id="01c91-321">進行前景記憶體回收時，所有 Managed 執行緒都會暫停。</span><span class="sxs-lookup"><span data-stu-id="01c91-321">When foreground garbage collections occur, all managed threads are suspended.</span></span>

<span data-ttu-id="01c91-322">當背景記憶體回收正在進行，而且您已經在層代 0 中配置足夠的物件時，CLR 就會執行層代 0 或層代 1 的前景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="01c91-322">When background garbage collection is in progress and you have allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection.</span></span> <span data-ttu-id="01c91-323">專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。</span><span class="sxs-lookup"><span data-stu-id="01c91-323">The dedicated background garbage collection thread checks at frequent safe points to determine whether there is a request for foreground garbage collection.</span></span> <span data-ttu-id="01c91-324">如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-324">If there is, the background collection suspends itself so that foreground garbage collection can occur.</span></span> <span data-ttu-id="01c91-325">在前景記憶體回收完成之後，專屬的背景記憶體回收執行緒和使用者執行緒就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-325">After the foreground garbage collection is completed, the dedicated background garbage collection thread and user threads resume.</span></span>

<span data-ttu-id="01c91-326">背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。</span><span class="sxs-lookup"><span data-stu-id="01c91-326">Background garbage collection removes allocation restrictions imposed by concurrent garbage collection, because ephemeral garbage collections can occur during background garbage collection.</span></span> <span data-ttu-id="01c91-327">這表示，背景記憶體回收可以移除暫時層代中的無作用物件，而且也可以在層代 1 記憶體回收期間視需要擴展堆積。</span><span class="sxs-lookup"><span data-stu-id="01c91-327">This means that background garbage collection can remove dead objects in ephemeral generations and can also expand the heap if needed during a generation 1 garbage collection.</span></span>

<span data-ttu-id="01c91-328">下圖顯示在工作站上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="01c91-328">The following illustration shows background garbage collection performed on a separate dedicated thread on a workstation:</span></span>

<span data-ttu-id="01c91-329">![顯示背景工作站垃圾收集的圖表。](./media/fundamentals/background-workstation-garbage-collection.png "顯示背景工作站垃圾收集的圖表。")</span><span class="sxs-lookup"><span data-stu-id="01c91-329">![Diagram that shows background workstation garbage collection.](./media/fundamentals/background-workstation-garbage-collection.png "Diagram that shows background workstation garbage collection.")</span></span>

[<span data-ttu-id="01c91-330">回到頁首</span><span class="sxs-lookup"><span data-stu-id="01c91-330">Back to top</span></span>](#top)

<a name="background_server_garbage_collection"></a>

## <a name="background-server-garbage-collection"></a><span data-ttu-id="01c91-331">背景伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-331">Background server garbage collection</span></span>

<span data-ttu-id="01c91-332">從 .NET Framework 4.5 開始，背景伺服器記憶體回收是伺服器記憶體回收的預設模式。</span><span class="sxs-lookup"><span data-stu-id="01c91-332">Starting with the .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.</span></span> <span data-ttu-id="01c91-333">若要選擇這個模式，在執行階段組態結構描述中，將 [\<gcServer> 項目](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)的 `enabled` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="01c91-333">To choose this mode, set the `enabled` attribute of the [\<gcServer> element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) to `true` in the runtime configuration schema.</span></span> <span data-ttu-id="01c91-334">這個模式的功能類似於背景工作站記憶體回收 (如上一節所述)，不過仍有一些差異。</span><span class="sxs-lookup"><span data-stu-id="01c91-334">This mode functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences.</span></span> <span data-ttu-id="01c91-335">背景工作站記憶體回收會使用一個專用的背景記憶體回收執行緒，而背景伺服器記憶體回收則使用多個執行緒，通常是針對每個邏輯處理器使用一個專用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="01c91-335">Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads, typically a dedicated thread for each logical processor.</span></span> <span data-ttu-id="01c91-336">與工作站背景記憶體回收執行緒不同的是，這些執行緒不會逾時。</span><span class="sxs-lookup"><span data-stu-id="01c91-336">Unlike the workstation background garbage collection thread, these threads do not time out.</span></span>

<span data-ttu-id="01c91-337">下圖顯示在伺服器上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="01c91-337">The following illustration shows background garbage collection performed on a separate dedicated thread on a server:</span></span>

<span data-ttu-id="01c91-338">![顯示背景伺服器垃圾收集的圖表。](./media/fundamentals/background-server-garbage-collection.png "顯示背景伺服器垃圾收集的圖表。")</span><span class="sxs-lookup"><span data-stu-id="01c91-338">![Diagram that shows background server garbage collection.](./media/fundamentals/background-server-garbage-collection.png "Diagram that shows background server garbage collection.")</span></span>

## <a name="see-also"></a><span data-ttu-id="01c91-339">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01c91-339">See also</span></span>

- [<span data-ttu-id="01c91-340">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="01c91-340">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
