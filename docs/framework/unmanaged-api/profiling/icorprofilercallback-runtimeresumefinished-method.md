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
ms.openlocfilehash: 1c7b3c3ea5e976645c265b34327caa38ef6a28fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226985"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="330f1-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="330f1-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="330f1-103">執行階段已繼續執行階段的所有執行緒，並回到正常的作業，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="330f1-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="330f1-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="330f1-105">備註</span><span class="sxs-lookup"><span data-stu-id="330f1-105">Remarks</span></span>  
 <span data-ttu-id="330f1-106">`RuntimeResumeFinished`不保證在相同的執行緒上進行回呼[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="330f1-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="330f1-107">不過，一定會與相同的執行緒上發生[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="330f1-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330f1-108">需求</span><span class="sxs-lookup"><span data-stu-id="330f1-108">Requirements</span></span>  
 <span data-ttu-id="330f1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="330f1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330f1-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="330f1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="330f1-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="330f1-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="330f1-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="330f1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="330f1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="330f1-113">See also</span></span>

- [<span data-ttu-id="330f1-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="330f1-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
