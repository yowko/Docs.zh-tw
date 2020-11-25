---
title: ICorProfilerCallback2 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: 597a3dfecd42e206c98974093fa2417eba570f6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729460"
---
# <a name="icorprofilercallback2-interface"></a><span data-ttu-id="a721b-102">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="a721b-102">ICorProfilerCallback2 Interface</span></span>

<span data-ttu-id="a721b-103">提供 common language runtime (CLR) 所使用的方法，以在分析工具已訂閱的事件發生時通知程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="a721b-103">Provides methods that are used by the common language runtime (CLR) to notify a code profiler when the events to which the profiler has subscribed occur.</span></span> <span data-ttu-id="a721b-104">`ICorProfilerCallback2`介面是[ICorProfilerCallback](icorprofilercallback-interface.md)介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="a721b-104">The `ICorProfilerCallback2` interface is an extension of the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span> <span data-ttu-id="a721b-105">也就是說，它會提供 .NET Framework 2.0 版中引進的新回呼。</span><span class="sxs-lookup"><span data-stu-id="a721b-105">That is, it provides new callbacks introduced in the .NET Framework version 2.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a721b-106">每個方法的執行都必須傳回一個 HRESULT，其值為「成功」或「失敗時 E_FAIL 的 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a721b-106">Each method implementation must return an HRESULT having a value of S_OK on success or E_FAIL on failure.</span></span> <span data-ttu-id="a721b-107">目前，CLR 會忽略每個回呼所傳回的 HRESULT，但 [ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)除外。</span><span class="sxs-lookup"><span data-stu-id="a721b-107">Currently, the CLR ignores the HRESULT that is returned by each callback except [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a721b-108">方法</span><span class="sxs-lookup"><span data-stu-id="a721b-108">Methods</span></span>  
  
|<span data-ttu-id="a721b-109">方法</span><span class="sxs-lookup"><span data-stu-id="a721b-109">Method</span></span>|<span data-ttu-id="a721b-110">描述</span><span class="sxs-lookup"><span data-stu-id="a721b-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a721b-111">FinalizeableObjectQueued 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-111">FinalizeableObjectQueued Method</span></span>](icorprofilercallback2-finalizeableobjectqueued-method.md)|<span data-ttu-id="a721b-112">通知程式碼分析工具，具有完成項的物件已排入完成項執行緒，以執行其 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="a721b-112">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>|  
|[<span data-ttu-id="a721b-113">GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-113">GarbageCollectionFinished Method</span></span>](icorprofilercallback2-garbagecollectionfinished-method.md)|<span data-ttu-id="a721b-114">通知分析工具，已完成垃圾收集，並對其發出所有垃圾收集回呼。</span><span class="sxs-lookup"><span data-stu-id="a721b-114">Notifies the profiler that a garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>|  
|[<span data-ttu-id="a721b-115">GarbageCollectionStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-115">GarbageCollectionStarted Method</span></span>](icorprofilercallback2-garbagecollectionstarted-method.md)|<span data-ttu-id="a721b-116">通知程式碼分析工具已啟動垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a721b-116">Notifies the code profiler that a garbage collection has started.</span></span>|  
|[<span data-ttu-id="a721b-117">HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-117">HandleCreated Method</span></span>](icorprofilercallback2-handlecreated-method.md)|<span data-ttu-id="a721b-118">通知程式碼分析工具已建立垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="a721b-118">Notifies the code profiler that a garbage collection handle has been created.</span></span>|  
|[<span data-ttu-id="a721b-119">HandleDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-119">HandleDestroyed Method</span></span>](icorprofilercallback2-handledestroyed-method.md)|<span data-ttu-id="a721b-120">通知程式碼分析工具，垃圾收集控制碼已損毀。</span><span class="sxs-lookup"><span data-stu-id="a721b-120">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>|  
|[<span data-ttu-id="a721b-121">RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-121">RootReferences2 Method</span></span>](icorprofilercallback2-rootreferences2-method.md)|<span data-ttu-id="a721b-122">在垃圾收集發生之後，通知分析工具有關根參考。</span><span class="sxs-lookup"><span data-stu-id="a721b-122">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="a721b-123">這個方法是 [ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md) 方法的延伸。</span><span class="sxs-lookup"><span data-stu-id="a721b-123">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>|  
|[<span data-ttu-id="a721b-124">SurvivingReferences 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-124">SurvivingReferences Method</span></span>](icorprofilercallback2-survivingreferences-method.md)|<span data-ttu-id="a721b-125">通知分析工具有關已回收垃圾收集的物件參考。</span><span class="sxs-lookup"><span data-stu-id="a721b-125">Notifies the profiler about object references that have survived a garbage collection.</span></span>|  
|[<span data-ttu-id="a721b-126">ThreadNameChanged 方法</span><span class="sxs-lookup"><span data-stu-id="a721b-126">ThreadNameChanged Method</span></span>](icorprofilercallback2-threadnamechanged-method.md)|<span data-ttu-id="a721b-127">通知程式碼分析工具，執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="a721b-127">Notifies the code profiler that the name of a thread has changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a721b-128">備註</span><span class="sxs-lookup"><span data-stu-id="a721b-128">Remarks</span></span>  

 <span data-ttu-id="a721b-129">CLR `ICorProfilerCallback` 會呼叫 (或) 介面中的方法，以在分析工具 `ICorProfilerCallback2` 已訂閱的事件發生時通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="a721b-129">The CLR calls a method in the `ICorProfilerCallback` (or `ICorProfilerCallback2`) interface to notify the profiler when an event, to which the profiler had subscribed, occurs.</span></span> <span data-ttu-id="a721b-130">這是 CLR 用來與程式碼分析工具通訊的主要回呼介面。</span><span class="sxs-lookup"><span data-stu-id="a721b-130">This is the primary callback interface through which the CLR communicates with the code profiler.</span></span>  
  
 <span data-ttu-id="a721b-131">程式碼分析工具必須執行介面的方法 `ICorProfilerCallback` 。</span><span class="sxs-lookup"><span data-stu-id="a721b-131">A code profiler must implement the methods of the `ICorProfilerCallback` interface.</span></span> <span data-ttu-id="a721b-132">針對 .NET Framework 2.0 和更新版本，分析工具也必須執行 `ICorProfilerCallback2` 方法。</span><span class="sxs-lookup"><span data-stu-id="a721b-132">For the .NET Framework 2.0 and later versions, the profiler must also implement the `ICorProfilerCallback2` methods.</span></span> <span data-ttu-id="a721b-133">每個方法的執行都必須傳回一個 HRESULT，其值為「成功」或「失敗時 E_FAIL 的 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a721b-133">Each method implementation must return an HRESULT having a value of S_OK on success or E_FAIL on failure.</span></span> <span data-ttu-id="a721b-134">目前，CLR 會忽略每個回呼所傳回的 HRESULT，但 [ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)除外。</span><span class="sxs-lookup"><span data-stu-id="a721b-134">Currently, the CLR ignores the HRESULT that is returned by each callback except [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md).</span></span>  
  
 <span data-ttu-id="a721b-135">程式碼分析工具必須在 Microsoft Windows 登錄中註冊，其 COM 物件會執行 `ICorProfilerCallback` 和 `ICorProfilerCallback2` 介面。</span><span class="sxs-lookup"><span data-stu-id="a721b-135">A code profiler must register in the Microsoft Windows registry, its COM object that implements the `ICorProfilerCallback` and `ICorProfilerCallback2` interfaces.</span></span> <span data-ttu-id="a721b-136">程式碼分析工具會藉由呼叫 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)，訂閱其想要接收通知的事件。</span><span class="sxs-lookup"><span data-stu-id="a721b-136">A code profiler subscribes to the events for which it wants to receive notification by calling [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="a721b-137">這通常是在分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)的執行中完成。</span><span class="sxs-lookup"><span data-stu-id="a721b-137">This is usually done in the profiler's implementation of [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md).</span></span> <span data-ttu-id="a721b-138">當事件即將發生或發生在執行中的執行時間進程時，分析工具就可以接收來自執行時間的通知。</span><span class="sxs-lookup"><span data-stu-id="a721b-138">The profiler is then able to receive notification from the runtime when an event is about to occur or has just occurred in an executing runtime process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a721b-139">Profiler 會註冊單一 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="a721b-139">The profiler registers a single COM object.</span></span> <span data-ttu-id="a721b-140">如果分析工具的目標是 .NET Framework 版本1.0 或1.1，則該 COM 物件只需要執行的方法 `ICorProfilerCallback` 。</span><span class="sxs-lookup"><span data-stu-id="a721b-140">If the profiler is targeting .NET Framework version 1.0 or 1.1, that COM object need only implement the methods of `ICorProfilerCallback`.</span></span> <span data-ttu-id="a721b-141">如果它的目標是 .NET Framework 2.0 版和更新版本，則 COM 物件也必須執行的方法 `ICorProfilerCallback2` 。</span><span class="sxs-lookup"><span data-stu-id="a721b-141">If it is targeting .NET Framework version 2.0 and later, the COM object must also implement the methods of `ICorProfilerCallback2`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a721b-142">需求</span><span class="sxs-lookup"><span data-stu-id="a721b-142">Requirements</span></span>  

 <span data-ttu-id="a721b-143">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a721b-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a721b-144">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a721b-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a721b-145">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a721b-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a721b-146">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a721b-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a721b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a721b-147">See also</span></span>

- [<span data-ttu-id="a721b-148">分析介面</span><span class="sxs-lookup"><span data-stu-id="a721b-148">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a721b-149">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a721b-149">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a721b-150">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="a721b-150">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)
- [<span data-ttu-id="a721b-151">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="a721b-151">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
