---
title: ThreadPool 運行時間事件
description: 請參閱 .net 運行時間表程集區事件，以收集 .NET Core 中線程集區的相關診斷資訊。 執行緒集區事件是背景工作執行緒集區事件或 i/o 執行緒集區事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586661"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="185dc-104">.NET 運行時間表程集區事件</span><span class="sxs-lookup"><span data-stu-id="185dc-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="185dc-105">這些事件會收集 threadpool 中工作者和 i/o 執行緒的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="185dc-106">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="185dc-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="185dc-107">IOThreadCreate_V1 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="185dc-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-109">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-109">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-110">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-112">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-112">Informational (4)</span></span>|

 <span data-ttu-id="185dc-113">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-113">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-114">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-114">Event</span></span>|<span data-ttu-id="185dc-115">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-115">Event ID</span></span>|<span data-ttu-id="185dc-116">引發的時機</span><span class="sxs-lookup"><span data-stu-id="185dc-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="185dc-117">44</span><span class="sxs-lookup"><span data-stu-id="185dc-117">44</span></span>|<span data-ttu-id="185dc-118">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="185dc-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="185dc-119">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-119">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-120">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-120">Field name</span></span>|<span data-ttu-id="185dc-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-121">Data type</span></span>|<span data-ttu-id="185dc-122">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="185dc-123">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="185dc-124">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-125">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="185dc-126">IOThreadTerminate_V1 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="185dc-127">下表說明關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="185dc-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="185dc-128">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-128">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-129">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="185dc-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-131">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-131">Informational (4)</span></span>

 <span data-ttu-id="185dc-132">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-132">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-133">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-133">Event</span></span>|<span data-ttu-id="185dc-134">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-134">Event ID</span></span>|<span data-ttu-id="185dc-135">引發的時機</span><span class="sxs-lookup"><span data-stu-id="185dc-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="185dc-136">45</span><span class="sxs-lookup"><span data-stu-id="185dc-136">45</span></span>|<span data-ttu-id="185dc-137">執行緒集區中的 i/o 執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="185dc-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="185dc-138">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-138">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-139">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-139">Field name</span></span>|<span data-ttu-id="185dc-140">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-140">Data type</span></span>|<span data-ttu-id="185dc-141">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="185dc-142">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="185dc-143">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-144">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="185dc-145">IOThreadRetire_V1 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="185dc-146">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-147">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-147">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-148">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-150">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-150">Informational (4)</span></span>|

 <span data-ttu-id="185dc-151">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-151">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-152">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-152">Event</span></span>|<span data-ttu-id="185dc-153">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-153">Event ID</span></span>|<span data-ttu-id="185dc-154">引發的時機</span><span class="sxs-lookup"><span data-stu-id="185dc-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="185dc-155">46</span><span class="sxs-lookup"><span data-stu-id="185dc-155">46</span></span>|<span data-ttu-id="185dc-156">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="185dc-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="185dc-157">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-157">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-158">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-158">Field name</span></span>|<span data-ttu-id="185dc-159">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-159">Data type</span></span>|<span data-ttu-id="185dc-160">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="185dc-161">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="185dc-162">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-163">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="185dc-164">IOThreadUnretire_V1 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="185dc-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-166">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-167">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-169">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-169">Informational (4)</span></span>|

 <span data-ttu-id="185dc-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-170">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-171">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-171">Event</span></span>|<span data-ttu-id="185dc-172">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-172">Event ID</span></span>|<span data-ttu-id="185dc-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="185dc-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="185dc-174">47</span><span class="sxs-lookup"><span data-stu-id="185dc-174">47</span></span>|<span data-ttu-id="185dc-175">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="185dc-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="185dc-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-176">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-177">Field name</span></span>|<span data-ttu-id="185dc-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-178">Data type</span></span>|<span data-ttu-id="185dc-179">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="185dc-180">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="185dc-181">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="185dc-182">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="185dc-183">ThreadPoolWorkerThreadStart 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="185dc-184">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-184">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-185">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="185dc-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-187">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-187">Informational (4)</span></span>|

|<span data-ttu-id="185dc-188">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-188">Event</span></span>|<span data-ttu-id="185dc-189">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-189">Event ID</span></span>|<span data-ttu-id="185dc-190">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="185dc-191">50</span><span class="sxs-lookup"><span data-stu-id="185dc-191">50</span></span>|<span data-ttu-id="185dc-192">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="185dc-192">A worker thread is created.</span></span>|

|<span data-ttu-id="185dc-193">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-193">Field name</span></span>|<span data-ttu-id="185dc-194">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-194">Data type</span></span>|<span data-ttu-id="185dc-195">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-196">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-197">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-198">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="185dc-199">ThreadPoolWorkerThreadStop 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="185dc-200">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-200">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-201">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="185dc-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-203">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-203">Informational (4)</span></span>|

|<span data-ttu-id="185dc-204">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-204">Event</span></span>|<span data-ttu-id="185dc-205">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-205">Event ID</span></span>|<span data-ttu-id="185dc-206">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="185dc-207">51</span><span class="sxs-lookup"><span data-stu-id="185dc-207">51</span></span>|<span data-ttu-id="185dc-208">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="185dc-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="185dc-209">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-209">Field name</span></span>|<span data-ttu-id="185dc-210">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-210">Data type</span></span>|<span data-ttu-id="185dc-211">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-212">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-213">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-214">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="185dc-215">ThreadPoolWorkerThreadWait 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="185dc-216">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-216">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-217">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="185dc-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-219">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-219">Informational (4)</span></span>|

|<span data-ttu-id="185dc-220">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-220">Event</span></span>|<span data-ttu-id="185dc-221">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-221">Event ID</span></span>|<span data-ttu-id="185dc-222">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="185dc-223">57</span><span class="sxs-lookup"><span data-stu-id="185dc-223">57</span></span>|<span data-ttu-id="185dc-224">工作者執行緒開始等候工作。</span><span class="sxs-lookup"><span data-stu-id="185dc-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="185dc-225">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-225">Field name</span></span>|<span data-ttu-id="185dc-226">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-226">Data type</span></span>|<span data-ttu-id="185dc-227">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-228">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-229">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-230">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="185dc-231">ThreadPoolWorkerThreadRetirementStart 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="185dc-232">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-232">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-233">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="185dc-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-235">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-235">Informational (4)</span></span>|

|<span data-ttu-id="185dc-236">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-236">Event</span></span>|<span data-ttu-id="185dc-237">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-237">Event ID</span></span>|<span data-ttu-id="185dc-238">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="185dc-239">52</span><span class="sxs-lookup"><span data-stu-id="185dc-239">52</span></span>|<span data-ttu-id="185dc-240">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="185dc-240">A worker thread retires.</span></span>|

|<span data-ttu-id="185dc-241">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-241">Field name</span></span>|<span data-ttu-id="185dc-242">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-242">Data type</span></span>|<span data-ttu-id="185dc-243">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-244">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-245">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-246">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="185dc-247">ThreadPoolWorkerThreadRetirementStop 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="185dc-248">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-248">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-249">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="185dc-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-251">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-251">Informational (4)</span></span>|

|<span data-ttu-id="185dc-252">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-252">Event</span></span>|<span data-ttu-id="185dc-253">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-253">Event ID</span></span>|<span data-ttu-id="185dc-254">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="185dc-255">53</span><span class="sxs-lookup"><span data-stu-id="185dc-255">53</span></span>|<span data-ttu-id="185dc-256">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="185dc-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="185dc-257">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-257">Field name</span></span>|<span data-ttu-id="185dc-258">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-258">Data type</span></span>|<span data-ttu-id="185dc-259">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-260">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-261">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-262">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="185dc-263">ThreadPoolWorkerThreadAdjustmentSample 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="185dc-264">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-265">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-265">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-266">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-268">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-268">Informational (4)</span></span>|

 <span data-ttu-id="185dc-269">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-269">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-270">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-270">Event</span></span>|<span data-ttu-id="185dc-271">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-271">Event ID</span></span>|<span data-ttu-id="185dc-272">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="185dc-273">54</span><span class="sxs-lookup"><span data-stu-id="185dc-273">54</span></span>|<span data-ttu-id="185dc-274">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="185dc-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="185dc-275">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-275">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-276">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-276">Field name</span></span>|<span data-ttu-id="185dc-277">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-277">Data type</span></span>|<span data-ttu-id="185dc-278">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="185dc-279">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-280">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="185dc-281">ThreadPoolWorkerThreadAdjustmentAdjustment 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="185dc-282">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-283">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-283">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-284">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-286">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-286">Informational (4)</span></span>|

 <span data-ttu-id="185dc-287">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-287">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-288">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-288">Event</span></span>|<span data-ttu-id="185dc-289">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-289">Event ID</span></span>|<span data-ttu-id="185dc-290">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="185dc-291">55</span><span class="sxs-lookup"><span data-stu-id="185dc-291">55</span></span>|<span data-ttu-id="185dc-292">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="185dc-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="185dc-293">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-293">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-294">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-294">Field name</span></span>|<span data-ttu-id="185dc-295">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-295">Data type</span></span>|<span data-ttu-id="185dc-296">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="185dc-297">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="185dc-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="185dc-298">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="185dc-299">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="185dc-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="185dc-300">`0x0` 預熱.</span><span class="sxs-lookup"><span data-stu-id="185dc-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="185dc-301">`0x1` 初始化.</span><span class="sxs-lookup"><span data-stu-id="185dc-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="185dc-302">`0x2` -隨機移動。</span><span class="sxs-lookup"><span data-stu-id="185dc-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="185dc-303">`0x3` -上升移動。</span><span class="sxs-lookup"><span data-stu-id="185dc-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="185dc-304">`0x4` -變更點。</span><span class="sxs-lookup"><span data-stu-id="185dc-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="185dc-305">`0x5` 穩定化.</span><span class="sxs-lookup"><span data-stu-id="185dc-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="185dc-306">`0x6` 不足.</span><span class="sxs-lookup"><span data-stu-id="185dc-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="185dc-307">`0x7` -執行緒超時。</span><span class="sxs-lookup"><span data-stu-id="185dc-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-308">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="185dc-309">ThreadPoolWorkerThreadAdjustmentStats 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="185dc-310">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-311">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-311">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-312">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-314">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-314">Verbose (5)</span></span>

 <span data-ttu-id="185dc-315">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-315">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-316">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-316">Event</span></span>|<span data-ttu-id="185dc-317">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-317">Event ID</span></span>|<span data-ttu-id="185dc-318">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="185dc-319">56</span><span class="sxs-lookup"><span data-stu-id="185dc-319">56</span></span>|<span data-ttu-id="185dc-320">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="185dc-321">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-321">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-322">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-322">Field name</span></span>|<span data-ttu-id="185dc-323">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-323">Data type</span></span>|<span data-ttu-id="185dc-324">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="185dc-325">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="185dc-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="185dc-326">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="185dc-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="185dc-327">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="185dc-328">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="185dc-329">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="185dc-330">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="185dc-331">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="185dc-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="185dc-332">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="185dc-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="185dc-333">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="185dc-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="185dc-334">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="185dc-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-335">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="185dc-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="185dc-336">ThreadPoolEnqueue 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="185dc-337">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-338">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-338">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-339">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-341">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-341">Verbose (5)</span></span>

 <span data-ttu-id="185dc-342">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-342">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-343">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-343">Event</span></span>|<span data-ttu-id="185dc-344">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-344">Event ID</span></span>|<span data-ttu-id="185dc-345">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="185dc-346">61</span><span class="sxs-lookup"><span data-stu-id="185dc-346">61</span></span>|<span data-ttu-id="185dc-347">工作專案已排入執行緒集區佇列中。</span><span class="sxs-lookup"><span data-stu-id="185dc-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="185dc-348">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-348">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-349">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-349">Field name</span></span>|<span data-ttu-id="185dc-350">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-350">Data type</span></span>|<span data-ttu-id="185dc-351">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="185dc-352">工作要求的指標。</span><span class="sxs-lookup"><span data-stu-id="185dc-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-353">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="185dc-354">ThreadPoolDequeue 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="185dc-355">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-356">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-356">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-357">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-359">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-359">Verbose (5)</span></span>

 <span data-ttu-id="185dc-360">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-360">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-361">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-361">Event</span></span>|<span data-ttu-id="185dc-362">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-362">Event ID</span></span>|<span data-ttu-id="185dc-363">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="185dc-364">62</span><span class="sxs-lookup"><span data-stu-id="185dc-364">62</span></span>|<span data-ttu-id="185dc-365">工作專案已從執行緒集區佇列中清除。</span><span class="sxs-lookup"><span data-stu-id="185dc-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="185dc-366">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-366">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-367">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-367">Field name</span></span>|<span data-ttu-id="185dc-368">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-368">Data type</span></span>|<span data-ttu-id="185dc-369">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="185dc-370">工作要求的指標。</span><span class="sxs-lookup"><span data-stu-id="185dc-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-371">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="185dc-372">ThreadPoolIOEnqueue 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="185dc-373">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-374">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-374">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-375">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-377">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-377">Verbose (5)</span></span>

 <span data-ttu-id="185dc-378">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-378">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-379">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-379">Event</span></span>|<span data-ttu-id="185dc-380">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-380">Event ID</span></span>|<span data-ttu-id="185dc-381">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="185dc-382">63</span><span class="sxs-lookup"><span data-stu-id="185dc-382">63</span></span>|<span data-ttu-id="185dc-383">在非同步 IO 完成之後，執行緒會將 IO 完成通知。</span><span class="sxs-lookup"><span data-stu-id="185dc-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="185dc-384">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-384">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-385">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-385">Field name</span></span>|<span data-ttu-id="185dc-386">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-386">Data type</span></span>|<span data-ttu-id="185dc-387">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="185dc-388">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="185dc-389">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="185dc-390">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-391">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="185dc-392">ThreadPoolIODequeue 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="185dc-393">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-394">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-394">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-395">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-397">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-397">Verbose (5)</span></span>

 <span data-ttu-id="185dc-398">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-398">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-399">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-399">Event</span></span>|<span data-ttu-id="185dc-400">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-400">Event ID</span></span>|<span data-ttu-id="185dc-401">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="185dc-402">64</span><span class="sxs-lookup"><span data-stu-id="185dc-402">64</span></span>|<span data-ttu-id="185dc-403">清除 IO 完成通知的執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="185dc-404">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-404">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-405">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-405">Field name</span></span>|<span data-ttu-id="185dc-406">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-406">Data type</span></span>|<span data-ttu-id="185dc-407">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="185dc-408">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="185dc-409">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="185dc-410">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-411">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="185dc-412">ThreadPoolIOPack 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="185dc-413">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="185dc-414">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-414">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-415">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-417">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="185dc-417">Verbose (5)</span></span>|

 <span data-ttu-id="185dc-418">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-418">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-419">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-419">Event</span></span>|<span data-ttu-id="185dc-420">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-420">Event ID</span></span>|<span data-ttu-id="185dc-421">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="185dc-422">65</span><span class="sxs-lookup"><span data-stu-id="185dc-422">65</span></span>|<span data-ttu-id="185dc-423">呼叫 ThreadPool 重迭 IO 套件。</span><span class="sxs-lookup"><span data-stu-id="185dc-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="185dc-424">下表顯示事件資料</span><span class="sxs-lookup"><span data-stu-id="185dc-424">The following table shows the event data</span></span>

|<span data-ttu-id="185dc-425">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-425">Field name</span></span>|<span data-ttu-id="185dc-426">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-426">Data type</span></span>|<span data-ttu-id="185dc-427">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="185dc-428">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="185dc-429">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="185dc-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-430">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="185dc-431">ThreadCreating 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-431">ThreadCreating event</span></span>

 <span data-ttu-id="185dc-432">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="185dc-433">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-433">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-434">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-436">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-436">Informational (4)</span></span>|

 <span data-ttu-id="185dc-437">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-437">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-438">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-438">Event</span></span>|<span data-ttu-id="185dc-439">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-439">Event ID</span></span>|<span data-ttu-id="185dc-440">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="185dc-441">70</span><span class="sxs-lookup"><span data-stu-id="185dc-441">70</span></span>|<span data-ttu-id="185dc-442">已建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="185dc-442">Thread has been created.</span></span>|

 <span data-ttu-id="185dc-443">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-443">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-444">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-444">Field name</span></span>|<span data-ttu-id="185dc-445">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-445">Data type</span></span>|<span data-ttu-id="185dc-446">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="185dc-447">執行緒識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-448">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="185dc-449">ThreadRunning 事件</span><span class="sxs-lookup"><span data-stu-id="185dc-449">ThreadRunning event</span></span>

 <span data-ttu-id="185dc-450">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="185dc-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="185dc-451">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="185dc-451">Keyword for raising the event</span></span>|<span data-ttu-id="185dc-452">層級</span><span class="sxs-lookup"><span data-stu-id="185dc-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="185dc-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="185dc-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="185dc-454">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="185dc-454">Informational (4)</span></span>|

 <span data-ttu-id="185dc-455">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="185dc-455">The following table shows the event information.</span></span>

|<span data-ttu-id="185dc-456">事件</span><span class="sxs-lookup"><span data-stu-id="185dc-456">Event</span></span>|<span data-ttu-id="185dc-457">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-457">Event ID</span></span>|<span data-ttu-id="185dc-458">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="185dc-459">71</span><span class="sxs-lookup"><span data-stu-id="185dc-459">71</span></span>|<span data-ttu-id="185dc-460">執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="185dc-460">Thread has started running.</span></span>|

 <span data-ttu-id="185dc-461">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="185dc-461">The following table shows the event data.</span></span>

|<span data-ttu-id="185dc-462">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="185dc-462">Field name</span></span>|<span data-ttu-id="185dc-463">資料類型</span><span class="sxs-lookup"><span data-stu-id="185dc-463">Data type</span></span>|<span data-ttu-id="185dc-464">描述</span><span class="sxs-lookup"><span data-stu-id="185dc-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="185dc-465">執行緒識別碼</span><span class="sxs-lookup"><span data-stu-id="185dc-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="185dc-466">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="185dc-466">Unique ID for the instance of CoreCLR.</span></span>|
