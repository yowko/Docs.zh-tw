---
title: "ICLRTask::Reset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c50dc4770665e2b049f41a105b58231221b8e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset 方法
通知主機已完成工作，並啟用 CLR，若要重複使用目前的 common language runtime (CLR) [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)來代表另一項工作的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fFull`  
 [in]`true`，如果執行階段應該重設所有與執行緒相關靜態值除了與目前的安全性和地區設定資訊`ICLRTask`執行個體; 否則`false`。  
  
 如果值為`true`，執行階段會重設使用儲存的資料<xref:System.Threading.Thread.AllocateDataSlot%2A>或<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Reset`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或處理呼叫的狀態。 已成功|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 可以回收之前建立`ICLRTask`執行個體，以避免重複建立新的執行個體，每次需要新的工作的額外負荷。 主應用程式啟用這項功能，藉由呼叫`ICLRTask::Reset`而不是[iclrtask:: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)何時完成工作。 下列清單摘要說明一般生命週期的`ICLRTask`執行個體：  
  
1.  執行階段建立新`ICLRTask`執行個體。  
  
2.  執行階段呼叫[ihosttaskmanager:: Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)取得目前的主控件工作的參考。  
  
3.  執行階段呼叫[ihosttask:: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)與 「 主機 」 工作的新執行個體。  
  
4.  工作會執行並完成。  
  
5.  藉由呼叫主機會終結的工作`ICLRTask::ExitTask`。  
  
 `Reset`改變此案例有兩種。 在步驟 5，主機會呼叫上述`Reset`重設為初始狀態的工作，然後以減少`ICLRTask`從及其相關聯的執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。 如有需要，主應用程式也可以快取`IHostTask`供重複使用的執行個體。 步驟 1 上述，以執行階段會提取回收`ICLRTask`從快取，而不是建立的新執行個體。  
  
 這個方法適用於主機也有可重複使用的工作者工作的集區時。 當主機的其中一個終結其`IHostTask`執行個體，它會終結對應`ICLRTask`藉由呼叫`ExitTask`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
