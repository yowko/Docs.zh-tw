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
ms.openlocfilehash: 8bc97bb0d36a046353587a95aa2b79eff12866e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499879"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="cb462-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="cb462-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="cb462-103">通知分析工具，執行時間已恢復所有運行時間表程，並已回到正常作業。</span><span class="sxs-lookup"><span data-stu-id="cb462-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb462-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb462-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb462-105">備註</span><span class="sxs-lookup"><span data-stu-id="cb462-105">Remarks</span></span>  
 <span data-ttu-id="cb462-106">`RuntimeResumeFinished`回呼不保證會在與[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="cb462-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="cb462-107">不過，它保證會在與[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="cb462-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb462-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="cb462-108">Requirements</span></span>  
 <span data-ttu-id="cb462-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb462-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb462-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb462-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb462-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb462-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb462-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb462-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb462-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb462-113">See also</span></span>

- [<span data-ttu-id="cb462-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cb462-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
