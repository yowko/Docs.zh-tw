---
title: ICLRDebugManager::SetConnectionTasks 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85db4247ebe4a488f7907e195bb0f25f72d87e9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951356"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks 方法
將[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例的清單與識別碼和易記名稱產生關聯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 在與`ppCLRTask`陣列相關聯之連接的主機特定識別碼。  
  
 `dwCount`  
 在的成員`ppCLRTask`數目。 這個數位必須大於零。  
  
 `ppCLRTask`  
 在要與所`ICLRTask` `id`識別之連接產生關聯的指標陣列。 此陣列至少必須包含一個成員。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|尚未使用此值`id`呼叫 [BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)，或`dwCount`或`id`為零，或的其中一個元素`ppCLRTask`為 null。|  
  
## <a name="remarks"></a>備註  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法`BeginConnection`： `SetConnectionTasks`、和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，用來建立工作清單與識別碼和易記名稱的關聯。  
  
> [!IMPORTANT]
> 這三種方法都必須以特定順序針對每一組工作進行呼叫。 `BeginConnection`會先呼叫以建立新的連接。 `SetConnectionTasks`接下來會呼叫，以提供與該連接相關聯的工作集合。 `EndConnection`最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [EndConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
