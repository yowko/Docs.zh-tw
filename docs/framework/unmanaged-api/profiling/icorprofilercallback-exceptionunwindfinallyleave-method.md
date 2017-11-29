---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf373872ada8364fe755162597dc9baf5c527f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="f7c03-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="f7c03-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="f7c03-103">通知分析工具的回溯階段的例外狀況處理已離開`finally`子句。</span><span class="sxs-lookup"><span data-stu-id="f7c03-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c03-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7c03-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7c03-105">備註</span><span class="sxs-lookup"><span data-stu-id="f7c03-105">Remarks</span></span>  
 <span data-ttu-id="f7c03-106">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個呼叫時封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f7c03-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f7c03-107">如果嘗試在程式碼剖析工具區塊和記憶體回收，則執行階段會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="f7c03-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f7c03-108">此外，此通話期間，程式碼剖析工具必須呼叫至 managed 程式碼或任何方式發生原因的 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="f7c03-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c03-109">需求</span><span class="sxs-lookup"><span data-stu-id="f7c03-109">Requirements</span></span>  
 <span data-ttu-id="f7c03-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c03-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c03-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7c03-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7c03-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7c03-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7c03-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c03-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c03-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7c03-114">See Also</span></span>  
 [<span data-ttu-id="f7c03-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f7c03-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f7c03-116">ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="f7c03-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
