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
ms.openlocfilehash: ae8e907d0e0d6ef5030b3e9aa1f1b3dcef50193e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726622"
---
# <a name="cor_field-structure"></a><span data-ttu-id="bc5a3-102">COR_FIELD 結構</span><span class="sxs-lookup"><span data-stu-id="bc5a3-102">COR_FIELD Structure</span></span>

<span data-ttu-id="bc5a3-103">提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc5a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc5a3-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="bc5a3-105">成員</span><span class="sxs-lookup"><span data-stu-id="bc5a3-105">Members</span></span>  
  
|<span data-ttu-id="bc5a3-106">member</span><span class="sxs-lookup"><span data-stu-id="bc5a3-106">Member</span></span>|<span data-ttu-id="bc5a3-107">描述</span><span class="sxs-lookup"><span data-stu-id="bc5a3-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="bc5a3-108">`mdFieldDef`可以用來取得欄位資訊的權杖。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="bc5a3-109">物件中欄位資料的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="bc5a3-110">識別此欄位之類型的 [COR_TYPEID](cor-typeid-structure.md) 值。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="bc5a3-111">表示欄位類型的 CorElementType 列舉值。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc5a3-112">備註</span><span class="sxs-lookup"><span data-stu-id="bc5a3-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc5a3-113">需求</span><span class="sxs-lookup"><span data-stu-id="bc5a3-113">Requirements</span></span>  

 <span data-ttu-id="bc5a3-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc5a3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc5a3-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc5a3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc5a3-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc5a3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc5a3-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc5a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc5a3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc5a3-118">See also</span></span>

- [<span data-ttu-id="bc5a3-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="bc5a3-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="bc5a3-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="bc5a3-120">Debugging</span></span>](index.md)
