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
ms.openlocfilehash: 6cb3a2235325533d5bd943a530a0a8e5b77100e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519940"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="52a8e-102">ICorProfilerInfo4::GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="52a8e-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="52a8e-103">傳回識別 JIT 重新編譯的所有版本指定的函式仍配置的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="52a8e-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="52a8e-104">這包括已後續還原，但尚未釋放 （比方說，當應用程式定義域，其中包含已還原的函式是仍在使用中） 的函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="52a8e-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a8e-105">語法</span><span class="sxs-lookup"><span data-stu-id="52a8e-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52a8e-106">參數</span><span class="sxs-lookup"><span data-stu-id="52a8e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="52a8e-107">[in]`FunctionID`函式執行個體，要列舉的版本。</span><span class="sxs-lookup"><span data-stu-id="52a8e-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="52a8e-108">[in]在中所配置的 JIT 重新編譯識別碼數目`reJitIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="52a8e-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="52a8e-109">[out]JIT 重新編譯識別碼實際數目。</span><span class="sxs-lookup"><span data-stu-id="52a8e-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="52a8e-110">[out]呼叫端配置的陣列會包含指定的函式的 JIT 重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="52a8e-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a8e-111">備註</span><span class="sxs-lookup"><span data-stu-id="52a8e-111">Remarks</span></span>  
 <span data-ttu-id="52a8e-112">`GetReJITIDs` 列舉指定的函式執行個體的作用中 JIT 重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="52a8e-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="52a8e-113">它會遵循相同的使用方式模式與其他`ICorProfilerInfo`接受呼叫端配置緩衝區的函式。</span><span class="sxs-lookup"><span data-stu-id="52a8e-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a8e-114">需求</span><span class="sxs-lookup"><span data-stu-id="52a8e-114">Requirements</span></span>  
 <span data-ttu-id="52a8e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52a8e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a8e-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52a8e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52a8e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a8e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a8e-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a8e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a8e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52a8e-119">See also</span></span>
- [<span data-ttu-id="52a8e-120">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="52a8e-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="52a8e-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="52a8e-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="52a8e-122">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="52a8e-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
