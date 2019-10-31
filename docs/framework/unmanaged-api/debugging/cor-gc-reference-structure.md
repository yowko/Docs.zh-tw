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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099148"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="409ef-102">COR_GC_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="409ef-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="409ef-103">包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="409ef-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="409ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="409ef-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="409ef-105">Members</span><span class="sxs-lookup"><span data-stu-id="409ef-105">Members</span></span>  
  
|<span data-ttu-id="409ef-106">成員</span><span class="sxs-lookup"><span data-stu-id="409ef-106">Member</span></span>|<span data-ttu-id="409ef-107">描述</span><span class="sxs-lookup"><span data-stu-id="409ef-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="409ef-108">控制碼或物件所屬之應用程式域的指標。</span><span class="sxs-lookup"><span data-stu-id="409ef-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="409ef-109">其值可能 `null`。</span><span class="sxs-lookup"><span data-stu-id="409ef-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="409ef-110">對應至要進行垃圾收集之物件的 ICorDebugValue 或 ICorDebugReferenceValue 介面。</span><span class="sxs-lookup"><span data-stu-id="409ef-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="409ef-111">指出根來源位置的[CorGCReferenceType](corgcreferencetype-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="409ef-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="409ef-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="409ef-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="409ef-113">有關要進行垃圾收集之物件的其他資料。</span><span class="sxs-lookup"><span data-stu-id="409ef-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="409ef-114">這項資訊取決於物件的來源，如 [`type`] 欄位所示。</span><span class="sxs-lookup"><span data-stu-id="409ef-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="409ef-115">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="409ef-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="409ef-116">備註</span><span class="sxs-lookup"><span data-stu-id="409ef-116">Remarks</span></span>  
 <span data-ttu-id="409ef-117">[`type`] 欄位是[CorGCReferenceType](corgcreferencetype-enumeration.md)列舉值，表示參考的來源位置。</span><span class="sxs-lookup"><span data-stu-id="409ef-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="409ef-118">特定的 `COR_GC_REFERENCE` 值可以反映下列任何一種受管理物件：</span><span class="sxs-lookup"><span data-stu-id="409ef-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="409ef-119">來自所有 managed 堆疊的物件（`CorGCReferenceType.CorReferenceStack`）。</span><span class="sxs-lookup"><span data-stu-id="409ef-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="409ef-120">這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="409ef-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="409ef-121">控制碼資料表中的物件（`CorGCReferenceType.CorHandle*`）。</span><span class="sxs-lookup"><span data-stu-id="409ef-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="409ef-122">這包括模組中的強式參考（`HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT`）和靜態變數。</span><span class="sxs-lookup"><span data-stu-id="409ef-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="409ef-123">完成項佇列中的物件（`CorGCReferenceType.CorReferenceFinalizer`）。</span><span class="sxs-lookup"><span data-stu-id="409ef-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="409ef-124">完成項會佇列根物件，直到完成項執行為止。</span><span class="sxs-lookup"><span data-stu-id="409ef-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="409ef-125">[`extraData`] 欄位包含額外的資料，視參考的來源（或類型）而定。</span><span class="sxs-lookup"><span data-stu-id="409ef-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="409ef-126">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="409ef-126">Possible values are:</span></span>  
  
- <span data-ttu-id="409ef-127">`DependentSource`</span><span class="sxs-lookup"><span data-stu-id="409ef-127">`DependentSource`.</span></span> <span data-ttu-id="409ef-128">如果 `type` 是 `CorGCREferenceType.CorHandleStrongDependent`，此欄位就是物件，如果正在進行，則會在 `COR_GC_REFERENCE.Location`時將物件進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="409ef-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="409ef-129">`RefCount`</span><span class="sxs-lookup"><span data-stu-id="409ef-129">`RefCount`.</span></span> <span data-ttu-id="409ef-130">如果 `CorGCREferenceType.CorHandleStrongRefCount``type`，此欄位就是控制碼的參考計數。</span><span class="sxs-lookup"><span data-stu-id="409ef-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="409ef-131">`Size`</span><span class="sxs-lookup"><span data-stu-id="409ef-131">`Size`.</span></span> <span data-ttu-id="409ef-132">如果 `CorGCREferenceType.CorHandleStrongSizedByref``type`，此欄位就是垃圾收集行程計算物件根之物件樹狀結構的最後大小。</span><span class="sxs-lookup"><span data-stu-id="409ef-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="409ef-133">請注意，這種計算不一定是最新的。</span><span class="sxs-lookup"><span data-stu-id="409ef-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="409ef-134">需求</span><span class="sxs-lookup"><span data-stu-id="409ef-134">Requirements</span></span>  
 <span data-ttu-id="409ef-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="409ef-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="409ef-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="409ef-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="409ef-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="409ef-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="409ef-138">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="409ef-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409ef-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="409ef-139">See also</span></span>

- [<span data-ttu-id="409ef-140">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="409ef-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="409ef-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="409ef-141">Debugging</span></span>](index.md)
