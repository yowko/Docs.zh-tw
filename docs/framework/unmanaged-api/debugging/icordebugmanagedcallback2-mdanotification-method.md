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
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131465"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification 方法
提供通知，指出程式碼執行在正在進行調試的應用程式中遇到受管理的調試助理（MDA）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>參數  
 `pController`  
 在ICorDebugController 介面的指標，它會公開發生 MDA 的進程或應用程式域。  
  
 偵錯工具不應該對控制器是否為進程或應用程式域進行任何假設，雖然它一定可以查詢介面來進行判斷。  
  
 `pThread`  
 在ICorDebugThread 介面的指標，它會公開發生 debug 事件的 managed 執行緒。  
  
 如果 MDA 發生在未受管理的執行緒上，`pThread` 的值將會是 null。  
  
 您必須從 MDA 物件本身取得作業系統（OS）執行緒識別碼。  
  
 `pMDA`  
 在公開 MDA 資訊之[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)介面的指標。  
  
## <a name="remarks"></a>備註  
 MDA 是啟發式警告，而且不需要任何明確的偵錯工具動作，除非呼叫[ICorDebugController：： Continue 繼續](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)執行正在進行調試的應用程式。  
  
 Common language runtime （CLR）可以判斷哪些 Mda 會引發，而哪些資料會在任何指定的 MDA 中。 因此，偵錯工具不應建立任何需要特定 MDA 模式的功能。  
  
 在遇到 MDA 之後，Mda 可能會排入佇列並很快引發。 如果執行時間必須等到到達安全點才能引發 MDA，就會發生這種情況，而不是在遇到 MDA 時引發它。 這也表示執行時間可能會在一組排入佇列的回呼中引發數個 Mda （類似于「附加」事件操作）。  
  
 偵錯工具應該在從 `MDANotification` 回呼傳回之後立即釋放 `ICorDebugMDA` 實例的參考，以允許 CLR 回收 MDA 所耗用的記憶體。 如果有許多 Mda 引發，發行實例可能會改善效能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
