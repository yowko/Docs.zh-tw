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
ms.openlocfilehash: 8f83d2ac9ca96145fa89b283fec42c71858097f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080822"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="33799-102">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="33799-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="33799-103">為將要記憶體回收的物件提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="33799-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33799-104">方法</span><span class="sxs-lookup"><span data-stu-id="33799-104">Methods</span></span>  
  
|<span data-ttu-id="33799-105">方法</span><span class="sxs-lookup"><span data-stu-id="33799-105">Method</span></span>|<span data-ttu-id="33799-106">描述</span><span class="sxs-lookup"><span data-stu-id="33799-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33799-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="33799-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="33799-108">取得指定的數目[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)包含會進行記憶體回收的物件的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="33799-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33799-109">備註</span><span class="sxs-lookup"><span data-stu-id="33799-109">Remarks</span></span>  
 <span data-ttu-id="33799-110">`ICorDebugGCReferenceEnum`介面會實作 「 ICorDebugEnum"介面。</span><span class="sxs-lookup"><span data-stu-id="33799-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="33799-111">`ICorDebugGCReferenceEnum`執行個體填入[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)藉由呼叫的執行個體[ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="33799-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="33799-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件可以藉由呼叫列舉[ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="33799-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="33799-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)以此方式填入集合中的物件代表三種類型的物件：</span><span class="sxs-lookup"><span data-stu-id="33799-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="33799-114">從所有受管理的堆疊物件。</span><span class="sxs-lookup"><span data-stu-id="33799-114">Objects from all managed stacks.</span></span> <span data-ttu-id="33799-115">這包括即時參考，在 managed 程式碼，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="33799-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="33799-116">控制代碼資料表中的物件。</span><span class="sxs-lookup"><span data-stu-id="33799-116">Objects from the handle table.</span></span> <span data-ttu-id="33799-117">這包括強式參考 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模組中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="33799-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="33799-118">完成項佇列中的物件。</span><span class="sxs-lookup"><span data-stu-id="33799-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="33799-119">完成項佇列根物件，直到執行完成項。</span><span class="sxs-lookup"><span data-stu-id="33799-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33799-120">需求</span><span class="sxs-lookup"><span data-stu-id="33799-120">Requirements</span></span>  
 <span data-ttu-id="33799-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33799-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33799-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33799-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33799-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33799-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="33799-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="33799-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33799-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33799-125">See also</span></span>

- [<span data-ttu-id="33799-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="33799-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
