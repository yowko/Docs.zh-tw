---
title: ICorDebugHeapSegmentEnum::Next 方法
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178886"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="19d8c-102">ICorDebugHeapSegmentEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="19d8c-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="19d8c-103">獲取包含有關託管堆記憶體區域[資訊的指定](cor-heapobject-structure.md)COR_HEAPOBJECT實例數。</span><span class="sxs-lookup"><span data-stu-id="19d8c-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="19d8c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19d8c-105">參數</span><span class="sxs-lookup"><span data-stu-id="19d8c-105">Parameters</span></span>  
 <span data-ttu-id="19d8c-106">celt</span><span class="sxs-lookup"><span data-stu-id="19d8c-106">celt</span></span>  
 <span data-ttu-id="19d8c-107">[在]要檢索的段數。</span><span class="sxs-lookup"><span data-stu-id="19d8c-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="19d8c-108">區段</span><span class="sxs-lookup"><span data-stu-id="19d8c-108">segments</span></span>  
 <span data-ttu-id="19d8c-109">[出]指標陣列，每個指標都[指向COR_HEAPOBJECT物件](cor-heapobject-structure.md)，該物件提供有關託管堆中記憶體區域的資訊。</span><span class="sxs-lookup"><span data-stu-id="19d8c-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="19d8c-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="19d8c-110">pceltFetched</span></span>  
 <span data-ttu-id="19d8c-111">[出]指向 中實際[返回COR_HEAPOBJECT物件的](cor-heapobject-structure.md)數量的指標`segments`。</span><span class="sxs-lookup"><span data-stu-id="19d8c-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="19d8c-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="19d8c-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19d8c-113">備註</span><span class="sxs-lookup"><span data-stu-id="19d8c-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19d8c-114">需求</span><span class="sxs-lookup"><span data-stu-id="19d8c-114">Requirements</span></span>  
 <span data-ttu-id="19d8c-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19d8c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d8c-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19d8c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19d8c-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19d8c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19d8c-118">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19d8c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d8c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d8c-119">See also</span></span>

- [<span data-ttu-id="19d8c-120">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="19d8c-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="19d8c-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="19d8c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
