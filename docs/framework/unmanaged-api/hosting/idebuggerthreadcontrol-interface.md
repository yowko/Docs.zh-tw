---
title: IDebuggerThreadControl 介面
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619a28d2382aa9cc3130a3130c07fa1e283119e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl 介面
提供方法來通知主機有關封鎖及解除封鎖的執行緒，偵錯服務。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger 方法](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|通知會傳送此回呼執行緒相關的主機至偵錯服務內的區塊。|  
|[ReleaseAllRuntimeThreads 方法](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|通知主機有偵錯服務即將要釋放所有的執行緒所封鎖。|  
|[StartBlockingForDebugger 方法](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|通知主機偵錯服務即將開始封鎖所有執行緒。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
