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
ms.openlocfilehash: 78e34d9d33d34047e3ebd2effb4894bc7b709585
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132362"
---
# <a name="cor_field-structure"></a><span data-ttu-id="e8e43-102">COR_FIELD 結構</span><span class="sxs-lookup"><span data-stu-id="e8e43-102">COR_FIELD Structure</span></span>
<span data-ttu-id="e8e43-103">提供物件中欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e8e43-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e43-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8e43-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="e8e43-105">Members</span><span class="sxs-lookup"><span data-stu-id="e8e43-105">Members</span></span>  
  
|<span data-ttu-id="e8e43-106">成員</span><span class="sxs-lookup"><span data-stu-id="e8e43-106">Member</span></span>|<span data-ttu-id="e8e43-107">描述</span><span class="sxs-lookup"><span data-stu-id="e8e43-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="e8e43-108">可以用來取得欄位資訊的 `mdFieldDef` token。</span><span class="sxs-lookup"><span data-stu-id="e8e43-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="e8e43-109">物件中欄位資料的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e8e43-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="e8e43-110">識別此欄位類型的[COR_TYPEID](cor-typeid-structure.md)值。</span><span class="sxs-lookup"><span data-stu-id="e8e43-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="e8e43-111">表示欄位類型的 CorElementType 列舉值。</span><span class="sxs-lookup"><span data-stu-id="e8e43-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8e43-112">備註</span><span class="sxs-lookup"><span data-stu-id="e8e43-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8e43-113">需求</span><span class="sxs-lookup"><span data-stu-id="e8e43-113">Requirements</span></span>  
 <span data-ttu-id="e8e43-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8e43-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e43-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8e43-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8e43-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8e43-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8e43-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e43-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e43-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8e43-118">See also</span></span>

- [<span data-ttu-id="e8e43-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="e8e43-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e8e43-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="e8e43-120">Debugging</span></span>](index.md)
