---
title: "ETaskType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52e027c5d2ead70bbd624fafe3021121557cd261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="etasktype-enumeration"></a>ETaskType 列舉
包含值，表示由表示的工作類型[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)或[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`TT_ADUNLOAD`|介面代表應用程式定義域的卸載工作。|  
|`TT_DEBUGGERHELPER`|介面表示偵錯工具 helper 工作。|  
|`TT_FINALIZER`|介面代表完成工作。|  
|`TT_GC`|介面表示記憶體回收工作。|  
|`TT_THREADPOOL_GATE`|介面代表閘道執行緒工作。|  
|`TT_THREADPOOL_IOCOMPLETION`|介面表示 I/O 執行緒工作或 「 完成連接埠執行緒工作。|  
|`TT_THREADPOOL_TIMER`|介面表示計時器執行緒工作。|  
|`TT_THREADPOOL_WAIT`|介面表示等候執行緒工作。|  
|`TT_THREADPOOL_WORKER`|介面代表背景工作執行緒工作。|  
|`TT_UNKNOWN`|未知的工作。|  
|`TT_USER`|介面代表使用者工作。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
