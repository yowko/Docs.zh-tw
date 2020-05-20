---
title: ETaskType 列舉
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 435d23d4a56d6ea98e3d368f0a5aa37c73e31d96
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616160"
---
# <a name="etasktype-enumeration"></a>ETaskType 列舉
包含值，表示由[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)或[IHostTask](ihosttask-interface.md)介面代表的工作類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
|`TT_ADUNLOAD`|介面代表應用程式域卸載工作。|  
|`TT_DEBUGGERHELPER`|介面代表偵錯工具 helper 工作。|  
|`TT_FINALIZER`|介面代表完成項工作。|  
|`TT_GC`|介面代表垃圾收集工作。|  
|`TT_THREADPOOL_GATE`|介面代表閘道執行緒工作。|  
|`TT_THREADPOOL_IOCOMPLETION`|介面代表 i/o 執行緒工作或完成通訊埠執行緒工作。|  
|`TT_THREADPOOL_TIMER`|介面代表計時器執行緒工作。|  
|`TT_THREADPOOL_WAIT`|介面代表等候執行緒工作。|  
|`TT_THREADPOOL_WORKER`|介面代表工作者執行緒工作。|  
|`TT_UNKNOWN`|工作不明。|  
|`TT_USER`|介面代表使用者工作。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
