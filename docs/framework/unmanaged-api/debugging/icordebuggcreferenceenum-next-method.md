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
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178872"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="f19b5-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="f19b5-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="f19b5-103">獲取指定數量的[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例，這些實例包含有關將垃圾回收的物件的資訊。</span><span class="sxs-lookup"><span data-stu-id="f19b5-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f19b5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f19b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="f19b5-105">Parameters</span></span>  
 <span data-ttu-id="f19b5-106">celt</span><span class="sxs-lookup"><span data-stu-id="f19b5-106">celt</span></span>  
 <span data-ttu-id="f19b5-107">[在]要檢索的根數。</span><span class="sxs-lookup"><span data-stu-id="f19b5-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="f19b5-108">根</span><span class="sxs-lookup"><span data-stu-id="f19b5-108">roots</span></span>  
 <span data-ttu-id="f19b5-109">[出]指標陣列，每個指標都指向表示要垃圾回收的物件的根[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="f19b5-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="f19b5-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f19b5-110">pceltFetched</span></span>  
 <span data-ttu-id="f19b5-111">[出]指向中實際返回的物件數[COR_GC_REFERENCE](cor-gc-reference-structure.md)的指標`roots`。</span><span class="sxs-lookup"><span data-stu-id="f19b5-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="f19b5-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f19b5-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f19b5-113">備註</span><span class="sxs-lookup"><span data-stu-id="f19b5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f19b5-114">需求</span><span class="sxs-lookup"><span data-stu-id="f19b5-114">Requirements</span></span>  
 <span data-ttu-id="f19b5-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f19b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f19b5-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f19b5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f19b5-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f19b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f19b5-118">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f19b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19b5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f19b5-119">See also</span></span>

- [<span data-ttu-id="f19b5-120">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f19b5-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="f19b5-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f19b5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
