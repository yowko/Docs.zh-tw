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
ms.openlocfilehash: 22274759f931da614a234efe0a6f6eb3aade027c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729560"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount 方法

設定目前 [IHostCrst](ihostcrst-interface.md) 實例的微調計數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwSpinCount`  
 在目前實例的新微調計數 `IHostCrst` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetSpinCount` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 在多處理器系統上，如果目前實例所代表的重要區段 `IHostCrst` 無法使用，呼叫執行緒會在 `dwSpinCount` 與重要區段相關聯的信號上呼叫 [IHostSemaphore：： Wait](ihostsemaphore-wait-method.md) 之前，先旋轉時間。 如果重要區段在微調作業期間變成可用，則呼叫執行緒會避免等候作業。  
  
 的使用 `dwSpinCount` 方式與 Win32 函數中相同名稱的參數使用方式相同 `InitializeCriticalSectionAndSpinCount` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostCrst 介面](ihostcrst-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
