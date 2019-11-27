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
ms.openlocfilehash: 81c26214762fba1cac43e42adc1ee9909759972f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430319"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="04e06-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="04e06-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="04e06-103">通知分析工具，執行時間已恢復所有運行時間表程，並已回到正常作業。</span><span class="sxs-lookup"><span data-stu-id="04e06-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e06-104">語法</span><span class="sxs-lookup"><span data-stu-id="04e06-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="04e06-105">備註</span><span class="sxs-lookup"><span data-stu-id="04e06-105">Remarks</span></span>  
 <span data-ttu-id="04e06-106">不保證 `RuntimeResumeFinished` 回呼會在與[ICorProfilerCallback：： RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="04e06-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="04e06-107">不過，它保證會在與[ICorProfilerCallback：： RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="04e06-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e06-108">需求</span><span class="sxs-lookup"><span data-stu-id="04e06-108">Requirements</span></span>  
 <span data-ttu-id="04e06-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04e06-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e06-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04e06-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04e06-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04e06-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04e06-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e06-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e06-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04e06-113">See also</span></span>

- [<span data-ttu-id="04e06-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="04e06-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
