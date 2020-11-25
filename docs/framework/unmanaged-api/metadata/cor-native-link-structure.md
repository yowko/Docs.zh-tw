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
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724165"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK 結構

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
  
|member|描述|  
|------------|-----------------|  
|`m_linkType`|要在原生程式碼中連結的型別。 此值是其中一個 [CorNativeLinkType](cornativelinktype-enumeration.md) 值。|  
|`m_flags`|連結器連結機器碼時，連結器所使用的旗標。 此值是其中一個 [CorNativeLinkFlags](cornativelinkflags-enumeration.md) 值。|  
|`m_entryPoint`|代表進入點的 MemberRef 元資料標記。 格式為 `lib:entrypoint`。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](metadata-structures.md)
- [CorNativeLinkType 列舉](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags 列舉](cornativelinkflags-enumeration.md)
