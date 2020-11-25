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
ms.openlocfilehash: eb7e52b5237d4341c27b8c167249dc2614168679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729515"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager 介面

提供方法，在 common language runtime (CLR) 所執行的垃圾收集機制中，通知主機事件。  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](ihostgcmanager-suspensionending-method.md)|通知主機 CLR 正在暫停執行垃圾收集的執行緒上執行工作。|  
|[SuspensionStarting 方法](ihostgcmanager-suspensionstarting-method.md)|通知主機 CLR 正在暫停執行工作，以執行垃圾收集。|  
|[ThreadIsBlockingForSuspension 方法](ihostgcmanager-threadisblockingforsuspension-method.md)|通知主機發出方法呼叫的執行緒，即將封鎖垃圾收集。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
