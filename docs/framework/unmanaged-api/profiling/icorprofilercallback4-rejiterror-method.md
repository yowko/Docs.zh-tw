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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f152279a21f28b54acebbf0be7c65bb73efa70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767471"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="c01d7-102">ICorProfilerCallback4::ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="c01d7-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="c01d7-103">通知分析工具在 just-in-time (JIT) 編譯器發生重新編譯程序中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c01d7-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c01d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c01d7-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c01d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="c01d7-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c01d7-106">[in]`ModuleID`中進行重新編譯失敗的嘗試。</span><span class="sxs-lookup"><span data-stu-id="c01d7-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="c01d7-107">[in]`MethodDef`上失敗的重新編譯嘗試的方法。</span><span class="sxs-lookup"><span data-stu-id="c01d7-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="c01d7-108">[in]正在重新編譯或標示為重新編譯函式執行個體。</span><span class="sxs-lookup"><span data-stu-id="c01d7-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="c01d7-109">這個值可以是`NULL`如果發生失敗而不是以每個具現化的方式以每個方法為基礎 （例如，如果分析工具指定重新編譯方法無效的中繼資料語彙基元）。</span><span class="sxs-lookup"><span data-stu-id="c01d7-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c01d7-110">[in]HRESULT，表示失敗的本質。</span><span class="sxs-lookup"><span data-stu-id="c01d7-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="c01d7-111">請參閱值的狀態 HRESULT 區段的清單。</span><span class="sxs-lookup"><span data-stu-id="c01d7-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c01d7-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="c01d7-112">Return Value</span></span>  
 <span data-ttu-id="c01d7-113">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="c01d7-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="c01d7-114">狀態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="c01d7-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="c01d7-115">狀態陣列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="c01d7-115">Status array HRESULT</span></span>|<span data-ttu-id="c01d7-116">描述</span><span class="sxs-lookup"><span data-stu-id="c01d7-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="c01d7-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c01d7-117">E_INVALIDARG</span></span>|<span data-ttu-id="c01d7-118">`moduleID`或是`methodDef`語彙基元是`NULL`。</span><span class="sxs-lookup"><span data-stu-id="c01d7-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="c01d7-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="c01d7-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="c01d7-120">這個模組未完全載入，或正在進行卸載。</span><span class="sxs-lookup"><span data-stu-id="c01d7-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="c01d7-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="c01d7-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="c01d7-122">動態產生指定的模組 (例如，藉由`Reflection.Emit`)，並因此不支援這個方法。</span><span class="sxs-lookup"><span data-stu-id="c01d7-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="c01d7-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="c01d7-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="c01d7-124">方法可回收組件中，具現化，因此無法重新編譯。</span><span class="sxs-lookup"><span data-stu-id="c01d7-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="c01d7-125">請注意，型別和非反映內容中定義的函式 (例如`List<MyCollectibleStruct>`) 可以具現化成可回收組件。</span><span class="sxs-lookup"><span data-stu-id="c01d7-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="c01d7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c01d7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c01d7-127">CLR 會嘗試將標記指定的方法進行 JIT 重新編譯時已用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="c01d7-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="c01d7-128">其他</span><span class="sxs-lookup"><span data-stu-id="c01d7-128">Other</span></span>|<span data-ttu-id="c01d7-129">作業系統會傳回在 CLR 的控制項外發生的失敗。</span><span class="sxs-lookup"><span data-stu-id="c01d7-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="c01d7-130">例如，如果要變更之存取保護的記憶體分頁的系統呼叫失敗，作業系統會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="c01d7-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c01d7-131">需求</span><span class="sxs-lookup"><span data-stu-id="c01d7-131">Requirements</span></span>  
 <span data-ttu-id="c01d7-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c01d7-133">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c01d7-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c01d7-134">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c01d7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c01d7-135">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c01d7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01d7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01d7-136">See also</span></span>

- [<span data-ttu-id="c01d7-137">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c01d7-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c01d7-138">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="c01d7-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
