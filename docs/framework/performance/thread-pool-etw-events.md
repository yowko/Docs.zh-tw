---
title: "執行緒集區 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3dfd8b17e4ca01802651087ff20988744a411ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="acd9f-102">執行緒集區 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-102">Thread Pool ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="acd9f-103">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-103">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="acd9f-104">執行緒集區事件可分兩組：</span><span class="sxs-lookup"><span data-stu-id="acd9f-104">There are two groups of thread pool events:</span></span>  
  
-   <span data-ttu-id="acd9f-105">[背景工作執行緒集區事件](#worker)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-105">[Worker thread pool events](#worker), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
-   <span data-ttu-id="acd9f-106">[I/O 執行緒集區事件](#io)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-106">[I/O thread pool events](#io), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a><span data-ttu-id="acd9f-107">背景工作執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-107">Worker Thread Pool Events</span></span>  
 <span data-ttu-id="acd9f-108">這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。</span><span class="sxs-lookup"><span data-stu-id="acd9f-108">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="acd9f-109">背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。</span><span class="sxs-lookup"><span data-stu-id="acd9f-109">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="acd9f-110">背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="acd9f-110">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="acd9f-111">ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="acd9f-111">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="acd9f-112">下表顯示這些事件的關鍵字與層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-112">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="acd9f-113">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="acd9f-113">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="acd9f-114">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-114">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-115">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-115">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-116">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-116">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-117">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-117">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-118">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-118">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-119">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-119">Event</span></span>|<span data-ttu-id="acd9f-120">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-120">Event ID</span></span>|<span data-ttu-id="acd9f-121">引發的時機</span><span class="sxs-lookup"><span data-stu-id="acd9f-121">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="acd9f-122">50</span><span class="sxs-lookup"><span data-stu-id="acd9f-122">50</span></span>|<span data-ttu-id="acd9f-123">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-123">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="acd9f-124">51</span><span class="sxs-lookup"><span data-stu-id="acd9f-124">51</span></span>|<span data-ttu-id="acd9f-125">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-125">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="acd9f-126">52</span><span class="sxs-lookup"><span data-stu-id="acd9f-126">52</span></span>|<span data-ttu-id="acd9f-127">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-127">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="acd9f-128">53</span><span class="sxs-lookup"><span data-stu-id="acd9f-128">53</span></span>|<span data-ttu-id="acd9f-129">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-129">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="acd9f-130">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-130">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-131">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-131">Field name</span></span>|<span data-ttu-id="acd9f-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-132">Data type</span></span>|<span data-ttu-id="acd9f-133">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-133">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-134">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="acd9f-134">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="acd9f-135">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="acd9f-135">win:UInt32</span></span>|<span data-ttu-id="acd9f-136">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="acd9f-136">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="acd9f-137">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="acd9f-137">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="acd9f-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="acd9f-138">win:UInt32</span></span>|<span data-ttu-id="acd9f-139">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="acd9f-139">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="acd9f-140">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-140">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-141">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-141">Win:UInt16</span></span>|<span data-ttu-id="acd9f-142">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-142">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="acd9f-143">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="acd9f-143">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="acd9f-144">這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="acd9f-144">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="acd9f-145">背景工作執行緒集區會於內部使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-145">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="acd9f-146">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="acd9f-146">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="acd9f-147">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-147">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-148">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-148">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-149">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-149">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-150">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-150">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-151">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-151">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-152">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-152">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-153">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-153">Event</span></span>|<span data-ttu-id="acd9f-154">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-154">Event ID</span></span>|<span data-ttu-id="acd9f-155">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-155">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="acd9f-156">54</span><span class="sxs-lookup"><span data-stu-id="acd9f-156">54</span></span>|<span data-ttu-id="acd9f-157">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="acd9f-157">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="acd9f-158">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-158">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-159">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-159">Field name</span></span>|<span data-ttu-id="acd9f-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-160">Data type</span></span>|<span data-ttu-id="acd9f-161">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-161">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-162">輸送量</span><span class="sxs-lookup"><span data-stu-id="acd9f-162">Throughput</span></span>|<span data-ttu-id="acd9f-163">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-163">win:Double</span></span>|<span data-ttu-id="acd9f-164">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-164">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="acd9f-165">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-165">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-166">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-166">Win:UInt16</span></span>|<span data-ttu-id="acd9f-167">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-167">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="acd9f-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="acd9f-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="acd9f-169">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-169">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-170">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-170">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-171">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-171">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-172">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-172">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-173">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-173">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-174">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-174">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-175">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-175">Event</span></span>|<span data-ttu-id="acd9f-176">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-176">Event ID</span></span>|<span data-ttu-id="acd9f-177">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-177">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="acd9f-178">55</span><span class="sxs-lookup"><span data-stu-id="acd9f-178">55</span></span>|<span data-ttu-id="acd9f-179">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="acd9f-179">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="acd9f-180">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-180">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-181">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-181">Field name</span></span>|<span data-ttu-id="acd9f-182">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-182">Data type</span></span>|<span data-ttu-id="acd9f-183">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-183">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-184">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="acd9f-184">AverageThroughput</span></span>|<span data-ttu-id="acd9f-185">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-185">win:Double</span></span>|<span data-ttu-id="acd9f-186">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="acd9f-186">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="acd9f-187">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="acd9f-187">NewWorkerThreadCount</span></span>|<span data-ttu-id="acd9f-188">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="acd9f-188">win:UInt32</span></span>|<span data-ttu-id="acd9f-189">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-189">New number of active worker threads.</span></span>|  
|<span data-ttu-id="acd9f-190">原因</span><span class="sxs-lookup"><span data-stu-id="acd9f-190">Reason</span></span>|<span data-ttu-id="acd9f-191">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="acd9f-191">win:UInt32</span></span>|<span data-ttu-id="acd9f-192">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="acd9f-192">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="acd9f-193">0x00 - 熱身。</span><span class="sxs-lookup"><span data-stu-id="acd9f-193">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="acd9f-194">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="acd9f-194">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="acd9f-195">0x02 - 隨機移動。</span><span class="sxs-lookup"><span data-stu-id="acd9f-195">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="acd9f-196">0x03 - 攀登移動。</span><span class="sxs-lookup"><span data-stu-id="acd9f-196">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="acd9f-197">0x04 - 變更點。</span><span class="sxs-lookup"><span data-stu-id="acd9f-197">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="acd9f-198">0x05 - 穩定。</span><span class="sxs-lookup"><span data-stu-id="acd9f-198">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="acd9f-199">0x06 - 資源不足。</span><span class="sxs-lookup"><span data-stu-id="acd9f-199">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="acd9f-200">0x07 - 執行緒逾時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-200">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="acd9f-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-201">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-202">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-202">Win:UInt16</span></span>|<span data-ttu-id="acd9f-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="acd9f-204">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="acd9f-204">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="acd9f-205">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-205">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-206">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-206">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-207">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-207">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-208">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-208">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-209">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-209">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-210">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-210">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-211">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-211">Event</span></span>|<span data-ttu-id="acd9f-212">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-212">Event ID</span></span>|<span data-ttu-id="acd9f-213">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-213">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="acd9f-214">56</span><span class="sxs-lookup"><span data-stu-id="acd9f-214">56</span></span>|<span data-ttu-id="acd9f-215">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-215">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="acd9f-216">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-216">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-217">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-217">Field name</span></span>|<span data-ttu-id="acd9f-218">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-218">Data type</span></span>|<span data-ttu-id="acd9f-219">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-219">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-220">持續期間</span><span class="sxs-lookup"><span data-stu-id="acd9f-220">Duration</span></span>|<span data-ttu-id="acd9f-221">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-221">win:Double</span></span>|<span data-ttu-id="acd9f-222">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="acd9f-222">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="acd9f-223">輸送量</span><span class="sxs-lookup"><span data-stu-id="acd9f-223">Throughput</span></span>|<span data-ttu-id="acd9f-224">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-224">win:Double</span></span>|<span data-ttu-id="acd9f-225">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-225">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="acd9f-226">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="acd9f-226">ThreadWave</span></span>|<span data-ttu-id="acd9f-227">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-227">win:Double</span></span>|<span data-ttu-id="acd9f-228">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="acd9f-228">Reserved for internal use.</span></span>|  
|<span data-ttu-id="acd9f-229">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="acd9f-229">ThroughputWave</span></span>|<span data-ttu-id="acd9f-230">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-230">win:Double</span></span>|<span data-ttu-id="acd9f-231">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="acd9f-231">Reserved for internal use.</span></span>|  
|<span data-ttu-id="acd9f-232">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="acd9f-232">ThroughputErrorEstimate</span></span>|<span data-ttu-id="acd9f-233">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-233">win:Double</span></span>|<span data-ttu-id="acd9f-234">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="acd9f-234">Reserved for internal use.</span></span>|  
|<span data-ttu-id="acd9f-235">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="acd9f-235">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="acd9f-236">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-236">win:Double</span></span>|<span data-ttu-id="acd9f-237">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="acd9f-237">Reserved for internal use.</span></span>|  
|<span data-ttu-id="acd9f-238">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="acd9f-238">ThroughputRatio</span></span>|<span data-ttu-id="acd9f-239">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-239">win:Double</span></span>|<span data-ttu-id="acd9f-240">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="acd9f-240">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="acd9f-241">Confidence</span><span class="sxs-lookup"><span data-stu-id="acd9f-241">Confidence</span></span>|<span data-ttu-id="acd9f-242">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-242">win:Double</span></span>|<span data-ttu-id="acd9f-243">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="acd9f-243">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="acd9f-244">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="acd9f-244">NewcontrolSetting</span></span>|<span data-ttu-id="acd9f-245">win:Double</span><span class="sxs-lookup"><span data-stu-id="acd9f-245">win:Double</span></span>|<span data-ttu-id="acd9f-246">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="acd9f-246">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="acd9f-247">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="acd9f-247">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="acd9f-248">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-248">Win:UInt16</span></span>|<span data-ttu-id="acd9f-249">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="acd9f-249">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="acd9f-250">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-250">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-251">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-251">Win:UInt16</span></span>|<span data-ttu-id="acd9f-252">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-252">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="acd9f-253">回到頁首</span><span class="sxs-lookup"><span data-stu-id="acd9f-253">Back to top</span></span>](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a><span data-ttu-id="acd9f-254">I/O 執行緒事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-254">I/O Thread Events</span></span>  
 <span data-ttu-id="acd9f-255">會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。</span><span class="sxs-lookup"><span data-stu-id="acd9f-255">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreatev1"></a><span data-ttu-id="acd9f-256">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="acd9f-256">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="acd9f-257">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-257">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-258">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-258">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-259">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-259">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-260">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-260">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-261">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-261">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-262">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-262">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-263">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-263">Event</span></span>|<span data-ttu-id="acd9f-264">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-264">Event ID</span></span>|<span data-ttu-id="acd9f-265">引發的時機</span><span class="sxs-lookup"><span data-stu-id="acd9f-265">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="acd9f-266">44</span><span class="sxs-lookup"><span data-stu-id="acd9f-266">44</span></span>|<span data-ttu-id="acd9f-267">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-267">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="acd9f-268">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-268">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-269">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-269">Field name</span></span>|<span data-ttu-id="acd9f-270">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-270">Data type</span></span>|<span data-ttu-id="acd9f-271">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-271">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-272">計數</span><span class="sxs-lookup"><span data-stu-id="acd9f-272">Count</span></span>|<span data-ttu-id="acd9f-273">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-273">win:UInt64</span></span>|<span data-ttu-id="acd9f-274">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="acd9f-274">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="acd9f-275">NumRetired</span><span class="sxs-lookup"><span data-stu-id="acd9f-275">NumRetired</span></span>|<span data-ttu-id="acd9f-276">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-276">win:UInt64</span></span>|<span data-ttu-id="acd9f-277">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-277">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="acd9f-278">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-278">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-279">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-279">Win:UInt16</span></span>|<span data-ttu-id="acd9f-280">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretirev1"></a><span data-ttu-id="acd9f-281">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="acd9f-281">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="acd9f-282">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-282">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-283">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-283">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-284">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-284">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-286">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-286">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-287">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-287">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-288">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-288">Event</span></span>|<span data-ttu-id="acd9f-289">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-289">Event ID</span></span>|<span data-ttu-id="acd9f-290">引發的時機</span><span class="sxs-lookup"><span data-stu-id="acd9f-290">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="acd9f-291">46</span><span class="sxs-lookup"><span data-stu-id="acd9f-291">46</span></span>|<span data-ttu-id="acd9f-292">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-292">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="acd9f-293">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-293">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-294">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-294">Field name</span></span>|<span data-ttu-id="acd9f-295">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-295">Data type</span></span>|<span data-ttu-id="acd9f-296">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-296">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-297">計數</span><span class="sxs-lookup"><span data-stu-id="acd9f-297">Count</span></span>|<span data-ttu-id="acd9f-298">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-298">win:UInt64</span></span>|<span data-ttu-id="acd9f-299">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-299">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="acd9f-300">NumRetired</span><span class="sxs-lookup"><span data-stu-id="acd9f-300">NumRetired</span></span>|<span data-ttu-id="acd9f-301">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-301">win:UInt64</span></span>|<span data-ttu-id="acd9f-302">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-302">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="acd9f-303">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-303">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-304">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-304">Win:UInt16</span></span>|<span data-ttu-id="acd9f-305">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-305">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretirev1"></a><span data-ttu-id="acd9f-306">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="acd9f-306">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="acd9f-307">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-307">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-308">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-308">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-309">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-309">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-310">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-310">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-311">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-311">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-312">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-312">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-313">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-313">Event</span></span>|<span data-ttu-id="acd9f-314">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-314">Event ID</span></span>|<span data-ttu-id="acd9f-315">引發的時機</span><span class="sxs-lookup"><span data-stu-id="acd9f-315">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="acd9f-316">47</span><span class="sxs-lookup"><span data-stu-id="acd9f-316">47</span></span>|<span data-ttu-id="acd9f-317">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-317">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="acd9f-318">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-318">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-319">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-319">Field name</span></span>|<span data-ttu-id="acd9f-320">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-320">Data type</span></span>|<span data-ttu-id="acd9f-321">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-321">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-322">計數</span><span class="sxs-lookup"><span data-stu-id="acd9f-322">Count</span></span>|<span data-ttu-id="acd9f-323">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-323">win:UInt64</span></span>|<span data-ttu-id="acd9f-324">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="acd9f-324">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="acd9f-325">NumRetired</span><span class="sxs-lookup"><span data-stu-id="acd9f-325">NumRetired</span></span>|<span data-ttu-id="acd9f-326">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-326">win:UInt64</span></span>|<span data-ttu-id="acd9f-327">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-327">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="acd9f-328">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-328">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-329">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-329">Win:UInt16</span></span>|<span data-ttu-id="acd9f-330">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-330">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="acd9f-331">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="acd9f-331">IOThreadTerminate</span></span>  
 <span data-ttu-id="acd9f-332">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="acd9f-332">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="acd9f-333">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="acd9f-333">Keyword for raising the event</span></span>|<span data-ttu-id="acd9f-334">層級</span><span class="sxs-lookup"><span data-stu-id="acd9f-334">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="acd9f-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="acd9f-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="acd9f-336">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="acd9f-336">Informational (4)</span></span>|  
  
 <span data-ttu-id="acd9f-337">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="acd9f-337">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="acd9f-338">事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-338">Event</span></span>|<span data-ttu-id="acd9f-339">事件 ID</span><span class="sxs-lookup"><span data-stu-id="acd9f-339">Event ID</span></span>|<span data-ttu-id="acd9f-340">引發的時機</span><span class="sxs-lookup"><span data-stu-id="acd9f-340">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="acd9f-341">45</span><span class="sxs-lookup"><span data-stu-id="acd9f-341">45</span></span>|<span data-ttu-id="acd9f-342">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="acd9f-342">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="acd9f-343">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="acd9f-343">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="acd9f-344">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="acd9f-344">Field name</span></span>|<span data-ttu-id="acd9f-345">資料類型</span><span class="sxs-lookup"><span data-stu-id="acd9f-345">Data type</span></span>|<span data-ttu-id="acd9f-346">描述</span><span class="sxs-lookup"><span data-stu-id="acd9f-346">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="acd9f-347">計數</span><span class="sxs-lookup"><span data-stu-id="acd9f-347">Count</span></span>|<span data-ttu-id="acd9f-348">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-348">win:UInt64</span></span>|<span data-ttu-id="acd9f-349">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-349">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="acd9f-350">NumRetired</span><span class="sxs-lookup"><span data-stu-id="acd9f-350">NumRetired</span></span>|<span data-ttu-id="acd9f-351">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="acd9f-351">win:UInt64</span></span>|<span data-ttu-id="acd9f-352">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="acd9f-352">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="acd9f-353">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="acd9f-353">ClrInstanceID</span></span>|<span data-ttu-id="acd9f-354">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="acd9f-354">Win:UInt16</span></span>|<span data-ttu-id="acd9f-355">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="acd9f-355">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acd9f-356">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd9f-356">See Also</span></span>  
 [<span data-ttu-id="acd9f-357">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="acd9f-357">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
