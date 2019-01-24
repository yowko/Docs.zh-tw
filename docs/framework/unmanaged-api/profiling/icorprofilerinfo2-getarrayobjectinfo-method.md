---
title: ICorProfilerInfo2::GetArrayObjectInfo 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0444b6a5fd1bb286df573b1bba7d35b0d2d14a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498839"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="8f84e-102">ICorProfilerInfo2::GetArrayObjectInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8f84e-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="8f84e-103">取得與陣列物件有關的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="8f84e-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f84e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f84e-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f84e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f84e-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8f84e-106">[in]有效的陣列物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8f84e-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="8f84e-107">[in]陣列陣序 （維度數目）。</span><span class="sxs-lookup"><span data-stu-id="8f84e-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="8f84e-108">[out]陣列，其中包含整數，每個均代表陣列的維度的大小。</span><span class="sxs-lookup"><span data-stu-id="8f84e-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="8f84e-109">[out]包含整數的陣列，表示較低的每個繫結的陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="8f84e-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="8f84e-110">[out]根據 c + + 慣例配置陣列的原始緩衝區的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8f84e-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f84e-111">備註</span><span class="sxs-lookup"><span data-stu-id="8f84e-111">Remarks</span></span>  
 <span data-ttu-id="8f84e-112">`pDimensionSizes`和`pDimensionLowerBounds`是平行陣列，因此位於相同的索引，每個陣列中的項目相同的實體特性。</span><span class="sxs-lookup"><span data-stu-id="8f84e-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f84e-113">需求</span><span class="sxs-lookup"><span data-stu-id="8f84e-113">Requirements</span></span>  
 <span data-ttu-id="8f84e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f84e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f84e-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f84e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f84e-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f84e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f84e-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f84e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f84e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f84e-118">See also</span></span>
- [<span data-ttu-id="8f84e-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8f84e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="8f84e-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="8f84e-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
