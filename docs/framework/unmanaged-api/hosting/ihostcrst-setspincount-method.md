---
title: IHostCrst::SetSpinCount 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d90bce1f693f571a5d5c5d5dca981d09bce59b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount 方法
設定目前的微調計數[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSpinCount`  
 [in]新的微調計數，目前`IHostCrst`執行個體。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetSpinCount` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 在多處理器系統中，如果關鍵區段以表示由目前`IHostCrst`執行個體無法使用，請呼叫執行緒旋轉`dwSpinCount`之前呼叫的時間點[ihostsemaphore:: Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)相關聯的號誌上與關鍵區段。 關鍵區段會變成可用微調作業期間，如果呼叫的執行緒可避免等候作業。  
  
 使用`dwSpinCount`等同於在 Win32 中相同名稱的參數的使用方式`InitializeCriticalSectionAndSpinCount`函式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostCrst 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
