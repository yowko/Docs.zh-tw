---
title: IDENTITY_ATTRIBUTE 結構
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107988"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="fe4f9-102">IDENTITY_ATTRIBUTE 結構</span><span class="sxs-lookup"><span data-stu-id="fe4f9-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="fe4f9-103">包含有關[IDefinitionIdentity](idefinitionidentity-interface.md)實例的中繼資料屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe4f9-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="fe4f9-105">Members</span><span class="sxs-lookup"><span data-stu-id="fe4f9-105">Members</span></span>  
  
|<span data-ttu-id="fe4f9-106">成員</span><span class="sxs-lookup"><span data-stu-id="fe4f9-106">Member</span></span>|<span data-ttu-id="fe4f9-107">描述</span><span class="sxs-lookup"><span data-stu-id="fe4f9-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="fe4f9-108">以 null 結束之字元字串的指標，其中包含屬性所在的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="fe4f9-109">以 null 結束的字元字串的指標，其中包含屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="fe4f9-110">以 null 結束的字元字串的指標，其中包含屬性的值。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe4f9-111">備註</span><span class="sxs-lookup"><span data-stu-id="fe4f9-111">Remarks</span></span>  
 <span data-ttu-id="fe4f9-112">`IDENTITY_ATTRIBUTE` 結構包含三個指向以 null 結束之字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="fe4f9-113">這三個字串描述一個屬性。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="fe4f9-114">`IDENTITY_ATTRIBUTE` 結構的實例與[IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)結構的實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="fe4f9-115">`IDENTITY_ATTRIBUTE` 結構包含實際的字串，而對應的 `IDENTITY_ATTRIBUTE_BLOB` 結構會列出 `IDENTITY_ATTRIBUTE` 結構中所列之三個字串的位移。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe4f9-116">需求</span><span class="sxs-lookup"><span data-stu-id="fe4f9-116">Requirements</span></span>  
 <span data-ttu-id="fe4f9-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe4f9-118">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="fe4f9-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="fe4f9-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe4f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4f9-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe4f9-120">See also</span></span>

- [<span data-ttu-id="fe4f9-121">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="fe4f9-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="fe4f9-122">IDENTITY_ATTRIBUTE_BLOB 結構</span><span class="sxs-lookup"><span data-stu-id="fe4f9-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="fe4f9-123">融合結構</span><span class="sxs-lookup"><span data-stu-id="fe4f9-123">Fusion Structures</span></span>](fusion-structures.md)
