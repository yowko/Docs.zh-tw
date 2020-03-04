---
title: 執行緒集區 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: 249d0607ddd280bcb4e9cf3ef34b28ff8ada3b04
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240489"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="339e6-102">執行緒集區 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="339e6-102">Thread Pool ETW Events</span></span>
<span data-ttu-id="339e6-103">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-103">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="339e6-104">執行緒集區事件可分兩組：</span><span class="sxs-lookup"><span data-stu-id="339e6-104">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="339e6-105">[背景工作執行緒集區事件](#worker-thread-pool-events)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-105">[Worker thread pool events](#worker-thread-pool-events), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="339e6-106">[I/O 執行緒集區事件](#io-thread-events)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-106">[I/O thread pool events](#io-thread-events), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  

## <a name="worker-thread-pool-events"></a><span data-ttu-id="339e6-107">背景工作執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="339e6-107">Worker Thread Pool Events</span></span>
 <span data-ttu-id="339e6-108">這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。</span><span class="sxs-lookup"><span data-stu-id="339e6-108">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="339e6-109">背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。</span><span class="sxs-lookup"><span data-stu-id="339e6-109">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="339e6-110">背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="339e6-110">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="339e6-111">ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="339e6-111">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="339e6-112">下表顯示這些事件的關鍵字與層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-112">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="339e6-113">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="339e6-113">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="339e6-114">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-114">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-115">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-115">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-116">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-116">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-117">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-117">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-118">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-118">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-119">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-119">Event</span></span>|<span data-ttu-id="339e6-120">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-120">Event ID</span></span>|<span data-ttu-id="339e6-121">引發的時機</span><span class="sxs-lookup"><span data-stu-id="339e6-121">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="339e6-122">50</span><span class="sxs-lookup"><span data-stu-id="339e6-122">50</span></span>|<span data-ttu-id="339e6-123">建立背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="339e6-123">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="339e6-124">51</span><span class="sxs-lookup"><span data-stu-id="339e6-124">51</span></span>|<span data-ttu-id="339e6-125">停止背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="339e6-125">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="339e6-126">52</span><span class="sxs-lookup"><span data-stu-id="339e6-126">52</span></span>|<span data-ttu-id="339e6-127">淘汰背景工作執行緒時。</span><span class="sxs-lookup"><span data-stu-id="339e6-127">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="339e6-128">53</span><span class="sxs-lookup"><span data-stu-id="339e6-128">53</span></span>|<span data-ttu-id="339e6-129">淘汰的背景工作執行緒再次作用時。</span><span class="sxs-lookup"><span data-stu-id="339e6-129">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="339e6-130">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-130">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-131">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-131">Field name</span></span>|<span data-ttu-id="339e6-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-132">Data type</span></span>|<span data-ttu-id="339e6-133">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-133">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-134">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="339e6-134">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="339e6-135">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="339e6-135">win:UInt32</span></span>|<span data-ttu-id="339e6-136">可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="339e6-136">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="339e6-137">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="339e6-137">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="339e6-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="339e6-138">win:UInt32</span></span>|<span data-ttu-id="339e6-139">無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。</span><span class="sxs-lookup"><span data-stu-id="339e6-139">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="339e6-140">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-140">ClrInstanceID</span></span>|<span data-ttu-id="339e6-141">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-141">Win:UInt16</span></span>|<span data-ttu-id="339e6-142">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-142">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="339e6-143">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="339e6-143">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="339e6-144">這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="339e6-144">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="339e6-145">背景工作執行緒集區會於內部使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-145">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="339e6-146">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="339e6-146">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="339e6-147">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-147">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-148">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-148">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-149">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-149">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-150">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-150">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-151">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-151">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-152">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-152">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-153">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-153">Event</span></span>|<span data-ttu-id="339e6-154">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-154">Event ID</span></span>|<span data-ttu-id="339e6-155">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-155">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="339e6-156">54</span><span class="sxs-lookup"><span data-stu-id="339e6-156">54</span></span>|<span data-ttu-id="339e6-157">表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。</span><span class="sxs-lookup"><span data-stu-id="339e6-157">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="339e6-158">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-158">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-159">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-159">Field name</span></span>|<span data-ttu-id="339e6-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-160">Data type</span></span>|<span data-ttu-id="339e6-161">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-161">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-162">Throughput</span><span class="sxs-lookup"><span data-stu-id="339e6-162">Throughput</span></span>|<span data-ttu-id="339e6-163">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-163">win:Double</span></span>|<span data-ttu-id="339e6-164">每個時間單位完成的數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-164">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="339e6-165">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-165">ClrInstanceID</span></span>|<span data-ttu-id="339e6-166">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-166">Win:UInt16</span></span>|<span data-ttu-id="339e6-167">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-167">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="339e6-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="339e6-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="339e6-169">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-169">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-170">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-170">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-171">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-171">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-172">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-172">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-173">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-173">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-174">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-174">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-175">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-175">Event</span></span>|<span data-ttu-id="339e6-176">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-176">Event ID</span></span>|<span data-ttu-id="339e6-177">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-177">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="339e6-178">55</span><span class="sxs-lookup"><span data-stu-id="339e6-178">55</span></span>|<span data-ttu-id="339e6-179">當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。</span><span class="sxs-lookup"><span data-stu-id="339e6-179">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="339e6-180">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-180">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-181">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-181">Field name</span></span>|<span data-ttu-id="339e6-182">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-182">Data type</span></span>|<span data-ttu-id="339e6-183">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-183">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-184">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="339e6-184">AverageThroughput</span></span>|<span data-ttu-id="339e6-185">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-185">win:Double</span></span>|<span data-ttu-id="339e6-186">度量範例的平均輸送量。</span><span class="sxs-lookup"><span data-stu-id="339e6-186">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="339e6-187">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="339e6-187">NewWorkerThreadCount</span></span>|<span data-ttu-id="339e6-188">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="339e6-188">win:UInt32</span></span>|<span data-ttu-id="339e6-189">作用中背景工作執行緒的新數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-189">New number of active worker threads.</span></span>|  
|<span data-ttu-id="339e6-190">原因</span><span class="sxs-lookup"><span data-stu-id="339e6-190">Reason</span></span>|<span data-ttu-id="339e6-191">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="339e6-191">win:UInt32</span></span>|<span data-ttu-id="339e6-192">調整的原因。</span><span class="sxs-lookup"><span data-stu-id="339e6-192">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="339e6-193">0x00 - 熱身。</span><span class="sxs-lookup"><span data-stu-id="339e6-193">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="339e6-194">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="339e6-194">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="339e6-195">0x02 - 隨機移動。</span><span class="sxs-lookup"><span data-stu-id="339e6-195">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="339e6-196">0x03 - 攀登移動。</span><span class="sxs-lookup"><span data-stu-id="339e6-196">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="339e6-197">0x04 - 變更點。</span><span class="sxs-lookup"><span data-stu-id="339e6-197">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="339e6-198">0x05 - 穩定。</span><span class="sxs-lookup"><span data-stu-id="339e6-198">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="339e6-199">0x06 - 資源不足。</span><span class="sxs-lookup"><span data-stu-id="339e6-199">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="339e6-200">0x07 - 執行緒逾時。</span><span class="sxs-lookup"><span data-stu-id="339e6-200">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="339e6-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-201">ClrInstanceID</span></span>|<span data-ttu-id="339e6-202">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-202">Win:UInt16</span></span>|<span data-ttu-id="339e6-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="339e6-204">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="339e6-204">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="339e6-205">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-205">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-206">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-206">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-207">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-207">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-208">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-208">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-209">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-209">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-210">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-210">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-211">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-211">Event</span></span>|<span data-ttu-id="339e6-212">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-212">Event ID</span></span>|<span data-ttu-id="339e6-213">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-213">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="339e6-214">56</span><span class="sxs-lookup"><span data-stu-id="339e6-214">56</span></span>|<span data-ttu-id="339e6-215">收集執行緒集區的資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-215">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="339e6-216">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-216">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-217">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-217">Field name</span></span>|<span data-ttu-id="339e6-218">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-218">Data type</span></span>|<span data-ttu-id="339e6-219">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-219">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-220">Duration</span><span class="sxs-lookup"><span data-stu-id="339e6-220">Duration</span></span>|<span data-ttu-id="339e6-221">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-221">win:Double</span></span>|<span data-ttu-id="339e6-222">收集這些統計資料期間的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="339e6-222">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="339e6-223">Throughput</span><span class="sxs-lookup"><span data-stu-id="339e6-223">Throughput</span></span>|<span data-ttu-id="339e6-224">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-224">win:Double</span></span>|<span data-ttu-id="339e6-225">在這段間隔期間，每秒完成的平均數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-225">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="339e6-226">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="339e6-226">ThreadWave</span></span>|<span data-ttu-id="339e6-227">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-227">win:Double</span></span>|<span data-ttu-id="339e6-228">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="339e6-228">Reserved for internal use.</span></span>|  
|<span data-ttu-id="339e6-229">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="339e6-229">ThroughputWave</span></span>|<span data-ttu-id="339e6-230">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-230">win:Double</span></span>|<span data-ttu-id="339e6-231">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="339e6-231">Reserved for internal use.</span></span>|  
|<span data-ttu-id="339e6-232">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="339e6-232">ThroughputErrorEstimate</span></span>|<span data-ttu-id="339e6-233">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-233">win:Double</span></span>|<span data-ttu-id="339e6-234">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="339e6-234">Reserved for internal use.</span></span>|  
|<span data-ttu-id="339e6-235">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="339e6-235">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="339e6-236">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-236">win:Double</span></span>|<span data-ttu-id="339e6-237">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="339e6-237">Reserved for internal use.</span></span>|  
|<span data-ttu-id="339e6-238">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="339e6-238">ThroughputRatio</span></span>|<span data-ttu-id="339e6-239">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-239">win:Double</span></span>|<span data-ttu-id="339e6-240">在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。</span><span class="sxs-lookup"><span data-stu-id="339e6-240">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="339e6-241">信賴度</span><span class="sxs-lookup"><span data-stu-id="339e6-241">Confidence</span></span>|<span data-ttu-id="339e6-242">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-242">win:Double</span></span>|<span data-ttu-id="339e6-243">ThroughputRatio 欄位有效性的度量。</span><span class="sxs-lookup"><span data-stu-id="339e6-243">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="339e6-244">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="339e6-244">NewcontrolSetting</span></span>|<span data-ttu-id="339e6-245">win:Double</span><span class="sxs-lookup"><span data-stu-id="339e6-245">win:Double</span></span>|<span data-ttu-id="339e6-246">作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。</span><span class="sxs-lookup"><span data-stu-id="339e6-246">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="339e6-247">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="339e6-247">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="339e6-248">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-248">Win:UInt16</span></span>|<span data-ttu-id="339e6-249">作用中執行緒計數未來變化的範圍。</span><span class="sxs-lookup"><span data-stu-id="339e6-249">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="339e6-250">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-250">ClrInstanceID</span></span>|<span data-ttu-id="339e6-251">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-251">Win:UInt16</span></span>|<span data-ttu-id="339e6-252">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-252">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="io-thread-events"></a><span data-ttu-id="339e6-253">I/O 執行緒事件</span><span class="sxs-lookup"><span data-stu-id="339e6-253">I/O Thread Events</span></span>  
 <span data-ttu-id="339e6-254">會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。</span><span class="sxs-lookup"><span data-stu-id="339e6-254">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreate_v1"></a><span data-ttu-id="339e6-255">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="339e6-255">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="339e6-256">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-256">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-257">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-257">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-258">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-258">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-259">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-259">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-260">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-260">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-261">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-261">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-262">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-262">Event</span></span>|<span data-ttu-id="339e6-263">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-263">Event ID</span></span>|<span data-ttu-id="339e6-264">引發的時機</span><span class="sxs-lookup"><span data-stu-id="339e6-264">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="339e6-265">44</span><span class="sxs-lookup"><span data-stu-id="339e6-265">44</span></span>|<span data-ttu-id="339e6-266">在執行緒集區中建立 I/O 執行緒時。</span><span class="sxs-lookup"><span data-stu-id="339e6-266">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="339e6-267">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-267">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-268">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-268">Field name</span></span>|<span data-ttu-id="339e6-269">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-269">Data type</span></span>|<span data-ttu-id="339e6-270">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-270">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-271">Count</span><span class="sxs-lookup"><span data-stu-id="339e6-271">Count</span></span>|<span data-ttu-id="339e6-272">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-272">win:UInt64</span></span>|<span data-ttu-id="339e6-273">I/O 執行緒的數目，其包含新建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="339e6-273">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="339e6-274">NumRetired</span><span class="sxs-lookup"><span data-stu-id="339e6-274">NumRetired</span></span>|<span data-ttu-id="339e6-275">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-275">win:UInt64</span></span>|<span data-ttu-id="339e6-276">已淘汰之背景工作執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-276">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="339e6-277">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-277">ClrInstanceID</span></span>|<span data-ttu-id="339e6-278">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-278">Win:UInt16</span></span>|<span data-ttu-id="339e6-279">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-279">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretire_v1"></a><span data-ttu-id="339e6-280">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="339e6-280">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="339e6-281">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-281">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-282">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-282">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-283">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-283">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-284">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-284">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-285">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-285">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-286">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-286">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-287">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-287">Event</span></span>|<span data-ttu-id="339e6-288">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-288">Event ID</span></span>|<span data-ttu-id="339e6-289">引發的時機</span><span class="sxs-lookup"><span data-stu-id="339e6-289">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="339e6-290">46</span><span class="sxs-lookup"><span data-stu-id="339e6-290">46</span></span>|<span data-ttu-id="339e6-291">當 I/O 執行緒變成淘汰候選時。</span><span class="sxs-lookup"><span data-stu-id="339e6-291">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="339e6-292">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-292">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-293">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-293">Field name</span></span>|<span data-ttu-id="339e6-294">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-294">Data type</span></span>|<span data-ttu-id="339e6-295">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-295">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-296">Count</span><span class="sxs-lookup"><span data-stu-id="339e6-296">Count</span></span>|<span data-ttu-id="339e6-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-297">win:UInt64</span></span>|<span data-ttu-id="339e6-298">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-298">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="339e6-299">NumRetired</span><span class="sxs-lookup"><span data-stu-id="339e6-299">NumRetired</span></span>|<span data-ttu-id="339e6-300">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-300">win:UInt64</span></span>|<span data-ttu-id="339e6-301">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-301">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="339e6-302">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-302">ClrInstanceID</span></span>|<span data-ttu-id="339e6-303">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-303">Win:UInt16</span></span>|<span data-ttu-id="339e6-304">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-304">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretire_v1"></a><span data-ttu-id="339e6-305">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="339e6-305">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="339e6-306">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-307">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-307">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-308">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-309">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-309">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-310">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-311">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-312">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-312">Event</span></span>|<span data-ttu-id="339e6-313">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-313">Event ID</span></span>|<span data-ttu-id="339e6-314">引發的時機</span><span class="sxs-lookup"><span data-stu-id="339e6-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="339e6-315">47</span><span class="sxs-lookup"><span data-stu-id="339e6-315">47</span></span>|<span data-ttu-id="339e6-316">因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。</span><span class="sxs-lookup"><span data-stu-id="339e6-316">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="339e6-317">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-317">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-318">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-318">Field name</span></span>|<span data-ttu-id="339e6-319">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-319">Data type</span></span>|<span data-ttu-id="339e6-320">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-320">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-321">Count</span><span class="sxs-lookup"><span data-stu-id="339e6-321">Count</span></span>|<span data-ttu-id="339e6-322">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-322">win:UInt64</span></span>|<span data-ttu-id="339e6-323">執行緒集區中的 I/O 執行緒數目，包含此執行緒。</span><span class="sxs-lookup"><span data-stu-id="339e6-323">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="339e6-324">NumRetired</span><span class="sxs-lookup"><span data-stu-id="339e6-324">NumRetired</span></span>|<span data-ttu-id="339e6-325">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-325">win:UInt64</span></span>|<span data-ttu-id="339e6-326">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-326">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="339e6-327">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-327">ClrInstanceID</span></span>|<span data-ttu-id="339e6-328">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-328">Win:UInt16</span></span>|<span data-ttu-id="339e6-329">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-329">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="339e6-330">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="339e6-330">IOThreadTerminate</span></span>  
 <span data-ttu-id="339e6-331">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="339e6-331">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="339e6-332">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="339e6-332">Keyword for raising the event</span></span>|<span data-ttu-id="339e6-333">層級</span><span class="sxs-lookup"><span data-stu-id="339e6-333">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="339e6-334">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="339e6-334">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="339e6-335">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="339e6-335">Informational (4)</span></span>|  
  
 <span data-ttu-id="339e6-336">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="339e6-336">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="339e6-337">事件</span><span class="sxs-lookup"><span data-stu-id="339e6-337">Event</span></span>|<span data-ttu-id="339e6-338">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="339e6-338">Event ID</span></span>|<span data-ttu-id="339e6-339">引發的時機</span><span class="sxs-lookup"><span data-stu-id="339e6-339">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="339e6-340">45</span><span class="sxs-lookup"><span data-stu-id="339e6-340">45</span></span>|<span data-ttu-id="339e6-341">執行緒集區中的 i/o 執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="339e6-341">An I/O thread is terminated in the thread pool.</span></span>|  
  
 <span data-ttu-id="339e6-342">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="339e6-342">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="339e6-343">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="339e6-343">Field name</span></span>|<span data-ttu-id="339e6-344">資料類型</span><span class="sxs-lookup"><span data-stu-id="339e6-344">Data type</span></span>|<span data-ttu-id="339e6-345">描述</span><span class="sxs-lookup"><span data-stu-id="339e6-345">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="339e6-346">Count</span><span class="sxs-lookup"><span data-stu-id="339e6-346">Count</span></span>|<span data-ttu-id="339e6-347">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-347">win:UInt64</span></span>|<span data-ttu-id="339e6-348">執行緒集區中剩餘的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-348">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="339e6-349">NumRetired</span><span class="sxs-lookup"><span data-stu-id="339e6-349">NumRetired</span></span>|<span data-ttu-id="339e6-350">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="339e6-350">win:UInt64</span></span>|<span data-ttu-id="339e6-351">已淘汰的 I/O 執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="339e6-351">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="339e6-352">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="339e6-352">ClrInstanceID</span></span>|<span data-ttu-id="339e6-353">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="339e6-353">Win:UInt16</span></span>|<span data-ttu-id="339e6-354">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="339e6-354">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="339e6-355">另請參閱</span><span class="sxs-lookup"><span data-stu-id="339e6-355">See also</span></span>

- [<span data-ttu-id="339e6-356">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="339e6-356">CLR ETW Events</span></span>](clr-etw-events.md)
