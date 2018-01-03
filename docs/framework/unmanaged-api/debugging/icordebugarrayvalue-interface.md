---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="0bb0f-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0bb0f-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="0bb0f-103">表示一維或多維陣列的 ICorDebugHeapValue 的子類別。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bb0f-104">方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-104">Methods</span></span>  
  
|<span data-ttu-id="0bb0f-105">方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-105">Method</span></span>|<span data-ttu-id="0bb0f-106">描述</span><span class="sxs-lookup"><span data-stu-id="0bb0f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bb0f-107">GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="0bb0f-108">取得陣列中的每個維度的基底的索引。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="0bb0f-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="0bb0f-110">取得陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="0bb0f-111">GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="0bb0f-112">取得陣列維度。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="0bb0f-113">GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="0bb0f-114">取得值，代表陣列中指定的項目。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="0bb0f-115">GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="0bb0f-116">取得陣列視為的以零為起始的一維陣列的指定位置處的元素。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="0bb0f-117">GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="0bb0f-118">取得陣列中的元素的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="0bb0f-119">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="0bb0f-120">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="0bb0f-121">HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="0bb0f-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="0bb0f-122">判斷陣列是否有基底的索引。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb0f-123">備註</span><span class="sxs-lookup"><span data-stu-id="0bb0f-123">Remarks</span></span>  
 <span data-ttu-id="0bb0f-124">`ICorDebugArrayValue`支援的一維和多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bb0f-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bb0f-126">需求</span><span class="sxs-lookup"><span data-stu-id="0bb0f-126">Requirements</span></span>  
 <span data-ttu-id="0bb0f-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bb0f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb0f-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bb0f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bb0f-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bb0f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bb0f-130">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb0f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb0f-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="0bb0f-131">See Also</span></span>  
 [<span data-ttu-id="0bb0f-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0bb0f-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
