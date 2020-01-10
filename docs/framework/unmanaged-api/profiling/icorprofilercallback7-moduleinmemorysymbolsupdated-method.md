---
title: ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: b9e404de96fa42509144904f5b2ff58e341578a9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740436"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="0de5c-102">ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="0de5c-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="0de5c-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="0de5c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="0de5c-104">每當與記憶體中模組相關聯的符號資料流程更新時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="0de5c-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de5c-105">語法</span><span class="sxs-lookup"><span data-stu-id="0de5c-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de5c-106">參數</span><span class="sxs-lookup"><span data-stu-id="0de5c-106">Parameters</span></span>  
 <span data-ttu-id="0de5c-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="0de5c-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="0de5c-108">已更新其符號資料流程之記憶體中模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0de5c-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de5c-109">備註</span><span class="sxs-lookup"><span data-stu-id="0de5c-109">Remarks</span></span>  
 <span data-ttu-id="0de5c-110">呼叫[ICorProfilerCallback5：： SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法時，會設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。</span><span class="sxs-lookup"><span data-stu-id="0de5c-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0de5c-111">目前不會針對透過 <xref:System.Reflection.Emit> Api 隱含建立或修改的符號引發此事件。</span><span class="sxs-lookup"><span data-stu-id="0de5c-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="0de5c-112">即使在呼叫 managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法的其中一個多載（其中包含 `rawSymbolStore` 引數來指定元件的符號）時，執行時間還是不會實際將符號資料與模組建立關聯，直到發生[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼為止。</span><span class="sxs-lookup"><span data-stu-id="0de5c-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="0de5c-113">此事件可讓您更好的機會收集這類別模組的符號。</span><span class="sxs-lookup"><span data-stu-id="0de5c-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de5c-114">需求</span><span class="sxs-lookup"><span data-stu-id="0de5c-114">Requirements</span></span>  
 <span data-ttu-id="0de5c-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0de5c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de5c-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0de5c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0de5c-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0de5c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0de5c-118">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de5c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de5c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0de5c-119">See also</span></span>

- [<span data-ttu-id="0de5c-120">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="0de5c-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="0de5c-121">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="0de5c-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="0de5c-122">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="0de5c-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
