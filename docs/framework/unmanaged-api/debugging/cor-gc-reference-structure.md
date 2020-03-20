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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179323"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="edda1-102">COR_GC_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="edda1-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="edda1-103">包含要進行記憶體回收之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="edda1-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edda1-104">語法</span><span class="sxs-lookup"><span data-stu-id="edda1-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="edda1-105">成員</span><span class="sxs-lookup"><span data-stu-id="edda1-105">Members</span></span>  
  
|<span data-ttu-id="edda1-106">member</span><span class="sxs-lookup"><span data-stu-id="edda1-106">Member</span></span>|<span data-ttu-id="edda1-107">描述</span><span class="sxs-lookup"><span data-stu-id="edda1-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="edda1-108">指向控制碼或物件所屬的應用程式域的指標。</span><span class="sxs-lookup"><span data-stu-id="edda1-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="edda1-109">其值可能是`null`。</span><span class="sxs-lookup"><span data-stu-id="edda1-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="edda1-110">ICorDebugValue 或 ICorDebugReferenceValue 介面對應于要垃圾回收的物件。</span><span class="sxs-lookup"><span data-stu-id="edda1-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="edda1-111">一個[CorGC 參考類型](corgcreferencetype-enumeration.md)枚舉值，指示根來自何處。</span><span class="sxs-lookup"><span data-stu-id="edda1-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="edda1-112">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="edda1-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="edda1-113">有關要垃圾回收的物件的其他資料。</span><span class="sxs-lookup"><span data-stu-id="edda1-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="edda1-114">此資訊取決於物件的源，如`type`欄位所示。</span><span class="sxs-lookup"><span data-stu-id="edda1-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="edda1-115">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="edda1-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edda1-116">備註</span><span class="sxs-lookup"><span data-stu-id="edda1-116">Remarks</span></span>  
 <span data-ttu-id="edda1-117">該`type`欄位是一個[CorGC 參考類型](corgcreferencetype-enumeration.md)枚舉值，指示引用來自何處。</span><span class="sxs-lookup"><span data-stu-id="edda1-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="edda1-118">特定`COR_GC_REFERENCE`值可以反映以下任何類型的託管物件：</span><span class="sxs-lookup"><span data-stu-id="edda1-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="edda1-119">來自所有託管堆疊的物件`CorGCReferenceType.CorReferenceStack`。</span><span class="sxs-lookup"><span data-stu-id="edda1-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="edda1-120">這包括託管代碼中的即時引用，以及由通用語言運行時創建的物件。</span><span class="sxs-lookup"><span data-stu-id="edda1-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="edda1-121">控制碼表中的物件 （`CorGCReferenceType.CorHandle*`。</span><span class="sxs-lookup"><span data-stu-id="edda1-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="edda1-122">這包括模組中的強引用`HNDTYPE_STRONG` `HNDTYPE_REFCOUNT`（ 和 ） 和 靜態變數。</span><span class="sxs-lookup"><span data-stu-id="edda1-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="edda1-123">終端子佇列中的物件 （`CorGCReferenceType.CorReferenceFinalizer`。</span><span class="sxs-lookup"><span data-stu-id="edda1-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="edda1-124">終端子佇列根物件，直到終端子運行。</span><span class="sxs-lookup"><span data-stu-id="edda1-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="edda1-125">該`extraData`欄位包含額外資料，具體取決於引用的源（或類型）。</span><span class="sxs-lookup"><span data-stu-id="edda1-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="edda1-126">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="edda1-126">Possible values are:</span></span>  
  
- <span data-ttu-id="edda1-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="edda1-127">`DependentSource`.</span></span> <span data-ttu-id="edda1-128">如果`type`是`CorGCREferenceType.CorHandleStrongDependent`，則此欄位是物件，如果處於活動狀態，則將物件根在 中`COR_GC_REFERENCE.Location`進行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="edda1-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="edda1-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="edda1-129">`RefCount`.</span></span> <span data-ttu-id="edda1-130">如果`type`為`CorGCREferenceType.CorHandleStrongRefCount`，則此欄位是控制碼的引用計數。</span><span class="sxs-lookup"><span data-stu-id="edda1-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="edda1-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="edda1-131">`Size`.</span></span> <span data-ttu-id="edda1-132">如果`type`為`CorGCREferenceType.CorHandleStrongSizedByref`，則此欄位是垃圾回收器為其計算物件根的物件樹的最後一個大小。</span><span class="sxs-lookup"><span data-stu-id="edda1-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="edda1-133">請注意，此計算不一定是最新的。</span><span class="sxs-lookup"><span data-stu-id="edda1-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edda1-134">需求</span><span class="sxs-lookup"><span data-stu-id="edda1-134">Requirements</span></span>  
 <span data-ttu-id="edda1-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edda1-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edda1-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edda1-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edda1-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edda1-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edda1-138">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edda1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edda1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edda1-139">See also</span></span>

- [<span data-ttu-id="edda1-140">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="edda1-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="edda1-141">偵錯</span><span class="sxs-lookup"><span data-stu-id="edda1-141">Debugging</span></span>](index.md)
