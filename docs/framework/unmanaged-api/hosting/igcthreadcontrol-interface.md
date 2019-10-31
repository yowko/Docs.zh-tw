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
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134806"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl 介面
提供方法來參與執行緒的排程，否則會封鎖垃圾收集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。|  
|[SuspensionStarting 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|通知主機執行時間正在中止垃圾收集或其他暫停的執行緒。|  
|[ThreadIsBlockingForSuspension 方法](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|通知主機發出呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
