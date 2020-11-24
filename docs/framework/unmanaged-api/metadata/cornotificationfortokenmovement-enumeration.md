---
title: CorNotificationForTokenMovement 列舉
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 0f9cb8db35a1669cead6f9f26c9a89e063628dd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687667"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列舉

指定當權杖重新對應發生時將傳送至中繼資料 API 用戶端的通知。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`MDNotifyDefault`|在 `mdTypeRef` 、 `mdMethodDef` 、 `mdMemberRef` 或 `mdFieldDef` 標記移動時通知。|  
|`MDNotifyAll`|在任何權杖移動時通知。|  
|`MDNotifyNone`|當令牌移動時不會通知。|  
|`MDNotifyMethodDef`|在 `mdMethodDef` 權杖移動時通知。|  
|`MDNotifyMemberRef`|在 `mdMemberRef` 權杖移動時通知。|  
|`MDNotifyFieldDef`|在 `mdFieldDef` 權杖移動時通知。|  
|`MDNotifyTypeRef`|在 `mdTypeRef` 權杖移動時通知。|  
|`MDNotifyTypeDef`|在 `mdTypeDef` 權杖移動時通知。|  
|`MDNotifyParamDef`|在 `mdParamDef` 權杖移動時通知。|  
|`MDNotifyInterfaceImpl`|在 `mdInterfaceImpl` 權杖移動時通知。|  
|`MDNotifyProperty`|在 `mdProperty` 權杖移動時通知。|  
|`MDNotifyEvent`|在 `mdEvent` 權杖移動時通知。|  
|`MDNotifySignature`|在 `mdSignature` 權杖移動時通知。|  
|`MDNotifyTypeSpec`|在 `mdTypeSpec` 權杖移動時通知。|  
|`MDNotifyCustomAttribute`|在 `mdCustomAttribute` 權杖移動時通知。|  
|`MDNotifySecurityValue`|在 `mdSecurityValue` 權杖移動時通知。|  
|`MDNotifyPermission`|在 `mdPermission` 權杖移動時通知。|  
|`MDNotifyModuleRef`|在 `mdModuleRef` 權杖移動時通知。|  
|`MDNotifyNameSpace`|在 `mdNameSpace` 權杖移動時通知。|  
|`MDNotifyAssemblyRef`|在 `mdAssemblyRef` 權杖移動時通知。|  
|`MDNotifyFile`|在 `mdFile` 權杖移動時通知。|  
|`MDNotifyExportedType`|在 `mdExportedType` 權杖移動時通知。|  
|`MDNotifyResource`|在 `mdManifestResource` 權杖移動時通知。|  
  
## <a name="remarks"></a>備註  

 權杖可能會重新對應 (也就是在中繼資料合併期間移動) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
