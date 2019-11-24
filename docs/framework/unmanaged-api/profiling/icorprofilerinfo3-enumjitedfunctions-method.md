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
ms.openlocfilehash: d21a793a88cd7561da9acb7daab2dc3bfecf0fc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449767"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="c9507-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="c9507-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="c9507-103">Returns an enumerator for all functions that were previously JIT-compiled.</span><span class="sxs-lookup"><span data-stu-id="c9507-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9507-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9507-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9507-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9507-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c9507-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span><span class="sxs-lookup"><span data-stu-id="c9507-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9507-107">備註</span><span class="sxs-lookup"><span data-stu-id="c9507-107">Remarks</span></span>  
 <span data-ttu-id="c9507-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="c9507-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="c9507-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="c9507-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9507-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span><span class="sxs-lookup"><span data-stu-id="c9507-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="c9507-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="c9507-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9507-112">需求</span><span class="sxs-lookup"><span data-stu-id="c9507-112">Requirements</span></span>  
 <span data-ttu-id="c9507-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9507-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9507-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9507-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9507-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9507-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9507-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9507-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9507-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9507-117">See also</span></span>

- [<span data-ttu-id="c9507-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="c9507-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c9507-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="c9507-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c9507-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c9507-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
