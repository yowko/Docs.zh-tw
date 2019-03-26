---
title: ICorDebugHeapEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a9e423a35ba8c592bbfd806f9087a88ee251e76
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502278"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="fb0e1-102">ICorDebugHeapEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="fb0e1-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="fb0e1-103">取得 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) 執行個體的指定數目，其中包含 Managed 堆積上物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb0e1-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb0e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb0e1-105">Parameters</span></span>  
 <span data-ttu-id="fb0e1-106">celt</span><span class="sxs-lookup"><span data-stu-id="fb0e1-106">celt</span></span>  
 <span data-ttu-id="fb0e1-107">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="fb0e1-108">物件</span><span class="sxs-lookup"><span data-stu-id="fb0e1-108">objects</span></span>  
 <span data-ttu-id="fb0e1-109">[out] 指標陣列，其中每一個指標會指向提供 Managed 堆積上物件之相關資訊的 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="fb0e1-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="fb0e1-110">pceltFetched</span></span>  
 <span data-ttu-id="fb0e1-111">[out] `objects` 中實際傳回之 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) 物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="fb0e1-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb0e1-113">備註</span><span class="sxs-lookup"><span data-stu-id="fb0e1-113">Remarks</span></span>  
 <span data-ttu-id="fb0e1-114">`COR_HEAPOBJECT.type` 欄位是計算巢狀參考數目之 COM 介面的識別項。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="fb0e1-115">這個參考必須由 `ICorDebugHeapEnum::Next` 的呼叫者釋放。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0e1-116">需求</span><span class="sxs-lookup"><span data-stu-id="fb0e1-116">Requirements</span></span>  
 <span data-ttu-id="fb0e1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0e1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0e1-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb0e1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb0e1-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb0e1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb0e1-120">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0e1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0e1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb0e1-121">See also</span></span>
- [<span data-ttu-id="fb0e1-122">ICorDebugHeapEnum 介面</span><span class="sxs-lookup"><span data-stu-id="fb0e1-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="fb0e1-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fb0e1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
