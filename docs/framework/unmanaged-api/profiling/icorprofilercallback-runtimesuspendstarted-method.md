---
title: ICorProfilerCallback::RuntimeSuspendStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: cc01254d9604ce39c964c7d78059ef4087483c77
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503220"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="3af2f-102">ICorProfilerCallback::RuntimeSuspendStarted 方法</span><span class="sxs-lookup"><span data-stu-id="3af2f-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="3af2f-103">通知分析工具，執行時間即將暫停所有運行時間表程。</span><span class="sxs-lookup"><span data-stu-id="3af2f-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af2f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3af2f-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3af2f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3af2f-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="3af2f-106">在[COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md)列舉的值，表示暫停的原因。</span><span class="sxs-lookup"><span data-stu-id="3af2f-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3af2f-107">備註</span><span class="sxs-lookup"><span data-stu-id="3af2f-107">Remarks</span></span>  
 <span data-ttu-id="3af2f-108">在非受控碼中的所有運行時間表程，都可以繼續執行，直到它們嘗試重新進入執行時間為止。</span><span class="sxs-lookup"><span data-stu-id="3af2f-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="3af2f-109">在該時間點，它們也會暫停，直到執行時間繼續執行為止。</span><span class="sxs-lookup"><span data-stu-id="3af2f-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="3af2f-110">這也適用于輸入執行時間的新執行緒。</span><span class="sxs-lookup"><span data-stu-id="3af2f-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="3af2f-111">執行時間中的所有線程如果已經在可中斷的程式碼中，就會立即暫停，或在到達可中斷的程式碼時，要求他們暫停。</span><span class="sxs-lookup"><span data-stu-id="3af2f-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af2f-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="3af2f-112">Requirements</span></span>  
 <span data-ttu-id="3af2f-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3af2f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3af2f-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3af2f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3af2f-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3af2f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3af2f-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3af2f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af2f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3af2f-117">See also</span></span>

- [<span data-ttu-id="3af2f-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3af2f-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3af2f-119">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="3af2f-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="3af2f-120">RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="3af2f-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
