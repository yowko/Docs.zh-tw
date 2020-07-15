---
title: 應用程式定義域資源監視 (ARM) ETW 事件
description: 閱讀 .NET 中應用程式域資源監視（ARM） ETW 事件的相關資訊，例如 ThreadCreated、AppDomainMemAllocated、AppDomainMemSurvived 等等。
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309777"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="c01d7-103">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="c01d7-104">這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="c01d7-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="c01d7-105">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="c01d7-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="c01d7-106">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-106">ThreadCreated Event</span></span>

<span data-ttu-id="c01d7-107">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="c01d7-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="c01d7-108">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="c01d7-109">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="c01d7-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="c01d7-110">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d7-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="c01d7-111">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c01d7-111">Keyword for raising the event</span></span>|<span data-ttu-id="c01d7-112">層級</span><span class="sxs-lookup"><span data-stu-id="c01d7-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c01d7-113">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c01d7-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c01d7-114">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-114">Informational(4)</span></span>|
|<span data-ttu-id="c01d7-115">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c01d7-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c01d7-116">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-116">Informational(4)</span></span>|

<span data-ttu-id="c01d7-117">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="c01d7-117">The following table shows the event information:</span></span>

|<span data-ttu-id="c01d7-118">事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-118">Event</span></span>|<span data-ttu-id="c01d7-119">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c01d7-119">Event ID</span></span>|<span data-ttu-id="c01d7-120">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c01d7-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="c01d7-121">85</span><span class="sxs-lookup"><span data-stu-id="c01d7-121">85</span></span>|<span data-ttu-id="c01d7-122">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="c01d7-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="c01d7-123">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="c01d7-123">The following table shows the event data:</span></span>

|<span data-ttu-id="c01d7-124">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c01d7-124">Field name</span></span>|<span data-ttu-id="c01d7-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="c01d7-125">Data type</span></span>|<span data-ttu-id="c01d7-126">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c01d7-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c01d7-127">ThreadID</span></span>|<span data-ttu-id="c01d7-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-128">win:UInt64</span></span>|<span data-ttu-id="c01d7-129">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c01d7-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="c01d7-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c01d7-130">AppDomainID</span></span>|<span data-ttu-id="c01d7-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-131">win:UInt64</span></span>|<span data-ttu-id="c01d7-132">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="c01d7-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="c01d7-133">Flags</span><span class="sxs-lookup"><span data-stu-id="c01d7-133">Flags</span></span>|<span data-ttu-id="c01d7-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c01d7-134">win:UInt32</span></span>|<span data-ttu-id="c01d7-135">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="c01d7-135">Thread creation flags.</span></span>|
|<span data-ttu-id="c01d7-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="c01d7-136">ManagedThreadIndex</span></span>|<span data-ttu-id="c01d7-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c01d7-137">win:UInt32</span></span>|<span data-ttu-id="c01d7-138">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="c01d7-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="c01d7-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="c01d7-139">OSThreadID</span></span>|<span data-ttu-id="c01d7-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c01d7-140">win:UInt32</span></span>|<span data-ttu-id="c01d7-141">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="c01d7-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="c01d7-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c01d7-142">ClrInstanceID</span></span>|<span data-ttu-id="c01d7-143">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c01d7-143">win:UInt16</span></span>|<span data-ttu-id="c01d7-144">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c01d7-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="c01d7-145">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="c01d7-146">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="c01d7-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c01d7-147">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c01d7-147">Keyword for raising the event</span></span>|<span data-ttu-id="c01d7-148">層級</span><span class="sxs-lookup"><span data-stu-id="c01d7-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c01d7-149">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c01d7-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c01d7-150">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-150">Informational(4)</span></span>|

<span data-ttu-id="c01d7-151">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="c01d7-151">The following table shows the event information:</span></span>

|<span data-ttu-id="c01d7-152">事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-152">Event</span></span>|<span data-ttu-id="c01d7-153">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c01d7-153">Event ID</span></span>|<span data-ttu-id="c01d7-154">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c01d7-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="c01d7-155">83</span><span class="sxs-lookup"><span data-stu-id="c01d7-155">83</span></span>|<span data-ttu-id="c01d7-156">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="c01d7-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="c01d7-157">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="c01d7-157">The following table shows the event data:</span></span>

|<span data-ttu-id="c01d7-158">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c01d7-158">Field name</span></span>|<span data-ttu-id="c01d7-159">資料類型</span><span class="sxs-lookup"><span data-stu-id="c01d7-159">Data type</span></span>|<span data-ttu-id="c01d7-160">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c01d7-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c01d7-161">AppDomainID</span></span>|<span data-ttu-id="c01d7-162">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-162">win:UInt64</span></span>|<span data-ttu-id="c01d7-163">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="c01d7-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="c01d7-164">已配置</span><span class="sxs-lookup"><span data-stu-id="c01d7-164">Allocated</span></span>|<span data-ttu-id="c01d7-165">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-165">win:UInt64</span></span>|<span data-ttu-id="c01d7-166">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="c01d7-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="c01d7-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c01d7-167">ClrInstanceID</span></span>|<span data-ttu-id="c01d7-168">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c01d7-168">win:UInt16</span></span>|<span data-ttu-id="c01d7-169">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c01d7-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="c01d7-170">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="c01d7-171">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="c01d7-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c01d7-172">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c01d7-172">Keyword for raising the event</span></span>|<span data-ttu-id="c01d7-173">層級</span><span class="sxs-lookup"><span data-stu-id="c01d7-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c01d7-174">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c01d7-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c01d7-175">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-175">Informational(4)</span></span>|

<span data-ttu-id="c01d7-176">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="c01d7-176">The following table shows the event information:</span></span>

|<span data-ttu-id="c01d7-177">事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-177">Event</span></span>|<span data-ttu-id="c01d7-178">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c01d7-178">Event ID</span></span>|<span data-ttu-id="c01d7-179">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c01d7-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="c01d7-180">84</span><span class="sxs-lookup"><span data-stu-id="c01d7-180">84</span></span>|<span data-ttu-id="c01d7-181">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="c01d7-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="c01d7-182">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="c01d7-182">The following table shows the event data:</span></span>

|<span data-ttu-id="c01d7-183">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c01d7-183">Field name</span></span>|<span data-ttu-id="c01d7-184">資料類型</span><span class="sxs-lookup"><span data-stu-id="c01d7-184">Data type</span></span>|<span data-ttu-id="c01d7-185">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c01d7-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c01d7-186">AppDomainID</span></span>|<span data-ttu-id="c01d7-187">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-187">win:UInt64</span></span>|<span data-ttu-id="c01d7-188">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="c01d7-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="c01d7-189">存活的</span><span class="sxs-lookup"><span data-stu-id="c01d7-189">Survived</span></span>|<span data-ttu-id="c01d7-190">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-190">win:UInt64</span></span>|<span data-ttu-id="c01d7-191">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="c01d7-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="c01d7-192">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="c01d7-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="c01d7-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="c01d7-193">ProcessSurvived</span></span>|<span data-ttu-id="c01d7-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-194">win:UInt64</span></span>|<span data-ttu-id="c01d7-195">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="c01d7-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="c01d7-196">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c01d7-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="c01d7-197">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c01d7-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="c01d7-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c01d7-198">ClrInstanceID</span></span>|<span data-ttu-id="c01d7-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c01d7-199">win:UInt16</span></span>|<span data-ttu-id="c01d7-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c01d7-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="c01d7-201">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="c01d7-202">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="c01d7-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c01d7-203">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c01d7-203">Keyword for raising the event</span></span>|<span data-ttu-id="c01d7-204">層級</span><span class="sxs-lookup"><span data-stu-id="c01d7-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c01d7-205">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c01d7-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c01d7-206">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-206">Informational(4)</span></span>|
|<span data-ttu-id="c01d7-207">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c01d7-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c01d7-208">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-208">Informational(4)</span></span>|

<span data-ttu-id="c01d7-209">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="c01d7-209">The following table shows the event information:</span></span>

|<span data-ttu-id="c01d7-210">事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-210">Event</span></span>|<span data-ttu-id="c01d7-211">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c01d7-211">Event ID</span></span>|<span data-ttu-id="c01d7-212">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c01d7-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="c01d7-213">87</span><span class="sxs-lookup"><span data-stu-id="c01d7-213">87</span></span>|<span data-ttu-id="c01d7-214">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c01d7-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="c01d7-215">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="c01d7-215">The following table shows the event data:</span></span>

|<span data-ttu-id="c01d7-216">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c01d7-216">Field name</span></span>|<span data-ttu-id="c01d7-217">資料類型</span><span class="sxs-lookup"><span data-stu-id="c01d7-217">Data type</span></span>|<span data-ttu-id="c01d7-218">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c01d7-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c01d7-219">ThreadID</span></span>|<span data-ttu-id="c01d7-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-220">win:UInt64</span></span>|<span data-ttu-id="c01d7-221">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="c01d7-221">The thread identifier.</span></span>|
|<span data-ttu-id="c01d7-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c01d7-222">AppDomainID</span></span>|<span data-ttu-id="c01d7-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-223">win:UInt64</span></span>|<span data-ttu-id="c01d7-224">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="c01d7-224">The application domain identifier.</span></span>|
|<span data-ttu-id="c01d7-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c01d7-225">ClrInstanceID</span></span>|<span data-ttu-id="c01d7-226">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c01d7-226">win:UInt16</span></span>|<span data-ttu-id="c01d7-227">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c01d7-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="c01d7-228">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-228">ThreadTerminated Event</span></span>

<span data-ttu-id="c01d7-229">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="c01d7-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c01d7-230">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c01d7-230">Keyword for raising the event</span></span>|<span data-ttu-id="c01d7-231">層級</span><span class="sxs-lookup"><span data-stu-id="c01d7-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c01d7-232">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c01d7-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c01d7-233">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-233">Informational(4)</span></span>|
|<span data-ttu-id="c01d7-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c01d7-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c01d7-235">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c01d7-235">Informational(4)</span></span>|

<span data-ttu-id="c01d7-236">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="c01d7-236">The following table shows the event information:</span></span>

|<span data-ttu-id="c01d7-237">事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-237">Event</span></span>|<span data-ttu-id="c01d7-238">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c01d7-238">Event ID</span></span>|<span data-ttu-id="c01d7-239">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c01d7-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="c01d7-240">86</span><span class="sxs-lookup"><span data-stu-id="c01d7-240">86</span></span>|<span data-ttu-id="c01d7-241">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="c01d7-241">A thread terminates.</span></span>|

<span data-ttu-id="c01d7-242">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="c01d7-242">The following table shows the event data:</span></span>

|<span data-ttu-id="c01d7-243">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c01d7-243">Field name</span></span>|<span data-ttu-id="c01d7-244">資料類型</span><span class="sxs-lookup"><span data-stu-id="c01d7-244">Data type</span></span>|<span data-ttu-id="c01d7-245">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c01d7-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c01d7-246">ThreadID</span></span>|<span data-ttu-id="c01d7-247">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-247">win:UInt64</span></span>|<span data-ttu-id="c01d7-248">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="c01d7-248">The thread identifier.</span></span>|
|<span data-ttu-id="c01d7-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c01d7-249">AppDomainID</span></span>|<span data-ttu-id="c01d7-250">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c01d7-250">win:UInt64</span></span>|<span data-ttu-id="c01d7-251">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="c01d7-251">The application domain identifier.</span></span>|
|<span data-ttu-id="c01d7-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c01d7-252">ClrInstanceID</span></span>|<span data-ttu-id="c01d7-253">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c01d7-253">win:UInt16</span></span>|<span data-ttu-id="c01d7-254">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c01d7-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c01d7-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01d7-255">See also</span></span>

- [<span data-ttu-id="c01d7-256">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="c01d7-256">CLR ETW Events</span></span>](clr-etw-events.md)
