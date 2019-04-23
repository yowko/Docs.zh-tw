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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23bda470b8b5812b567081ba268ad503ac39ecaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090351"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="c08a8-102">COR_HEAPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="c08a8-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="c08a8-103">提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。</span><span class="sxs-lookup"><span data-stu-id="c08a8-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="c08a8-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c08a8-105">成員</span><span class="sxs-lookup"><span data-stu-id="c08a8-105">Members</span></span>  
  
|<span data-ttu-id="c08a8-106">成員</span><span class="sxs-lookup"><span data-stu-id="c08a8-106">Member</span></span>|<span data-ttu-id="c08a8-107">描述</span><span class="sxs-lookup"><span data-stu-id="c08a8-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="c08a8-108">`true` 如果記憶體回收結構都有效，而且可以列舉堆積;，否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="c08a8-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="c08a8-109">大小，以位元組為單位的目標架構上的指標。</span><span class="sxs-lookup"><span data-stu-id="c08a8-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="c08a8-110">處理序堆積中的邏輯回收數目。</span><span class="sxs-lookup"><span data-stu-id="c08a8-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="c08a8-111">`TRUE` 如果同時啟用 （背景） 記憶體回收;否則， `FALSE`。</span><span class="sxs-lookup"><span data-stu-id="c08a8-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="c08a8-112">成員[CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)列舉，指出是否在工作站或伺服器上執行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="c08a8-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c08a8-113">備註</span><span class="sxs-lookup"><span data-stu-id="c08a8-113">Remarks</span></span>  
 <span data-ttu-id="c08a8-114">執行個體`COR_HEAPINFO`結構由呼叫[ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c08a8-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="c08a8-115">之前列舉在記憶體回收堆積上的物件，您必須一律檢查`areGCStructuresValid`欄位，以確保在堆積中的可列舉的狀態。</span><span class="sxs-lookup"><span data-stu-id="c08a8-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="c08a8-116">如需詳細資訊，請參閱 < [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c08a8-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c08a8-117">需求</span><span class="sxs-lookup"><span data-stu-id="c08a8-117">Requirements</span></span>  
 <span data-ttu-id="c08a8-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c08a8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08a8-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c08a8-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c08a8-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c08a8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c08a8-121">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c08a8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08a8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c08a8-122">See also</span></span>

- [<span data-ttu-id="c08a8-123">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="c08a8-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c08a8-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="c08a8-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
