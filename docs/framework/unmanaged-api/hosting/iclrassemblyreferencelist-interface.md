---
title: "ICLRAssemblyReferenceList 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList
helpviewer_keywords: ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4249616ca46fe5ef09dce4a3e245794a103298c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList 介面
管理由 common language runtime (CLR)，而不是由主應用程式載入的組件清單。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[IsAssemblyReferenceInList 方法](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|取得值，指出是否提供的指標參考的組件清單中。|  
|[IsStringAssemblyReferenceInList 方法](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|取得值，指出所提供的名稱是否符合清單中的組件的名稱。|  
  
## <a name="remarks"></a>備註  
 呼叫[iclrassemblyidentitymanager:: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)方法來取得執行個體的指標`ICLRAssemblyReferenceList`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
