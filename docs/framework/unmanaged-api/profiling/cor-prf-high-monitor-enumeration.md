---
title: COR_PRF_HIGH_MONITOR 列舉
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24fde3901f4a866fb14461533a24f0ce265847ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600124"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="aaa33-102">COR_PRF_HIGH_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="aaa33-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="aaa33-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="aaa33-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="aaa33-104">提供旗標，除了那些常見於[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具，以[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法載入時。</span><span class="sxs-lookup"><span data-stu-id="aaa33-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa33-105">語法</span><span class="sxs-lookup"><span data-stu-id="aaa33-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="aaa33-106">成員</span><span class="sxs-lookup"><span data-stu-id="aaa33-106">Members</span></span>  
  
|<span data-ttu-id="aaa33-107">成員</span><span class="sxs-lookup"><span data-stu-id="aaa33-107">Member</span></span>|<span data-ttu-id="aaa33-108">描述</span><span class="sxs-lookup"><span data-stu-id="aaa33-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="aaa33-109">沒有設定旗標。</span><span class="sxs-lookup"><span data-stu-id="aaa33-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="aaa33-110">控制項[ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼期間 CLR 組件參考關閉查核加入組件參考。</span><span class="sxs-lookup"><span data-stu-id="aaa33-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="aaa33-111">控制項[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)更新記憶體中模組相關聯的符號資料流的回呼。</span><span class="sxs-lookup"><span data-stu-id="aaa33-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="aaa33-112">控制項[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回呼，指出當動態方法已被記憶體回收所收集，並卸載。</span><span class="sxs-lookup"><span data-stu-id="aaa33-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="aaa33-113">代表需要設定檔增強影像的所有 `COR_PRF_HIGH_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="aaa33-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="aaa33-114">它會對應至`COR_PRF_REQUIRE_PROFILE_IMAGE`中的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="aaa33-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="aaa33-115">代表分析工具連結至執行中應用程式之後，可以設定的所有 `COR_PRF_HIGH_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="aaa33-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="aaa33-116">代表只能在初始化期間設定的所有 `COR_PRF_HIGH_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="aaa33-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="aaa33-117">嘗試在其他地方變更這些任何旗標，會產生 `HRESULT` 值來指出失敗。</span><span class="sxs-lookup"><span data-stu-id="aaa33-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa33-118">備註</span><span class="sxs-lookup"><span data-stu-id="aaa33-118">Remarks</span></span>  
 <span data-ttu-id="aaa33-119">`COR_PRF_HIGH_MONITOR`旗標可搭配`pdwEventsHigh`的參數[ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)並[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aaa33-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="aaa33-120">開頭[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]，值`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`從 0 到變更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。</span><span class="sxs-lookup"><span data-stu-id="aaa33-120">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="aaa33-121">從.NET Framework 4.7.2 開始，從變更該值`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`至`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。</span><span class="sxs-lookup"><span data-stu-id="aaa33-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="aaa33-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` 是代表只在初始化期間設定的所有旗標的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="aaa33-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="aaa33-123">嘗試變更任何其他地方會導致失敗的這些旗標`HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="aaa33-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="aaa33-124">需求</span><span class="sxs-lookup"><span data-stu-id="aaa33-124">Requirements</span></span>  
 <span data-ttu-id="aaa33-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa33-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa33-126">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aaa33-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aaa33-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaa33-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaa33-128">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa33-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa33-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaa33-129">See also</span></span>
- [<span data-ttu-id="aaa33-130">分析列舉</span><span class="sxs-lookup"><span data-stu-id="aaa33-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="aaa33-131">COR_PRF_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="aaa33-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="aaa33-132">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="aaa33-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
