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
ms.openlocfilehash: a15391b63012fec3d0e6a0aa67540c3d2541944c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671313"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind 方法

提供例外狀況回溯進程期間的狀態通知。  
  
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
 在ICorDebugAppDomain 物件的指標，代表包含擲回例外狀況之執行緒的應用程式域。  
  
 `pThread`  
 在代表擲回例外狀況之執行緒的 ICorDebugThread 物件指標。  
  
 `dwEventType`  
 在CorDebugExceptionUnwindCallbackType 列舉的值，這個值會指定在回溯階段期間回呼所收到的事件。  
  
 `dwFlags`  
 在 [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) 列舉的值，指定例外狀況的其他資訊。  
  
## <a name="remarks"></a>備註  

 `ExceptionUnwind` 在例外狀況處理常式的回溯階段期間，會在不同的點呼叫。 `ExceptionUnwind` 可以在回溯單一例外狀況時呼叫一次以上。  
  
 如果 `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED，指令指標會線上程的分葉框架中，在 (之前的序列點可能會有幾個指令，才能) 導致例外狀況的指示。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
