---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 898adf043e425c00d6e311e2f67c53ed65cacb33
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="4b929-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="4b929-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="4b929-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="4b929-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="4b929-104">每次更新記憶體中模組相關聯的符號資料流時，通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="4b929-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b929-105">語法</span><span class="sxs-lookup"><span data-stu-id="4b929-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b929-106">參數</span><span class="sxs-lookup"><span data-stu-id="4b929-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4b929-107">已更新其符號資料流的記憶體中模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b929-107">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b929-108">備註</span><span class="sxs-lookup"><span data-stu-id="4b929-108">Remarks</span></span>  
 <span data-ttu-id="4b929-109">此回呼由設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標時呼叫[ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4b929-109">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b929-110">這個事件目前不引發符號以隱含方式建立或修改透過<xref:System.Reflection.Emit>應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="4b929-110">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="4b929-111">即使當符號提供最前面位置的其中一個多載 managed 呼叫<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>方法包含`rawSymbolStore`引數指定的組件，執行階段的符號可能實際上將關聯的符號資料與模組直到之後[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼發生。</span><span class="sxs-lookup"><span data-stu-id="4b929-111">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="4b929-112">這個事件提供的更新版本的機會來收集這類模組的符號。</span><span class="sxs-lookup"><span data-stu-id="4b929-112">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b929-113">需求</span><span class="sxs-lookup"><span data-stu-id="4b929-113">Requirements</span></span>  
 <span data-ttu-id="4b929-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b929-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b929-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b929-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b929-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b929-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b929-117">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b929-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b929-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b929-118">See Also</span></span>  
 [<span data-ttu-id="4b929-119">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="4b929-119">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="4b929-120">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="4b929-120">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="4b929-121">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="4b929-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
