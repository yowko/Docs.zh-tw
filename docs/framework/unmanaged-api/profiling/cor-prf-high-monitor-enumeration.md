---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92ba2b5eac5eb1368a7d7ccf3b666886f4ca92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列舉
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 提供除了中找到的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具[icorprofilerinfo5:: Seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法在載入時。  
  
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
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|控制項[icorprofilercallback6:: Getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼，以在 CLR 組件參考結束查核期間加入的組件參考。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|控制項[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)更新記憶體中模組相關聯的符號資料流的回呼。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|控制項[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回呼，以指出當動態方法已被記憶體回收收集並卸載。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。 它會對應至`COR_PRF_REQUIRE_PROFILE_IMAGE`加上旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|代表分析工具連結至執行中應用程式之後，可以設定的所有 `COR_PRF_HIGH_MONITOR` 旗標。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|代表只能在初始化期間設定的所有 `COR_PRF_HIGH_MONITOR` 旗標。 嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_HIGH_MONITOR`旗標可搭配`pdwEventsHigh`參數[icorprofilerinfo5:: Geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)和[icorprofilerinfo5:: Seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
從開始[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]，值`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`變更從 0 到`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。 從.NET Framework 4.7.2 開始，其值變更從`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`至`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` 就是要代表只在初始化期間設定的所有旗標的位元遮罩。 嘗試變更任何其他地方會導致失敗的這些旗標`HRESULT`。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
