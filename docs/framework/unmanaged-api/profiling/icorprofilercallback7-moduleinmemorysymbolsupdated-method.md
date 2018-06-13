---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455810"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="30dd1-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="30dd1-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="30dd1-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="30dd1-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="30dd1-104">每次更新記憶體中模組相關聯的符號資料流時，通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="30dd1-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dd1-105">語法</span><span class="sxs-lookup"><span data-stu-id="30dd1-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30dd1-106">參數</span><span class="sxs-lookup"><span data-stu-id="30dd1-106">Parameters</span></span>  
 <span data-ttu-id="30dd1-107">[輸入] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="30dd1-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="30dd1-108">已更新其符號資料流的記憶體中模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="30dd1-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30dd1-109">備註</span><span class="sxs-lookup"><span data-stu-id="30dd1-109">Remarks</span></span>  
 <span data-ttu-id="30dd1-110">此回呼由設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標時呼叫[ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="30dd1-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30dd1-111">這個事件目前不引發符號以隱含方式建立或修改透過<xref:System.Reflection.Emit>應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="30dd1-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="30dd1-112">即使當符號提供最前面位置的其中一個多載 managed 呼叫<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>方法包含`rawSymbolStore`引數指定的組件，執行階段的符號可能實際上將關聯的符號資料與模組直到之後[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼發生。</span><span class="sxs-lookup"><span data-stu-id="30dd1-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="30dd1-113">這個事件提供的更新版本的機會來收集這類模組的符號。</span><span class="sxs-lookup"><span data-stu-id="30dd1-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30dd1-114">需求</span><span class="sxs-lookup"><span data-stu-id="30dd1-114">Requirements</span></span>  
 <span data-ttu-id="30dd1-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30dd1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30dd1-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30dd1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30dd1-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30dd1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30dd1-118">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30dd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dd1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30dd1-119">See Also</span></span>  
 [<span data-ttu-id="30dd1-120">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="30dd1-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="30dd1-121">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="30dd1-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="30dd1-122">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="30dd1-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
