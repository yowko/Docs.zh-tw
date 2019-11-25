---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: fc0251624738a06d1be7081ebd099e97f7278a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283133"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列舉

[.NET Framework 4.5.2 與更新版本提供支援]  
  
除了在 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) 列舉中找到的旗標，可供分析工具在載入時指定給 [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) 方法，另外還提供其他旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|沒有設定旗標。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|控制 [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) 回呼，以在 CLR 組件參考結束查核期間，加入組件參考。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|控制與記憶體中模組相關聯之符號資料流程更新的[ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)回呼。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|控制[ICorProfilerCallback9：:D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回呼，以指出動態方法何時已進行垃圾收集和卸載。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|僅限 .NET Core 3.0 和更新版本：停用分析工具的[分層式編譯](../../../core/whats-new/dotnet-core-3-0.md)。|
|`COR_PRF_HIGH_BASIC_GC`|僅限 .NET Core 3.0 和更新版本：提供輕量 GC 的程式碼剖析選項，相較于[`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)。 僅控制[GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)、 [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)和[GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)回呼。 不同于 `COR_PRF_MONITOR_GC` 旗標，`COR_PRF_HIGH_BASIC_GC` 不會停用並行垃圾收集。|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|僅限 .NET Core 3.0 和更新版本：僅啟用[MovedReferences](icorprofilercallback-movedreferences-method.md)和[MovedReferences2](icorprofilercallback4-movedreferences2-method.md)回呼來壓縮 gc。|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|僅限 .NET Core 3.0 和更新版本：類似于[`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)，但只提供大型物件堆積（LOH）之物件配置的相關資訊。|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。 其對應於 `COR_PRF_REQUIRE_PROFILE_IMAGE`COR_PRF_MONITOR[ 列舉中的 ](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) 旗標。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。 嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。|  
  
## <a name="remarks"></a>備註

`COR_PRF_HIGH_MONITOR` 旗標需與 {2&gt;ICorProfilerInfo5::GetEventMask2&lt;2} 和 {3&gt;ICorProfilerInfo5::SetEventMask2&lt;3} 方法的 `pdwEventsHigh` 參數搭配使用。  
  
從 .NET Framework 4.6.1 開始，`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 的值從0變更為 `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` （0x00000002）。 從 .NET Framework 4.7.2 開始，其值從 `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` 變更為 `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` 的目的是一個位元遮罩，代表只能在初始化期間設定的所有旗標。 嘗試在其他位置變更其中任何旗標會導致失敗的 `HRESULT`。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
**標頭：** CorProf.idl、CorProf.h  
  
**程式庫：** CorGuids.lib  
  
**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
