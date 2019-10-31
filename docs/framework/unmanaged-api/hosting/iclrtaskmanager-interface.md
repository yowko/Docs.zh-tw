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
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092193"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 介面
提供的方法可讓主機明確要求 common language runtime （CLR）建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|明確要求 CLR 建立新的[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|取得表示目前正在執行之工作的 `ICLRTask` 實例。|  
|[GetCurrentTaskType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|取得目前正在執行之工作的型別。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。|  
  
## <a name="remarks"></a>備註  
 在主控環境中執行的每個工作都有主機端（ [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)的實例）和 CLR 端（ [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)的實例）的標記法。 主機或 CLR 可以起始工作的建立作業，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主機與 CLR 之間的工作相關成功通訊。 您必須先建立和具現化這兩個物件，然後才能在作業系統執行緒上執行 managed 程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
