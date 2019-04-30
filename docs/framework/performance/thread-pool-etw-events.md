---
title: 執行緒集區 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caacee591c4df8389cea241916618f50da56b22b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949158"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="dce36-102">執行緒集區 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-102">Thread Pool ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="dce36-103">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-103">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="dce36-104">執行緒集區事件可分兩組：</span><span class="sxs-lookup"><span data-stu-id="dce36-104">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="dce36-105">[背景工作執行緒集區事件](#worker)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-105">[Worker thread pool events](#worker), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="dce36-106">[I/O 執行緒集區事件](#io)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-106">[I/O thread pool events](#io), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a><span data-ttu-id="dce36-107">背景工作執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="dce36-107">Worker Thread Pool Events</span></span>  
 <span data-ttu-id="dce36-108">這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。</span><span class="sxs-lookup"><span data-stu-id="dce36-108">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="dce36-109">背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。</span><span class="sxs-lookup"><span data-stu-id="dce36-109">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="dce36-110">背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="dce36-110">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="dce36-111">ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="dce36-111">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="dce36-112">下表顯示這些事件的關鍵字與層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-112">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="dce36-113">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="dce36-113">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="dce36-114">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-114">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-115">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-115">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-116">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-116">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-117">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-117">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-118">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-118">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-119">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-119">Event</span></span>|<span data-ttu-id="dce36-120">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-120">Event ID</span></span>|<span data-ttu-id="dce36-121">引發的時機</span><span class="sxs-lookup"><span data-stu-id="dce36-121">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="dce36-122">50</span><span class="sxs-lookup"><span data-stu-id="dce36-122">50</span></span>|<span data-ttu-id="dce36-123">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="dce36-123">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="dce36-124">51</span><span class="sxs-lookup"><span data-stu-id="dce36-124">51</span></span>|<span data-ttu-id="dce36-125">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="dce36-125">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="dce36-126">52</span><span class="sxs-lookup"><span data-stu-id="dce36-126">52</span></span>|<span data-ttu-id="dce36-127">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="dce36-127">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="dce36-128">53</span><span class="sxs-lookup"><span data-stu-id="dce36-128">53</span></span>|<span data-ttu-id="dce36-129">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="dce36-129">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="dce36-130">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-130">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-131">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-131">Field name</span></span>|<span data-ttu-id="dce36-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-132">Data type</span></span>|<span data-ttu-id="dce36-133">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-133">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-134">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="dce36-134">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="dce36-135">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dce36-135">win:UInt32</span></span>|<span data-ttu-id="dce36-136">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="dce36-136">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="dce36-137">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="dce36-137">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="dce36-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dce36-138">win:UInt32</span></span>|<span data-ttu-id="dce36-139">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="dce36-139">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="dce36-140">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-140">ClrInstanceID</span></span>|<span data-ttu-id="dce36-141">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-141">Win:UInt16</span></span>|<span data-ttu-id="dce36-142">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-142">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="dce36-143">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="dce36-143">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="dce36-144">這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="dce36-144">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="dce36-145">背景工作執行緒集區會於內部使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-145">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="dce36-146">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="dce36-146">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="dce36-147">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-147">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-148">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-148">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-149">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-149">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-150">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-150">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-151">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-151">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-152">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-152">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-153">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-153">Event</span></span>|<span data-ttu-id="dce36-154">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-154">Event ID</span></span>|<span data-ttu-id="dce36-155">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-155">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="dce36-156">54</span><span class="sxs-lookup"><span data-stu-id="dce36-156">54</span></span>|<span data-ttu-id="dce36-157">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="dce36-157">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="dce36-158">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-158">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-159">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-159">Field name</span></span>|<span data-ttu-id="dce36-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-160">Data type</span></span>|<span data-ttu-id="dce36-161">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-161">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-162">輸送量</span><span class="sxs-lookup"><span data-stu-id="dce36-162">Throughput</span></span>|<span data-ttu-id="dce36-163">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-163">win:Double</span></span>|<span data-ttu-id="dce36-164">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-164">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="dce36-165">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-165">ClrInstanceID</span></span>|<span data-ttu-id="dce36-166">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-166">Win:UInt16</span></span>|<span data-ttu-id="dce36-167">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-167">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="dce36-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="dce36-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="dce36-169">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-169">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-170">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-170">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-171">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-171">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-172">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-172">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-173">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-173">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-174">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-174">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-175">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-175">Event</span></span>|<span data-ttu-id="dce36-176">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-176">Event ID</span></span>|<span data-ttu-id="dce36-177">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-177">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="dce36-178">55</span><span class="sxs-lookup"><span data-stu-id="dce36-178">55</span></span>|<span data-ttu-id="dce36-179">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="dce36-179">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="dce36-180">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-180">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-181">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-181">Field name</span></span>|<span data-ttu-id="dce36-182">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-182">Data type</span></span>|<span data-ttu-id="dce36-183">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-183">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-184">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="dce36-184">AverageThroughput</span></span>|<span data-ttu-id="dce36-185">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-185">win:Double</span></span>|<span data-ttu-id="dce36-186">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="dce36-186">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="dce36-187">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="dce36-187">NewWorkerThreadCount</span></span>|<span data-ttu-id="dce36-188">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dce36-188">win:UInt32</span></span>|<span data-ttu-id="dce36-189">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-189">New number of active worker threads.</span></span>|  
|<span data-ttu-id="dce36-190">原因</span><span class="sxs-lookup"><span data-stu-id="dce36-190">Reason</span></span>|<span data-ttu-id="dce36-191">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="dce36-191">win:UInt32</span></span>|<span data-ttu-id="dce36-192">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="dce36-192">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="dce36-193">0x00 - 熱身。</span><span class="sxs-lookup"><span data-stu-id="dce36-193">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="dce36-194">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="dce36-194">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="dce36-195">0x02 - 隨機移動。</span><span class="sxs-lookup"><span data-stu-id="dce36-195">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="dce36-196">0x03 - 攀登移動。</span><span class="sxs-lookup"><span data-stu-id="dce36-196">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="dce36-197">0x04 - 變更點。</span><span class="sxs-lookup"><span data-stu-id="dce36-197">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="dce36-198">0x05 - 穩定。</span><span class="sxs-lookup"><span data-stu-id="dce36-198">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="dce36-199">0x06 - 資源不足。</span><span class="sxs-lookup"><span data-stu-id="dce36-199">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="dce36-200">0x07 - 執行緒逾時。</span><span class="sxs-lookup"><span data-stu-id="dce36-200">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="dce36-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-201">ClrInstanceID</span></span>|<span data-ttu-id="dce36-202">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-202">Win:UInt16</span></span>|<span data-ttu-id="dce36-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="dce36-204">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="dce36-204">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="dce36-205">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-205">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-206">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-206">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-207">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-207">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-208">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-208">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-209">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-209">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-210">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-210">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-211">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-211">Event</span></span>|<span data-ttu-id="dce36-212">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-212">Event ID</span></span>|<span data-ttu-id="dce36-213">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-213">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="dce36-214">56</span><span class="sxs-lookup"><span data-stu-id="dce36-214">56</span></span>|<span data-ttu-id="dce36-215">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-215">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="dce36-216">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-216">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-217">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-217">Field name</span></span>|<span data-ttu-id="dce36-218">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-218">Data type</span></span>|<span data-ttu-id="dce36-219">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-219">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-220">持續期間</span><span class="sxs-lookup"><span data-stu-id="dce36-220">Duration</span></span>|<span data-ttu-id="dce36-221">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-221">win:Double</span></span>|<span data-ttu-id="dce36-222">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="dce36-222">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="dce36-223">輸送量</span><span class="sxs-lookup"><span data-stu-id="dce36-223">Throughput</span></span>|<span data-ttu-id="dce36-224">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-224">win:Double</span></span>|<span data-ttu-id="dce36-225">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-225">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="dce36-226">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="dce36-226">ThreadWave</span></span>|<span data-ttu-id="dce36-227">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-227">win:Double</span></span>|<span data-ttu-id="dce36-228">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="dce36-228">Reserved for internal use.</span></span>|  
|<span data-ttu-id="dce36-229">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="dce36-229">ThroughputWave</span></span>|<span data-ttu-id="dce36-230">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-230">win:Double</span></span>|<span data-ttu-id="dce36-231">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="dce36-231">Reserved for internal use.</span></span>|  
|<span data-ttu-id="dce36-232">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="dce36-232">ThroughputErrorEstimate</span></span>|<span data-ttu-id="dce36-233">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-233">win:Double</span></span>|<span data-ttu-id="dce36-234">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="dce36-234">Reserved for internal use.</span></span>|  
|<span data-ttu-id="dce36-235">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="dce36-235">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="dce36-236">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-236">win:Double</span></span>|<span data-ttu-id="dce36-237">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="dce36-237">Reserved for internal use.</span></span>|  
|<span data-ttu-id="dce36-238">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="dce36-238">ThroughputRatio</span></span>|<span data-ttu-id="dce36-239">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-239">win:Double</span></span>|<span data-ttu-id="dce36-240">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="dce36-240">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="dce36-241">Confidence</span><span class="sxs-lookup"><span data-stu-id="dce36-241">Confidence</span></span>|<span data-ttu-id="dce36-242">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-242">win:Double</span></span>|<span data-ttu-id="dce36-243">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="dce36-243">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="dce36-244">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="dce36-244">NewcontrolSetting</span></span>|<span data-ttu-id="dce36-245">win:Double</span><span class="sxs-lookup"><span data-stu-id="dce36-245">win:Double</span></span>|<span data-ttu-id="dce36-246">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="dce36-246">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="dce36-247">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="dce36-247">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="dce36-248">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-248">Win:UInt16</span></span>|<span data-ttu-id="dce36-249">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="dce36-249">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="dce36-250">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-250">ClrInstanceID</span></span>|<span data-ttu-id="dce36-251">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-251">Win:UInt16</span></span>|<span data-ttu-id="dce36-252">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-252">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="dce36-253">回到頁首</span><span class="sxs-lookup"><span data-stu-id="dce36-253">Back to top</span></span>](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a><span data-ttu-id="dce36-254">I/O 執行緒事件</span><span class="sxs-lookup"><span data-stu-id="dce36-254">I/O Thread Events</span></span>  
 <span data-ttu-id="dce36-255">會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。</span><span class="sxs-lookup"><span data-stu-id="dce36-255">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreatev1"></a><span data-ttu-id="dce36-256">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="dce36-256">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="dce36-257">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-257">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-258">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-258">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-259">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-259">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-260">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-260">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-261">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-261">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-262">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-262">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-263">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-263">Event</span></span>|<span data-ttu-id="dce36-264">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-264">Event ID</span></span>|<span data-ttu-id="dce36-265">引發的時機</span><span class="sxs-lookup"><span data-stu-id="dce36-265">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="dce36-266">44</span><span class="sxs-lookup"><span data-stu-id="dce36-266">44</span></span>|<span data-ttu-id="dce36-267">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="dce36-267">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="dce36-268">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-268">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-269">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-269">Field name</span></span>|<span data-ttu-id="dce36-270">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-270">Data type</span></span>|<span data-ttu-id="dce36-271">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-271">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-272">Count</span><span class="sxs-lookup"><span data-stu-id="dce36-272">Count</span></span>|<span data-ttu-id="dce36-273">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-273">win:UInt64</span></span>|<span data-ttu-id="dce36-274">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="dce36-274">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="dce36-275">NumRetired</span><span class="sxs-lookup"><span data-stu-id="dce36-275">NumRetired</span></span>|<span data-ttu-id="dce36-276">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-276">win:UInt64</span></span>|<span data-ttu-id="dce36-277">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-277">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="dce36-278">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-278">ClrInstanceID</span></span>|<span data-ttu-id="dce36-279">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-279">Win:UInt16</span></span>|<span data-ttu-id="dce36-280">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretirev1"></a><span data-ttu-id="dce36-281">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="dce36-281">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="dce36-282">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-282">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-283">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-283">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-284">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-284">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-286">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-286">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-287">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-287">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-288">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-288">Event</span></span>|<span data-ttu-id="dce36-289">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-289">Event ID</span></span>|<span data-ttu-id="dce36-290">引發的時機</span><span class="sxs-lookup"><span data-stu-id="dce36-290">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="dce36-291">46</span><span class="sxs-lookup"><span data-stu-id="dce36-291">46</span></span>|<span data-ttu-id="dce36-292">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="dce36-292">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="dce36-293">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-293">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-294">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-294">Field name</span></span>|<span data-ttu-id="dce36-295">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-295">Data type</span></span>|<span data-ttu-id="dce36-296">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-296">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-297">Count</span><span class="sxs-lookup"><span data-stu-id="dce36-297">Count</span></span>|<span data-ttu-id="dce36-298">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-298">win:UInt64</span></span>|<span data-ttu-id="dce36-299">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-299">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="dce36-300">NumRetired</span><span class="sxs-lookup"><span data-stu-id="dce36-300">NumRetired</span></span>|<span data-ttu-id="dce36-301">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-301">win:UInt64</span></span>|<span data-ttu-id="dce36-302">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-302">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="dce36-303">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-303">ClrInstanceID</span></span>|<span data-ttu-id="dce36-304">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-304">Win:UInt16</span></span>|<span data-ttu-id="dce36-305">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-305">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretirev1"></a><span data-ttu-id="dce36-306">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="dce36-306">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="dce36-307">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-307">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-308">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-308">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-309">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-309">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-310">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-310">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-311">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-311">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-312">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-312">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-313">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-313">Event</span></span>|<span data-ttu-id="dce36-314">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-314">Event ID</span></span>|<span data-ttu-id="dce36-315">引發的時機</span><span class="sxs-lookup"><span data-stu-id="dce36-315">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="dce36-316">47</span><span class="sxs-lookup"><span data-stu-id="dce36-316">47</span></span>|<span data-ttu-id="dce36-317">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="dce36-317">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="dce36-318">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-318">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-319">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-319">Field name</span></span>|<span data-ttu-id="dce36-320">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-320">Data type</span></span>|<span data-ttu-id="dce36-321">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-321">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-322">Count</span><span class="sxs-lookup"><span data-stu-id="dce36-322">Count</span></span>|<span data-ttu-id="dce36-323">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-323">win:UInt64</span></span>|<span data-ttu-id="dce36-324">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="dce36-324">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="dce36-325">NumRetired</span><span class="sxs-lookup"><span data-stu-id="dce36-325">NumRetired</span></span>|<span data-ttu-id="dce36-326">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-326">win:UInt64</span></span>|<span data-ttu-id="dce36-327">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-327">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="dce36-328">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-328">ClrInstanceID</span></span>|<span data-ttu-id="dce36-329">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-329">Win:UInt16</span></span>|<span data-ttu-id="dce36-330">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-330">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="dce36-331">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="dce36-331">IOThreadTerminate</span></span>  
 <span data-ttu-id="dce36-332">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="dce36-332">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dce36-333">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="dce36-333">Keyword for raising the event</span></span>|<span data-ttu-id="dce36-334">層級</span><span class="sxs-lookup"><span data-stu-id="dce36-334">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dce36-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dce36-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dce36-336">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="dce36-336">Informational (4)</span></span>|  
  
 <span data-ttu-id="dce36-337">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="dce36-337">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dce36-338">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-338">Event</span></span>|<span data-ttu-id="dce36-339">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dce36-339">Event ID</span></span>|<span data-ttu-id="dce36-340">引發的時機</span><span class="sxs-lookup"><span data-stu-id="dce36-340">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="dce36-341">45</span><span class="sxs-lookup"><span data-stu-id="dce36-341">45</span></span>|<span data-ttu-id="dce36-342">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="dce36-342">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="dce36-343">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="dce36-343">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dce36-344">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="dce36-344">Field name</span></span>|<span data-ttu-id="dce36-345">資料類型</span><span class="sxs-lookup"><span data-stu-id="dce36-345">Data type</span></span>|<span data-ttu-id="dce36-346">描述</span><span class="sxs-lookup"><span data-stu-id="dce36-346">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dce36-347">Count</span><span class="sxs-lookup"><span data-stu-id="dce36-347">Count</span></span>|<span data-ttu-id="dce36-348">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-348">win:UInt64</span></span>|<span data-ttu-id="dce36-349">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-349">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="dce36-350">NumRetired</span><span class="sxs-lookup"><span data-stu-id="dce36-350">NumRetired</span></span>|<span data-ttu-id="dce36-351">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="dce36-351">win:UInt64</span></span>|<span data-ttu-id="dce36-352">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dce36-352">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="dce36-353">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dce36-353">ClrInstanceID</span></span>|<span data-ttu-id="dce36-354">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="dce36-354">Win:UInt16</span></span>|<span data-ttu-id="dce36-355">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="dce36-355">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dce36-356">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce36-356">See also</span></span>

- [<span data-ttu-id="dce36-357">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dce36-357">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
