---
title: "ICorProfilerCallback4::ReJITError 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="3d232-102">ICorProfilerCallback4::ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="3d232-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="3d232-103">通知分析工具在 just-in-time (JIT) 編譯器遇到重新編譯程序中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d232-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d232-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d232-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d232-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d232-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3d232-106">[in]`ModuleID`中進行重新編譯失敗的嘗試。</span><span class="sxs-lookup"><span data-stu-id="3d232-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="3d232-107">[in]`MethodDef`失敗的重新編譯嘗試進行會在其上的方法。</span><span class="sxs-lookup"><span data-stu-id="3d232-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="3d232-108">[in]正在重新編譯或標示為進行重新編譯函式執行個體。</span><span class="sxs-lookup"><span data-stu-id="3d232-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="3d232-109">這個值可能是`NULL`若失敗發生的每個方法為基礎而不是以每個具現化的方式 （例如，如果分析工具指定重新編譯方法無效的中繼資料語彙基元）。</span><span class="sxs-lookup"><span data-stu-id="3d232-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3d232-110">[in]指出失敗原因的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3d232-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="3d232-111">請參閱 < 狀態 HRESULT > 一節清單的值。</span><span class="sxs-lookup"><span data-stu-id="3d232-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d232-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3d232-112">Return Value</span></span>  
 <span data-ttu-id="3d232-113">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="3d232-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="3d232-114">狀態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d232-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="3d232-115">狀態陣列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d232-115">Status array HRESULT</span></span>|<span data-ttu-id="3d232-116">描述</span><span class="sxs-lookup"><span data-stu-id="3d232-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="3d232-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3d232-117">E_INVALIDARG</span></span>|<span data-ttu-id="3d232-118">`moduleID`或`methodDef`語彙基元是`NULL`。</span><span class="sxs-lookup"><span data-stu-id="3d232-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="3d232-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="3d232-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="3d232-120">這個模組未完全載入，或正在進行卸載。</span><span class="sxs-lookup"><span data-stu-id="3d232-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="3d232-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="3d232-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="3d232-122">已動態產生指定的模組 (例如，藉由`Reflection.Emit`)，並因此不支援這個方法。</span><span class="sxs-lookup"><span data-stu-id="3d232-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="3d232-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="3d232-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="3d232-124">方法可回收組件中，具現化，因此無法重新編譯。</span><span class="sxs-lookup"><span data-stu-id="3d232-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="3d232-125">請注意，型別和非反映內容中定義的函式 (例如， `List<MyCollectibleStruct>`) 可以具現化成可回收組件。</span><span class="sxs-lookup"><span data-stu-id="3d232-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="3d232-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3d232-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3d232-127">CLR 會嘗試將指定進行 JIT 重新編譯方法標示已用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="3d232-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="3d232-128">其他</span><span class="sxs-lookup"><span data-stu-id="3d232-128">Other</span></span>|<span data-ttu-id="3d232-129">作業系統會傳回在 CLR 的控制項外發生的失敗。</span><span class="sxs-lookup"><span data-stu-id="3d232-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="3d232-130">例如，如果要變更之存取保護的記憶體分頁的系統呼叫失敗，作業系統會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d232-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d232-131">需求</span><span class="sxs-lookup"><span data-stu-id="3d232-131">Requirements</span></span>  
 <span data-ttu-id="3d232-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d232-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d232-133">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d232-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d232-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d232-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d232-135">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d232-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d232-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d232-136">See Also</span></span>  
 [<span data-ttu-id="3d232-137">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3d232-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3d232-138">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="3d232-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
