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
ms.openlocfilehash: 21838bdd8ff45f8f74524dc4da52364fb032b396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723398"
---
# <a name="icordebug-interface"></a>ICorDebug 介面

提供的方法可讓開發人員在 common language runtime (CLR) 環境中，進行應用程式的偵錯工具。  
  
> [!NOTE]
> 在 Windows 95、Windows 98 或 Windows ME 或非 x86 平臺 (（例如 IA64 和 AMD64) ）上，不支援混合模式 (managed 和機器碼) 的偵錯工具。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanLaunchOrAttach 方法](icordebug-canlaunchorattach-method.md)|判斷在目前電腦和執行時間設定的內容中，是否可以啟動新的進程或附加至指定的進程。|  
|[CreateProcess 方法](icordebug-createprocess-method.md)|在偵錯工具的控制下啟動進程和其主要執行緒。|  
|[DebugActiveProcess 方法](icordebug-debugactiveprocess-method.md)|將偵錯工具附加至現有的進程。|  
|[EnumerateProcesses 方法](icordebug-enumerateprocesses-method.md)|取得正在進行調試之進程的列舉值。|  
|[GetProcess 方法](icordebug-getprocess-method.md)|傳回具有指定處理序識別碼的 "ICorDebugProcess" 物件。|  
|[Initialize 方法](icordebug-initialize-method.md)|初始化 `ICorDebug` 物件。|  
|[SetManagedHandler 方法](icordebug-setmanagedhandler-method.md)|指定 managed 事件的事件處理常式物件。|  
|[SetUnmanagedHandler 方法](icordebug-setunmanagedhandler-method.md)|指定非受控事件的事件處理常式物件。|  
|[Terminate 方法](icordebug-terminate-method.md)|終止 `ICorDebug` 物件。|  
  
## <a name="remarks"></a>備註  

 `ICorDebug` 代表偵錯工具進程的事件處理迴圈。 偵錯工具必須等待所有正在進行的進程的 [ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md) 回呼，再釋放這個介面。  
  
 `ICorDebug`物件是用來控制所有進一步 managed 偵錯工具的初始物件。 在 .NET Framework 1.0 和1.1 版中，此物件是 `CoClass` 從 COM 建立的物件。 在 .NET Framework 2.0 版中，此物件不再是 `CoClass` 物件。 它必須由 [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) 函式所建立，此函式可感知版本。 這個新的建立函式可讓用戶端取得的特定執行 `ICorDebug` ，這也會模擬特定版本的偵錯工具 API。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
