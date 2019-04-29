---
title: COR_HEAPOBJECT 結構
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609436"
---
# <a name="corheapobject-structure"></a><span data-ttu-id="ed4d6-102">COR_HEAPOBJECT 結構</span><span class="sxs-lookup"><span data-stu-id="ed4d6-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="ed4d6-103">提供 Managed 堆積上的物件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed4d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed4d6-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="ed4d6-105">成員</span><span class="sxs-lookup"><span data-stu-id="ed4d6-105">Members</span></span>  
  
|<span data-ttu-id="ed4d6-106">成員</span><span class="sxs-lookup"><span data-stu-id="ed4d6-106">Member</span></span>|<span data-ttu-id="ed4d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="ed4d6-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="ed4d6-108">在記憶體中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="ed4d6-109">物件，以位元組為單位的大小總計。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="ed4d6-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)語彙基元，表示物件的型別。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed4d6-111">備註</span><span class="sxs-lookup"><span data-stu-id="ed4d6-111">Remarks</span></span>  
 <span data-ttu-id="ed4d6-112">`COR_HEAPOBJECT` 可以擷取執行個體列舉[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)填入藉由呼叫的介面物件[ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="ed4d6-113">A`COR_HEAPOBJECT`執行個體會提供有關在 managed 堆積中，即時物件或物件不根目錄的任何物件，但尚未收集記憶體回收行程的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="ed4d6-114">為了達到最佳效能，`COR_HEAPOBJECT.address`欄位是`CORDB_ADDRESS`值，而不是 ICorDebugValue 介面中大部分的偵錯 API 所使用的值。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="ed4d6-115">若要取得 ICorDebugValue 物件指定的物件位址，您可以傳遞`CORDB_ADDRESS`值加入[ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="ed4d6-116">為了達到最佳效能，`COR_HEAPOBJECT.type`欄位是`COR_TYPEID`值，而不是 ICorDebugType 介面中大部分的偵錯 API 所使用的值。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="ed4d6-117">若要取得 ICorDebugType 物件指定的型別 id，您可以傳遞`COR_TYPEID`值加入[ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="ed4d6-118">`COR_HEAPOBJECT`結構包含的參考計數的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="ed4d6-119">如果您擷取`COR_HEAPOBJECT`來自列舉值，藉由呼叫的執行個體[icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法，接下來，您必須釋放參考。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed4d6-120">需求</span><span class="sxs-lookup"><span data-stu-id="ed4d6-120">Requirements</span></span>  
 <span data-ttu-id="ed4d6-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed4d6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed4d6-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed4d6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed4d6-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed4d6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed4d6-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed4d6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4d6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed4d6-125">See also</span></span>

- [<span data-ttu-id="ed4d6-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="ed4d6-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="ed4d6-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="ed4d6-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
