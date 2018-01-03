---
title: "ICorDebugController::HasQueuedCallbacks 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03d52bb31a81876a00e1af33494b14fb99fee0fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks 方法
取得值，指出是否針對指定的執行緒目前佇列任何受管理的回呼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in]表示執行緒 」 ICorDebugThread 」 物件的指標。  
  
 `pbQueued`  
 [out]值的指標`true`如果任何受管理的回呼目前佇列指定的執行緒，否則`false`。  
  
 如果指定 null`pThread`參數，`HasQueuedCallbacks`會傳回`true`如果目前沒有任何執行緒排入佇列 managed 回撥。  
  
## <a name="remarks"></a>備註  
 回呼會分派的一次，每次[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫。 偵錯工具可以檢查這個旗標，如果想要報告多個同時發生的偵錯事件。  
  
 當偵錯事件會排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確定偵錯項目狀態。 (呼叫`ICorDebugController::Continue`清空佇列。)例如，如果佇列包含兩個執行緒上的偵錯事件*X*，和偵錯工具暫止的執行緒*X*之後第一個偵錯事件，然後呼叫`ICorDebugController::Continue`，第二個偵錯事件執行緒*X*會分派，雖然執行緒已經暫止。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 
