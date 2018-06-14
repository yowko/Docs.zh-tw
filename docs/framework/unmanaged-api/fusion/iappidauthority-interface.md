---
title: IAppIdAuthority 介面
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433746"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority 介面
提供方法，產生並比較應用程式的身分識別與參考的索引鍵。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|取得值，指出兩個指定[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)執行個體會相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。|  
|`IAppIdAuthority::AreReferencesEqual`|取得值，指出兩個指定[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)執行個體會相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|取得值，指出兩個指定的字串定義是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|取得值，指出兩個指定的字串參考是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。|  
|`IAppIdAuthority::CreateDefinition`|取得新產生的介面指標`IDefinitionAppId`代表目前範圍中的組件的執行個體。|  
|`IAppIdAuthority::CreateReference`|取得的介面指標，新建`IReferenceAppId`，代表目前範圍中的組件。|  
|`IAppIdAuthority::DefinitionToText`|取得指定的字串版本`IDefinitionAppId`，使用指定的旗標值。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|取得值，指出是否指定`IDefinitionAppId`和`IReferenceAppId`代表相同的組件。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|取得值，指出指定的定義字串和參考字串是否表示相同的組件。|  
|`IAppIdAuthority::GenerateDefinitionKey`|取得代表指定的字串索引鍵`IDefinitionAppId`執行個體。|  
|`IAppIdAuthority::GenerateReferenceKey`|取得代表指定的字串索引鍵`IReferenceAppId`執行個體。|  
|`IAppIdAuthority::HashDefinition`|取得所指定的雜湊索引鍵`IDefinitionAppId`執行個體。|  
|`IAppIdAuthority::HashReference`|取得所指定的雜湊索引鍵`IReferenceAppId`執行個體。|  
|`IAppIdAuthority::ReferenceToText`|取得指定的字串版本`IReferenceAppId`，使用指定的旗標值。|  
|`IAppIdAuthority::TextToDefinition`|取得的介面指標`IDefinitionAppId`表示的指定的字串索引鍵參考的組件執行個體。|  
|`IAppIdAuthority::TextToReference`|取得的介面指標`IReferenceAppId`表示的指定的字串索引鍵參考的組件執行個體。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
