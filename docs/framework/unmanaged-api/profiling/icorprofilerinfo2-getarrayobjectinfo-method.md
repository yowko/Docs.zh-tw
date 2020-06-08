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
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497347"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="047be-102">ICorProfilerInfo2::GetArrayObjectInfo 方法</span><span class="sxs-lookup"><span data-stu-id="047be-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="047be-103">取得陣列物件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="047be-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047be-104">語法</span><span class="sxs-lookup"><span data-stu-id="047be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="047be-105">參數</span><span class="sxs-lookup"><span data-stu-id="047be-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="047be-106">在有效陣列物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="047be-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="047be-107">在陣列的順位（維度數目）。</span><span class="sxs-lookup"><span data-stu-id="047be-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="047be-108">脫銷包含整數的陣列，每個都代表陣列的維度大小。</span><span class="sxs-lookup"><span data-stu-id="047be-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="047be-109">脫銷包含整數的陣列，每個都代表陣列維度的下限。</span><span class="sxs-lookup"><span data-stu-id="047be-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="047be-110">脫銷陣列的原始緩衝區位址指標，根據 c + + 慣例配置。</span><span class="sxs-lookup"><span data-stu-id="047be-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="047be-111">備註</span><span class="sxs-lookup"><span data-stu-id="047be-111">Remarks</span></span>  
 <span data-ttu-id="047be-112">`pDimensionSizes`和 `pDimensionLowerBounds` 是平行陣列，因此位於每個陣列中相同索引的元素都是相同實體的特性。</span><span class="sxs-lookup"><span data-stu-id="047be-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="047be-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="047be-113">Requirements</span></span>  
 <span data-ttu-id="047be-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="047be-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="047be-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="047be-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="047be-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="047be-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="047be-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="047be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047be-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="047be-118">See also</span></span>

- [<span data-ttu-id="047be-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="047be-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="047be-120">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="047be-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
