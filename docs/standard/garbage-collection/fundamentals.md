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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330422"
---
# <a name="fundamentals-of-garbage-collection"></a><span data-ttu-id="a891e-103">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="a891e-103">Fundamentals of garbage collection</span></span>

<span data-ttu-id="a891e-104">在 common language runtime （CLR）中，垃圾收集行程（GC）可作為自動記憶體管理員。</span><span class="sxs-lookup"><span data-stu-id="a891e-104">In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager.</span></span> <span data-ttu-id="a891e-105">它提供了下列優點：</span><span class="sxs-lookup"><span data-stu-id="a891e-105">It provides the following benefits:</span></span>

- <span data-ttu-id="a891e-106">可讓您開發應用程式，而不需要手動釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-106">Enables you to develop your application without having to manually free memory.</span></span>

- <span data-ttu-id="a891e-107">有效率地在 Managed 堆積上配置物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-107">Allocates objects on the managed heap efficiently.</span></span>

- <span data-ttu-id="a891e-108">回收不再使用的物件、清除其記憶體，並且讓記憶體可供未來的配置使用。</span><span class="sxs-lookup"><span data-stu-id="a891e-108">Reclaims objects that are no longer being used, clears their memory, and keeps the memory available for future allocations.</span></span> <span data-ttu-id="a891e-109">Managed 物件在開始時會自動取得乾淨的內容，因此其建構函式不需要初始化每個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="a891e-109">Managed objects automatically get clean content to start with, so their constructors do not have to initialize every data field.</span></span>

- <span data-ttu-id="a891e-110">確保某個物件無法使用另一個物件的內容，藉以提供記憶體安全性。</span><span class="sxs-lookup"><span data-stu-id="a891e-110">Provides memory safety by making sure that an object cannot use the content of another object.</span></span>

<span data-ttu-id="a891e-111">本文描述垃圾收集的核心概念。</span><span class="sxs-lookup"><span data-stu-id="a891e-111">This article describes the core concepts of garbage collection.</span></span>

## <a name="fundamentals-of-memory"></a><span data-ttu-id="a891e-112">記憶體的基本概念</span><span class="sxs-lookup"><span data-stu-id="a891e-112">Fundamentals of memory</span></span>

<span data-ttu-id="a891e-113">下列清單摘要說明重要的 CLR 記憶體概念。</span><span class="sxs-lookup"><span data-stu-id="a891e-113">The following list summarizes important CLR memory concepts.</span></span>

- <span data-ttu-id="a891e-114">每個處理序都有各自獨立的虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="a891e-114">Each process has its own, separate virtual address space.</span></span> <span data-ttu-id="a891e-115">相同電腦上的所有處理常式都會共用相同的實體記憶體和分頁檔（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="a891e-115">All processes on the same computer share the same physical memory and the page file, if there is one.</span></span>

- <span data-ttu-id="a891e-116">根據預設，在 32 位元電腦上，每個處理序都有 2 GB 使用者模式虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="a891e-116">By default, on 32-bit computers, each process has a 2-GB user-mode virtual address space.</span></span>

- <span data-ttu-id="a891e-117">身為應用程式開發人員，您只會處理虛擬位址空間，絕不會直接操作實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-117">As an application developer, you work only with virtual address space and never manipulate physical memory directly.</span></span> <span data-ttu-id="a891e-118">記憶體回收行程會在 Managed 堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-118">The garbage collector allocates and frees virtual memory for you on the managed heap.</span></span>

  <span data-ttu-id="a891e-119">如果您要撰寫機器碼，請使用 Windows 函數來處理虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="a891e-119">If you are writing native code, you use Windows functions to work with the virtual address space.</span></span> <span data-ttu-id="a891e-120">這些函式會在原生堆積上自動配置和釋出虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-120">These functions allocate and free virtual memory for you on native heaps.</span></span>

- <span data-ttu-id="a891e-121">虛擬記憶體可以有三種狀態：</span><span class="sxs-lookup"><span data-stu-id="a891e-121">Virtual memory can be in three states:</span></span>

  - <span data-ttu-id="a891e-122">可用。</span><span class="sxs-lookup"><span data-stu-id="a891e-122">Free.</span></span> <span data-ttu-id="a891e-123">記憶體區塊沒有任何參考，可進行配置。</span><span class="sxs-lookup"><span data-stu-id="a891e-123">The block of memory has no references to it and is available for allocation.</span></span>

  - <span data-ttu-id="a891e-124">保留。</span><span class="sxs-lookup"><span data-stu-id="a891e-124">Reserved.</span></span> <span data-ttu-id="a891e-125">記憶體區塊可供您使用，但是無法用於任何其他配置要求。</span><span class="sxs-lookup"><span data-stu-id="a891e-125">The block of memory is available for your use and cannot be used for any other allocation request.</span></span> <span data-ttu-id="a891e-126">不過，在此記憶體區塊認可之前，您無法將資料儲存到其中。</span><span class="sxs-lookup"><span data-stu-id="a891e-126">However, you cannot store data to this memory block until it is committed.</span></span>

  - <span data-ttu-id="a891e-127">已認可。</span><span class="sxs-lookup"><span data-stu-id="a891e-127">Committed.</span></span> <span data-ttu-id="a891e-128">記憶體區塊會指派給實體儲存區。</span><span class="sxs-lookup"><span data-stu-id="a891e-128">The block of memory is assigned to physical storage.</span></span>

- <span data-ttu-id="a891e-129">虛擬位址空間可能會分成片段。</span><span class="sxs-lookup"><span data-stu-id="a891e-129">Virtual address space can get fragmented.</span></span> <span data-ttu-id="a891e-130">這表示，位址空間中有可用的區塊，也稱為可用的洞 (Hole)。</span><span class="sxs-lookup"><span data-stu-id="a891e-130">This means that there are free blocks, also known as holes, in the address space.</span></span> <span data-ttu-id="a891e-131">要求虛擬記憶體配置時，虛擬記憶體管理程式必須找到大小可滿足配置要求的單一可用區塊。</span><span class="sxs-lookup"><span data-stu-id="a891e-131">When a virtual memory allocation is requested, the virtual memory manager has to find a single free block that is large enough to satisfy that allocation request.</span></span> <span data-ttu-id="a891e-132">即使您擁有 2GB 可用空間，要求 2GB 的配置仍然不會成功，除非該可用空間全都在單一位址區塊中。</span><span class="sxs-lookup"><span data-stu-id="a891e-132">Even if you have 2 GB of free space, the allocation that requires 2 GB will be unsuccessful unless all of that free space is in a single address block.</span></span>

- <span data-ttu-id="a891e-133">如果沒有足夠的虛擬位址空間可供保留或實體空間認可，您可以用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-133">You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.</span></span>

  <span data-ttu-id="a891e-134">即使實體記憶體壓力（也就是實體記憶體的需求）偏低，也會使用分頁檔案。</span><span class="sxs-lookup"><span data-stu-id="a891e-134">The page file is used even if physical memory pressure (that is, demand for physical memory) is low.</span></span> <span data-ttu-id="a891e-135">第一次實體記憶體壓力很高時，作業系統必須在實體記憶體中騰出空間來儲存資料，而且它會將實體記憶體中的一些資料備份至分頁檔案。</span><span class="sxs-lookup"><span data-stu-id="a891e-135">The first time physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file.</span></span> <span data-ttu-id="a891e-136">該資料在需要之前不會分頁，因此可能會在實體記憶體不足壓力的情況下遇到分頁。</span><span class="sxs-lookup"><span data-stu-id="a891e-136">That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.</span></span>

## <a name="conditions-for-a-garbage-collection"></a><span data-ttu-id="a891e-137">記憶體回收的條件</span><span class="sxs-lookup"><span data-stu-id="a891e-137">Conditions for a garbage collection</span></span>

<span data-ttu-id="a891e-138">當下列其中一個條件成立時，就會進行記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="a891e-138">Garbage collection occurs when one of the following conditions is true:</span></span>

- <span data-ttu-id="a891e-139">系統的實體記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="a891e-139">The system has low physical memory.</span></span> <span data-ttu-id="a891e-140">這是由作業系統的低記憶體通知或主機所指示的記憶體不足所偵測到。</span><span class="sxs-lookup"><span data-stu-id="a891e-140">This is detected by either the low memory notification from the OS or low memory as indicated by the host.</span></span>

- <span data-ttu-id="a891e-141">由 Managed 堆積上之已配置物件所使用的記憶體超過可接受的臨界值。</span><span class="sxs-lookup"><span data-stu-id="a891e-141">The memory that is used by allocated objects on the managed heap surpasses an acceptable threshold.</span></span> <span data-ttu-id="a891e-142">這個臨界值會在處理序執行時持續調整。</span><span class="sxs-lookup"><span data-stu-id="a891e-142">This threshold is continuously adjusted as the process runs.</span></span>

- <span data-ttu-id="a891e-143">呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a891e-143">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a891e-144">在大多數的情況下，您不需要呼叫這個方法，因為記憶體回收行程會持續執行。</span><span class="sxs-lookup"><span data-stu-id="a891e-144">In almost all cases, you do not have to call this method, because the garbage collector runs continuously.</span></span> <span data-ttu-id="a891e-145">這個方法主要用於獨特的情況和測試。</span><span class="sxs-lookup"><span data-stu-id="a891e-145">This method is primarily used for unique situations and testing.</span></span>

## <a name="the-managed-heap"></a><span data-ttu-id="a891e-146">Managed 堆積</span><span class="sxs-lookup"><span data-stu-id="a891e-146">The managed heap</span></span>

<span data-ttu-id="a891e-147">CLR 初始化記憶體回收行程之後，記憶體回收行程就會配置用來儲存和管理物件的記憶體區段。</span><span class="sxs-lookup"><span data-stu-id="a891e-147">After the garbage collector is initialized by the CLR, it allocates a segment of memory to store and manage objects.</span></span> <span data-ttu-id="a891e-148">這個記憶體稱為 Managed 堆積，與作業系統中的原生堆積相反。</span><span class="sxs-lookup"><span data-stu-id="a891e-148">This memory is called the managed heap, as opposed to a native heap in the operating system.</span></span>

<span data-ttu-id="a891e-149">每個 Managed 處理序都有一個 Managed 堆積。</span><span class="sxs-lookup"><span data-stu-id="a891e-149">There is a managed heap for each managed process.</span></span> <span data-ttu-id="a891e-150">處理序中的所有執行緒都會對相同堆積上的物件配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-150">All threads in the process allocate memory for objects on the same heap.</span></span>

<span data-ttu-id="a891e-151">為了保留記憶體，垃圾收集行程會呼叫 Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)函式，並針對 managed 應用程式一次保留一個記憶體區段。</span><span class="sxs-lookup"><span data-stu-id="a891e-151">To reserve memory, the garbage collector calls the Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function and reserves one segment of memory at a time for managed applications.</span></span> <span data-ttu-id="a891e-152">垃圾收集行程也會視需要保留區段，並藉由呼叫 Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)函數，將區段釋放回作業系統（在清除任何物件之後）。</span><span class="sxs-lookup"><span data-stu-id="a891e-152">The garbage collector also reserves segments, as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a891e-153">記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="a891e-153">The size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="a891e-154">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="a891e-154">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

<span data-ttu-id="a891e-155">配置在堆積上的物件越少，記憶體回收行程必須進行的工作就越少。</span><span class="sxs-lookup"><span data-stu-id="a891e-155">The fewer objects allocated on the heap, the less work the garbage collector has to do.</span></span> <span data-ttu-id="a891e-156">當您配置物件時，請勿使用超出需求的進位值，例如，當您只需要 15 個位元組時，卻配置 32 個位元組的陣列。</span><span class="sxs-lookup"><span data-stu-id="a891e-156">When you allocate objects, do not use rounded-up values that exceed your needs, such as allocating an array of 32 bytes when you need only 15 bytes.</span></span>

<span data-ttu-id="a891e-157">觸發記憶體回收時，記憶體回收行程就會回收無作用物件所佔據的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-157">When a garbage collection is triggered, the garbage collector reclaims the memory that is occupied by dead objects.</span></span> <span data-ttu-id="a891e-158">回收處理序會壓縮使用中物件，讓它們集合在一起，並且移除無作用物件，因而讓堆積更小。</span><span class="sxs-lookup"><span data-stu-id="a891e-158">The reclaiming process compacts live objects so that they are moved together, and the dead space is removed, thereby making the heap smaller.</span></span> <span data-ttu-id="a891e-159">這樣可確保一起配置的物件會在 Managed 堆積上集中，以便保持其區域性。</span><span class="sxs-lookup"><span data-stu-id="a891e-159">This ensures that objects that are allocated together stay together on the managed heap, to preserve their locality.</span></span>

<span data-ttu-id="a891e-160">記憶體回收的干擾程度 (頻率和持續期間) 是 Managed 堆積上之配置量和未被回收記憶體數量的結果。</span><span class="sxs-lookup"><span data-stu-id="a891e-160">The intrusiveness (frequency and duration) of garbage collections is the result of the volume of allocations and the amount of survived memory on the managed heap.</span></span>

<span data-ttu-id="a891e-161">您可以將此堆積視為兩個堆積的累積：[大型物件堆積](large-object-heap.md)和小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="a891e-161">The heap can be considered as the accumulation of two heaps: the [large object heap](large-object-heap.md) and the small object heap.</span></span>

<span data-ttu-id="a891e-162">[大型物件堆積](large-object-heap.md)包含 85,000 個位元組以上的超大型物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-162">The [large object heap](large-object-heap.md) contains very large objects that are 85,000 bytes and larger.</span></span> <span data-ttu-id="a891e-163">大型物件堆積上的物件通常是陣列。</span><span class="sxs-lookup"><span data-stu-id="a891e-163">The objects on the large object heap are usually arrays.</span></span> <span data-ttu-id="a891e-164">超大型的執行個體物件非常罕見。</span><span class="sxs-lookup"><span data-stu-id="a891e-164">It is rare for an instance object to be extremely large.</span></span>

> [!TIP]
> <span data-ttu-id="a891e-165">您可以設定物件在大型物件堆積上[的臨界值大小](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold)。</span><span class="sxs-lookup"><span data-stu-id="a891e-165">You can [configure the threshold size](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) for objects to go on the large object heap.</span></span>

## <a name="generations"></a><span data-ttu-id="a891e-166">層代</span><span class="sxs-lookup"><span data-stu-id="a891e-166">Generations</span></span>

<span data-ttu-id="a891e-167">堆積會組織成層代，因此它可以處理存留較久和存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-167">The heap is organized into generations so it can handle long-lived and short-lived objects.</span></span> <span data-ttu-id="a891e-168">記憶體回收主要與存留較短物件的回收一起進行，而這些物件通常只佔據堆積的一小部分。</span><span class="sxs-lookup"><span data-stu-id="a891e-168">Garbage collection primarily occurs with the reclamation of short-lived objects that typically occupy only a small part of the heap.</span></span> <span data-ttu-id="a891e-169">堆積上的物件有三個層代：</span><span class="sxs-lookup"><span data-stu-id="a891e-169">There are three generations of objects on the heap:</span></span>

- <span data-ttu-id="a891e-170">**層代 0**。</span><span class="sxs-lookup"><span data-stu-id="a891e-170">**Generation 0**.</span></span> <span data-ttu-id="a891e-171">這是最新的層代而且包含存留較短的物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-171">This is the youngest generation and contains short-lived objects.</span></span> <span data-ttu-id="a891e-172">存留較短的物件範例是暫存變數。</span><span class="sxs-lookup"><span data-stu-id="a891e-172">An example of a short-lived object is a temporary variable.</span></span> <span data-ttu-id="a891e-173">記憶體回收最常在這個層代中進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-173">Garbage collection occurs most frequently in this generation.</span></span>

  <span data-ttu-id="a891e-174">新配置的物件會形成新一代的物件，而且是隱含的層代0集合。</span><span class="sxs-lookup"><span data-stu-id="a891e-174">Newly allocated objects form a new generation of objects and are implicitly generation 0 collections.</span></span> <span data-ttu-id="a891e-175">不過，如果它們是大型物件，則會在層代2回收中的大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="a891e-175">However, if they are large objects, they go on the large object heap in a generation 2 collection.</span></span>

  <span data-ttu-id="a891e-176">大部分物件都會在層代 0 的記憶體回收中回收，而且不會存留至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="a891e-176">Most objects are reclaimed for garbage collection in generation 0 and do not survive to the next generation.</span></span>

- <span data-ttu-id="a891e-177">**層代 1**。</span><span class="sxs-lookup"><span data-stu-id="a891e-177">**Generation 1**.</span></span> <span data-ttu-id="a891e-178">這個層代包含存留較短的物件，而且當做存留較短物件與存留較長物件之間的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a891e-178">This generation contains short-lived objects and serves as a buffer between short-lived objects and long-lived objects.</span></span>

- <span data-ttu-id="a891e-179">**層代 2**。</span><span class="sxs-lookup"><span data-stu-id="a891e-179">**Generation 2**.</span></span> <span data-ttu-id="a891e-180">這個層代包含存留較長的物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-180">This generation contains long-lived objects.</span></span> <span data-ttu-id="a891e-181">長時間存留物件的範例是伺服器應用程式中的物件，其中包含在進程期間即時的靜態資料。</span><span class="sxs-lookup"><span data-stu-id="a891e-181">An example of a long-lived object is an object in a server application that contains static data that's live for the duration of the process.</span></span>

<span data-ttu-id="a891e-182">當條件許可時，記憶體回收會針對特定層代進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-182">Garbage collections occur on specific generations as conditions warrant.</span></span> <span data-ttu-id="a891e-183">回收層代是指回收該層代中的物件及其所有較新的層代。</span><span class="sxs-lookup"><span data-stu-id="a891e-183">Collecting a generation means collecting objects in that generation and all its younger generations.</span></span> <span data-ttu-id="a891e-184">層代 2 記憶體回收也稱為完整記憶體回收，因為它會回收所有層代中的所有物件 (亦即，Managed 堆積中的所有物件)。</span><span class="sxs-lookup"><span data-stu-id="a891e-184">A generation 2 garbage collection is also known as a full garbage collection, because it reclaims all objects in all generations (that is, all objects in the managed heap).</span></span>

### <a name="survival-and-promotions"></a><span data-ttu-id="a891e-185">未回收和提升</span><span class="sxs-lookup"><span data-stu-id="a891e-185">Survival and promotions</span></span>

<span data-ttu-id="a891e-186">未在垃圾收集中回收的物件稱為「survivors」，並會升級為下一代。</span><span class="sxs-lookup"><span data-stu-id="a891e-186">Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation.</span></span> <span data-ttu-id="a891e-187">在層代 0 記憶體回收中未被回收的物件會提升至層代 1、在層代 1 記憶體回收中未被回收的物件會提升至層代 2，而在層代 2 記憶體回收中未被回收的物件則保留在層代 2 中。</span><span class="sxs-lookup"><span data-stu-id="a891e-187">Objects that survive a generation 0 garbage collection are promoted to generation 1; objects that survive a generation 1 garbage collection are promoted to generation 2; and objects that survive a generation 2 garbage collection remain in generation 2.</span></span>

<span data-ttu-id="a891e-188">當垃圾收集行程偵測到產生中的生存率很高時，它會增加該世代的配置臨界值。</span><span class="sxs-lookup"><span data-stu-id="a891e-188">When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation.</span></span> <span data-ttu-id="a891e-189">下一個集合會取得大量回收的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a891e-189">The next collection gets a substantial size of reclaimed memory.</span></span> <span data-ttu-id="a891e-190">CLR 會持續平衡兩個優先順序：不讓應用程式的工作集變得太大，因為會延遲垃圾收集，而不會讓垃圾收集的執行頻率太高。</span><span class="sxs-lookup"><span data-stu-id="a891e-190">The CLR continually balances two priorities: not letting an application's working set get too large by delaying garbage collection and not letting the garbage collection run too frequently.</span></span>

### <a name="ephemeral-generations-and-segments"></a><span data-ttu-id="a891e-191">暫時層代和區段</span><span class="sxs-lookup"><span data-stu-id="a891e-191">Ephemeral generations and segments</span></span>

<span data-ttu-id="a891e-192">因為層代 0 和 1 中的物件存留較短，所以這些層代稱為暫時層代。</span><span class="sxs-lookup"><span data-stu-id="a891e-192">Because objects in generations 0 and 1 are short-lived, these generations are known as the ephemeral generations.</span></span>

<span data-ttu-id="a891e-193">暫時層代必須配置於稱為暫時區段的記憶體區段中。</span><span class="sxs-lookup"><span data-stu-id="a891e-193">Ephemeral generations must be allocated in the memory segment that is known as the ephemeral segment.</span></span> <span data-ttu-id="a891e-194">記憶體回收行程所取得的每個新區段都會成為新的暫時區段，而且包含在層代 0 記憶體回收中未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-194">Each new segment acquired by the garbage collector becomes the new ephemeral segment and contains the objects that survived a generation 0 garbage collection.</span></span> <span data-ttu-id="a891e-195">舊的暫時區段會成為新的層代 2 區段。</span><span class="sxs-lookup"><span data-stu-id="a891e-195">The old ephemeral segment becomes the new generation 2 segment.</span></span>

<span data-ttu-id="a891e-196">暫時區段的大小會根據系統是32位還是64位，以及它正在執行的垃圾收集行程類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a891e-196">The size of the ephemeral segment varies depending on whether a system is 32-bit or 64-bit, and on the type of garbage collector it is running.</span></span> <span data-ttu-id="a891e-197">下表顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="a891e-197">Default values are shown in the following table.</span></span>

||<span data-ttu-id="a891e-198">32 位元</span><span class="sxs-lookup"><span data-stu-id="a891e-198">32-bit</span></span>|<span data-ttu-id="a891e-199">64 位元</span><span class="sxs-lookup"><span data-stu-id="a891e-199">64-bit</span></span>|
|-|-------------|-------------|
|<span data-ttu-id="a891e-200">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="a891e-200">Workstation GC</span></span>|<span data-ttu-id="a891e-201">16 MB</span><span class="sxs-lookup"><span data-stu-id="a891e-201">16 MB</span></span>|<span data-ttu-id="a891e-202">256 MB</span><span class="sxs-lookup"><span data-stu-id="a891e-202">256 MB</span></span>|
|<span data-ttu-id="a891e-203">伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="a891e-203">Server GC</span></span>|<span data-ttu-id="a891e-204">64 MB</span><span class="sxs-lookup"><span data-stu-id="a891e-204">64 MB</span></span>|<span data-ttu-id="a891e-205">4 GB</span><span class="sxs-lookup"><span data-stu-id="a891e-205">4 GB</span></span>|
|<span data-ttu-id="a891e-206">具有多於 4 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="a891e-206">Server GC with > 4 logical CPUs</span></span>|<span data-ttu-id="a891e-207">32 MB</span><span class="sxs-lookup"><span data-stu-id="a891e-207">32 MB</span></span>|<span data-ttu-id="a891e-208">2 GB</span><span class="sxs-lookup"><span data-stu-id="a891e-208">2 GB</span></span>|
|<span data-ttu-id="a891e-209">具有 > 8 個邏輯 CPU 的伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="a891e-209">Server GC with > 8 logical CPUs</span></span>|<span data-ttu-id="a891e-210">16 MB</span><span class="sxs-lookup"><span data-stu-id="a891e-210">16 MB</span></span>|<span data-ttu-id="a891e-211">1 GB</span><span class="sxs-lookup"><span data-stu-id="a891e-211">1 GB</span></span>|

<span data-ttu-id="a891e-212">暫時區段可能會包括層代 2 物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-212">The ephemeral segment can include generation 2 objects.</span></span> <span data-ttu-id="a891e-213">層代 2 物件可以使用多個區段 (取決於處理序所需而且記憶體允許的數目)。</span><span class="sxs-lookup"><span data-stu-id="a891e-213">Generation 2 objects can use multiple segments (as many as your process requires and memory allows for).</span></span>

<span data-ttu-id="a891e-214">暫時記憶體回收中釋放記憶體的數量會限制為暫時區段的大小。</span><span class="sxs-lookup"><span data-stu-id="a891e-214">The amount of freed memory from an ephemeral garbage collection is limited to the size of the ephemeral segment.</span></span> <span data-ttu-id="a891e-215">所釋放的記憶體數量會與無作用物件所佔據的空間成正比。</span><span class="sxs-lookup"><span data-stu-id="a891e-215">The amount of memory that is freed is proportional to the space that was occupied by the dead objects.</span></span>

## <a name="what-happens-during-a-garbage-collection"></a><span data-ttu-id="a891e-216">記憶體回收期間進行的作業</span><span class="sxs-lookup"><span data-stu-id="a891e-216">What happens during a garbage collection</span></span>

<span data-ttu-id="a891e-217">記憶體回收具有下列階段：</span><span class="sxs-lookup"><span data-stu-id="a891e-217">A garbage collection has the following phases:</span></span>

- <span data-ttu-id="a891e-218">標記階段：尋找和建立所有使用中物件的清單。</span><span class="sxs-lookup"><span data-stu-id="a891e-218">A marking phase that finds and creates a list of all live objects.</span></span>

- <span data-ttu-id="a891e-219">重新配置階段：更新即將壓縮之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="a891e-219">A relocating phase that updates the references to the objects that will be compacted.</span></span>

- <span data-ttu-id="a891e-220">壓縮階段：回收無作用物件所佔據的空間並壓縮未被回收的物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-220">A compacting phase that reclaims the space occupied by the dead objects and compacts the surviving objects.</span></span> <span data-ttu-id="a891e-221">壓縮階段會將記憶體回收中未被回收的物件移至區段的較舊端。</span><span class="sxs-lookup"><span data-stu-id="a891e-221">The compacting phase moves objects that have survived a garbage collection toward the older end of the segment.</span></span>

  <span data-ttu-id="a891e-222">因為層代 2 回收可能會佔據多個區段，所以提升至層代 2 的物件可能會移至較舊區段。</span><span class="sxs-lookup"><span data-stu-id="a891e-222">Because generation 2 collections can occupy multiple segments, objects that are promoted into generation 2 can be moved into an older segment.</span></span> <span data-ttu-id="a891e-223">層代 1 和層代 2 的未回收物件都可能會移至不同的區段，因為它們都會被提升至層代 2。</span><span class="sxs-lookup"><span data-stu-id="a891e-223">Both generation 1 and generation 2 survivors can be moved to a different segment, because they are promoted to generation 2.</span></span>

  <span data-ttu-id="a891e-224">一般來說，大型物件堆積（LOH）不會壓縮，因為複製大型物件會造成效能上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="a891e-224">Ordinarily, the large object heap (LOH) is not compacted, because copying large objects imposes a performance penalty.</span></span> <span data-ttu-id="a891e-225">不過，在 .NET Core 和 .NET Framework 4.5.1 和更新版本中，您可以使用 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> 屬性，視需要壓縮大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="a891e-225">However, in .NET Core and in .NET Framework 4.5.1 and later, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand.</span></span> <span data-ttu-id="a891e-226">此外，藉由指定下列任一項來設定固定限制時，會自動壓縮 LOH：</span><span class="sxs-lookup"><span data-stu-id="a891e-226">In addition, the LOH is automatically compacted when a hard limit is set by specifying either:</span></span>

  - <span data-ttu-id="a891e-227">容器上的記憶體限制，或</span><span class="sxs-lookup"><span data-stu-id="a891e-227">a memory limit on a container, or</span></span>
  - <span data-ttu-id="a891e-228">[GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit)或[GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="a891e-228">the [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) or [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) run-time configuration options</span></span>

<span data-ttu-id="a891e-229">記憶體回收行程會使用下列資訊來判斷物件是否使用中：</span><span class="sxs-lookup"><span data-stu-id="a891e-229">The garbage collector uses the following information to determine whether objects are live:</span></span>

- <span data-ttu-id="a891e-230">**堆疊根目錄**。</span><span class="sxs-lookup"><span data-stu-id="a891e-230">**Stack roots**.</span></span> <span data-ttu-id="a891e-231">Just-in-Time (JIT) 編譯器和堆疊查核器所提供的堆疊變數。</span><span class="sxs-lookup"><span data-stu-id="a891e-231">Stack variables provided by the just-in-time (JIT) compiler and stack walker.</span></span> <span data-ttu-id="a891e-232">JIT 優化可以延長或縮短在其中向垃圾收集行程報告堆疊變數的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="a891e-232">JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.</span></span>

- <span data-ttu-id="a891e-233">**記憶體回收控制代碼**。</span><span class="sxs-lookup"><span data-stu-id="a891e-233">**Garbage collection handles**.</span></span> <span data-ttu-id="a891e-234">會指向 Managed 物件，而且可由使用者程式碼或 Common Language Runtime 配置的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a891e-234">Handles that point to managed objects and that can be allocated by user code or by the common language runtime.</span></span>

- <span data-ttu-id="a891e-235">**靜態資料**。</span><span class="sxs-lookup"><span data-stu-id="a891e-235">**Static data**.</span></span> <span data-ttu-id="a891e-236">應用程式定義域中可能參考其他物件的靜態物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-236">Static objects in application domains that could be referencing other objects.</span></span> <span data-ttu-id="a891e-237">每個應用程式定義域都會追蹤其靜態物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-237">Each application domain keeps track of its static objects.</span></span>

<span data-ttu-id="a891e-238">記憶體回收開始之前，所有 Managed 執行緒都會暫停，但觸發記憶體回收的執行緒除外。</span><span class="sxs-lookup"><span data-stu-id="a891e-238">Before a garbage collection starts, all managed threads are suspended except for the thread that triggered the garbage collection.</span></span>

<span data-ttu-id="a891e-239">下圖顯示觸發記憶體回收且造成其他執行緒暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a891e-239">The following illustration shows a thread that triggers a garbage collection and causes the other threads to be suspended.</span></span>

![當執行緒觸發記憶體回收時](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a><span data-ttu-id="a891e-241">操作非受控資源</span><span class="sxs-lookup"><span data-stu-id="a891e-241">Manipulate unmanaged resources</span></span>

<span data-ttu-id="a891e-242">如果 managed 物件使用其原生檔案控制代碼來參考非受控物件，您就必須明確釋放非受控物件，因為垃圾收集行程只會追蹤 managed 堆積上的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a891e-242">If managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector only tracks memory on the managed heap.</span></span>

<span data-ttu-id="a891e-243">受管理物件的使用者可能不會處置物件所使用的原生資源。</span><span class="sxs-lookup"><span data-stu-id="a891e-243">Users of the managed object may not dispose the native resources used by the object.</span></span> <span data-ttu-id="a891e-244">若要執行清除，您可以讓 managed 物件成為可終結的。</span><span class="sxs-lookup"><span data-stu-id="a891e-244">To perform the cleanup, you can make the managed object finalizable.</span></span> <span data-ttu-id="a891e-245">「完成」是由不再使用物件時執行的清除動作所組成。</span><span class="sxs-lookup"><span data-stu-id="a891e-245">Finalization consists of cleanup actions that execute when the object is no longer in use.</span></span> <span data-ttu-id="a891e-246">當 managed 物件當時，它會執行其完成項方法中所指定的清除動作。</span><span class="sxs-lookup"><span data-stu-id="a891e-246">When the managed object dies, it performs cleanup actions that are specified in its finalizer method.</span></span>

<span data-ttu-id="a891e-247">當系統發現某個可最終處理物件無作用時，該物件的完成項就會放入佇列中，以便執行其清除動作，但是物件本身會提升至下一個層代。</span><span class="sxs-lookup"><span data-stu-id="a891e-247">When a finalizable object is discovered to be dead, its finalizer is put in a queue so that its cleanup actions are executed, but the object itself is promoted to the next generation.</span></span> <span data-ttu-id="a891e-248">因此，您必須等候直到在該層代上進行的下一次記憶體回收 (不一定是下一次記憶體回收)，以便判斷此物件是否已經回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-248">Therefore, you have to wait until the next garbage collection that occurs on that generation (which is not necessarily the next garbage collection) to determine whether the object has been reclaimed.</span></span>

<span data-ttu-id="a891e-249">如需最終結束的詳細資訊，請參閱 <xref:System.Object.Finalize?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a891e-249">For more information about finalization, see <xref:System.Object.Finalize?displayProperty=nameWithType>.</span></span>

## <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="a891e-250">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a891e-250">Workstation and server garbage collection</span></span>

<span data-ttu-id="a891e-251">記憶體回收行程會自行調整而且可在各種案例中運作。</span><span class="sxs-lookup"><span data-stu-id="a891e-251">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="a891e-252">您可以使用[設定檔設定](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)，根據工作負載的特性來設定垃圾收集的類型。</span><span class="sxs-lookup"><span data-stu-id="a891e-252">You can use a [configuration file setting](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) to set the type of garbage collection based on the characteristics of the workload.</span></span> <span data-ttu-id="a891e-253">CLR 會提供下列記憶體回收類型：</span><span class="sxs-lookup"><span data-stu-id="a891e-253">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="a891e-254">工作站垃圾收集（GC）是針對用戶端應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="a891e-254">Workstation garbage collection (GC) is designed for client apps.</span></span> <span data-ttu-id="a891e-255">這是獨立應用程式的預設 GC 類別。</span><span class="sxs-lookup"><span data-stu-id="a891e-255">It is the default GC flavor for standalone apps.</span></span> <span data-ttu-id="a891e-256">例如，針對裝載的應用程式（由 ASP.NET 所主控），主機會決定預設的 GC 類別。</span><span class="sxs-lookup"><span data-stu-id="a891e-256">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="a891e-257">工作站記憶體回收可能是並行或非並行的。</span><span class="sxs-lookup"><span data-stu-id="a891e-257">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="a891e-258">並行記憶體回收可讓 Managed 執行緒在記憶體回收期間繼續運作。</span><span class="sxs-lookup"><span data-stu-id="a891e-258">Concurrent garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="a891e-259">[背景垃圾收集](#background-workstation-garbage-collection)會取代 .NET Framework 4 和更新版本中的[並行垃圾收集](#concurrent-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="a891e-259">[Background garbage collection](#background-workstation-garbage-collection) replaces [concurrent garbage collection](#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="a891e-260">伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="a891e-260">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="a891e-261">在 .NET Core 中，伺服器垃圾收集可以是非並行或背景。</span><span class="sxs-lookup"><span data-stu-id="a891e-261">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="a891e-262">在 .NET Framework 4.5 和更新版本中，伺服器垃圾收集可以是非並行或背景（背景垃圾收集會取代並行垃圾收集）。</span><span class="sxs-lookup"><span data-stu-id="a891e-262">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background (background garbage collection replaces concurrent garbage collection).</span></span> <span data-ttu-id="a891e-263">在 .NET Framework 4 和舊版中，伺服器垃圾收集為非並行的。</span><span class="sxs-lookup"><span data-stu-id="a891e-263">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="a891e-264">下圖顯示在伺服器上執行垃圾收集的專用線程：</span><span class="sxs-lookup"><span data-stu-id="a891e-264">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![伺服器記憶體回收執行緒](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a><span data-ttu-id="a891e-266">比較工作站和伺服器垃圾收集</span><span class="sxs-lookup"><span data-stu-id="a891e-266">Compare workstation and server garbage collection</span></span>

<span data-ttu-id="a891e-267">以下是工作站記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="a891e-267">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="a891e-268">此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="a891e-268">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="a891e-269">因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="a891e-269">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="a891e-270">（執行機器碼的執行緒在伺服器或工作站垃圾收集上不會暫停）。</span><span class="sxs-lookup"><span data-stu-id="a891e-270">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="a891e-271">工作站垃圾收集一律會在只有一個處理器的電腦上使用，不論[設定](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)為何。</span><span class="sxs-lookup"><span data-stu-id="a891e-271">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

<span data-ttu-id="a891e-272">以下是伺服器記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="a891e-272">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="a891e-273">此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-273">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="a891e-274">執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-274">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="a891e-275">每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="a891e-275">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="a891e-276">不同堆積上的物件可以彼此參考。</span><span class="sxs-lookup"><span data-stu-id="a891e-276">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="a891e-277">因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。</span><span class="sxs-lookup"><span data-stu-id="a891e-277">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="a891e-278">伺服器記憶體回收通常具有較大的區段。</span><span class="sxs-lookup"><span data-stu-id="a891e-278">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="a891e-279">不過，這只是一般化：區段大小是特定執行，而且可能會變更。</span><span class="sxs-lookup"><span data-stu-id="a891e-279">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="a891e-280">請不要在調整應用程式時，假設垃圾收集行程所配置的區段大小。</span><span class="sxs-lookup"><span data-stu-id="a891e-280">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="a891e-281">伺服器記憶體回收可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="a891e-281">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="a891e-282">例如，假設有12個處理常式在具有4個處理器的電腦上執行伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="a891e-282">For example, imagine that there are 12 processes that use server GC running on a computer that has 4 processors.</span></span> <span data-ttu-id="a891e-283">如果所有處理常式都是同時收集垃圾，它們會互相干擾，因為同一個處理器上有12個執行緒排程。</span><span class="sxs-lookup"><span data-stu-id="a891e-283">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="a891e-284">如果處理常式是作用中的，最好不要讓它們全部使用伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="a891e-284">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="a891e-285">如果您執行的是數百個應用程式實例，請考慮使用已停用並行垃圾收集的工作站垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a891e-285">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="a891e-286">這樣會產生較少的內容切換，因此可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="a891e-286">This will result in less context switching, which can improve performance.</span></span>

## <a name="background-workstation-garbage-collection"></a><span data-ttu-id="a891e-287">背景工作站記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a891e-287">Background workstation garbage collection</span></span>

<span data-ttu-id="a891e-288">在背景工作站垃圾收集中，當層代2的收集正在進行時，會視需要收集暫時層代（0和1）。</span><span class="sxs-lookup"><span data-stu-id="a891e-288">In background workstation garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress.</span></span> <span data-ttu-id="a891e-289">背景工作站垃圾收集是在專用的執行緒上執行，而且只適用于層代2回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-289">Background workstation garbage collection is performed on a dedicated thread and applies only to generation 2 collections.</span></span>

<span data-ttu-id="a891e-290">背景垃圾收集預設為啟用，而且可以在 .NET Core 應用程式的 [.NET Framework apps][或 [system.string](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) ] 設定中，使用 [ [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ] 設定來啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="a891e-290">Background garbage collection is enabled by default and can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.</span></span>

> [!NOTE]
> <span data-ttu-id="a891e-291">背景垃圾收集會取代[並行垃圾收集](#concurrent-garbage-collection)，並在 .NET Framework 4 和更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="a891e-291">Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions.</span></span> <span data-ttu-id="a891e-292">在 .NET Framework 4 中，只有工作站垃圾收集才支援此功能。</span><span class="sxs-lookup"><span data-stu-id="a891e-292">In .NET Framework 4, it's supported only for workstation garbage collection.</span></span> <span data-ttu-id="a891e-293">從 .NET Framework 4.5 開始，背景垃圾收集適用于工作站和伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a891e-293">Starting with .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.</span></span>

<span data-ttu-id="a891e-294">背景記憶體回收期間，暫時層代的回收稱為前景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-294">A collection on ephemeral generations during background garbage collection is known as foreground garbage collection.</span></span> <span data-ttu-id="a891e-295">進行前景記憶體回收時，所有 Managed 執行緒都會暫停。</span><span class="sxs-lookup"><span data-stu-id="a891e-295">When foreground garbage collections occur, all managed threads are suspended.</span></span>

<span data-ttu-id="a891e-296">當背景垃圾收集正在進行中，而且您已在層代0中配置足夠的物件時，CLR 會執行層代0或第1代的前景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a891e-296">When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection.</span></span> <span data-ttu-id="a891e-297">專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。</span><span class="sxs-lookup"><span data-stu-id="a891e-297">The dedicated background garbage collection thread checks at frequent safe points to determine whether there is a request for foreground garbage collection.</span></span> <span data-ttu-id="a891e-298">如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-298">If there is, the background collection suspends itself so that foreground garbage collection can occur.</span></span> <span data-ttu-id="a891e-299">在前景記憶體回收完成之後，專屬的背景記憶體回收執行緒和使用者執行緒就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-299">After the foreground garbage collection is completed, the dedicated background garbage collection thread and user threads resume.</span></span>

<span data-ttu-id="a891e-300">背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。</span><span class="sxs-lookup"><span data-stu-id="a891e-300">Background garbage collection removes allocation restrictions imposed by concurrent garbage collection, because ephemeral garbage collections can occur during background garbage collection.</span></span> <span data-ttu-id="a891e-301">背景垃圾收集可以移除暫時層代中的無作用物件。</span><span class="sxs-lookup"><span data-stu-id="a891e-301">Background garbage collection can remove dead objects in ephemeral generations.</span></span> <span data-ttu-id="a891e-302">它也可以在層代1垃圾收集期間視需要擴充堆積。</span><span class="sxs-lookup"><span data-stu-id="a891e-302">It can also expand the heap if needed during a generation 1 garbage collection.</span></span>

<span data-ttu-id="a891e-303">下圖顯示在工作站上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="a891e-303">The following illustration shows background garbage collection performed on a separate dedicated thread on a workstation:</span></span>

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a><span data-ttu-id="a891e-305">背景伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a891e-305">Background server garbage collection</span></span>

<span data-ttu-id="a891e-306">從 .NET Framework 4.5 開始，背景伺服器垃圾收集是伺服器垃圾收集的預設模式。</span><span class="sxs-lookup"><span data-stu-id="a891e-306">Starting with .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.</span></span>

<span data-ttu-id="a891e-307">背景伺服器垃圾收集的功能類似于背景工作站垃圾收集（如上一節所述），但有幾項差異：</span><span class="sxs-lookup"><span data-stu-id="a891e-307">Background server garbage collection functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences:</span></span>

- <span data-ttu-id="a891e-308">背景工作站垃圾收集使用一個專用的背景垃圾收集執行緒，而背景伺服器垃圾收集則使用多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="a891e-308">Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads.</span></span> <span data-ttu-id="a891e-309">一般來說，每個邏輯處理器都有專用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a891e-309">Typically, there's a dedicated thread for each logical processor.</span></span>

- <span data-ttu-id="a891e-310">與工作站背景記憶體回收執行緒不同的是，這些執行緒不會逾時。</span><span class="sxs-lookup"><span data-stu-id="a891e-310">Unlike the workstation background garbage collection thread, these threads do not time out.</span></span>

<span data-ttu-id="a891e-311">下圖顯示在伺服器上另一個專用執行緒上執行的背景記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="a891e-311">The following illustration shows background garbage collection performed on a separate dedicated thread on a server:</span></span>

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a><span data-ttu-id="a891e-313">並行的記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a891e-313">Concurrent garbage collection</span></span>

> [!TIP]
> <span data-ttu-id="a891e-314">本節適用于：</span><span class="sxs-lookup"><span data-stu-id="a891e-314">This section applies to:</span></span>
>
> - <span data-ttu-id="a891e-315">適用于工作站垃圾收集的 .NET Framework 3.5 和更早版本</span><span class="sxs-lookup"><span data-stu-id="a891e-315">.NET Framework 3.5 and earlier for workstation garbage collection</span></span>
> - <span data-ttu-id="a891e-316">.NET Framework 4 和更早版本進行伺服器垃圾收集</span><span class="sxs-lookup"><span data-stu-id="a891e-316">.NET Framework 4 and earlier for server garbage collection</span></span>
>
> <span data-ttu-id="a891e-317">在較新版本中，會以[背景垃圾收集](#background-workstation-garbage-collection)取代並行的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a891e-317">Concurrent garbage is replaced by [background garbage collection](#background-workstation-garbage-collection) in later versions.</span></span>

<span data-ttu-id="a891e-318">在 [工作站] 或 [伺服器垃圾收集] 中，您可以[啟用並行垃圾收集](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)，讓執行緒可以與在集合大部分持續時間內執行垃圾收集的專用線程並存執行。</span><span class="sxs-lookup"><span data-stu-id="a891e-318">In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection.</span></span> <span data-ttu-id="a891e-319">這個選項只會影響層代 2 中的記憶體回收。層代 0 和 1 一律為非並行，因為它們的完成速度非常快。</span><span class="sxs-lookup"><span data-stu-id="a891e-319">This option affects only garbage collections in generation 2; generations 0 and 1 are always non-concurrent because they finish very fast.</span></span>

<span data-ttu-id="a891e-320">並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。</span><span class="sxs-lookup"><span data-stu-id="a891e-320">Concurrent garbage collection enables interactive applications to be more responsive by minimizing pauses for a collection.</span></span> <span data-ttu-id="a891e-321">當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a891e-321">Managed threads can continue to run most of the time while the concurrent garbage collection thread is running.</span></span> <span data-ttu-id="a891e-322">這會在記憶體回收進行時縮短暫停時間。</span><span class="sxs-lookup"><span data-stu-id="a891e-322">This results in shorter pauses while a garbage collection is occurring.</span></span>

<span data-ttu-id="a891e-323">並行記憶體回收會針對專屬執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="a891e-323">Concurrent garbage collection is performed on a dedicated thread.</span></span> <span data-ttu-id="a891e-324">根據預設，CLR 會執行工作站記憶體回收並啟用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-324">By default, the CLR runs workstation garbage collection with concurrent garbage collection enabled.</span></span> <span data-ttu-id="a891e-325">這種回收適用於單一處理器和多處理器電腦。</span><span class="sxs-lookup"><span data-stu-id="a891e-325">This is true for single-processor and multi-processor computers.</span></span>

<span data-ttu-id="a891e-326">下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a891e-326">The following illustration shows concurrent garbage collection performed on a separate dedicated thread.</span></span>

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a><span data-ttu-id="a891e-328">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a891e-328">See also</span></span>

- [<span data-ttu-id="a891e-329">GC 的設定選項</span><span class="sxs-lookup"><span data-stu-id="a891e-329">Configuration options for GC</span></span>](../../core/run-time-config/garbage-collector.md)
- [<span data-ttu-id="a891e-330">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a891e-330">Garbage collection</span></span>](index.md)
