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
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132326"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="0e21f-102">COR_HEAPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="0e21f-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="0e21f-103">提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。</span><span class="sxs-lookup"><span data-stu-id="0e21f-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e21f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e21f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0e21f-105">Members</span><span class="sxs-lookup"><span data-stu-id="0e21f-105">Members</span></span>  
  
|<span data-ttu-id="0e21f-106">成員</span><span class="sxs-lookup"><span data-stu-id="0e21f-106">Member</span></span>|<span data-ttu-id="0e21f-107">描述</span><span class="sxs-lookup"><span data-stu-id="0e21f-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="0e21f-108">`true` 垃圾收集結構是否有效，而且可以列舉堆積;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="0e21f-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="0e21f-109">目標架構上指標的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0e21f-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="0e21f-110">進程中的邏輯垃圾收集堆積數目。</span><span class="sxs-lookup"><span data-stu-id="0e21f-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="0e21f-111">如果已啟用並行（背景）垃圾收集，`TRUE`否則，`FALSE`。</span><span class="sxs-lookup"><span data-stu-id="0e21f-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="0e21f-112">[CorDebugGCType](cordebuggctype-enumeration.md)列舉的成員，表示垃圾收集行程是否在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="0e21f-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e21f-113">備註</span><span class="sxs-lookup"><span data-stu-id="0e21f-113">Remarks</span></span>  
 <span data-ttu-id="0e21f-114">藉由呼叫[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法，會傳回 `COR_HEAPINFO` 結構的實例。</span><span class="sxs-lookup"><span data-stu-id="0e21f-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="0e21f-115">列舉垃圾收集堆積上的物件之前，您必須務必檢查 [`areGCStructuresValid`] 欄位，以確保堆積處於可列舉的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e21f-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="0e21f-116">如需詳細資訊，請參閱[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0e21f-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e21f-117">需求</span><span class="sxs-lookup"><span data-stu-id="0e21f-117">Requirements</span></span>  
 <span data-ttu-id="0e21f-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e21f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e21f-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e21f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e21f-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e21f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e21f-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e21f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e21f-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e21f-122">See also</span></span>

- [<span data-ttu-id="0e21f-123">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="0e21f-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0e21f-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="0e21f-124">Debugging</span></span>](index.md)
