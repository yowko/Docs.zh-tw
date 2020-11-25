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
ms.openlocfilehash: bd623f8bee2feafebe80c0c7513bcfb33d6ad367
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707889"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks 方法

取得值，這個值表示是否目前已針對指定的執行緒將任何受控回呼排入佇列。  
  
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
 擴展值的指標， `true` 如果有任何受控回呼目前排入指定執行緒的佇列，則為，否則為 `false` 。  
  
 如果為參數指定了 null `pThread` ，則 `HasQueuedCallbacks` `true` 如果目前有任何執行緒的受控回呼已排入佇列，則會傳回。  
  
## <a name="remarks"></a>備註  

 回呼會一次分派一個，每次呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 。 如果偵錯工具想要報告多個同時發生的偵錯工具事件，則可以檢查此旗標。  
  
 當偵測到事件已排入佇列時，偵錯工具必須清空整個佇列，以確定偵錯工具的狀態。  (呼叫 `ICorDebugController::Continue` 以清空佇列 ) 。例如，如果佇列包含執行緒 *x* 上的兩個偵錯工具事件，而且偵錯工具在第一個偵測事件之後暫停執行緒 *x* ，然後呼叫，則會 `ICorDebugController::Continue` 分派執行緒 *x* 的第二個偵測事件，雖然執行緒已暫止。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
