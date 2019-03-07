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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b107ceec5c9e88117e8ec1f6f94d60debfdf7201
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500053"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks 方法
取得值，指出是否任何受管理的回呼目前在佇列中等待指定的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>參數  
 `pThread`  
 [in]表示執行緒 」 ICorDebugThread 」 物件的指標。  
  
 `pbQueued`  
 [out]為值的指標`true`如果任何受管理的回呼目前針對指定的執行緒已排入佇列，否則`false`。  
  
 如果指定 null`pThread`參數，`HasQueuedCallbacks`會傳回`true`如果目前沒有受管理的回呼排入佇列的任何執行緒。  
  
## <a name="remarks"></a>備註  
 回呼會在時間內，每次分派的一個[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫。 偵錯工具可以檢查此旗標，如果想要報告多個同時進行的偵錯事件。  
  
 當偵錯事件會排入佇列時，它們已經發生，因此偵錯工具必須清空的偵錯工具的狀態，確定整個佇列。 (呼叫`ICorDebugController::Continue`清空佇列。)比方說，如果佇列包含兩個執行緒上的偵錯事件*X*，以及偵錯工具暫止的執行緒*X*之後第一個偵錯事件，然後呼叫`ICorDebugController::Continue`，第二個偵錯事件執行緒*X*雖然已暫停的執行緒會分派。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

