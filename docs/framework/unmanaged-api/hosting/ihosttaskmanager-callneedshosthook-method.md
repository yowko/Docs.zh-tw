---
title: IHostTaskManager::CallNeedsHostHook 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 7c7af1bbf3d13c3f66d525dfce69d8b49fbe045c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675135"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook 方法

可讓主機指定 common language runtime (CLR) 是否可以將指定的呼叫內嵌至非受控函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>參數  

 `target`  
 在在對應的可執行檔中， (PE) 要呼叫之非受控函式的檔案內的位址。  
  
 `pbCallNeedsHostHook`  
 擴展布林值的指標，指出主機是否需要連結呼叫。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 為了協助優化程式碼執行，CLR 會在編譯期間執行每個平台叫用呼叫的分析，以判斷呼叫是否可以內嵌。 `CallNeedsHostHook` 藉由要求呼叫非受控函式，讓主機覆寫該決策。 如果主機需要勾點，則執行時間不會內嵌呼叫。  
  
 主機通常需要有必須調整浮點數狀態的勾點，或是收到呼叫進入的通知，指出主機無法追蹤執行時間的記憶體要求或任何所採取的鎖定。 當主機需要呼叫的呼叫時，執行時間會使用 [EnterRuntime](ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)、 [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)和 [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫，通知主機 managed 程式碼的轉換。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
