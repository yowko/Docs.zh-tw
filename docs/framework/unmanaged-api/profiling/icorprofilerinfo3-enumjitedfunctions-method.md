---
title: ICorProfilerInfo3::EnumJITedFunctions 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7525d107fec7229d9b86eee63bde2aaf2d701b1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190297"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="e9e15-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="e9e15-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="e9e15-103">傳回所有已先前 JIT 編譯的函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e9e15-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e15-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9e15-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9e15-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9e15-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e9e15-106">[out]指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="e9e15-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9e15-107">備註</span><span class="sxs-lookup"><span data-stu-id="e9e15-107">Remarks</span></span>  
 <span data-ttu-id="e9e15-108">這個方法可能與重疊`JITCompilation`這類的回呼[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e9e15-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="e9e15-109">這個方法所傳回的列舉值不包含以 Ngen.exe 產生的原生映像從載入的函式。</span><span class="sxs-lookup"><span data-stu-id="e9e15-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9e15-110">傳回的列舉會包含只有"0"值的`COR_PRF_FUNCTION::reJitId`欄位。</span><span class="sxs-lookup"><span data-stu-id="e9e15-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="e9e15-111">如果您需要有效`COR_PRF_FUNCTION::reJitId`值，會使用[ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e9e15-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e15-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9e15-112">Requirements</span></span>  
 <span data-ttu-id="e9e15-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e15-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e15-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9e15-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9e15-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9e15-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9e15-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e15-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e15-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9e15-117">See also</span></span>

- [<span data-ttu-id="e9e15-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="e9e15-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e9e15-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="e9e15-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e9e15-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e9e15-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
