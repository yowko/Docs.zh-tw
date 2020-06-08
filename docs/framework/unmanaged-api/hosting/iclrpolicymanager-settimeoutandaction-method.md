---
title: ICLRPolicyManager::SetTimeoutAndAction 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 02e836601be72d54f561e077cd3c466470bafb25
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504091"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction 方法
設定指定之作業的超時值，並指定當作業發生時，common language runtime （CLR）應採取的原則動作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>參數  
 `operation`  
 在其中一個[EClrOperation](eclroperation-enumeration.md)值，表示要設定其超時和原則的作業 `action` 。 支援下列值：  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 在新的超時值（以毫秒為單位）。 無限值會導致 `operation` 永遠不會超時。  
  
 `action`  
 在其中一個[EPolicyAction](epolicyaction-enumeration.md)值，表示 CLR 在發生時應採取的原則動作 `operation` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|無法為指定的設定超時 `operation` ，或為提供了不正確值 `action` 。|  
  
## <a name="remarks"></a>備註  
 `SetTimeoutAndAction`封裝[ICLRPolicyManager：： SetTimeout](iclrpolicymanager-settimeout-method.md)和[ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)方法的功能，而且可以呼叫這兩個方法的連續呼叫來取代。  
  
> [!IMPORTANT]
> 並非所有的原則動作值都可以指定為 CLR 作業的超時行為。 如需有效值的這兩個方法，請參閱主題的「備註」小節。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrOperation 列舉](eclroperation-enumeration.md)
- [EPolicyAction 列舉](epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [SetActionOnTimeout 方法](iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager：： SetTimeoutAndAction](iclrpolicymanager-settimeoutandaction-method.md)
