---
title: "COR_PRF_HIGH_MONITOR 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df931796b32b6bea49e8b69da02d39e6a4803e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列舉
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 提供除了中找到的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具[icorprofilerinfo5:: Seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法在載入時。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|沒有設定旗標。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|控制項[icorprofilercallback6:: Getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼，以在 CLR 組件參考結束查核期間加入的組件參考。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|控制項[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)更新記憶體中模組相關聯的符號資料流的回呼。|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|代表需要分析增強型映像的所有 `COR_PRF_HIGH_MONITOR` 旗標。 它會對應至`COR_PRF_REQUIRE_PROFILE_IMAGE`加上旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|代表只能在初始化期間設定的所有 `COR_PRF_HIGH_MONITOR` 旗標。 嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_HIGH_MONITOR`旗標可搭配`pdwEventsHigh`參數[icorprofilerinfo5:: Geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)和[icorprofilerinfo5:: Seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
 從開始[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]，值`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`變更從 0 到`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
