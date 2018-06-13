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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416799"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="eaeae-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="eaeae-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="eaeae-103">取得指定的數目[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)含有物件將會進行記憶體回收的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaeae-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaeae-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaeae-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eaeae-105">參數</span><span class="sxs-lookup"><span data-stu-id="eaeae-105">Parameters</span></span>  
 <span data-ttu-id="eaeae-106">celt</span><span class="sxs-lookup"><span data-stu-id="eaeae-106">celt</span></span>  
 <span data-ttu-id="eaeae-107">[in]要擷取的根目錄的數目。</span><span class="sxs-lookup"><span data-stu-id="eaeae-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="eaeae-108">根目錄</span><span class="sxs-lookup"><span data-stu-id="eaeae-108">roots</span></span>  
 <span data-ttu-id="eaeae-109">[out]陣列的指標，其中每個指向[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件，代表要進行記憶體回收的物件的根。</span><span class="sxs-lookup"><span data-stu-id="eaeae-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="eaeae-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="eaeae-110">pceltFetched</span></span>  
 <span data-ttu-id="eaeae-111">[out]數目的指標[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)中實際傳回的物件`roots`。</span><span class="sxs-lookup"><span data-stu-id="eaeae-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="eaeae-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="eaeae-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaeae-113">備註</span><span class="sxs-lookup"><span data-stu-id="eaeae-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaeae-114">需求</span><span class="sxs-lookup"><span data-stu-id="eaeae-114">Requirements</span></span>  
 <span data-ttu-id="eaeae-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaeae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaeae-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaeae-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaeae-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaeae-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaeae-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaeae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaeae-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaeae-119">See Also</span></span>  
 [<span data-ttu-id="eaeae-120">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="eaeae-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="eaeae-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eaeae-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
