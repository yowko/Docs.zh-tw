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
ms.openlocfilehash: a344f2ab5d9a7aa92018c47ee7a162cd1721aeb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732108"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority 介面

提供方法來產生和比較應用程式識別和參考的索引鍵。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|取得值，這個值表示兩個指定的 [IDefinitionAppId](idefinitionappid-interface.md) 實例是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION，以忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreReferencesEqual`|取得值，這個值表示兩個指定的 [IReferenceAppId](ireferenceappid-interface.md) 實例是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION，以忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|取得值，這個值表示兩個指定的字串定義是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION，以忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|取得值，這個值表示兩個指定的字串參考是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION，以忽略其各自的版本資訊。|  
|`IAppIdAuthority::CreateDefinition`|取得新產生之實例的介面指標 `IDefinitionAppId` ，表示目前範圍中的元件。|  
|`IAppIdAuthority::CreateReference`|取得新建立的介面指標 `IReferenceAppId` ，表示目前範圍中的元件。|  
|`IAppIdAuthority::DefinitionToText`|使用指定的旗標值，取得指定之的字串版本 `IDefinitionAppId` 。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|取得值，這個值表示指定的 `IDefinitionAppId` 和是否 `IReferenceAppId` 代表相同的元件。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|取得值，這個值表示指定的定義字串和參考字串是否代表相同的元件。|  
|`IAppIdAuthority::GenerateDefinitionKey`|取得表示指定之實例的字串索引鍵 `IDefinitionAppId` 。|  
|`IAppIdAuthority::GenerateReferenceKey`|取得表示指定之實例的字串索引鍵 `IReferenceAppId` 。|  
|`IAppIdAuthority::HashDefinition`|取得指定之實例的雜湊索引鍵 `IDefinitionAppId` 。|  
|`IAppIdAuthority::HashReference`|取得指定之實例的雜湊索引鍵 `IReferenceAppId` 。|  
|`IAppIdAuthority::ReferenceToText`|使用指定的旗標值，取得指定之的字串版本 `IReferenceAppId` 。|  
|`IAppIdAuthority::TextToDefinition`|取得 `IDefinitionAppId` 實例的介面指標，該實例表示指定之字串索引鍵所參考的元件。|  
|`IAppIdAuthority::TextToReference`|取得 `IReferenceAppId` 實例的介面指標，該實例表示指定之字串索引鍵所參考的元件。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
