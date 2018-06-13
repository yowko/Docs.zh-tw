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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70e687f0645fdb68d95effe6fdd52178b92c08e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452253"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="bb3a0-102">ICorProfilerCallback::RuntimeResumeStarted 方法</span><span class="sxs-lookup"><span data-stu-id="bb3a0-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="bb3a0-103">通知分析工具執行階段會繼續執行階段的所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="bb3a0-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb3a0-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="bb3a0-105">需求</span><span class="sxs-lookup"><span data-stu-id="bb3a0-105">Requirements</span></span>  
 <span data-ttu-id="bb3a0-106">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb3a0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3a0-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb3a0-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb3a0-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb3a0-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb3a0-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3a0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3a0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb3a0-110">See Also</span></span>  
 [<span data-ttu-id="bb3a0-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bb3a0-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="bb3a0-112">RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="bb3a0-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
