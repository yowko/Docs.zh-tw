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
ms.openlocfilehash: 1cf6f9c5fe8777f3333e449a804a3c3a0a64ff19
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213084"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="4633a-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="4633a-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="4633a-103">取得指定的[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4633a-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4633a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4633a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4633a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4633a-105">Parameters</span></span>  
 <span data-ttu-id="4633a-106">celt</span><span class="sxs-lookup"><span data-stu-id="4633a-106">celt</span></span>  
 <span data-ttu-id="4633a-107">在要抓取的根數目。</span><span class="sxs-lookup"><span data-stu-id="4633a-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="4633a-108">方根</span><span class="sxs-lookup"><span data-stu-id="4633a-108">roots</span></span>  
 <span data-ttu-id="4633a-109">脫銷指標陣列，其中每一個都會指向一個[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件，代表要進行垃圾收集之物件的根。</span><span class="sxs-lookup"><span data-stu-id="4633a-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="4633a-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="4633a-110">pceltFetched</span></span>  
 <span data-ttu-id="4633a-111">脫銷中實際傳回之[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件數目的指標 `roots` 。</span><span class="sxs-lookup"><span data-stu-id="4633a-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="4633a-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="4633a-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4633a-113">備註</span><span class="sxs-lookup"><span data-stu-id="4633a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4633a-114">需求</span><span class="sxs-lookup"><span data-stu-id="4633a-114">Requirements</span></span>  
 <span data-ttu-id="4633a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4633a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4633a-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4633a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4633a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4633a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4633a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4633a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4633a-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="4633a-119">See also</span></span>

- [<span data-ttu-id="4633a-120">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4633a-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="4633a-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4633a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
