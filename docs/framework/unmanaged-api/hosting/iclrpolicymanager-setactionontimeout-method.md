---
title: ICLRPolicyManager::SetActionOnTimeout 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140798"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a>ICLRPolicyManager::SetActionOnTimeout 方法
指定當指定的作業超時時，common language runtime （CLR）應採取的原則動作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>參數  
 `operation`  
 在其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要指定其超時動作的作業。 支援下列值：  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `action`  
 在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示作業超時時要採取的原則動作。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `SetActionOnTimeout`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|無法為指定的 `operation`設定超時，或為 `operation`提供了不正確值。|  
  
## <a name="remarks"></a>備註  
 Timeout 值可以是 CLR 所設定的預設超時時間，或是由主機在[ICLRPolicyManager：： SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)方法的呼叫中所指定的值。  
  
 並非所有的原則動作值都可以指定為 CLR 作業的超時行為。 `SetActionOnTimeout` 通常僅用於呈報行為。 例如，主機可以指定執行緒中止會變成強制執行緒中止，但無法指定相反的。 下表描述有效 `operation` 值的有效 `action` 值。  
  
|`operation` 的值|`action` 的有效值|  
|---------------------------|-------------------------------|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|- eRudeAbortThread<br />- eUnloadAppDomain<br />- eRudeUnloadAppDomain<br />- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
|OPR_AppDomainUnload|- eUnloadAppDomain<br />- eRudeUnloadAppDomain<br />- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
|OPR_ProcessExit|- eExitProcess<br />- eFastExitProcess<br />- eRudeExitProcess<br />- eDisableRuntime|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
