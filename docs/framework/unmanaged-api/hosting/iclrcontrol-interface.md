---
title: ICLRControl 介面
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06c1f4e1fcfe9c9c361a0e0bb2e8722577a13b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrcontrol-interface"></a>ICLRControl 介面
提供方法，讓主應用程式取得參考，並設定方面的 common language runtime (CLR)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCLRManager 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|取得任何主機可以用來設定 CLR 管理員類型的執行個體的介面指標。|  
|[SetAppDomainManagerType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|設定型別衍生自<xref:System.AppDomainManager>做為應用程式定義域管理員類型。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
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
