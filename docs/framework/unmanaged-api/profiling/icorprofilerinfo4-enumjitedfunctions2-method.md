---
title: ICorProfilerInfo4::EnumJITedFunctions2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862200"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="73bd8-102">ICorProfilerInfo4::EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="73bd8-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="73bd8-103">傳回先前已進行 JIT 編譯和 JIT 重新編譯之所有函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="73bd8-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="73bd8-104">這個方法會取代[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)方法，這不會列舉 JIT 重新編譯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="73bd8-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73bd8-105">語法</span><span class="sxs-lookup"><span data-stu-id="73bd8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73bd8-106">參數</span><span class="sxs-lookup"><span data-stu-id="73bd8-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="73bd8-107">脫銷[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="73bd8-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73bd8-108">備註</span><span class="sxs-lookup"><span data-stu-id="73bd8-108">Remarks</span></span>  
 <span data-ttu-id="73bd8-109">這個方法可能會與 `JITCompilation` 回呼（例如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重迭。</span><span class="sxs-lookup"><span data-stu-id="73bd8-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="73bd8-110">傳回的列舉包含 `COR_PRF_FUNCTION::reJitId` 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="73bd8-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="73bd8-111">這個方法取代的[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)方法不會列舉 JIT 重新編譯的識別碼，因為 `COR_PRF_FUNCTION::reJitId` 欄位一律設定為0。</span><span class="sxs-lookup"><span data-stu-id="73bd8-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="73bd8-112">`ICorProfilerInfo4::EnumJITedFunctions` 方法會列舉 JIT 重新編譯的識別碼，因為已正確設定 `COR_PRF_FUNCTION::reJitId` 欄位。</span><span class="sxs-lookup"><span data-stu-id="73bd8-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="73bd8-113">請注意， [ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法可以觸發垃圾收集，而[ICorProfilerInfo3：： EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)則不會。</span><span class="sxs-lookup"><span data-stu-id="73bd8-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="73bd8-114">如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="73bd8-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73bd8-115">需求</span><span class="sxs-lookup"><span data-stu-id="73bd8-115">Requirements</span></span>  
 <span data-ttu-id="73bd8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73bd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73bd8-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73bd8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73bd8-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73bd8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73bd8-119">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73bd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bd8-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="73bd8-120">See also</span></span>

- [<span data-ttu-id="73bd8-121">EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="73bd8-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="73bd8-122">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="73bd8-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="73bd8-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="73bd8-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="73bd8-124">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="73bd8-124">Profiling</span></span>](index.md)
