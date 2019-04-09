---
title: ICorProfilerModuleEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57d8279ba9733e6a381d445d50df56b415353a16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077143"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="b6e32-102">ICorProfilerModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="b6e32-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="b6e32-103">從循序模組集合中取得指定的連續模組數目，從序列中列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="b6e32-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e32-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6e32-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6e32-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6e32-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b6e32-106">[in] 要擷取的模組數目。</span><span class="sxs-lookup"><span data-stu-id="b6e32-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="b6e32-107">[out] `ModuleID` 值的陣列，每個值各代表一個擷取的模組。</span><span class="sxs-lookup"><span data-stu-id="b6e32-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b6e32-108">[out] `ids` 陣列中實際傳回之項目數目的指標。</span><span class="sxs-lookup"><span data-stu-id="b6e32-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6e32-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6e32-109">Return Value</span></span>  
 <span data-ttu-id="b6e32-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6e32-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b6e32-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6e32-111">HRESULT</span></span>|<span data-ttu-id="b6e32-112">描述</span><span class="sxs-lookup"><span data-stu-id="b6e32-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6e32-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6e32-113">S_OK</span></span>|`celt` <span data-ttu-id="b6e32-114">傳回項目。</span><span class="sxs-lookup"><span data-stu-id="b6e32-114">elements were returned.</span></span>|  
|<span data-ttu-id="b6e32-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b6e32-115">S_FALSE</span></span>|<span data-ttu-id="b6e32-116">傳回少於 `celt` 的項目數，表示列舉已完成。</span><span class="sxs-lookup"><span data-stu-id="b6e32-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6e32-117">需求</span><span class="sxs-lookup"><span data-stu-id="b6e32-117">Requirements</span></span>  
 <span data-ttu-id="b6e32-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e32-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e32-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6e32-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6e32-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6e32-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b6e32-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b6e32-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6e32-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e32-122">See also</span></span>

- [<span data-ttu-id="b6e32-123">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b6e32-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="b6e32-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="b6e32-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
