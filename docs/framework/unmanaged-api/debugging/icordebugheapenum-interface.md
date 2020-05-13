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
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208534"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="a8f8d-102">ICorDebugHeapEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a8f8d-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="a8f8d-103">為 Managed 堆積上的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="a8f8d-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8f8d-105">方法</span><span class="sxs-lookup"><span data-stu-id="a8f8d-105">Methods</span></span>  
  
|<span data-ttu-id="a8f8d-106">方法</span><span class="sxs-lookup"><span data-stu-id="a8f8d-106">Method</span></span>|<span data-ttu-id="a8f8d-107">描述</span><span class="sxs-lookup"><span data-stu-id="a8f8d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8f8d-108">下一個方法</span><span class="sxs-lookup"><span data-stu-id="a8f8d-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="a8f8d-109">取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積上物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8f8d-110">備註</span><span class="sxs-lookup"><span data-stu-id="a8f8d-110">Remarks</span></span>  
 <span data-ttu-id="a8f8d-111">介面會實 `ICorDebugHeapEnum` ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a8f8d-112">`ICorDebugHeapEnum`實例會藉由呼叫[ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md)方法來填入[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="a8f8d-113">集合中的每個[COR_HEAPOBJECT](cor-heapobject-structure.md)實例都代表堆積上的即時物件，或是未受垃圾收集行程回收但尚未收集的物件。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="a8f8d-114">您可以藉由呼叫[ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md)方法來列舉集合中的[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f8d-115">需求</span><span class="sxs-lookup"><span data-stu-id="a8f8d-115">Requirements</span></span>  
 <span data-ttu-id="a8f8d-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8f8d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f8d-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8f8d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8f8d-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8f8d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8f8d-119">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f8d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f8d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f8d-120">See also</span></span>

- [<span data-ttu-id="a8f8d-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a8f8d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
