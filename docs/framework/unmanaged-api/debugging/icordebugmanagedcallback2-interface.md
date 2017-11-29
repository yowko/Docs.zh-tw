---
title: "ICorDebugManagedCallback2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2
helpviewer_keywords: ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d5b8ac63d200e54d25b58870089f6c062397186
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 介面
提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。 `ICorDebugManagedCallback2`是的邏輯擴充功能[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[ChangeConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|告知偵錯工具使用指定的連接相關聯的工作集，已變更。|  
|[CreateConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|告知偵錯工具已建立新的連接。|  
|[DestroyConnection 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|指定的連接已終止會告知偵錯工具。|  
|[Exception 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|告知偵錯工具搜尋例外狀況處理常式已開始。|  
|[ExceptionUnwind 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|提供例外狀況回溯程序期間的狀態通知。|  
|[FunctionRemapComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|告知偵錯工具執行程式碼已切換為編輯的函式的新版本。|  
|[FunctionRemapOpportunity 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|告知偵錯工具執行程式碼已達到較舊版本的已編輯函式中的序列點。|  
|[MDANotification 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|提供執行程式碼發現 managed 偵錯助理 (MDA) 訊息的通知。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugManagedCallback2`介面延伸`ICorDebugManagedCallback`處理 .NET Framework 2.0 版中引進的新偵錯事件介面。  
  
 偵錯工具必須實作`ICorDebugManagedCallback2`如果它.NET Framework 2.0 應用程式進行偵錯。 執行個體`ICorDebugManagedCallback`或`ICorDebugManagedCallback2`為回呼物件，以傳遞[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
