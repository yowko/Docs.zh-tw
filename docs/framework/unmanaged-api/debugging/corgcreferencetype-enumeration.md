---
title: "CorGCReferenceType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45ca1e9c6123a4b22a1645d151e49a0dd65addbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="ff5b5-102">CorGCReferenceType 列舉</span><span class="sxs-lookup"><span data-stu-id="ff5b5-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="ff5b5-103">識別要進行記憶體回收的物件來源。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff5b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff5b5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ff5b5-105">成員</span><span class="sxs-lookup"><span data-stu-id="ff5b5-105">Members</span></span>  
  
|<span data-ttu-id="ff5b5-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="ff5b5-106">Member name</span></span>|<span data-ttu-id="ff5b5-107">說明</span><span class="sxs-lookup"><span data-stu-id="ff5b5-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="ff5b5-108">物件控制代碼資料表中的強式參考控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="ff5b5-109">控制代碼已釘選的強式參考物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="ff5b5-110">控制代碼的弱式參考物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="ff5b5-111">物件的控制代碼弱式參考計數物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="ff5b5-112">物件的控制代碼參考計數物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="ff5b5-113">物件的控制代碼相依物件控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="ff5b5-114">物件控制代碼資料表中的非同步固定物件。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="ff5b5-115">強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="ff5b5-116">從 managed 堆疊的參考。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="ff5b5-117">完成項佇列中的參考。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="ff5b5-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="ff5b5-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="ff5b5-119">傳回只有強式參考控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="ff5b5-120">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="ff5b5-121">傳回只弱式參考控制代碼資料表中。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="ff5b5-122">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="ff5b5-123">傳回控制代碼資料表中的所有參考。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-123">Return all references from the handle table.</span></span> <span data-ttu-id="ff5b5-124">這個值由[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)只方法。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff5b5-125">備註</span><span class="sxs-lookup"><span data-stu-id="ff5b5-125">Remarks</span></span>  
 <span data-ttu-id="ff5b5-126">`CorGCReferenceType`列舉可用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ff5b5-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="ff5b5-127">值為`type`欄位[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)結構，它會指出來源的參考或控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="ff5b5-128">做為`types`引數[icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)方法，它會指定要包含在列舉中的控制代碼的類型。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff5b5-129">需求</span><span class="sxs-lookup"><span data-stu-id="ff5b5-129">Requirements</span></span>  
 <span data-ttu-id="ff5b5-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff5b5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff5b5-131">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff5b5-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff5b5-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff5b5-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff5b5-133">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff5b5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5b5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff5b5-134">See Also</span></span>  
 [<span data-ttu-id="ff5b5-135">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ff5b5-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
