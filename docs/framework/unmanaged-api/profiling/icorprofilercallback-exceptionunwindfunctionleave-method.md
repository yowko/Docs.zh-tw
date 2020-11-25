---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 9f88a3fde7d7cb5941e3a7f44a7d94056a959ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733915"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="3ee25-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="3ee25-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>

<span data-ttu-id="3ee25-103">通知分析工具，例外狀況處理的回溯階段已完成回溯函式。</span><span class="sxs-lookup"><span data-stu-id="3ee25-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee25-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ee25-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ee25-105">備註</span><span class="sxs-lookup"><span data-stu-id="3ee25-105">Remarks</span></span>  

 <span data-ttu-id="3ee25-106">`ExceptionUnwindFunctionLeave`呼叫方法時，會從堆疊中移除函式實例和其堆疊資料。</span><span class="sxs-lookup"><span data-stu-id="3ee25-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="3ee25-107">分析工具不應該在此呼叫期間封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用搶先式垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3ee25-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3ee25-108">如果分析工具在此封鎖並嘗試垃圾收集，則執行時間會封鎖，直到回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="3ee25-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3ee25-109">此外，在此呼叫期間，分析工具不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="3ee25-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee25-110">需求</span><span class="sxs-lookup"><span data-stu-id="3ee25-110">Requirements</span></span>  

 <span data-ttu-id="3ee25-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ee25-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ee25-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ee25-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ee25-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ee25-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ee25-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ee25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee25-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ee25-115">See also</span></span>

- [<span data-ttu-id="3ee25-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3ee25-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3ee25-117">ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="3ee25-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
