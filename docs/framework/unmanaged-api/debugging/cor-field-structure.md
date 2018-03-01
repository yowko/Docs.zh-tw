---
title: "COR_FIELD 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09a96a22a653688540bcc2ea3a03d86e242c10f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corfield-structure"></a><span data-ttu-id="39403-102">COR_FIELD 結構</span><span class="sxs-lookup"><span data-stu-id="39403-102">COR_FIELD Structure</span></span>
<span data-ttu-id="39403-103">提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="39403-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39403-104">語法</span><span class="sxs-lookup"><span data-stu-id="39403-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="39403-105">成員</span><span class="sxs-lookup"><span data-stu-id="39403-105">Members</span></span>  
  
|<span data-ttu-id="39403-106">成員</span><span class="sxs-lookup"><span data-stu-id="39403-106">Member</span></span>|<span data-ttu-id="39403-107">描述</span><span class="sxs-lookup"><span data-stu-id="39403-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="39403-108">`mdFieldDef`語彙基元可以用來取得欄位資訊。</span><span class="sxs-lookup"><span data-stu-id="39403-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="39403-109">在物件中的欄位資料的位元組位移。</span><span class="sxs-lookup"><span data-stu-id="39403-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="39403-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)可識別此欄位的類型值。</span><span class="sxs-lookup"><span data-stu-id="39403-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="39403-111">CorElementType 列舉值，指出欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="39403-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39403-112">備註</span><span class="sxs-lookup"><span data-stu-id="39403-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39403-113">需求</span><span class="sxs-lookup"><span data-stu-id="39403-113">Requirements</span></span>  
 <span data-ttu-id="39403-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39403-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39403-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39403-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39403-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39403-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39403-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39403-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39403-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="39403-118">See Also</span></span>  
 [<span data-ttu-id="39403-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="39403-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="39403-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="39403-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
