---
title: ICorProfilerCallback::RuntimeResumeFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 883e226042225b63097acf731b13abd69cc757ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750414"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="dc30f-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="dc30f-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="dc30f-103">執行階段已繼續執行階段的所有執行緒，並回到正常的作業，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="dc30f-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc30f-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc30f-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dc30f-105">備註</span><span class="sxs-lookup"><span data-stu-id="dc30f-105">Remarks</span></span>  
 <span data-ttu-id="dc30f-106">`RuntimeResumeFinished`不保證在相同的執行緒上進行回呼[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="dc30f-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="dc30f-107">不過，一定會與相同的執行緒上發生[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="dc30f-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc30f-108">需求</span><span class="sxs-lookup"><span data-stu-id="dc30f-108">Requirements</span></span>  
 <span data-ttu-id="dc30f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc30f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc30f-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc30f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc30f-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc30f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc30f-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc30f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc30f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc30f-113">See also</span></span>

- [<span data-ttu-id="dc30f-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dc30f-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
