---
title: ICorProfilerCallback::RuntimeThreadSuspended 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865866"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="33c85-102">ICorProfilerCallback::RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="33c85-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="33c85-103">通知分析工具，指定的執行緒已暫止或即將暫止。</span><span class="sxs-lookup"><span data-stu-id="33c85-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c85-104">語法</span><span class="sxs-lookup"><span data-stu-id="33c85-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33c85-105">參數</span><span class="sxs-lookup"><span data-stu-id="33c85-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="33c85-106">在已暫止之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="33c85-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33c85-107">備註</span><span class="sxs-lookup"><span data-stu-id="33c85-107">Remarks</span></span>  
 <span data-ttu-id="33c85-108">`RuntimeThreadSuspended` 通知可以在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)和相關聯的[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回呼之間隨時發生。</span><span class="sxs-lookup"><span data-stu-id="33c85-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="33c85-109">在[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)和 `RuntimeResumeStarted` 之間發生的通知，適用于已在非受控程式碼中執行，並在進入執行時間時暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="33c85-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="33c85-110">一般來說，這個回呼會線上程暫停之後發生。</span><span class="sxs-lookup"><span data-stu-id="33c85-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="33c85-111">不過，如果目前執行中的執行緒（呼叫此回呼的執行緒）是要暫止的執行緒，此回呼會線上程暫停之前發生。</span><span class="sxs-lookup"><span data-stu-id="33c85-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c85-112">需求</span><span class="sxs-lookup"><span data-stu-id="33c85-112">Requirements</span></span>  
 <span data-ttu-id="33c85-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33c85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c85-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33c85-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33c85-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33c85-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33c85-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c85-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="33c85-117">See also</span></span>

- [<span data-ttu-id="33c85-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="33c85-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="33c85-119">RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="33c85-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
