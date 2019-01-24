---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3184b0b3bc03aa300832211b52e40f2f2f2988a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678638"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="870ac-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="870ac-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="870ac-103">通知分析工具的例外狀況處理回溯階段已開始回溯函式。</span><span class="sxs-lookup"><span data-stu-id="870ac-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="870ac-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="870ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="870ac-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="870ac-106">[in]要回溯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="870ac-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="870ac-107">備註</span><span class="sxs-lookup"><span data-stu-id="870ac-107">Remarks</span></span>  
 <span data-ttu-id="870ac-108">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="870ac-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="870ac-109">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="870ac-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="870ac-110">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="870ac-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="870ac-111">需求</span><span class="sxs-lookup"><span data-stu-id="870ac-111">Requirements</span></span>  
 <span data-ttu-id="870ac-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="870ac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="870ac-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="870ac-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="870ac-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="870ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="870ac-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="870ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870ac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="870ac-116">See also</span></span>
- [<span data-ttu-id="870ac-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="870ac-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="870ac-118">ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="870ac-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
