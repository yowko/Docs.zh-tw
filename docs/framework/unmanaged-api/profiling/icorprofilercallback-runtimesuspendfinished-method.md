---
title: "ICorProfilerCallback::RuntimeSuspendFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c922ee4f986df22f213820b8aed60ea28a76377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="62580-102">ICorProfilerCallback::RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="62580-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="62580-103">通知分析工具執行階段已完成的所有執行階段執行緒的暫停。</span><span class="sxs-lookup"><span data-stu-id="62580-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62580-104">語法</span><span class="sxs-lookup"><span data-stu-id="62580-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="62580-105">備註</span><span class="sxs-lookup"><span data-stu-id="62580-105">Remarks</span></span>  
 <span data-ttu-id="62580-106">允許在 unmanaged 程式碼中的所有執行階段執行緒繼續執行，直到嘗試重新進入執行階段。</span><span class="sxs-lookup"><span data-stu-id="62580-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="62580-107">此時，它們也會被暫止直到執行階段繼續。</span><span class="sxs-lookup"><span data-stu-id="62580-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="62580-108">這也適用於新的執行緒進入執行階段。</span><span class="sxs-lookup"><span data-stu-id="62580-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="62580-109">執行階段中的所有執行緒都都在立即暫止都已中斷的程式碼，或者都會要求他們在到達可中斷的程式碼時暫停。</span><span class="sxs-lookup"><span data-stu-id="62580-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="62580-110">`RuntimeSuspendFinished`回呼會保證在相同執行緒上發生[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="62580-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62580-111">需求</span><span class="sxs-lookup"><span data-stu-id="62580-111">Requirements</span></span>  
 <span data-ttu-id="62580-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62580-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62580-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62580-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62580-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62580-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62580-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62580-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62580-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62580-116">See Also</span></span>  
 [<span data-ttu-id="62580-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="62580-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="62580-118">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="62580-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
