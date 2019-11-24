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
ms.openlocfilehash: 97b127c9a6aac0a0fefe25faf294791dcd2c8e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436028"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="0812b-102">ICorProfilerInfo2::GetArrayObjectInfo 方法</span><span class="sxs-lookup"><span data-stu-id="0812b-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="0812b-103">Gets detailed information about an array object.</span><span class="sxs-lookup"><span data-stu-id="0812b-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0812b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0812b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0812b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0812b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="0812b-106">[in] The ID of a valid array object.</span><span class="sxs-lookup"><span data-stu-id="0812b-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="0812b-107">[in] The rank (number of dimensions) of the array.</span><span class="sxs-lookup"><span data-stu-id="0812b-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="0812b-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span><span class="sxs-lookup"><span data-stu-id="0812b-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="0812b-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span><span class="sxs-lookup"><span data-stu-id="0812b-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="0812b-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span><span class="sxs-lookup"><span data-stu-id="0812b-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0812b-111">備註</span><span class="sxs-lookup"><span data-stu-id="0812b-111">Remarks</span></span>  
 <span data-ttu-id="0812b-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span><span class="sxs-lookup"><span data-stu-id="0812b-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0812b-113">需求</span><span class="sxs-lookup"><span data-stu-id="0812b-113">Requirements</span></span>  
 <span data-ttu-id="0812b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0812b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0812b-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0812b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0812b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0812b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0812b-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0812b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0812b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="0812b-118">See also</span></span>

- [<span data-ttu-id="0812b-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="0812b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0812b-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="0812b-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
