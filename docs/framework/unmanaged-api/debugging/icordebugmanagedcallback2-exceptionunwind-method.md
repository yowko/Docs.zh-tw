---
title: "ICorDebugManagedCallback2::ExceptionUnwind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind 方法
提供例外狀況回溯程序期間的狀態通知。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAppDomain`  
 [in]表示包含擲回例外狀況所在的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。  
  
 `pThread`  
 [in]表示擲回例外狀況所在的執行緒 ICorDebugThread 物件的指標。  
  
 `dwEventType`  
 [in]CorDebugExceptionUnwindCallbackType 列舉型別會指定回呼在回溯階段期間通知的事件值。  
  
 `dwFlags`  
 [in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊。  
  
## <a name="remarks"></a>備註  
 `ExceptionUnwind`會在回溯階段的例外狀況處理程序期間呼叫的各個點上。 `ExceptionUnwind`可以被呼叫一次以上時回溯單一例外狀況。  
  
 如果`dwEventType`= DEBUG_EXCEPTION_INTERCEPTED，指令指標會在執行緒，在之前的序列點的分葉框架 （這可能是之前的幾個指令） 造成例外狀況的指示。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
