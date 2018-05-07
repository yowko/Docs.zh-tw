---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a3d5bb8a8cc5acc88373fa4952848d08ccd485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a>ICLRPolicyManager::SetUnhandledExceptionPolicy 方法
發生未處理的例外狀況時，請指定 common language runtime (CLR) 的行為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a>參數  
 `policy`  
 [in]其中一個[EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)值，表示由 CLR 或主機是否已設定行為。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetUnhandledExceptionPolicy` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 根據預設，CLR 是所有未處理的例外狀況的最後一個處理常式，其預設行為是終止處理程序。 主機可以變更此行為，藉由設定`policy`eHostDeterminedPolicy 的值。 這個值允許主應用程式實作它自己的預設行為，如同舊版的 CLR。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [EClrUnhandledException 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
