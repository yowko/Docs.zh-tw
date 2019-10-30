---
title: 應用程式定義域資源監視 (ARM) ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e1c2a38be6f2c15a118b35925570119b474f096
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040571"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="5f4ed-102">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="5f4ed-103">這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="5f4ed-104">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="5f4ed-105">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-105">ThreadCreated Event</span></span>

<span data-ttu-id="5f4ed-106">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="5f4ed-107">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="5f4ed-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5f4ed-109">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="5f4ed-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f4ed-110">Keyword for raising the event</span></span>|<span data-ttu-id="5f4ed-111">層級</span><span class="sxs-lookup"><span data-stu-id="5f4ed-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f4ed-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5f4ed-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-113">Informational(4)</span></span>|
|<span data-ttu-id="5f4ed-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5f4ed-115">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-115">Informational(4)</span></span>|

<span data-ttu-id="5f4ed-116">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-116">The following table shows the event information:</span></span>

|<span data-ttu-id="5f4ed-117">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-117">Event</span></span>|<span data-ttu-id="5f4ed-118">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-118">Event ID</span></span>|<span data-ttu-id="5f4ed-119">引發的時機</span><span class="sxs-lookup"><span data-stu-id="5f4ed-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="5f4ed-120">85</span><span class="sxs-lookup"><span data-stu-id="5f4ed-120">85</span></span>|<span data-ttu-id="5f4ed-121">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="5f4ed-122">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-122">The following table shows the event data:</span></span>

|<span data-ttu-id="5f4ed-123">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-123">Field name</span></span>|<span data-ttu-id="5f4ed-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f4ed-124">Data type</span></span>|<span data-ttu-id="5f4ed-125">描述</span><span class="sxs-lookup"><span data-stu-id="5f4ed-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f4ed-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-126">ThreadID</span></span>|<span data-ttu-id="5f4ed-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-127">win:UInt64</span></span>|<span data-ttu-id="5f4ed-128">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="5f4ed-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-129">AppDomainID</span></span>|<span data-ttu-id="5f4ed-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-130">win:UInt64</span></span>|<span data-ttu-id="5f4ed-131">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="5f4ed-132">旗標</span><span class="sxs-lookup"><span data-stu-id="5f4ed-132">Flags</span></span>|<span data-ttu-id="5f4ed-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f4ed-133">win:UInt32</span></span>|<span data-ttu-id="5f4ed-134">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-134">Thread creation flags.</span></span>|
|<span data-ttu-id="5f4ed-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="5f4ed-135">ManagedThreadIndex</span></span>|<span data-ttu-id="5f4ed-136">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f4ed-136">win:UInt32</span></span>|<span data-ttu-id="5f4ed-137">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="5f4ed-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-138">OSThreadID</span></span>|<span data-ttu-id="5f4ed-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f4ed-139">win:UInt32</span></span>|<span data-ttu-id="5f4ed-140">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="5f4ed-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-141">ClrInstanceID</span></span>|<span data-ttu-id="5f4ed-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f4ed-142">win:UInt16</span></span>|<span data-ttu-id="5f4ed-143">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="5f4ed-144">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="5f4ed-145">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f4ed-146">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f4ed-146">Keyword for raising the event</span></span>|<span data-ttu-id="5f4ed-147">層級</span><span class="sxs-lookup"><span data-stu-id="5f4ed-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f4ed-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5f4ed-149">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-149">Informational(4)</span></span>|

<span data-ttu-id="5f4ed-150">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-150">The following table shows the event information:</span></span>

|<span data-ttu-id="5f4ed-151">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-151">Event</span></span>|<span data-ttu-id="5f4ed-152">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-152">Event ID</span></span>|<span data-ttu-id="5f4ed-153">引發的時機</span><span class="sxs-lookup"><span data-stu-id="5f4ed-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="5f4ed-154">83</span><span class="sxs-lookup"><span data-stu-id="5f4ed-154">83</span></span>|<span data-ttu-id="5f4ed-155">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="5f4ed-156">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-156">The following table shows the event data:</span></span>

|<span data-ttu-id="5f4ed-157">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-157">Field name</span></span>|<span data-ttu-id="5f4ed-158">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f4ed-158">Data type</span></span>|<span data-ttu-id="5f4ed-159">描述</span><span class="sxs-lookup"><span data-stu-id="5f4ed-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f4ed-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-160">AppDomainID</span></span>|<span data-ttu-id="5f4ed-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-161">win:UInt64</span></span>|<span data-ttu-id="5f4ed-162">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="5f4ed-163">已配置</span><span class="sxs-lookup"><span data-stu-id="5f4ed-163">Allocated</span></span>|<span data-ttu-id="5f4ed-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-164">win:UInt64</span></span>|<span data-ttu-id="5f4ed-165">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="5f4ed-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-166">ClrInstanceID</span></span>|<span data-ttu-id="5f4ed-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f4ed-167">win:UInt16</span></span>|<span data-ttu-id="5f4ed-168">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="5f4ed-169">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="5f4ed-170">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f4ed-171">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f4ed-171">Keyword for raising the event</span></span>|<span data-ttu-id="5f4ed-172">層級</span><span class="sxs-lookup"><span data-stu-id="5f4ed-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f4ed-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5f4ed-174">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-174">Informational(4)</span></span>|

<span data-ttu-id="5f4ed-175">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-175">The following table shows the event information:</span></span>

|<span data-ttu-id="5f4ed-176">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-176">Event</span></span>|<span data-ttu-id="5f4ed-177">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-177">Event ID</span></span>|<span data-ttu-id="5f4ed-178">引發的時機</span><span class="sxs-lookup"><span data-stu-id="5f4ed-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="5f4ed-179">84</span><span class="sxs-lookup"><span data-stu-id="5f4ed-179">84</span></span>|<span data-ttu-id="5f4ed-180">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="5f4ed-181">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-181">The following table shows the event data:</span></span>

|<span data-ttu-id="5f4ed-182">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-182">Field name</span></span>|<span data-ttu-id="5f4ed-183">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f4ed-183">Data type</span></span>|<span data-ttu-id="5f4ed-184">描述</span><span class="sxs-lookup"><span data-stu-id="5f4ed-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f4ed-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-185">AppDomainID</span></span>|<span data-ttu-id="5f4ed-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-186">win:UInt64</span></span>|<span data-ttu-id="5f4ed-187">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="5f4ed-188">存活的</span><span class="sxs-lookup"><span data-stu-id="5f4ed-188">Survived</span></span>|<span data-ttu-id="5f4ed-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-189">win:UInt64</span></span>|<span data-ttu-id="5f4ed-190">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="5f4ed-191">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="5f4ed-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="5f4ed-192">ProcessSurvived</span></span>|<span data-ttu-id="5f4ed-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-193">win:UInt64</span></span>|<span data-ttu-id="5f4ed-194">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="5f4ed-195">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="5f4ed-196">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="5f4ed-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-197">ClrInstanceID</span></span>|<span data-ttu-id="5f4ed-198">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f4ed-198">win:UInt16</span></span>|<span data-ttu-id="5f4ed-199">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="5f4ed-200">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="5f4ed-201">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f4ed-202">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f4ed-202">Keyword for raising the event</span></span>|<span data-ttu-id="5f4ed-203">層級</span><span class="sxs-lookup"><span data-stu-id="5f4ed-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f4ed-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5f4ed-205">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-205">Informational(4)</span></span>|
|<span data-ttu-id="5f4ed-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5f4ed-207">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-207">Informational(4)</span></span>|

<span data-ttu-id="5f4ed-208">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-208">The following table shows the event information:</span></span>

|<span data-ttu-id="5f4ed-209">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-209">Event</span></span>|<span data-ttu-id="5f4ed-210">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-210">Event ID</span></span>|<span data-ttu-id="5f4ed-211">引發的時機</span><span class="sxs-lookup"><span data-stu-id="5f4ed-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="5f4ed-212">87</span><span class="sxs-lookup"><span data-stu-id="5f4ed-212">87</span></span>|<span data-ttu-id="5f4ed-213">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="5f4ed-214">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-214">The following table shows the event data:</span></span>

|<span data-ttu-id="5f4ed-215">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-215">Field name</span></span>|<span data-ttu-id="5f4ed-216">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f4ed-216">Data type</span></span>|<span data-ttu-id="5f4ed-217">描述</span><span class="sxs-lookup"><span data-stu-id="5f4ed-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f4ed-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-218">ThreadID</span></span>|<span data-ttu-id="5f4ed-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-219">win:UInt64</span></span>|<span data-ttu-id="5f4ed-220">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-220">The thread identifier.</span></span>|
|<span data-ttu-id="5f4ed-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-221">AppDomainID</span></span>|<span data-ttu-id="5f4ed-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-222">win:UInt64</span></span>|<span data-ttu-id="5f4ed-223">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-223">The application domain identifier.</span></span>|
|<span data-ttu-id="5f4ed-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-224">ClrInstanceID</span></span>|<span data-ttu-id="5f4ed-225">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f4ed-225">win:UInt16</span></span>|<span data-ttu-id="5f4ed-226">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="5f4ed-227">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-227">ThreadTerminated Event</span></span>

<span data-ttu-id="5f4ed-228">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f4ed-229">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f4ed-229">Keyword for raising the event</span></span>|<span data-ttu-id="5f4ed-230">層級</span><span class="sxs-lookup"><span data-stu-id="5f4ed-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f4ed-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="5f4ed-232">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-232">Informational(4)</span></span>|
|<span data-ttu-id="5f4ed-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5f4ed-234">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-234">Informational(4)</span></span>|

<span data-ttu-id="5f4ed-235">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-235">The following table shows the event information:</span></span>

|<span data-ttu-id="5f4ed-236">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-236">Event</span></span>|<span data-ttu-id="5f4ed-237">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-237">Event ID</span></span>|<span data-ttu-id="5f4ed-238">引發的時機</span><span class="sxs-lookup"><span data-stu-id="5f4ed-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="5f4ed-239">86</span><span class="sxs-lookup"><span data-stu-id="5f4ed-239">86</span></span>|<span data-ttu-id="5f4ed-240">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-240">A thread terminates.</span></span>|

<span data-ttu-id="5f4ed-241">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="5f4ed-241">The following table shows the event data:</span></span>

|<span data-ttu-id="5f4ed-242">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-242">Field name</span></span>|<span data-ttu-id="5f4ed-243">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f4ed-243">Data type</span></span>|<span data-ttu-id="5f4ed-244">描述</span><span class="sxs-lookup"><span data-stu-id="5f4ed-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f4ed-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-245">ThreadID</span></span>|<span data-ttu-id="5f4ed-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-246">win:UInt64</span></span>|<span data-ttu-id="5f4ed-247">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-247">The thread identifier.</span></span>|
|<span data-ttu-id="5f4ed-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-248">AppDomainID</span></span>|<span data-ttu-id="5f4ed-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f4ed-249">win:UInt64</span></span>|<span data-ttu-id="5f4ed-250">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-250">The application domain identifier.</span></span>|
|<span data-ttu-id="5f4ed-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f4ed-251">ClrInstanceID</span></span>|<span data-ttu-id="5f4ed-252">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f4ed-252">win:UInt16</span></span>|<span data-ttu-id="5f4ed-253">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5f4ed-254">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f4ed-254">See also</span></span>

- [<span data-ttu-id="5f4ed-255">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-255">CLR ETW Events</span></span>](clr-etw-events.md)
