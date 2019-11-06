---
title: ICorDebugController::HasQueuedCallbacks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125391"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks 方法
取得值，指出目前是否已針對指定的執行緒將任何 managed 回呼排入佇列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>參數  
 `pThread`  
 在代表執行緒之 "ICorDebugThread" 物件的指標。  
  
 `pbQueued`  
 脫銷如果目前已針對指定的執行緒將任何 managed 回呼排入佇列，則為 `true` 的值指標。否則，`false`。  
  
 如果指定了 `pThread` 參數的 null，`HasQueuedCallbacks` 會傳回 `true` （如果有任何執行緒目前已排入佇列的受控回呼）。  
  
## <a name="remarks"></a>備註  
 回呼會一次分派一個，每次呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)時。 如果偵錯工具想要報告同時發生的多個偵測事件，可以檢查此旗標。  
  
 當偵測事件排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確保偵錯工具的狀態。 （呼叫 `ICorDebugController::Continue` 以清空佇列）。例如，如果佇列包含執行緒*x*上的兩個偵測事件，而且偵錯工具在第一個偵錯工具事件之後暫停執行緒*x* ，然後呼叫 `ICorDebugController::Continue`，則會分派執行緒*x*的第二個偵錯工具事件，但執行緒已暫止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
