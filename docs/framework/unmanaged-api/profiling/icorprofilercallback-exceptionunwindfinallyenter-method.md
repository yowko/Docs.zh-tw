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
ms.openlocfilehash: 0e6109796d633c5facf5c0b07e0793cb8f7dc77e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549807"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="b3c9e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="b3c9e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="b3c9e-103">通知分析工具的輸入處理的例外狀況回溯階段`finally`包含在指定的函式的子句。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3c9e-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3c9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3c9e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b3c9e-106">[in]包含的函式的識別碼`finally`子句。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c9e-107">備註</span><span class="sxs-lookup"><span data-stu-id="b3c9e-107">Remarks</span></span>  
 <span data-ttu-id="b3c9e-108">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b3c9e-109">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b3c9e-110">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c9e-111">需求</span><span class="sxs-lookup"><span data-stu-id="b3c9e-111">Requirements</span></span>  
 <span data-ttu-id="b3c9e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3c9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c9e-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3c9e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3c9e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3c9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3c9e-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c9e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3c9e-116">See also</span></span>
- [<span data-ttu-id="b3c9e-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b3c9e-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b3c9e-118">GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="b3c9e-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="b3c9e-119">ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="b3c9e-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
