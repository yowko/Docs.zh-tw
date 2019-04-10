---
title: ICLRTask::Reset 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bf7342157de48e0183537afea2f2e53d1498dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300303"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset 方法
通知 common language runtime (CLR) 主機已完成一項工作，並可讓重複使用目前的 CLR [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)來代表另一項工作的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>參數  
 `fFull`  
 [in]`true`，如果執行階段應該重設所有執行緒相關靜態值除了與目前的安全性和地區設定資訊`ICLRTask`執行個體; 否則`false`。  
  
 如果值為`true`，執行階段會使用儲存的資料重設<xref:System.Threading.Thread.AllocateDataSlot%2A>或<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Reset` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 中不能在其中執行 managed 程式碼，或處理呼叫的狀態。 已成功|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 可以回收之前建立`ICLRTask`避免重複建立新的執行個體，每次需要新的工作負載的執行個體。 主應用程式啟用這項功能，藉由呼叫`ICLRTask::Reset`而非[iclrtask:: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)何時已完成工作。 下列清單摘要說明一般生命週期的`ICLRTask`執行個體：  
  
1. 執行階段建立新`ICLRTask`執行個體。  
  
2. 執行階段會呼叫[ihosttaskmanager:: Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)來取得目前的主控件工作的參考。  
  
3. 執行階段會呼叫[ihosttask:: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)主應用程式工作相關聯的新執行個體。  
  
4. 工作執行，並完成。  
  
5. 主機會終結工作，藉由呼叫`ICLRTask::ExitTask`。  
  
 `Reset` 改變此案例中的有兩種。 在步驟 5，主機會呼叫上述`Reset`重設為初始狀態的工作，然後以減少`ICLRTask`與其關聯的執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。 如有需要，主應用程式也可以快取`IHostTask`供重複使用的執行個體。 在步驟 1 所述，執行階段提取回收`ICLRTask`從快取，而不是建立新的執行個體。  
  
 也在主應用程式也有可重複使用的背景工作的工作集區時，適用於這種方法。 當主應用程式會終結的其中一個其`IHostTask`執行個體，它會終結對應`ICLRTask`藉由呼叫`ExitTask`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
