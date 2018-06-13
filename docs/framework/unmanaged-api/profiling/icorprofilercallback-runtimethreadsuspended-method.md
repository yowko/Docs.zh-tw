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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7673d6fac2626bc0059204ea77a23686b11638cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452731"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="fb86b-102">ICorProfilerCallback::RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="fb86b-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="fb86b-103">指定的執行緒已暫止或即將暫停時，通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="fb86b-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb86b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb86b-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb86b-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb86b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="fb86b-106">[in]已暫止執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fb86b-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb86b-107">備註</span><span class="sxs-lookup"><span data-stu-id="fb86b-107">Remarks</span></span>  
 <span data-ttu-id="fb86b-108">`RuntimeThreadSuspended`通知可能會發生任何時間之間[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)和相關聯[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="fb86b-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="fb86b-109">之間發生的通知[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)和`RuntimeResumeStarted`原本執行中的執行緒 unmanaged 程式碼，且已進入執行階段時被擱置。</span><span class="sxs-lookup"><span data-stu-id="fb86b-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="fb86b-110">通常，暫止的執行緒之後，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="fb86b-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="fb86b-111">不過，如果處於暫停狀態的目前執行中執行緒 （呼叫此回呼的執行緒），此回呼會暫止的執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="fb86b-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb86b-112">需求</span><span class="sxs-lookup"><span data-stu-id="fb86b-112">Requirements</span></span>  
 <span data-ttu-id="fb86b-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb86b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb86b-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb86b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb86b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb86b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb86b-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb86b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb86b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb86b-117">See Also</span></span>  
 [<span data-ttu-id="fb86b-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fb86b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fb86b-119">RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="fb86b-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
