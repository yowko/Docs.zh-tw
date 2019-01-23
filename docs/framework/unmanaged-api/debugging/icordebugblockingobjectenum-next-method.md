---
title: ICorDebugBlockingObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: def9d810917495165c7deda9e3dff158582a0e61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566251"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="1d610-102">ICorDebugBlockingObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="1d610-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="1d610-103">取得指定的數目[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)從列舉型別，從目前位置開始的物件。</span><span class="sxs-lookup"><span data-stu-id="1d610-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d610-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d610-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d610-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d610-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1d610-106">[in]若要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="1d610-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="1d610-107">[out]陣列的指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="1d610-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1d610-108">[out]已擷取的物件數目指標。</span><span class="sxs-lookup"><span data-stu-id="1d610-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d610-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d610-109">Return Value</span></span>  
 <span data-ttu-id="1d610-110">這個方法會傳回下列特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1d610-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="1d610-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d610-111">HRESULT</span></span>|<span data-ttu-id="1d610-112">描述</span><span class="sxs-lookup"><span data-stu-id="1d610-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d610-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d610-113">S_OK</span></span>|<span data-ttu-id="1d610-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1d610-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="1d610-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1d610-115">S_FALSE</span></span>|<span data-ttu-id="1d610-116">`pceltFetched` 不等於 `celt`。</span><span class="sxs-lookup"><span data-stu-id="1d610-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d610-117">備註</span><span class="sxs-lookup"><span data-stu-id="1d610-117">Remarks</span></span>  
 <span data-ttu-id="1d610-118">這個方法會如同一般的 COM 列舉值。</span><span class="sxs-lookup"><span data-stu-id="1d610-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="1d610-119">至少必須為輸入的陣列值的大小`celt`。</span><span class="sxs-lookup"><span data-stu-id="1d610-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="1d610-120">陣列會填滿可能的下一步`celt`值的列舉型別中或使用所有剩餘的值，如果少於`celt`保留。</span><span class="sxs-lookup"><span data-stu-id="1d610-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="1d610-121">當這個方法傳回時，`pceltFetched`將會填入已擷取的值數目。</span><span class="sxs-lookup"><span data-stu-id="1d610-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="1d610-122">如果`values`包含無效的指標或指向小於緩衝區`celt`，或如果`pceltFetched`是無效的指標，結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="1d610-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d610-123">雖然[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構不需要釋出，在其內部的"ICorDebugValue 」 介面需要釋出。</span><span class="sxs-lookup"><span data-stu-id="1d610-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d610-124">需求</span><span class="sxs-lookup"><span data-stu-id="1d610-124">Requirements</span></span>  
 <span data-ttu-id="1d610-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d610-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d610-126">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d610-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d610-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d610-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d610-128">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d610-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d610-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d610-129">See also</span></span>
- [<span data-ttu-id="1d610-130">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="1d610-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="1d610-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1d610-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1d610-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="1d610-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
