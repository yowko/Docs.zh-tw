---
title: "ICorDebugHeapSegmentEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b477631b5920401127d34b2304485bd32c3d78f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="ba651-102">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ba651-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="ba651-103">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="ba651-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="ba651-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="ba651-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba651-105">方法</span><span class="sxs-lookup"><span data-stu-id="ba651-105">Methods</span></span>  
  
|<span data-ttu-id="ba651-106">方法</span><span class="sxs-lookup"><span data-stu-id="ba651-106">Method</span></span>|<span data-ttu-id="ba651-107">描述</span><span class="sxs-lookup"><span data-stu-id="ba651-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba651-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="ba651-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="ba651-109">取得指定的數目[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)包含 managed 堆積的區域相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ba651-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba651-110">備註</span><span class="sxs-lookup"><span data-stu-id="ba651-110">Remarks</span></span>  
 <span data-ttu-id="ba651-111">`ICorDebugHeapSegmentEnum`介面會實作 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="ba651-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="ba651-112">`ICorDebugHeapSegmentEnum`執行個體填入[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)藉由呼叫的執行個體[icordebugprocess5:: Enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ba651-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="ba651-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)可列舉集合中的物件，藉由呼叫[icordebugheapsegmentenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ba651-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="ba651-114">`ICorDebugHeapSegmentEnum`集合物件列舉的所有記憶體區域，可能會包含受管理的物件，但它並不保證 managed 的物件實際位於這些區域。</span><span class="sxs-lookup"><span data-stu-id="ba651-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="ba651-115">它可以包含空白或保留的記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba651-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba651-116">需求</span><span class="sxs-lookup"><span data-stu-id="ba651-116">Requirements</span></span>  
 <span data-ttu-id="ba651-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba651-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba651-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba651-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba651-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba651-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba651-120">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba651-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba651-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba651-121">See Also</span></span>  
 [<span data-ttu-id="ba651-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ba651-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
