---
title: ICorDebugHeapEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79ef77e52e14fede9949121e7ec4575d10b820c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775579"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="ee4ce-102">ICorDebugHeapEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ee4ce-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="ee4ce-103">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="ee4ce-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee4ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="ee4ce-105">Methods</span></span>  
  
|<span data-ttu-id="ee4ce-106">方法</span><span class="sxs-lookup"><span data-stu-id="ee4ce-106">Method</span></span>|<span data-ttu-id="ee4ce-107">描述</span><span class="sxs-lookup"><span data-stu-id="ee4ce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee4ce-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="ee4ce-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="ee4ce-109">取得 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) 執行個體的指定數目，其中包含 Managed 堆積上物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee4ce-110">備註</span><span class="sxs-lookup"><span data-stu-id="ee4ce-110">Remarks</span></span>  
 <span data-ttu-id="ee4ce-111">`ICorDebugHeapEnum` ICorDebugEnum 介面實作的介面。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="ee4ce-112">`ICorDebugHeapEnum`執行個體填入[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)藉由呼叫的執行個體[ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="ee4ce-113">每個[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的執行個體代表的是在堆積上的即時物件或物件不根目錄的任何物件，但尚未收集記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="ee4ce-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的物件可以藉由呼叫列舉[icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4ce-115">需求</span><span class="sxs-lookup"><span data-stu-id="ee4ce-115">Requirements</span></span>  
 <span data-ttu-id="ee4ce-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4ce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4ce-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee4ce-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee4ce-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee4ce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee4ce-119">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4ce-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee4ce-120">See also</span></span>

- [<span data-ttu-id="ee4ce-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ee4ce-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
