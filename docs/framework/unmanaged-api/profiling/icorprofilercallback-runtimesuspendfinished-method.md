---
title: ICorProfilerCallback::RuntimeSuspendFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: 8bad09ddb2b821d0e02d43c1e3d1585b3473ec98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446969"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="9e52f-102">ICorProfilerCallback::RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9e52f-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="9e52f-103">通知 profiler，執行時間已完成所有運行時間表程的暫止。</span><span class="sxs-lookup"><span data-stu-id="9e52f-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e52f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e52f-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9e52f-105">備註</span><span class="sxs-lookup"><span data-stu-id="9e52f-105">Remarks</span></span>  
 <span data-ttu-id="9e52f-106">在非受控碼中的所有運行時間表程，都可以繼續執行，直到它們嘗試重新進入執行時間為止。</span><span class="sxs-lookup"><span data-stu-id="9e52f-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="9e52f-107">在該時間點，它們也會暫停，直到執行時間繼續執行為止。</span><span class="sxs-lookup"><span data-stu-id="9e52f-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="9e52f-108">這也適用于輸入執行時間的新執行緒。</span><span class="sxs-lookup"><span data-stu-id="9e52f-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="9e52f-109">執行時間中的所有線程如果已經在可中斷的程式碼中，就會立即暫停，或在到達可中斷的程式碼時，要求他們暫停。</span><span class="sxs-lookup"><span data-stu-id="9e52f-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="9e52f-110">`RuntimeSuspendFinished` 回呼保證會在與[ICorProfilerCallback：： RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="9e52f-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e52f-111">需求</span><span class="sxs-lookup"><span data-stu-id="9e52f-111">Requirements</span></span>  
 <span data-ttu-id="9e52f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e52f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e52f-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e52f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e52f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e52f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e52f-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e52f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e52f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e52f-116">See also</span></span>

- [<span data-ttu-id="9e52f-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9e52f-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9e52f-118">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="9e52f-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
