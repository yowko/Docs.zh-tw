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
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法
取得即將執行或剛執行的 exception 子句（`catch`/`finally`/`filter`）的原生位址和框架資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>參數  
 `pinfo`  
 脫銷描述目前例外狀況子句實例和其相關聯框架之[COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)結構的指標。  
  
## <a name="remarks"></a>備註  
 收到例外狀況通知時，`GetNotifiedExceptionClauseInfo` 可以用來取得即將執行之 exception 子句 /`finally`/`catch`（[ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback）的原生位址和框架資訊（由分析工具接收）或剛執行（[ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)回呼是由 profiler 接收）。  
  
 在上述其中一個 Enter 回呼之後，您可以隨時執行此呼叫，直到收到相符的離開回呼，或在目前的子句中擲回嵌套的例外狀況為止，在此情況下，該子句不會有任何離開通知。 請注意，擲回的例外狀況不可能會將 `filter` exception 子句，因此在此情況下一律會有「離開」通知。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
