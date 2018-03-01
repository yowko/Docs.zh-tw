---
title: "ICorProfilerInfo2::GetArrayObjectInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b20530081f7c9ad32f4702099abacc78e052ebd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="413c5-102">ICorProfilerInfo2::GetArrayObjectInfo 方法</span><span class="sxs-lookup"><span data-stu-id="413c5-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="413c5-103">取得有關陣列物件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="413c5-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="413c5-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="413c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="413c5-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="413c5-106">[in]有效的陣列物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="413c5-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="413c5-107">[in]陣列陣序 （維度數目）。</span><span class="sxs-lookup"><span data-stu-id="413c5-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="413c5-108">[out]陣列，其中包含整數，分別代表陣列的維度的大小。</span><span class="sxs-lookup"><span data-stu-id="413c5-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="413c5-109">[out]包含整數的陣列，代表較低的每個繫結的陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="413c5-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="413c5-110">[out]根據 c + + 慣例配置的陣列的原始緩衝區的位址指標。</span><span class="sxs-lookup"><span data-stu-id="413c5-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="413c5-111">備註</span><span class="sxs-lookup"><span data-stu-id="413c5-111">Remarks</span></span>  
 <span data-ttu-id="413c5-112">`pDimensionSizes`和`pDimensionLowerBounds`是平行的陣列，因此位於每個陣列中相同的索引處的項目都是相同的實體的特性。</span><span class="sxs-lookup"><span data-stu-id="413c5-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413c5-113">需求</span><span class="sxs-lookup"><span data-stu-id="413c5-113">Requirements</span></span>  
 <span data-ttu-id="413c5-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="413c5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413c5-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="413c5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="413c5-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="413c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="413c5-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413c5-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="413c5-118">See Also</span></span>  
 [<span data-ttu-id="413c5-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="413c5-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="413c5-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="413c5-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
