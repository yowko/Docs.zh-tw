---
title: IHostPolicyManager::OnTimeout 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: e3f2dc7ff9beaf417184f3d09db76e611982118a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690664"
---
# <a name="ihostpolicymanagerontimeout-method"></a>IHostPolicyManager::OnTimeout 方法

通知主機 common language runtime (CLR) 即將採取 [ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) 方法呼叫所指定的動作，以回應超時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a>參數  

 `operation`  
 在其中一個 [EClrOperation](eclroperation-enumeration.md) 值，表示超時的作業種類。  
  
 `action`  
 在其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，表示 CLR 為了回應超時所採取的動作。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OnTimeout` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrOperation 列舉](eclroperation-enumeration.md)
- [EPolicyAction 列舉](epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
