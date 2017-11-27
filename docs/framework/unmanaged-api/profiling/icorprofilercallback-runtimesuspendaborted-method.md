---
title: "ICorProfilerCallback::RuntimeSuspendAborted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="5ce0f-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="5ce0f-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="5ce0f-103">通知分析工具執行階段已中止執行階段暫停之前發生。</span><span class="sxs-lookup"><span data-stu-id="5ce0f-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ce0f-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5ce0f-105">備註</span><span class="sxs-lookup"><span data-stu-id="5ce0f-105">Remarks</span></span>  
 <span data-ttu-id="5ce0f-106">如果兩個執行緒同時嘗試暫止執行階段，可能會中止執行階段暫止。</span><span class="sxs-lookup"><span data-stu-id="5ce0f-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="5ce0f-107">任一[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)回呼或`RuntimeSuspendAborted`回呼會在單一執行緒下列上[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="5ce0f-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="5ce0f-108">`RuntimeSuspendAborted`回呼會保證在相同執行緒上發生`RuntimeSuspendStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="5ce0f-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce0f-109">需求</span><span class="sxs-lookup"><span data-stu-id="5ce0f-109">Requirements</span></span>  
 <span data-ttu-id="5ce0f-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ce0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce0f-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ce0f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ce0f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ce0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ce0f-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce0f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ce0f-114">See Also</span></span>  
 [<span data-ttu-id="5ce0f-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5ce0f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
