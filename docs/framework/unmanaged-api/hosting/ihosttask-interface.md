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
ms.openlocfilehash: 1b7209a36f8e9d6f02bd4cc1882adeef8af30c3d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503914"
---
# <a name="ihosttask-interface"></a>IHostTask 介面
提供可讓 common language runtime （CLR）與主機通訊的方法，以管理工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alert 方法](ihosttask-alert-method.md)|要求主機喚醒目前實例所代表的工作 `IHostTask` ，讓工作可以中止。|  
|[GetPriority 方法](ihosttask-getpriority-method.md)|取得目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。|  
|[Join 方法](ihosttask-join-method.md)|封鎖呼叫工作，直到目前實例所代表的工作 `IHostTask` 完成、已超過指定的時間間隔，或呼叫[IHostTask：： Alert](ihosttask-alert-method.md)為止。|  
|[SetCLRTask 方法](ihosttask-setclrtask-method.md)|將[ICLRTask 介面](iclrtask-interface.md)實例與目前的實例產生關聯 `IHostTask` 。|  
|[SetPriority 方法](ihosttask-setpriority-method.md)|要求主機調整目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。|  
|[Start 方法](ihosttask-start-method.md)|要求主機將目前實例所代表的工作 `IHostTask` 從暫停狀態移動到即時狀態，在此情況下可以執行程式碼。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫所定義的方法 `IHostTask` 來啟動工作、設定其執行緒優先順序層級等等。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
