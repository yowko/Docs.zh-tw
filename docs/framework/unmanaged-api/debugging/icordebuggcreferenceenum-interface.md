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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa8c3160dc779b2475dec63be896af5283cf5346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418161"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="b7247-102">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b7247-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="b7247-103">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="b7247-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7247-104">方法</span><span class="sxs-lookup"><span data-stu-id="b7247-104">Methods</span></span>  
  
|<span data-ttu-id="b7247-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7247-105">Method</span></span>|<span data-ttu-id="b7247-106">描述</span><span class="sxs-lookup"><span data-stu-id="b7247-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7247-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="b7247-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="b7247-108">取得指定的數目[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)含有物件將會進行記憶體回收的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7247-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7247-109">備註</span><span class="sxs-lookup"><span data-stu-id="b7247-109">Remarks</span></span>  
 <span data-ttu-id="b7247-110">`ICorDebugGCReferenceEnum`介面會實作"ICorDebugEnum"介面。</span><span class="sxs-lookup"><span data-stu-id="b7247-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="b7247-111">`ICorDebugGCReferenceEnum`執行個體填入[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)藉由呼叫的執行個體[icordebugprocess5:: Enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b7247-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="b7247-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)可以藉由呼叫列舉物件[ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b7247-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b7247-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)填入這個方法的集合中物件代表物件的三種：</span><span class="sxs-lookup"><span data-stu-id="b7247-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="b7247-114">從所有受管理的堆疊物件。</span><span class="sxs-lookup"><span data-stu-id="b7247-114">Objects from all managed stacks.</span></span> <span data-ttu-id="b7247-115">這包括即時參考 managed 程式碼，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="b7247-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="b7247-116">控制代碼資料表中的物件。</span><span class="sxs-lookup"><span data-stu-id="b7247-116">Objects from the handle table.</span></span> <span data-ttu-id="b7247-117">這包括強式參考 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模組中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="b7247-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="b7247-118">完成項佇列中的物件。</span><span class="sxs-lookup"><span data-stu-id="b7247-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="b7247-119">完成項佇列根物件，直到執行完成項。</span><span class="sxs-lookup"><span data-stu-id="b7247-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7247-120">需求</span><span class="sxs-lookup"><span data-stu-id="b7247-120">Requirements</span></span>  
 <span data-ttu-id="b7247-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7247-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7247-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7247-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7247-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7247-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7247-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7247-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7247-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7247-125">See Also</span></span>  
 [<span data-ttu-id="b7247-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7247-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
