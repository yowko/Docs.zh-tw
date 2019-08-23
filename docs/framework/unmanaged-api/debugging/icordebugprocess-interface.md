---
title: ICorDebugProcess 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943307"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess 介面
表示執行 Managed 程式碼的處理序。 這個介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[ClearCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|清除指定執行緒上目前的非受控例外狀況。|  
|[EnableLogMessages 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|啟用和停用將記錄訊息傳送至偵錯工具的功能。|  
|[EnumerateAppDomains 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|列舉進程中的所有應用程式域。|  
|[EnumerateObjects 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|未實作。|  
|[GetHandle 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|取得進程的控制碼。|  
|[GetHelperThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|取得偵錯工具內部 helper 執行緒的作業系統 (OS) 執行緒識別碼。|  
|[GetID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|取得進程的作業系統 (OS) 識別碼。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|未實作。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|取得具有指定之 OS 執行緒識別碼的 ICorDebugThread 實例。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|取得給定執行緒的內容。|  
|[IsOSSuspended 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|判斷線程是否因偵錯工具停止進程而暫停。|  
|[IsTransitionStub 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|判斷位址是否在將導致轉換成 managed 程式碼的存根內部。|  
|[ModifyLogSwitch 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|設定指定之記錄參數的嚴重性層級。|  
|[ReadMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|從進程讀取記憶體。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|設定指定執行緒的內容。|  
|[ThreadForFiberCookie 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|已取代。|  
|[WriteMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|將資料寫入進程中的記憶體區域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
