---
title: ICLRMemoryNotificationCallback::OnMemoryNotification 方法
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: 11b9b500e16917498856888c437c58c0df2edafb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140981"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a>ICLRMemoryNotificationCallback::OnMemoryNotification 方法
通知 common language runtime （CLR）電腦上的記憶體負載。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a>參數  
 `eMemoryAvailable`  
 在其中一個[EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)值，表示電腦目前遇到的記憶體壓力。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `OnMemoryNotification`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 會使用[IHostMemoryManager：： RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)方法的呼叫，將回呼註冊到 `OnMemoryNotification`。 執行時間會使用在回呼中傳回的資訊，在主機報告記憶體資源的不足時釋放額外的記憶體。  
  
> [!NOTE]
> 對 `OnMemoryNotification` 的呼叫永遠不會封鎖。 它們一律會立即傳回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [RegisterMemoryNotificationCallback 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [ICLRMemoryNotificationCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
