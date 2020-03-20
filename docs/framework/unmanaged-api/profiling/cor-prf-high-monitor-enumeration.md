---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175209"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列舉

[.NET Framework 4.5.2 與更新版本提供支援]  
  
除了[在COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)枚舉中找到的標誌外，探測器在載入時可以指定到[ICorProfilerInfo5：：setEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法。  
  
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|沒有設定旗標。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|控制[ICorProfiler 回檔6：：獲取組裝參考](icorprofilercallback6-getassemblyreferences-method.md)回檔，用於在 CLR 程式集引用閉合演練期間添加程式集引用。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|控制[ICorProfiler 回檔7：：模組記憶體符號更新](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)回檔，以更新與記憶體中模組關聯的符號流的更新。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|控制[ICorProfiler Callback9：:DynamicMethod未載入](icorprofilercallback9-dynamicmethodunloaded-method.md)回檔，用於指示動態方法何時被垃圾回收和卸載。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 及更高版本：禁用探測器[的分層編譯](../../../core/whats-new/dotnet-core-3-0.md)。|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 及更高版本：提供與[`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)的羽量級 GC 分析選項。 僅控制[垃圾回收啟動](icorprofilercallback2-garbagecollectionstarted-method.md)、[垃圾回收完成](icorprofilercallback2-garbagecollectionfinished-method.md)和[獲取生成綁定](icorprofilerinfo2-getgenerationbounds-method.md)回檔。 與`COR_PRF_MONITOR_GC`標誌不同，`COR_PRF_HIGH_BASIC_GC`不禁用併發垃圾回收。|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 及更高版本：啟用[移動引用](icorprofilercallback-movedreferences-method.md)和[移動引用2](icorprofilercallback4-movedreferences2-method.md)回檔，僅用於壓縮 G。|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 及更高版本：[`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)與 類似，但僅提供有關大型物件堆 （LOH） 物件分配的資訊。|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。 它對應于COR_PRF_MONITOR枚`COR_PRF_REQUIRE_PROFILE_IMAGE`舉中的標誌[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。 嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。|  
  
## <a name="remarks"></a>備註

標誌`COR_PRF_HIGH_MONITOR`與`pdwEventsHigh`[ICorProfilerInfo5：：getEventMask2](icorprofilerinfo5-geteventmask2-method.md)和[ICorProfilerInfo5：：setEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法的參數一起使用。  
  
從 .NET 框架 4.6.1 開始，將`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`的值從`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`0 更改為 （0x00000002）。 從 .NET 框架 4.7.2 開始，其`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`值`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`從 更改為 。

`COR_PRF_HIGH_MONITOR_IMMUTABLE`旨在成為一個位元遮罩，表示僅在初始化期間才能設置的所有標誌。 嘗試在其他地方更改這些標誌會導致失敗`HRESULT`。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
**標頭：** CorProf.idl、CorProf.h  
  
**程式庫：** CorGuids.lib  
  
**.NET 框架版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
- [COR_PRF_MONITOR 列舉](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 介面](icorprofilerinfo5-interface.md)
