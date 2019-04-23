---
title: ICorDebugArrayValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168385"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="8d0e4-102">ICorDebugArrayValue 介面</span><span class="sxs-lookup"><span data-stu-id="8d0e4-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="8d0e4-103">ICorDebugHeapValue，表示一維或多維陣列的子類別。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d0e4-104">方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-104">Methods</span></span>  
  
|<span data-ttu-id="8d0e4-105">方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-105">Method</span></span>|<span data-ttu-id="8d0e4-106">描述</span><span class="sxs-lookup"><span data-stu-id="8d0e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d0e4-107">GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="8d0e4-108">取得陣列中的每個維度的基底的索引。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="8d0e4-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="8d0e4-110">取得陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="8d0e4-111">GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="8d0e4-112">取得陣列維度。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="8d0e4-113">GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="8d0e4-114">取得值，表示陣列中指定的項目。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="8d0e4-115">GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="8d0e4-116">取得陣列視為的以零為起始的一維陣列的指定位置的項目。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="8d0e4-117">GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="8d0e4-118">取得陣列中的簡單類型的項目。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="8d0e4-119">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="8d0e4-120">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="8d0e4-121">HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="8d0e4-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="8d0e4-122">判斷陣列是否有基底的索引。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d0e4-123">備註</span><span class="sxs-lookup"><span data-stu-id="8d0e4-123">Remarks</span></span>  
 <span data-ttu-id="8d0e4-124">`ICorDebugArrayValue` 支援一維及多維陣列。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d0e4-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d0e4-126">需求</span><span class="sxs-lookup"><span data-stu-id="8d0e4-126">Requirements</span></span>  
 <span data-ttu-id="8d0e4-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0e4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0e4-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d0e4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d0e4-129">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d0e4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d0e4-130">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d0e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0e4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d0e4-131">See also</span></span>

- [<span data-ttu-id="8d0e4-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8d0e4-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
