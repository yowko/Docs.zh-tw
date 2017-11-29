---
title: "應用程式定義域資源監視 (ARM) ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="4275e-102">應用程式定義域資源監視 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="4275e-103"><a name="top"></a> 這些事件可提供有關應用程式網域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="4275e-104">您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="4275e-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="4275e-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="4275e-106">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="4275e-107">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="4275e-108">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="4275e-109">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="4275e-110">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="4275e-111">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="4275e-112">此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。</span><span class="sxs-lookup"><span data-stu-id="4275e-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="4275e-113">此為在這類取消提供者之下引發的唯一事件</span><span class="sxs-lookup"><span data-stu-id="4275e-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="4275e-114">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4275e-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="4275e-115">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="4275e-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4275e-116">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4275e-116">Keyword for raising the event</span></span>|<span data-ttu-id="4275e-117">層級</span><span class="sxs-lookup"><span data-stu-id="4275e-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4275e-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="4275e-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4275e-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-119">Informational(4)</span></span>|  
|<span data-ttu-id="4275e-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4275e-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4275e-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="4275e-122">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4275e-123">事件</span><span class="sxs-lookup"><span data-stu-id="4275e-123">Event</span></span>|<span data-ttu-id="4275e-124">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4275e-124">Event ID</span></span>|<span data-ttu-id="4275e-125">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4275e-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="4275e-126">85</span><span class="sxs-lookup"><span data-stu-id="4275e-126">85</span></span>|<span data-ttu-id="4275e-127">已為應用程式網域建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="4275e-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="4275e-128">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="4275e-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4275e-129">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4275e-129">Field name</span></span>|<span data-ttu-id="4275e-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="4275e-130">Data type</span></span>|<span data-ttu-id="4275e-131">描述</span><span class="sxs-lookup"><span data-stu-id="4275e-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4275e-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="4275e-132">ThreadID</span></span>|<span data-ttu-id="4275e-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-133">win:UInt64</span></span>|<span data-ttu-id="4275e-134">已建立執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4275e-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="4275e-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4275e-135">AppDomainID</span></span>|<span data-ttu-id="4275e-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-136">win:UInt64</span></span>|<span data-ttu-id="4275e-137">目前回報其執行緒活動之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="4275e-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="4275e-138">旗標</span><span class="sxs-lookup"><span data-stu-id="4275e-138">Flags</span></span>|<span data-ttu-id="4275e-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4275e-139">win:UInt32</span></span>|<span data-ttu-id="4275e-140">執行緒建立旗標。</span><span class="sxs-lookup"><span data-stu-id="4275e-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="4275e-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="4275e-141">ManagedThreadIndex</span></span>|<span data-ttu-id="4275e-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4275e-142">win:UInt32</span></span>|<span data-ttu-id="4275e-143">已建立之執行緒的 Managed 索引。</span><span class="sxs-lookup"><span data-stu-id="4275e-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="4275e-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="4275e-144">OSThreadID</span></span>|<span data-ttu-id="4275e-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4275e-145">win:UInt32</span></span>|<span data-ttu-id="4275e-146">已建立之執行緒的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="4275e-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="4275e-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4275e-147">ClrInstanceID</span></span>|<span data-ttu-id="4275e-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4275e-148">win:UInt16</span></span>|<span data-ttu-id="4275e-149">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4275e-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4275e-150">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4275e-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="4275e-151">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="4275e-152">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4275e-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4275e-153">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4275e-153">Keyword for raising the event</span></span>|<span data-ttu-id="4275e-154">層級</span><span class="sxs-lookup"><span data-stu-id="4275e-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4275e-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="4275e-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4275e-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="4275e-157">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4275e-158">事件</span><span class="sxs-lookup"><span data-stu-id="4275e-158">Event</span></span>|<span data-ttu-id="4275e-159">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4275e-159">Event ID</span></span>|<span data-ttu-id="4275e-160">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4275e-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="4275e-161">83</span><span class="sxs-lookup"><span data-stu-id="4275e-161">83</span></span>|<span data-ttu-id="4275e-162">每 4 MB 的記憶體 (大約)，配置於應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="4275e-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="4275e-163">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="4275e-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4275e-164">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4275e-164">Field name</span></span>|<span data-ttu-id="4275e-165">資料類型</span><span class="sxs-lookup"><span data-stu-id="4275e-165">Data type</span></span>|<span data-ttu-id="4275e-166">描述</span><span class="sxs-lookup"><span data-stu-id="4275e-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4275e-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4275e-167">AppDomainID</span></span>|<span data-ttu-id="4275e-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-168">win:UInt64</span></span>|<span data-ttu-id="4275e-169">已回報其資源使用量之應用程式網域的識別項。</span><span class="sxs-lookup"><span data-stu-id="4275e-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="4275e-170">已配置</span><span class="sxs-lookup"><span data-stu-id="4275e-170">Allocated</span></span>|<span data-ttu-id="4275e-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-171">win:UInt64</span></span>|<span data-ttu-id="4275e-172">建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。</span><span class="sxs-lookup"><span data-stu-id="4275e-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="4275e-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4275e-173">ClrInstanceID</span></span>|<span data-ttu-id="4275e-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4275e-174">win:UInt16</span></span>|<span data-ttu-id="4275e-175">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4275e-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4275e-176">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4275e-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="4275e-177">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="4275e-178">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4275e-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4275e-179">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4275e-179">Keyword for raising the event</span></span>|<span data-ttu-id="4275e-180">層級</span><span class="sxs-lookup"><span data-stu-id="4275e-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4275e-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="4275e-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4275e-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="4275e-183">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4275e-184">事件</span><span class="sxs-lookup"><span data-stu-id="4275e-184">Event</span></span>|<span data-ttu-id="4275e-185">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4275e-185">Event ID</span></span>|<span data-ttu-id="4275e-186">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4275e-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="4275e-187">84</span><span class="sxs-lookup"><span data-stu-id="4275e-187">84</span></span>|<span data-ttu-id="4275e-188">已結束回收每個記憶體。</span><span class="sxs-lookup"><span data-stu-id="4275e-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="4275e-189">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="4275e-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4275e-190">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4275e-190">Field name</span></span>|<span data-ttu-id="4275e-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="4275e-191">Data type</span></span>|<span data-ttu-id="4275e-192">描述</span><span class="sxs-lookup"><span data-stu-id="4275e-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4275e-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4275e-193">AppDomainID</span></span>|<span data-ttu-id="4275e-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-194">win:UInt64</span></span>|<span data-ttu-id="4275e-195">已回報其資源使用量的網域識別項。</span><span class="sxs-lookup"><span data-stu-id="4275e-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="4275e-196">存活的</span><span class="sxs-lookup"><span data-stu-id="4275e-196">Survived</span></span>|<span data-ttu-id="4275e-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-197">win:UInt64</span></span>|<span data-ttu-id="4275e-198">自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="4275e-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="4275e-199">在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="4275e-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="4275e-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="4275e-200">ProcessSurvived</span></span>|<span data-ttu-id="4275e-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-201">win:UInt64</span></span>|<span data-ttu-id="4275e-202">從最後一次集合中存活下來的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="4275e-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="4275e-203">收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="4275e-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="4275e-204">暫時收集之後，此數字代表存在於短暫世代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="4275e-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="4275e-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4275e-205">ClrInstanceID</span></span>|<span data-ttu-id="4275e-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4275e-206">win:UInt16</span></span>|<span data-ttu-id="4275e-207">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4275e-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4275e-208">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4275e-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="4275e-209">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="4275e-210">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4275e-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4275e-211">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4275e-211">Keyword for raising the event</span></span>|<span data-ttu-id="4275e-212">層級</span><span class="sxs-lookup"><span data-stu-id="4275e-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4275e-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="4275e-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4275e-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-214">Informational(4)</span></span>|  
|<span data-ttu-id="4275e-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4275e-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4275e-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="4275e-217">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4275e-218">事件</span><span class="sxs-lookup"><span data-stu-id="4275e-218">Event</span></span>|<span data-ttu-id="4275e-219">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4275e-219">Event ID</span></span>|<span data-ttu-id="4275e-220">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4275e-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="4275e-221">87</span><span class="sxs-lookup"><span data-stu-id="4275e-221">87</span></span>|<span data-ttu-id="4275e-222">進入應用程式網域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4275e-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="4275e-223">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="4275e-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4275e-224">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4275e-224">Field name</span></span>|<span data-ttu-id="4275e-225">資料類型</span><span class="sxs-lookup"><span data-stu-id="4275e-225">Data type</span></span>|<span data-ttu-id="4275e-226">描述</span><span class="sxs-lookup"><span data-stu-id="4275e-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4275e-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="4275e-227">ThreadID</span></span>|<span data-ttu-id="4275e-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-228">win:UInt64</span></span>|<span data-ttu-id="4275e-229">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="4275e-229">The thread identifier.</span></span>|  
|<span data-ttu-id="4275e-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4275e-230">AppDomainID</span></span>|<span data-ttu-id="4275e-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-231">win:UInt64</span></span>|<span data-ttu-id="4275e-232">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="4275e-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="4275e-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4275e-233">ClrInstanceID</span></span>|<span data-ttu-id="4275e-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4275e-234">win:UInt16</span></span>|<span data-ttu-id="4275e-235">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4275e-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4275e-236">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4275e-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="4275e-237">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="4275e-238">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4275e-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4275e-239">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4275e-239">Keyword for raising the event</span></span>|<span data-ttu-id="4275e-240">層級</span><span class="sxs-lookup"><span data-stu-id="4275e-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4275e-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="4275e-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4275e-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-242">Informational(4)</span></span>|  
|<span data-ttu-id="4275e-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4275e-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4275e-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4275e-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="4275e-245">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4275e-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4275e-246">事件</span><span class="sxs-lookup"><span data-stu-id="4275e-246">Event</span></span>|<span data-ttu-id="4275e-247">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4275e-247">Event ID</span></span>|<span data-ttu-id="4275e-248">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4275e-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="4275e-249">86</span><span class="sxs-lookup"><span data-stu-id="4275e-249">86</span></span>|<span data-ttu-id="4275e-250">一個執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="4275e-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="4275e-251">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="4275e-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="4275e-252">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4275e-252">Field name</span></span>|<span data-ttu-id="4275e-253">資料類型</span><span class="sxs-lookup"><span data-stu-id="4275e-253">Data type</span></span>|<span data-ttu-id="4275e-254">描述</span><span class="sxs-lookup"><span data-stu-id="4275e-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4275e-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="4275e-255">ThreadID</span></span>|<span data-ttu-id="4275e-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-256">win:UInt64</span></span>|<span data-ttu-id="4275e-257">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="4275e-257">The thread identifier.</span></span>|  
|<span data-ttu-id="4275e-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4275e-258">AppDomainID</span></span>|<span data-ttu-id="4275e-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4275e-259">win:UInt64</span></span>|<span data-ttu-id="4275e-260">應用程式網域識別項。</span><span class="sxs-lookup"><span data-stu-id="4275e-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="4275e-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4275e-261">ClrInstanceID</span></span>|<span data-ttu-id="4275e-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4275e-262">win:UInt16</span></span>|<span data-ttu-id="4275e-263">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4275e-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4275e-264">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4275e-264">See Also</span></span>  
 [<span data-ttu-id="4275e-265">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4275e-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
