---
title: COR_TYPEID 結構
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273988"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="bd2bc-102">COR_TYPEID 結構</span><span class="sxs-lookup"><span data-stu-id="bd2bc-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="bd2bc-103">包含類型識別項。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd2bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd2bc-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="bd2bc-105">成員</span><span class="sxs-lookup"><span data-stu-id="bd2bc-105">Members</span></span>  
  
|<span data-ttu-id="bd2bc-106">成員</span><span class="sxs-lookup"><span data-stu-id="bd2bc-106">Member</span></span>|<span data-ttu-id="bd2bc-107">描述</span><span class="sxs-lookup"><span data-stu-id="bd2bc-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="bd2bc-108">第一個 token。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="bd2bc-109">第二個 token。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd2bc-110">備註</span><span class="sxs-lookup"><span data-stu-id="bd2bc-110">Remarks</span></span>  
 <span data-ttu-id="bd2bc-111">`COR_TYPEID`結構會由數個偵錯工具傳回，這些方法會提供要進行垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="bd2bc-112">然後，可以將它當做引數傳遞給其他的偵錯工具方法，以提供該專案的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="bd2bc-113">例如，藉由列舉[ICorDebugHeapEnum](icordebugheapenum-interface.md)物件，您可以在 managed 堆積上，抓取代表個別物件的個別[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="bd2bc-114">接著，您可以將`COR_TYPEID` `COR_HEAPOBJECT.type`欄位中的值傳遞給[ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法，以抓取提供物件之型別資訊的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="bd2bc-115">`COR_TYPEID`物件應為不透明。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="bd2bc-116">其個別欄位不應存取或操作。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="bd2bc-117">其唯一用途就是當做方法呼叫中的`out`參數提供的識別碼，然後可以傳遞給其他方法來提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd2bc-118">需求</span><span class="sxs-lookup"><span data-stu-id="bd2bc-118">Requirements</span></span>  
 <span data-ttu-id="bd2bc-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd2bc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd2bc-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd2bc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd2bc-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd2bc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd2bc-122">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd2bc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2bc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd2bc-123">See also</span></span>

- [<span data-ttu-id="bd2bc-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="bd2bc-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="bd2bc-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="bd2bc-125">Debugging</span></span>](index.md)
