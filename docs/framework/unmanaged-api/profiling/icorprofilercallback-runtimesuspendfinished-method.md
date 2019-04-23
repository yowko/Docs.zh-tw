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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07e2ebe8afe6002dee6c45f56fa1f11a4083d6bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145596"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="fcfe4-102">ICorProfilerCallback::RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fcfe4-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="fcfe4-103">通知分析工具執行階段已完成的執行階段的所有執行緒暫停。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfe4-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcfe4-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcfe4-105">備註</span><span class="sxs-lookup"><span data-stu-id="fcfe4-105">Remarks</span></span>  
 <span data-ttu-id="fcfe4-106">Unmanaged 程式碼中的所有執行階段執行緒才能繼續執行，直到他們試著重新進入執行階段。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="fcfe4-107">此時，它們也會擱置直到執行階段繼續。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="fcfe4-108">這也適用於新的執行緒進入執行階段。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="fcfe4-109">在執行階段中的所有執行緒都都在立即暫止，如果他們都已在可中斷的程式碼，或要求他們到達可中斷的程式碼時暫停。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="fcfe4-110">`RuntimeSuspendFinished`保證在相同的執行緒上進行回呼[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfe4-111">需求</span><span class="sxs-lookup"><span data-stu-id="fcfe4-111">Requirements</span></span>  
 <span data-ttu-id="fcfe4-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcfe4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfe4-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcfe4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcfe4-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcfe4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcfe4-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfe4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfe4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcfe4-116">See also</span></span>

- [<span data-ttu-id="fcfe4-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fcfe4-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fcfe4-118">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="fcfe4-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
