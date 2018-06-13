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
ms.openlocfilehash: b4336978825fbf7844b3ceaf179954f28660f08c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409403"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="6b964-102">ICorDebugBlockingObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6b964-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="6b964-103">取得指定的數目[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)列舉型別，從目前位置開始的物件。</span><span class="sxs-lookup"><span data-stu-id="6b964-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b964-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b964-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b964-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b964-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6b964-106">[in]要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="6b964-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="6b964-107">[out]陣列的指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="6b964-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6b964-108">[out]已擷取的物件數目指標。</span><span class="sxs-lookup"><span data-stu-id="6b964-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b964-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b964-109">Return Value</span></span>  
 <span data-ttu-id="6b964-110">這個方法會傳回下列特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6b964-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="6b964-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b964-111">HRESULT</span></span>|<span data-ttu-id="6b964-112">描述</span><span class="sxs-lookup"><span data-stu-id="6b964-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b964-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b964-113">S_OK</span></span>|<span data-ttu-id="6b964-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="6b964-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b964-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b964-115">S_FALSE</span></span>|<span data-ttu-id="6b964-116">`pceltFetched` 不等於 `celt`。</span><span class="sxs-lookup"><span data-stu-id="6b964-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b964-117">備註</span><span class="sxs-lookup"><span data-stu-id="6b964-117">Remarks</span></span>  
 <span data-ttu-id="6b964-118">此方法的功能，例如一般的 COM 列舉值。</span><span class="sxs-lookup"><span data-stu-id="6b964-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="6b964-119">至少必須為輸入的陣列值的大小`celt`。</span><span class="sxs-lookup"><span data-stu-id="6b964-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="6b964-120">陣列將會填入 [下一步]`celt`值列舉中，或使用的所有其餘的值，如果少於`celt`保留。</span><span class="sxs-lookup"><span data-stu-id="6b964-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="6b964-121">此方法傳回時，`pceltFetched`將會填入已擷取的值數目。</span><span class="sxs-lookup"><span data-stu-id="6b964-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="6b964-122">如果`values`包含無效的指標或指向小於緩衝區`celt`，或如果`pceltFetched`是無效的指標，結果會是未定義。</span><span class="sxs-lookup"><span data-stu-id="6b964-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b964-123">雖然[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構不需要釋出、 釋放需要在其內部的"ICorDebugValue"介面。</span><span class="sxs-lookup"><span data-stu-id="6b964-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
-  
  
## <a name="requirements"></a><span data-ttu-id="6b964-124">需求</span><span class="sxs-lookup"><span data-stu-id="6b964-124">Requirements</span></span>  
 <span data-ttu-id="6b964-125">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b964-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b964-126">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b964-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b964-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b964-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b964-128">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b964-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b964-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b964-129">See Also</span></span>  
 [<span data-ttu-id="6b964-130">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="6b964-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="6b964-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6b964-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6b964-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="6b964-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
