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
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894959"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="4d3eb-102">ICorDebugArrayValue 介面</span><span class="sxs-lookup"><span data-stu-id="4d3eb-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="4d3eb-103">ICorDebugHeapValue 的子類別，表示一維或多維陣列。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d3eb-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-104">Methods</span></span>  
  
|<span data-ttu-id="4d3eb-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-105">Method</span></span>|<span data-ttu-id="4d3eb-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d3eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d3eb-107">GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="4d3eb-108">取得陣列中每個維度的基底索引。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="4d3eb-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="4d3eb-110">取得陣列中的元素總數。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="4d3eb-111">GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="4d3eb-112">取得陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="4d3eb-113">GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="4d3eb-114">取得值，表示陣列中的指定元素。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="4d3eb-115">GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="4d3eb-116">取得位於指定位置的專案，將陣列視為以零為基底的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="4d3eb-117">GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="4d3eb-118">取得陣列中元素的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="4d3eb-119">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="4d3eb-120">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="4d3eb-121">HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="4d3eb-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="4d3eb-122">判斷陣列是否有基底索引。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d3eb-123">備註</span><span class="sxs-lookup"><span data-stu-id="4d3eb-123">Remarks</span></span>  
 <span data-ttu-id="4d3eb-124">`ICorDebugArrayValue`支援一維和多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d3eb-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d3eb-126">需求</span><span class="sxs-lookup"><span data-stu-id="4d3eb-126">Requirements</span></span>  
 <span data-ttu-id="4d3eb-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d3eb-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d3eb-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d3eb-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d3eb-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d3eb-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d3eb-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d3eb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d3eb-131">See also</span></span>

- [<span data-ttu-id="4d3eb-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4d3eb-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
