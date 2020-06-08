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
ms.openlocfilehash: 08e76e295e30ede48733ab35870ec965eb157f60
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499866"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="ba8d0-102">ICorProfilerCallback::RuntimeResumeStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ba8d0-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="ba8d0-103">通知分析工具，執行時間正在繼續所有運行時間表程。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba8d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba8d0-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ba8d0-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="ba8d0-105">Requirements</span></span>  
 <span data-ttu-id="ba8d0-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba8d0-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba8d0-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba8d0-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba8d0-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba8d0-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba8d0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8d0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba8d0-110">See also</span></span>

- [<span data-ttu-id="ba8d0-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ba8d0-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ba8d0-112">RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="ba8d0-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
