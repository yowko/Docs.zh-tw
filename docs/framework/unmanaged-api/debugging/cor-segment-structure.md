---
title: COR_SEGMENT 結構
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faf1be65d308b223490f3ae67eed3d8a2b1688b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223065"
---
# <a name="corsegment-structure"></a><span data-ttu-id="b8e4b-102">COR_SEGMENT 結構</span><span class="sxs-lookup"><span data-stu-id="b8e4b-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="b8e4b-103">包含 Managed 堆積中記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8e4b-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="b8e4b-105">成員</span><span class="sxs-lookup"><span data-stu-id="b8e4b-105">Members</span></span>  
  
|<span data-ttu-id="b8e4b-106">成員</span><span class="sxs-lookup"><span data-stu-id="b8e4b-106">Member</span></span>|<span data-ttu-id="b8e4b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b8e4b-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="b8e4b-108">記憶體區域的起始位址。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="b8e4b-109">記憶體區域的結束位址。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="b8e4b-110">[CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) 列舉成員，表示記憶體區域的層代。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="b8e4b-111">記憶體區域所在的堆積號碼。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="b8e4b-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e4b-113">備註</span><span class="sxs-lookup"><span data-stu-id="b8e4b-113">Remarks</span></span>  
 <span data-ttu-id="b8e4b-114">`COR_SEGMENTS` 結構代表受空控堆積中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="b8e4b-115">`COR_SEGMENTS` 物件是 [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) 集合物件的成員，集合物件的填入是藉由呼叫 [icordebugprocess5:: Enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="b8e4b-116">`heap` 欄位是處理器號碼，其對應到正在回報的堆積。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="b8e4b-117">針對工作站記憶體回收行程，其值一律為零，因為工作站只有一個記憶體回收堆積。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="b8e4b-118">針對伺服器記憶體回收行程，其值對應至堆積附加的處理器。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="b8e4b-119">請注意，可能會有比實際處理器更多或更少記憶體回收堆積，這是因為記憶體回收行程的實作詳細資料所致。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e4b-120">需求</span><span class="sxs-lookup"><span data-stu-id="b8e4b-120">Requirements</span></span>  
 <span data-ttu-id="b8e4b-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e4b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e4b-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e4b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e4b-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e4b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e4b-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e4b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e4b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e4b-125">See also</span></span>

- [<span data-ttu-id="b8e4b-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b8e4b-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b8e4b-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="b8e4b-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
