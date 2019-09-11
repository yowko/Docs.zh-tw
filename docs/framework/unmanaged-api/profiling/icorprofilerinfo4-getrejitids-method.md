---
title: ICorProfilerInfo4::GetReJITIDs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855948"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="788e5-102">ICorProfilerInfo4::GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="788e5-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="788e5-103">傳回識別碼的陣列，識別仍然配置的指定函式的所有 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="788e5-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="788e5-104">這包括 JIT 重新編譯的函式版本，這些函數之後已還原但尚未釋放（例如，當包含已還原函式的應用程式域仍在使用中時）。</span><span class="sxs-lookup"><span data-stu-id="788e5-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788e5-105">語法</span><span class="sxs-lookup"><span data-stu-id="788e5-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="788e5-106">參數</span><span class="sxs-lookup"><span data-stu-id="788e5-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="788e5-107">在`FunctionID`要列舉版本之函式實例的。</span><span class="sxs-lookup"><span data-stu-id="788e5-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="788e5-108">在在`reJitIds`陣列中配置的 JIT 重新編譯識別碼數目。</span><span class="sxs-lookup"><span data-stu-id="788e5-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="788e5-109">脫銷JIT 重新編譯識別碼的實際數目。</span><span class="sxs-lookup"><span data-stu-id="788e5-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="788e5-110">脫銷呼叫端配置的陣列，其中將包含所指定函式的 JIT 重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="788e5-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="788e5-111">備註</span><span class="sxs-lookup"><span data-stu-id="788e5-111">Remarks</span></span>  
 <span data-ttu-id="788e5-112">`GetReJITIDs`列舉指定函式實例之使用中 JIT 重新編譯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="788e5-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="788e5-113">它會遵循與其他`ICorProfilerInfo`接受呼叫者配置緩衝區的函式相同的使用模式。</span><span class="sxs-lookup"><span data-stu-id="788e5-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788e5-114">需求</span><span class="sxs-lookup"><span data-stu-id="788e5-114">Requirements</span></span>  
 <span data-ttu-id="788e5-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="788e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="788e5-116">**標頭：** Corprof.idl .idl，Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="788e5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="788e5-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="788e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="788e5-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="788e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788e5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="788e5-119">See also</span></span>

- [<span data-ttu-id="788e5-120">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="788e5-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="788e5-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="788e5-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="788e5-122">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="788e5-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
