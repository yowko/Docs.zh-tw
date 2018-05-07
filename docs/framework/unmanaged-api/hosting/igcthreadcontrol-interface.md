---
title: IGCThreadControl 介面
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9296aedf24979624c3d7357a4d51be835716a16f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl 介面
提供方法來參與，否則記憶體回收會封鎖執行緒的排程。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|通知主機執行階段會在記憶體回收或其他暫止後繼續處理執行緒。|  
|[SuspensionStarting 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。|  
|[ThreadIsBlockingForSuspension 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|通知主機進行呼叫的執行緒即將封鎖，可能是記憶體回收集合或其他暫止。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
