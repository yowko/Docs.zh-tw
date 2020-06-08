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
ms.openlocfilehash: f5e4939c814239c297fc0aa88644dc0472b0c419
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500152"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="33a52-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="33a52-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="33a52-103">通知分析工具，例外狀況處理的回溯階段正在輸入 `finally` 包含在指定之函式中的子句。</span><span class="sxs-lookup"><span data-stu-id="33a52-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a52-104">語法</span><span class="sxs-lookup"><span data-stu-id="33a52-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a52-105">參數</span><span class="sxs-lookup"><span data-stu-id="33a52-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="33a52-106">\[in] 包含子句之函式的識別碼 `finally` 。</span><span class="sxs-lookup"><span data-stu-id="33a52-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="33a52-107">備註</span><span class="sxs-lookup"><span data-stu-id="33a52-107">Remarks</span></span>  
 <span data-ttu-id="33a52-108">分析工具不應在此方法的執行中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="33a52-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="33a52-109">如果分析工具在此處封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="33a52-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="33a52-110">分析工具的此方法的執行不應呼叫 managed 程式碼，或以任何方式進行，以造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="33a52-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a52-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="33a52-111">Requirements</span></span>  
 <span data-ttu-id="33a52-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33a52-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a52-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33a52-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33a52-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33a52-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33a52-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a52-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a52-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33a52-116">See also</span></span>

- [<span data-ttu-id="33a52-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="33a52-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="33a52-118">GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="33a52-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="33a52-119">ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="33a52-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
