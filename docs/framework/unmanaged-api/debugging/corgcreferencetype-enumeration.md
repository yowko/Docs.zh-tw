---
title: "CorGCReferenceType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b314580f7628eca68a3996aaafb362081c6ed705
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="9cbab-102">CorGCReferenceType 列舉</span><span class="sxs-lookup"><span data-stu-id="9cbab-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="9cbab-103">識別要進行記憶體回收的物件來源。</span><span class="sxs-lookup"><span data-stu-id="9cbab-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cbab-104">語法</span><span class="sxs-lookup"><span data-stu-id="9cbab-104">Syntax</span></span>  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="9cbab-105">成員</span><span class="sxs-lookup"><span data-stu-id="9cbab-105">Members</span></span>  
  
|<span data-ttu-id="9cbab-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="9cbab-106">Member name</span></span>|<span data-ttu-id="9cbab-107">描述</span><span class="sxs-lookup"><span data-stu-id="9cbab-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="9cbab-108">物件控制代碼資料表中的強式參考控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9cbab-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="9cbab-109">控制代碼已釘選的強式參考物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="9cbab-110">控制代碼的弱式參考物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="9cbab-111">物件的控制代碼弱式參考計數物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="9cbab-112">物件的控制代碼參考計數物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="9cbab-113">物件的控制代碼相依物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="9cbab-114">物件控制代碼資料表中的非同步固定物件。</span><span class="sxs-lookup"><span data-stu-id="9cbab-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="9cbab-115">強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。</span><span class="sxs-lookup"><span data-stu-id="9cbab-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="9cbab-116">從 managed 堆疊的參考。</span><span class="sxs-lookup"><span data-stu-id="9cbab-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="9cbab-117">完成項佇列中的參考。</span><span class="sxs-lookup"><span data-stu-id="9cbab-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="9cbab-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="9cbab-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="9cbab-119">傳回只有強式參考控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="9cbab-120">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="9cbab-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="9cbab-121">傳回只弱式參考控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="9cbab-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="9cbab-122">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="9cbab-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="9cbab-123">傳回控制代碼資料表中的所有參考。</span><span class="sxs-lookup"><span data-stu-id="9cbab-123">Return all references from the handle table.</span></span> <span data-ttu-id="9cbab-124">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="9cbab-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cbab-125">備註</span><span class="sxs-lookup"><span data-stu-id="9cbab-125">Remarks</span></span>  
 <span data-ttu-id="9cbab-126">`CorGCReferenceType`列舉可用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9cbab-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="9cbab-127">值為`type`欄位[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)結構，它會指出來源的參考或控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9cbab-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="9cbab-128">做為`types`引數[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)方法，它會指定要包含在列舉中的控制代碼的類型。</span><span class="sxs-lookup"><span data-stu-id="9cbab-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cbab-129">需求</span><span class="sxs-lookup"><span data-stu-id="9cbab-129">Requirements</span></span>  
 <span data-ttu-id="9cbab-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cbab-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cbab-131">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cbab-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cbab-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cbab-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cbab-133">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cbab-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbab-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cbab-134">See Also</span></span>  
 [<span data-ttu-id="9cbab-135">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="9cbab-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
