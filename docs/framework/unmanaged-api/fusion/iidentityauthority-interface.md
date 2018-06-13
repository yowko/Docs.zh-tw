---
title: IIdentityAuthority 介面
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 692ac4ef4fe8ea64c6a63dc2f02cc04244a842c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432519"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority 介面
管理程式碼物件的識別索引鍵。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|取得值，指出兩個指定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體會相等。|  
|`IIdentityAuthority::AreReferencesEqual`|取得值，指出兩個指定[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)執行個體會相等。|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|取得值，指出兩個指定的字串定義識別的表示是否相等。|  
|`IIdentityAuthority::AreTextualReferencesEqual`|取得值，指出兩個指定的字串參考識別表示法是否相等。|  
|`IIdentityAuthority::CreateDefinition`|取得新的指標`IDefinitionIdentity`代表目前範圍中的程式碼物件的執行個體。|  
|`IIdentityAuthority::CreateReference`|取得新的指標`IReferenceIdentity`代表目前範圍中的程式碼物件的執行個體。|  
|`IIdentityAuthority::DefinitionToText`|取得指定的格式化的字串版`IDefinitionIdentity`。|  
|`IIdentityAuthority::DefinitionToTextBuffer`|填滿指定的字串版本指定寬字元緩衝區`IDefinitionIdentity`。|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|取得值，指出是否指定`IDefinitionIdentity`和`IReferenceIdentity`執行個體會參考相同的程式碼物件。|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|取得值，指出指定的字串是否參考相同的程式碼物件。|  
|`IIdentityAuthority::GenerateDefinitionKey`|取得的指標，新建的字串索引鍵指定`IDefinitionIdentity`。|  
|`IIdentityAuthority::GenerateReferenceKey`|取得的指標，新建的字串索引鍵指定`IReferenceIdentity`。|  
|`IIdentityAuthority::HashDefinition`|取得指定雜湊值`IDefinitionIdentity`。|  
|`IIdentityAuthority::HashReference`|取得指定雜湊值`IreferenceIdentity`。|  
|`IIdentityAuthority::ReferenceToText`|取得指定的格式化的字串版`IReferenceIdentity`。|  
|`IIdentityAuthority::ReferenceToTextBuffer`|填滿指定的字串版本指定寬字元緩衝區`IReferenceIdentity`。|  
|`IIdentityAuthority::TextToDefinition`|取得的介面指標`IDefinitionIdentity`產生從指定的執行個體的格式字串。|  
|`IIdentityAuthority::TextToReference`|取得的介面指標`IReferenceIdentity`產生從指定的執行個體的格式字串。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
