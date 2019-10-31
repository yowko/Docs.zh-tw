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
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099071"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="69339-102">COR_HEAPOBJECT 結構</span><span class="sxs-lookup"><span data-stu-id="69339-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="69339-103">提供 Managed 堆積上的物件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="69339-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69339-104">語法</span><span class="sxs-lookup"><span data-stu-id="69339-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="69339-105">Members</span><span class="sxs-lookup"><span data-stu-id="69339-105">Members</span></span>  
  
|<span data-ttu-id="69339-106">成員</span><span class="sxs-lookup"><span data-stu-id="69339-106">Member</span></span>|<span data-ttu-id="69339-107">描述</span><span class="sxs-lookup"><span data-stu-id="69339-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="69339-108">記憶體中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="69339-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="69339-109">物件的總大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="69339-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="69339-110">代表物件類型的[COR_TYPEID](cor-typeid-structure.md) token。</span><span class="sxs-lookup"><span data-stu-id="69339-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69339-111">備註</span><span class="sxs-lookup"><span data-stu-id="69339-111">Remarks</span></span>  
 <span data-ttu-id="69339-112">藉由列舉藉由呼叫[ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md)方法填入的[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件，可以抓取 `COR_HEAPOBJECT` 實例。</span><span class="sxs-lookup"><span data-stu-id="69339-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="69339-113">`COR_HEAPOBJECT` 實例提供有關 managed 堆積上之即時物件的資訊，或關於未由任何物件（但垃圾收集行程尚未收集）的物件。</span><span class="sxs-lookup"><span data-stu-id="69339-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="69339-114">為獲得較佳的效能，`COR_HEAPOBJECT.address` 欄位是 `CORDB_ADDRESS` 值，而不是大部分偵錯工具 API 中使用的 ICorDebugValue 介面值。</span><span class="sxs-lookup"><span data-stu-id="69339-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="69339-115">若要取得指定物件位址的 ICorDebugValue 物件，您可以將 `CORDB_ADDRESS` 值傳遞至[ICorDebugProcess5：： GetObject](icordebugprocess5-getobject-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="69339-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="69339-116">為獲得較佳的效能，`COR_HEAPOBJECT.type` 欄位是 `COR_TYPEID` 值，而不是大部分偵錯工具 API 中使用的 ICorDebugType 介面值。</span><span class="sxs-lookup"><span data-stu-id="69339-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="69339-117">若要取得給定型別識別碼的 ICorDebugType 物件，您可以將 `COR_TYPEID` 值傳遞至[ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="69339-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="69339-118">`COR_HEAPOBJECT` 結構包含參考計數的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="69339-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="69339-119">如果您藉由呼叫[ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md)方法從列舉值抓取 `COR_HEAPOBJECT` 實例，您就必須釋放參考。</span><span class="sxs-lookup"><span data-stu-id="69339-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69339-120">需求</span><span class="sxs-lookup"><span data-stu-id="69339-120">Requirements</span></span>  
 <span data-ttu-id="69339-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69339-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69339-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69339-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69339-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69339-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69339-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69339-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69339-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="69339-125">See also</span></span>

- [<span data-ttu-id="69339-126">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="69339-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="69339-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="69339-127">Debugging</span></span>](index.md)
