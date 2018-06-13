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
ms.openlocfilehash: 25f352a3a6dfae69116d6cda2497d55485b951cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417059"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="b8e83-102">ICorDebugHeapEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b8e83-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="b8e83-103">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="b8e83-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="b8e83-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="b8e83-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8e83-105">方法</span><span class="sxs-lookup"><span data-stu-id="b8e83-105">Methods</span></span>  
  
|<span data-ttu-id="b8e83-106">方法</span><span class="sxs-lookup"><span data-stu-id="b8e83-106">Method</span></span>|<span data-ttu-id="b8e83-107">描述</span><span class="sxs-lookup"><span data-stu-id="b8e83-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8e83-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="b8e83-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="b8e83-109">取得指定的數目[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)包含 managed 堆積上物件的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8e83-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e83-110">備註</span><span class="sxs-lookup"><span data-stu-id="b8e83-110">Remarks</span></span>  
 <span data-ttu-id="b8e83-111">`ICorDebugHeapEnum`介面會實作 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="b8e83-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b8e83-112">`ICorDebugHeapEnum`執行個體填入[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)藉由呼叫的執行個體[icordebugprocess5:: Enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b8e83-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="b8e83-113">每個[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的執行個體代表在堆積上的即時物件或物件不根目錄的任何物件，但尚未收集記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="b8e83-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="b8e83-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)可列舉集合中的物件，藉由呼叫[icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b8e83-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e83-115">需求</span><span class="sxs-lookup"><span data-stu-id="b8e83-115">Requirements</span></span>  
 <span data-ttu-id="b8e83-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e83-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e83-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e83-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e83-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e83-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e83-119">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e83-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e83-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e83-120">See Also</span></span>  
 [<span data-ttu-id="b8e83-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b8e83-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
