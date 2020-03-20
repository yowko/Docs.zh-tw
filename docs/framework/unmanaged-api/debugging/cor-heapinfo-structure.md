---
title: COR_HEAPINFO 結構
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179314"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="cc720-102">COR_HEAPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="cc720-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="cc720-103">提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。</span><span class="sxs-lookup"><span data-stu-id="cc720-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc720-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc720-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="cc720-105">成員</span><span class="sxs-lookup"><span data-stu-id="cc720-105">Members</span></span>  
  
|<span data-ttu-id="cc720-106">member</span><span class="sxs-lookup"><span data-stu-id="cc720-106">Member</span></span>|<span data-ttu-id="cc720-107">描述</span><span class="sxs-lookup"><span data-stu-id="cc720-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="cc720-108">`true`如果垃圾回收結構有效，並且可以枚舉堆;如果垃圾回收結構有效，則為堆。否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="cc720-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="cc720-109">目標體系結構上指標的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="cc720-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="cc720-110">進程中的邏輯垃圾回收堆數。</span><span class="sxs-lookup"><span data-stu-id="cc720-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="cc720-111">`TRUE`如果啟用併發（後臺）垃圾回收;如果啟用了併發（後臺）垃圾回收;否則， `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="cc720-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="cc720-112">[CorDebugGCType](cordebuggctype-enumeration.md)枚舉的成員，用於指示垃圾回收器是在工作站上運行還是伺服器上運行。</span><span class="sxs-lookup"><span data-stu-id="cc720-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc720-113">備註</span><span class="sxs-lookup"><span data-stu-id="cc720-113">Remarks</span></span>  
 <span data-ttu-id="cc720-114">結構的`COR_HEAPINFO`實例通過調用[ICorDebugProcess5：：：getGCHeap資訊](icordebugprocess5-getgcheapinformation-method.md)方法返回。</span><span class="sxs-lookup"><span data-stu-id="cc720-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="cc720-115">在枚舉垃圾回收堆上的物件之前，必須始終檢查該`areGCStructuresValid`欄位以確保堆處於枚舉狀態。</span><span class="sxs-lookup"><span data-stu-id="cc720-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="cc720-116">有關詳細資訊，請參閱[ICorDebugProcess5：：getGCHeap資訊](icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cc720-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc720-117">需求</span><span class="sxs-lookup"><span data-stu-id="cc720-117">Requirements</span></span>  
 <span data-ttu-id="cc720-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc720-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc720-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc720-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc720-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc720-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc720-121">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc720-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc720-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc720-122">See also</span></span>

- [<span data-ttu-id="cc720-123">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="cc720-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="cc720-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="cc720-124">Debugging</span></span>](index.md)
