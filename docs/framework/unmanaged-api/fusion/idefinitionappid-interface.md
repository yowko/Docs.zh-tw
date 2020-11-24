---
title: IDefinitionAppId 介面
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673861"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId 介面

表示在目前範圍中定義應用程式之程式碼的唯一識別碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|取得表示此物件中之程式碼的格式化字串 `IDefinitionAppId` 。|  
|`IDefinitionAppId::put_Codebase`|將這個物件的程式碼設定 `IDefinitionAppId` 為指定的格式化字串值。|  
|`IDefinitionAppId::EnumAppPath`|取得 [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) 物件的介面指標，該物件包含目前應用程式路徑中的元件。|  
|`IDefinitionAppId::SetAppPath`|將目前範圍中元件的應用程式路徑設定為指定之 [IDefinitionIdentity](idefinitionidentity-interface.md) 物件所參考的值。|  
|`IDefinitionAppId::get_SubscriptionId`|取得這個物件之訂閱的標記識別項之字串表示的指標 `IDefinitionAppId` 。|  
|`IDefinitionAppId::put_SubscriptionId`|將這個物件之訂閱的標記識別項設定 `IDefinitionAppId` 為指定的字串值。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
