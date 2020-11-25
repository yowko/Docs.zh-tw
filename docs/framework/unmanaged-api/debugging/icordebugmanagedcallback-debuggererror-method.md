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
ms.openlocfilehash: eb95bf779e54742cd2cc4b688c24a49e6d85a40d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731900"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError 方法

通知偵錯工具，在嘗試處理 common language runtime (CLR) 的事件時發生錯誤。  
  
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
 在"ICorDebugProcess" 物件的指標，表示發生事件的進程。  
  
 `errorHR`  
 在從事件處理常式傳回的 HRESULT 值。  
  
 `errorCode`  
 在指定 CLR 錯誤的整數。  
  
## <a name="remarks"></a>備註  

 視錯誤的性質而定，此程式可能會置於通過模式中。  
  
 `DebugError`回呼表示由於發生錯誤，偵錯工具已停用，因此偵錯工具應該將錯誤訊息提供給使用者。 [ICorDebugProcess：： GetID](icordebugprocess-getid-method.md) 將可安全地呼叫，但不應該呼叫所有其他方法，包括 [ICorDebug：： Terminate](icordebug-terminate-method.md)。 偵錯工具應該使用作業系統功能來終止進程。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
