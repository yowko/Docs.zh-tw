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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762822"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 介面
提供的方法可讓主機明確要求 common language runtime （CLR）建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|明確要求 CLR 建立新的[ICLRTask](iclrtask-interface.md)實例。|  
|[GetCurrentTask 方法](iclrtaskmanager-getcurrenttask-method.md)|取得 `ICLRTask` 表示目前正在執行之工作的實例。|  
|[GetCurrentTaskType 方法](iclrtaskmanager-getcurrenttasktype-method.md)|取得目前正在執行之工作的型別。|  
|[SetLocale 方法](iclrtaskmanager-setlocale-method.md)|通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。|  
|[SetUILocale 方法](iclrtaskmanager-setuilocale-method.md)|通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。|  
  
## <a name="remarks"></a>備註  
 在主控環境中執行的每個工作都有主機端（ [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)的實例）和 CLR 端（ [ICLRTask](iclrtask-interface.md)的實例）的標記法。 主機或 CLR 可以起始工作的建立作業，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主機與 CLR 之間的工作相關成功通訊。 您必須先建立和具現化這兩個物件，然後才能在作業系統執行緒上執行 managed 程式碼。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
