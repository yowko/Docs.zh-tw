---
title: 應用程式定義域資源監視 (ARM) ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac396e1a5b83f33068266553024c37ef436c150d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616639"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="61c43-102">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="61c43-103">這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="61c43-104">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="61c43-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="61c43-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="61c43-106">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="61c43-107">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="61c43-108">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="61c43-109">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="61c43-110">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="61c43-111">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="61c43-112">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="61c43-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="61c43-113">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="61c43-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="61c43-114">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="61c43-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="61c43-115">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="61c43-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="61c43-116">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="61c43-116">Keyword for raising the event</span></span>|<span data-ttu-id="61c43-117">層級</span><span class="sxs-lookup"><span data-stu-id="61c43-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61c43-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="61c43-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="61c43-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-119">Informational(4)</span></span>|  
|<span data-ttu-id="61c43-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="61c43-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="61c43-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="61c43-122">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61c43-123">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-123">Event</span></span>|<span data-ttu-id="61c43-124">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61c43-124">Event ID</span></span>|<span data-ttu-id="61c43-125">引發的時機</span><span class="sxs-lookup"><span data-stu-id="61c43-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="61c43-126">85</span><span class="sxs-lookup"><span data-stu-id="61c43-126">85</span></span>|<span data-ttu-id="61c43-127">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="61c43-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="61c43-128">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="61c43-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61c43-129">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="61c43-129">Field name</span></span>|<span data-ttu-id="61c43-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="61c43-130">Data type</span></span>|<span data-ttu-id="61c43-131">描述</span><span class="sxs-lookup"><span data-stu-id="61c43-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61c43-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="61c43-132">ThreadID</span></span>|<span data-ttu-id="61c43-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-133">win:UInt64</span></span>|<span data-ttu-id="61c43-134">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="61c43-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="61c43-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="61c43-135">AppDomainID</span></span>|<span data-ttu-id="61c43-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-136">win:UInt64</span></span>|<span data-ttu-id="61c43-137">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="61c43-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="61c43-138">旗標</span><span class="sxs-lookup"><span data-stu-id="61c43-138">Flags</span></span>|<span data-ttu-id="61c43-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="61c43-139">win:UInt32</span></span>|<span data-ttu-id="61c43-140">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="61c43-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="61c43-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="61c43-141">ManagedThreadIndex</span></span>|<span data-ttu-id="61c43-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="61c43-142">win:UInt32</span></span>|<span data-ttu-id="61c43-143">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="61c43-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="61c43-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="61c43-144">OSThreadID</span></span>|<span data-ttu-id="61c43-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="61c43-145">win:UInt32</span></span>|<span data-ttu-id="61c43-146">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="61c43-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="61c43-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61c43-147">ClrInstanceID</span></span>|<span data-ttu-id="61c43-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="61c43-148">win:UInt16</span></span>|<span data-ttu-id="61c43-149">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="61c43-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61c43-150">回到頁首</span><span class="sxs-lookup"><span data-stu-id="61c43-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="61c43-151">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="61c43-152">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="61c43-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="61c43-153">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="61c43-153">Keyword for raising the event</span></span>|<span data-ttu-id="61c43-154">層級</span><span class="sxs-lookup"><span data-stu-id="61c43-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61c43-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="61c43-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="61c43-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="61c43-157">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61c43-158">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-158">Event</span></span>|<span data-ttu-id="61c43-159">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61c43-159">Event ID</span></span>|<span data-ttu-id="61c43-160">引發的時機</span><span class="sxs-lookup"><span data-stu-id="61c43-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="61c43-161">83</span><span class="sxs-lookup"><span data-stu-id="61c43-161">83</span></span>|<span data-ttu-id="61c43-162">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="61c43-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="61c43-163">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="61c43-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61c43-164">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="61c43-164">Field name</span></span>|<span data-ttu-id="61c43-165">資料類型</span><span class="sxs-lookup"><span data-stu-id="61c43-165">Data type</span></span>|<span data-ttu-id="61c43-166">描述</span><span class="sxs-lookup"><span data-stu-id="61c43-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61c43-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="61c43-167">AppDomainID</span></span>|<span data-ttu-id="61c43-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-168">win:UInt64</span></span>|<span data-ttu-id="61c43-169">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="61c43-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="61c43-170">已配置</span><span class="sxs-lookup"><span data-stu-id="61c43-170">Allocated</span></span>|<span data-ttu-id="61c43-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-171">win:UInt64</span></span>|<span data-ttu-id="61c43-172">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="61c43-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="61c43-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61c43-173">ClrInstanceID</span></span>|<span data-ttu-id="61c43-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="61c43-174">win:UInt16</span></span>|<span data-ttu-id="61c43-175">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="61c43-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61c43-176">回到頁首</span><span class="sxs-lookup"><span data-stu-id="61c43-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="61c43-177">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="61c43-178">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="61c43-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="61c43-179">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="61c43-179">Keyword for raising the event</span></span>|<span data-ttu-id="61c43-180">層級</span><span class="sxs-lookup"><span data-stu-id="61c43-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61c43-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="61c43-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="61c43-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="61c43-183">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61c43-184">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-184">Event</span></span>|<span data-ttu-id="61c43-185">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61c43-185">Event ID</span></span>|<span data-ttu-id="61c43-186">引發的時機</span><span class="sxs-lookup"><span data-stu-id="61c43-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="61c43-187">84</span><span class="sxs-lookup"><span data-stu-id="61c43-187">84</span></span>|<span data-ttu-id="61c43-188">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="61c43-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="61c43-189">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="61c43-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61c43-190">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="61c43-190">Field name</span></span>|<span data-ttu-id="61c43-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="61c43-191">Data type</span></span>|<span data-ttu-id="61c43-192">描述</span><span class="sxs-lookup"><span data-stu-id="61c43-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61c43-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="61c43-193">AppDomainID</span></span>|<span data-ttu-id="61c43-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-194">win:UInt64</span></span>|<span data-ttu-id="61c43-195">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="61c43-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="61c43-196">存活的</span><span class="sxs-lookup"><span data-stu-id="61c43-196">Survived</span></span>|<span data-ttu-id="61c43-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-197">win:UInt64</span></span>|<span data-ttu-id="61c43-198">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="61c43-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="61c43-199">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="61c43-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="61c43-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="61c43-200">ProcessSurvived</span></span>|<span data-ttu-id="61c43-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-201">win:UInt64</span></span>|<span data-ttu-id="61c43-202">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="61c43-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="61c43-203">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="61c43-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="61c43-204">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="61c43-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="61c43-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61c43-205">ClrInstanceID</span></span>|<span data-ttu-id="61c43-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="61c43-206">win:UInt16</span></span>|<span data-ttu-id="61c43-207">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="61c43-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61c43-208">回到頁首</span><span class="sxs-lookup"><span data-stu-id="61c43-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="61c43-209">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="61c43-210">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="61c43-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="61c43-211">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="61c43-211">Keyword for raising the event</span></span>|<span data-ttu-id="61c43-212">層級</span><span class="sxs-lookup"><span data-stu-id="61c43-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61c43-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="61c43-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="61c43-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-214">Informational(4)</span></span>|  
|<span data-ttu-id="61c43-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="61c43-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="61c43-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="61c43-217">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61c43-218">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-218">Event</span></span>|<span data-ttu-id="61c43-219">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61c43-219">Event ID</span></span>|<span data-ttu-id="61c43-220">引發的時機</span><span class="sxs-lookup"><span data-stu-id="61c43-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="61c43-221">87</span><span class="sxs-lookup"><span data-stu-id="61c43-221">87</span></span>|<span data-ttu-id="61c43-222">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="61c43-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="61c43-223">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="61c43-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61c43-224">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="61c43-224">Field name</span></span>|<span data-ttu-id="61c43-225">資料類型</span><span class="sxs-lookup"><span data-stu-id="61c43-225">Data type</span></span>|<span data-ttu-id="61c43-226">描述</span><span class="sxs-lookup"><span data-stu-id="61c43-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61c43-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="61c43-227">ThreadID</span></span>|<span data-ttu-id="61c43-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-228">win:UInt64</span></span>|<span data-ttu-id="61c43-229">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="61c43-229">The thread identifier.</span></span>|  
|<span data-ttu-id="61c43-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="61c43-230">AppDomainID</span></span>|<span data-ttu-id="61c43-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-231">win:UInt64</span></span>|<span data-ttu-id="61c43-232">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="61c43-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="61c43-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61c43-233">ClrInstanceID</span></span>|<span data-ttu-id="61c43-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="61c43-234">win:UInt16</span></span>|<span data-ttu-id="61c43-235">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="61c43-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61c43-236">回到頁首</span><span class="sxs-lookup"><span data-stu-id="61c43-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="61c43-237">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="61c43-238">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="61c43-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="61c43-239">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="61c43-239">Keyword for raising the event</span></span>|<span data-ttu-id="61c43-240">層級</span><span class="sxs-lookup"><span data-stu-id="61c43-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61c43-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="61c43-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="61c43-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-242">Informational(4)</span></span>|  
|<span data-ttu-id="61c43-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="61c43-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="61c43-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61c43-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="61c43-245">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="61c43-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61c43-246">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-246">Event</span></span>|<span data-ttu-id="61c43-247">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61c43-247">Event ID</span></span>|<span data-ttu-id="61c43-248">引發的時機</span><span class="sxs-lookup"><span data-stu-id="61c43-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="61c43-249">86</span><span class="sxs-lookup"><span data-stu-id="61c43-249">86</span></span>|<span data-ttu-id="61c43-250">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="61c43-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="61c43-251">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="61c43-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="61c43-252">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="61c43-252">Field name</span></span>|<span data-ttu-id="61c43-253">資料類型</span><span class="sxs-lookup"><span data-stu-id="61c43-253">Data type</span></span>|<span data-ttu-id="61c43-254">描述</span><span class="sxs-lookup"><span data-stu-id="61c43-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61c43-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="61c43-255">ThreadID</span></span>|<span data-ttu-id="61c43-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-256">win:UInt64</span></span>|<span data-ttu-id="61c43-257">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="61c43-257">The thread identifier.</span></span>|  
|<span data-ttu-id="61c43-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="61c43-258">AppDomainID</span></span>|<span data-ttu-id="61c43-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="61c43-259">win:UInt64</span></span>|<span data-ttu-id="61c43-260">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="61c43-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="61c43-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61c43-261">ClrInstanceID</span></span>|<span data-ttu-id="61c43-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="61c43-262">win:UInt16</span></span>|<span data-ttu-id="61c43-263">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="61c43-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61c43-264">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c43-264">See also</span></span>

- [<span data-ttu-id="61c43-265">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="61c43-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
