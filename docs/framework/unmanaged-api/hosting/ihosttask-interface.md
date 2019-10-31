---
title: IHostTask 介面
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121386"
---
# <a name="ihosttask-interface"></a>IHostTask 介面
提供可讓 common language runtime （CLR）與主機通訊的方法，以管理工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alert 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|要求主機喚醒目前 `IHostTask` 實例所代表的工作，讓工作可以中止。|  
|[GetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|取得目前 `IHostTask` 實例所表示之工作的執行緒優先權層級。|  
|[Join 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|封鎖呼叫工作，直到目前的 `IHostTask` 實例所表示的工作完成、已超過指定的時間間隔，或呼叫[IHostTask：： Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)為止。|  
|[SetCLRTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|將[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例與目前的 `IHostTask` 實例產生關聯。|  
|[SetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|要求主機針對目前 `IHostTask` 實例所表示的工作，調整執行緒優先順序層級。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|要求主機將目前 `IHostTask` 實例所代表的工作從暫停狀態移至即時狀態，在其中可執行程式碼。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫 `IHostTask` 所定義的方法來啟動工作、設定其執行緒優先順序層級等等。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
