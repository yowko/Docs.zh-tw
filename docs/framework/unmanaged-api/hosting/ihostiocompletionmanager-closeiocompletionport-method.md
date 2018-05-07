---
title: IHostIoCompletionManager::CloseIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 761e3b22014bdd628ffc6763615a285a16a86309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a>IHostIoCompletionManager::CloseIoCompletionPort 方法
要求主機關閉的連接埠已開啟的檔案之前呼叫， [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hPort`  
 [in]若要關閉的連接埠控制代碼。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CloseIoCompletionPort` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|傳遞了無效的連接埠控制代碼。|  
  
## <a name="remarks"></a>備註  
 `hPort` 必須是已由先前呼叫所建立的連接埠的控制代碼`CreateIoCompletionPort`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [IHostIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
