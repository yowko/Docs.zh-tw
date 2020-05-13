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
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210172"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="581b1-102">ICorDebugHeapSegmentEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="581b1-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="581b1-103">取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積的記憶體區域相關資訊。</span><span class="sxs-lookup"><span data-stu-id="581b1-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="581b1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="581b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="581b1-105">Parameters</span></span>  
 <span data-ttu-id="581b1-106">celt</span><span class="sxs-lookup"><span data-stu-id="581b1-106">celt</span></span>  
 <span data-ttu-id="581b1-107">在要抓取的區段數目。</span><span class="sxs-lookup"><span data-stu-id="581b1-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="581b1-108">區段</span><span class="sxs-lookup"><span data-stu-id="581b1-108">segments</span></span>  
 <span data-ttu-id="581b1-109">脫銷指標的陣列，其中每一個都會指向一個[COR_HEAPOBJECT](cor-heapobject-structure.md)物件，以提供受控堆積中的記憶體區域相關資訊。</span><span class="sxs-lookup"><span data-stu-id="581b1-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="581b1-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="581b1-110">pceltFetched</span></span>  
 <span data-ttu-id="581b1-111">脫銷中實際傳回之[COR_HEAPOBJECT](cor-heapobject-structure.md)物件數目的指標 `segments` 。</span><span class="sxs-lookup"><span data-stu-id="581b1-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="581b1-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="581b1-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="581b1-113">備註</span><span class="sxs-lookup"><span data-stu-id="581b1-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="581b1-114">需求</span><span class="sxs-lookup"><span data-stu-id="581b1-114">Requirements</span></span>  
 <span data-ttu-id="581b1-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="581b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="581b1-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="581b1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="581b1-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="581b1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="581b1-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="581b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581b1-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="581b1-119">See also</span></span>

- [<span data-ttu-id="581b1-120">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="581b1-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="581b1-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="581b1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
