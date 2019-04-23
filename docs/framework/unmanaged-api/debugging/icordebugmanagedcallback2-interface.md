---
title: ICorDebugManagedCallback2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1ecfea208f87f53f15fcc4cdafb58341c293e43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096084"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 介面
提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。 `ICorDebugManagedCallback2` 是的邏輯擴充[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ChangeConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|告知偵錯工具與指定的連接相關聯的工作集合已變更。|  
|[CreateConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|告知偵錯工具已建立的新的連線。|  
|[DestroyConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|指定的連接已終止會告知偵錯工具。|  
|[Exception 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|已開始搜尋例外狀況處理常式會告知偵錯工具。|  
|[ExceptionUnwind 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|提供例外狀況回溯程序期間的狀態通知。|  
|[FunctionRemapComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|執行程式碼已切換為新版的已編輯的函式會告知偵錯工具。|  
|[FunctionRemapOpportunity 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|告知偵錯工具執行程式碼已達到較舊版本的已編輯的函式中的序列點。|  
|[MDANotification 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|提供執行程式碼發生 managed 偵錯助理 (MDA) 訊息的通知。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugManagedCallback2`介面會擴充`ICorDebugManagedCallback`介面，以處理 .NET Framework 2.0 版中導入新的偵錯事件。  
  
 偵錯工具必須實作`ICorDebugManagedCallback2`如果它.NET Framework 2.0 應用程式進行偵錯。 執行個體`ICorDebugManagedCallback`或是`ICorDebugManagedCallback2`被當做回呼物件[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
