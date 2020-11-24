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
ms.openlocfilehash: 937a2fb322eb63461d90e215635e1b10ab6afd09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689780"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 介面

提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。 `ICorDebugManagedCallback2` 是 [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ChangeConnection 方法](icordebugmanagedcallback2-changeconnection-method.md)|通知偵錯工具，與指定之連接相關聯的工作集已變更。|  
|[CreateConnection 方法](icordebugmanagedcallback2-createconnection-method.md)|通知偵錯工具已建立新的連接。|  
|[DestroyConnection 方法](icordebugmanagedcallback2-destroyconnection-method.md)|通知偵錯工具已終止指定的連接。|  
|[Exception 方法](icordebugmanagedcallback2-exception-method.md)|通知偵錯工具已開始搜尋例外狀況處理常式。|  
|[ExceptionUnwind 方法](icordebugmanagedcallback2-exceptionunwind-method.md)|提供例外狀況回溯進程期間的狀態通知。|  
|[FunctionRemapComplete 方法](icordebugmanagedcallback2-functionremapcomplete-method.md)|通知偵錯工具程式碼執行已切換至新版本的編輯函式。|  
|[FunctionRemapOpportunity 方法](icordebugmanagedcallback2-functionremapopportunity-method.md)|通知偵錯工具程式碼執行已在較舊版本的已編輯函式中到達序列點。|  
|[MDANotification 方法](icordebugmanagedcallback2-mdanotification-method.md)|提供程式碼執行在 (MDA) 訊息中遇到 managed 偵錯工具的通知。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugManagedCallback2`介面會擴充 `ICorDebugManagedCallback` 介面，以處理 .NET Framework 版本2.0 中引進的新的 debug 事件。  
  
 `ICorDebugManagedCallback2`如果偵錯工具正在進行 .NET Framework 2.0 應用程式的偵錯工具，則必須執行偵錯工具。 或的實例 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` 會以回呼物件的形式傳遞至 [ICorDebug：： SetManagedHandler](icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [偵錯介面](debugging-interfaces.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
