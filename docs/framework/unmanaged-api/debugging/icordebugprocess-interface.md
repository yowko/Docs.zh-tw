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
ms.openlocfilehash: 7f9d4ac99234545ef75d9b91e6e84f79a133ffef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694915"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess 介面

表示執行 Managed 程式碼的處理序。 此介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearCurrentException 方法](icordebugprocess-clearcurrentexception-method.md)|清除指定執行緒上目前的非受控例外狀況。|  
|[EnableLogMessages 方法](icordebugprocess-enablelogmessages-method.md)|啟用和停用將記錄訊息傳送至偵錯工具。|  
|[EnumerateAppDomains 方法](icordebugprocess-enumerateappdomains-method.md)|列舉進程中的所有應用程式域。|  
|[EnumerateObjects 方法](icordebugprocess-enumerateobjects-method.md)|未實作。|  
|[GetHandle 方法](icordebugprocess-gethandle-method.md)|取得進程的控制碼。|  
|[GetHelperThreadID 方法](icordebugprocess-gethelperthreadid-method.md)|取得作業系統 (作業系統) 偵錯工具內部 helper 執行緒的執行緒識別碼。|  
|[GetID 方法](icordebugprocess-getid-method.md)|取得進程的作業系統 (OS) 識別碼。|  
|[GetObject 方法](icordebugprocess-getobject-method.md)|未實作。|  
|[GetThread 方法](icordebugprocess-getthread-method.md)|取得具有指定之 OS 執行緒識別碼的 ICorDebugThread 實例。|  
|[GetThreadContext 方法](icordebugprocess-getthreadcontext-method.md)|取得指定執行緒的內容。|  
|[IsOSSuspended 方法](icordebugprocess-isossuspended-method.md)|判斷線程是否因偵錯工具停止進程而暫止。|  
|[IsTransitionStub 方法](icordebugprocess-istransitionstub-method.md)|判斷位址是否在會導致轉換成 managed 程式碼的存根內。|  
|[ModifyLogSwitch 方法](icordebugprocess-modifylogswitch-method.md)|設定指定之記錄參數的嚴重性層級。|  
|[ReadMemory 方法](icordebugprocess-readmemory-method.md)|從進程讀取記憶體。|  
|[SetThreadContext 方法](icordebugprocess-setthreadcontext-method.md)|設定指定執行緒的內容。|  
|[ThreadForFiberCookie 方法](icordebugprocess-threadforfibercookie-method.md)|已取代。|  
|[WriteMemory 方法](icordebugprocess-writememory-method.md)|將資料寫入進程中的記憶體區域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
- [偵錯介面](debugging-interfaces.md)
