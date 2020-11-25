---
title: ICorDebug::SetUnmanagedHandler 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723385"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler 方法

指定非受控事件的事件處理常式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>參數  

 `pCallback`  
 在 [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) 物件的指標，該物件代表非受控事件的事件處理常式。  
  
## <a name="remarks"></a>備註  

 您必須在呼叫 [ICorDebug：： Initialize](icordebug-initialize-method.md) 之後，以及對 [ICorDebug：： CreateProcess](icordebug-createprocess-method.md) 或 [ICorDebug：:D ebugactiveprocess](icordebug-debugactiveprocess-method.md)的任何呼叫之前，設定非受控事件的事件處理常式物件。 不過，基於舊版的目的，在引發第一個原生偵錯工具事件之前，您不需要為非受控事件設定事件處理常式物件。 具體而言，如果 `ICorDebug::CreateProcess` 已設定 CREATE_SUSPENDED 旗標，則在繼續主執行緒之前，無法分派原生偵錯工具事件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
