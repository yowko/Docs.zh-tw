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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796493"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="b1e66-102">IDENTITY_ATTRIBUTE 結構</span><span class="sxs-lookup"><span data-stu-id="b1e66-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="b1e66-103">包含有關[IDefinitionIdentity](idefinitionidentity-interface.md)實例的中繼資料屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="b1e66-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e66-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1e66-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="b1e66-105">成員</span><span class="sxs-lookup"><span data-stu-id="b1e66-105">Members</span></span>  
  
|<span data-ttu-id="b1e66-106">成員</span><span class="sxs-lookup"><span data-stu-id="b1e66-106">Member</span></span>|<span data-ttu-id="b1e66-107">描述</span><span class="sxs-lookup"><span data-stu-id="b1e66-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="b1e66-108">以 null 結束之字元字串的指標，其中包含屬性所在的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b1e66-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="b1e66-109">以 null 結束的字元字串的指標，其中包含屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1e66-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="b1e66-110">以 null 結束的字元字串的指標，其中包含屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b1e66-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e66-111">備註</span><span class="sxs-lookup"><span data-stu-id="b1e66-111">Remarks</span></span>  
 <span data-ttu-id="b1e66-112">`IDENTITY_ATTRIBUTE`結構包含三個指向以 null 結束之字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="b1e66-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="b1e66-113">這三個字串描述一個屬性。</span><span class="sxs-lookup"><span data-stu-id="b1e66-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="b1e66-114">`IDENTITY_ATTRIBUTE`結構的實例與[IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)結構的實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="b1e66-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="b1e66-115">結構包含實際的字串，而對應`IDENTITY_ATTRIBUTE_BLOB`的結構會列出`IDENTITY_ATTRIBUTE`結構中所列之三個字串的位移。 `IDENTITY_ATTRIBUTE`</span><span class="sxs-lookup"><span data-stu-id="b1e66-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e66-116">需求</span><span class="sxs-lookup"><span data-stu-id="b1e66-116">Requirements</span></span>  
 <span data-ttu-id="b1e66-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e66-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e66-118">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="b1e66-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b1e66-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e66-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e66-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1e66-120">See also</span></span>

- [<span data-ttu-id="b1e66-121">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="b1e66-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="b1e66-122">IDENTITY_ATTRIBUTE_BLOB 結構</span><span class="sxs-lookup"><span data-stu-id="b1e66-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="b1e66-123">融合結構</span><span class="sxs-lookup"><span data-stu-id="b1e66-123">Fusion Structures</span></span>](fusion-structures.md)
