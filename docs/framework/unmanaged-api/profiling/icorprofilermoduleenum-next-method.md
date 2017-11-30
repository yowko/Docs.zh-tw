---
title: "ICorProfilerModuleEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="27378-102">ICorProfilerModuleEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="27378-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="27378-103">從循序模組集合中取得指定的連續模組數目，從序列中列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="27378-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27378-104">語法</span><span class="sxs-lookup"><span data-stu-id="27378-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27378-105">參數</span><span class="sxs-lookup"><span data-stu-id="27378-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="27378-106">[in] 要擷取的模組數目。</span><span class="sxs-lookup"><span data-stu-id="27378-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="27378-107">[out] `ModuleID` 值的陣列，每個值各代表一個擷取的模組。</span><span class="sxs-lookup"><span data-stu-id="27378-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="27378-108">[out] `ids` 陣列中實際傳回之項目數目的指標。</span><span class="sxs-lookup"><span data-stu-id="27378-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27378-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="27378-109">Return Value</span></span>  
 <span data-ttu-id="27378-110">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="27378-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="27378-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27378-111">HRESULT</span></span>|<span data-ttu-id="27378-112">描述</span><span class="sxs-lookup"><span data-stu-id="27378-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27378-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="27378-113">S_OK</span></span>|<span data-ttu-id="27378-114">已傳回 `celt` 項目。</span><span class="sxs-lookup"><span data-stu-id="27378-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="27378-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="27378-115">S_FALSE</span></span>|<span data-ttu-id="27378-116">傳回少於 `celt` 的項目數，表示列舉已完成。</span><span class="sxs-lookup"><span data-stu-id="27378-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27378-117">需求</span><span class="sxs-lookup"><span data-stu-id="27378-117">Requirements</span></span>  
 <span data-ttu-id="27378-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27378-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27378-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27378-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27378-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27378-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27378-121">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27378-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27378-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27378-122">See Also</span></span>  
 [<span data-ttu-id="27378-123">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="27378-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="27378-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="27378-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
