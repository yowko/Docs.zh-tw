---
title: ICorProfilerCallback::RuntimeThreadResumed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b4464c72e8d189cea4831cb641b9ff05063ce25
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747225"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="43263-102">ICorProfilerCallback::RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="43263-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="43263-103">指定的執行緒已恢復在暫停之後會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="43263-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43263-104">語法</span><span class="sxs-lookup"><span data-stu-id="43263-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43263-105">參數</span><span class="sxs-lookup"><span data-stu-id="43263-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="43263-106">[in]已繼續執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="43263-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43263-107">需求</span><span class="sxs-lookup"><span data-stu-id="43263-107">Requirements</span></span>  
 <span data-ttu-id="43263-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43263-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43263-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43263-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43263-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43263-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43263-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43263-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43263-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43263-112">See also</span></span>

- [<span data-ttu-id="43263-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="43263-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="43263-114">RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="43263-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
