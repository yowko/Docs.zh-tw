---
title: ICorProfilerFunctionEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62e70a2fe421651aac9a4921ca885c53c864c4f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101799"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="19ea4-102">ICorProfilerFunctionEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="19ea4-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="19ea4-103">從循序函式集合中取得指定的連續函式數目，從序列中列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="19ea4-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ea4-104">語法</span><span class="sxs-lookup"><span data-stu-id="19ea4-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19ea4-105">參數</span><span class="sxs-lookup"><span data-stu-id="19ea4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="19ea4-106">[in] 要擷取的函式數目。</span><span class="sxs-lookup"><span data-stu-id="19ea4-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="19ea4-107">[out] `COR_PRF_FUNCTION` 值的陣列，每個值各代表一個擷取的函式。</span><span class="sxs-lookup"><span data-stu-id="19ea4-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="19ea4-108">[out] `ids` 陣列中實際傳回之函式數目的指標。</span><span class="sxs-lookup"><span data-stu-id="19ea4-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19ea4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="19ea4-109">Return Value</span></span>  
 <span data-ttu-id="19ea4-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="19ea4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="19ea4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19ea4-111">HRESULT</span></span>|<span data-ttu-id="19ea4-112">描述</span><span class="sxs-lookup"><span data-stu-id="19ea4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19ea4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="19ea4-113">S_OK</span></span>|`celt` <span data-ttu-id="19ea4-114">傳回項目。</span><span class="sxs-lookup"><span data-stu-id="19ea4-114">elements were returned.</span></span>|  
|<span data-ttu-id="19ea4-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="19ea4-115">S_FALSE</span></span>|<span data-ttu-id="19ea4-116">傳回少於 `celt` 的項目數，表示列舉已完成。</span><span class="sxs-lookup"><span data-stu-id="19ea4-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19ea4-117">需求</span><span class="sxs-lookup"><span data-stu-id="19ea4-117">Requirements</span></span>  
 <span data-ttu-id="19ea4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19ea4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ea4-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19ea4-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19ea4-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19ea4-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="19ea4-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="19ea4-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19ea4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19ea4-122">See also</span></span>

- [<span data-ttu-id="19ea4-123">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="19ea4-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="19ea4-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="19ea4-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
