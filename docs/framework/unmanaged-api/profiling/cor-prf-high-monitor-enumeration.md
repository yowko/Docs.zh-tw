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
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="f1aaa-102">COR_PRF_HIGH_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="f1aaa-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="f1aaa-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="f1aaa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="f1aaa-104">除了[在COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)枚舉中找到的標誌外，探測器在載入時可以指定到[ICorProfilerInfo5：：setEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1aaa-105">語法</span><span class="sxs-lookup"><span data-stu-id="f1aaa-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f1aaa-106">成員</span><span class="sxs-lookup"><span data-stu-id="f1aaa-106">Members</span></span>  
  
|<span data-ttu-id="f1aaa-107">member</span><span class="sxs-lookup"><span data-stu-id="f1aaa-107">Member</span></span>|<span data-ttu-id="f1aaa-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1aaa-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="f1aaa-109">沒有設定旗標。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="f1aaa-110">控制[ICorProfiler 回檔6：：獲取組裝參考](icorprofilercallback6-getassemblyreferences-method.md)回檔，用於在 CLR 程式集引用閉合演練期間添加程式集引用。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="f1aaa-111">控制[ICorProfiler 回檔7：：模組記憶體符號更新](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)回檔，以更新與記憶體中模組關聯的符號流的更新。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="f1aaa-112">控制[ICorProfiler Callback9：:DynamicMethod未載入](icorprofilercallback9-dynamicmethodunloaded-method.md)回檔，用於指示動態方法何時被垃圾回收和卸載。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="f1aaa-113">.NET Core 3.0 及更高版本：禁用探測器[的分層編譯](../../../core/whats-new/dotnet-core-3-0.md)。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="f1aaa-114">.NET Core 3.0 及更高版本：提供與[`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)的羽量級 GC 分析選項。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="f1aaa-115">僅控制[垃圾回收啟動](icorprofilercallback2-garbagecollectionstarted-method.md)、[垃圾回收完成](icorprofilercallback2-garbagecollectionfinished-method.md)和[獲取生成綁定](icorprofilerinfo2-getgenerationbounds-method.md)回檔。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="f1aaa-116">與`COR_PRF_MONITOR_GC`標誌不同，`COR_PRF_HIGH_BASIC_GC`不禁用併發垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="f1aaa-117">.NET Core 3.0 及更高版本：啟用[移動引用](icorprofilercallback-movedreferences-method.md)和[移動引用2](icorprofilercallback4-movedreferences2-method.md)回檔，僅用於壓縮 G。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="f1aaa-118">.NET Core 3.0 及更高版本：[`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)與 類似，但僅提供有關大型物件堆 （LOH） 物件分配的資訊。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="f1aaa-119">代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="f1aaa-120">它對應于COR_PRF_MONITOR枚`COR_PRF_REQUIRE_PROFILE_IMAGE`舉中的標誌[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="f1aaa-121">代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="f1aaa-122">代表所有 `COR_PRF_HIGH_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="f1aaa-123">嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1aaa-124">備註</span><span class="sxs-lookup"><span data-stu-id="f1aaa-124">Remarks</span></span>

<span data-ttu-id="f1aaa-125">標誌`COR_PRF_HIGH_MONITOR`與`pdwEventsHigh`[ICorProfilerInfo5：：getEventMask2](icorprofilerinfo5-geteventmask2-method.md)和[ICorProfilerInfo5：：setEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法的參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="f1aaa-126">從 .NET 框架 4.6.1 開始，將`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`的值從`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`0 更改為 （0x00000002）。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="f1aaa-127">從 .NET 框架 4.7.2 開始，其`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`值`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`從 更改為 。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="f1aaa-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`旨在成為一個位元遮罩，表示僅在初始化期間才能設置的所有標誌。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="f1aaa-129">嘗試在其他地方更改這些標誌會導致失敗`HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f1aaa-130">需求</span><span class="sxs-lookup"><span data-stu-id="f1aaa-130">Requirements</span></span>

<span data-ttu-id="f1aaa-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1aaa-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="f1aaa-132">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1aaa-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="f1aaa-133">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1aaa-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="f1aaa-134">**.NET 框架版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1aaa-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aaa-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1aaa-135">See also</span></span>

- [<span data-ttu-id="f1aaa-136">分析列舉</span><span class="sxs-lookup"><span data-stu-id="f1aaa-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="f1aaa-137">COR_PRF_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="f1aaa-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="f1aaa-138">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="f1aaa-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
