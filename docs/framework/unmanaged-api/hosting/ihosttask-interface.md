---
title: "IHostTask 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask
helpviewer_keywords: IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a>IHostTask 介面
提供方法讓 common language runtime (CLR) 來管理工作主機進行通訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alert 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|要求主機喚醒表示由目前的工作`IHostTask`執行個體，因此可以中止的工作。|  
|[GetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|取得表示由目前的工作的執行緒優先權等級`IHostTask`執行個體。|  
|[Join 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|表示由目前的工作之前會封鎖呼叫工作`IHostTask`執行個體完成，已超過指定的時間間隔，或[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)呼叫。|  
|[SetCLRTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|將[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)與目前的執行個體`IHostTask`執行個體。|  
|[SetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|表示由目前的工作要求主機調整的執行緒優先權等級`IHostTask`執行個體。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|要求主機移到表示由目前的工作`IHostTask`即時狀態，可執行程式碼的執行個體從暫停狀態。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫所定義的方法`IHostTask`啟動工作，設定它的執行緒優先權層級，依此類推。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
