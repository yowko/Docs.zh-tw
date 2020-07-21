---
title: 執行緒集區 ETW 事件
description: 審查執行緒集區 ETW 事件，這會收集 .NET 中線程的相關資訊。 執行緒集區事件是背景工作執行緒集區事件或 i/o 執行緒集區事件。
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: d3059cec5007c24d41a4a779939d4990f19305ca
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475199"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="e8831-104">執行緒集區 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e8831-104">Thread Pool ETW Events</span></span>
<span data-ttu-id="e8831-105">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-105">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="e8831-106">執行緒集區事件可分兩組：</span><span class="sxs-lookup"><span data-stu-id="e8831-106">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="e8831-107">[背景工作執行緒集區事件](#worker-thread-pool-events)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-107">[Worker thread pool events](#worker-thread-pool-events), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="e8831-108">[I/O 執行緒集區事件](#io-thread-events)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-108">[I/O thread pool events](#io-thread-events), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  

## <a name="worker-thread-pool-events"></a><span data-ttu-id="e8831-109">背景工作執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="e8831-109">Worker Thread Pool Events</span></span>
 <span data-ttu-id="e8831-110">這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。</span><span class="sxs-lookup"><span data-stu-id="e8831-110">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="e8831-111">背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。</span><span class="sxs-lookup"><span data-stu-id="e8831-111">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="e8831-112">背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="e8831-112">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="e8831-113">ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="e8831-113">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="e8831-114">下表顯示這些事件的關鍵字與層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-114">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="e8831-115">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="e8831-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e8831-116">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-116">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-117">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-118">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-118">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-119">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-119">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-120">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-120">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-121">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-121">Event</span></span>|<span data-ttu-id="e8831-122">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-122">Event ID</span></span>|<span data-ttu-id="e8831-123">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e8831-123">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="e8831-124">50</span><span class="sxs-lookup"><span data-stu-id="e8831-124">50</span></span>|<span data-ttu-id="e8831-125">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="e8831-125">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="e8831-126">51</span><span class="sxs-lookup"><span data-stu-id="e8831-126">51</span></span>|<span data-ttu-id="e8831-127">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="e8831-127">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="e8831-128">52</span><span class="sxs-lookup"><span data-stu-id="e8831-128">52</span></span>|<span data-ttu-id="e8831-129">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="e8831-129">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="e8831-130">53</span><span class="sxs-lookup"><span data-stu-id="e8831-130">53</span></span>|<span data-ttu-id="e8831-131">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="e8831-131">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="e8831-132">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-132">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-133">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-133">Field name</span></span>|<span data-ttu-id="e8831-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-134">Data type</span></span>|<span data-ttu-id="e8831-135">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-135">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-136">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e8831-136">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="e8831-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e8831-137">win:UInt32</span></span>|<span data-ttu-id="e8831-138">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8831-138">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="e8831-139">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e8831-139">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="e8831-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e8831-140">win:UInt32</span></span>|<span data-ttu-id="e8831-141">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8831-141">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="e8831-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-142">ClrInstanceID</span></span>|<span data-ttu-id="e8831-143">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-143">Win:UInt16</span></span>|<span data-ttu-id="e8831-144">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="e8831-145">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="e8831-145">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="e8831-146">這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="e8831-146">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="e8831-147">背景工作執行緒集區會於內部使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-147">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="e8831-148">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="e8831-148">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="e8831-149">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-149">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-150">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-150">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-151">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-151">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-152">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-152">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-153">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-153">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-154">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-154">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-155">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-155">Event</span></span>|<span data-ttu-id="e8831-156">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-156">Event ID</span></span>|<span data-ttu-id="e8831-157">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-157">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="e8831-158">54</span><span class="sxs-lookup"><span data-stu-id="e8831-158">54</span></span>|<span data-ttu-id="e8831-159">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="e8831-159">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="e8831-160">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-160">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-161">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-161">Field name</span></span>|<span data-ttu-id="e8831-162">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-162">Data type</span></span>|<span data-ttu-id="e8831-163">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-163">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-164">輸送量</span><span class="sxs-lookup"><span data-stu-id="e8831-164">Throughput</span></span>|<span data-ttu-id="e8831-165">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-165">win:Double</span></span>|<span data-ttu-id="e8831-166">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-166">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="e8831-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-167">ClrInstanceID</span></span>|<span data-ttu-id="e8831-168">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-168">Win:UInt16</span></span>|<span data-ttu-id="e8831-169">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="e8831-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="e8831-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="e8831-171">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-171">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-172">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-172">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-173">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-173">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-174">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-174">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-175">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-175">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-176">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-176">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-177">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-177">Event</span></span>|<span data-ttu-id="e8831-178">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-178">Event ID</span></span>|<span data-ttu-id="e8831-179">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-179">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="e8831-180">55</span><span class="sxs-lookup"><span data-stu-id="e8831-180">55</span></span>|<span data-ttu-id="e8831-181">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="e8831-181">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="e8831-182">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-182">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-183">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-183">Field name</span></span>|<span data-ttu-id="e8831-184">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-184">Data type</span></span>|<span data-ttu-id="e8831-185">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-185">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-186">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="e8831-186">AverageThroughput</span></span>|<span data-ttu-id="e8831-187">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-187">win:Double</span></span>|<span data-ttu-id="e8831-188">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="e8831-188">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="e8831-189">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e8831-189">NewWorkerThreadCount</span></span>|<span data-ttu-id="e8831-190">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e8831-190">win:UInt32</span></span>|<span data-ttu-id="e8831-191">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-191">New number of active worker threads.</span></span>|  
|<span data-ttu-id="e8831-192">原因</span><span class="sxs-lookup"><span data-stu-id="e8831-192">Reason</span></span>|<span data-ttu-id="e8831-193">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e8831-193">win:UInt32</span></span>|<span data-ttu-id="e8831-194">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="e8831-194">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="e8831-195">0x00 - 熱身。</span><span class="sxs-lookup"><span data-stu-id="e8831-195">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="e8831-196">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="e8831-196">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="e8831-197">0x02 - 隨機移動。</span><span class="sxs-lookup"><span data-stu-id="e8831-197">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="e8831-198">0x03 - 攀登移動。</span><span class="sxs-lookup"><span data-stu-id="e8831-198">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="e8831-199">0x04 - 變更點。</span><span class="sxs-lookup"><span data-stu-id="e8831-199">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="e8831-200">0x05 - 穩定。</span><span class="sxs-lookup"><span data-stu-id="e8831-200">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="e8831-201">0x06 - 資源不足。</span><span class="sxs-lookup"><span data-stu-id="e8831-201">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="e8831-202">0x07 - 執行緒逾時。</span><span class="sxs-lookup"><span data-stu-id="e8831-202">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="e8831-203">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-203">ClrInstanceID</span></span>|<span data-ttu-id="e8831-204">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-204">Win:UInt16</span></span>|<span data-ttu-id="e8831-205">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-205">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="e8831-206">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="e8831-206">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="e8831-207">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-207">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-208">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-208">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-209">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-209">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-210">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-210">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-211">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-211">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-212">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-212">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-213">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-213">Event</span></span>|<span data-ttu-id="e8831-214">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-214">Event ID</span></span>|<span data-ttu-id="e8831-215">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-215">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="e8831-216">56</span><span class="sxs-lookup"><span data-stu-id="e8831-216">56</span></span>|<span data-ttu-id="e8831-217">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-217">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="e8831-218">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-218">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-219">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-219">Field name</span></span>|<span data-ttu-id="e8831-220">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-220">Data type</span></span>|<span data-ttu-id="e8831-221">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-221">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-222">Duration</span><span class="sxs-lookup"><span data-stu-id="e8831-222">Duration</span></span>|<span data-ttu-id="e8831-223">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-223">win:Double</span></span>|<span data-ttu-id="e8831-224">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="e8831-224">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="e8831-225">輸送量</span><span class="sxs-lookup"><span data-stu-id="e8831-225">Throughput</span></span>|<span data-ttu-id="e8831-226">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-226">win:Double</span></span>|<span data-ttu-id="e8831-227">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-227">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="e8831-228">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="e8831-228">ThreadWave</span></span>|<span data-ttu-id="e8831-229">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-229">win:Double</span></span>|<span data-ttu-id="e8831-230">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="e8831-230">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e8831-231">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="e8831-231">ThroughputWave</span></span>|<span data-ttu-id="e8831-232">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-232">win:Double</span></span>|<span data-ttu-id="e8831-233">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="e8831-233">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e8831-234">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="e8831-234">ThroughputErrorEstimate</span></span>|<span data-ttu-id="e8831-235">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-235">win:Double</span></span>|<span data-ttu-id="e8831-236">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="e8831-236">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e8831-237">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="e8831-237">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="e8831-238">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-238">win:Double</span></span>|<span data-ttu-id="e8831-239">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="e8831-239">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e8831-240">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="e8831-240">ThroughputRatio</span></span>|<span data-ttu-id="e8831-241">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-241">win:Double</span></span>|<span data-ttu-id="e8831-242">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="e8831-242">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="e8831-243">信賴度</span><span class="sxs-lookup"><span data-stu-id="e8831-243">Confidence</span></span>|<span data-ttu-id="e8831-244">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-244">win:Double</span></span>|<span data-ttu-id="e8831-245">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="e8831-245">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="e8831-246">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="e8831-246">NewcontrolSetting</span></span>|<span data-ttu-id="e8831-247">win:Double</span><span class="sxs-lookup"><span data-stu-id="e8831-247">win:Double</span></span>|<span data-ttu-id="e8831-248">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="e8831-248">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="e8831-249">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="e8831-249">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="e8831-250">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-250">Win:UInt16</span></span>|<span data-ttu-id="e8831-251">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="e8831-251">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="e8831-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-252">ClrInstanceID</span></span>|<span data-ttu-id="e8831-253">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-253">Win:UInt16</span></span>|<span data-ttu-id="e8831-254">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="io-thread-events"></a><span data-ttu-id="e8831-255">I/O 執行緒事件</span><span class="sxs-lookup"><span data-stu-id="e8831-255">I/O Thread Events</span></span>  
 <span data-ttu-id="e8831-256">會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。</span><span class="sxs-lookup"><span data-stu-id="e8831-256">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreate_v1"></a><span data-ttu-id="e8831-257">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="e8831-257">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="e8831-258">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-258">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-259">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-259">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-260">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-260">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-261">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-261">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-262">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-262">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-263">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-263">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-264">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-264">Event</span></span>|<span data-ttu-id="e8831-265">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-265">Event ID</span></span>|<span data-ttu-id="e8831-266">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e8831-266">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="e8831-267">44</span><span class="sxs-lookup"><span data-stu-id="e8831-267">44</span></span>|<span data-ttu-id="e8831-268">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="e8831-268">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="e8831-269">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-269">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-270">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-270">Field name</span></span>|<span data-ttu-id="e8831-271">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-271">Data type</span></span>|<span data-ttu-id="e8831-272">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-272">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-273">計數</span><span class="sxs-lookup"><span data-stu-id="e8831-273">Count</span></span>|<span data-ttu-id="e8831-274">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-274">win:UInt64</span></span>|<span data-ttu-id="e8831-275">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8831-275">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="e8831-276">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e8831-276">NumRetired</span></span>|<span data-ttu-id="e8831-277">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-277">win:UInt64</span></span>|<span data-ttu-id="e8831-278">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-278">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="e8831-279">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-279">ClrInstanceID</span></span>|<span data-ttu-id="e8831-280">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-280">Win:UInt16</span></span>|<span data-ttu-id="e8831-281">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-281">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretire_v1"></a><span data-ttu-id="e8831-282">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="e8831-282">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="e8831-283">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-284">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-284">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-285">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-286">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-286">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-287">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-288">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-289">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-289">Event</span></span>|<span data-ttu-id="e8831-290">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-290">Event ID</span></span>|<span data-ttu-id="e8831-291">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e8831-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="e8831-292">46</span><span class="sxs-lookup"><span data-stu-id="e8831-292">46</span></span>|<span data-ttu-id="e8831-293">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="e8831-293">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="e8831-294">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-295">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-295">Field name</span></span>|<span data-ttu-id="e8831-296">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-296">Data type</span></span>|<span data-ttu-id="e8831-297">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-298">計數</span><span class="sxs-lookup"><span data-stu-id="e8831-298">Count</span></span>|<span data-ttu-id="e8831-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-299">win:UInt64</span></span>|<span data-ttu-id="e8831-300">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-300">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="e8831-301">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e8831-301">NumRetired</span></span>|<span data-ttu-id="e8831-302">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-302">win:UInt64</span></span>|<span data-ttu-id="e8831-303">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-303">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e8831-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-304">ClrInstanceID</span></span>|<span data-ttu-id="e8831-305">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-305">Win:UInt16</span></span>|<span data-ttu-id="e8831-306">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretire_v1"></a><span data-ttu-id="e8831-307">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="e8831-307">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="e8831-308">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-308">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-309">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-309">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-310">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-310">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-311">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-311">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-312">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-312">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-313">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-313">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-314">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-314">Event</span></span>|<span data-ttu-id="e8831-315">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-315">Event ID</span></span>|<span data-ttu-id="e8831-316">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e8831-316">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="e8831-317">47</span><span class="sxs-lookup"><span data-stu-id="e8831-317">47</span></span>|<span data-ttu-id="e8831-318">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="e8831-318">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="e8831-319">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-319">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-320">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-320">Field name</span></span>|<span data-ttu-id="e8831-321">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-321">Data type</span></span>|<span data-ttu-id="e8831-322">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-322">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-323">計數</span><span class="sxs-lookup"><span data-stu-id="e8831-323">Count</span></span>|<span data-ttu-id="e8831-324">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-324">win:UInt64</span></span>|<span data-ttu-id="e8831-325">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8831-325">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="e8831-326">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e8831-326">NumRetired</span></span>|<span data-ttu-id="e8831-327">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-327">win:UInt64</span></span>|<span data-ttu-id="e8831-328">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-328">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e8831-329">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-329">ClrInstanceID</span></span>|<span data-ttu-id="e8831-330">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-330">Win:UInt16</span></span>|<span data-ttu-id="e8831-331">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-331">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="e8831-332">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="e8831-332">IOThreadTerminate</span></span>  
 <span data-ttu-id="e8831-333">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e8831-333">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e8831-334">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8831-334">Keyword for raising the event</span></span>|<span data-ttu-id="e8831-335">層級</span><span class="sxs-lookup"><span data-stu-id="e8831-335">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e8831-336">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e8831-336">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e8831-337">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="e8831-337">Informational (4)</span></span>|  
  
 <span data-ttu-id="e8831-338">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e8831-338">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e8831-339">事件</span><span class="sxs-lookup"><span data-stu-id="e8831-339">Event</span></span>|<span data-ttu-id="e8831-340">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8831-340">Event ID</span></span>|<span data-ttu-id="e8831-341">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e8831-341">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="e8831-342">45</span><span class="sxs-lookup"><span data-stu-id="e8831-342">45</span></span>|<span data-ttu-id="e8831-343">執行緒集區中的 i/o 執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="e8831-343">An I/O thread is terminated in the thread pool.</span></span>|  
  
 <span data-ttu-id="e8831-344">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e8831-344">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e8831-345">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e8831-345">Field name</span></span>|<span data-ttu-id="e8831-346">資料類型</span><span class="sxs-lookup"><span data-stu-id="e8831-346">Data type</span></span>|<span data-ttu-id="e8831-347">描述</span><span class="sxs-lookup"><span data-stu-id="e8831-347">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e8831-348">計數</span><span class="sxs-lookup"><span data-stu-id="e8831-348">Count</span></span>|<span data-ttu-id="e8831-349">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-349">win:UInt64</span></span>|<span data-ttu-id="e8831-350">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-350">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="e8831-351">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e8831-351">NumRetired</span></span>|<span data-ttu-id="e8831-352">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e8831-352">win:UInt64</span></span>|<span data-ttu-id="e8831-353">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="e8831-353">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e8831-354">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e8831-354">ClrInstanceID</span></span>|<span data-ttu-id="e8831-355">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e8831-355">Win:UInt16</span></span>|<span data-ttu-id="e8831-356">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e8831-356">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8831-357">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8831-357">See also</span></span>

- [<span data-ttu-id="e8831-358">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e8831-358">CLR ETW Events</span></span>](clr-etw-events.md)
