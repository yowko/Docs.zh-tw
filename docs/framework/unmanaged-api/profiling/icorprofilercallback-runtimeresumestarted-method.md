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
ms.openlocfilehash: e5fcc9d19a400e23d98a997d051c26af1c1084a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783028"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="2c67b-102">ICorProfilerCallback::RuntimeResumeStarted 方法</span><span class="sxs-lookup"><span data-stu-id="2c67b-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="2c67b-103">通知執行階段會繼續執行階段的所有執行緒的分析工具。</span><span class="sxs-lookup"><span data-stu-id="2c67b-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c67b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c67b-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="2c67b-105">需求</span><span class="sxs-lookup"><span data-stu-id="2c67b-105">Requirements</span></span>  
 <span data-ttu-id="2c67b-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c67b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c67b-107">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c67b-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c67b-108">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c67b-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c67b-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c67b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c67b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c67b-110">See also</span></span>

- [<span data-ttu-id="2c67b-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2c67b-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2c67b-112">RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="2c67b-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
