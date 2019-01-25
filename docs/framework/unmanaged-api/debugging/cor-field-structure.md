---
title: COR_FIELD 結構
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d570f9392bbd66f0d9031c776b139ee3b30541b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698215"
---
# <a name="corfield-structure"></a><span data-ttu-id="47222-102">COR_FIELD 結構</span><span class="sxs-lookup"><span data-stu-id="47222-102">COR_FIELD Structure</span></span>
<span data-ttu-id="47222-103">提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="47222-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47222-104">語法</span><span class="sxs-lookup"><span data-stu-id="47222-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="47222-105">成員</span><span class="sxs-lookup"><span data-stu-id="47222-105">Members</span></span>  
  
|<span data-ttu-id="47222-106">成員</span><span class="sxs-lookup"><span data-stu-id="47222-106">Member</span></span>|<span data-ttu-id="47222-107">描述</span><span class="sxs-lookup"><span data-stu-id="47222-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="47222-108">`mdFieldDef`權杖，可用來取得欄位資訊。</span><span class="sxs-lookup"><span data-stu-id="47222-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="47222-109">在物件中的欄位資料的位元組位移。</span><span class="sxs-lookup"><span data-stu-id="47222-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="47222-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)可識別此欄位的型別值。</span><span class="sxs-lookup"><span data-stu-id="47222-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="47222-111">CorElementType 列舉值，指出欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="47222-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47222-112">備註</span><span class="sxs-lookup"><span data-stu-id="47222-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47222-113">需求</span><span class="sxs-lookup"><span data-stu-id="47222-113">Requirements</span></span>  
 <span data-ttu-id="47222-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47222-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47222-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47222-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47222-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47222-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47222-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47222-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47222-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47222-118">See also</span></span>
- [<span data-ttu-id="47222-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="47222-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="47222-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="47222-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
