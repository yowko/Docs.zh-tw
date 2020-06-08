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
ms.openlocfilehash: ba15440df79dded95a8afa9438657d064e167f36
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495966"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="4f153-102">ICorProfilerInfo4::GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="4f153-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="4f153-103">傳回識別碼的陣列，識別仍然配置的指定函式的所有 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="4f153-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="4f153-104">這包括 JIT 重新編譯的函式版本，這些函數之後已還原但尚未釋放（例如，當包含已還原函式的應用程式域仍在使用中時）。</span><span class="sxs-lookup"><span data-stu-id="4f153-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f153-105">語法</span><span class="sxs-lookup"><span data-stu-id="4f153-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f153-106">參數</span><span class="sxs-lookup"><span data-stu-id="4f153-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4f153-107">在`FunctionID`要列舉版本之函式實例的。</span><span class="sxs-lookup"><span data-stu-id="4f153-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="4f153-108">在在陣列中配置的 JIT 重新編譯識別碼數目 `reJitIds` 。</span><span class="sxs-lookup"><span data-stu-id="4f153-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="4f153-109">脫銷JIT 重新編譯識別碼的實際數目。</span><span class="sxs-lookup"><span data-stu-id="4f153-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="4f153-110">脫銷呼叫端配置的陣列，其中將包含所指定函式的 JIT 重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="4f153-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f153-111">備註</span><span class="sxs-lookup"><span data-stu-id="4f153-111">Remarks</span></span>  
 <span data-ttu-id="4f153-112">`GetReJITIDs`列舉指定函式實例之使用中 JIT 重新編譯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4f153-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="4f153-113">它會遵循與其他接受呼叫者配置緩衝區的函式相同的使用模式 `ICorProfilerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="4f153-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f153-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="4f153-114">Requirements</span></span>  
 <span data-ttu-id="4f153-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f153-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f153-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f153-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f153-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f153-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f153-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f153-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f153-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f153-119">See also</span></span>

- [<span data-ttu-id="4f153-120">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="4f153-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4f153-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="4f153-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4f153-122">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="4f153-122">Profiling</span></span>](index.md)
