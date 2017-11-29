---
title: "IDENTITY_ATTRIBUTE 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="97d8e-102">IDENTITY_ATTRIBUTE 結構</span><span class="sxs-lookup"><span data-stu-id="97d8e-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="97d8e-103">包含有關屬性的中繼資料資訊[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="97d8e-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="97d8e-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="97d8e-105">成員</span><span class="sxs-lookup"><span data-stu-id="97d8e-105">Members</span></span>  
  
|<span data-ttu-id="97d8e-106">成員</span><span class="sxs-lookup"><span data-stu-id="97d8e-106">Member</span></span>|<span data-ttu-id="97d8e-107">說明</span><span class="sxs-lookup"><span data-stu-id="97d8e-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="97d8e-108">指向以 null 結束的字元字串，包含命名空間的屬性內。</span><span class="sxs-lookup"><span data-stu-id="97d8e-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="97d8e-109">以 null 結尾字元字串，包含屬性名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="97d8e-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="97d8e-110">包含屬性的值為 null 結束的字元字串指標。</span><span class="sxs-lookup"><span data-stu-id="97d8e-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97d8e-111">備註</span><span class="sxs-lookup"><span data-stu-id="97d8e-111">Remarks</span></span>  
 <span data-ttu-id="97d8e-112">`IDENTITY_ATTRIBUTE`結構包含三個指向以 null 結尾字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="97d8e-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="97d8e-113">這三個字串描述一個屬性。</span><span class="sxs-lookup"><span data-stu-id="97d8e-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="97d8e-114">執行個體`IDENTITY_ATTRIBUTE`結構是相關聯的執行個體[IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="97d8e-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="97d8e-115">`IDENTITY_ATTRIBUTE`結構包含實際的字串，而且對應`IDENTITY_ATTRIBUTE_BLOB`結構清單中所列之三個字串的位移`IDENTITY_ATTRIBUTE`結構。</span><span class="sxs-lookup"><span data-stu-id="97d8e-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d8e-116">需求</span><span class="sxs-lookup"><span data-stu-id="97d8e-116">Requirements</span></span>  
 <span data-ttu-id="97d8e-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97d8e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d8e-118">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="97d8e-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="97d8e-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d8e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d8e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d8e-120">See Also</span></span>  
 [<span data-ttu-id="97d8e-121">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="97d8e-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="97d8e-122">IDENTITY_ATTRIBUTE_BLOB 結構</span><span class="sxs-lookup"><span data-stu-id="97d8e-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="97d8e-123">融合結構</span><span class="sxs-lookup"><span data-stu-id="97d8e-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
