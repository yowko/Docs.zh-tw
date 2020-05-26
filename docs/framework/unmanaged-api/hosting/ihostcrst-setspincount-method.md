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
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804874"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount 方法
設定目前[IHostCrst](ihostcrst-interface.md)實例的微調計數。  
  
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
|S_OK|`SetSpinCount`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 在多處理器系統上，如果目前實例所代表的重要區段 `IHostCrst` 無法使用，呼叫執行緒會在 `dwSpinCount` 呼叫[IHostSemaphore：： Wait](ihostsemaphore-wait-method.md) （與重要區段相關聯的信號）之前旋轉時間。 如果關鍵區段在微調作業期間變得免費，呼叫的執行緒會避免等候作業。  
  
 的使用方式與 Win32 函式 `dwSpinCount` 中相同名稱的參數用法相同 `InitializeCriticalSectionAndSpinCount` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostCrst 介面](ihostcrst-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
