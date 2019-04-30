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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045431"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列舉
指定權杖的重新對應發生時將中繼資料 API 用戶端傳送的通知。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`MDNotifyDefault`|時通知我`mdTypeRef`， `mdMethodDef`， `mdMemberRef`，或`mdFieldDef`語彙基元移動。|  
|`MDNotifyAll`|語彙基元移動時，就會通知。|  
|`MDNotifyNone`|不通知語彙基元移動時。|  
|`MDNotifyMethodDef`|通知時機`mdMethodDef`k 的移動。|  
|`MDNotifyMemberRef`|通知時機`mdMemberRef`k 的移動。|  
|`MDNotifyFieldDef`|通知時機`mdFieldDef`k 的移動。|  
|`MDNotifyTypeRef`|通知時機`mdTypeRef`k 的移動。|  
|`MDNotifyTypeDef`|通知時機`mdTypeDef`k 的移動。|  
|`MDNotifyParamDef`|通知時機`mdParamDef`k 的移動。|  
|`MDNotifyInterfaceImpl`|通知時機`mdInterfaceImpl`k 的移動。|  
|`MDNotifyProperty`|通知時機`mdProperty`k 的移動。|  
|`MDNotifyEvent`|通知時機`mdEvent`k 的移動。|  
|`MDNotifySignature`|通知時機`mdSignature`k 的移動。|  
|`MDNotifyTypeSpec`|通知時機`mdTypeSpec`k 的移動。|  
|`MDNotifyCustomAttribute`|通知時機`mdCustomAttribute`k 的移動。|  
|`MDNotifySecurityValue`|通知時機`mdSecurityValue`k 的移動。|  
|`MDNotifyPermission`|通知時機`mdPermission`k 的移動。|  
|`MDNotifyModuleRef`|通知時機`mdModuleRef`k 的移動。|  
|`MDNotifyNameSpace`|通知時機`mdNameSpace`k 的移動。|  
|`MDNotifyAssemblyRef`|通知時機`mdAssemblyRef`k 的移動。|  
|`MDNotifyFile`|通知時機`mdFile`k 的移動。|  
|`MDNotifyExportedType`|通知時機`mdExportedType`k 的移動。|  
|`MDNotifyResource`|通知時機`mdManifestResource`k 的移動。|  
  
## <a name="remarks"></a>備註  
 語彙基元可能會重新對應 （也就是指移動） 期間的中繼資料合併。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
