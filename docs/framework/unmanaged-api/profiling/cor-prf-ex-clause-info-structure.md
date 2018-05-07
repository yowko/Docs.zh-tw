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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3cf8b8735fc10b741d13b041eedc3e96607bef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corprfexclauseinfo-structure"></a>COR_PRF_EX_CLAUSE_INFO 結構
儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`clauseType`|值為[COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)列舉，指定例外狀況子句的程式碼輸入或留下的類型。|  
|`programCounter`|子句的處理常式的原生進入點 — 比方說，X86 EIP 暫存器的內容。|  
|`framePointer`|子句的處理常式的邏輯框架指標 — 比方說，X86 EBP 暫存器的內容。|  
|`shadowStackPointer`|陰影堆疊指標。 此值是 BSP 暫存器的內容，而且只適用於 IA64。|  
  
## <a name="remarks"></a>備註  
 例外狀況會收到通知， [icorprofilerinfo2:: Getnotifiedexceptionclauseinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)可以用來取得例外狀況子句的原生位址和框架資訊 (`catch` / `finally`/篩選) 是即將執行或剛執行。  
  
 例外狀況子句執行包含這些回呼，從 common language runtime (CLR):  
  
-   [Icorprofilercallback:: Exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [Icorprofilercallback:: Exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [Icorprofilercallback:: Exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [Icorprofilercallback:: Exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [Icorprofilercallback:: Exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [Icorprofilercallback:: Exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
