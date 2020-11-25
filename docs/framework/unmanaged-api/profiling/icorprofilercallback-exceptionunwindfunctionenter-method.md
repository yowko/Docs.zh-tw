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
ms.openlocfilehash: d3a09a6caf3febd04296fce518ade42e8676a4b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731003"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="9b648-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="9b648-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>

<span data-ttu-id="9b648-103">通知分析工具，例外狀況處理的回溯階段已開始回溯函數。</span><span class="sxs-lookup"><span data-stu-id="9b648-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b648-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b648-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b648-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b648-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9b648-106">\[in] 正在展開的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b648-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b648-107">備註</span><span class="sxs-lookup"><span data-stu-id="9b648-107">Remarks</span></span>  

 <span data-ttu-id="9b648-108">分析工具不應該在其實作為此方法的實中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用搶先式垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="9b648-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9b648-109">如果分析工具在此封鎖並嘗試垃圾收集，則執行時間會封鎖，直到回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="9b648-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9b648-110">分析工具在執行此方法時，不應呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="9b648-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b648-111">需求</span><span class="sxs-lookup"><span data-stu-id="9b648-111">Requirements</span></span>  

 <span data-ttu-id="9b648-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b648-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b648-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b648-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b648-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b648-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b648-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b648-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b648-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b648-116">See also</span></span>

- [<span data-ttu-id="9b648-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9b648-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9b648-118">ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="9b648-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
