---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebfc0d763fa1ea14c55a0c61fbf63db65fefe02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137861"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="aa1a9-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="aa1a9-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="aa1a9-103">通知分析工具的輸入處理的例外狀況回溯階段`finally`包含在指定的函式的子句。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa1a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa1a9-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa1a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="aa1a9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="aa1a9-106">[in]包含的函式的識別碼`finally`子句。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa1a9-107">備註</span><span class="sxs-lookup"><span data-stu-id="aa1a9-107">Remarks</span></span>  
 <span data-ttu-id="aa1a9-108">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="aa1a9-109">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="aa1a9-110">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa1a9-111">需求</span><span class="sxs-lookup"><span data-stu-id="aa1a9-111">Requirements</span></span>  
 <span data-ttu-id="aa1a9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa1a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa1a9-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa1a9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa1a9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa1a9-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="aa1a9-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="aa1a9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa1a9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa1a9-116">See also</span></span>

- [<span data-ttu-id="aa1a9-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="aa1a9-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="aa1a9-118">GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="aa1a9-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="aa1a9-119">ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="aa1a9-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
