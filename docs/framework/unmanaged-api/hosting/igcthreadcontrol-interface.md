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
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721682"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl 介面

提供方法來參與執行緒的排程，而這些執行緒會被封鎖，以進行垃圾收集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](igcthreadcontrol-suspensionending-method.md)|通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。|  
|[SuspensionStarting 方法](igcthreadcontrol-suspensionstarting-method.md)|通知主機執行時間正在等待垃圾收集或其他暫止的執行緒暫停。|  
|[ThreadIsBlockingForSuspension 方法](igcthreadcontrol-threadisblockingforsuspension-method.md)|通知主機發出呼叫的執行緒即將封鎖，或許是針對垃圾收集或其他擱置。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
