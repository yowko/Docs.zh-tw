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
ms.openlocfilehash: 4b6eb59dd771e4013106e6a77fc7475b77b2b007
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732017"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="f3d45-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="f3d45-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>

<span data-ttu-id="f3d45-103">通知分析工具，執行時間已中止發生的執行時間暫止。</span><span class="sxs-lookup"><span data-stu-id="f3d45-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d45-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3d45-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f3d45-105">備註</span><span class="sxs-lookup"><span data-stu-id="f3d45-105">Remarks</span></span>  

 <span data-ttu-id="f3d45-106">如果兩個執行緒同時嘗試暫停執行時間，則執行時間暫止可能會中止。</span><span class="sxs-lookup"><span data-stu-id="f3d45-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="f3d45-107">[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)回呼或 `RuntimeSuspendAborted` 回呼會在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回呼之後的單一執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="f3d45-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="f3d45-108">`RuntimeSuspendAborted`回呼保證會在與回呼相同的執行緒上發生 `RuntimeSuspendStarted` 。</span><span class="sxs-lookup"><span data-stu-id="f3d45-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3d45-109">需求</span><span class="sxs-lookup"><span data-stu-id="f3d45-109">Requirements</span></span>  

 <span data-ttu-id="f3d45-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d45-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3d45-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3d45-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3d45-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3d45-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3d45-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3d45-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d45-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d45-114">See also</span></span>

- [<span data-ttu-id="f3d45-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f3d45-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
