---
title: ICorDebugManagedCallback2::MDANotification 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15addd0b35c43945f643386f8983fc14c9312bae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492331"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification 方法
提供執行程式碼發生在應用程式進行偵錯 managed 偵錯助理 (MDA) 的通知。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>參數  
 `pController`  
 [in]ICorDebugController 介面，公開程序或應用程式定義域發生 MDA 的指標。  
  
 雖然永遠可以查詢的介面，以決定偵錯工具不應建立任何假設該控制器是處理程序或應用程式定義域。  
  
 `pThread`  
 [in]ICorDebugThread 介面會公開 managed 偵錯事件發生所在的執行緒指標。  
  
 如果 MDA 發生 unmanaged 執行緒，值`pThread`將會是 null。  
  
 您必須取得作業系統 (OS) 執行緒識別碼，來自 MDA 物件本身。  
  
 `pMDA`  
 [in]指標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA 資訊公開 （expose） 的介面。  
  
## <a name="remarks"></a>備註  
 MDA 是啟發式的警告，而且不需要任何明確的偵錯工具動作，但呼叫除外[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)以繼續執行應用程式進行偵錯。  
  
 Mda 會引發以及哪些資料是在任何給定的 MDA，在任何時間點，可以判斷 common language runtime (CLR)。 因此，偵錯工具應該不會建置需要特定的 MDA 模式的任何功能。  
  
 Mda 可能已排入佇列，不久之後遇到 MDA 時，才引發。 如果執行階段必須等候，直到它到達安全點引發 MDA，而不是它遇到時引發之 MDA 的則會發生此問題。 這也表示執行階段可能會引發 Mda 已排入佇列的回呼 （類似於 「 附加 」 事件作業） 的以一組數目。  
  
 偵錯工具應該釋放的參考`ICorDebugMDA`之後立即從傳回的執行個體`MDANotification`回呼，以允許 CLR 回收 MDA 所耗用的記憶體。 釋放此執行個體可能會改善效能，如果引發許多 Mda。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
