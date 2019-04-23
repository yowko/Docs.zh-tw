---
title: ICorDebugHeapSegmentEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137640"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="f8ee1-102">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f8ee1-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="f8ee1-103">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="f8ee1-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8ee1-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8ee1-105">Methods</span></span>  
  
|<span data-ttu-id="f8ee1-106">方法</span><span class="sxs-lookup"><span data-stu-id="f8ee1-106">Method</span></span>|<span data-ttu-id="f8ee1-107">描述</span><span class="sxs-lookup"><span data-stu-id="f8ee1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8ee1-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="f8ee1-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="f8ee1-109">取得指定的數目[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)含有區域資訊的 managed 堆積的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8ee1-110">備註</span><span class="sxs-lookup"><span data-stu-id="f8ee1-110">Remarks</span></span>  
 <span data-ttu-id="f8ee1-111">`ICorDebugHeapSegmentEnum` ICorDebugEnum 介面實作的介面。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f8ee1-112">`ICorDebugHeapSegmentEnum`執行個體填入[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)藉由呼叫的執行個體[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="f8ee1-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的物件可以藉由呼叫列舉[icordebugheapsegmentenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="f8ee1-114">`ICorDebugHeapSegmentEnum`集合物件列舉的所有記憶體區域，可能會包含受管理的物件，但它並不保證受管理的物件實際上位於這些區域。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="f8ee1-115">它可以包含空白或保留的記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8ee1-116">需求</span><span class="sxs-lookup"><span data-stu-id="f8ee1-116">Requirements</span></span>  
 <span data-ttu-id="f8ee1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ee1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8ee1-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8ee1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8ee1-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8ee1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8ee1-120">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ee1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ee1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8ee1-121">See also</span></span>

- [<span data-ttu-id="f8ee1-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f8ee1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
