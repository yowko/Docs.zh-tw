---
title: ICLRTaskManager 介面
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763369"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 介面
提供方法，可讓主應用程式明確要求，common language runtime (CLR) 建立新的工作、 取得目前正在執行的工作，並設定地理的語言和文化特性的工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|明確要求建立新的 CLR [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|取得`ICLRTask`代表目前正在執行之工作的執行個體。|  
|[GetCurrentTaskType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|取得目前正在執行之工作的類型。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|通知 CLR 主機已經修改目前執行之工作的地區設定識別項。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|通知 common language runtime 主應用程式已修改目前執行之工作的使用者介面的地區設定識別項。|  
  
## <a name="remarks"></a>備註  
 正在裝載環境中執行每項工作會將表示這兩個對主機端 (執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) 和 CLR 端 (執行個體[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md))。 主應用程式或 CLR 可以開始建立一項工作，但主應用程式端表示法必須與對應的 CLR 方表示法，以確保在主機與工作相關 CLR 之間的成功通訊相關聯。 必須建立兩個物件，並具現化 managed 程式碼可以在作業系統執行緒上執行之前。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
