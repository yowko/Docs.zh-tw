---
title: ICorDebugThread 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184700"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread 介面
表示處理序中的執行緒。 `ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|這個方法尚未實作。 不要使用它。|  
|[CreateEval 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|在此建立操作的 ICorDebugEval 物件`ICorDebugThread`。|  
|[CreateStepper 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|建立 ICorDebugStepper 物件，可讓您逐步完成每個在此使用中畫面格`ICorDebugThread`。|  
|[EnumerateChains 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|ICorDebugChainEnum 列舉值，其中包含所有的堆疊鏈結，在此取得的介面指標`ICorDebugThread`。|  
|[GetActiveChain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|取得作用中的 ICorDebugChain 的介面指標，此`ICorDebugThread`。|  
|[GetActiveFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|取得作用中的 ICorDebugFrame 的介面指標，此`ICorDebugThread`。|  
|[GetAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|取得應用程式定義域的介面指標，這個`ICorDebugThread`目前正在執行。|  
|[GetCurrentException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|ICorDebugValue 物件，表示目前所擲回例外狀況的 managed 程式碼中取得的介面指標。|  
|[GetDebugState 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|取得描述目前的偵錯狀態，這個 CorDebugThreadState 值`ICorDebugThread`。|  
|[GetHandle 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|取得目前的控制代碼的作用中的部分`ICorDebugThread`。|  
|[GetID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|取得目前的作業系統識別項的使用中的這部分`ICorDebugThread`。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|取得 common language runtime (CLR) 執行緒的介面指標。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|這個程序中取得的介面指標`ICorDebugThread`構成部分。|  
|[GetRegisterSet 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|取得與此相關聯的暫存器集的介面指標`ICorDebugThread`。|  
|[GetUserState 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|取得描述這個的目前狀態的 CorDebugUserState 值的位元組合`ICorDebugThread`。|  
|[SetDebugState 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|設定的位元組合`CorDebugThreadState`值，描述偵錯的狀態這`ICorDebugThread`。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
