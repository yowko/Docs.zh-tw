---
title: ICorDebug 介面
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebug-interface"></a>ICorDebug 介面
提供方法，可讓開發人員偵錯在 common language runtime (CLR) 環境中的應用程式。  
  
> [!NOTE]
>  不支援偵錯混合模式 （managed 與原生程式碼），在 Windows 95、 Windows 98 或 Windows ME 或非 x86 的平台 （例如 IA64 和 AMD64）。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanLaunchOrAttach 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|判斷是否可能在目前的電腦以及執行階段組態的內容中啟動新的處理序或附加至指定的處理序。|  
|[CreateProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|啟動處理序與它所控制的偵錯工具的主要執行緒。|  
|[DebugActiveProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|將偵錯工具附加至現有的處理序。|  
|[EnumerateProcesses 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|取得正在進行偵錯的處理程序中的列舉值。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|傳回"ICorDebugProcess 」 物件，並提供指定的處理序識別碼。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|初始化 `ICorDebug` 物件。|  
|[SetManagedHandler 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|指定 managed 事件的事件處理常式物件。|  
|[SetUnmanagedHandler 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|指定 unmanaged 事件的事件處理常式的物件。|  
|[Terminate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|終止`ICorDebug`物件。|  
  
## <a name="remarks"></a>備註  
 `ICorDebug` 表示在偵錯工具處理序的事件處理迴圈。 偵錯工具必須等候[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)從所有處理序進行偵錯之前釋出此介面的回呼。  
  
 `ICorDebug`物件是要控制所有進一步 managed 偵錯的初始物件。 在.NET framework 1.0 和 1.1 版中，這個物件是`CoClass`所建立的 COM 物件 在.NET Framework 2.0 版中，此物件已不再`CoClass`物件。 它必須先建立[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式，也就是多版本感知。 這個新的建立函式可讓用戶端取得的特定實作`ICorDebug`，也是模擬偵錯 API 的特定版本。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
