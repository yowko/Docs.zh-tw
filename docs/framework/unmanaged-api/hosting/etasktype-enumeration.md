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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73098077e3860d3f4a8a02921ecedf8dff24165b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774054"
---
# <a name="etasktype-enumeration"></a>ETaskType 列舉
包含值，表示工作透過下列方式表示的型別[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)該[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)介面。  
  
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
|`TT_ADUNLOAD`|介面代表應用程式定義域卸載的工作。|  
|`TT_DEBUGGERHELPER`|介面表示偵錯工具協助程式工作。|  
|`TT_FINALIZER`|介面表示完成項工作。|  
|`TT_GC`|介面表示記憶體回收工作。|  
|`TT_THREADPOOL_GATE`|介面表示閘道執行緒工作。|  
|`TT_THREADPOOL_IOCOMPLETION`|介面代表 「 I/O 執行緒的工作或完成連接埠執行緒工作。|  
|`TT_THREADPOOL_TIMER`|介面表示計時器執行緒工作。|  
|`TT_THREADPOOL_WAIT`|介面表示等候執行緒工作。|  
|`TT_THREADPOOL_WORKER`|介面代表背景工作執行緒的工作。|  
|`TT_UNKNOWN`|未知的工作。|  
|`TT_USER`|介面代表使用者的工作。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
