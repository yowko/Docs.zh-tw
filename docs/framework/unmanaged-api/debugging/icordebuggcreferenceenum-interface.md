---
title: ICorDebugGCReferenceEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134637"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="9df8f-102">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9df8f-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="9df8f-103">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="9df8f-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9df8f-104">方法</span><span class="sxs-lookup"><span data-stu-id="9df8f-104">Methods</span></span>  
  
|<span data-ttu-id="9df8f-105">方法</span><span class="sxs-lookup"><span data-stu-id="9df8f-105">Method</span></span>|<span data-ttu-id="9df8f-106">描述</span><span class="sxs-lookup"><span data-stu-id="9df8f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9df8f-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="9df8f-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="9df8f-108">取得指定的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9df8f-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9df8f-109">備註</span><span class="sxs-lookup"><span data-stu-id="9df8f-109">Remarks</span></span>  
 <span data-ttu-id="9df8f-110">`ICorDebugGCReferenceEnum` 介面會執行 "ICorDebugEnum" 介面。</span><span class="sxs-lookup"><span data-stu-id="9df8f-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="9df8f-111">`ICorDebugGCReferenceEnum` 實例會藉由呼叫[ICorDebugProcess5：： EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法來填入[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="9df8f-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="9df8f-112">您可以藉由呼叫[ICorDebugGCReference：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)方法來列舉[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="9df8f-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="9df8f-113">這個方法所填入之集合中的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件代表三種物件：</span><span class="sxs-lookup"><span data-stu-id="9df8f-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="9df8f-114">來自所有 managed 堆疊的物件。</span><span class="sxs-lookup"><span data-stu-id="9df8f-114">Objects from all managed stacks.</span></span> <span data-ttu-id="9df8f-115">這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="9df8f-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="9df8f-116">控制碼資料表中的物件。</span><span class="sxs-lookup"><span data-stu-id="9df8f-116">Objects from the handle table.</span></span> <span data-ttu-id="9df8f-117">這包括模組中的強式參考（`HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT`）和靜態變數。</span><span class="sxs-lookup"><span data-stu-id="9df8f-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="9df8f-118">完成項佇列中的物件。</span><span class="sxs-lookup"><span data-stu-id="9df8f-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="9df8f-119">完成項會佇列根物件，直到完成項執行為止。</span><span class="sxs-lookup"><span data-stu-id="9df8f-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9df8f-120">需求</span><span class="sxs-lookup"><span data-stu-id="9df8f-120">Requirements</span></span>  
 <span data-ttu-id="9df8f-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9df8f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9df8f-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9df8f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9df8f-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9df8f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9df8f-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9df8f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df8f-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="9df8f-125">See also</span></span>

- [<span data-ttu-id="9df8f-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9df8f-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
