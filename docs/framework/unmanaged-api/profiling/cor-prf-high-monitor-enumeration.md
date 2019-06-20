---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b29fc50e4bda23053c239292956f9b2cd0c628a3
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268075"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="28af8-102">COR_PRF_HIGH_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="28af8-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="28af8-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="28af8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="28af8-104">提供旗標，除了那些常見於[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具，以[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法載入時。</span><span class="sxs-lookup"><span data-stu-id="28af8-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28af8-105">語法</span><span class="sxs-lookup"><span data-stu-id="28af8-105">Syntax</span></span>  
  
```
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
  
## <a name="members"></a><span data-ttu-id="28af8-106">成員</span><span class="sxs-lookup"><span data-stu-id="28af8-106">Members</span></span>  
  
|<span data-ttu-id="28af8-107">成員</span><span class="sxs-lookup"><span data-stu-id="28af8-107">Member</span></span>|<span data-ttu-id="28af8-108">描述</span><span class="sxs-lookup"><span data-stu-id="28af8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="28af8-109">沒有設定旗標。</span><span class="sxs-lookup"><span data-stu-id="28af8-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="28af8-110">控制項[ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼期間 CLR 組件參考關閉查核加入組件參考。</span><span class="sxs-lookup"><span data-stu-id="28af8-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="28af8-111">控制項[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)更新記憶體中模組相關聯的符號資料流的回呼。</span><span class="sxs-lookup"><span data-stu-id="28af8-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="28af8-112">控制項[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回呼，指出當動態方法已被記憶體回收所收集，並卸載。</span><span class="sxs-lookup"><span data-stu-id="28af8-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="28af8-113">.NET core 3.0 和更新版本：停用[分層編譯](../../../core/whats-new/dotnet-core-3-0.md)的程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="28af8-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="28af8-114">.NET core 3.0 和更新版本：提供程式碼剖析選項的 GC 相較於輕量型[ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="28af8-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="28af8-115">只會控制[GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)， [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)，並[GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="28af8-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="28af8-116">不同於`COR_PRF_MONITOR_GC`旗標，`COR_PRF_HIGH_BASIC_GC`不停用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="28af8-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="28af8-117">.NET core 3.0 和更新版本：可讓[MovedReferences](icorprofilercallback-movedreferences-method.md)並[MovedReferences2](icorprofilercallback4-movedreferences2-method.md)壓縮的 Gc 的回呼。</span><span class="sxs-lookup"><span data-stu-id="28af8-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="28af8-118">.NET core 3.0 和更新版本：類似於[ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md)，但上物件配置的大型物件堆積 (LOH) 只會提供資訊。</span><span class="sxs-lookup"><span data-stu-id="28af8-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the Large Object Heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="28af8-119">代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="28af8-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="28af8-120">它會對應至`COR_PRF_REQUIRE_PROFILE_IMAGE`中的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="28af8-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="28af8-121">代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。</span><span class="sxs-lookup"><span data-stu-id="28af8-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="28af8-122">代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。</span><span class="sxs-lookup"><span data-stu-id="28af8-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="28af8-123">嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。</span><span class="sxs-lookup"><span data-stu-id="28af8-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28af8-124">備註</span><span class="sxs-lookup"><span data-stu-id="28af8-124">Remarks</span></span>  
 <span data-ttu-id="28af8-125">`COR_PRF_HIGH_MONITOR`旗標可搭配`pdwEventsHigh`的參數[ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)並[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="28af8-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="28af8-126">從.NET Framework 4.6.1 的值開始`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`變更從 0 到`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。</span><span class="sxs-lookup"><span data-stu-id="28af8-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="28af8-127">從.NET Framework 4.7.2 開始，從變更該值`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`至`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。</span><span class="sxs-lookup"><span data-stu-id="28af8-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="28af8-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` 是代表只在初始化期間設定的所有旗標的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="28af8-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="28af8-129">嘗試變更任何其他地方會導致失敗的這些旗標`HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="28af8-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="28af8-130">需求</span><span class="sxs-lookup"><span data-stu-id="28af8-130">Requirements</span></span>  
 <span data-ttu-id="28af8-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28af8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28af8-132">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28af8-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28af8-133">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28af8-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28af8-134">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28af8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28af8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28af8-135">See also</span></span>

- [<span data-ttu-id="28af8-136">分析列舉</span><span class="sxs-lookup"><span data-stu-id="28af8-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="28af8-137">COR_PRF_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="28af8-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="28af8-138">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="28af8-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
