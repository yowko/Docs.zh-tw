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
ms.openlocfilehash: afbf480d69e97662b5963706bb8c192aec0325a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966286"
---
# <a name="icordebug-interface"></a>ICorDebug 介面
提供可讓開發人員在 common language runtime (CLR) 環境中, 對應用程式進行 debug 的方法。  
  
> [!NOTE]
> Windows 95、Windows 98 或 Windows ME 或非 x86 平臺 (例如 IA64 和 AMD64) 不支援混合模式 (managed 和機器碼) 的偵錯工具。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[CanLaunchOrAttach 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|判斷是否可以在目前的電腦和執行時間設定的內容中, 啟動新的進程或附加至指定的進程。|  
|[CreateProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|在偵錯工具的控制項底下啟動進程和其主要執行緒。|  
|[DebugActiveProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|將偵錯工具附加至現有的進程。|  
|[EnumerateProcesses 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|取得正在進行調試之進程的列舉值。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|傳回具有指定處理序識別碼的 "ICorDebugProcess" 物件。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|初始化 `ICorDebug` 物件。|  
|[SetManagedHandler 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|指定 managed 事件的事件處理常式物件。|  
|[SetUnmanagedHandler 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|指定非受控事件的事件處理常式物件。|  
|[Terminate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|`ICorDebug`終止物件。|  
  
## <a name="remarks"></a>備註  
 `ICorDebug`表示偵錯工具進程的事件處理迴圈。 偵錯工具必須等到所有進程中的[ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼, 才會釋放此介面。  
  
 `ICorDebug`物件是用來控制所有進一步 managed 調試的初始物件。 在 .NET Framework 版本1.0 和1.1 中, 此物件是從`CoClass` COM 建立的物件。 在 .NET Framework 版本2.0 中, 此物件`CoClass`不再是物件。 它必須由[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式所建立, 這是更容易感知版本的功能。 這個新的建立功能可讓用戶端取得的特定`ICorDebug`執行, 這也會模擬特定版本的調試 API。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
