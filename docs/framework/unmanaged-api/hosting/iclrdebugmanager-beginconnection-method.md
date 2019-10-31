---
title: ICLRDebugManager::BeginConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 2ac2b0dde97b883313e1bca17c5e99855484e4aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126566"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection 方法
在主機與偵錯工具之間建立新的連接，以將工作清單與識別碼和易記名稱產生關聯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwConnectionId`  
 在要與 common language runtime （CLR）工作清單建立關聯的識別碼。  
  
 `szConnectionName`  
 在要與 CLR 工作清單產生關聯的易記名稱。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `BeginConnection`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|`dwConnectionId` 為零，或已經使用此 `dwConnectionId` 值呼叫 `BeginConnection`，或 `szConnectionName` 為 null。|  
|E_OUTOFMEMORY|無法配置足夠的記憶體來保存與此連接相關聯的工作清單。|  
  
## <a name="remarks"></a>備註  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法： `BeginConnection`、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，以便將工作清單與識別碼和易記名稱產生關聯。  
  
> [!IMPORTANT]
> 這三種方法都必須以特定順序針對每一組工作進行呼叫。 首先會呼叫 `BeginConnection` 以建立新的連接。 下一步會呼叫 `SetConnectionTasks`，以提供與該連接相關聯的工作集合。 最後會呼叫 `EndConnection`，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [EndConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
