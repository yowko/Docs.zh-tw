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
ms.openlocfilehash: 08337a118a80d213f16e2a16f744b96f5dde2e7f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496993"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="54f8d-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="54f8d-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="54f8d-103">取得 `catch` / `finally` / `filter` 即將執行或剛執行的例外狀況子句（）的原生位址和框架資訊。</span><span class="sxs-lookup"><span data-stu-id="54f8d-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="54f8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54f8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="54f8d-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="54f8d-106">脫銷描述目前例外狀況子句實例和其相關聯框架之[COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="54f8d-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54f8d-107">備註</span><span class="sxs-lookup"><span data-stu-id="54f8d-107">Remarks</span></span>  
 <span data-ttu-id="54f8d-108">收到例外狀況通知時， `GetNotifiedExceptionClauseInfo` 可以用來取得即將執行之例外狀況子句（）的原生位址和框架資訊（ `catch` / `finally` / `filter` [ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)，或分析工具會收到 ICorProfilerCallback [：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)回呼），或剛剛執行（[ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)， [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)，或[ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)回呼是由分析工具接收）。</span><span class="sxs-lookup"><span data-stu-id="54f8d-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="54f8d-109">在上述其中一個 Enter 回呼之後，您可以隨時執行此呼叫，直到收到相符的離開回呼，或在目前的子句中擲回嵌套的例外狀況為止，在此情況下，該子句不會有任何離開通知。</span><span class="sxs-lookup"><span data-stu-id="54f8d-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="54f8d-110">請注意，所擲回的例外狀況不可能會將 `filter` exception 子句轉義，因此在這種情況下一律會有「離開」通知。</span><span class="sxs-lookup"><span data-stu-id="54f8d-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f8d-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="54f8d-111">Requirements</span></span>  
 <span data-ttu-id="54f8d-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54f8d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f8d-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54f8d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54f8d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54f8d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54f8d-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f8d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f8d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54f8d-116">See also</span></span>

- [<span data-ttu-id="54f8d-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="54f8d-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="54f8d-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="54f8d-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
