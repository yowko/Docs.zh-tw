---
title: "COR_TYPE_LAYOUT 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 250d78dd9983b75fa7e1b3cfd99215160fbc2b1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="4911d-102">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="4911d-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="4911d-103">提供記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4911d-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4911d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4911d-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="4911d-105">成員</span><span class="sxs-lookup"><span data-stu-id="4911d-105">Members</span></span>  
  
|<span data-ttu-id="4911d-106">成員</span><span class="sxs-lookup"><span data-stu-id="4911d-106">Member</span></span>|<span data-ttu-id="4911d-107">描述</span><span class="sxs-lookup"><span data-stu-id="4911d-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="4911d-108">此類型的父類型的識別項。</span><span class="sxs-lookup"><span data-stu-id="4911d-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="4911d-109">這會是 NULL 類型 id (token1 = 0，token2 = 0) 的型別 id 對應於<xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4911d-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="4911d-110">此類型的物件的基底的大小。</span><span class="sxs-lookup"><span data-stu-id="4911d-110">The base size of an object of this type.</span></span> <span data-ttu-id="4911d-111">這是針對非變數可調整大小的物件大小總計。</span><span class="sxs-lookup"><span data-stu-id="4911d-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="4911d-112">此類型的物件中包含的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="4911d-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="4911d-113">如果此類型經過 box 處理，開頭位移的物件的欄位。</span><span class="sxs-lookup"><span data-stu-id="4911d-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="4911d-114">這個欄位是僅適用於實值類型，例如基本類型和結構。</span><span class="sxs-lookup"><span data-stu-id="4911d-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="4911d-115">這個型別所屬 CorElementType。</span><span class="sxs-lookup"><span data-stu-id="4911d-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4911d-116">備註</span><span class="sxs-lookup"><span data-stu-id="4911d-116">Remarks</span></span>  
 <span data-ttu-id="4911d-117">如果`numFields`大於零，您可以呼叫[icordebugprocess5:: Gettypefields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)方法，以取得這種類型的欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4911d-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="4911d-118">如果`type`是`ELEMENT_TYPE_STRING`， `ELEMENT_TYPE_ARRAY`，或`ELEMENT_TYPE_SZARRAY`、 此類型之物件的大小是變數，而您可以[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)結構以[icordebugprocess5:: Getarraylayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4911d-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4911d-119">需求</span><span class="sxs-lookup"><span data-stu-id="4911d-119">Requirements</span></span>  
 <span data-ttu-id="4911d-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4911d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4911d-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4911d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4911d-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4911d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4911d-123">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4911d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4911d-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="4911d-124">See Also</span></span>  
 [<span data-ttu-id="4911d-125">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="4911d-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="4911d-126">偵錯</span><span class="sxs-lookup"><span data-stu-id="4911d-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
