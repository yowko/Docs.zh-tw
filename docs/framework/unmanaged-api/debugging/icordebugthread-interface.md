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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791480"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread 介面
表示處理序中的執行緒。 `ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearCurrentException 方法](icordebugthread-clearcurrentexception-method.md)|這個方法尚未實作。 不要使用它。|  
|[CreateEval 方法](icordebugthread-createeval-method.md)|建立可在此 `ICorDebugThread`上運作的 ICorDebugEval 物件。|  
|[CreateStepper 方法](icordebugthread-createstepper-method.md)|建立 ICorDebugStepper 物件，允許在此 `ICorDebugThread`中逐步執行使用中的框架。|  
|[EnumerateChains 方法](icordebugthread-enumeratechains-method.md)|取得 ICorDebugChainEnum 列舉值的介面指標，其中包含此 `ICorDebugThread`中的所有堆疊鏈。|  
|[GetActiveChain 方法](icordebugthread-getactivechain-method.md)|取得此 `ICorDebugThread`上作用中 ICorDebugChain 的介面指標。|  
|[GetActiveFrame 方法](icordebugthread-getactiveframe-method.md)|取得此 `ICorDebugThread`上作用中 ICorDebugFrame 的介面指標。|  
|[GetAppDomain 方法](icordebugthread-getappdomain-method.md)|取得此 `ICorDebugThread` 目前執行所在之應用程式域的介面指標。|  
|[GetCurrentException 方法](icordebugthread-getcurrentexception-method.md)|取得 ICorDebugValue 物件的介面指標，代表目前由 managed 程式碼擲回的例外狀況。|  
|[GetDebugState 方法](icordebugthread-getdebugstate-method.md)|取得描述此 `ICorDebugThread`目前的 debug 狀態的 CorDebugThreadState 值。|  
|[GetHandle 方法](icordebugthread-gethandle-method.md)|取得此 `ICorDebugThread`之使用中部分的目前控制碼。|  
|[GetID 方法](icordebugthread-getid-method.md)|取得此 `ICorDebugThread`之使用中部分的目前作業系統識別碼。|  
|[GetObject 方法](icordebugthread-getobject-method.md)|取得 common language runtime （CLR）執行緒的介面指標。|  
|[GetProcess 方法](icordebugthread-getprocess-method.md)|取得此 `ICorDebugThread` 構成元件之進程的介面指標。|  
|[GetRegisterSet 方法](icordebugthread-getregisterset-method.md)|取得與此 `ICorDebugThread`相關聯之緩存集的介面指標。|  
|[GetUserState 方法](icordebugthread-getuserstate-method.md)|取得 CorDebugUserState 值的位元組合，這個組合會描述這個 `ICorDebugThread`的目前狀態。|  
|[SetDebugState 方法](icordebugthread-setdebugstate-method.md)|設定 `CorDebugThreadState` 值的位元組合，以描述此 `ICorDebugThread`的偵錯工具狀態。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
