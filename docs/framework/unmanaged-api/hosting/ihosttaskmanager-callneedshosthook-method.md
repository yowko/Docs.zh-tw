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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176288"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook 方法
使主機能夠指定通用語言運行時 （CLR） 是否可以將指定的調用內聯到非託管函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>參數  
 `target`  
 [在]要調用的非託管函數的映射的可移植可執行 （PE） 檔中的位址。  
  
 `pbCallNeedsHostHook`  
 [出]指向布林值的指標，指示主機是否需要掛接調用。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 當方法返回E_FAIL時，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 為了説明優化代碼執行，CLR 在編譯期間對每個平台叫用調用執行分析，以確定調用是否可以內聯。 `CallNeedsHostHook`使主機通過要求對非託管函數的調用進行掛接來覆蓋該決策。 如果主機需要掛鉤，則運行時不會內聯呼叫。  
  
 主機通常需要一個掛鉤，它必須調整浮點狀態，或在收到通知時，呼叫正在進入一個狀態，其中主機無法跟蹤運行時的記憶體請求或獲取的任何鎖。 當主機要求掛接調用時，運行時通過使用對[EnterRuntime、](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)[離開運行時](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)、[反向EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)和[反向LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)的調用來通知主機與託管代碼轉換。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
