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
ms.openlocfilehash: 90688132b98f8316a4b08988c08b2f7cc7ce0fd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725041"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="b0cb7-102">ICorDebugArrayValue 介面</span><span class="sxs-lookup"><span data-stu-id="b0cb7-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="b0cb7-103">ICorDebugHeapValue 的子類別，表示一維或多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0cb7-104">方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-104">Methods</span></span>  
  
|<span data-ttu-id="b0cb7-105">方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-105">Method</span></span>|<span data-ttu-id="b0cb7-106">描述</span><span class="sxs-lookup"><span data-stu-id="b0cb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0cb7-107">GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="b0cb7-108">取得陣列中每個維度的基底索引。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="b0cb7-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="b0cb7-110">取得陣列中的元素總數。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="b0cb7-111">GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="b0cb7-112">取得陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="b0cb7-113">GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="b0cb7-114">取得值，這個值表示陣列中的指定元素。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="b0cb7-115">GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="b0cb7-116">取得指定位置的專案，將陣列視為以零為基礎的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="b0cb7-117">GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="b0cb7-118">取得陣列中元素的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="b0cb7-119">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="b0cb7-120">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="b0cb7-121">HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="b0cb7-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="b0cb7-122">判斷陣列是否有基底索引。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0cb7-123">備註</span><span class="sxs-lookup"><span data-stu-id="b0cb7-123">Remarks</span></span>  

 <span data-ttu-id="b0cb7-124">`ICorDebugArrayValue` 支援單一維度和多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0cb7-125">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0cb7-126">需求</span><span class="sxs-lookup"><span data-stu-id="b0cb7-126">Requirements</span></span>  

 <span data-ttu-id="b0cb7-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0cb7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0cb7-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0cb7-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0cb7-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0cb7-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0cb7-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0cb7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cb7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0cb7-131">See also</span></span>

- [<span data-ttu-id="b0cb7-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b0cb7-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
