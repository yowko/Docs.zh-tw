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
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781522"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception 方法
通知偵錯工具已開始搜尋例外狀況處理常式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在ICorDebugAppDomain 物件的指標，表示包含擲回例外狀況之執行緒的應用程式域。  
  
 `pThread`  
 在ICorDebugThread 物件的指標，表示擲回例外狀況的執行緒。  
  
 `pFrame`  
 在代表框架的 ICorDebugFrame 物件指標，由 `dwEventType` 參數決定。 如需詳細資訊，請參閱備註一節中的表格。  
  
 `nOffset`  
 在指定位移的整數，由 `dwEventType` 參數決定。 如需詳細資訊，請參閱備註一節中的表格。  
  
 `dwEventType`  
 在CorDebugExceptionCallbackType 列舉的值，指定這個例外狀況回呼的類型。  
  
 `dwFlags`  
 在[CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md)列舉的值，指定例外狀況的其他資訊。  
  
## <a name="remarks"></a>備註  
 在例外狀況處理常式的搜尋階段，會在不同的時間點呼叫 `Exception` 回呼。 也就是說，它可以在回溯例外狀況時呼叫多次。  
  
 所處理的例外狀況可以從 `pThread` 參數所參考的 ICorDebugThread 物件中抓取。  
  
 特定的框架和位移取決於 `dwEventType` 參數，如下所示：  
  
|`dwEventType` 的值|`pFrame` 的值|`nOffset` 的值|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|擲回例外狀況的框架。|框架中的指令指標。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|最接近所擲回例外狀況點的使用者程式碼框架。|框架中的指令指標。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|包含 catch 處理常式的框架。|Catch 處理常式開頭的 Microsoft 中繼語言（MSIL）位移。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Useraccountcontrol.|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
