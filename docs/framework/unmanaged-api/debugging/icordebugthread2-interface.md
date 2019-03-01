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
ms.openlocfilehash: 0e162c114de013eed160a515dbc92fef47ea3327
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980499"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 介面
可做為 ICorDebugThread 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetActiveFunctions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|取得包含執行緒的框架中作用中的函式的相關資料的 COR_ACTIVE_FUNCTION 執行個體的陣列。|  
|[GetConnectionID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|取得這個連接識別碼`ICorDebugThread2`。|  
|[GetTaskID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|取得這個工作識別碼`ICorDebugThread2`。|  
|[GetVolatileOSThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|取得這個作業系統執行緒識別項`ICorDebugThread2`。|  
|[InterceptCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|可讓偵錯工具攔截在執行緒上目前的例外狀況。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
