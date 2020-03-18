---
title: 記憶體回收的基本概念
description: 了解記憶體回收行程如何運作，以及如何為它設定最佳效能。
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400537"
---
# <a name="fundamentals-of-garbage-collection"></a><span data-ttu-id="97f1f-103">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="97f1f-103">Fundamentals of garbage collection</span></span>

<span data-ttu-id="97f1f-104">在通用語言運行時 （CLR） 中，垃圾回收器 （GC） 充當自動記憶體管理器。</span><span class="sxs-lookup"><span data-stu-id="97f1f-104">In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager.</span></span> <span data-ttu-id="97f1f-105">它提供了下列優點：</span><span class="sxs-lookup"><span data-stu-id="97f1f-105">It provides the following benefits:</span></span>

- <span data-ttu-id="97f1f-106">使您能夠開發應用程式，而無需手動釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-106">Enables you to develop your application without having to manually free memory.</span></span>

- <span data-ttu-id="97f1f-107">有效率地在 Managed 堆積上配置物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-107">Allocates objects on the managed heap efficiently.</span></span>

- <span data-ttu-id="97f1f-108">回收不再使用的物件、清除其記憶體，並且讓記憶體可供未來的配置使用。</span><span class="sxs-lookup"><span data-stu-id="97f1f-108">Reclaims objects that are no longer being used, clears their memory, and keeps the memory available for future allocations.</span></span> <span data-ttu-id="97f1f-109">Managed 物件在開始時會自動取得乾淨的內容，因此其建構函式不需要初始化每個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="97f1f-109">Managed objects automatically get clean content to start with, so their constructors do not have to initialize every data field.</span></span>

- <span data-ttu-id="97f1f-110">確保某個物件無法使用另一個物件的內容，藉以提供記憶體安全性。</span><span class="sxs-lookup"><span data-stu-id="97f1f-110">Provides memory safety by making sure that an object cannot use the content of another object.</span></span>

<span data-ttu-id="97f1f-111">本文介紹了垃圾回收的核心概念。</span><span class="sxs-lookup"><span data-stu-id="97f1f-111">This article describes the core concepts of garbage collection.</span></span>

## <a name="fundamentals-of-memory"></a><span data-ttu-id="97f1f-112">記憶體的基本概念</span><span class="sxs-lookup"><span data-stu-id="97f1f-112">Fundamentals of memory</span></span>

<span data-ttu-id="97f1f-113">下列清單摘要說明重要的 CLR 記憶體概念。</span><span class="sxs-lookup"><span data-stu-id="97f1f-113">The following list summarizes important CLR memory concepts.</span></span>

- <span data-ttu-id="97f1f-114">每個處理序都有各自獨立的虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="97f1f-114">Each process has its own, separate virtual address space.</span></span> <span data-ttu-id="97f1f-115">同一台電腦上的所有進程共用相同的實體記憶體和分頁檔（如果有）。</span><span class="sxs-lookup"><span data-stu-id="97f1f-115">All processes on the same computer share the same physical memory and the page file, if there is one.</span></span>

- <span data-ttu-id="97f1f-116">根據預設，在 32 位元電腦上，每個處理序都有 2 GB 使用者模式虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="97f1f-116">By default, on 32-bit computers, each process has a 2-GB user-mode virtual address space.</span></span>

- <span data-ttu-id="97f1f-117">身為應用程式開發人員，您只會處理虛擬位址空間，絕不會直接操作實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-117">As an application developer, you work only with virtual address space and never manipulate physical memory directly.</span></span> <span data-ttu-id="97f1f-118">記憶體回收行程會在 Managed 堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-118">The garbage collector allocates and frees virtual memory for you on the managed heap.</span></span>

  <span data-ttu-id="97f1f-119">如果要編寫本機代碼，請使用 Windows 函數來處理虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="97f1f-119">If you are writing native code, you use Windows functions to work with the virtual address space.</span></span> <span data-ttu-id="97f1f-120">這些函式會在原生堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-120">These functions allocate and free virtual memory for you on native heaps.</span></span>

- <span data-ttu-id="97f1f-121">虛擬記憶體可以有三種狀態：</span><span class="sxs-lookup"><span data-stu-id="97f1f-121">Virtual memory can be in three states:</span></span>

  - <span data-ttu-id="97f1f-122">可用。</span><span class="sxs-lookup"><span data-stu-id="97f1f-122">Free.</span></span> <span data-ttu-id="97f1f-123">記憶體區塊沒有任何參考，可進行配置。</span><span class="sxs-lookup"><span data-stu-id="97f1f-123">The block of memory has no references to it and is available for allocation.</span></span>

  - <span data-ttu-id="97f1f-124">已保留。</span><span class="sxs-lookup"><span data-stu-id="97f1f-124">Reserved.</span></span> <span data-ttu-id="97f1f-125">記憶體區塊可供您使用，但是無法用於任何其他配置要求。</span><span class="sxs-lookup"><span data-stu-id="97f1f-125">The block of memory is available for your use and cannot be used for any other allocation request.</span></span> <span data-ttu-id="97f1f-126">不過，在此記憶體區塊認可之前，您無法將資料儲存到其中。</span><span class="sxs-lookup"><span data-stu-id="97f1f-126">However, you cannot store data to this memory block until it is committed.</span></span>

  - <span data-ttu-id="97f1f-127">已認可。</span><span class="sxs-lookup"><span data-stu-id="97f1f-127">Committed.</span></span> <span data-ttu-id="97f1f-128">記憶體區塊會指派給實體儲存區。</span><span class="sxs-lookup"><span data-stu-id="97f1f-128">The block of memory is assigned to physical storage.</span></span>

- <span data-ttu-id="97f1f-129">虛擬位址空間可能會分成片段。</span><span class="sxs-lookup"><span data-stu-id="97f1f-129">Virtual address space can get fragmented.</span></span> <span data-ttu-id="97f1f-130">這表示，位址空間中有可用的區塊，也稱為可用的洞 (Hole)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-130">This means that there are free blocks, also known as holes, in the address space.</span></span> <span data-ttu-id="97f1f-131">要求虛擬記憶體配置時，虛擬記憶體管理程式必須找到大小可滿足配置要求的單一可用區塊。</span><span class="sxs-lookup"><span data-stu-id="97f1f-131">When a virtual memory allocation is requested, the virtual memory manager has to find a single free block that is large enough to satisfy that allocation request.</span></span> <span data-ttu-id="97f1f-132">即使您擁有 2GB 可用空間，要求 2GB 的配置仍然不會成功，除非該可用空間全都在單一位址區塊中。</span><span class="sxs-lookup"><span data-stu-id="97f1f-132">Even if you have 2 GB of free space, the allocation that requires 2 GB will be unsuccessful unless all of that free space is in a single address block.</span></span>

- <span data-ttu-id="97f1f-133">如果沒有足夠的虛擬位址空間來保留或物理空間進行提交，則記憶體可能會耗盡。</span><span class="sxs-lookup"><span data-stu-id="97f1f-133">You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.</span></span>

  <span data-ttu-id="97f1f-134">即使實體記憶體壓力（即實體記憶體需求）較低，也會使用分頁檔。</span><span class="sxs-lookup"><span data-stu-id="97f1f-134">The page file is used even if physical memory pressure (that is, demand for physical memory) is low.</span></span> <span data-ttu-id="97f1f-135">第一次實體記憶體壓力較高時，作業系統必須在實體記憶體中留出空間來存儲資料，並將實體記憶體中的某些資料備份到分頁檔。</span><span class="sxs-lookup"><span data-stu-id="97f1f-135">The first time physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file.</span></span> <span data-ttu-id="97f1f-136">在需要資料之前不會分頁，因此在實體記憶體壓力低的情況下可能會遇到分頁。</span><span class="sxs-lookup"><span data-stu-id="97f1f-136">That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.</span></span>

## <a name="conditions-for-a-garbage-collection"></a><span data-ttu-id="97f1f-137">記憶體回收的條件</span><span class="sxs-lookup"><span data-stu-id="97f1f-137">Conditions for a garbage collection</span></span>

<span data-ttu-id="97f1f-138">當下列其中一個條件成立時，就會進行記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="97f1f-138">Garbage collection occurs when one of the following conditions is true:</span></span>

- <span data-ttu-id="97f1f-139">系統的實體記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="97f1f-139">The system has low physical memory.</span></span> <span data-ttu-id="97f1f-140">這由來自作業系統的低記憶體通知或主機指示的低記憶體檢測到。</span><span class="sxs-lookup"><span data-stu-id="97f1f-140">This is detected by either the low memory notification from the OS or low memory as indicated by the host.</span></span>

- <span data-ttu-id="97f1f-141">由 Managed 堆積上之已配置物件所使用的記憶體超過可接受的臨界值。</span><span class="sxs-lookup"><span data-stu-id="97f1f-141">The memory that is used by allocated objects on the managed heap surpasses an acceptable threshold.</span></span> <span data-ttu-id="97f1f-142">這個臨界值會在處理序執行時持續調整。</span><span class="sxs-lookup"><span data-stu-id="97f1f-142">This threshold is continuously adjusted as the process runs.</span></span>

- <span data-ttu-id="97f1f-143">已呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="97f1f-143">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="97f1f-144">在大多數的情況下，您不需要呼叫這個方法，因為記憶體回收行程會持續執行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-144">In almost all cases, you do not have to call this method, because the garbage collector runs continuously.</span></span> <span data-ttu-id="97f1f-145">這個方法主要用於獨特的情況和測試。</span><span class="sxs-lookup"><span data-stu-id="97f1f-145">This method is primarily used for unique situations and testing.</span></span>

## <a name="the-managed-heap"></a><span data-ttu-id="97f1f-146">Managed 堆積</span><span class="sxs-lookup"><span data-stu-id="97f1f-146">The managed heap</span></span>

<span data-ttu-id="97f1f-147">CLR 初始化記憶體回收行程之後，記憶體回收行程就會配置用來儲存和管理物件的記憶體區段。</span><span class="sxs-lookup"><span data-stu-id="97f1f-147">After the garbage collector is initialized by the CLR, it allocates a segment of memory to store and manage objects.</span></span> <span data-ttu-id="97f1f-148">這個記憶體稱為 Managed 堆積，與作業系統中的原生堆積相反。</span><span class="sxs-lookup"><span data-stu-id="97f1f-148">This memory is called the managed heap, as opposed to a native heap in the operating system.</span></span>

<span data-ttu-id="97f1f-149">每個 Managed 處理序都有一個 Managed 堆積。</span><span class="sxs-lookup"><span data-stu-id="97f1f-149">There is a managed heap for each managed process.</span></span> <span data-ttu-id="97f1f-150">處理序中的所有執行緒都會對相同堆積上的物件配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-150">All threads in the process allocate memory for objects on the same heap.</span></span>

<span data-ttu-id="97f1f-151">為了保留記憶體，垃圾回收器調用 Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)函數，並一次為託管應用程式保留一段記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-151">To reserve memory, the garbage collector calls the Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function and reserves one segment of memory at a time for managed applications.</span></span> <span data-ttu-id="97f1f-152">垃圾回收器還根據需要保留段，並通過調用 Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)函數將段釋放回作業系統（清除任何物件後）。</span><span class="sxs-lookup"><span data-stu-id="97f1f-152">The garbage collector also reserves segments, as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97f1f-153">記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="97f1f-153">The size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="97f1f-154">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="97f1f-154">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

<span data-ttu-id="97f1f-155">配置在堆積上的物件越少，記憶體回收行程必須進行的工作就越少。</span><span class="sxs-lookup"><span data-stu-id="97f1f-155">The fewer objects allocated on the heap, the less work the garbage collector has to do.</span></span> <span data-ttu-id="97f1f-156">當您配置物件時，請勿使用超出需求的進位值，例如，當您只需要 15 個位元組時，卻配置 32 個位元組的陣列。</span><span class="sxs-lookup"><span data-stu-id="97f1f-156">When you allocate objects, do not use rounded-up values that exceed your needs, such as allocating an array of 32 bytes when you need only 15 bytes.</span></span>

<span data-ttu-id="97f1f-157">觸發記憶體回收時，記憶體回收行程就會回收無作用物件所佔據的記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-157">When a garbage collection is triggered, the garbage collector reclaims the memory that is occupied by dead objects.</span></span> <span data-ttu-id="97f1f-158">回收處理序會壓縮使用中物件，讓它們集合在一起，並且移除無作用物件，因而讓堆積更小。</span><span class="sxs-lookup"><span data-stu-id="97f1f-158">The reclaiming process compacts live objects so that they are moved together, and the dead space is removed, thereby making the heap smaller.</span></span> <span data-ttu-id="97f1f-159">這樣可確保一起配置的物件會在 Managed 堆積上集中，以便保持其區域性。</span><span class="sxs-lookup"><span data-stu-id="97f1f-159">This ensures that objects that are allocated together stay together on the managed heap, to preserve their locality.</span></span>

<span data-ttu-id="97f1f-160">記憶體回收的干擾程度 (頻率和持續期間) 是 Managed 堆積上之配置量和未被回收記憶體數量的結果。</span><span class="sxs-lookup"><span data-stu-id="97f1f-160">The intrusiveness (frequency and duration) of garbage collections is the result of the volume of allocations and the amount of survived memory on the managed heap.</span></span>

<span data-ttu-id="97f1f-161">堆可以被視為兩個堆的累積：[大型物件堆](large-object-heap.md)和小物件堆。</span><span class="sxs-lookup"><span data-stu-id="97f1f-161">The heap can be considered as the accumulation of two heaps: the [large object heap](large-object-heap.md) and the small object heap.</span></span>

<span data-ttu-id="97f1f-162">[大型物件堆](large-object-heap.md)包含非常大的物件，物件為 85，000 位元組和較大。</span><span class="sxs-lookup"><span data-stu-id="97f1f-162">The [large object heap](large-object-heap.md) contains very large objects that are 85,000 bytes and larger.</span></span> <span data-ttu-id="97f1f-163">大型物件堆積上的物件通常是陣列。</span><span class="sxs-lookup"><span data-stu-id="97f1f-163">The objects on the large object heap are usually arrays.</span></span> <span data-ttu-id="97f1f-164">超大型的執行個體物件非常罕見。</span><span class="sxs-lookup"><span data-stu-id="97f1f-164">It is rare for an instance object to be extremely large.</span></span>

> [!TIP]
> <span data-ttu-id="97f1f-165">您可以設定物件在大型物件堆上的[閾值大小](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-165">You can [configure the threshold size](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) for objects to go on the large object heap.</span></span>

## <a name="generations"></a><span data-ttu-id="97f1f-166">層代</span><span class="sxs-lookup"><span data-stu-id="97f1f-166">Generations</span></span>

<span data-ttu-id="97f1f-167">堆積會組織成層代，因此它可以處理存留較久和存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-167">The heap is organized into generations so it can handle long-lived and short-lived objects.</span></span> <span data-ttu-id="97f1f-168">記憶體回收主要與存留較短物件的回收一起進行，而這些物件通常只佔據堆積的一小部分。</span><span class="sxs-lookup"><span data-stu-id="97f1f-168">Garbage collection primarily occurs with the reclamation of short-lived objects that typically occupy only a small part of the heap.</span></span> <span data-ttu-id="97f1f-169">堆積上的物件有三個層代：</span><span class="sxs-lookup"><span data-stu-id="97f1f-169">There are three generations of objects on the heap:</span></span>

- <span data-ttu-id="97f1f-170">**第 0 代**.</span><span class="sxs-lookup"><span data-stu-id="97f1f-170">**Generation 0**.</span></span> <span data-ttu-id="97f1f-171">這是最新的層代而且包含存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-171">This is the youngest generation and contains short-lived objects.</span></span> <span data-ttu-id="97f1f-172">存留較短的物件範例是暫存變數。</span><span class="sxs-lookup"><span data-stu-id="97f1f-172">An example of a short-lived object is a temporary variable.</span></span> <span data-ttu-id="97f1f-173">記憶體回收最常在這個層代中進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-173">Garbage collection occurs most frequently in this generation.</span></span>

  <span data-ttu-id="97f1f-174">新分配的物件構成新一代的物件，並且隱式生成 0 集合。</span><span class="sxs-lookup"><span data-stu-id="97f1f-174">Newly allocated objects form a new generation of objects and are implicitly generation 0 collections.</span></span> <span data-ttu-id="97f1f-175">但是，如果它們是大型物件，它們將位於第 2 代集合中的大物件堆上。</span><span class="sxs-lookup"><span data-stu-id="97f1f-175">However, if they are large objects, they go on the large object heap in a generation 2 collection.</span></span>

  <span data-ttu-id="97f1f-176">大部分物件都會在層代 0 的記憶體回收中回收，而且不會存留至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="97f1f-176">Most objects are reclaimed for garbage collection in generation 0 and do not survive to the next generation.</span></span>

- <span data-ttu-id="97f1f-177">**第 1 代**.</span><span class="sxs-lookup"><span data-stu-id="97f1f-177">**Generation 1**.</span></span> <span data-ttu-id="97f1f-178">這個層代包含存留較短的物件，而且當做存留較短物件與存留較長物件之間的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="97f1f-178">This generation contains short-lived objects and serves as a buffer between short-lived objects and long-lived objects.</span></span>

- <span data-ttu-id="97f1f-179">**第 2 代**.</span><span class="sxs-lookup"><span data-stu-id="97f1f-179">**Generation 2**.</span></span> <span data-ttu-id="97f1f-180">這個層代包含存留較長的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-180">This generation contains long-lived objects.</span></span> <span data-ttu-id="97f1f-181">長壽命物件的一個示例是伺服器應用程式中包含在進程持續時間內即時的靜態資料的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-181">An example of a long-lived object is an object in a server application that contains static data that's live for the duration of the process.</span></span>

<span data-ttu-id="97f1f-182">當條件許可時，記憶體回收會針對特定層代進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-182">Garbage collections occur on specific generations as conditions warrant.</span></span> <span data-ttu-id="97f1f-183">回收層代是指回收該層代中的物件及其所有較新的層代。</span><span class="sxs-lookup"><span data-stu-id="97f1f-183">Collecting a generation means collecting objects in that generation and all its younger generations.</span></span> <span data-ttu-id="97f1f-184">層代 2 記憶體回收也稱為完整記憶體回收，因為它會回收所有層代中的所有物件 (亦即，Managed 堆積中的所有物件)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-184">A generation 2 garbage collection is also known as a full garbage collection, because it reclaims all objects in all generations (that is, all objects in the managed heap).</span></span>

### <a name="survival-and-promotions"></a><span data-ttu-id="97f1f-185">未回收和提升</span><span class="sxs-lookup"><span data-stu-id="97f1f-185">Survival and promotions</span></span>

<span data-ttu-id="97f1f-186">垃圾回收中未回收的物件稱為倖存者，並提升為下一代。</span><span class="sxs-lookup"><span data-stu-id="97f1f-186">Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation.</span></span> <span data-ttu-id="97f1f-187">在層代 0 記憶體回收中未被回收的物件會提升至層代 1、在層代 1 記憶體回收中未被回收的物件會提升至層代 2，而在層代 2 記憶體回收中未被回收的物件則保留在層代 2 中。</span><span class="sxs-lookup"><span data-stu-id="97f1f-187">Objects that survive a generation 0 garbage collection are promoted to generation 1; objects that survive a generation 1 garbage collection are promoted to generation 2; and objects that survive a generation 2 garbage collection remain in generation 2.</span></span>

<span data-ttu-id="97f1f-188">當垃圾回收器檢測到一代人的存活率很高時，它會增加該代的分配閾值。</span><span class="sxs-lookup"><span data-stu-id="97f1f-188">When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation.</span></span> <span data-ttu-id="97f1f-189">下一個集合獲得大量回收記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-189">The next collection gets a substantial size of reclaimed memory.</span></span> <span data-ttu-id="97f1f-190">CLR 不斷平衡兩個優先順序：不要讓應用程式的工作集通過延遲垃圾回收而變得太大，並且不要讓垃圾回收過於頻繁地運行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-190">The CLR continually balances two priorities: not letting an application's working set get too large by delaying garbage collection and not letting the garbage collection run too frequently.</span></span>

### <a name="ephemeral-generations-and-segments"></a><span data-ttu-id="97f1f-191">暫時層代和區段</span><span class="sxs-lookup"><span data-stu-id="97f1f-191">Ephemeral generations and segments</span></span>

<span data-ttu-id="97f1f-192">因為層代 0 和 1 中的物件存留較短，所以這些層代稱為暫時層代。</span><span class="sxs-lookup"><span data-stu-id="97f1f-192">Because objects in generations 0 and 1 are short-lived, these generations are known as the ephemeral generations.</span></span>

<span data-ttu-id="97f1f-193">暫時層代必須配置於稱為暫時區段的記憶體區段中。</span><span class="sxs-lookup"><span data-stu-id="97f1f-193">Ephemeral generations must be allocated in the memory segment that is known as the ephemeral segment.</span></span> <span data-ttu-id="97f1f-194">記憶體回收行程所取得的每個新區段都會成為新的暫時區段，而且包含在層代 0 記憶體回收中未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-194">Each new segment acquired by the garbage collector becomes the new ephemeral segment and contains the objects that survived a generation 0 garbage collection.</span></span> <span data-ttu-id="97f1f-195">舊的暫時區段會成為新的層代 2 區段。</span><span class="sxs-lookup"><span data-stu-id="97f1f-195">The old ephemeral segment becomes the new generation 2 segment.</span></span>

<span data-ttu-id="97f1f-196">臨時段的大小因系統是 32 位還是 64 位以及運行的垃圾回收器類型而異。</span><span class="sxs-lookup"><span data-stu-id="97f1f-196">The size of the ephemeral segment varies depending on whether a system is 32-bit or 64-bit, and on the type of garbage collector it is running.</span></span> <span data-ttu-id="97f1f-197">下表顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="97f1f-197">Default values are shown in the following table.</span></span>

||<span data-ttu-id="97f1f-198">32 位元</span><span class="sxs-lookup"><span data-stu-id="97f1f-198">32-bit</span></span>|<span data-ttu-id="97f1f-199">64 位元</span><span class="sxs-lookup"><span data-stu-id="97f1f-199">64-bit</span></span>|
|-|-------------|-------------|
|<span data-ttu-id="97f1f-200">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="97f1f-200">Workstation GC</span></span>|<span data-ttu-id="97f1f-201">16 MB</span><span class="sxs-lookup"><span data-stu-id="97f1f-201">16 MB</span></span>|<span data-ttu-id="97f1f-202">256 MB</span><span class="sxs-lookup"><span data-stu-id="97f1f-202">256 MB</span></span>|
|<span data-ttu-id="97f1f-203">伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="97f1f-203">Server GC</span></span>|<span data-ttu-id="97f1f-204">64 MB</span><span class="sxs-lookup"><span data-stu-id="97f1f-204">64 MB</span></span>|<span data-ttu-id="97f1f-205">4 GB</span><span class="sxs-lookup"><span data-stu-id="97f1f-205">4 GB</span></span>|
|<span data-ttu-id="97f1f-206">具有多於 4 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="97f1f-206">Server GC with > 4 logical CPUs</span></span>|<span data-ttu-id="97f1f-207">32 MB</span><span class="sxs-lookup"><span data-stu-id="97f1f-207">32 MB</span></span>|<span data-ttu-id="97f1f-208">2 GB</span><span class="sxs-lookup"><span data-stu-id="97f1f-208">2 GB</span></span>|
|<span data-ttu-id="97f1f-209">具有 > 8 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="97f1f-209">Server GC with > 8 logical CPUs</span></span>|<span data-ttu-id="97f1f-210">16 MB</span><span class="sxs-lookup"><span data-stu-id="97f1f-210">16 MB</span></span>|<span data-ttu-id="97f1f-211">1 GB</span><span class="sxs-lookup"><span data-stu-id="97f1f-211">1 GB</span></span>|

<span data-ttu-id="97f1f-212">暫時區段可能會包括層代 2 物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-212">The ephemeral segment can include generation 2 objects.</span></span> <span data-ttu-id="97f1f-213">層代 2 物件可以使用多個區段 (取決於處理序所需而且記憶體允許的數目)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-213">Generation 2 objects can use multiple segments (as many as your process requires and memory allows for).</span></span>

<span data-ttu-id="97f1f-214">暫時記憶體回收中釋放記憶體的數量會限制為暫時區段的大小。</span><span class="sxs-lookup"><span data-stu-id="97f1f-214">The amount of freed memory from an ephemeral garbage collection is limited to the size of the ephemeral segment.</span></span> <span data-ttu-id="97f1f-215">所釋放的記憶體數量會與無作用物件所佔據的空間成正比。</span><span class="sxs-lookup"><span data-stu-id="97f1f-215">The amount of memory that is freed is proportional to the space that was occupied by the dead objects.</span></span>

## <a name="what-happens-during-a-garbage-collection"></a><span data-ttu-id="97f1f-216">記憶體回收期間進行的作業</span><span class="sxs-lookup"><span data-stu-id="97f1f-216">What happens during a garbage collection</span></span>

<span data-ttu-id="97f1f-217">記憶體回收具有下列階段：</span><span class="sxs-lookup"><span data-stu-id="97f1f-217">A garbage collection has the following phases:</span></span>

- <span data-ttu-id="97f1f-218">標記階段：尋找和建立所有使用中物件的清單。</span><span class="sxs-lookup"><span data-stu-id="97f1f-218">A marking phase that finds and creates a list of all live objects.</span></span>

- <span data-ttu-id="97f1f-219">重新配置階段：更新即將壓縮之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="97f1f-219">A relocating phase that updates the references to the objects that will be compacted.</span></span>

- <span data-ttu-id="97f1f-220">壓縮階段：回收無作用物件所佔據的空間並壓縮未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-220">A compacting phase that reclaims the space occupied by the dead objects and compacts the surviving objects.</span></span> <span data-ttu-id="97f1f-221">壓縮階段會將記憶體回收中未被回收的物件移至區段的較舊端。</span><span class="sxs-lookup"><span data-stu-id="97f1f-221">The compacting phase moves objects that have survived a garbage collection toward the older end of the segment.</span></span>

  <span data-ttu-id="97f1f-222">因為層代 2 回收可能會佔據多個區段，所以提升至層代 2 的物件可能會移至較舊區段。</span><span class="sxs-lookup"><span data-stu-id="97f1f-222">Because generation 2 collections can occupy multiple segments, objects that are promoted into generation 2 can be moved into an older segment.</span></span> <span data-ttu-id="97f1f-223">層代 1 和層代 2 的未回收物件都可能會移至不同的區段，因為它們都會被提升至層代 2。</span><span class="sxs-lookup"><span data-stu-id="97f1f-223">Both generation 1 and generation 2 survivors can be moved to a different segment, because they are promoted to generation 2.</span></span>

  <span data-ttu-id="97f1f-224">通常，大型物件堆 （LOH） 不會壓縮，因為複製大型物件會造成性能損失。</span><span class="sxs-lookup"><span data-stu-id="97f1f-224">Ordinarily, the large object heap (LOH) is not compacted, because copying large objects imposes a performance penalty.</span></span> <span data-ttu-id="97f1f-225">但是，在 .NET Core 和 .NET 框架 4.5.1 及<xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>更高版本中，可以使用 屬性按需壓縮大型物件堆。</span><span class="sxs-lookup"><span data-stu-id="97f1f-225">However, in .NET Core and in .NET Framework 4.5.1 and later, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand.</span></span> <span data-ttu-id="97f1f-226">此外，通過指定以下任一條件設置硬限制時，LOH 會自動壓縮：</span><span class="sxs-lookup"><span data-stu-id="97f1f-226">In addition, the LOH is automatically compacted when a hard limit is set by specifying either:</span></span>

  - <span data-ttu-id="97f1f-227">容器上的記憶體限制，或</span><span class="sxs-lookup"><span data-stu-id="97f1f-227">a memory limit on a container, or</span></span>
  - <span data-ttu-id="97f1f-228">[GCHeapHard 限制](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit)或[GCHeapHard 限制百分比](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="97f1f-228">the [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) or [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) run-time configuration options</span></span>

<span data-ttu-id="97f1f-229">記憶體回收行程會使用下列資訊來判斷物件是否使用中：</span><span class="sxs-lookup"><span data-stu-id="97f1f-229">The garbage collector uses the following information to determine whether objects are live:</span></span>

- <span data-ttu-id="97f1f-230">**堆疊根**。</span><span class="sxs-lookup"><span data-stu-id="97f1f-230">**Stack roots**.</span></span> <span data-ttu-id="97f1f-231">Just-in-Time (JIT) 編譯器和堆疊查核器所提供的堆疊變數。</span><span class="sxs-lookup"><span data-stu-id="97f1f-231">Stack variables provided by the just-in-time (JIT) compiler and stack walker.</span></span> <span data-ttu-id="97f1f-232">JIT 優化可以延長或縮短向垃圾回收器報告堆疊變數的代碼區域。</span><span class="sxs-lookup"><span data-stu-id="97f1f-232">JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.</span></span>

- <span data-ttu-id="97f1f-233">**垃圾回收控制碼**。</span><span class="sxs-lookup"><span data-stu-id="97f1f-233">**Garbage collection handles**.</span></span> <span data-ttu-id="97f1f-234">會指向 Managed 物件，而且可由使用者程式碼或 Common Language Runtime 配置的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="97f1f-234">Handles that point to managed objects and that can be allocated by user code or by the common language runtime.</span></span>

- <span data-ttu-id="97f1f-235">**靜態資料**。</span><span class="sxs-lookup"><span data-stu-id="97f1f-235">**Static data**.</span></span> <span data-ttu-id="97f1f-236">應用程式定義域中可能參考其他物件的靜態物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-236">Static objects in application domains that could be referencing other objects.</span></span> <span data-ttu-id="97f1f-237">每個應用程式定義域都會追蹤其靜態物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-237">Each application domain keeps track of its static objects.</span></span>

<span data-ttu-id="97f1f-238">記憶體回收開始之前，所有 Managed 執行緒都會暫停，但觸發記憶體回收的執行緒除外。</span><span class="sxs-lookup"><span data-stu-id="97f1f-238">Before a garbage collection starts, all managed threads are suspended except for the thread that triggered the garbage collection.</span></span>

<span data-ttu-id="97f1f-239">下圖顯示觸發記憶體回收且造成其他執行緒暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="97f1f-239">The following illustration shows a thread that triggers a garbage collection and causes the other threads to be suspended.</span></span>

![當執行緒觸發記憶體回收時](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a><span data-ttu-id="97f1f-241">操作非託管資源</span><span class="sxs-lookup"><span data-stu-id="97f1f-241">Manipulate unmanaged resources</span></span>

<span data-ttu-id="97f1f-242">如果託管物件使用其本機檔案控制代碼引用非託管物件，則必須顯式釋放非託管物件，因為垃圾回收器僅跟蹤託管堆上的記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f1f-242">If managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector only tracks memory on the managed heap.</span></span>

<span data-ttu-id="97f1f-243">託管物件的使用者可能不會釋放該物件使用的本機資源。</span><span class="sxs-lookup"><span data-stu-id="97f1f-243">Users of the managed object may not dispose the native resources used by the object.</span></span> <span data-ttu-id="97f1f-244">要執行清理，可以使託管物件可最終化。</span><span class="sxs-lookup"><span data-stu-id="97f1f-244">To perform the cleanup, you can make the managed object finalizable.</span></span> <span data-ttu-id="97f1f-245">最終化包括在物件不再使用時執行的清理操作。</span><span class="sxs-lookup"><span data-stu-id="97f1f-245">Finalization consists of cleanup actions that execute when the object is no longer in use.</span></span> <span data-ttu-id="97f1f-246">當託管物件死亡時，它將執行在其終端子方法中指定的清理操作。</span><span class="sxs-lookup"><span data-stu-id="97f1f-246">When the managed object dies, it performs cleanup actions that are specified in its finalizer method.</span></span>

<span data-ttu-id="97f1f-247">當系統發現某個可最終處理物件無作用時，該物件的完成項就會放入佇列中，以便執行其清除動作，但是物件本身會提升至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="97f1f-247">When a finalizable object is discovered to be dead, its finalizer is put in a queue so that its cleanup actions are executed, but the object itself is promoted to the next generation.</span></span> <span data-ttu-id="97f1f-248">因此，您必須等候直到在該層代上進行的下一次記憶體回收 (不一定是下一次記憶體回收)，以便判斷此物件是否已經回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-248">Therefore, you have to wait until the next garbage collection that occurs on that generation (which is not necessarily the next garbage collection) to determine whether the object has been reclaimed.</span></span>

<span data-ttu-id="97f1f-249">有關最終化的詳細資訊，請參閱<xref:System.Object.Finalize?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="97f1f-249">For more information about finalization, see <xref:System.Object.Finalize?displayProperty=nameWithType>.</span></span>

## <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="97f1f-250">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-250">Workstation and server garbage collection</span></span>

<span data-ttu-id="97f1f-251">記憶體回收行程會自行調整而且可在各種案例中運作。</span><span class="sxs-lookup"><span data-stu-id="97f1f-251">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="97f1f-252">可以使用[設定檔設置](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)根據工作負載的特徵設置垃圾回收的類型。</span><span class="sxs-lookup"><span data-stu-id="97f1f-252">You can use a [configuration file setting](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) to set the type of garbage collection based on the characteristics of the workload.</span></span> <span data-ttu-id="97f1f-253">CLR 會提供下列記憶體回收類型：</span><span class="sxs-lookup"><span data-stu-id="97f1f-253">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="97f1f-254">工作站垃圾回收 （GC） 專為用戶端應用而設計。</span><span class="sxs-lookup"><span data-stu-id="97f1f-254">Workstation garbage collection (GC) is designed for client apps.</span></span> <span data-ttu-id="97f1f-255">它是獨立應用的預設 GC 風格。</span><span class="sxs-lookup"><span data-stu-id="97f1f-255">It is the default GC flavor for standalone apps.</span></span> <span data-ttu-id="97f1f-256">對於託管應用（例如，由ASP.NET託管的應用，主機確定預設 GC 風格。</span><span class="sxs-lookup"><span data-stu-id="97f1f-256">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="97f1f-257">工作站記憶體回收可能是並行或非並行的。</span><span class="sxs-lookup"><span data-stu-id="97f1f-257">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="97f1f-258">並行記憶體回收可讓 Managed 執行緒在記憶體回收期間繼續運作。</span><span class="sxs-lookup"><span data-stu-id="97f1f-258">Concurrent garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="97f1f-259">[後臺垃圾回收](#background-workstation-garbage-collection)將替換 .NET 框架 4 和更高版本中[的併發垃圾回收](#concurrent-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-259">[Background garbage collection](#background-workstation-garbage-collection) replaces [concurrent garbage collection](#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="97f1f-260">伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="97f1f-260">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="97f1f-261">在 .NET Core 中，伺服器垃圾回收可以是非併發或後臺。</span><span class="sxs-lookup"><span data-stu-id="97f1f-261">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="97f1f-262">在 .NET Framework 4.5 和更高版本中，伺服器垃圾回收可以是非併發或後臺（後臺垃圾回收將取代併發垃圾回收）。</span><span class="sxs-lookup"><span data-stu-id="97f1f-262">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background (background garbage collection replaces concurrent garbage collection).</span></span> <span data-ttu-id="97f1f-263">在 .NET 框架 4 和早期版本中，伺服器垃圾回收是非併發的。</span><span class="sxs-lookup"><span data-stu-id="97f1f-263">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="97f1f-264">下圖顯示了在伺服器上執行垃圾回收的專用線程：</span><span class="sxs-lookup"><span data-stu-id="97f1f-264">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![伺服器記憶體回收執行緒](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a><span data-ttu-id="97f1f-266">比較工作站和伺服器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-266">Compare workstation and server garbage collection</span></span>

<span data-ttu-id="97f1f-267">以下是工作站記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="97f1f-267">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="97f1f-268">此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="97f1f-268">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="97f1f-269">因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="97f1f-269">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="97f1f-270">（運行本機代碼的執行緒不會在伺服器或工作站垃圾回收上掛起。</span><span class="sxs-lookup"><span data-stu-id="97f1f-270">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="97f1f-271">工作站垃圾回收始終用於只有一個處理器的電腦，而不考慮[配置設置](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。</span><span class="sxs-lookup"><span data-stu-id="97f1f-271">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

<span data-ttu-id="97f1f-272">以下是伺服器記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="97f1f-272">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="97f1f-273">此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-273">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="97f1f-274">執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-274">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="97f1f-275">每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="97f1f-275">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="97f1f-276">不同堆積上的物件可以彼此參考。</span><span class="sxs-lookup"><span data-stu-id="97f1f-276">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="97f1f-277">因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。</span><span class="sxs-lookup"><span data-stu-id="97f1f-277">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="97f1f-278">伺服器記憶體回收通常具有較大的區段。</span><span class="sxs-lookup"><span data-stu-id="97f1f-278">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="97f1f-279">但是，這只是一個概括：段大小特定于實現，可能會發生變化。</span><span class="sxs-lookup"><span data-stu-id="97f1f-279">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="97f1f-280">調整應用時，不要對垃圾回收器分配的段大小進行假設。</span><span class="sxs-lookup"><span data-stu-id="97f1f-280">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="97f1f-281">伺服器記憶體回收可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="97f1f-281">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="97f1f-282">例如，假設有 12 個進程使用伺服器 GC 運行在具有 4 個處理器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="97f1f-282">For example, imagine that there are 12 processes that use server GC running on a computer that has 4 processors.</span></span> <span data-ttu-id="97f1f-283">如果所有進程都同時收集垃圾，它們就會相互干擾，因為同一處理器上將安排 12 個執行緒。</span><span class="sxs-lookup"><span data-stu-id="97f1f-283">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="97f1f-284">如果進程處於活動狀態，則讓所有進程都使用伺服器 GC 不是個好主意。</span><span class="sxs-lookup"><span data-stu-id="97f1f-284">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="97f1f-285">如果您正在運行應用程式的數百個實例，請考慮使用禁用併發垃圾回收的工作站垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-285">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="97f1f-286">這樣會產生較少的內容切換，因此可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="97f1f-286">This will result in less context switching, which can improve performance.</span></span>

## <a name="background-workstation-garbage-collection"></a><span data-ttu-id="97f1f-287">背景工作站記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-287">Background workstation garbage collection</span></span>

<span data-ttu-id="97f1f-288">在後臺工作站垃圾回收中，臨時代（0 和 1）根據需要收集，同時收集第 2 代正在進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-288">In background workstation garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress.</span></span> <span data-ttu-id="97f1f-289">後臺工作站垃圾回收在專用線程上執行，僅應用於第 2 代集合。</span><span class="sxs-lookup"><span data-stu-id="97f1f-289">Background workstation garbage collection is performed on a dedicated thread and applies only to generation 2 collections.</span></span>

<span data-ttu-id="97f1f-290">預設情況下，後臺垃圾回收處於啟用狀態，並且可以通過 .NET Framework 應用中[的 gc併發](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)配置設置或 .NET Core 應用中[的 System.GC.併發](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)設置啟用或禁用。</span><span class="sxs-lookup"><span data-stu-id="97f1f-290">Background garbage collection is enabled by default and can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.</span></span>

> [!NOTE]
> <span data-ttu-id="97f1f-291">後臺垃圾回收將替換[併發垃圾回收](#concurrent-garbage-collection)，並在 .NET 框架 4 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="97f1f-291">Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions.</span></span> <span data-ttu-id="97f1f-292">在 .NET 框架 4 中，它僅支援工作站垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-292">In .NET Framework 4, it's supported only for workstation garbage collection.</span></span> <span data-ttu-id="97f1f-293">從 .NET 框架 4.5 開始，後臺垃圾回收可用於工作站和伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-293">Starting with .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.</span></span>

<span data-ttu-id="97f1f-294">背景記憶體回收期間，暫時層代的回收稱為前景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-294">A collection on ephemeral generations during background garbage collection is known as foreground garbage collection.</span></span> <span data-ttu-id="97f1f-295">進行前景記憶體回收時，所有 Managed 執行緒都會暫停。</span><span class="sxs-lookup"><span data-stu-id="97f1f-295">When foreground garbage collections occur, all managed threads are suspended.</span></span>

<span data-ttu-id="97f1f-296">當後臺垃圾回收正在進行，並且您在第 0 代中分配了足夠的物件時，CLR 將執行第 0 代或第 1 代前臺垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-296">When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection.</span></span> <span data-ttu-id="97f1f-297">專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。</span><span class="sxs-lookup"><span data-stu-id="97f1f-297">The dedicated background garbage collection thread checks at frequent safe points to determine whether there is a request for foreground garbage collection.</span></span> <span data-ttu-id="97f1f-298">如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-298">If there is, the background collection suspends itself so that foreground garbage collection can occur.</span></span> <span data-ttu-id="97f1f-299">在前景記憶體回收完成之後，專屬的背景記憶體回收執行緒和使用者執行緒就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-299">After the foreground garbage collection is completed, the dedicated background garbage collection thread and user threads resume.</span></span>

<span data-ttu-id="97f1f-300">背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-300">Background garbage collection removes allocation restrictions imposed by concurrent garbage collection, because ephemeral garbage collections can occur during background garbage collection.</span></span> <span data-ttu-id="97f1f-301">後臺垃圾回收可以刪除臨時代中的死物件。</span><span class="sxs-lookup"><span data-stu-id="97f1f-301">Background garbage collection can remove dead objects in ephemeral generations.</span></span> <span data-ttu-id="97f1f-302">如果需要，它還可以在第 1 代垃圾回收期間展開堆。</span><span class="sxs-lookup"><span data-stu-id="97f1f-302">It can also expand the heap if needed during a generation 1 garbage collection.</span></span>

<span data-ttu-id="97f1f-303">下圖顯示在工作站上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="97f1f-303">The following illustration shows background garbage collection performed on a separate dedicated thread on a workstation:</span></span>

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a><span data-ttu-id="97f1f-305">背景伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-305">Background server garbage collection</span></span>

<span data-ttu-id="97f1f-306">從 .NET 框架 4.5 開始，後臺伺服器垃圾回收是伺服器垃圾回收的預設模式。</span><span class="sxs-lookup"><span data-stu-id="97f1f-306">Starting with .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.</span></span>

<span data-ttu-id="97f1f-307">後臺伺服器垃圾回收功能類似于上一節所述的後臺工作站垃圾回收，但有一些區別：</span><span class="sxs-lookup"><span data-stu-id="97f1f-307">Background server garbage collection functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences:</span></span>

- <span data-ttu-id="97f1f-308">後臺工作站垃圾回收使用一個專用後臺垃圾回收執行緒，而後台伺服器垃圾回收使用多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="97f1f-308">Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads.</span></span> <span data-ttu-id="97f1f-309">通常，每個邏輯處理器都有一個專用線程。</span><span class="sxs-lookup"><span data-stu-id="97f1f-309">Typically, there's a dedicated thread for each logical processor.</span></span>

- <span data-ttu-id="97f1f-310">與工作站背景記憶體回收執行緒不同的是，這些執行緒不會逾時。</span><span class="sxs-lookup"><span data-stu-id="97f1f-310">Unlike the workstation background garbage collection thread, these threads do not time out.</span></span>

<span data-ttu-id="97f1f-311">下圖顯示在伺服器上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="97f1f-311">The following illustration shows background garbage collection performed on a separate dedicated thread on a server:</span></span>

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a><span data-ttu-id="97f1f-313">並行的記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-313">Concurrent garbage collection</span></span>

> [!TIP]
> <span data-ttu-id="97f1f-314">本節適用於：</span><span class="sxs-lookup"><span data-stu-id="97f1f-314">This section applies to:</span></span>
>
> - <span data-ttu-id="97f1f-315">.NET 框架 3.5 及更早版本用於工作站垃圾回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-315">.NET Framework 3.5 and earlier for workstation garbage collection</span></span>
> - <span data-ttu-id="97f1f-316">.NET 框架 4 及更早版本用於伺服器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-316">.NET Framework 4 and earlier for server garbage collection</span></span>
>
> <span data-ttu-id="97f1f-317">並行垃圾在更高版本中被[後臺垃圾回收](#background-workstation-garbage-collection)替換。</span><span class="sxs-lookup"><span data-stu-id="97f1f-317">Concurrent garbage is replaced by [background garbage collection](#background-workstation-garbage-collection) in later versions.</span></span>

<span data-ttu-id="97f1f-318">在工作站或伺服器垃圾回收中，可以[啟用併發垃圾回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)，使執行緒與在收集的大部分持續時間內執行垃圾回收的專用線程同時運行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-318">In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection.</span></span> <span data-ttu-id="97f1f-319">這個選項只會影響層代 2 中的記憶體回收。層代 0 和 1 一律為非並行，因為它們的完成速度非常快。</span><span class="sxs-lookup"><span data-stu-id="97f1f-319">This option affects only garbage collections in generation 2; generations 0 and 1 are always non-concurrent because they finish very fast.</span></span>

<span data-ttu-id="97f1f-320">並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。</span><span class="sxs-lookup"><span data-stu-id="97f1f-320">Concurrent garbage collection enables interactive applications to be more responsive by minimizing pauses for a collection.</span></span> <span data-ttu-id="97f1f-321">當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-321">Managed threads can continue to run most of the time while the concurrent garbage collection thread is running.</span></span> <span data-ttu-id="97f1f-322">這會在記憶體回收進行時縮短暫停時間。</span><span class="sxs-lookup"><span data-stu-id="97f1f-322">This results in shorter pauses while a garbage collection is occurring.</span></span>

<span data-ttu-id="97f1f-323">並行記憶體回收會針對專屬執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="97f1f-323">Concurrent garbage collection is performed on a dedicated thread.</span></span> <span data-ttu-id="97f1f-324">根據預設，CLR 會執行工作站記憶體回收並啟用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-324">By default, the CLR runs workstation garbage collection with concurrent garbage collection enabled.</span></span> <span data-ttu-id="97f1f-325">這種回收適用於單一處理器和多處理器電腦。</span><span class="sxs-lookup"><span data-stu-id="97f1f-325">This is true for single-processor and multi-processor computers.</span></span>

<span data-ttu-id="97f1f-326">下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="97f1f-326">The following illustration shows concurrent garbage collection performed on a separate dedicated thread.</span></span>

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a><span data-ttu-id="97f1f-328">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f1f-328">See also</span></span>

- [<span data-ttu-id="97f1f-329">GC 的配置選項</span><span class="sxs-lookup"><span data-stu-id="97f1f-329">Configuration options for GC</span></span>](../../core/run-time-config/garbage-collector.md)
- [<span data-ttu-id="97f1f-330">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f1f-330">Garbage collection</span></span>](index.md)
