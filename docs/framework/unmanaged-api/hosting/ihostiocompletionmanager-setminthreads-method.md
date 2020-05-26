---
title: IHostIoCompletionManager::SetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 29a2fc5652badcc00378192debccba0356f5339e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804660"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a>IHostIoCompletionManager::SetMinThreads 方法
設定主機應該為 i/o 完成所配置的執行緒數目下限。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwMinIoCompletionThreads`  
 在主機應該建立的 i/o 完成執行緒最小數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetMinThreads`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOTIMPL|主機未提供的執行 `SetMinThreads` 。|  
  
## <a name="remarks"></a>備註  
 主機可能會想要獨佔控制可配置給處理 i/o 要求的執行緒數目，原因包括執行、效能或擴充性。 基於這個理由，主機不需要執行 `SetMinThreads` 。 在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [SetMaxThreads 方法](ihostiocompletionmanager-setmaxthreads-method.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
