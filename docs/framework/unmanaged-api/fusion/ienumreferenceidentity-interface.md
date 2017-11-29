---
title: "IEnumReferenceIdentity 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity 介面
做為集合的列舉值`IReferenceIdentity`物件。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|取得新的介面指標`IEnumReferenceIdentity`，其中包含這個相同的成員`IEnumReferenceIdentity`。|  
|`IEnumReferenceIdentity::Next`|取得指定的數目`IReferenceIdentity`物件，從目前位置開始。|  
|`IEnumReferenceIdentity::Reset`|將指令指標移到開頭`IEnumReferenceIdentity`。|  
|`IEnumReferenceIdentity::Skip`|將指令指標向前移以指定的項目，從目前位置開始。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
