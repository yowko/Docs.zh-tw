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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379825"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread 介面
表示處理序中的執行緒。 `ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearCurrentException 方法](icordebugthread-clearcurrentexception-method.md)|這個方法尚未實作。 不要使用它。|  
|[CreateEval 方法](icordebugthread-createeval-method.md)|建立可在這個上操作的 ICorDebugEval 物件 `ICorDebugThread` 。|  
|[CreateStepper 方法](icordebugthread-createstepper-method.md)|建立 ICorDebugStepper 物件，允許在這個中逐步執行使用中的框架 `ICorDebugThread` 。|  
|[EnumerateChains 方法](icordebugthread-enumeratechains-method.md)|取得 ICorDebugChainEnum 列舉值的介面指標，其中包含這個中的所有堆疊鏈 `ICorDebugThread` 。|  
|[GetActiveChain 方法](icordebugthread-getactivechain-method.md)|取得這個上作用中 ICorDebugChain 的介面指標 `ICorDebugThread` 。|  
|[GetActiveFrame 方法](icordebugthread-getactiveframe-method.md)|取得這個上作用中 ICorDebugFrame 的介面指標 `ICorDebugThread` 。|  
|[GetAppDomain 方法](icordebugthread-getappdomain-method.md)|取得此目前執行所在之應用程式域的介面指標 `ICorDebugThread` 。|  
|[GetCurrentException 方法](icordebugthread-getcurrentexception-method.md)|取得 ICorDebugValue 物件的介面指標，代表目前由 managed 程式碼擲回的例外狀況。|  
|[GetDebugState 方法](icordebugthread-getdebugstate-method.md)|取得 CorDebugThreadState 值，描述這個的目前的偵錯工具狀態 `ICorDebugThread` 。|  
|[GetHandle 方法](icordebugthread-gethandle-method.md)|取得這個之使用中部分的目前控制碼 `ICorDebugThread` 。|  
|[GetID 方法](icordebugthread-getid-method.md)|取得這個之使用中部分的目前作業系統識別碼 `ICorDebugThread` 。|  
|[GetObject 方法](icordebugthread-getobject-method.md)|取得 common language runtime （CLR）執行緒的介面指標。|  
|[GetProcess 方法](icordebugthread-getprocess-method.md)|取得此組成元件之進程的介面指標 `ICorDebugThread` 。|  
|[GetRegisterSet 方法](icordebugthread-getregisterset-method.md)|取得與這個相關聯之緩存集的介面指標 `ICorDebugThread` 。|  
|[GetUserState 方法](icordebugthread-getuserstate-method.md)|取得 CorDebugUserState 值的位元組合，這個組合會描述這個的目前狀態 `ICorDebugThread` 。|  
|[SetDebugState 方法](icordebugthread-setdebugstate-method.md)|設定值的位元組合 `CorDebugThreadState` ，這個組合會描述這個的偵錯工具狀態 `ICorDebugThread` 。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
