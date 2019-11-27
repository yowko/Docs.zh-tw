---
title: ICorProfilerCallback::RuntimeSuspendAborted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: fb09a9422f2aeec239f9aef25fb61c731e0aa2e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430617"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="7159d-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="7159d-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="7159d-103">通知分析工具，執行時間已中止發生的運行時暫停。</span><span class="sxs-lookup"><span data-stu-id="7159d-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7159d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7159d-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7159d-105">備註</span><span class="sxs-lookup"><span data-stu-id="7159d-105">Remarks</span></span>  
 <span data-ttu-id="7159d-106">如果兩個執行緒同時嘗試暫停執行時間，則運行時暫停可能會中止。</span><span class="sxs-lookup"><span data-stu-id="7159d-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="7159d-107">[ICorProfilerCallback：： RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)回呼或 `RuntimeSuspendAborted` 回呼會在[ICorProfilerCallback：： RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼之後的單一執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="7159d-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="7159d-108">`RuntimeSuspendAborted` 回呼保證會在與 `RuntimeSuspendStarted` 回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="7159d-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7159d-109">需求</span><span class="sxs-lookup"><span data-stu-id="7159d-109">Requirements</span></span>  
 <span data-ttu-id="7159d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7159d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7159d-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7159d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7159d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7159d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7159d-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7159d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7159d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7159d-114">See also</span></span>

- [<span data-ttu-id="7159d-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7159d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
