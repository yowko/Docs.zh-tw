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
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503194"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="aea96-102">ICorProfilerCallback::RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="aea96-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="aea96-103">通知分析工具，指定的執行緒已暫止或即將暫止。</span><span class="sxs-lookup"><span data-stu-id="aea96-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea96-104">語法</span><span class="sxs-lookup"><span data-stu-id="aea96-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea96-105">參數</span><span class="sxs-lookup"><span data-stu-id="aea96-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="aea96-106">在已暫止之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="aea96-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aea96-107">備註</span><span class="sxs-lookup"><span data-stu-id="aea96-107">Remarks</span></span>  
 <span data-ttu-id="aea96-108">`RuntimeThreadSuspended`通知可以在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)和相關聯的[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回呼之間的任何時間發生。</span><span class="sxs-lookup"><span data-stu-id="aea96-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="aea96-109">在[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)之間發生的通知， `RuntimeResumeStarted` 適用于已在非受控程式碼中執行，並在進入執行時間時暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="aea96-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="aea96-110">一般來說，這個回呼會線上程暫停之後發生。</span><span class="sxs-lookup"><span data-stu-id="aea96-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="aea96-111">不過，如果目前執行中的執行緒（呼叫此回呼的執行緒）是要暫止的執行緒，此回呼會線上程暫停之前發生。</span><span class="sxs-lookup"><span data-stu-id="aea96-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea96-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="aea96-112">Requirements</span></span>  
 <span data-ttu-id="aea96-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aea96-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea96-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aea96-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aea96-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aea96-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aea96-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea96-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea96-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aea96-117">See also</span></span>

- [<span data-ttu-id="aea96-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="aea96-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="aea96-119">RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="aea96-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
