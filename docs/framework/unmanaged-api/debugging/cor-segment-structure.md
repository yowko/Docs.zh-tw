---
title: "COR_SEGMENT 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="8106a-102">COR_SEGMENT 結構</span><span class="sxs-lookup"><span data-stu-id="8106a-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="8106a-103">包含 Managed 堆積中記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8106a-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8106a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8106a-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="8106a-105">成員</span><span class="sxs-lookup"><span data-stu-id="8106a-105">Members</span></span>  
  
|<span data-ttu-id="8106a-106">成員</span><span class="sxs-lookup"><span data-stu-id="8106a-106">Member</span></span>|<span data-ttu-id="8106a-107">描述</span><span class="sxs-lookup"><span data-stu-id="8106a-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="8106a-108">記憶體區域的起始位址。</span><span class="sxs-lookup"><span data-stu-id="8106a-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="8106a-109">記憶體區域的結束位址。</span><span class="sxs-lookup"><span data-stu-id="8106a-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="8106a-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)列舉的成員，表示記憶體區域的層代。</span><span class="sxs-lookup"><span data-stu-id="8106a-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="8106a-111">記憶體區域所在堆積數目。</span><span class="sxs-lookup"><span data-stu-id="8106a-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="8106a-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="8106a-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8106a-113">備註</span><span class="sxs-lookup"><span data-stu-id="8106a-113">Remarks</span></span>  
 <span data-ttu-id="8106a-114">`COR_SEGMENTS`結構表示的 managed 堆積中記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="8106a-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="8106a-115">`COR_SEGMENTS`物件是成員的[ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件，會填入呼叫[icordebugprocess5:: Enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8106a-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="8106a-116">`heap`欄位則是處理器數目，其對應到所回報的堆積。</span><span class="sxs-lookup"><span data-stu-id="8106a-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="8106a-117">用於工作站記憶體回收行程，其值永遠是零，因為工作站必須只有一個記憶體回收堆積。</span><span class="sxs-lookup"><span data-stu-id="8106a-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="8106a-118">伺服器記憶體回收行程，其值會對應至堆積附加至該處理器。</span><span class="sxs-lookup"><span data-stu-id="8106a-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="8106a-119">請注意可能會有更多或更少記憶體回收堆積比實際處理器由於記憶體回收行程的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8106a-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8106a-120">需求</span><span class="sxs-lookup"><span data-stu-id="8106a-120">Requirements</span></span>  
 <span data-ttu-id="8106a-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8106a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8106a-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8106a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8106a-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8106a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8106a-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8106a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8106a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="8106a-125">See Also</span></span>  
 [<span data-ttu-id="8106a-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="8106a-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8106a-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="8106a-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
