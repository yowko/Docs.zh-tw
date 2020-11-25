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
ms.openlocfilehash: 1170b29c01275b108a6ccdf6e324c96d97c10c82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732446"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 介面

提供的方法可讓主機明確要求 common language runtime (CLR) 建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateTask 方法](iclrtaskmanager-createtask-method.md)|明確要求 CLR 建立新的 [ICLRTask](iclrtask-interface.md) 實例。|  
|[GetCurrentTask 方法](iclrtaskmanager-getcurrenttask-method.md)|取得 `ICLRTask` 表示目前正在執行之工作的實例。|  
|[GetCurrentTaskType 方法](iclrtaskmanager-getcurrenttasktype-method.md)|取得目前正在執行之工作的類型。|  
|[SetLocale 方法](iclrtaskmanager-setlocale-method.md)|通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。|  
|[SetUILocale 方法](iclrtaskmanager-setuilocale-method.md)|通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。|  
  
## <a name="remarks"></a>備註  

 在裝載環境中執行的每個工作，在主控制項端都具有表示 [IHostTask](ihosttask-interface.md) 實例的 () 和 CLR 端 [ () 的](iclrtask-interface.md) 實例。 主機或 CLR 可以起始工作的建立，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主控制項和 CLR 之間的通訊成功與工作相關。 這兩個物件必須先建立並具現化，managed 程式碼才能在作業系統執行緒上執行。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
