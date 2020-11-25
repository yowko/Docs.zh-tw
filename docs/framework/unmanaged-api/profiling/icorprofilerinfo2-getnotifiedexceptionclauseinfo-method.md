---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: b0d94f5004da85caf0460e8f1d1b2d964944b045
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727064"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="ba6cc-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ba6cc-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>

<span data-ttu-id="ba6cc-103">取得例外狀況子句的原生位址和框架資訊， (`catch` / `finally` / `filter` 即將執行或剛剛執行的) 。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba6cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba6cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba6cc-105">Parameters</span></span>  

 `pinfo`  
 <span data-ttu-id="ba6cc-106">擴展描述目前的例外狀況子句實例及其關聯框架的 [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) 結構指標。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba6cc-107">備註</span><span class="sxs-lookup"><span data-stu-id="ba6cc-107">Remarks</span></span>  

 <span data-ttu-id="ba6cc-108">收到例外狀況通知時， `GetNotifiedExceptionClauseInfo` 可以用來取得例外狀況子句的原生位址和框架資訊 (`catch` / `finally` / `filter` 要執行的)  ([ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)回呼是由分析工具接收) 或剛剛執行 ([ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)回呼是由分析工具) 所接收。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="ba6cc-109">您可以在上述其中一個輸入回呼之後的任何時間進行此呼叫，直到收到相符的離開回呼或在目前子句中擲回嵌套例外狀況為止，在這種情況下，不會有該子句的離開通知。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="ba6cc-110">請注意，擲回的例外狀況無法對 `filter` 例外狀況子句進行 escape，因此在此情況下一律會有離開通知。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba6cc-111">需求</span><span class="sxs-lookup"><span data-stu-id="ba6cc-111">Requirements</span></span>  

 <span data-ttu-id="ba6cc-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba6cc-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba6cc-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba6cc-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba6cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba6cc-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba6cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba6cc-116">See also</span></span>

- [<span data-ttu-id="ba6cc-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ba6cc-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ba6cc-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="ba6cc-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
