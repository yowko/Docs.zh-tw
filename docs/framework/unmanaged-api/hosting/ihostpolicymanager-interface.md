---
title: IHostPolicyManager 介面
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128605"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager 介面
提供方法，以通知主機 common language runtime （CLR）在中止、超時或失敗時所執行的動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnDefaultAction 方法](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|通知主機 CLR 即將採取[ICLRPolicyManager：： SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)呼叫所指定的預設動作，以回應執行緒中止或 <xref:System.AppDomain> 卸載。|  
|[OnFailure 方法](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)呼叫所指定的動作，以回應資源配置或回收失敗。|  
|[OnTimeout 方法](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)呼叫所指定的動作，以回應超時。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
