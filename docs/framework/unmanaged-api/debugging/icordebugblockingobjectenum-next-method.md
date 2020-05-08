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
ms.openlocfilehash: 0ef49d2d833841eac62b2b964a0fdc902b4fb6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894764"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="d0aa0-102">ICorDebugBlockingObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="d0aa0-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="d0aa0-103">從列舉中取得指定數目的[CorDebugBlockingObject](cordebugblockingobject-structure.md)物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0aa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0aa0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0aa0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0aa0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d0aa0-106">在要取得的物件數目。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="d0aa0-107">脫銷[CorDebugBlockingObject](cordebugblockingobject-structure.md)物件的指標陣列。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d0aa0-108">脫銷已抓取物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0aa0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d0aa0-109">Return Value</span></span>  
 <span data-ttu-id="d0aa0-110">這個方法會傳回下列特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="d0aa0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0aa0-111">HRESULT</span></span>|<span data-ttu-id="d0aa0-112">描述</span><span class="sxs-lookup"><span data-stu-id="d0aa0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0aa0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0aa0-113">S_OK</span></span>|<span data-ttu-id="d0aa0-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d0aa0-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d0aa0-115">S_FALSE</span></span>|<span data-ttu-id="d0aa0-116">`pceltFetched` 不等於 `celt`。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0aa0-117">備註</span><span class="sxs-lookup"><span data-stu-id="d0aa0-117">Remarks</span></span>  
 <span data-ttu-id="d0aa0-118">這個方法的功能就像一般的 COM 列舉值。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="d0aa0-119">輸入陣列值的大小`celt`至少必須為。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="d0aa0-120">陣列將會填入列舉中的下一個`celt`值，或所有剩餘的值（如果少於`celt`保留）。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="d0aa0-121">當這個方法傳回時`pceltFetched` ，將會填入已抓取的值數目。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="d0aa0-122">如果`values`包含不正確指標或指向小於`celt`的緩衝區，或如果`pceltFetched`是不正確指標，則結果會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0aa0-123">雖然不需要釋放[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構，但它裡面的 "ICorDebugValue" 介面必須釋放。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0aa0-124">需求</span><span class="sxs-lookup"><span data-stu-id="d0aa0-124">Requirements</span></span>  
 <span data-ttu-id="d0aa0-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0aa0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0aa0-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0aa0-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0aa0-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0aa0-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0aa0-128">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0aa0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0aa0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0aa0-129">See also</span></span>

- [<span data-ttu-id="d0aa0-130">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="d0aa0-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="d0aa0-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0aa0-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d0aa0-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="d0aa0-132">Debugging</span></span>](index.md)
