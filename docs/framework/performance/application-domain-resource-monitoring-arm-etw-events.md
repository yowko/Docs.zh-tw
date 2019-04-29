---
title: 應用程式定義域資源監視 (ARM) ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788059"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="f3041-102">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f3041-103">這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="f3041-104">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="f3041-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="f3041-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="f3041-106">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="f3041-107">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="f3041-108">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="f3041-109">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="f3041-110">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="f3041-111">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="f3041-112">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="f3041-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="f3041-113">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="f3041-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="f3041-114">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f3041-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="f3041-115">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="f3041-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f3041-116">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3041-116">Keyword for raising the event</span></span>|<span data-ttu-id="f3041-117">層級</span><span class="sxs-lookup"><span data-stu-id="f3041-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3041-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f3041-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f3041-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-119">Informational(4)</span></span>|  
|<span data-ttu-id="f3041-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f3041-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f3041-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="f3041-122">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3041-123">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-123">Event</span></span>|<span data-ttu-id="f3041-124">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3041-124">Event ID</span></span>|<span data-ttu-id="f3041-125">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f3041-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="f3041-126">85</span><span class="sxs-lookup"><span data-stu-id="f3041-126">85</span></span>|<span data-ttu-id="f3041-127">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3041-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="f3041-128">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f3041-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f3041-129">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f3041-129">Field name</span></span>|<span data-ttu-id="f3041-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="f3041-130">Data type</span></span>|<span data-ttu-id="f3041-131">描述</span><span class="sxs-lookup"><span data-stu-id="f3041-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3041-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f3041-132">ThreadID</span></span>|<span data-ttu-id="f3041-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-133">win:UInt64</span></span>|<span data-ttu-id="f3041-134">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3041-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="f3041-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f3041-135">AppDomainID</span></span>|<span data-ttu-id="f3041-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-136">win:UInt64</span></span>|<span data-ttu-id="f3041-137">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="f3041-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="f3041-138">旗標</span><span class="sxs-lookup"><span data-stu-id="f3041-138">Flags</span></span>|<span data-ttu-id="f3041-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f3041-139">win:UInt32</span></span>|<span data-ttu-id="f3041-140">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="f3041-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="f3041-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="f3041-141">ManagedThreadIndex</span></span>|<span data-ttu-id="f3041-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f3041-142">win:UInt32</span></span>|<span data-ttu-id="f3041-143">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="f3041-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="f3041-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="f3041-144">OSThreadID</span></span>|<span data-ttu-id="f3041-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f3041-145">win:UInt32</span></span>|<span data-ttu-id="f3041-146">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3041-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="f3041-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3041-147">ClrInstanceID</span></span>|<span data-ttu-id="f3041-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f3041-148">win:UInt16</span></span>|<span data-ttu-id="f3041-149">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f3041-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f3041-150">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f3041-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="f3041-151">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="f3041-152">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f3041-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f3041-153">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3041-153">Keyword for raising the event</span></span>|<span data-ttu-id="f3041-154">層級</span><span class="sxs-lookup"><span data-stu-id="f3041-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3041-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f3041-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f3041-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="f3041-157">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3041-158">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-158">Event</span></span>|<span data-ttu-id="f3041-159">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3041-159">Event ID</span></span>|<span data-ttu-id="f3041-160">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f3041-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="f3041-161">83</span><span class="sxs-lookup"><span data-stu-id="f3041-161">83</span></span>|<span data-ttu-id="f3041-162">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="f3041-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="f3041-163">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f3041-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f3041-164">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f3041-164">Field name</span></span>|<span data-ttu-id="f3041-165">資料類型</span><span class="sxs-lookup"><span data-stu-id="f3041-165">Data type</span></span>|<span data-ttu-id="f3041-166">描述</span><span class="sxs-lookup"><span data-stu-id="f3041-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3041-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f3041-167">AppDomainID</span></span>|<span data-ttu-id="f3041-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-168">win:UInt64</span></span>|<span data-ttu-id="f3041-169">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="f3041-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="f3041-170">已配置</span><span class="sxs-lookup"><span data-stu-id="f3041-170">Allocated</span></span>|<span data-ttu-id="f3041-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-171">win:UInt64</span></span>|<span data-ttu-id="f3041-172">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="f3041-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="f3041-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3041-173">ClrInstanceID</span></span>|<span data-ttu-id="f3041-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f3041-174">win:UInt16</span></span>|<span data-ttu-id="f3041-175">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f3041-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f3041-176">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f3041-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="f3041-177">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="f3041-178">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f3041-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f3041-179">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3041-179">Keyword for raising the event</span></span>|<span data-ttu-id="f3041-180">層級</span><span class="sxs-lookup"><span data-stu-id="f3041-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3041-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f3041-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f3041-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="f3041-183">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3041-184">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-184">Event</span></span>|<span data-ttu-id="f3041-185">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3041-185">Event ID</span></span>|<span data-ttu-id="f3041-186">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f3041-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="f3041-187">84</span><span class="sxs-lookup"><span data-stu-id="f3041-187">84</span></span>|<span data-ttu-id="f3041-188">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="f3041-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="f3041-189">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f3041-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f3041-190">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f3041-190">Field name</span></span>|<span data-ttu-id="f3041-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="f3041-191">Data type</span></span>|<span data-ttu-id="f3041-192">描述</span><span class="sxs-lookup"><span data-stu-id="f3041-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3041-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f3041-193">AppDomainID</span></span>|<span data-ttu-id="f3041-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-194">win:UInt64</span></span>|<span data-ttu-id="f3041-195">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="f3041-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="f3041-196">存活的</span><span class="sxs-lookup"><span data-stu-id="f3041-196">Survived</span></span>|<span data-ttu-id="f3041-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-197">win:UInt64</span></span>|<span data-ttu-id="f3041-198">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="f3041-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="f3041-199">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="f3041-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="f3041-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="f3041-200">ProcessSurvived</span></span>|<span data-ttu-id="f3041-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-201">win:UInt64</span></span>|<span data-ttu-id="f3041-202">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="f3041-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="f3041-203">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="f3041-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="f3041-204">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="f3041-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="f3041-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3041-205">ClrInstanceID</span></span>|<span data-ttu-id="f3041-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f3041-206">win:UInt16</span></span>|<span data-ttu-id="f3041-207">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f3041-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f3041-208">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f3041-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="f3041-209">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="f3041-210">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f3041-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f3041-211">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3041-211">Keyword for raising the event</span></span>|<span data-ttu-id="f3041-212">層級</span><span class="sxs-lookup"><span data-stu-id="f3041-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3041-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f3041-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f3041-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-214">Informational(4)</span></span>|  
|<span data-ttu-id="f3041-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f3041-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f3041-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="f3041-217">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3041-218">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-218">Event</span></span>|<span data-ttu-id="f3041-219">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3041-219">Event ID</span></span>|<span data-ttu-id="f3041-220">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f3041-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="f3041-221">87</span><span class="sxs-lookup"><span data-stu-id="f3041-221">87</span></span>|<span data-ttu-id="f3041-222">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3041-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="f3041-223">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f3041-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f3041-224">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f3041-224">Field name</span></span>|<span data-ttu-id="f3041-225">資料類型</span><span class="sxs-lookup"><span data-stu-id="f3041-225">Data type</span></span>|<span data-ttu-id="f3041-226">描述</span><span class="sxs-lookup"><span data-stu-id="f3041-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3041-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f3041-227">ThreadID</span></span>|<span data-ttu-id="f3041-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-228">win:UInt64</span></span>|<span data-ttu-id="f3041-229">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3041-229">The thread identifier.</span></span>|  
|<span data-ttu-id="f3041-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f3041-230">AppDomainID</span></span>|<span data-ttu-id="f3041-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-231">win:UInt64</span></span>|<span data-ttu-id="f3041-232">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="f3041-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="f3041-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3041-233">ClrInstanceID</span></span>|<span data-ttu-id="f3041-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f3041-234">win:UInt16</span></span>|<span data-ttu-id="f3041-235">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f3041-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f3041-236">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f3041-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="f3041-237">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="f3041-238">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f3041-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f3041-239">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3041-239">Keyword for raising the event</span></span>|<span data-ttu-id="f3041-240">層級</span><span class="sxs-lookup"><span data-stu-id="f3041-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3041-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f3041-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f3041-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-242">Informational(4)</span></span>|  
|<span data-ttu-id="f3041-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f3041-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f3041-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f3041-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="f3041-245">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f3041-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3041-246">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-246">Event</span></span>|<span data-ttu-id="f3041-247">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f3041-247">Event ID</span></span>|<span data-ttu-id="f3041-248">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f3041-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="f3041-249">86</span><span class="sxs-lookup"><span data-stu-id="f3041-249">86</span></span>|<span data-ttu-id="f3041-250">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="f3041-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="f3041-251">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="f3041-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="f3041-252">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f3041-252">Field name</span></span>|<span data-ttu-id="f3041-253">資料類型</span><span class="sxs-lookup"><span data-stu-id="f3041-253">Data type</span></span>|<span data-ttu-id="f3041-254">描述</span><span class="sxs-lookup"><span data-stu-id="f3041-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3041-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f3041-255">ThreadID</span></span>|<span data-ttu-id="f3041-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-256">win:UInt64</span></span>|<span data-ttu-id="f3041-257">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3041-257">The thread identifier.</span></span>|  
|<span data-ttu-id="f3041-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f3041-258">AppDomainID</span></span>|<span data-ttu-id="f3041-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f3041-259">win:UInt64</span></span>|<span data-ttu-id="f3041-260">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="f3041-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="f3041-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3041-261">ClrInstanceID</span></span>|<span data-ttu-id="f3041-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f3041-262">win:UInt16</span></span>|<span data-ttu-id="f3041-263">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f3041-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3041-264">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3041-264">See also</span></span>

- [<span data-ttu-id="f3041-265">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f3041-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
