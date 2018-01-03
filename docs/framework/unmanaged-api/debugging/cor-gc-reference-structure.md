---
title: "COR_GC_REFERENCE 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86604febb7641eef147608e564a27883fdc4bec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreference-structure"></a><span data-ttu-id="a2e7f-102">COR_GC_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="a2e7f-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="a2e7f-103">包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2e7f-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="a2e7f-105">成員</span><span class="sxs-lookup"><span data-stu-id="a2e7f-105">Members</span></span>  
  
|<span data-ttu-id="a2e7f-106">成員</span><span class="sxs-lookup"><span data-stu-id="a2e7f-106">Member</span></span>|<span data-ttu-id="a2e7f-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2e7f-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="a2e7f-108">緩衝區的指標或物件的控制代碼所屬的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="a2e7f-109">其值可能是`null`。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="a2e7f-110">ICorDebugValue 或 ICorDebugReferenceValue 介面對應至要進行記憶體回收的物件。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="a2e7f-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出根來自何處。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="a2e7f-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="a2e7f-113">其他要進行記憶體回收的物件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="a2e7f-114">這項資訊視物件的來源所示`type`欄位。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="a2e7f-115">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e7f-116">備註</span><span class="sxs-lookup"><span data-stu-id="a2e7f-116">Remarks</span></span>  
 <span data-ttu-id="a2e7f-117">`type`欄位是[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出參考的來源。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="a2e7f-118">特定`COR_GC_REFERENCE`值可反映出任何下列種類的受管理物件：</span><span class="sxs-lookup"><span data-stu-id="a2e7f-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="a2e7f-119">從所有受管理的堆疊物件 (`CorGCReferenceType.CorReferenceStack`)。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="a2e7f-120">這包括即時參考 managed 程式碼，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="a2e7f-121">物件控制代碼資料表中的 (`CorGCReferenceType.CorHandle*`)。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="a2e7f-122">這包括強式參考 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模組中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="a2e7f-123">完成項佇列中的物件 (`CorGCReferenceType.CorReferenceFinalizer`)。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="a2e7f-124">完成項佇列根物件，直到執行完成項。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="a2e7f-125">`extraData`欄位包含額外的資料，根據參考的來源 （或類型）。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="a2e7f-126">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="a2e7f-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="a2e7f-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="a2e7f-127">`DependentSource`.</span></span> <span data-ttu-id="a2e7f-128">如果`type`是`CorGCREferenceType.CorHandleStrongDependent`，這個欄位是物件，如果運作，根目錄的物件進行記憶體回收在`COR_GC_REFERENCE.Location`。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="a2e7f-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="a2e7f-129">`RefCount`.</span></span> <span data-ttu-id="a2e7f-130">如果`type`是`CorGCREferenceType.CorHandleStrongRefCount`，這個欄位是控制代碼的參考計數。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="a2e7f-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="a2e7f-131">`Size`.</span></span> <span data-ttu-id="a2e7f-132">如果`type`是`CorGCREferenceType.CorHandleStrongSizedByref`，這個欄位是記憶體回收行程，導出物件根物件樹狀結構的最後大小。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="a2e7f-133">請注意，這項計算不一定是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e7f-134">需求</span><span class="sxs-lookup"><span data-stu-id="a2e7f-134">Requirements</span></span>  
 <span data-ttu-id="a2e7f-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2e7f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e7f-136">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2e7f-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2e7f-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2e7f-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e7f-138">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e7f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e7f-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2e7f-139">See Also</span></span>  
 [<span data-ttu-id="a2e7f-140">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="a2e7f-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="a2e7f-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="a2e7f-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
