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
ms.openlocfilehash: 09a410f54ddf07c9a5f6bb7dd34f2aaf266e0734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704574"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification 方法

提供在正在進行調試的應用程式中，程式碼執行遇到 managed 偵錯工具 (MDA) 的通知。  
  
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
 在ICorDebugController 介面的指標，此介面會公開發生 MDA 的進程或應用程式域。  
  
 偵錯工具不應對控制器是否為進程或應用程式域提出任何假設，不過它一律可以查詢介面以做出判斷。  
  
 `pThread`  
 在ICorDebugThread 介面的指標，此介面會公開發生 debug 事件的 managed 執行緒。  
  
 如果 MDA 發生在非受控執行緒上，的值 `pThread` 將會是 null。  
  
 您必須從 MDA 物件本身取得作業系統 (OS) 執行緒識別碼。  
  
 `pMDA`  
 在 [ICorDebugMDA](icordebugmda-interface.md) 介面的指標，此介面會公開 MDA 資訊。  
  
## <a name="remarks"></a>備註  

 MDA 是啟發式警告，不需要任何明確的偵錯工具動作，除非呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 繼續執行正在進行調試的應用程式。  
  
 Common language runtime (CLR) 可判斷所引發的 Mda，以及任何指定之 MDA 中的哪些資料在任何時間點。 因此，偵錯工具不應建立任何需要特定 MDA 模式的功能。  
  
 Mda 可能會排入佇列，並在遇到 MDA 之後立即引發。 如果執行時間需要等候，直到達到引發 MDA 的安全點（而不是在遇到 MDA 時引發 MDA），就會發生這種情況。 這也表示執行時間可能會在一組佇列的回呼中引發一些 Mda (類似于「附加」事件作業) 。  
  
 偵錯工具應該會 `ICorDebugMDA` 在從回呼傳回之後立即釋出實例的參考 `MDANotification` ，以便讓 CLR 回收 MDA 所耗用的記憶體。 如果引發許多 Mda，則釋放實例可能會改善效能。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
