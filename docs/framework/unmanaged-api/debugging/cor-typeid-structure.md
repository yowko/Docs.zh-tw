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
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109859"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="fc6b1-102">COR_TYPEID 結構</span><span class="sxs-lookup"><span data-stu-id="fc6b1-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="fc6b1-103">包含類型識別項。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc6b1-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="fc6b1-105">成員</span><span class="sxs-lookup"><span data-stu-id="fc6b1-105">Members</span></span>  
  
|<span data-ttu-id="fc6b1-106">成員</span><span class="sxs-lookup"><span data-stu-id="fc6b1-106">Member</span></span>|<span data-ttu-id="fc6b1-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc6b1-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="fc6b1-108">第一個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="fc6b1-109">第二個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc6b1-110">備註</span><span class="sxs-lookup"><span data-stu-id="fc6b1-110">Remarks</span></span>  
 <span data-ttu-id="fc6b1-111">`COR_TYPEID`結構由偵錯的方法，可提供資訊以進行記憶體回收的物件數目。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="fc6b1-112">它接著會傳遞做為引數其他偵錯的方法，提供關於該項目的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="fc6b1-113">例如，透過列舉[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)物件，您可以擷取個別[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)代表 managed 堆積上的個別物件的物件。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="fc6b1-114">您可以傳遞`COR_TYPEID`值從`COR_HEAPOBJECT.type`欄位設為[ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法來擷取 ICorDebugType 物件，提供物件的型別資訊。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="fc6b1-115">A`COR_TYPEID`物件是不透明。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="fc6b1-116">其個別的欄位不應該存取或操作。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="fc6b1-117">其唯一用途是做為識別項提供做為`out`中方法呼叫，並可中，參數會傳遞至其他方法，以提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6b1-118">需求</span><span class="sxs-lookup"><span data-stu-id="fc6b1-118">Requirements</span></span>  
 <span data-ttu-id="fc6b1-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc6b1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6b1-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc6b1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc6b1-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc6b1-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fc6b1-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fc6b1-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc6b1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc6b1-123">See also</span></span>

- [<span data-ttu-id="fc6b1-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="fc6b1-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="fc6b1-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="fc6b1-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
