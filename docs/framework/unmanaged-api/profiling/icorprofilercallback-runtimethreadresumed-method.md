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
ms.openlocfilehash: d3949189a72583ebb50b67a270694a31f1eb23dc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503207"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="5430e-102">ICorProfilerCallback::RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="5430e-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="5430e-103">通知分析工具，指定的執行緒在暫止後已繼續。</span><span class="sxs-lookup"><span data-stu-id="5430e-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5430e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5430e-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5430e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5430e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5430e-106">在已繼續之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5430e-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5430e-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="5430e-107">Requirements</span></span>  
 <span data-ttu-id="5430e-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5430e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5430e-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5430e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5430e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5430e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5430e-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5430e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5430e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5430e-112">See also</span></span>

- [<span data-ttu-id="5430e-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5430e-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5430e-114">RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="5430e-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
