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
ms.openlocfilehash: f33c8f5cf218979404063342d9b1cc5123839f83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726323"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="baea2-102">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="baea2-102">COR_TYPE_LAYOUT Structure</span></span>

<span data-ttu-id="baea2-103">提供記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="baea2-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baea2-104">語法</span><span class="sxs-lookup"><span data-stu-id="baea2-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="baea2-105">成員</span><span class="sxs-lookup"><span data-stu-id="baea2-105">Members</span></span>  
  
|<span data-ttu-id="baea2-106">member</span><span class="sxs-lookup"><span data-stu-id="baea2-106">Member</span></span>|<span data-ttu-id="baea2-107">描述</span><span class="sxs-lookup"><span data-stu-id="baea2-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="baea2-108">這個類型的父類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="baea2-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="baea2-109">如果類型識別碼對應至，則這會是 Null 類型識別碼 (token1 = 0、token2 = 0) <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="baea2-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="baea2-110">此類型之物件的基底大小。</span><span class="sxs-lookup"><span data-stu-id="baea2-110">The base size of an object of this type.</span></span> <span data-ttu-id="baea2-111">這是非變數大小物件的總大小。</span><span class="sxs-lookup"><span data-stu-id="baea2-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="baea2-112">此類型的物件中包含的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="baea2-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="baea2-113">如果此類型是已封裝的，則為物件欄位的開始位移。</span><span class="sxs-lookup"><span data-stu-id="baea2-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="baea2-114">此欄位僅適用于實數值型別，例如基本和結構。</span><span class="sxs-lookup"><span data-stu-id="baea2-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="baea2-115">此類型所屬的 CorElementType。</span><span class="sxs-lookup"><span data-stu-id="baea2-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baea2-116">備註</span><span class="sxs-lookup"><span data-stu-id="baea2-116">Remarks</span></span>  

 <span data-ttu-id="baea2-117">如果 `numFields` 大於零，您可以呼叫 [ICorDebugProcess5：： GetTypeFields](icordebugprocess5-gettypefields-method.md) 方法，以取得有關此類型中之欄位的資訊。</span><span class="sxs-lookup"><span data-stu-id="baea2-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="baea2-118">如果 `type` 是 `ELEMENT_TYPE_STRING` 、 `ELEMENT_TYPE_ARRAY` 或 `ELEMENT_TYPE_SZARRAY` ，則此類型的物件大小為變數，您可以將 [COR_TYPEID](cor-typeid-structure.md) 結構傳遞給 [ICorDebugProcess5：： GetArrayLayout](icordebugprocess5-getarraylayout-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="baea2-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baea2-119">需求</span><span class="sxs-lookup"><span data-stu-id="baea2-119">Requirements</span></span>  

 <span data-ttu-id="baea2-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baea2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baea2-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="baea2-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baea2-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baea2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baea2-123">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baea2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baea2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baea2-124">See also</span></span>

- [<span data-ttu-id="baea2-125">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="baea2-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="baea2-126">偵錯</span><span class="sxs-lookup"><span data-stu-id="baea2-126">Debugging</span></span>](index.md)
