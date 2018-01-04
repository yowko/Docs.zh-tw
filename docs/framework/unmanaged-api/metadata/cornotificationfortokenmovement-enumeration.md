---
title: "CorNotificationForTokenMovement 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e1d3ad11867dbd06dfe3f43cc31817a44cb96d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列舉
指定權杖的重新對應時將中繼資料 API 用戶端傳送的通知。  
  
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
|`MDNotifyDefault`|通知`mdTypeRef`， `mdMethodDef`， `mdMemberRef`，或`mdFieldDef`語彙基元移動。|  
|`MDNotifyAll`|語彙基元移動時，通知。|  
|`MDNotifyNone`|不通知語彙基元移動時。|  
|`MDNotifyMethodDef`|通知`mdMethodDef`語彙基元移動。|  
|`MDNotifyMemberRef`|通知`mdMemberRef`語彙基元移動。|  
|`MDNotifyFieldDef`|通知`mdFieldDef`語彙基元移動。|  
|`MDNotifyTypeRef`|通知`mdTypeRef`語彙基元移動。|  
|`MDNotifyTypeDef`|通知`mdTypeDef`語彙基元移動。|  
|`MDNotifyParamDef`|通知`mdParamDef`語彙基元移動。|  
|`MDNotifyInterfaceImpl`|通知`mdInterfaceImpl`語彙基元移動。|  
|`MDNotifyProperty`|通知`mdProperty`語彙基元移動。|  
|`MDNotifyEvent`|通知`mdEvent`語彙基元移動。|  
|`MDNotifySignature`|通知`mdSignature`語彙基元移動。|  
|`MDNotifyTypeSpec`|通知`mdTypeSpec`語彙基元移動。|  
|`MDNotifyCustomAttribute`|通知`mdCustomAttribute`語彙基元移動。|  
|`MDNotifySecurityValue`|通知`mdSecurityValue`語彙基元移動。|  
|`MDNotifyPermission`|通知`mdPermission`語彙基元移動。|  
|`MDNotifyModuleRef`|通知`mdModuleRef`語彙基元移動。|  
|`MDNotifyNameSpace`|通知`mdNameSpace`語彙基元移動。|  
|`MDNotifyAssemblyRef`|通知`mdAssemblyRef`語彙基元移動。|  
|`MDNotifyFile`|通知`mdFile`語彙基元移動。|  
|`MDNotifyExportedType`|通知`mdExportedType`語彙基元移動。|  
|`MDNotifyResource`|通知`mdManifestResource`語彙基元移動。|  
  
## <a name="remarks"></a>備註  
 語彙基元可能會重新對應 （也就是指移動） 期間的中繼資料合併。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
