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
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107337"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="0f9f7-102">IDENTITY_ATTRIBUTE 結構</span><span class="sxs-lookup"><span data-stu-id="0f9f7-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="0f9f7-103">包含屬性的中繼資料資訊的相關[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f9f7-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="0f9f7-105">成員</span><span class="sxs-lookup"><span data-stu-id="0f9f7-105">Members</span></span>  
  
|<span data-ttu-id="0f9f7-106">成員</span><span class="sxs-lookup"><span data-stu-id="0f9f7-106">Member</span></span>|<span data-ttu-id="0f9f7-107">描述</span><span class="sxs-lookup"><span data-stu-id="0f9f7-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="0f9f7-108">以 null 結束的字元字串，包含命名空間的指標，此屬性會是中。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="0f9f7-109">以 null 結束的字元字串，包含屬性名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="0f9f7-110">包含屬性的值為 null 結束的字元字串指標。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f9f7-111">備註</span><span class="sxs-lookup"><span data-stu-id="0f9f7-111">Remarks</span></span>  
 <span data-ttu-id="0f9f7-112">`IDENTITY_ATTRIBUTE`結構包含三個以 null 結束的字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="0f9f7-113">這三個字串會描述一個屬性。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="0f9f7-114">執行個體`IDENTITY_ATTRIBUTE`結構是的執行個體相關聯[IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="0f9f7-115">`IDENTITY_ATTRIBUTE`結構包含實際的字串，和對應`IDENTITY_ATTRIBUTE_BLOB`結構會列出三個字串中所列的位移`IDENTITY_ATTRIBUTE`結構。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f9f7-116">需求</span><span class="sxs-lookup"><span data-stu-id="0f9f7-116">Requirements</span></span>  
 <span data-ttu-id="0f9f7-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f9f7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f9f7-118">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="0f9f7-118">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="0f9f7-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0f9f7-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0f9f7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f9f7-120">See also</span></span>

- [<span data-ttu-id="0f9f7-121">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="0f9f7-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="0f9f7-122">IDENTITY_ATTRIBUTE_BLOB 結構</span><span class="sxs-lookup"><span data-stu-id="0f9f7-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="0f9f7-123">融合結構</span><span class="sxs-lookup"><span data-stu-id="0f9f7-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
