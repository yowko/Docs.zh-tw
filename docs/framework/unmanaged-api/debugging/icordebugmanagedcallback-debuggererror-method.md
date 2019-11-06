---
title: ICorDebugManagedCallback::DebuggerError 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137379"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError 方法
通知偵錯工具，在嘗試處理來自 common language runtime （CLR）的事件時發生錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 在代表發生事件之進程的 "ICorDebugProcess" 物件指標。  
  
 `errorHR`  
 在從事件處理常式傳回的 HRESULT 值。  
  
 `errorCode`  
 在指定 CLR 錯誤的整數。  
  
## <a name="remarks"></a>備註  
 視錯誤的性質而定，此程式可能會置於傳遞模式。  
  
 `DebugError` 回呼表示因為發生錯誤而停用了偵錯工具，因此偵錯工具應該將錯誤訊息提供給使用者。 [ICorDebugProcess：： GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)可放心呼叫，但不應呼叫所有其他方法，包括[ICorDebug：： Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)。 偵錯工具應該使用作業系統功能來終止進程。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
