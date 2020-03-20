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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179328"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="e0b5d-102">COR_HEAPOBJECT 結構</span><span class="sxs-lookup"><span data-stu-id="e0b5d-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="e0b5d-103">提供 Managed 堆積上的物件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0b5d-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="e0b5d-105">成員</span><span class="sxs-lookup"><span data-stu-id="e0b5d-105">Members</span></span>  
  
|<span data-ttu-id="e0b5d-106">member</span><span class="sxs-lookup"><span data-stu-id="e0b5d-106">Member</span></span>|<span data-ttu-id="e0b5d-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0b5d-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="e0b5d-108">記憶體中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="e0b5d-109">物件的總大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="e0b5d-110">表示物件類型的[COR_TYPEID](cor-typeid-structure.md)權杖。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0b5d-111">備註</span><span class="sxs-lookup"><span data-stu-id="e0b5d-111">Remarks</span></span>  
 <span data-ttu-id="e0b5d-112">`COR_HEAPOBJECT`可以通過枚舉[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件來檢索實例，該介面物件通過調用[ICorDebugProcess5：：：枚舉堆](icordebugprocess5-enumerateheap-method.md)方法填充。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="e0b5d-113">實例`COR_HEAPOBJECT`提供有關託管堆上的即時物件的資訊，或者提供有關未由任何物件紮根但尚未由垃圾回收器收集的物件的資訊。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="e0b5d-114">為了更好的性能，該`COR_HEAPOBJECT.address`欄位是一`CORDB_ADDRESS`個值，而不是許多調試 API 中使用的 ICorDebugValue 介面值。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="e0b5d-115">要獲取給定物件位址的 ICorDebugValue 物件，可以將`CORDB_ADDRESS`該值傳遞給[ICorDebugProcess5：：：getObject](icordebugprocess5-getobject-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="e0b5d-116">為了更好的性能，該`COR_HEAPOBJECT.type`欄位是一`COR_TYPEID`個值，而不是許多調試 API 中使用的 ICorDebugType 介面值。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="e0b5d-117">要獲取給定類型 ID 的 ICorDebugType 物件，可以將`COR_TYPEID`該值傳遞給[ICorDebugProcess5：：getTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="e0b5d-118">該`COR_HEAPOBJECT`結構包括一個引用計數的COM介面。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="e0b5d-119">如果通過調用`COR_HEAPOBJECT`[ICorDebugHeapEnum：Next](icordebugheapenum-next-method.md)方法從枚舉器檢索實例，則必須隨後釋放引用。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b5d-120">需求</span><span class="sxs-lookup"><span data-stu-id="e0b5d-120">Requirements</span></span>  
 <span data-ttu-id="e0b5d-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0b5d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b5d-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0b5d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0b5d-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0b5d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0b5d-124">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b5d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b5d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0b5d-125">See also</span></span>

- [<span data-ttu-id="e0b5d-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="e0b5d-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e0b5d-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="e0b5d-127">Debugging</span></span>](index.md)
