---
title: ICorDebugGCReferenceEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: 43408486fec9cd50222eed08ec2d3397bc11bc18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134612"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="984bb-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="984bb-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="984bb-103">取得指定的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="984bb-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="984bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="984bb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="984bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="984bb-105">Parameters</span></span>  
 <span data-ttu-id="984bb-106">celt</span><span class="sxs-lookup"><span data-stu-id="984bb-106">celt</span></span>  
 <span data-ttu-id="984bb-107">在要抓取的根數目。</span><span class="sxs-lookup"><span data-stu-id="984bb-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="984bb-108">方根</span><span class="sxs-lookup"><span data-stu-id="984bb-108">roots</span></span>  
 <span data-ttu-id="984bb-109">脫銷指標陣列，其中每一個都會指向[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件，代表要進行垃圾收集之物件的根。</span><span class="sxs-lookup"><span data-stu-id="984bb-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="984bb-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="984bb-110">pceltFetched</span></span>  
 <span data-ttu-id="984bb-111">脫銷`roots`中實際傳回之[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="984bb-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="984bb-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="984bb-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="984bb-113">備註</span><span class="sxs-lookup"><span data-stu-id="984bb-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="984bb-114">需求</span><span class="sxs-lookup"><span data-stu-id="984bb-114">Requirements</span></span>  
 <span data-ttu-id="984bb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="984bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="984bb-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="984bb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="984bb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="984bb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="984bb-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="984bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984bb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="984bb-119">See also</span></span>

- [<span data-ttu-id="984bb-120">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="984bb-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="984bb-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="984bb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
