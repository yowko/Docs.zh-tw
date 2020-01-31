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
ms.openlocfilehash: 6fbb86fc63a26599ae83c81817dbcb9abfb88cc8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864684"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="c256e-102">ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="c256e-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="c256e-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="c256e-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c256e-104">每當與記憶體中模組相關聯的符號資料流程更新時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="c256e-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c256e-105">語法</span><span class="sxs-lookup"><span data-stu-id="c256e-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c256e-106">參數</span><span class="sxs-lookup"><span data-stu-id="c256e-106">Parameters</span></span>  
 <span data-ttu-id="c256e-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="c256e-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="c256e-108">已更新其符號資料流程之記憶體中模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c256e-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c256e-109">備註</span><span class="sxs-lookup"><span data-stu-id="c256e-109">Remarks</span></span>  
 <span data-ttu-id="c256e-110">呼叫[ICorProfilerCallback5：： SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法時，會設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。</span><span class="sxs-lookup"><span data-stu-id="c256e-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c256e-111">目前不會針對透過 <xref:System.Reflection.Emit> Api 隱含建立或修改的符號引發此事件。</span><span class="sxs-lookup"><span data-stu-id="c256e-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="c256e-112">即使在呼叫 managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法的其中一個多載（其中包含 `rawSymbolStore` 引數來指定元件的符號）時，執行時間還是不會實際將符號資料與模組建立關聯，直到發生[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼為止。</span><span class="sxs-lookup"><span data-stu-id="c256e-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="c256e-113">此事件可讓您更好的機會收集這類別模組的符號。</span><span class="sxs-lookup"><span data-stu-id="c256e-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c256e-114">需求</span><span class="sxs-lookup"><span data-stu-id="c256e-114">Requirements</span></span>  
 <span data-ttu-id="c256e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c256e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c256e-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c256e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c256e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c256e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c256e-118">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c256e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c256e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="c256e-119">See also</span></span>

- [<span data-ttu-id="c256e-120">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="c256e-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="c256e-121">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="c256e-121">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="c256e-122">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="c256e-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
