---
title: ICorDebug::SetManagedHandler 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90eb63b277f5c40053ecc3939890c87adc145251
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738127"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler 方法
指定 managed 事件的事件處理常式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>參數  
 `pCallback`  
 [in]指標[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)物件，也就是事件處理常式物件。  
  
## <a name="remarks"></a>備註  
 `SetManagedHandler` 必須在建立時呼叫。  
  
 如果`ICorDebugManagedCallback`實作不包含足夠的介面，以處理應用程式進行偵錯，偵錯事件`SetManagedHandler`傳回 E_NOINTERFACE HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
