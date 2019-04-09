---
title: ICorProfilerInfo2::DoStackSnapshot 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ef215253ca02048a5a3fc2c7c682823233929f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108078"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="137b9-102">ICorProfilerInfo2::DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="137b9-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="137b9-103">引導指定的執行緒的堆疊上的 managed 的框架，並將資訊傳送到透過回呼程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="137b9-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="137b9-104">Syntax</span></span>  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="137b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="137b9-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="137b9-106">[in]目標執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="137b9-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="137b9-107">傳遞 null`thread`會產生目前執行緒的快照集。</span><span class="sxs-lookup"><span data-stu-id="137b9-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="137b9-108">如果`ThreadID`的傳遞不同的執行緒，common language runtime (CLR) 該執行緒會暫止、 執行快照集，並繼續。</span><span class="sxs-lookup"><span data-stu-id="137b9-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="137b9-109">[in]實作的指標[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)方法，由 CLR 分析工具提供有關每個 managed 的框架和未受管理的畫面格的每次執行所呼叫。</span><span class="sxs-lookup"><span data-stu-id="137b9-109">[in] A pointer to the implementation of the [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="137b9-110">`StackSnapshotCallback`方法藉由分析工具寫入器。</span><span class="sxs-lookup"><span data-stu-id="137b9-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="137b9-111">[in]值為[COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)列舉，指定要傳遞回每個框架的資料數量`StackSnapshotCallback`。</span><span class="sxs-lookup"><span data-stu-id="137b9-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="137b9-112">[in]用戶端資料指標，直接傳遞至`StackSnapshotCallback`回呼函式。</span><span class="sxs-lookup"><span data-stu-id="137b9-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="137b9-113">[in]Win32 指標`CONTEXT`結構，用來植入堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="137b9-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="137b9-114">Win32`CONTEXT`結構包含 CPU 暫存器的值，而且在特定時間點表示 CPU 的狀態。</span><span class="sxs-lookup"><span data-stu-id="137b9-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="137b9-115">之種子可協助決定在何處開始堆疊查核行程，堆疊的頂端時未受管理的協助程式程式碼; CLR否則會忽略種子。</span><span class="sxs-lookup"><span data-stu-id="137b9-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="137b9-116">識別值種子必須提供給非同步查核行程。</span><span class="sxs-lookup"><span data-stu-id="137b9-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="137b9-117">如果您要進行同步的查核行程，任何初始值不是必要的。</span><span class="sxs-lookup"><span data-stu-id="137b9-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="137b9-118">`context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`infoFlags`參數。</span><span class="sxs-lookup"><span data-stu-id="137b9-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="137b9-119">[in]大小`CONTEXT`結構，也就由參考`context`參數。</span><span class="sxs-lookup"><span data-stu-id="137b9-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137b9-120">備註</span><span class="sxs-lookup"><span data-stu-id="137b9-120">Remarks</span></span>  
 <span data-ttu-id="137b9-121">傳遞 null`thread`會產生目前執行緒的快照集。</span><span class="sxs-lookup"><span data-stu-id="137b9-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="137b9-122">只有當目標執行緒會暫停時，可以建立快照的其他執行緒。</span><span class="sxs-lookup"><span data-stu-id="137b9-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="137b9-123">當分析工具想要堆疊查核行程時，它會呼叫`DoStackSnapshot`。</span><span class="sxs-lookup"><span data-stu-id="137b9-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="137b9-124">CLR 會從該呼叫傳回之前，它會呼叫您`StackSnapshotCallback`好幾次，一次針對每個 managed 框架 （或執行未受管理的畫面格數） 堆疊上。</span><span class="sxs-lookup"><span data-stu-id="137b9-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="137b9-125">當遇到未受管理的畫面格時，您必須逐步教他們自己。</span><span class="sxs-lookup"><span data-stu-id="137b9-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="137b9-126">堆疊查核行程中的順序就是畫面格已推送至堆疊的方式相反︰ 上次分葉 （最後一個推入） 的畫面格第一次的主要 （第一個推入） 框架。</span><span class="sxs-lookup"><span data-stu-id="137b9-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="137b9-127">如需如何進行程式設計以查核 managed 的堆疊的詳細資訊，請參閱[Profiler 堆疊查核行程.NET Framework 2.0 中：基礎與進階](https://go.microsoft.com/fwlink/?LinkId=73638)。</span><span class="sxs-lookup"><span data-stu-id="137b9-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](https://go.microsoft.com/fwlink/?LinkId=73638).</span></span>  
  
 <span data-ttu-id="137b9-128">堆疊查核行程可以是同步或非同步，如下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="137b9-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="137b9-129">同步的堆疊查核行程</span><span class="sxs-lookup"><span data-stu-id="137b9-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="137b9-130">同步的堆疊查核行程牽涉到目前執行緒的堆疊查核回呼回應。</span><span class="sxs-lookup"><span data-stu-id="137b9-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="137b9-131">它不需要執行或暫止。</span><span class="sxs-lookup"><span data-stu-id="137b9-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="137b9-132">您進行同步時，呼叫以回應呼叫您的分析工具的其中一個 CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 方法，您可以呼叫`DoStackSnapshot`至的堆疊查核行程目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="137b9-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (or [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="137b9-133">這是很有用，當您想要查看堆疊樣貌通知在這類[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。</span><span class="sxs-lookup"><span data-stu-id="137b9-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="137b9-134">您只需要呼叫`DoStackSnapshot`內您`ICorProfilerCallback`方法，傳遞 null`context`和`thread`參數。</span><span class="sxs-lookup"><span data-stu-id="137b9-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="137b9-135">非同步的堆疊查核行程</span><span class="sxs-lookup"><span data-stu-id="137b9-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="137b9-136">的非同步堆疊查核行程需要不同的執行緒的堆疊查核或目前執行緒的堆疊查核不在回應回呼，而是由攔截目前執行緒的指令指標。</span><span class="sxs-lookup"><span data-stu-id="137b9-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="137b9-137">非同步查核行程要求的種子，如果堆疊的頂端是不是平台一部分的 unmanaged 程式碼叫用 (PInvoke) 或 COM 呼叫，但 CLR 本身中的協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="137b9-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="137b9-138">比方說，在 just-in-time (JIT) 編譯或記憶體回收收集的程式碼是協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="137b9-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="137b9-139">您取得種子透過直接暫停目標執行緒，並逐一查看其堆疊自行，直到您找到的最上層 managed 框架。</span><span class="sxs-lookup"><span data-stu-id="137b9-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="137b9-140">目標執行緒暫止之後，取得目標執行緒目前的暫存器內容。</span><span class="sxs-lookup"><span data-stu-id="137b9-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="137b9-141">接下來，判斷是否註冊內容指向 unmanaged 程式碼藉由呼叫[icorprofilerinfo:: Getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — 如果它傳回`FunctionID`等於零，框架的 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="137b9-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="137b9-142">現在，查看堆疊，直到到達第一個 managed 的框架，然後計算該範圍內的暫存器內容為基礎的識別值種子內容。</span><span class="sxs-lookup"><span data-stu-id="137b9-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="137b9-143">呼叫`DoStackSnapshot`與您的識別值種子內容，開始非同步的堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="137b9-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="137b9-144">如果您未提供的種子，`DoStackSnapshot`可能略過的受控的框架在堆疊的頂端，並因此，所得到的不完整的堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="137b9-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="137b9-145">如果您提供的種子，它必須指向 JIT 編譯或原生映像產生器 (Ngen.exe)-產生的程式碼;否則，`DoStackSnapshot`傳回失敗碼，而 CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。</span><span class="sxs-lookup"><span data-stu-id="137b9-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="137b9-146">非同步的堆疊查核行程可以輕易地會造成死結 （deadlock），或存取違規，除非您遵循這些指導方針：</span><span class="sxs-lookup"><span data-stu-id="137b9-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="137b9-147">當您直接暫停執行緒時，請記得從未執行 managed 程式碼的執行緒可以暫停另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="137b9-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
-   <span data-ttu-id="137b9-148">會一直封鎖您[icorprofilercallback:: Threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)回呼，直到該執行緒的堆疊查核行程完成為止。</span><span class="sxs-lookup"><span data-stu-id="137b9-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
-   <span data-ttu-id="137b9-149">請勿保留鎖定，而您的程式碼剖析工具呼叫可以觸發記憶體回收的 CLR 函式。</span><span class="sxs-lookup"><span data-stu-id="137b9-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="137b9-150">也就是說，如果擁有的執行緒可能會觸發記憶體回收的呼叫請勿保留鎖定。</span><span class="sxs-lookup"><span data-stu-id="137b9-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="137b9-151">另外還有死結的風險。 如果您呼叫`DoStackSnapshot`從您的程式碼剖析工具，讓您可以將個別的目標執行緒的堆疊查核行程，已建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="137b9-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="137b9-152">第一次在您建立的執行緒進入特定`ICorProfilerInfo*`方法 (包括`DoStackSnapshot`)，CLR 會執行每個執行緒，在該執行緒上的 CLR 特定的初始化。</span><span class="sxs-lookup"><span data-stu-id="137b9-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="137b9-153">如果您的分析工具已暫止的目標執行緒嘗試查核行程的堆疊，而且該目標執行緒發生擁有鎖定所需執行這項每個執行緒初始化，則會發生死結。</span><span class="sxs-lookup"><span data-stu-id="137b9-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="137b9-154">若要避免這個死結，讓初始呼叫`DoStackSnapshot`個別目標執行緒，但並不會擱置目標執行緒先從引導您程式碼剖析工具建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="137b9-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="137b9-155">此初始呼叫可確保每個執行緒初始化可以完成不包含死結。</span><span class="sxs-lookup"><span data-stu-id="137b9-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="137b9-156">如果`DoStackSnapshot`成功，而且至少一個框架時，會報告該動作之後，將會暫止任何目標執行緒和呼叫該程式碼剖析工具建立執行緒安全`DoStackSnapshot`到該目標執行緒的堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="137b9-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137b9-157">需求</span><span class="sxs-lookup"><span data-stu-id="137b9-157">Requirements</span></span>  
 <span data-ttu-id="137b9-158">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="137b9-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137b9-159">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="137b9-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="137b9-160">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="137b9-160">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="137b9-161">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="137b9-161">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="137b9-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="137b9-162">See also</span></span>

- [<span data-ttu-id="137b9-163">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="137b9-163">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="137b9-164">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="137b9-164">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
