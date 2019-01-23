---
title: ICLRPolicyManager::SetTimeout 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8edb16de4c02d2589ecfb9ae5becba22e10e6be6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609326"
---
# <a name="iclrpolicymanagersettimeout-method"></a>ICLRPolicyManager::SetTimeout 方法
設定指定之作業的逾時值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a>參數  
 `operation`  
 [in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要設定逾時的常見語言執行平台 (CLR) 作業。 支援下列值：  
  
-   OPR_AppDomainUnload  
  
-   OPR_ProcessExit  
  
-   OPR_ThreadRudeAbortInCriticalRegion  
  
-   OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 [in]新逾時值，以毫秒為單位。 無限的值會導致作業永遠不會逾時。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetTimeout` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|無法設定逾時指定`operation`，或為無效的值提供`operation`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
