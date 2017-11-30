---
title: "ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e5ad1742d6f714b53b109bb99fc288bccd4a3bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="71e1c-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法</span><span class="sxs-lookup"><span data-stu-id="71e1c-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="71e1c-103">取得例外狀況子句的原生位址和框架資訊 (`catch`/`finally`/`filter`) 是即將執行或剛執行。</span><span class="sxs-lookup"><span data-stu-id="71e1c-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e1c-104">語法</span><span class="sxs-lookup"><span data-stu-id="71e1c-104">Syntax</span></span>  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71e1c-105">參數</span><span class="sxs-lookup"><span data-stu-id="71e1c-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="71e1c-106">[out]指標[COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)結構，描述目前例外狀況子句執行個體和其相關聯的框架。</span><span class="sxs-lookup"><span data-stu-id="71e1c-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71e1c-107">備註</span><span class="sxs-lookup"><span data-stu-id="71e1c-107">Remarks</span></span>  
 <span data-ttu-id="71e1c-108">例外狀況會收到通知，`GetNotifiedExceptionClauseInfo`可以用來取得例外狀況子句的原生位址和框架資訊 (`catch`/`finally`/`filter`)，為執行 ([Icorprofilercallback:: Exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)， [icorprofilercallback:: Exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)，或[icorprofilercallback:: Exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)回呼收到程式碼剖析工具) 或剛執行 ([icorprofilercallback:: Exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)， [icorprofilercallback:: Exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)，或[Icorprofilercallback:: Exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)收到分析工具回呼)。</span><span class="sxs-lookup"><span data-stu-id="71e1c-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="71e1c-109">這個呼叫可在任何時間之後的 Enter 回呼上述其中一個直到收到對應的 Leave 回呼或巢狀例外狀況擲回目前子句，則有這個是沒有保留的通知該子句中。</span><span class="sxs-lookup"><span data-stu-id="71e1c-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="71e1c-110">請注意，不可能擲回的例外狀況來逸出`filter`例外狀況子句，所以一律保持通知在此情況下。</span><span class="sxs-lookup"><span data-stu-id="71e1c-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e1c-111">需求</span><span class="sxs-lookup"><span data-stu-id="71e1c-111">Requirements</span></span>  
 <span data-ttu-id="71e1c-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71e1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e1c-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71e1c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71e1c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71e1c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71e1c-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71e1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e1c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71e1c-116">See Also</span></span>  
 [<span data-ttu-id="71e1c-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="71e1c-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="71e1c-118">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="71e1c-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
