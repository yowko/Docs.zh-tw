---
title: "ICLRControl 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98b41ea0062534d9e990a7fe366e8f746ae87f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrol-interface"></a>ICLRControl 介面
提供方法，讓主應用程式取得參考，並設定方面的 common language runtime (CLR)。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetCLRManager 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|取得任何主機可以用來設定 CLR 管理員類型的執行個體的介面指標。|  
|[SetAppDomainManagerType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|設定型別衍生自<xref:System.AppDomainManager>做為應用程式定義域管理員類型。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
