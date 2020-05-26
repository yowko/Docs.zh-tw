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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805120"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl 介面
提供方法來參與執行緒的排程，否則會封鎖垃圾收集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](igcthreadcontrol-suspensionending-method.md)|通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。|  
|[SuspensionStarting 方法](igcthreadcontrol-suspensionstarting-method.md)|通知主機執行時間正在中止垃圾收集或其他暫停的執行緒。|  
|[ThreadIsBlockingForSuspension 方法](igcthreadcontrol-threadisblockingforsuspension-method.md)|通知主機發出呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
