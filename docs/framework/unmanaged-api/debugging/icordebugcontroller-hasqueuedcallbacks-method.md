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
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892783"
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
 脫銷值的指標，如果目前已`true`針對指定的執行緒將任何 managed 回呼排入佇列，則為;否則為`false`。  
  
 如果為`pThread`參數指定 null， `HasQueuedCallbacks`將會`true`在目前有 managed 回呼排入佇列給任何執行緒時傳回。  
  
## <a name="remarks"></a>備註  
 回呼會一次分派一個，每次呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)時。 如果偵錯工具想要報告同時發生的多個偵測事件，可以檢查此旗標。  
  
 當偵測事件排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確保偵錯工具的狀態。 （呼叫`ICorDebugController::Continue`以清空佇列）。例如，如果佇列包含執行緒*x*上的兩個偵測事件，而偵錯工具在第一次調試事件之後暫停執行緒*x* ， `ICorDebugController::Continue`然後再呼叫，則執行緒*x*的第二個偵錯工具事件將會分派，雖然執行緒已暫止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
