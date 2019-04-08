---
title: ICorDebugManagedCallback2::Exception 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103346"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception 方法
已開始搜尋例外狀況處理常式會告知偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 [in]ICorDebugAppDomain 物件，表示應用程式定義域包含的執行緒例外狀況的指標。  
  
 `pThread`  
 [in]ICorDebugThread 物件，表示的執行緒例外狀況的指標。  
  
 `pFrame`  
 [in]ICorDebugFrame 物件，表示在範圍內，由指標`dwEventType`參數。 如需詳細資訊，請參閱 < 備註 > 一節的表格。  
  
 `nOffset`  
 [in]整數，指定位移，由`dwEventType`參數。 如需詳細資訊，請參閱 < 備註 > 一節的表格。  
  
 `dwEventType`  
 [in]CorDebugExceptionCallbackType 列舉，指定此例外狀況的回呼類型的值。  
  
 `dwFlags`  
 [in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊  
  
## <a name="remarks"></a>備註  
 `Exception`回呼例外狀況處理程序的 「 搜尋 」 階段期間，會呼叫在不同的點。 也就是說，它可以呼叫超過一次而回溯例外狀況。  
  
 正在處理的例外狀況可以擷取從所參考的 ICorDebugThread 物件`pThread`參數。  
  
 特定畫面格和位移取決於`dwEventType`參數，如下所示：  
  
|值 `dwEventType`|值 `pFrame`|值 `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|擲回例外狀況框架。|指令指標框架中。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|擲回的例外狀況的點最接近的使用者程式碼框架。|指令指標框架中。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|包含 catch 處理常式之框架。|Microsoft intermediate language (MSIL) 位移開頭的 catch 處理常式。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|未定義。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
