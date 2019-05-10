---
title: COR_GC_REFERENCE 結構
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 848765a4ea9657020bd84e476f992ae69750dda9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617703"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="85ad9-102">COR_GC_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="85ad9-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="85ad9-103">包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="85ad9-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ad9-104">語法</span><span class="sxs-lookup"><span data-stu-id="85ad9-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="85ad9-105">成員</span><span class="sxs-lookup"><span data-stu-id="85ad9-105">Members</span></span>  
  
|<span data-ttu-id="85ad9-106">成員</span><span class="sxs-lookup"><span data-stu-id="85ad9-106">Member</span></span>|<span data-ttu-id="85ad9-107">描述</span><span class="sxs-lookup"><span data-stu-id="85ad9-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="85ad9-108">物件的控制代碼所屬的應用程式定義域的指標。</span><span class="sxs-lookup"><span data-stu-id="85ad9-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="85ad9-109">其值可能是`null`。</span><span class="sxs-lookup"><span data-stu-id="85ad9-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="85ad9-110">ICorDebugValue 或 ICorDebugReferenceValue 介面對應至要進行記憶體回收的物件。</span><span class="sxs-lookup"><span data-stu-id="85ad9-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="85ad9-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出根來自何處。</span><span class="sxs-lookup"><span data-stu-id="85ad9-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="85ad9-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="85ad9-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="85ad9-113">其他要進行記憶體回收的物件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="85ad9-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="85ad9-114">這項資訊視物件的來源所示`type`欄位。</span><span class="sxs-lookup"><span data-stu-id="85ad9-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="85ad9-115">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="85ad9-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85ad9-116">備註</span><span class="sxs-lookup"><span data-stu-id="85ad9-116">Remarks</span></span>  
 <span data-ttu-id="85ad9-117">`type`欄位是[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出參考的來源。</span><span class="sxs-lookup"><span data-stu-id="85ad9-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="85ad9-118">特定`COR_GC_REFERENCE`值可反映出任何下列類型的受管理物件：</span><span class="sxs-lookup"><span data-stu-id="85ad9-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="85ad9-119">從所有受管理的堆疊物件 (`CorGCReferenceType.CorReferenceStack`)。</span><span class="sxs-lookup"><span data-stu-id="85ad9-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="85ad9-120">這包括即時參考，在 managed 程式碼，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="85ad9-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="85ad9-121">控制代碼資料表中的物件 (`CorGCReferenceType.CorHandle*`)。</span><span class="sxs-lookup"><span data-stu-id="85ad9-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="85ad9-122">這包括強式參考 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模組中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="85ad9-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="85ad9-123">完成項佇列中的物件 (`CorGCReferenceType.CorReferenceFinalizer`)。</span><span class="sxs-lookup"><span data-stu-id="85ad9-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="85ad9-124">完成項佇列根物件，直到執行完成項。</span><span class="sxs-lookup"><span data-stu-id="85ad9-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="85ad9-125">`extraData`欄位包含額外的資料，取決於參考的來源 （或類型）。</span><span class="sxs-lookup"><span data-stu-id="85ad9-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="85ad9-126">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="85ad9-126">Possible values are:</span></span>  
  
- <span data-ttu-id="85ad9-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="85ad9-127">`DependentSource`.</span></span> <span data-ttu-id="85ad9-128">如果`type`已`CorGCREferenceType.CorHandleStrongDependent`，這個欄位是物件，如果保持運作，根目錄的物件進行記憶體回收在`COR_GC_REFERENCE.Location`。</span><span class="sxs-lookup"><span data-stu-id="85ad9-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="85ad9-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="85ad9-129">`RefCount`.</span></span> <span data-ttu-id="85ad9-130">如果`type`是`CorGCREferenceType.CorHandleStrongRefCount`，這個欄位是控制代碼的參考計數。</span><span class="sxs-lookup"><span data-stu-id="85ad9-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="85ad9-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="85ad9-131">`Size`.</span></span> <span data-ttu-id="85ad9-132">如果`type`是`CorGCREferenceType.CorHandleStrongSizedByref`，這個欄位是記憶體回收行程，導出物件根物件樹狀結構的最後大小。</span><span class="sxs-lookup"><span data-stu-id="85ad9-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="85ad9-133">請注意，這項計算不一定是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="85ad9-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85ad9-134">需求</span><span class="sxs-lookup"><span data-stu-id="85ad9-134">Requirements</span></span>  
 <span data-ttu-id="85ad9-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85ad9-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ad9-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85ad9-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85ad9-137">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85ad9-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85ad9-138">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ad9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ad9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85ad9-139">See also</span></span>

- [<span data-ttu-id="85ad9-140">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="85ad9-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="85ad9-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="85ad9-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
