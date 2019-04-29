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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698040"
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE 結構
包含屬性的中繼資料資訊的相關[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pszNamespace`|以 null 結束的字元字串，包含命名空間的指標，此屬性會是中。|  
|`pszName`|以 null 結束的字元字串，包含屬性名稱的指標。|  
|`pszValue`|包含屬性的值為 null 結束的字元字串指標。|  
  
## <a name="remarks"></a>備註  
 `IDENTITY_ATTRIBUTE`結構包含三個以 null 結束的字元字串的指標。 這三個字串會描述一個屬性。  
  
 執行個體`IDENTITY_ATTRIBUTE`結構是的執行個體相關聯[IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)結構。 `IDENTITY_ATTRIBUTE`結構包含實際的字串，和對應`IDENTITY_ATTRIBUTE_BLOB`結構會列出三個字串中所列的位移`IDENTITY_ATTRIBUTE`結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IDefinitionIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB 結構](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [融合結構](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
