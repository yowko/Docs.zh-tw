---
title: ICorDebugThread2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d21c221bba3ac668924003f96580bb660229ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962996"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 介面
作為 ICorDebugThread 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetActiveFunctions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|取得 COR_ACTIVE_FUNCTION 實例的陣列, 其中包含執行緒框架中作用中函式的相關資料。|  
|[GetConnectionID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|取得這個`ICorDebugThread2`的連接識別碼。|  
|[GetTaskID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|取得這個`ICorDebugThread2`的工作識別碼。|  
|[GetVolatileOSThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|取得這個`ICorDebugThread2`的作業系統執行緒識別碼。|  
|[InterceptCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|允許偵錯工具攔截執行緒上目前的例外狀況。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
