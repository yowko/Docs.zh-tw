---
title: "ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eba7f6e5123108a7040bd2185eb57fc703c72c30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="3b395-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="3b395-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="3b395-103">通知分析工具已完成回溯函式回溯階段的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="3b395-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b395-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b395-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b395-105">備註</span><span class="sxs-lookup"><span data-stu-id="3b395-105">Remarks</span></span>  
 <span data-ttu-id="3b395-106">當`ExceptionUnwindFunctionLeave`呼叫方法、 函式的執行個體和其堆疊資料會從堆疊移除。</span><span class="sxs-lookup"><span data-stu-id="3b395-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="3b395-107">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個呼叫時封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3b395-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3b395-108">如果嘗試在程式碼剖析工具區塊和記憶體回收，則執行階段會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="3b395-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3b395-109">此外，此通話期間，程式碼剖析工具必須呼叫至 managed 程式碼或任何方式發生原因的 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="3b395-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b395-110">需求</span><span class="sxs-lookup"><span data-stu-id="3b395-110">Requirements</span></span>  
 <span data-ttu-id="3b395-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b395-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b395-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b395-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b395-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b395-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b395-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b395-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b395-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b395-115">See Also</span></span>  
 [<span data-ttu-id="3b395-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3b395-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3b395-117">ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="3b395-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
