---
title: ICorProfilerCallback4::ReJITError 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430103"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="2edc9-102">ICorProfilerCallback4::ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="2edc9-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="2edc9-103">通知分析工具，及時（JIT）編譯器在重新編譯程式中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2edc9-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="2edc9-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2edc9-105">參數</span><span class="sxs-lookup"><span data-stu-id="2edc9-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="2edc9-106">在嘗試進行重新編譯失敗的 `ModuleID`。</span><span class="sxs-lookup"><span data-stu-id="2edc9-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="2edc9-107">在嘗試進行重新編譯失敗之方法的 `MethodDef`。</span><span class="sxs-lookup"><span data-stu-id="2edc9-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="2edc9-108">在重新編譯或標示為重新編譯的函式實例。</span><span class="sxs-lookup"><span data-stu-id="2edc9-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="2edc9-109">如果失敗發生在每個方法的基礎上，而不是每個具現化，此值可能會 `NULL` （例如，如果分析工具指定了不正確元資料標記來重新編譯方法）。</span><span class="sxs-lookup"><span data-stu-id="2edc9-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2edc9-110">在HRESULT，表示失敗的本質。</span><span class="sxs-lookup"><span data-stu-id="2edc9-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="2edc9-111">如需值清單，請參閱 Status HRESULT 一節。</span><span class="sxs-lookup"><span data-stu-id="2edc9-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2edc9-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2edc9-112">Return Value</span></span>  
 <span data-ttu-id="2edc9-113">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="2edc9-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="2edc9-114">狀態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="2edc9-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="2edc9-115">狀態陣列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="2edc9-115">Status array HRESULT</span></span>|<span data-ttu-id="2edc9-116">描述</span><span class="sxs-lookup"><span data-stu-id="2edc9-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="2edc9-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2edc9-117">E_INVALIDARG</span></span>|<span data-ttu-id="2edc9-118">`NULL``moduleID` 或 `methodDef` token。</span><span class="sxs-lookup"><span data-stu-id="2edc9-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="2edc9-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="2edc9-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="2edc9-120">這個模組未完全載入，或正在進行卸載。</span><span class="sxs-lookup"><span data-stu-id="2edc9-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="2edc9-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="2edc9-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="2edc9-122">指定的模組是以動態方式產生（例如，藉由 `Reflection.Emit`），因此這個方法不支援。</span><span class="sxs-lookup"><span data-stu-id="2edc9-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="2edc9-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="2edc9-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="2edc9-124">方法會具現化成為可回收元件，因此無法重新編譯。</span><span class="sxs-lookup"><span data-stu-id="2edc9-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="2edc9-125">請注意，在非反映內容中定義的類型和函式（例如 `List<MyCollectibleStruct>`）可以具現化成為可回收元件。</span><span class="sxs-lookup"><span data-stu-id="2edc9-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="2edc9-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2edc9-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2edc9-127">CLR 在嘗試標記指定的 JIT 重新編譯方法時，已用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="2edc9-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="2edc9-128">其他</span><span class="sxs-lookup"><span data-stu-id="2edc9-128">Other</span></span>|<span data-ttu-id="2edc9-129">作業系統會傳回在 CLR 的控制項外發生的失敗。</span><span class="sxs-lookup"><span data-stu-id="2edc9-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="2edc9-130">例如，如果變更記憶體分頁存取保護的系統呼叫失敗，則會顯示作業系統錯誤。</span><span class="sxs-lookup"><span data-stu-id="2edc9-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2edc9-131">需求</span><span class="sxs-lookup"><span data-stu-id="2edc9-131">Requirements</span></span>  
 <span data-ttu-id="2edc9-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2edc9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2edc9-133">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2edc9-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2edc9-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2edc9-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2edc9-135">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2edc9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edc9-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2edc9-136">See also</span></span>

- [<span data-ttu-id="2edc9-137">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2edc9-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2edc9-138">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="2edc9-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
