---
title: ICorDebugController 介面
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107545"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController 介面

表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|這個方法已過時。|  
|`ICorDebugController::CommitChanges`|這個方法已過時。|  
|[Continue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|之後繼續執行的受管理的執行緒呼叫[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。|  
|[Detach 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|中斷連結處理序或應用程式定義域與偵錯工具。|  
|[EnumerateThreads 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|取得作用中的 managed 執行緒處理序中的列舉值。|  
|[HasQueuedCallbacks 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|取得值，指出是否任何受管理的回呼目前在佇列中等待指定的執行緒。|  
|[IsRunning 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|取得值，指出是否在程序中的執行緒目前正在自由。|  
|[SetAllThreadsDebugState 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|設定程序中的所有 managed 執行緒的偵錯狀態。|  
|[Stop 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|在此程序中執行 managed 程式碼的所有執行緒上執行合作式的停駐點。|  
|[Terminate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|終止與指定的結束代碼的程序。|  
  
## <a name="remarks"></a>備註  
 如果`ICorDebugController`是控制處理程序，其範圍包括所有執行緒的處理程序。 如果`ICorDebugController`會控制應用程式定義域，範圍包括該特定應用程式定義域的執行緒。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
