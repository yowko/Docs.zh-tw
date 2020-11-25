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
ms.openlocfilehash: 17dd0cc8d26c328bf6128795f02d751b7ae9e471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717218"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="219ab-102">ICorProfilerCallback::RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="219ab-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>

<span data-ttu-id="219ab-103">通知分析工具，執行時間已完成所有運行時間表程的擱置。</span><span class="sxs-lookup"><span data-stu-id="219ab-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="219ab-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="219ab-105">備註</span><span class="sxs-lookup"><span data-stu-id="219ab-105">Remarks</span></span>  

 <span data-ttu-id="219ab-106">非受控碼中的所有運行時間表程都可以繼續執行，直到他們嘗試重新進入執行時間為止。</span><span class="sxs-lookup"><span data-stu-id="219ab-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="219ab-107">屆時它們也會暫止，直到執行時間恢復為止。</span><span class="sxs-lookup"><span data-stu-id="219ab-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="219ab-108">這也適用于進入執行時間的新執行緒。</span><span class="sxs-lookup"><span data-stu-id="219ab-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="219ab-109">執行時間中的所有線程如果已在可中斷的程式碼中，就會立即暫停，或在它們到達可中斷的程式碼時被要求暫停。</span><span class="sxs-lookup"><span data-stu-id="219ab-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="219ab-110">`RuntimeSuspendFinished`回呼保證會在與[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回呼相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="219ab-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="219ab-111">需求</span><span class="sxs-lookup"><span data-stu-id="219ab-111">Requirements</span></span>  

 <span data-ttu-id="219ab-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="219ab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="219ab-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="219ab-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="219ab-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="219ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="219ab-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219ab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="219ab-116">See also</span></span>

- [<span data-ttu-id="219ab-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="219ab-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="219ab-118">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="219ab-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
