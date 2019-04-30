---
title: ICLRControl::GetCLRManager 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09079c8847b7cb995d97a4577d03982602bbadfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979169"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager 方法
取得任何主應用程式可用來設定 common language runtime (CLR) 的管理員型別的執行個體的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `riid`  
 [in]`IID`管理員類型，傳回。 下列`IID`支援值。  
  
-   IID_ICLRDebugManager:指定`ppObject`的類型會是[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)。  
  
-   IID_ICLRErrorReportingManager:指定`ppObject`的類型會是[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)。  
  
-   IID_ICLRGCManager:指定`ppObject`的類型會是[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。  
  
-   IID_ICLRHostProtectionManager:指定`ppObject`的類型會是[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)。  
  
-   IID_ICLROnEventManager:指定`ppObject`的類型會是[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)。  
  
-   IID_ICLRPolicyManager:指定`ppObject`的類型會是[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。  
  
-   IID_ICLRTaskManager:指定`ppObject`的類型會是[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)。  
  
 `ppObject`  
 [out]要求的管理員 中或如果要求不正確的管理員類型的 null 介面指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOINTERFACE|不支援的介面型別。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
