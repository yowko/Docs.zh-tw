---
title: "ICorProfilerCallback2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7927d3b4d41731c9b69154fa8895a8f698f53e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2-interface"></a><span data-ttu-id="dc551-102">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="dc551-102">ICorProfilerCallback2 Interface</span></span>
<span data-ttu-id="dc551-103">提供用來在分析工具已訂閱的事件發生時，通知程式碼分析工具 common language runtime (CLR) 的方法。</span><span class="sxs-lookup"><span data-stu-id="dc551-103">Provides methods that are used by the common language runtime (CLR) to notify a code profiler when the events to which the profiler has subscribed occur.</span></span> <span data-ttu-id="dc551-104">`ICorProfilerCallback2`介面是延伸[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="dc551-104">The `ICorProfilerCallback2` interface is an extension of the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span> <span data-ttu-id="dc551-105">也就是說，它會提供.NET Framework 2.0 版中導入新的回呼。</span><span class="sxs-lookup"><span data-stu-id="dc551-105">That is, it provides new callbacks introduced in the .NET Framework version 2.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc551-106">每個方法實作必須傳回值 s_ok 只在成功或 E_FAIL 失敗 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="dc551-106">Each method implementation must return an HRESULT having a value of S_OK on success or E_FAIL on failure.</span></span> <span data-ttu-id="dc551-107">目前，CLR 會忽略除了每個回撥所傳回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dc551-107">Currently, the CLR ignores the HRESULT that is returned by each callback except [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc551-108">方法</span><span class="sxs-lookup"><span data-stu-id="dc551-108">Methods</span></span>  
  
|<span data-ttu-id="dc551-109">方法</span><span class="sxs-lookup"><span data-stu-id="dc551-109">Method</span></span>|<span data-ttu-id="dc551-110">描述</span><span class="sxs-lookup"><span data-stu-id="dc551-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc551-111">FinalizeableObjectQueued 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-111">FinalizeableObjectQueued Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|<span data-ttu-id="dc551-112">通知程式碼分析工具的物件具有完成項佇列中的完成項執行緒執行其`Finalize`方法。</span><span class="sxs-lookup"><span data-stu-id="dc551-112">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>|  
|[<span data-ttu-id="dc551-113">GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-113">GarbageCollectionFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|<span data-ttu-id="dc551-114">記憶體回收回收完成，並為其已發行所有記憶體回收回呼通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="dc551-114">Notifies the profiler that a garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>|  
|[<span data-ttu-id="dc551-115">GarbageCollectionStarted 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-115">GarbageCollectionStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|<span data-ttu-id="dc551-116">已開始在記憶體回收通知的程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="dc551-116">Notifies the code profiler that a garbage collection has started.</span></span>|  
|[<span data-ttu-id="dc551-117">HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-117">HandleCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|<span data-ttu-id="dc551-118">通知記憶體回收控制代碼已建立的程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="dc551-118">Notifies the code profiler that a garbage collection handle has been created.</span></span>|  
|[<span data-ttu-id="dc551-119">HandleDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-119">HandleDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|<span data-ttu-id="dc551-120">通知記憶體回收控制代碼已終結的程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="dc551-120">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>|  
|[<span data-ttu-id="dc551-121">RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-121">RootReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|<span data-ttu-id="dc551-122">在記憶體回收發生後，請通知根參考的相關程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="dc551-122">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="dc551-123">這個方法是延伸[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="dc551-123">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>|  
|[<span data-ttu-id="dc551-124">SurvivingReferences 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-124">SurvivingReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|<span data-ttu-id="dc551-125">通知分析工具需有未被記憶體回收的物件參考。</span><span class="sxs-lookup"><span data-stu-id="dc551-125">Notifies the profiler about object references that have survived a garbage collection.</span></span>|  
|[<span data-ttu-id="dc551-126">ThreadNameChanged 方法</span><span class="sxs-lookup"><span data-stu-id="dc551-126">ThreadNameChanged Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|<span data-ttu-id="dc551-127">通知程式碼剖析工具，執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="dc551-127">Notifies the code profiler that the name of a thread has changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc551-128">備註</span><span class="sxs-lookup"><span data-stu-id="dc551-128">Remarks</span></span>  
 <span data-ttu-id="dc551-129">CLR 會呼叫的方法`ICorProfilerCallback`(或`ICorProfilerCallback2`) 介面，以通知分析工具事件，要在分析工具已訂閱時，就會發生。</span><span class="sxs-lookup"><span data-stu-id="dc551-129">The CLR calls a method in the `ICorProfilerCallback` (or `ICorProfilerCallback2`) interface to notify the profiler when an event, to which the profiler had subscribed, occurs.</span></span> <span data-ttu-id="dc551-130">這是主要的回呼介面，透過此 CLR 與程式碼分析工具的通訊。</span><span class="sxs-lookup"><span data-stu-id="dc551-130">This is the primary callback interface through which the CLR communicates with the code profiler.</span></span>  
  
 <span data-ttu-id="dc551-131">程式碼分析工具必須實作的方法`ICorProfilerCallback`介面。</span><span class="sxs-lookup"><span data-stu-id="dc551-131">A code profiler must implement the methods of the `ICorProfilerCallback` interface.</span></span> <span data-ttu-id="dc551-132">.NET Framework 2.0 和更新版本中，分析工具也必須實作`ICorProfilerCallback2`方法。</span><span class="sxs-lookup"><span data-stu-id="dc551-132">For the .NET Framework 2.0 and later versions, the profiler must also implement the `ICorProfilerCallback2` methods.</span></span> <span data-ttu-id="dc551-133">每個方法實作必須傳回值 s_ok 只在成功或 E_FAIL 失敗 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="dc551-133">Each method implementation must return an HRESULT having a value of S_OK on success or E_FAIL on failure.</span></span> <span data-ttu-id="dc551-134">目前，CLR 會忽略除了每個回撥所傳回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dc551-134">Currently, the CLR ignores the HRESULT that is returned by each callback except [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).</span></span>  
  
 <span data-ttu-id="dc551-135">程式碼分析工具必須註冊在 Microsoft Windows 登錄中，其會實作的 COM 物件`ICorProfilerCallback`和`ICorProfilerCallback2`介面。</span><span class="sxs-lookup"><span data-stu-id="dc551-135">A code profiler must register in the Microsoft Windows registry, its COM object that implements the `ICorProfilerCallback` and `ICorProfilerCallback2` interfaces.</span></span> <span data-ttu-id="dc551-136">程式碼分析工具訂閱它要接收通知，藉由呼叫的事件[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dc551-136">A code profiler subscribes to the events for which it wants to receive notification by calling [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="dc551-137">這通常會在程式碼剖析工具實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dc551-137">This is usually done in the profiler's implementation of [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md).</span></span> <span data-ttu-id="dc551-138">程式碼剖析工具就能夠從執行階段時通知事件會發生或剛執行的執行階段程序中發生。</span><span class="sxs-lookup"><span data-stu-id="dc551-138">The profiler is then able to receive notification from the runtime when an event is about to occur or has just occurred in an executing runtime process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc551-139">分析工具註冊單一的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="dc551-139">The profiler registers a single COM object.</span></span> <span data-ttu-id="dc551-140">如果程式碼剖析工具的目標.NET Framework 1.0 或 1.1 版，此 COM 物件只需要實作的方法`ICorProfilerCallback`。</span><span class="sxs-lookup"><span data-stu-id="dc551-140">If the profiler is targeting .NET Framework version 1.0 or 1.1, that COM object need only implement the methods of `ICorProfilerCallback`.</span></span> <span data-ttu-id="dc551-141">如果它設為目標.NET Framework 2.0 版和更新版本中，COM 物件也必須實作的方法`ICorProfilerCallback2`。</span><span class="sxs-lookup"><span data-stu-id="dc551-141">If it is targeting .NET Framework version 2.0 and later, the COM object must also implement the methods of `ICorProfilerCallback2`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc551-142">需求</span><span class="sxs-lookup"><span data-stu-id="dc551-142">Requirements</span></span>  
 <span data-ttu-id="dc551-143">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc551-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc551-144">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc551-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc551-145">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc551-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc551-146">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc551-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc551-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc551-147">See Also</span></span>  
 [<span data-ttu-id="dc551-148">分析介面</span><span class="sxs-lookup"><span data-stu-id="dc551-148">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="dc551-149">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dc551-149">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dc551-150">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="dc551-150">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [<span data-ttu-id="dc551-151">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="dc551-151">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
