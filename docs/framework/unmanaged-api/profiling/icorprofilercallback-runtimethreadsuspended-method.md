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
ms.openlocfilehash: 33a39cf2781f49ff0e31989831c4c9829889ec3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731991"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="ac2d7-102">ICorProfilerCallback::RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="ac2d7-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>

<span data-ttu-id="ac2d7-103">通知分析工具，指定的執行緒已暫止或即將暫停。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac2d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac2d7-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac2d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac2d7-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="ac2d7-106">在已暫停之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac2d7-107">備註</span><span class="sxs-lookup"><span data-stu-id="ac2d7-107">Remarks</span></span>  

 <span data-ttu-id="ac2d7-108">`RuntimeThreadSuspended`通知可以在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)和相關聯的[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回呼之間的任何時間進行。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="ac2d7-109">在 [ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) 與執行于非受控程式碼中的執行緒，以及在進入執行時間時暫止的執行緒，都會出現通知 `RuntimeResumeStarted` 。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="ac2d7-110">一般來說，這個回呼會線上程暫止之後發生。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="ac2d7-111">但是，如果目前執行中的執行緒 (呼叫此回呼的執行緒) 是要暫止的執行緒，就會線上程暫停之前發生此回呼。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac2d7-112">需求</span><span class="sxs-lookup"><span data-stu-id="ac2d7-112">Requirements</span></span>  

 <span data-ttu-id="ac2d7-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac2d7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac2d7-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac2d7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac2d7-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac2d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac2d7-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2d7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac2d7-117">See also</span></span>

- [<span data-ttu-id="ac2d7-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ac2d7-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ac2d7-119">RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="ac2d7-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
