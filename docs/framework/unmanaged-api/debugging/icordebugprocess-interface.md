---
title: ICorDebugProcess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423165"
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
表示執行 Managed 程式碼的處理序。 這個介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|清除指定的執行緒上目前的 unmanaged 例外狀況。|  
|[EnableLogMessages 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|啟用和停用記錄檔訊息傳送給偵錯工具。|  
|[EnumerateAppDomains 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|列舉中的所有應用程式網域的程序。|  
|[EnumerateObjects 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|未實作。|  
|[GetHandle 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|取得處理程序的控制代碼。|  
|[GetHelperThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒 ID。|  
|[GetID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|取得處理序的作業系統 (OS) 識別碼。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|未實作。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|取得具有指定的作業系統執行緒的 ICorDebugThread 執行個體識別碼。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|取得指定執行緒的內容。|  
|[IsOSSuspended 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|判斷執行緒是否已暫止偵錯工具停止處理序的結果。|  
|[IsTransitionStub 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|判斷是否會導致轉換為 managed 程式碼的虛設常式內位址。|  
|[ModifyLogSwitch 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|設定參數，因為指定的記錄檔的嚴重性層級。|  
|[ReadMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|處理程序會讀取記憶體。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|設定指定之執行緒的內容。|  
|[ThreadForFiberCookie 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|已取代。|  
|[WriteMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|將資料寫入的處理序中的記憶體區域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
