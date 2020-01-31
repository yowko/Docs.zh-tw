---
title: ICorProfilerCallback::RuntimeResumeStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: c7b52954a6be449de0c3633f0ac648980c6d13f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865918"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="ea424-102">ICorProfilerCallback::RuntimeResumeStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ea424-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="ea424-103">通知分析工具，執行時間正在繼續所有運行時間表程。</span><span class="sxs-lookup"><span data-stu-id="ea424-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea424-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea424-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ea424-105">需求</span><span class="sxs-lookup"><span data-stu-id="ea424-105">Requirements</span></span>  
 <span data-ttu-id="ea424-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea424-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea424-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea424-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea424-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea424-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea424-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea424-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea424-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea424-110">See also</span></span>

- [<span data-ttu-id="ea424-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ea424-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ea424-112">RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="ea424-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
