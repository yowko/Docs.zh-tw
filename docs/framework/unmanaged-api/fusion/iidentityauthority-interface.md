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
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796417"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority 介面

管理程式碼物件的識別索引鍵。

## <a name="methods"></a>方法

|方法|描述|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|取得值，指出兩個指定的[IDefinitionIdentity](idefinitionidentity-interface.md)實例是否相等。|
|`IIdentityAuthority::AreReferencesEqual`|取得值，指出兩個指定的[IReferenceIdentity](ireferenceidentity-interface.md)實例是否相等。|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|取得值，指出兩個指定的字串定義識別表示是否相等。|
|`IIdentityAuthority::AreTextualReferencesEqual`|取得值，指出兩個指定的字串參考身分識別表示是否相等。|
|`IIdentityAuthority::CreateDefinition`|取得新`IDefinitionIdentity`實例的指標，表示目前範圍中的程式碼物件。|
|`IIdentityAuthority::CreateReference`|取得新`IReferenceIdentity`實例的指標，表示目前範圍中的程式碼物件。|
|`IIdentityAuthority::DefinitionToText`|取得指定`IDefinitionIdentity`的格式化字串版本。|
|`IIdentityAuthority::DefinitionToTextBuffer`|使用指定`IDefinitionIdentity`的字串版本，填滿指定的寬字元緩衝區。|
|`IIdentityAuthority::DoesDefinitionMatchReference`|取得值，指出指定`IDefinitionIdentity`的和`IReferenceIdentity`實例是否參考相同的程式碼物件。|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|取得值，指出指定的字串是否參考相同的程式碼物件。|
|`IIdentityAuthority::GenerateDefinitionKey`|取得所指定`IDefinitionIdentity`的新建立之字串索引鍵的指標。|
|`IIdentityAuthority::GenerateReferenceKey`|取得所指定`IReferenceIdentity`的新建立之字串索引鍵的指標。|
|`IIdentityAuthority::HashDefinition`|取得所指定`IDefinitionIdentity`的雜湊值。|
|`IIdentityAuthority::HashReference`|取得所指定`IReferenceIdentity`的雜湊值。|
|`IIdentityAuthority::ReferenceToText`|取得指定`IReferenceIdentity`的格式化字串版本。|
|`IIdentityAuthority::ReferenceToTextBuffer`|使用指定`IReferenceIdentity`的字串版本，填滿指定的寬字元緩衝區。|
|`IIdentityAuthority::TextToDefinition`|取得從指定的格式化字串`IDefinitionIdentity`產生之實例的介面指標。|
|`IIdentityAuthority::TextToReference`|取得從指定的格式化字串`IReferenceIdentity`產生之實例的介面指標。|

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** 隔離。h

**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
