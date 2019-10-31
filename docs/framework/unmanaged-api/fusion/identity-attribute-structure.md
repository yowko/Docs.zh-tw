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
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE 結構
包含有關[IDefinitionIdentity](idefinitionidentity-interface.md)實例的中繼資料屬性資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`pszNamespace`|以 null 結束之字元字串的指標，其中包含屬性所在的命名空間。|  
|`pszName`|以 null 結束的字元字串的指標，其中包含屬性的名稱。|  
|`pszValue`|以 null 結束的字元字串的指標，其中包含屬性的值。|  
  
## <a name="remarks"></a>備註  
 `IDENTITY_ATTRIBUTE` 結構包含三個指向以 null 結束之字元字串的指標。 這三個字串描述一個屬性。  
  
 `IDENTITY_ATTRIBUTE` 結構的實例與[IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)結構的實例相關聯。 `IDENTITY_ATTRIBUTE` 結構包含實際的字串，而對應的 `IDENTITY_ATTRIBUTE_BLOB` 結構會列出 `IDENTITY_ATTRIBUTE` 結構中所列之三個字串的位移。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IDefinitionIdentity 介面](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB 結構](identity-attribute-blob-structure.md)
- [融合結構](fusion-structures.md)
