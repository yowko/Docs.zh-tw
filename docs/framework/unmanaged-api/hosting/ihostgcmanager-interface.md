---
title: IHostGCManager 介面
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804847"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager 介面
提供方法，以通知 common language runtime （CLR）所實作為垃圾收集機制的事件主機。  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](ihostgcmanager-suspensionending-method.md)|通知主機 CLR 正在繼續執行已暫止垃圾收集的執行緒上的工作。|  
|[SuspensionStarting 方法](ihostgcmanager-suspensionstarting-method.md)|通知主機 CLR 正在暫停執行工作，以執行垃圾收集。|  
|[ThreadIsBlockingForSuspension 方法](ihostgcmanager-threadisblockingforsuspension-method.md)|通知主機，方法呼叫的來源執行緒即將封鎖進行垃圾收集。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
