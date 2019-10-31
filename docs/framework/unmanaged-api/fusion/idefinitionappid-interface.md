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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108205"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId 介面
表示在目前範圍中定義應用程式之程式碼的唯一識別碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|取得格式字串，表示這個 `IDefinitionAppId` 物件中的程式碼。|  
|`IDefinitionAppId::put_Codebase`|將這個 `IDefinitionAppId` 物件的程式碼設定為指定的格式化字串值。|  
|`IDefinitionAppId::EnumAppPath`|取得[IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md)物件的介面指標，其中包含目前應用程式路徑中的元件。|  
|`IDefinitionAppId::SetAppPath`|將目前範圍中元件的應用程式路徑，設定為指定之[IDefinitionIdentity](idefinitionidentity-interface.md)物件所參考的值。|  
|`IDefinitionAppId::get_SubscriptionId`|取得此 `IDefinitionAppId` 物件之訂閱的 token 識別碼之字串表示的指標。|  
|`IDefinitionAppId::put_SubscriptionId`|將此 `IDefinitionAppId` 物件之訂閱的 token 識別碼設定為指定的字串值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [融合介面](fusion-interfaces.md)
