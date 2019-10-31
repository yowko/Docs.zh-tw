---
title: ICorDebugManagedCallback2::ExceptionUnwind 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: fa317e1217ac0a9ca46bfeb312446534b1fca63a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131569"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind 方法
提供例外狀況回溯程式期間的狀態通知。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，表示包含擲回例外狀況之執行緒的應用程式域。  
  
 `pThread`  
 在ICorDebugThread 物件的指標，表示擲回例外狀況的執行緒。  
  
 `dwEventType`  
 在CorDebugExceptionUnwindCallbackType 列舉的值，指定在回溯階段期間由回呼所通知的事件。  
  
 `dwFlags`  
 在[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉的值，指定例外狀況的其他相關資訊。  
  
## <a name="remarks"></a>備註  
 在例外狀況處理常式的回溯階段期間，會在不同的時間點呼叫 `ExceptionUnwind`。 在回溯單一例外狀況時，可以多次呼叫 `ExceptionUnwind`。  
  
 如果 `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED，指令指標將會線上程的分葉框架中，在此位置之前的序列點（這可能是之前的幾個指示）導致例外狀況的指令。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
