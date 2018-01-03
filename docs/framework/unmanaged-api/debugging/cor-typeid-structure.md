---
title: "COR_TYPEID 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca6c9b3b02314843a3eaf01d8cd4a9eac5513efa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeid-structure"></a><span data-ttu-id="d295b-102">COR_TYPEID 結構</span><span class="sxs-lookup"><span data-stu-id="d295b-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="d295b-103">包含類型識別項。</span><span class="sxs-lookup"><span data-stu-id="d295b-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d295b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d295b-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="d295b-105">成員</span><span class="sxs-lookup"><span data-stu-id="d295b-105">Members</span></span>  
  
|<span data-ttu-id="d295b-106">成員</span><span class="sxs-lookup"><span data-stu-id="d295b-106">Member</span></span>|<span data-ttu-id="d295b-107">描述</span><span class="sxs-lookup"><span data-stu-id="d295b-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="d295b-108">第一個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d295b-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="d295b-109">第二個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d295b-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d295b-110">備註</span><span class="sxs-lookup"><span data-stu-id="d295b-110">Remarks</span></span>  
 <span data-ttu-id="d295b-111">`COR_TYPEID`結構由偵錯的方法，提供有關要進行記憶體回收的物件數目。</span><span class="sxs-lookup"><span data-stu-id="d295b-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="d295b-112">它接著會傳遞做為引數至其他偵錯的方法，提供有關項目的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d295b-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="d295b-113">例如，透過列舉[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)物件，您可以擷取個別[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)代表 managed 堆積上的個別物件的物件。</span><span class="sxs-lookup"><span data-stu-id="d295b-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="d295b-114">然後您可以傳遞`COR_TYPEID`值`COR_HEAPOBJECT.type`欄位設為[icordebugprocess5:: Gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法來擷取 ICorDebugType 物件，提供物件的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="d295b-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="d295b-115">A`COR_TYPEID`物件要當做不透明。</span><span class="sxs-lookup"><span data-stu-id="d295b-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="d295b-116">其個別的欄位不應該存取或操作。</span><span class="sxs-lookup"><span data-stu-id="d295b-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="d295b-117">其唯一用途是做為識別項提供做為`out`中參數的方法呼叫，且可，接著傳遞給其他方法，以提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d295b-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d295b-118">需求</span><span class="sxs-lookup"><span data-stu-id="d295b-118">Requirements</span></span>  
 <span data-ttu-id="d295b-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d295b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d295b-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d295b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d295b-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d295b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d295b-122">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d295b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d295b-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="d295b-123">See Also</span></span>  
 [<span data-ttu-id="d295b-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="d295b-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="d295b-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="d295b-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
