---
title: "IDefinitionAppId 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId 介面
代表目前範圍中定義的應用程式的程式碼的唯一識別碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|取得格式化的字串，表示在此程式碼`IDefinitionAppId`物件。|  
|`IDefinitionAppId::put_Codebase`|設定這個程式碼`IDefinitionAppId`到指定的物件格式化字串值。|  
|`IDefinitionAppId::EnumAppPath`|取得的介面指標[IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)物件，其中包含目前的應用程式路徑中的組件。|  
|`IDefinitionAppId::SetAppPath`|設定組件參考所指定的值目前範圍中的應用程式路徑[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)物件。|  
|`IDefinitionAppId::get_SubscriptionId`|取得權杖識別碼的字串表示的指標，此訂用帳戶`IDefinitionAppId`物件。|  
|`IDefinitionAppId::put_SubscriptionId`|設定此訂用帳戶的語彙基元識別碼`IDefinitionAppId`指定的字串值的物件。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
