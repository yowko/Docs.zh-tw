---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572fcee528098a4f2929e07dfae63efc56e93dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599545"
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列舉
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 提供旗標，除了那些常見於[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具，以[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法載入時。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|沒有設定旗標。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|控制項[ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼期間 CLR 組件參考關閉查核加入組件參考。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|控制項[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)更新記憶體中模組相關聯的符號資料流的回呼。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|控制項[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回呼，指出當動態方法已被記憶體回收所收集，並卸載。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。 它會對應至`COR_PRF_REQUIRE_PROFILE_IMAGE`中的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。 嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_HIGH_MONITOR`旗標可搭配`pdwEventsHigh`的參數[ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)並[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
開頭[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]，值`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`從 0 到變更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。 從.NET Framework 4.7.2 開始，從變更該值`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`至`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` 是代表只在初始化期間設定的所有旗標的位元遮罩。 嘗試變更任何其他地方會導致失敗的這些旗標`HRESULT`。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
