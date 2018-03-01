---
title: "ICorProfilerInfo3::RequestProfilerDetach 方法"
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
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 33a5c45bbb64029177a0a680243dd39a825683e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="a8af7-102">ICorProfilerInfo3::RequestProfilerDetach 方法</span><span class="sxs-lookup"><span data-stu-id="a8af7-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>
<span data-ttu-id="a8af7-103">指示該執行階段中斷與分析工具的連結。</span><span class="sxs-lookup"><span data-stu-id="a8af7-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8af7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8af7-104">Syntax</span></span>  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8af7-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8af7-105">Parameters</span></span>  
 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="a8af7-106">[in] 時間長度，以毫秒為單位，Common Language Runtime (CLR) 應該在檢查之前等待，以查看它是否能安全卸載分析工具 。</span><span class="sxs-lookup"><span data-stu-id="a8af7-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8af7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8af7-107">Return Value</span></span>  
 <span data-ttu-id="a8af7-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a8af7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a8af7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8af7-109">HRESULT</span></span>|<span data-ttu-id="a8af7-110">描述</span><span class="sxs-lookup"><span data-stu-id="a8af7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8af7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8af7-111">S_OK</span></span>|<span data-ttu-id="a8af7-112">中斷連結要求有效，而且現在中斷連結程序會在另一個執行緒上繼續。</span><span class="sxs-lookup"><span data-stu-id="a8af7-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="a8af7-113">中斷連結全部完成時，會發生 `ProfilerDetachSucceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="a8af7-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="a8af7-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="a8af7-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="a8af7-115">分析工具失敗[iunknown:: Queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)嘗試[ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)介面，它必須實作以支援中斷連結作業。</span><span class="sxs-lookup"><span data-stu-id="a8af7-115">The profiler failed an [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) attempt for the [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="a8af7-116">未嘗試中斷連結。</span><span class="sxs-lookup"><span data-stu-id="a8af7-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="a8af7-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="a8af7-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="a8af7-118">因為分析工具在啟動時將旗標設定為不可變，造成無法中斷連結。</span><span class="sxs-lookup"><span data-stu-id="a8af7-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="a8af7-119">未嘗試中斷連結；分析工具仍然完整連結。</span><span class="sxs-lookup"><span data-stu-id="a8af7-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="a8af7-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a8af7-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="a8af7-121">中斷連結是不可能因為使用程式碼剖析工具檢測的 Microsoft intermediate language (MSIL) 程式碼，或插入`enter` / `leave`攔截程序。</span><span class="sxs-lookup"><span data-stu-id="a8af7-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="a8af7-122">未嘗試中斷連結；分析工具仍然完整連結。</span><span class="sxs-lookup"><span data-stu-id="a8af7-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="a8af7-123">**請注意**檢測的 MSIL 是使用分析工具所提供的程式碼[SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a8af7-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="a8af7-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="a8af7-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="a8af7-125">在受管理的應用程式中，執行階段尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="a8af7-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="a8af7-126">(也就是說，執行階段尚未完全載入。)當要求中斷連結在分析工具回呼可能會傳回此錯誤碼[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a8af7-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="a8af7-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8af7-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="a8af7-128">`RequestProfilerDetach` 在不支援的時間呼叫。</span><span class="sxs-lookup"><span data-stu-id="a8af7-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="a8af7-129">會發生這個錯誤的 managed 執行緒上而不是從內部呼叫該方法[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法或是從[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)無法容許記憶體回收的方法。</span><span class="sxs-lookup"><span data-stu-id="a8af7-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="a8af7-130">如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="a8af7-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8af7-131">備註</span><span class="sxs-lookup"><span data-stu-id="a8af7-131">Remarks</span></span>  
 <span data-ttu-id="a8af7-132">在中斷連結程序中，中斷連結的執行緒 (專為對分析工具中斷連結所建立的執行緒) 偶爾會檢查是否所有執行緒都結束分析工具的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a8af7-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="a8af7-133">分析工具應該透過 `dwExpectedCompletionMilliseconds` 參數提供所需時間的估計。</span><span class="sxs-lookup"><span data-stu-id="a8af7-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="a8af7-134">要使用的理想值是分析工具花在任何指定的 `ICorProfilerCallback*` 方法上所需的典型時間量；此值不應小於分析工具預期所需最大時間量的一半。</span><span class="sxs-lookup"><span data-stu-id="a8af7-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="a8af7-135">中斷連結執行緒使用 `dwExpectedCompletionMilliseconds` 來決定睡眠多久之後，再檢查分析工具回呼程式碼是否已迅速卸離所有堆疊。</span><span class="sxs-lookup"><span data-stu-id="a8af7-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="a8af7-136">雖然下列演算法的詳細資料可能會在未來版本中的 CLR 有所變更，它也說明了一種 `dwExpectedCompletionMilliseconds` 能夠用來判斷何時可安全卸載分析工具的方式。</span><span class="sxs-lookup"><span data-stu-id="a8af7-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="a8af7-137">中斷連結執行緒先睡眠 `dwExpectedCompletionMilliseconds` 毫秒。</span><span class="sxs-lookup"><span data-stu-id="a8af7-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a8af7-138">如果從睡眠狀態喚醒後，CLR 發現分析工具回呼程式碼是仍然存在，中斷連結執行緒會再次睡眠，此時兩次`dwExpectedCompletionMilliseconds`毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="a8af7-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a8af7-139">從這個第二個睡眠狀態喚醒後，如果卸離執行緒發現分析工具回呼程式碼仍然存在，它會睡眠 10 分鐘後再檢查一次。</span><span class="sxs-lookup"><span data-stu-id="a8af7-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="a8af7-140">中斷連結執行緒會每隔 10 分鐘重新檢查一次。</span><span class="sxs-lookup"><span data-stu-id="a8af7-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="a8af7-141">如果分析工具指定 `dwExpectedCompletionMilliseconds` 為 0 (零) 時，CLR 會使用預設值為 5000，這表示它會在 5 秒後執行檢查，接著 10 秒後再次檢查，然後之後每隔 10 分鐘一次。</span><span class="sxs-lookup"><span data-stu-id="a8af7-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8af7-142">需求</span><span class="sxs-lookup"><span data-stu-id="a8af7-142">Requirements</span></span>  
 <span data-ttu-id="a8af7-143">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8af7-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8af7-144">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8af7-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8af7-145">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8af7-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8af7-146">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8af7-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8af7-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8af7-147">See Also</span></span>  
 [<span data-ttu-id="a8af7-148">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="a8af7-148">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="a8af7-149">分析介面</span><span class="sxs-lookup"><span data-stu-id="a8af7-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a8af7-150">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="a8af7-150">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
