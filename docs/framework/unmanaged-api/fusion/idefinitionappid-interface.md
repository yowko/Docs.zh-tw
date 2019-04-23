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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083175"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId 介面
代表目前範圍中定義應用程式的程式碼的唯一識別碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|取得格式化的字串，表示在此程式碼`IDefinitionAppId`物件。|  
|`IDefinitionAppId::put_Codebase`|設定這個程式碼`IDefinitionAppId`至指定的物件格式化的字串值。|  
|`IDefinitionAppId::EnumAppPath`|取得的介面指標[IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)物件，包含目前的應用程式路徑中的組件。|  
|`IDefinitionAppId::SetAppPath`|設定組件參考所指定的值是目前範圍中的應用程式路徑[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)物件。|  
|`IDefinitionAppId::get_SubscriptionId`|此訂用帳戶取得的 token 識別碼的字串表示的指標`IDefinitionAppId`物件。|  
|`IDefinitionAppId::put_SubscriptionId`|此設定訂用帳戶的語彙基元識別碼`IDefinitionAppId`物件到指定的字串值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
