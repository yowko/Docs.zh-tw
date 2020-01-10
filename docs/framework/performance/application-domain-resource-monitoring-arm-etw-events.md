---
title: 應用程式定義域資源監視 (ARM) ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716220"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="0cbde-102">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="0cbde-103">這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="0cbde-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="0cbde-104">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="0cbde-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="0cbde-105">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-105">ThreadCreated Event</span></span>

<span data-ttu-id="0cbde-106">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="0cbde-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="0cbde-107">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="0cbde-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="0cbde-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="0cbde-109">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0cbde-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="0cbde-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0cbde-110">Keyword for raising the event</span></span>|<span data-ttu-id="0cbde-111">Level</span><span class="sxs-lookup"><span data-stu-id="0cbde-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0cbde-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0cbde-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0cbde-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-113">Informational(4)</span></span>|
|<span data-ttu-id="0cbde-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0cbde-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0cbde-115">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-115">Informational(4)</span></span>|

<span data-ttu-id="0cbde-116">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0cbde-116">The following table shows the event information:</span></span>

|<span data-ttu-id="0cbde-117">Event</span><span class="sxs-lookup"><span data-stu-id="0cbde-117">Event</span></span>|<span data-ttu-id="0cbde-118">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0cbde-118">Event ID</span></span>|<span data-ttu-id="0cbde-119">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0cbde-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="0cbde-120">85</span><span class="sxs-lookup"><span data-stu-id="0cbde-120">85</span></span>|<span data-ttu-id="0cbde-121">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="0cbde-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="0cbde-122">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0cbde-122">The following table shows the event data:</span></span>

|<span data-ttu-id="0cbde-123">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0cbde-123">Field name</span></span>|<span data-ttu-id="0cbde-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cbde-124">Data type</span></span>|<span data-ttu-id="0cbde-125">描述</span><span class="sxs-lookup"><span data-stu-id="0cbde-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0cbde-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0cbde-126">ThreadID</span></span>|<span data-ttu-id="0cbde-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-127">win:UInt64</span></span>|<span data-ttu-id="0cbde-128">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0cbde-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="0cbde-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0cbde-129">AppDomainID</span></span>|<span data-ttu-id="0cbde-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-130">win:UInt64</span></span>|<span data-ttu-id="0cbde-131">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="0cbde-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="0cbde-132">旗標</span><span class="sxs-lookup"><span data-stu-id="0cbde-132">Flags</span></span>|<span data-ttu-id="0cbde-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0cbde-133">win:UInt32</span></span>|<span data-ttu-id="0cbde-134">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="0cbde-134">Thread creation flags.</span></span>|
|<span data-ttu-id="0cbde-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="0cbde-135">ManagedThreadIndex</span></span>|<span data-ttu-id="0cbde-136">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0cbde-136">win:UInt32</span></span>|<span data-ttu-id="0cbde-137">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="0cbde-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="0cbde-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="0cbde-138">OSThreadID</span></span>|<span data-ttu-id="0cbde-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0cbde-139">win:UInt32</span></span>|<span data-ttu-id="0cbde-140">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="0cbde-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="0cbde-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0cbde-141">ClrInstanceID</span></span>|<span data-ttu-id="0cbde-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0cbde-142">win:UInt16</span></span>|<span data-ttu-id="0cbde-143">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0cbde-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="0cbde-144">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="0cbde-145">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0cbde-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0cbde-146">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0cbde-146">Keyword for raising the event</span></span>|<span data-ttu-id="0cbde-147">Level</span><span class="sxs-lookup"><span data-stu-id="0cbde-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0cbde-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0cbde-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0cbde-149">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-149">Informational(4)</span></span>|

<span data-ttu-id="0cbde-150">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0cbde-150">The following table shows the event information:</span></span>

|<span data-ttu-id="0cbde-151">Event</span><span class="sxs-lookup"><span data-stu-id="0cbde-151">Event</span></span>|<span data-ttu-id="0cbde-152">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0cbde-152">Event ID</span></span>|<span data-ttu-id="0cbde-153">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0cbde-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="0cbde-154">83</span><span class="sxs-lookup"><span data-stu-id="0cbde-154">83</span></span>|<span data-ttu-id="0cbde-155">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="0cbde-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="0cbde-156">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0cbde-156">The following table shows the event data:</span></span>

|<span data-ttu-id="0cbde-157">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0cbde-157">Field name</span></span>|<span data-ttu-id="0cbde-158">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cbde-158">Data type</span></span>|<span data-ttu-id="0cbde-159">描述</span><span class="sxs-lookup"><span data-stu-id="0cbde-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0cbde-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0cbde-160">AppDomainID</span></span>|<span data-ttu-id="0cbde-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-161">win:UInt64</span></span>|<span data-ttu-id="0cbde-162">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="0cbde-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="0cbde-163">已配置</span><span class="sxs-lookup"><span data-stu-id="0cbde-163">Allocated</span></span>|<span data-ttu-id="0cbde-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-164">win:UInt64</span></span>|<span data-ttu-id="0cbde-165">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="0cbde-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="0cbde-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0cbde-166">ClrInstanceID</span></span>|<span data-ttu-id="0cbde-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0cbde-167">win:UInt16</span></span>|<span data-ttu-id="0cbde-168">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0cbde-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="0cbde-169">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="0cbde-170">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0cbde-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0cbde-171">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0cbde-171">Keyword for raising the event</span></span>|<span data-ttu-id="0cbde-172">Level</span><span class="sxs-lookup"><span data-stu-id="0cbde-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0cbde-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0cbde-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0cbde-174">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-174">Informational(4)</span></span>|

<span data-ttu-id="0cbde-175">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0cbde-175">The following table shows the event information:</span></span>

|<span data-ttu-id="0cbde-176">Event</span><span class="sxs-lookup"><span data-stu-id="0cbde-176">Event</span></span>|<span data-ttu-id="0cbde-177">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0cbde-177">Event ID</span></span>|<span data-ttu-id="0cbde-178">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0cbde-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="0cbde-179">84</span><span class="sxs-lookup"><span data-stu-id="0cbde-179">84</span></span>|<span data-ttu-id="0cbde-180">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="0cbde-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="0cbde-181">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0cbde-181">The following table shows the event data:</span></span>

|<span data-ttu-id="0cbde-182">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0cbde-182">Field name</span></span>|<span data-ttu-id="0cbde-183">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cbde-183">Data type</span></span>|<span data-ttu-id="0cbde-184">描述</span><span class="sxs-lookup"><span data-stu-id="0cbde-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0cbde-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0cbde-185">AppDomainID</span></span>|<span data-ttu-id="0cbde-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-186">win:UInt64</span></span>|<span data-ttu-id="0cbde-187">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="0cbde-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="0cbde-188">存活的</span><span class="sxs-lookup"><span data-stu-id="0cbde-188">Survived</span></span>|<span data-ttu-id="0cbde-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-189">win:UInt64</span></span>|<span data-ttu-id="0cbde-190">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="0cbde-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="0cbde-191">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="0cbde-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="0cbde-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="0cbde-192">ProcessSurvived</span></span>|<span data-ttu-id="0cbde-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-193">win:UInt64</span></span>|<span data-ttu-id="0cbde-194">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="0cbde-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="0cbde-195">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0cbde-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="0cbde-196">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0cbde-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="0cbde-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0cbde-197">ClrInstanceID</span></span>|<span data-ttu-id="0cbde-198">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0cbde-198">win:UInt16</span></span>|<span data-ttu-id="0cbde-199">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0cbde-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="0cbde-200">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="0cbde-201">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0cbde-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0cbde-202">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0cbde-202">Keyword for raising the event</span></span>|<span data-ttu-id="0cbde-203">Level</span><span class="sxs-lookup"><span data-stu-id="0cbde-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0cbde-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0cbde-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0cbde-205">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-205">Informational(4)</span></span>|
|<span data-ttu-id="0cbde-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0cbde-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0cbde-207">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-207">Informational(4)</span></span>|

<span data-ttu-id="0cbde-208">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0cbde-208">The following table shows the event information:</span></span>

|<span data-ttu-id="0cbde-209">Event</span><span class="sxs-lookup"><span data-stu-id="0cbde-209">Event</span></span>|<span data-ttu-id="0cbde-210">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0cbde-210">Event ID</span></span>|<span data-ttu-id="0cbde-211">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0cbde-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="0cbde-212">87</span><span class="sxs-lookup"><span data-stu-id="0cbde-212">87</span></span>|<span data-ttu-id="0cbde-213">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0cbde-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="0cbde-214">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0cbde-214">The following table shows the event data:</span></span>

|<span data-ttu-id="0cbde-215">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0cbde-215">Field name</span></span>|<span data-ttu-id="0cbde-216">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cbde-216">Data type</span></span>|<span data-ttu-id="0cbde-217">描述</span><span class="sxs-lookup"><span data-stu-id="0cbde-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0cbde-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0cbde-218">ThreadID</span></span>|<span data-ttu-id="0cbde-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-219">win:UInt64</span></span>|<span data-ttu-id="0cbde-220">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="0cbde-220">The thread identifier.</span></span>|
|<span data-ttu-id="0cbde-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0cbde-221">AppDomainID</span></span>|<span data-ttu-id="0cbde-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-222">win:UInt64</span></span>|<span data-ttu-id="0cbde-223">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="0cbde-223">The application domain identifier.</span></span>|
|<span data-ttu-id="0cbde-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0cbde-224">ClrInstanceID</span></span>|<span data-ttu-id="0cbde-225">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0cbde-225">win:UInt16</span></span>|<span data-ttu-id="0cbde-226">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0cbde-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="0cbde-227">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-227">ThreadTerminated Event</span></span>

<span data-ttu-id="0cbde-228">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0cbde-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0cbde-229">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0cbde-229">Keyword for raising the event</span></span>|<span data-ttu-id="0cbde-230">Level</span><span class="sxs-lookup"><span data-stu-id="0cbde-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0cbde-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0cbde-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0cbde-232">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-232">Informational(4)</span></span>|
|<span data-ttu-id="0cbde-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0cbde-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0cbde-234">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0cbde-234">Informational(4)</span></span>|

<span data-ttu-id="0cbde-235">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0cbde-235">The following table shows the event information:</span></span>

|<span data-ttu-id="0cbde-236">Event</span><span class="sxs-lookup"><span data-stu-id="0cbde-236">Event</span></span>|<span data-ttu-id="0cbde-237">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0cbde-237">Event ID</span></span>|<span data-ttu-id="0cbde-238">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0cbde-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="0cbde-239">86</span><span class="sxs-lookup"><span data-stu-id="0cbde-239">86</span></span>|<span data-ttu-id="0cbde-240">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="0cbde-240">A thread terminates.</span></span>|

<span data-ttu-id="0cbde-241">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0cbde-241">The following table shows the event data:</span></span>

|<span data-ttu-id="0cbde-242">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0cbde-242">Field name</span></span>|<span data-ttu-id="0cbde-243">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cbde-243">Data type</span></span>|<span data-ttu-id="0cbde-244">描述</span><span class="sxs-lookup"><span data-stu-id="0cbde-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0cbde-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0cbde-245">ThreadID</span></span>|<span data-ttu-id="0cbde-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-246">win:UInt64</span></span>|<span data-ttu-id="0cbde-247">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="0cbde-247">The thread identifier.</span></span>|
|<span data-ttu-id="0cbde-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0cbde-248">AppDomainID</span></span>|<span data-ttu-id="0cbde-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0cbde-249">win:UInt64</span></span>|<span data-ttu-id="0cbde-250">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="0cbde-250">The application domain identifier.</span></span>|
|<span data-ttu-id="0cbde-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0cbde-251">ClrInstanceID</span></span>|<span data-ttu-id="0cbde-252">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0cbde-252">win:UInt16</span></span>|<span data-ttu-id="0cbde-253">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0cbde-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0cbde-254">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cbde-254">See also</span></span>

- [<span data-ttu-id="0cbde-255">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0cbde-255">CLR ETW Events</span></span>](clr-etw-events.md)
