---
title: 執行緒集區 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 309570fb5a159d24f5b423d96fd9987ee3bb886f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503309"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="d6aec-102">執行緒集區 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-102">Thread Pool ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="d6aec-103">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-103">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="d6aec-104">執行緒集區事件可分兩組：</span><span class="sxs-lookup"><span data-stu-id="d6aec-104">There are two groups of thread pool events:</span></span>  
  
-   <span data-ttu-id="d6aec-105">[背景工作執行緒集區事件](#worker)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-105">[Worker thread pool events](#worker), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
-   <span data-ttu-id="d6aec-106">[I/O 執行緒集區事件](#io)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-106">[I/O thread pool events](#io), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a><span data-ttu-id="d6aec-107">背景工作執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-107">Worker Thread Pool Events</span></span>  
 <span data-ttu-id="d6aec-108">這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。</span><span class="sxs-lookup"><span data-stu-id="d6aec-108">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="d6aec-109">背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。</span><span class="sxs-lookup"><span data-stu-id="d6aec-109">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="d6aec-110">背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="d6aec-110">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="d6aec-111">ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="d6aec-111">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="d6aec-112">下表顯示這些事件的關鍵字與層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-112">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="d6aec-113">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="d6aec-113">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d6aec-114">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-114">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-115">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-115">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-116">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-116">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-117">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-117">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-118">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-118">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-119">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-119">Event</span></span>|<span data-ttu-id="d6aec-120">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-120">Event ID</span></span>|<span data-ttu-id="d6aec-121">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d6aec-121">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="d6aec-122">50</span><span class="sxs-lookup"><span data-stu-id="d6aec-122">50</span></span>|<span data-ttu-id="d6aec-123">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-123">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="d6aec-124">51</span><span class="sxs-lookup"><span data-stu-id="d6aec-124">51</span></span>|<span data-ttu-id="d6aec-125">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-125">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="d6aec-126">52</span><span class="sxs-lookup"><span data-stu-id="d6aec-126">52</span></span>|<span data-ttu-id="d6aec-127">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-127">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="d6aec-128">53</span><span class="sxs-lookup"><span data-stu-id="d6aec-128">53</span></span>|<span data-ttu-id="d6aec-129">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-129">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="d6aec-130">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-130">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-131">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-131">Field name</span></span>|<span data-ttu-id="d6aec-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-132">Data type</span></span>|<span data-ttu-id="d6aec-133">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-133">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-134">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="d6aec-134">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="d6aec-135">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d6aec-135">win:UInt32</span></span>|<span data-ttu-id="d6aec-136">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d6aec-136">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="d6aec-137">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="d6aec-137">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="d6aec-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d6aec-138">win:UInt32</span></span>|<span data-ttu-id="d6aec-139">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="d6aec-139">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="d6aec-140">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-140">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-141">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-141">Win:UInt16</span></span>|<span data-ttu-id="d6aec-142">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-142">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="d6aec-143">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="d6aec-143">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="d6aec-144">這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="d6aec-144">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="d6aec-145">背景工作執行緒集區會於內部使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-145">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="d6aec-146">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="d6aec-146">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="d6aec-147">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-147">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-148">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-148">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-149">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-149">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-150">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-150">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-151">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-151">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-152">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-152">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-153">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-153">Event</span></span>|<span data-ttu-id="d6aec-154">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-154">Event ID</span></span>|<span data-ttu-id="d6aec-155">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-155">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="d6aec-156">54</span><span class="sxs-lookup"><span data-stu-id="d6aec-156">54</span></span>|<span data-ttu-id="d6aec-157">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="d6aec-157">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="d6aec-158">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-158">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-159">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-159">Field name</span></span>|<span data-ttu-id="d6aec-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-160">Data type</span></span>|<span data-ttu-id="d6aec-161">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-161">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-162">輸送量</span><span class="sxs-lookup"><span data-stu-id="d6aec-162">Throughput</span></span>|<span data-ttu-id="d6aec-163">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-163">win:Double</span></span>|<span data-ttu-id="d6aec-164">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-164">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="d6aec-165">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-165">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-166">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-166">Win:UInt16</span></span>|<span data-ttu-id="d6aec-167">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-167">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="d6aec-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="d6aec-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="d6aec-169">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-169">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-170">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-170">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-171">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-171">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-172">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-172">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-173">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-173">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-174">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-174">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-175">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-175">Event</span></span>|<span data-ttu-id="d6aec-176">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-176">Event ID</span></span>|<span data-ttu-id="d6aec-177">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-177">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="d6aec-178">55</span><span class="sxs-lookup"><span data-stu-id="d6aec-178">55</span></span>|<span data-ttu-id="d6aec-179">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="d6aec-179">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="d6aec-180">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-180">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-181">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-181">Field name</span></span>|<span data-ttu-id="d6aec-182">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-182">Data type</span></span>|<span data-ttu-id="d6aec-183">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-183">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-184">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="d6aec-184">AverageThroughput</span></span>|<span data-ttu-id="d6aec-185">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-185">win:Double</span></span>|<span data-ttu-id="d6aec-186">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="d6aec-186">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="d6aec-187">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="d6aec-187">NewWorkerThreadCount</span></span>|<span data-ttu-id="d6aec-188">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d6aec-188">win:UInt32</span></span>|<span data-ttu-id="d6aec-189">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-189">New number of active worker threads.</span></span>|  
|<span data-ttu-id="d6aec-190">原因</span><span class="sxs-lookup"><span data-stu-id="d6aec-190">Reason</span></span>|<span data-ttu-id="d6aec-191">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d6aec-191">win:UInt32</span></span>|<span data-ttu-id="d6aec-192">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="d6aec-192">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="d6aec-193">0x00 - 熱身。</span><span class="sxs-lookup"><span data-stu-id="d6aec-193">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="d6aec-194">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="d6aec-194">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="d6aec-195">0x02 - 隨機移動。</span><span class="sxs-lookup"><span data-stu-id="d6aec-195">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="d6aec-196">0x03 - 攀登移動。</span><span class="sxs-lookup"><span data-stu-id="d6aec-196">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="d6aec-197">0x04 - 變更點。</span><span class="sxs-lookup"><span data-stu-id="d6aec-197">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="d6aec-198">0x05 - 穩定。</span><span class="sxs-lookup"><span data-stu-id="d6aec-198">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="d6aec-199">0x06 - 資源不足。</span><span class="sxs-lookup"><span data-stu-id="d6aec-199">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="d6aec-200">0x07 - 執行緒逾時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-200">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="d6aec-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-201">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-202">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-202">Win:UInt16</span></span>|<span data-ttu-id="d6aec-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="d6aec-204">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="d6aec-204">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="d6aec-205">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-205">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-206">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-206">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-207">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-207">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-208">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-208">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-209">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-209">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-210">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-210">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-211">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-211">Event</span></span>|<span data-ttu-id="d6aec-212">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-212">Event ID</span></span>|<span data-ttu-id="d6aec-213">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-213">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="d6aec-214">56</span><span class="sxs-lookup"><span data-stu-id="d6aec-214">56</span></span>|<span data-ttu-id="d6aec-215">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-215">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="d6aec-216">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-216">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-217">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-217">Field name</span></span>|<span data-ttu-id="d6aec-218">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-218">Data type</span></span>|<span data-ttu-id="d6aec-219">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-219">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-220">持續期間</span><span class="sxs-lookup"><span data-stu-id="d6aec-220">Duration</span></span>|<span data-ttu-id="d6aec-221">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-221">win:Double</span></span>|<span data-ttu-id="d6aec-222">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6aec-222">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="d6aec-223">輸送量</span><span class="sxs-lookup"><span data-stu-id="d6aec-223">Throughput</span></span>|<span data-ttu-id="d6aec-224">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-224">win:Double</span></span>|<span data-ttu-id="d6aec-225">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-225">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="d6aec-226">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="d6aec-226">ThreadWave</span></span>|<span data-ttu-id="d6aec-227">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-227">win:Double</span></span>|<span data-ttu-id="d6aec-228">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="d6aec-228">Reserved for internal use.</span></span>|  
|<span data-ttu-id="d6aec-229">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="d6aec-229">ThroughputWave</span></span>|<span data-ttu-id="d6aec-230">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-230">win:Double</span></span>|<span data-ttu-id="d6aec-231">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="d6aec-231">Reserved for internal use.</span></span>|  
|<span data-ttu-id="d6aec-232">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="d6aec-232">ThroughputErrorEstimate</span></span>|<span data-ttu-id="d6aec-233">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-233">win:Double</span></span>|<span data-ttu-id="d6aec-234">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="d6aec-234">Reserved for internal use.</span></span>|  
|<span data-ttu-id="d6aec-235">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="d6aec-235">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="d6aec-236">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-236">win:Double</span></span>|<span data-ttu-id="d6aec-237">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="d6aec-237">Reserved for internal use.</span></span>|  
|<span data-ttu-id="d6aec-238">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="d6aec-238">ThroughputRatio</span></span>|<span data-ttu-id="d6aec-239">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-239">win:Double</span></span>|<span data-ttu-id="d6aec-240">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="d6aec-240">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="d6aec-241">Confidence</span><span class="sxs-lookup"><span data-stu-id="d6aec-241">Confidence</span></span>|<span data-ttu-id="d6aec-242">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-242">win:Double</span></span>|<span data-ttu-id="d6aec-243">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="d6aec-243">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="d6aec-244">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="d6aec-244">NewcontrolSetting</span></span>|<span data-ttu-id="d6aec-245">win:Double</span><span class="sxs-lookup"><span data-stu-id="d6aec-245">win:Double</span></span>|<span data-ttu-id="d6aec-246">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="d6aec-246">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="d6aec-247">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="d6aec-247">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="d6aec-248">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-248">Win:UInt16</span></span>|<span data-ttu-id="d6aec-249">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="d6aec-249">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="d6aec-250">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-250">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-251">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-251">Win:UInt16</span></span>|<span data-ttu-id="d6aec-252">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-252">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d6aec-253">回到頁首</span><span class="sxs-lookup"><span data-stu-id="d6aec-253">Back to top</span></span>](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a><span data-ttu-id="d6aec-254">I/O 執行緒事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-254">I/O Thread Events</span></span>  
 <span data-ttu-id="d6aec-255">會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。</span><span class="sxs-lookup"><span data-stu-id="d6aec-255">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreatev1"></a><span data-ttu-id="d6aec-256">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="d6aec-256">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="d6aec-257">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-257">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-258">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-258">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-259">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-259">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-260">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-260">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-261">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-261">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-262">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-262">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-263">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-263">Event</span></span>|<span data-ttu-id="d6aec-264">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-264">Event ID</span></span>|<span data-ttu-id="d6aec-265">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d6aec-265">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="d6aec-266">44</span><span class="sxs-lookup"><span data-stu-id="d6aec-266">44</span></span>|<span data-ttu-id="d6aec-267">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-267">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="d6aec-268">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-268">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-269">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-269">Field name</span></span>|<span data-ttu-id="d6aec-270">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-270">Data type</span></span>|<span data-ttu-id="d6aec-271">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-271">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-272">計數</span><span class="sxs-lookup"><span data-stu-id="d6aec-272">Count</span></span>|<span data-ttu-id="d6aec-273">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-273">win:UInt64</span></span>|<span data-ttu-id="d6aec-274">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d6aec-274">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="d6aec-275">NumRetired</span><span class="sxs-lookup"><span data-stu-id="d6aec-275">NumRetired</span></span>|<span data-ttu-id="d6aec-276">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-276">win:UInt64</span></span>|<span data-ttu-id="d6aec-277">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-277">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="d6aec-278">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-278">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-279">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-279">Win:UInt16</span></span>|<span data-ttu-id="d6aec-280">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretirev1"></a><span data-ttu-id="d6aec-281">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="d6aec-281">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="d6aec-282">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-282">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-283">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-283">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-284">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-284">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-286">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-286">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-287">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-287">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-288">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-288">Event</span></span>|<span data-ttu-id="d6aec-289">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-289">Event ID</span></span>|<span data-ttu-id="d6aec-290">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d6aec-290">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="d6aec-291">46</span><span class="sxs-lookup"><span data-stu-id="d6aec-291">46</span></span>|<span data-ttu-id="d6aec-292">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-292">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="d6aec-293">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-293">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-294">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-294">Field name</span></span>|<span data-ttu-id="d6aec-295">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-295">Data type</span></span>|<span data-ttu-id="d6aec-296">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-296">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-297">計數</span><span class="sxs-lookup"><span data-stu-id="d6aec-297">Count</span></span>|<span data-ttu-id="d6aec-298">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-298">win:UInt64</span></span>|<span data-ttu-id="d6aec-299">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-299">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="d6aec-300">NumRetired</span><span class="sxs-lookup"><span data-stu-id="d6aec-300">NumRetired</span></span>|<span data-ttu-id="d6aec-301">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-301">win:UInt64</span></span>|<span data-ttu-id="d6aec-302">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-302">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="d6aec-303">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-303">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-304">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-304">Win:UInt16</span></span>|<span data-ttu-id="d6aec-305">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-305">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretirev1"></a><span data-ttu-id="d6aec-306">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="d6aec-306">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="d6aec-307">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-307">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-308">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-308">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-309">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-309">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-310">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-310">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-311">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-311">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-312">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-312">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-313">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-313">Event</span></span>|<span data-ttu-id="d6aec-314">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-314">Event ID</span></span>|<span data-ttu-id="d6aec-315">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d6aec-315">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="d6aec-316">47</span><span class="sxs-lookup"><span data-stu-id="d6aec-316">47</span></span>|<span data-ttu-id="d6aec-317">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-317">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="d6aec-318">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-318">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-319">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-319">Field name</span></span>|<span data-ttu-id="d6aec-320">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-320">Data type</span></span>|<span data-ttu-id="d6aec-321">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-321">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-322">計數</span><span class="sxs-lookup"><span data-stu-id="d6aec-322">Count</span></span>|<span data-ttu-id="d6aec-323">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-323">win:UInt64</span></span>|<span data-ttu-id="d6aec-324">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="d6aec-324">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="d6aec-325">NumRetired</span><span class="sxs-lookup"><span data-stu-id="d6aec-325">NumRetired</span></span>|<span data-ttu-id="d6aec-326">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-326">win:UInt64</span></span>|<span data-ttu-id="d6aec-327">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-327">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="d6aec-328">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-328">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-329">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-329">Win:UInt16</span></span>|<span data-ttu-id="d6aec-330">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-330">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="d6aec-331">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="d6aec-331">IOThreadTerminate</span></span>  
 <span data-ttu-id="d6aec-332">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="d6aec-332">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d6aec-333">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6aec-333">Keyword for raising the event</span></span>|<span data-ttu-id="d6aec-334">層級</span><span class="sxs-lookup"><span data-stu-id="d6aec-334">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d6aec-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d6aec-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d6aec-336">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d6aec-336">Informational (4)</span></span>|  
  
 <span data-ttu-id="d6aec-337">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="d6aec-337">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d6aec-338">事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-338">Event</span></span>|<span data-ttu-id="d6aec-339">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d6aec-339">Event ID</span></span>|<span data-ttu-id="d6aec-340">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d6aec-340">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="d6aec-341">45</span><span class="sxs-lookup"><span data-stu-id="d6aec-341">45</span></span>|<span data-ttu-id="d6aec-342">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="d6aec-342">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="d6aec-343">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="d6aec-343">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d6aec-344">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d6aec-344">Field name</span></span>|<span data-ttu-id="d6aec-345">資料類型</span><span class="sxs-lookup"><span data-stu-id="d6aec-345">Data type</span></span>|<span data-ttu-id="d6aec-346">描述</span><span class="sxs-lookup"><span data-stu-id="d6aec-346">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d6aec-347">計數</span><span class="sxs-lookup"><span data-stu-id="d6aec-347">Count</span></span>|<span data-ttu-id="d6aec-348">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-348">win:UInt64</span></span>|<span data-ttu-id="d6aec-349">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-349">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="d6aec-350">NumRetired</span><span class="sxs-lookup"><span data-stu-id="d6aec-350">NumRetired</span></span>|<span data-ttu-id="d6aec-351">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d6aec-351">win:UInt64</span></span>|<span data-ttu-id="d6aec-352">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6aec-352">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="d6aec-353">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d6aec-353">ClrInstanceID</span></span>|<span data-ttu-id="d6aec-354">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d6aec-354">Win:UInt16</span></span>|<span data-ttu-id="d6aec-355">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6aec-355">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6aec-356">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6aec-356">See also</span></span>
- [<span data-ttu-id="d6aec-357">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="d6aec-357">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
