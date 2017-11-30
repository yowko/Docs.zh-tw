---
title: "ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec1b05e67a10f5e7b22a950d1dec24528b5c4914
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="ac5a3-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="ac5a3-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="ac5a3-103">通知分析工具處理正在進入例外狀況回溯階段`finally`子句包含在指定的函式。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac5a3-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac5a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac5a3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ac5a3-106">[in]包含函數的識別碼`finally`子句。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac5a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="ac5a3-107">Remarks</span></span>  
 <span data-ttu-id="ac5a3-108">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="ac5a3-109">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="ac5a3-110">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5a3-111">需求</span><span class="sxs-lookup"><span data-stu-id="ac5a3-111">Requirements</span></span>  
 <span data-ttu-id="ac5a3-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac5a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5a3-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac5a3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac5a3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac5a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac5a3-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5a3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac5a3-116">See Also</span></span>  
 [<span data-ttu-id="ac5a3-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ac5a3-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ac5a3-118">GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ac5a3-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="ac5a3-119">ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="ac5a3-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
