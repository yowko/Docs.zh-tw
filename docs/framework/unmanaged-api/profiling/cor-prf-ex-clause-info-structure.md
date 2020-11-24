---
title: COR_PRF_EX_CLAUSE_INFO 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: e8dd9f21803021975f4651ba3e6e5f4d3da0ea82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674992"
---
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO 結構

儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`clauseType`|[COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md)列舉值，這個值會指定程式碼剛剛輸入或留下的例外狀況子句類型。|  
|`programCounter`|子句處理常式的原生進入點，例如 X86 EIP 註冊的內容。|  
|`framePointer`|子句處理常式的邏輯框架指標，例如 X86 EBP 暫存器的內容。|  
|`shadowStackPointer`|陰影堆疊的指標。 此值是 BSP 註冊的內容，而且只適用于 IA64。|  
  
## <a name="remarks"></a>備註  

 收到例外狀況通知時，可以使用[ICorProfilerInfo2：： GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)來取得例外狀況子句的原生位址和框架資訊， (`catch` / `finally` 即將執行或剛剛執行的/篩選) 。  
  
 例外狀況子句的執行牽涉到 (CLR) 的 common language runtime 回呼：  
  
- [ICorProfilerCallback：： ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback：： ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback：： ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback：： ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback：： ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback：： ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析結構](profiling-structures.md)
