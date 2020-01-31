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
ms.openlocfilehash: a430631948230d16e5d04c869625b4c670faaf02
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868638"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="f18ce-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f18ce-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="f18ce-103">取得即將執行或剛執行的 exception 子句（`catch`/`finally`/`filter`）的原生位址和框架資訊。</span><span class="sxs-lookup"><span data-stu-id="f18ce-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="f18ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f18ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="f18ce-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="f18ce-106">脫銷描述目前例外狀況子句實例和其相關聯框架之[COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="f18ce-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f18ce-107">備註</span><span class="sxs-lookup"><span data-stu-id="f18ce-107">Remarks</span></span>  
 <span data-ttu-id="f18ce-108">收到例外狀況通知時，`GetNotifiedExceptionClauseInfo` 可以用來取得即將執行之 exception 子句 /`finally`/`catch`（[ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback）的原生位址和框架資訊（由分析工具接收）或剛執行（[ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)回呼是由 profiler 接收）。</span><span class="sxs-lookup"><span data-stu-id="f18ce-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="f18ce-109">在上述其中一個 Enter 回呼之後，您可以隨時執行此呼叫，直到收到相符的離開回呼，或在目前的子句中擲回嵌套的例外狀況為止，在此情況下，該子句不會有任何離開通知。</span><span class="sxs-lookup"><span data-stu-id="f18ce-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="f18ce-110">請注意，擲回的例外狀況不可能會將 `filter` exception 子句，因此在此情況下一律會有「離開」通知。</span><span class="sxs-lookup"><span data-stu-id="f18ce-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f18ce-111">需求</span><span class="sxs-lookup"><span data-stu-id="f18ce-111">Requirements</span></span>  
 <span data-ttu-id="f18ce-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f18ce-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f18ce-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f18ce-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f18ce-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f18ce-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f18ce-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f18ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18ce-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f18ce-116">See also</span></span>

- [<span data-ttu-id="f18ce-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f18ce-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f18ce-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="f18ce-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
