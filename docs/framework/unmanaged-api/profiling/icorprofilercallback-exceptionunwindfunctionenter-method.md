---
title: "ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc41dc95776ca31178153402d2e145a3d2c13bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="070cf-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="070cf-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="070cf-103">通知分析工具回溯階段的例外狀況處理已開始回溯函式。</span><span class="sxs-lookup"><span data-stu-id="070cf-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="070cf-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="070cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="070cf-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="070cf-106">[in]要回溯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="070cf-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="070cf-107">備註</span><span class="sxs-lookup"><span data-stu-id="070cf-107">Remarks</span></span>  
 <span data-ttu-id="070cf-108">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="070cf-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="070cf-109">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="070cf-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="070cf-110">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="070cf-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="070cf-111">需求</span><span class="sxs-lookup"><span data-stu-id="070cf-111">Requirements</span></span>  
 <span data-ttu-id="070cf-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="070cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="070cf-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="070cf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="070cf-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="070cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="070cf-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="070cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070cf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="070cf-116">See Also</span></span>  
 [<span data-ttu-id="070cf-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="070cf-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="070cf-118">ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="070cf-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
