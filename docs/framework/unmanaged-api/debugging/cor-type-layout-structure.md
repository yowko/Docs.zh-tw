---
title: COR_TYPE_LAYOUT 結構
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7efb2c3e8033b8bd8fa736a29b2ab9b3bedebeaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109638"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="92f66-102">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="92f66-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="92f66-103">提供記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92f66-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f66-104">語法</span><span class="sxs-lookup"><span data-stu-id="92f66-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="92f66-105">成員</span><span class="sxs-lookup"><span data-stu-id="92f66-105">Members</span></span>  
  
|<span data-ttu-id="92f66-106">成員</span><span class="sxs-lookup"><span data-stu-id="92f66-106">Member</span></span>|<span data-ttu-id="92f66-107">描述</span><span class="sxs-lookup"><span data-stu-id="92f66-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="92f66-108">此類型的父類型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="92f66-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="92f66-109">這會是 NULL 類型識別碼 (token1 = 0，token2 = 0) 的型別 id 對應於<xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="92f66-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="92f66-110">此類型物件的基底的大小。</span><span class="sxs-lookup"><span data-stu-id="92f66-110">The base size of an object of this type.</span></span> <span data-ttu-id="92f66-111">這是針對非變數大小物件的總大小。</span><span class="sxs-lookup"><span data-stu-id="92f66-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="92f66-112">此類型的物件中包含的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="92f66-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="92f66-113">如果此類型經過 box 處理，則會在物件的欄位的位移開頭。</span><span class="sxs-lookup"><span data-stu-id="92f66-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="92f66-114">這個欄位是僅適用於實值型別，例如基本類型和結構。</span><span class="sxs-lookup"><span data-stu-id="92f66-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="92f66-115">CorElementType，屬於此類型。</span><span class="sxs-lookup"><span data-stu-id="92f66-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92f66-116">備註</span><span class="sxs-lookup"><span data-stu-id="92f66-116">Remarks</span></span>  
 <span data-ttu-id="92f66-117">如果`numFields`是小於或等於零，您可以呼叫[ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)方法，以取得此類型中的欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92f66-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="92f66-118">如果`type`已`ELEMENT_TYPE_STRING`， `ELEMENT_TYPE_ARRAY`，或`ELEMENT_TYPE_SZARRAY`，此類型之物件的大小是變數，您可以傳遞[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)結構[ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="92f66-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f66-119">需求</span><span class="sxs-lookup"><span data-stu-id="92f66-119">Requirements</span></span>  
 <span data-ttu-id="92f66-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92f66-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f66-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92f66-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92f66-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f66-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f66-123">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f66-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f66-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92f66-124">See also</span></span>

- [<span data-ttu-id="92f66-125">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="92f66-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="92f66-126">偵錯</span><span class="sxs-lookup"><span data-stu-id="92f66-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
