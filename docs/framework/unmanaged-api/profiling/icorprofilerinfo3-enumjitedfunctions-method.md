---
title: "ICorProfilerInfo3::EnumJITedFunctions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c367ae29cc0daa406356a245f3dc16a671d3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="ea32e-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="ea32e-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="ea32e-103">傳回所有已先前 JIT 編譯的函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ea32e-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea32e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea32e-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea32e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea32e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ea32e-106">[out]指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="ea32e-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea32e-107">備註</span><span class="sxs-lookup"><span data-stu-id="ea32e-107">Remarks</span></span>  
 <span data-ttu-id="ea32e-108">這個方法可能與重疊`JITCompilation`例如回呼[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ea32e-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="ea32e-109">這個方法所傳回的列舉值不包含從以 Ngen.exe 產生的原生映像載入的函式。</span><span class="sxs-lookup"><span data-stu-id="ea32e-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea32e-110">傳回的列舉包含只"0"值的`COR_PRF_FUNCTION::reJitId`欄位。</span><span class="sxs-lookup"><span data-stu-id="ea32e-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="ea32e-111">如果您需要有效`COR_PRF_FUNCTION::reJitId`值，會使用[icorprofilerinfo4:: Enumjitedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ea32e-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea32e-112">需求</span><span class="sxs-lookup"><span data-stu-id="ea32e-112">Requirements</span></span>  
 <span data-ttu-id="ea32e-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea32e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea32e-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea32e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea32e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea32e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea32e-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea32e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea32e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea32e-117">See Also</span></span>  
 [<span data-ttu-id="ea32e-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="ea32e-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="ea32e-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="ea32e-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ea32e-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="ea32e-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
