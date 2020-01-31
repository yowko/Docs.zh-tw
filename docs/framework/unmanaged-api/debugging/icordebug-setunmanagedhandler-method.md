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
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785057"
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
 在[ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)物件的指標，表示非受控事件的事件處理常式。  
  
## <a name="remarks"></a>備註  
 非受控事件的事件處理常式物件必須在呼叫[ICorDebug：： Initialize](icordebug-initialize-method.md)之後，以及對[ICorDebug：： CreateProcess](icordebug-createprocess-method.md)或[ICorDebug：:D ebugactiveprocess](icordebug-debugactiveprocess-method.md)的任何呼叫之後設定。 不過，基於舊版目的，您不需要設定非受控事件的事件處理常式物件，直到引發第一個原生的 debug 事件為止。 具體而言，如果 `ICorDebug::CreateProcess` 已設定 CREATE_SUSPENDED 旗標，則原生的 debug 事件無法分派到主執行緒繼續執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](icordebug-interface.md)
