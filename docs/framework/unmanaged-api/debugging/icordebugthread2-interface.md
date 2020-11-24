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
ms.openlocfilehash: fd4ad536d7d3df2b8f91f206459122cf083c8b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691132"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 介面

作為 ICorDebugThread 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetActiveFunctions 方法](icordebugthread2-getactivefunctions-method.md)|取得 COR_ACTIVE_FUNCTION 實例的陣列，其中包含執行緒框架中作用中函式的相關資料。|  
|[GetConnectionID 方法](icordebugthread2-getconnectionid-method.md)|取得這個的連接識別碼 `ICorDebugThread2` 。|  
|[GetTaskID 方法](icordebugthread2-gettaskid-method.md)|取得這個的工作識別碼 `ICorDebugThread2` 。|  
|[GetVolatileOSThreadID 方法](icordebugthread2-getvolatileosthreadid-method.md)|取得這個的作業系統執行緒識別碼 `ICorDebugThread2` 。|  
|[InterceptCurrentException 方法](icordebugthread2-interceptcurrentexception-method.md)|允許偵錯工具攔截執行緒上目前的例外狀況。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
