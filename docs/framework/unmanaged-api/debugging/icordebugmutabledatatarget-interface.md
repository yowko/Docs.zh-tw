---
title: "ICorDebugMutableDataTarget 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget 介面
擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以支援可變動的資料目標。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[ContinueStatusChanged 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|變更指定執行緒上未處理之偵錯事件的接續狀態。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|設定執行緒的內容 (登錄值)。|  
|[WriteVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|將記憶體寫入目標處理序位址空間。|  
  
## <a name="remarks"></a>備註  
 這個延伸模組[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面可以實作的偵錯工具想要修改目標處理序 （例如，若要執行即時入侵式偵錯）。  
  
 上述所有方法都是選擇性的，未實作這個介面或無法呼叫這些方法，並不會失去以核心檢查為基礎的偵錯功能。  這些方法中的任何失敗 `HRESULT` 都會以 `HRESULT` 形式從 ICorDebug 方法呼叫向外傳播。  
  
 請注意，單一 ICorDebug 方法呼叫可能會導致多項變動，沒有任何機制可確保相關的變動會以交易方式 (全有或全無) 來套用。  這表示如果某項變動在其他變動成功之後失敗 (在相同的 ICorDebug 呼叫中)，目標處理序的狀態可能會不一致，因此偵錯可能會變成不可靠。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
