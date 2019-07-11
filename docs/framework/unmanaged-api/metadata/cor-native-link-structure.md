---
title: COR_NATIVE_LINK 結構
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae518e5a736a78a261dc3821d53d93afee95a271
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779987"
---
# <a name="cornativelink-structure"></a>COR_NATIVE_LINK 結構
包含用來連結原生程式碼的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`m_linkType`|要連結原生程式碼的類型。 此值是其中一個[CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)值。|  
|`m_flags`|在連結原生程式碼時使用連結器旗標。 此值是其中一個[CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)值。|  
|`m_entryPoint`|MemberRef 中繼資料語彙基元所代表的進入點。 格式是`lib:entrypoint`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType 列舉](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
