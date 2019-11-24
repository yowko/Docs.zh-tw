---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: b6ef54297b69892f07df1aa92a92600fb20756e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445297"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="5a355-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="5a355-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="5a355-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="5a355-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a355-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a355-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a355-105">備註</span><span class="sxs-lookup"><span data-stu-id="5a355-105">Remarks</span></span>  
 <span data-ttu-id="5a355-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="5a355-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5a355-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="5a355-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5a355-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="5a355-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a355-109">需求</span><span class="sxs-lookup"><span data-stu-id="5a355-109">Requirements</span></span>  
 <span data-ttu-id="5a355-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a355-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a355-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a355-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a355-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a355-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a355-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a355-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a355-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a355-114">See also</span></span>

- [<span data-ttu-id="5a355-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5a355-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5a355-116">ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="5a355-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
