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
ms.openlocfilehash: bb93dbf35501d44bb21d3d689aebeba3acd19f79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616796"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="988bc-102">ICorProfilerCallback::RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="988bc-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="988bc-103">指定的執行緒已暫止，或被暫停，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="988bc-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="988bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="988bc-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="988bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="988bc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="988bc-106">[in]已暫止執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="988bc-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="988bc-107">備註</span><span class="sxs-lookup"><span data-stu-id="988bc-107">Remarks</span></span>  
 <span data-ttu-id="988bc-108">`RuntimeThreadSuspended`通知可能會發生任何時間之間[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)和相關聯[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="988bc-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="988bc-109">之間發生的通知[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)和`RuntimeResumeStarted`執行緒中執行 unmanaged 程式碼，且在執行階段的輸入時被暫止。</span><span class="sxs-lookup"><span data-stu-id="988bc-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="988bc-110">一般而言，暫止的執行緒之後，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="988bc-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="988bc-111">不過，如果目前正在執行的執行緒 （執行緒呼叫此回呼） 是指已遭到擱置，此回呼會發生，暫止執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="988bc-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="988bc-112">需求</span><span class="sxs-lookup"><span data-stu-id="988bc-112">Requirements</span></span>  
 <span data-ttu-id="988bc-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="988bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="988bc-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="988bc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="988bc-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="988bc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="988bc-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="988bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988bc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="988bc-117">See also</span></span>
- [<span data-ttu-id="988bc-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="988bc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="988bc-119">RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="988bc-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
