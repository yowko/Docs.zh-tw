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
ms.openlocfilehash: ff0ff35f42e20725cab49afd971523aabda866c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547789"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="f00a5-102">ICorProfilerInfo2::DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="f00a5-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="f00a5-103">引導堆疊上指定執行緒的 managed 框架，並透過回呼將資訊傳送至分析工具。</span><span class="sxs-lookup"><span data-stu-id="f00a5-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f00a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f00a5-104">Syntax</span></span>  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f00a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="f00a5-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="f00a5-106">在目標執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f00a5-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="f00a5-107">傳遞 null 時 `thread` ，會產生目前線程的快照。</span><span class="sxs-lookup"><span data-stu-id="f00a5-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="f00a5-108">如果傳遞的是 `ThreadID` 不同的執行緒，則 common language runtime (CLR) 會暫停該執行緒、執行快照集，然後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="f00a5-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="f00a5-109">在 [StackSnapshotCallback](stacksnapshotcallback-function.md) 方法的執行指標，由 CLR 呼叫，以提供分析工具每個 managed 框架的資訊，以及每次執行非受控框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f00a5-109">[in] A pointer to the implementation of the [StackSnapshotCallback](stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="f00a5-110">`StackSnapshotCallback`方法是由分析工具寫入器所執行。</span><span class="sxs-lookup"><span data-stu-id="f00a5-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="f00a5-111">在 [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) 列舉值，這個值會指定要針對每個框架傳回的資料量 `StackSnapshotCallback` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="f00a5-112">在用戶端資料的指標，會直接傳遞至 `StackSnapshotCallback` 回呼函數。</span><span class="sxs-lookup"><span data-stu-id="f00a5-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="f00a5-113">在Win32 結構的指標 `CONTEXT` ，用來植入堆疊的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f00a5-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="f00a5-114">Win32 `CONTEXT` 結構包含 cpu 暫存器的值，並代表特定時間點的 cpu 狀態。</span><span class="sxs-lookup"><span data-stu-id="f00a5-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="f00a5-115">如果堆疊的頂端是未受管理的 helper 程式碼，則種子可協助 CLR 判斷開始堆疊的位置：否則會忽略種子。</span><span class="sxs-lookup"><span data-stu-id="f00a5-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="f00a5-116">必須提供種子給非同步逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f00a5-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="f00a5-117">如果您執行的是同步的逐步解說，則不需要任何種子。</span><span class="sxs-lookup"><span data-stu-id="f00a5-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="f00a5-118">`context`只有在參數中傳遞 COR_PRF_SNAPSHOT_CONTEXT 旗標時，參數才有效 `infoFlags` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f00a5-119">在 `CONTEXT` 參數所參考之結構的大小 `context` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f00a5-120">備註</span><span class="sxs-lookup"><span data-stu-id="f00a5-120">Remarks</span></span>  
 <span data-ttu-id="f00a5-121">傳遞 null 以 `thread` 產生目前線程的快照集。</span><span class="sxs-lookup"><span data-stu-id="f00a5-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="f00a5-122">只有在目標執行緒暫止時，才可以建立其他執行緒的快照集。</span><span class="sxs-lookup"><span data-stu-id="f00a5-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="f00a5-123">當分析工具想要引導堆疊時，它會呼叫 `DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="f00a5-124">在 CLR 從該呼叫傳回之前，會呼叫您 `StackSnapshotCallback` 數次，每個 managed 框架 (或執行堆疊上) 非受控框架。</span><span class="sxs-lookup"><span data-stu-id="f00a5-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="f00a5-125">當遇到非受控框架時，您必須自行引導。</span><span class="sxs-lookup"><span data-stu-id="f00a5-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="f00a5-126">堆疊的進行順序，就是將框架推送至堆疊的方式：分葉 (最後推入) 框架，主要 (第一次推送) 框架。</span><span class="sxs-lookup"><span data-stu-id="f00a5-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="f00a5-127">如需如何設計程式碼剖析工具以逐步執行 managed 堆疊的詳細資訊，請參閱 [.NET Framework 2.0：基本版和更高範圍中的 Profiler 堆疊逐步](/previous-versions/dotnet/articles/bb264782(v=msdn.10))解說。</span><span class="sxs-lookup"><span data-stu-id="f00a5-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="f00a5-128">堆疊逐步解說可以是同步或非同步，如下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="f00a5-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="f00a5-129">同步堆疊逐步解說</span><span class="sxs-lookup"><span data-stu-id="f00a5-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="f00a5-130">同步堆疊的逐步解說牽涉到目前線程的堆疊，以回應回呼。</span><span class="sxs-lookup"><span data-stu-id="f00a5-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="f00a5-131">它不需要植入或暫停。</span><span class="sxs-lookup"><span data-stu-id="f00a5-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="f00a5-132">當您呼叫其中一個分析工具的 ICorProfilerCallback (或[ICorProfilerCallback2](icorprofilercallback2-interface.md)) 方法時，您會呼叫以逐步執行目前線程的堆疊，以回應 CLR 呼叫其中一個 Profiler 的[ICorProfilerCallback](icorprofilercallback-interface.md) `DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](icorprofilercallback-interface.md) (or [ICorProfilerCallback2](icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="f00a5-133">當您想要查看堆疊在 [ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)之類的通知時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="f00a5-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="f00a5-134">您只需要在 `DoStackSnapshot` 方法中呼叫 `ICorProfilerCallback` ， `context` 並在和參數中傳遞 null `thread` 。</span><span class="sxs-lookup"><span data-stu-id="f00a5-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="f00a5-135">非同步堆疊逐步解說</span><span class="sxs-lookup"><span data-stu-id="f00a5-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="f00a5-136">非同步堆疊的逐步解說需要離開不同執行緒的堆疊，或將目前線程的堆疊移至目前線程的堆疊，而不是回應回呼，但藉由劫持目前線程的指令指標。</span><span class="sxs-lookup"><span data-stu-id="f00a5-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="f00a5-137">如果堆疊的頂端是非受控程式碼，而不是平台叫用的一部分 (PInvoke) 或 COM 呼叫，但是 CLR 本身的 helper 程式碼，則非同步逐步解說需要種子。</span><span class="sxs-lookup"><span data-stu-id="f00a5-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="f00a5-138">例如，執行即時 (JIT) 編譯或垃圾收集的程式碼是 helper 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f00a5-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="f00a5-139">您可以直接暫停目標執行緒，並自行進行堆疊來取得種子，直到您找到最上層的 managed 框架為止。</span><span class="sxs-lookup"><span data-stu-id="f00a5-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="f00a5-140">在目標執行緒暫止之後，取得目標執行緒的目前註冊內容。</span><span class="sxs-lookup"><span data-stu-id="f00a5-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="f00a5-141">接下來，藉由呼叫 [ICorProfilerInfo：： GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) ，判斷註冊內容是否指向非受控程式碼，如果它傳回 `FunctionID` 等於零，則框架為非受控碼。</span><span class="sxs-lookup"><span data-stu-id="f00a5-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="f00a5-142">現在，請先進入堆疊，直到到達第一個 managed 框架，然後根據該框架的註冊內容來計算種子內容。</span><span class="sxs-lookup"><span data-stu-id="f00a5-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="f00a5-143">`DoStackSnapshot`使用您的種子內容來呼叫，以開始非同步堆疊的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f00a5-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="f00a5-144">如果您未提供種子， `DoStackSnapshot` 可能會略過堆疊頂端的 managed 框架，因此會提供您不完整的堆疊逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f00a5-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="f00a5-145">如果您提供種子，它必須指向 JIT 編譯或原生映射產生器 ( # A0) 產生的程式碼;否則，會傳回 `DoStackSnapshot` 失敗碼 CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。</span><span class="sxs-lookup"><span data-stu-id="f00a5-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="f00a5-146">除非您遵循下列指導方針，否則非同步堆疊的逐步解說很容易就會造成鎖死或存取違規：</span><span class="sxs-lookup"><span data-stu-id="f00a5-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
- <span data-ttu-id="f00a5-147">當您直接暫停執行緒時，請記住，只有從未執行 managed 程式碼的執行緒才能暫停另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="f00a5-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
- <span data-ttu-id="f00a5-148">一律在 [ICorProfilerCallback：： ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) 回呼中封鎖，直到該執行緒的堆疊逐步完成為止。</span><span class="sxs-lookup"><span data-stu-id="f00a5-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
- <span data-ttu-id="f00a5-149">當分析工具呼叫可觸發垃圾收集的 CLR 函式時，請勿保留鎖定。</span><span class="sxs-lookup"><span data-stu-id="f00a5-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="f00a5-150">也就是，如果主控執行緒可能進行呼叫來觸發垃圾收集，就不會保留鎖定。</span><span class="sxs-lookup"><span data-stu-id="f00a5-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="f00a5-151">如果您從分析工具所建立的執行緒呼叫， `DoStackSnapshot` 讓您可以逐步解說不同的目標執行緒，也會有鎖死的風險。</span><span class="sxs-lookup"><span data-stu-id="f00a5-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="f00a5-152">當您第一次建立的執行緒進入特定 `ICorProfilerInfo*` 方法 (包括 `DoStackSnapshot`) 時，clr 會在該執行緒上執行每個執行緒的 clr 特定初始化。</span><span class="sxs-lookup"><span data-stu-id="f00a5-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="f00a5-153">如果您的分析工具已暫止您嘗試進行堆疊的目標執行緒，而且如果該目標執行緒擁有執行此每個執行緒初始化所需的鎖定，就會發生鎖死。</span><span class="sxs-lookup"><span data-stu-id="f00a5-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="f00a5-154">若要避免這個鎖死，請從分析工具建立的執行緒進行初始呼叫 `DoStackSnapshot` ，以逐步執行個別的目標執行緒，但不要先暫停目標執行緒。</span><span class="sxs-lookup"><span data-stu-id="f00a5-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="f00a5-155">這個初始呼叫可確保每個執行緒的初始化都能在沒有鎖死的情況下完成。</span><span class="sxs-lookup"><span data-stu-id="f00a5-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="f00a5-156">如果 `DoStackSnapshot` 成功並報告至少一個框架，則在該時間點之後，該分析工具建立的執行緒將可安全地暫停任何目標執行緒，並呼叫 `DoStackSnapshot` 以取得該目標執行緒的堆疊。</span><span class="sxs-lookup"><span data-stu-id="f00a5-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f00a5-157">需求</span><span class="sxs-lookup"><span data-stu-id="f00a5-157">Requirements</span></span>  
 <span data-ttu-id="f00a5-158">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f00a5-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f00a5-159">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f00a5-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f00a5-160">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f00a5-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f00a5-161">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f00a5-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f00a5-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f00a5-162">See also</span></span>

- [<span data-ttu-id="f00a5-163">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f00a5-163">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f00a5-164">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="f00a5-164">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
