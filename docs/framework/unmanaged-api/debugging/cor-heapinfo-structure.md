---
title: "COR_HEAPINFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991e018c3967693f5b87b71c77cdbadcd4ae0cfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="55182-102">COR_HEAPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="55182-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="55182-103">提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。</span><span class="sxs-lookup"><span data-stu-id="55182-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55182-104">語法</span><span class="sxs-lookup"><span data-stu-id="55182-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="55182-105">成員</span><span class="sxs-lookup"><span data-stu-id="55182-105">Members</span></span>  
  
|<span data-ttu-id="55182-106">成員</span><span class="sxs-lookup"><span data-stu-id="55182-106">Member</span></span>|<span data-ttu-id="55182-107">描述</span><span class="sxs-lookup"><span data-stu-id="55182-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="55182-108">`true`如果記憶體回收結構有效且可以列舉堆積。，否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="55182-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="55182-109">以位元組為單位的目標架構上的指標大小。</span><span class="sxs-lookup"><span data-stu-id="55182-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="55182-110">邏輯記憶體回收堆積中的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="55182-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="55182-111">`TRUE`如果同時啟用 （背景） 記憶體回收。否則， `FALSE`。</span><span class="sxs-lookup"><span data-stu-id="55182-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="55182-112">成員[CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)列舉，指出是否在工作站或伺服器上執行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="55182-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55182-113">備註</span><span class="sxs-lookup"><span data-stu-id="55182-113">Remarks</span></span>  
 <span data-ttu-id="55182-114">執行個體`COR_HEAPINFO`結構由呼叫[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="55182-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="55182-115">之前列舉的物件在記憶體回收堆積上的，您必須一律檢查`areGCStructuresValid`欄位，以確保在堆積中的可列舉的狀態。</span><span class="sxs-lookup"><span data-stu-id="55182-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="55182-116">如需詳細資訊，請參閱[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="55182-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55182-117">需求</span><span class="sxs-lookup"><span data-stu-id="55182-117">Requirements</span></span>  
 <span data-ttu-id="55182-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55182-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55182-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55182-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55182-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55182-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55182-121">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55182-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55182-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="55182-122">See Also</span></span>  
 [<span data-ttu-id="55182-123">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="55182-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="55182-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="55182-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
