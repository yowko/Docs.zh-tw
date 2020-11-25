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
ms.openlocfilehash: e7bd07205a87ecefb658e01db17100a48681b54b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732030"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="52584-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="52584-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="52584-103">通知分析工具，執行時間已繼續所有運行時間表程，並已恢復正常作業。</span><span class="sxs-lookup"><span data-stu-id="52584-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52584-104">語法</span><span class="sxs-lookup"><span data-stu-id="52584-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="52584-105">備註</span><span class="sxs-lookup"><span data-stu-id="52584-105">Remarks</span></span>  

 <span data-ttu-id="52584-106">`RuntimeResumeFinished`回呼不保證會在與[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="52584-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="52584-107">不過，它保證會在與 [ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) 回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="52584-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52584-108">需求</span><span class="sxs-lookup"><span data-stu-id="52584-108">Requirements</span></span>  

 <span data-ttu-id="52584-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52584-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52584-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52584-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52584-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52584-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52584-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52584-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52584-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52584-113">See also</span></span>

- [<span data-ttu-id="52584-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="52584-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
