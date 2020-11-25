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
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo 方法

取得例外狀況子句的原生位址和框架資訊， (`catch` / `finally` / `filter` 即將執行或剛剛執行的) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>參數  

 `pinfo`  
 擴展描述目前的例外狀況子句實例及其關聯框架的 [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) 結構指標。  
  
## <a name="remarks"></a>備註  

 收到例外狀況通知時， `GetNotifiedExceptionClauseInfo` 可以用來取得例外狀況子句的原生位址和框架資訊 (`catch` / `finally` / `filter` 要執行的)  ([ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)回呼是由分析工具接收) 或剛剛執行 ([ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)或[ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)回呼是由分析工具) 所接收。  
  
 您可以在上述其中一個輸入回呼之後的任何時間進行此呼叫，直到收到相符的離開回呼或在目前子句中擲回嵌套例外狀況為止，在這種情況下，不會有該子句的離開通知。 請注意，擲回的例外狀況無法對 `filter` 例外狀況子句進行 escape，因此在此情況下一律會有離開通知。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
