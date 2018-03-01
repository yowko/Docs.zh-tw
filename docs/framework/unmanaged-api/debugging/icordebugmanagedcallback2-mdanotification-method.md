---
title: "ICorDebugManagedCallback2::MDANotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a58e286feb3387557d0a37c463f2af67abf8cc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification 方法
提供執行程式碼發現正在偵錯的應用程式中 managed 偵錯助理 (MDA) 的通知。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pController`  
 [in]ICorDebugController 介面，公開程序或應用程式定義域發生 MDA 的指標。  
  
 雖然永遠可以查詢做出判斷介面的偵錯工具不應做任何假設控制器是處理程序或應用程式定義域。  
  
 `pThread`  
 [in]ICorDebugThread 介面公開 managed 偵錯事件發生所在的執行緒的指標。  
  
 如果 MDA 發生 unmanaged 執行緒，之中的值`pThread`將會是 null。  
  
 您必須從 MDA 物件本身，以取得作業系統 (OS) 執行緒 ID。  
  
 `pMDA`  
 [in]指標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)公開 MDA 資訊的介面。  
  
## <a name="remarks"></a>備註  
 MDA 是啟發式的警告，而且不需要任何明確的偵錯工具動作，除了呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)以繼續執行應用程式進行偵錯。  
  
 Mda 會引發以及哪些資料是在任何給定的 MDA，在任何時間點，可以判斷 common language runtime (CLR)。 因此，偵錯工具應該不會建置需要特定 MDA 模式的任何功能。  
  
 Mda 會進入佇列並不久之後遇到的 MDA 時引發。 如果執行階段必須等候，直到達到安全點引發而非引發 MDA，當它遇到的 MDA，則會發生此問題。 這也表示執行階段可能會引發 Mda 集中單一佇列的回呼 （類似於 「 附加 」 事件作業） 的數目。  
  
 偵錯工具就會釋放參考`ICorDebugMDA`之後立即從傳回的執行個體`MDANotification`回呼，讓 CLR 回收 MDA 所耗用的記憶體。 釋放此執行個體可改善效能，當引發許多 Mda。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
