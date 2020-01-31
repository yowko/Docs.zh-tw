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
ms.openlocfilehash: 285bdd3f2a96d3c6cb0039382d9944e48c49971a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865905"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="4ea43-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="4ea43-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="4ea43-103">通知分析工具，執行時間已中止發生的運行時暫停。</span><span class="sxs-lookup"><span data-stu-id="4ea43-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea43-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ea43-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4ea43-105">備註</span><span class="sxs-lookup"><span data-stu-id="4ea43-105">Remarks</span></span>  
 <span data-ttu-id="4ea43-106">如果兩個執行緒同時嘗試暫停執行時間，則運行時暫停可能會中止。</span><span class="sxs-lookup"><span data-stu-id="4ea43-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="4ea43-107">[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)回呼或 `RuntimeSuspendAborted` 回呼會在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回呼之後的單一執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="4ea43-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="4ea43-108">`RuntimeSuspendAborted` 回呼保證會在與 `RuntimeSuspendStarted` 回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="4ea43-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea43-109">需求</span><span class="sxs-lookup"><span data-stu-id="4ea43-109">Requirements</span></span>  
 <span data-ttu-id="4ea43-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ea43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ea43-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ea43-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ea43-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ea43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ea43-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea43-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea43-114">See also</span></span>

- [<span data-ttu-id="4ea43-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4ea43-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
