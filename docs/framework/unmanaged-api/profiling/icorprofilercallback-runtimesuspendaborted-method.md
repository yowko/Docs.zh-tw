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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62682ca19b9f987370ca11d2bda63fba27f28474
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782998"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="1ee7f-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="1ee7f-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="1ee7f-103">通知分析工具執行階段已中止執行階段暫止之前發生。</span><span class="sxs-lookup"><span data-stu-id="1ee7f-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ee7f-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1ee7f-105">備註</span><span class="sxs-lookup"><span data-stu-id="1ee7f-105">Remarks</span></span>  
 <span data-ttu-id="1ee7f-106">如果兩個執行緒同時嘗試暫停執行階段，可能會被中止的執行階段暫止。</span><span class="sxs-lookup"><span data-stu-id="1ee7f-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="1ee7f-107">任一[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)回呼或`RuntimeSuspendAborted`回呼會在單一執行緒下列上[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="1ee7f-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="1ee7f-108">`RuntimeSuspendAborted`保證在相同的執行緒上進行回呼`RuntimeSuspendStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="1ee7f-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee7f-109">需求</span><span class="sxs-lookup"><span data-stu-id="1ee7f-109">Requirements</span></span>  
 <span data-ttu-id="1ee7f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee7f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee7f-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ee7f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ee7f-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee7f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee7f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee7f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee7f-114">See also</span></span>

- [<span data-ttu-id="1ee7f-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1ee7f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
